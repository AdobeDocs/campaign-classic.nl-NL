---
product: campaign
title: Migreren naar de nieuwe releaseserver
description: Meer informatie over het implementeren van de server voor het leveren van campagnes
hide: true
hidefromtoc: true
source-git-commit: cd2fa2450f6e8389e9c47c412da8943a5c8bb7f3
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 4%

---

# Campagne Deliverability Server {#acc-deliverability}

Vanaf de release van Campaign Classic v7 21.1 stelt Adobe Campaign een nieuwe leverbaarbaarheidsserver voor die problemen met hoge beschikbaarheid oplost en de naleving van de beveiligingsvereisten aanpakt. Campaign Classic synchroniseert nu de leveringsregels, de uitzendingen en het onderdrukkingsadres van en aan nieuwe leverbaarheidsserver.

Als klant van Campaign Classic, moet u de nieuwe leverbaarheidsserver uitvoeren

>[!NOTE]
>
>Voor alle vragen over deze wijzigingen leest u de [Veelgestelde vragen](#faq-aa). Neem voor meer informatie contact op met [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Wat is er veranderd?{#acc-deliverability-changes}

Adobe ontmantelt oudere gegevenscentra wegens veiligheidsoverwegingen. Adobe Campaign Classic-clients moeten migreren naar de nieuwe, op de Amazon Web Service (AWS) gehoste service.

Deze nieuwe server garandeert een hoge beschikbaarheid (99.9) &#x200B; en biedt veilige en geverifieerde eindpunten om campagnemeservers in staat te stellen de vereiste gegevens op te halen: in plaats van verbinding te maken met de database voor elk verzoek, slaat de nieuwe, te leveren server de gegevens in de cache op om de aanvragen waar mogelijk te bedienen. Dit mechanisme verbetert de responstijd. &#x200B;


## Heeft dit gevolgen voor u?{#acc-deliverability-impacts}

Als u de oude Adobe Campaign-releaseserver gebruikt en uw omgeving is geïmplementeerd op een lagere build dan Campagne 21.1.1, heeft dit gevolgen voor u. U moet een upgrade uitvoeren naar Campagne 21.1 (of meer).

Leer hoe u uw versie kunt controleren [in deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Hoe kan ik bijwerken?{#acc-deliverability-update}

Als gehoste klant werkt Adobe samen met u om uw exemplaar(s) te upgraden naar de nieuwere versie.

Als klant op locatie/hybride klant moet u een upgrade uitvoeren naar een van de nieuwere versies om te profiteren van de nieuwe, te leveren server.
Zodra alle instanties worden bevorderd, zult u kunnen [de nieuwe integratie uitvoeren](#implementation-steps) naar Adobe-leverbaarbaarheidsserver en zorg voor een naadloze overgang.

## Implementatiestappen (hybride en on-premise klanten) {#implementation-steps}

>[!IMPORTANT]
>
>Deze stappen mogen alleen worden uitgevoerd door Hybride en On-premise implementaties.
>
>Voor gehoste implementaties neemt u contact op met [Adobe Klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

### Vereisten{#prerequisites}

Als onderdeel van de nieuwe integratie van de leverbaarheidsserver, moet de Campagne met Adobe Gedeelde Diensten via een op de Dienst van Identity Management (IMS) gebaseerde authentificatie communiceren. De aangewezen manier is het op Adobe Developer gebaseerde Token van de Gateway te gebruiken (ook genoemd Token van de Technische Rekening of JWT van Adobe IO).

### Stap 1: Adobe Developer-project maken/bijwerken {#adobe-io-project}

1. Toegang [Adobe Developer Console](https://developer.adobe.com/console/home) en meld u aan bij de toegang tot ontwikkelaars van uw organisatie.

   >[!NOTE]
   >
   > Zorg ervoor u in het correcte portaal van de Organisatie wordt geregistreerd.

1. Selecteren **[!UICONTROL + Add to Project]** en kiest u **[!UICONTROL API]**.
1. In de **[!UICONTROL Add an API]** venster, selecteert u **[!UICONTROL Adobe Campaign]**.
1. Kies **[!UICONTROL Service Account (JWT)]** als het verificatietype.
1. Als uw client-id leeg was, selecteert u **[!UICONTROL Generate a key pair]** om een openbare en privé zeer belangrijke paar tot stand te brengen.

   De sleutels zullen dan automatisch met een standaardvervaldatum van 365 dagen worden gedownload. Zodra verlopen, zult u een nieuw zeer belangrijk paar moeten creëren en de integratie in het configuratiedossier bijwerken. Met de optie 2 kunt u handmatig uw **[!UICONTROL Public key]** met een langere vervaldatum.

   >[!CAUTION]
   >
   >Sla het bestand config.zip op wanneer de downloadprompt verschijnt, omdat u deze niet opnieuw kunt downloaden.

1. Klik op **[!UICONTROL Next]**.
1. Bestaande kiezen **[!UICONTROL Product profile]** of maak indien nodig een nieuwe versie. Hiervoor is geen toestemming vereist **[!UICONTROL Product profile]**. Voor meer informatie over [!DNL Analytics] **[!UICONTROL Product Profiles]**, zie [deze olie](https://helpx.adobe.com/enterprise/using/manage-developers.html).

   Klik vervolgens op **[!UICONTROL Save configured API]**.

1. Van uw project, selecteer **[!UICONTROL Adobe Campaign]** en kopieert u de volgende informatie onder **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

>[!CAUTION]
>
>Adobe Developer-certificaat verloopt na twaalf maanden. Je moet elk jaar een nieuw sleutelpaar genereren.

### Stap 2: De referenties van het project toevoegen in Adobe Campaign {#add-credentials-campaign}

De persoonlijke sleutel moet in base64 UTF-8-indeling worden gecodeerd.

Dit doet u als volgt:

1. Gebruik de persoonlijke sleutel die in de bovenstaande stappen is gegenereerd.
1. Codeer de persoonlijke sleutel met behulp van de volgende opdracht: `base64 ./private.key > private.key.base64`. Hierdoor wordt de base64-inhoud opgeslagen in een nieuw bestand `private.key.base64`.

   >[!NOTE]
   >
   >Soms kunnen extra regels automatisch worden toegevoegd wanneer u de persoonlijke sleutel kopieert/plakt. Vergeet niet deze te verwijderen voordat u uw persoonlijke sleutel gaat coderen.

1. De inhoud van het bestand kopiëren `private.key.base64`.
1. Meld u via SSH aan bij elke container waarin de Adobe Campaign-instantie is geïnstalleerd en voeg de projectgegevens toe in Adobe Campaign door de volgende opdracht uit te voeren als `neolane` gebruiker. Hiermee voegt u de **[!UICONTROL Technical Account]** referenties in het configuratiebestand van de instantie.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. U moet de server stoppen en dan opnieuw beginnen om met de wijziging rekening te houden. U kunt ook een `config -reload` gebruiken.

### Stap 3: Controleer uw configuratie

Zodra de montages worden gedaan, kunt u uw instantieconfiguratie controleren. Volg de onderstaande stappen:

1. Open de clientconsole en meld u als beheerder aan bij Adobe Campaign.
1. Bladeren naar **Beheer > Platform > Opties**.
1. Controleer de `DmRendering_cuid` option value is fill. Deze moet op al uw campagneexemplaren worden ingevuld (MKT, MID, RT, EXEC). Als deze waarde niet is gevuld, moet u deze invullen. Als geen waarde wordt gevuld, contacteer [Adobe Klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om uw CUID op te halen.

### Stap 4: De nieuwe releaseserver inschakelen

U kunt nu de nieuwe releaseserver inschakelen. Dit doet u als volgt:

1. Open de clientconsole en meld u als beheerder aan bij Adobe Campaign.
1. Bladeren naar **Beheer > Platform > Opties**.
1. Toegang krijgen tot `NewDeliverabilityServer_FeatureFlag` en de waarde instellen op `1`. Deze configuratie zou op al uw instanties van de Campagne (MKT, MID, RT, EXEC) moeten worden uitgevoerd.


### Stap 5: Valideer uw configuratie

Volg onderstaande stappen om te controleren of de integratie is gelukt:


1. Open de clientconsole en meld u aan bij Adobe Campaign.
1. Bladeren naar **Beheer > Productie > Technische workflows**.
1. Start de **Update voor leverbaarheid** (leverabilityUpdate) workflow. Dit moet worden uitgevoerd op al uw campagneinstanties (MKT, MID, RT, EXEC).
1. Logbestanden controleren: de workflow moet zonder fouten worden uitgevoerd.

## Veelgestelde vragen{#faq-aa}

V: A:

V: A:



Voor meer hulp, contacteer [Adobe Klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
