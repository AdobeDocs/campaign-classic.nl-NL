---
product: campaign
title: Migreren naar de nieuwe releaseserver
description: Meer informatie over het implementeren van de server voor het leveren van campagnes
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 2c70b5a4434b9fb22490eb3c1705f4e5c803643e
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 4%

---

# Campagne Deliverability Server {#acc-deliverability}

Vanaf de release van Campaign Classic v7 21.1 stelt Adobe Campaign een nieuwe leverbaarbaarheidsserver voor die problemen met hoge beschikbaarheid oplost en de naleving van de beveiligingsvereisten aanpakt. Campaign Classic synchroniseert nu de leveringsregels, de uitzendingen en het onderdrukkingsadres van en aan nieuwe leverbaarheidsserver.

Als klant van Campaign Classic, moet u de nieuwe leveringsserver uitvoeren.

>[!NOTE]
>
>Voor vragen over deze wijzigingen neemt u contact op met de [Adobe-klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Wat is er veranderd?{#acc-deliverability-changes}

Adobe ontmantelt oudere gegevenscentra wegens veiligheidsoverwegingen. Adobe Campaign Classic-clients moeten migreren naar de nieuwe, op de Amazon Web Service (AWS) gehoste service.

Deze nieuwe server garandeert een hoge beschikbaarheid (99.9) &#x200B; en biedt veilige en geverifieerde eindpunten om campagnemeservers in staat te stellen de vereiste gegevens op te halen: in plaats van verbinding te maken met de database voor elk verzoek, slaat de nieuwe, te leveren server de gegevens in de cache op om de aanvragen waar mogelijk te bedienen. Dit mechanisme verbetert de responstijd. &#x200B;

## Heeft dit gevolgen voor u?{#acc-deliverability-impacts}

Als u de oude Adobe Campaign-releaseserver gebruikt en uw omgeving is geïmplementeerd op een lagere build dan Campagne 21.1.1, heeft dit gevolgen voor u. U moet een upgrade uitvoeren naar Campagne 21.1 (of meer).

Leer hoe u uw versie kunt controleren [in deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Hoe kan ik bijwerken?{#acc-deliverability-update}

Als **gehoste klant**, werkt Adobe samen met u om uw exemplaar(s) te upgraden naar de nieuwere versie en het project te maken in Adobe Developer Console.

Als **on-premise/hybride klant**, moet u een upgrade uitvoeren naar een van de nieuwere versies om te kunnen profiteren van de nieuwe releaseserver. Zodra alle instanties worden bevorderd, zult u kunnen [de nieuwe integratie uitvoeren](#implementation-steps) naar Adobe-leverbaarbaarheidsserver en zorg voor een naadloze overgang.

## Implementatiestappen {#implementation-steps}

Als onderdeel van de nieuwe integratie van de leverbaarheidsserver, moet de Campagne met Adobe Gedeelde Diensten via een op de Dienst van Identity Management (IMS) gebaseerde authentificatie communiceren. De aangewezen manier is de op Adobe Developer gebaseerde Token van de Gateway te gebruiken (ook genoemd de Token van de Technische Rekening of JWT van Adobe IO).


>[!WARNING]
>
>Deze stappen mogen alleen worden uitgevoerd door Hybride en On-premise implementaties.

### Vereisten{#prerequisites}

Controleer uw instantieconfiguratie voordat u de implementatie start.

1. Open de clientconsole van Campagne en meld u als beheerder aan bij Adobe Campaign.
1. Bladeren naar **Beheer > Platform > Opties**.
1. Controleer de `DmRendering_cuid` option value is fill.

   * Als de optie is gevuld, kunt u de implementatie starten.
   * Als geen waarde wordt gevuld, contacteer [Adobe Klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om uw CUID op te halen.

      Deze optie moet op al uw instanties van de Campagne (MKT, MID, RT, EXEC) met de zelfde waarde worden ingevuld.

### Stap 1: Adobe Developer-project maken/bijwerken {#adobe-io-project}

1. Toegang [Adobe Developer Console](https://developer.adobe.com/console/home) en meld u aan bij de toegang tot ontwikkelaars van uw organisatie.

   >[!NOTE]
   >
   > Zorg ervoor u in het correcte portaal van de Organisatie wordt geregistreerd.

1. Selecteer **[!UICONTROL Create new project]**.
   ![](assets/New-Project.png)


   >[!CAUTION]
   >
   >Als u reeds Adobe IO JWT authentificatiefunctionaliteit voor een andere integratie, zoals de schakelaar van de Analyse, of de Trekkers van de Adobe gebruikt, dan moet u uw project bijwerken door toe te voegen **Campagne-API** voor dat project.
1. Kies **[!UICONTROL Add API]**.
   ![](assets/Add-API.png)
1. In de **[!UICONTROL Add an API]** venster, selecteert u **[!UICONTROL Adobe Campaign]**.
   ![](assets/AC-API.png)
<!--1. Choose **[!UICONTROL Service Account (JWT)]** as the authentication type.-->
1. Als uw client-id leeg was, selecteert u **[!UICONTROL Generate a key pair]** om een openbare en privé zeer belangrijke paar tot stand te brengen.
   ![](assets/Generate-a-key-pair.png)

   De sleutels zullen dan automatisch met een standaardvervaldatum van 365 dagen worden gedownload. Zodra verlopen, zult u een nieuw zeer belangrijk paar moeten creëren en de integratie in het configuratiedossier bijwerken. Met de optie 2 kunt u handmatig uw **[!UICONTROL Public key]** met een langere vervaldatum.
   ![](assets/New-key-pair.png)

   >[!CAUTION]
   >
   >U moet de `config.zip` bestand wanneer de downloadprompt verschijnt omdat u deze niet opnieuw kunt downloaden.

1. Klik op **[!UICONTROL Next]**.
1. Bestaande kiezen **[!UICONTROL Product profile]** of maak indien nodig een nieuwe versie. Hiervoor is geen toestemming vereist **[!UICONTROL Product profile]**. Voor meer informatie over **[!UICONTROL Product Profiles]**, zie [deze pagina](https://helpx.adobe.com/enterprise/using/manage-developers.html).
   ![](assets/Product-Profile-API.png)

   Klik vervolgens op **[!UICONTROL Save configured API]**.

1. Van uw project, selecteer **[!UICONTROL Adobe Campaign]** en kopieert u de volgende informatie onder **[!UICONTROL Service Account (JWT)]**

   ![](assets/Config-API.png)

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

### Stap 3: De nieuwe releaseserver inschakelen

U kunt nu de nieuwe releaseserver inschakelen. Dit doet u als volgt:

1. Open de clientconsole en meld u als beheerder aan bij Adobe Campaign.
1. Bladeren naar **Beheer > Platform > Opties**.
1. Toegang krijgen tot `NewDeliverabilityServer_FeatureFlag` en de waarde instellen op `1`. Deze configuratie zou op al uw instanties van de Campagne (MKT, MID, RT, EXEC) moeten worden uitgevoerd.

### Stap 4: Valideer uw configuratie

Volg onderstaande stappen om te controleren of de integratie is gelukt:


1. Open de clientconsole en meld u aan bij Adobe Campaign.
1. Bladeren naar **Beheer > Productie > Technische workflows**.
1. Start de **Update voor leverbaarheid** (leverabilityUpdate) workflow. Dit moet worden uitgevoerd op al uw campagneinstanties (MKT, MID, RT, EXEC).
1. Logbestanden controleren: de workflow moet zonder fouten worden uitgevoerd.

Voor meer hulp, contacteer [Adobe Klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
