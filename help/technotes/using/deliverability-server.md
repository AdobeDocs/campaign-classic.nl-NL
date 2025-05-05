---
product: campaign
title: Bijwerken naar de nieuwe releaseserver
description: Leer hoe u een update kunt uitvoeren naar de nieuwe server voor campagneresultaten
feature: Technote, Deliverability
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: c42d4022587846081442a39d03546c0ef335c7a0
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Bijwerken naar de nieuwe releaseserver {#acc-deliverability}

Beginnend [ v7.2.2 versie ](../../rn/using/latest-release.md#release-7-2-2), baseert Adobe Campaign zich op een nieuwe leverbaarheidsserver die hoge beschikbaarheid brengt en veiligheidsnalevingskwesties richt. Campaign Classic synchroniseert nu de regels, de uitzending en het suppressieadres van en naar de nieuwe aanwijsbaarheidsserver. De oude leverbaarheidsserver wordt op 31 augustus 2022 gedecomisseerd.

Als klant van het Campaign Classic, moet u de nieuwe leverbaarheidsserver **vóór 31 augustus, 2022** uitvoeren.

>[!NOTE]
>
>Voor meer vragen over deze veranderingen, verwijs naar [ Veelgestelde vragen ](#faq), of contacteer [ de Zorg van de Klant van de Adobe ](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) {_blank}.
>

## Wat is er veranderd?{#acc-deliverability-changes}

Adobe ontmantelt oudere gegevenscentra wegens veiligheidsnalevingsredenen. Adobe Campaign Classic-clients moeten migreren naar de nieuwe, op de Amazon Web Service (AWS) gehoste service.

Deze nieuwe server garandeert een hoge beschikbaarheid (99.9) &#x200B; en biedt veilige en geverifieerde eindpunten om campagnemeservers in staat te stellen de vereiste gegevens op te halen: in plaats van verbinding te maken met de database voor elk verzoek, slaat de nieuwe leverbaarbaarheidsserver de gegevens in cache om de aanvragen waar mogelijk te bedienen. Dit mechanisme verbetert de responstijd. &#x200B;

## Heb je invloed op?{#acc-deliverability-impacts}

Alle klanten worden beïnvloed en moeten aan [ Campagne v7.2.2 ](../../rn/using/latest-release.md#release-7-2-2) (of meer) bevorderen en hun milieu uitvoeren om van de nieuwe leverbaarheidsserver te profiteren.

## Hoe kan ik bijwerken?{#acc-deliverability-update}

Als a **ontvangen klant**, zal de Adobe met u werken om uw instantie(s) aan de nieuwere versie te bevorderen, en tot het project in Adobe Developer Console te leiden.

Als **op-gebouw/hybride klant**, moet u aan [ Campagne v7.2.2 ](../../rn/using/latest-release.md#release-7-2-2) (of meer) bevorderen om van de nieuwe leverbaarheidsserver te profiteren. Zodra alle instanties worden bevorderd, moet u [ de nieuwe integratie ](#implementation-steps) aan de server van de Adobe leverbaarheid uitvoeren, en een naadloze overgang verzekeren.

## Implementatiestappen {#implementation-steps}

>[!WARNING]
>
>Deze stappen dienen alleen te worden uitgevoerd voor Hybride en On-premise implementaties.

Als onderdeel van de nieuwe integratie van de leverbaarheidsserver, moet de Campagne met de Adobe Gedeelde Diensten via een op de Dienst van Identity Management (IMS) gebaseerde authentificatie communiceren. De aangewezen manier is de op Adobe Developer gebaseerde Token van de Gateway te gebruiken (ook genoemd Token van de Technische Rekening of Adobe IO JWT).

>[!AVAILABILITY]
>
> De referentie van de Rekening van de Dienst (JWT) wordt afgekeurd door Adobe, de integratie van de Campagne met de oplossingen van de Adobe en apps moet nu op server-aan-server referentie van OAuth vertrouwen. </br>
>
> * Als u binnenkomende integratie met Campagne hebt uitgevoerd, moet u uw Technische Rekening zoals die in [ wordt gedetailleerd deze documentatie ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank) migreren. De bestaande [ geloofsbrieven van de Rekening van de Dienst (JWT) ](../../integrations/using/oauth-technical-account.md) zullen tot 27 Januari, 2025 blijven werken. </br>
>
> * Als u uitgaande integratie hebt geïmplementeerd, zoals integratie met Campaign-Analytics of Experience Cloud Triggers, blijven ze tot 27 januari 2025 werken. Nochtans, vóór die datum, moet u uw milieu van de Campagne aan v7.4.1 bevorderen en uw Technische Rekening migreren aan Auth.

### Vereisten{#prerequisites}

Controleer uw instantieconfiguratie voordat u de implementatie start.

1. Open de clientconsole van Campagne en meld u als beheerder aan bij Adobe Campaign.
1. Blader naar **Beleid > Platform > Opties**.
1. Controleer of de waarde van de optie `DmRendering_cuid` is opgevuld.

   * Als de optie is gevuld, kunt u de implementatie starten.
   * Als geen waarde wordt gevuld, contacteer [&#128279;](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) {_blank} de Zorg van de Klant van de Adobe  om uw CUID te krijgen.

   Deze optie moet op al uw instanties van de Campagne (MKT, MID, RT, EXEC) met de correcte waarde worden ingevuld. Als hybride klant, bereik uit aan Adobe om de optie te hebben die op uw instanties MID, RT en EXEC wordt geplaatst.

Als klant op locatie moet u ook controleren of er een campagne **[!UICONTROL Product profile]** beschikbaar is voor uw organisatie. Volg onderstaande stappen om dit te doen:

1. Als Beheerder, verbind met [ Adobe Admin Console ](https://adminconsole.adobe.com/) {_blank}.
1. Heb toegang tot het **Product en de sectie van de Diensten** en controle **Adobe Campaign** is vermeld.
Als u niet **contact [ de Zorg van de Klant van de Adobe van 0&rbrace; Adobe Campaign ](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) {_blank} kunt zien om het toegevoegde te krijgen.**
1. Klik **Adobe Campaign** en selecteer uw Organisatie.
   **Voorzichtigheid**: Als u meer dan één organisatie hebt, zorg ervoor om correcte te selecteren. Leer meer over Organisaties [ in deze pagina ](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=nl-NL#ims-org-id) {_blank}.

1. Controleer of een **[!UICONTROL Product profile]** bestaat. Als dat niet het geval is, maakt u het. Voor deze **[!UICONTROL Product profile]** is geen toestemming vereist.


>[!CAUTION]
>
>Als klant op locatie, als een firewall aan uw zijde is geïmplementeerd, moet u deze URL `https://deliverability-service.adobe.io` toevoegen aan uw lijst van gewenste personen. [Meer informatie](../../installation/using/url-permissions.md).


### Stap 1: uw Adobe Developer-project maken/bijwerken {#adobe-io-project}

Als u verder wilt gaan met het configureren van uw Adobe Analytics-connector, opent u de Adobe Developer-console en maakt u uw OAuth Server-to-Server-project.

Verwijs naar [ deze pagina ](../../integrations/using/oauth-technical-account.md#oauth-service) voor de gedetailleerde documentatie.

### Stap 2: Voeg de projectgeloofsbrieven in Adobe Campaign toe {#add-credentials-campaign}

Volg de stappen die in [ worden gedetailleerd deze pagina ](../../integrations/using/oauth-technical-account.md#add-credentials) om uw OAuth projectgeloofsbrieven in Adobe Campaign toe te voegen.

### Stap 3: Valideer uw configuratie

Volg onderstaande stappen om te controleren of de integratie is gelukt:

1. Open de clientconsole en meld u aan bij Adobe Campaign.
1. Blader naar **Beleid > Productie > Technische werkschema&#39;s**.
1. Begin **vernieuwen voor leverability** (leverabilityUpdate) werkschema. Dit moet worden uitgevoerd op al uw campagneinstanties (MKT, MID, RT, EXEC). Als hybride klant, bereik uit aan Adobe om het werkschema op uw MID, RT en EXEC instanties opnieuw te hebben begonnen.
1. Logbestanden controleren: de workflow moet zonder fouten worden uitgevoerd.

>[!CAUTION]
>
>Na de update, moet het **zaadnetwerk van de Update voor Inbox Rendering (updateRenderingSeeds)** werkschema worden tegengehouden, aangezien het niet meer van toepassing zal zijn en zal ontbreken.

## Veelgestelde vragen {#faq}

### Wat is de tijdlijn voor de update?

De overgang naar de nieuwe leverbaarbaarheidsserver, die de toevoeging van deze verbeterde mogelijkheden en de versterking van de beveiliging mogelijk maakt, begint op 22 juli voor gehoste klanten (Campagne Managed Services). Alle gehoste klanten worden eind augustus bijgewerkt.

Op locatie en hybride klanten moeten binnen hetzelfde tijdsbestek overstappen.

### Wat gebeurt er als ik mijn omgeving niet opwaardeer?

Om het even welke instantie van de Campagne die niet tegen 31 Augustus wordt bevorderd zal niet meer met de server van de Leverbaarheid van de Campagne kunnen verbinden. Dientengevolge, verfrist **zich voor leverability** (leverabilityUpdate) werkschema zal ontbreken, en dit zal uw leverbaarheid beïnvloeden.

Als u uw milieu niet bevordert, zullen de e-mailmontages ophouden gesynchroniseerd (MX de regels van het Beheer, Binnenkomende E-mailregels, de regels van het Beheer van het Domein, en stuiterende kwalificatieregels). Dit kan in de loop der tijd invloed hebben op uw leverbaarheid. Als deze regels ingrijpend worden gewijzigd, moeten ze vanaf dit punt handmatig worden toegepast.

Voor instanties MKT, slechts wordt de [ Globale Lijst van de Onderdrukking ](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) beïnvloed.
