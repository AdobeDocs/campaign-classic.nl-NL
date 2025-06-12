---
product: campaign
title: Informatie over leveringsinstellingen
description: Ontdek de specifieke v7-leveringsinstellingen
feature: Channel Configuration
role: User
hide: true
hidefromtoc: true
exl-id: 66250817-f829-4b8b-92dd-2daa92a97fe0
source-git-commit: d3d731c64cb5a430de6adac3aeb326f74134c436
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 2%

---

# Leveringsinstellingen {#about-delivery-settings}

De volgende instellingen gelden specifiek voor Campaign Classic. Voor andere leveringsmontages, verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html){target="_blank"}.

## Leveringsanalyse {#delivery-analysis}

### De prestaties van de leveringsanalyse verbeteren {#improving-delivery-analysis}

Als u de voorbereiding van de levering wilt versnellen, controleert u de optie **[!UICONTROL Prepare the delivery parts in the database]** voordat u de analyse start.

Wanneer deze optie wordt toegelaten, wordt de levering voorbereiding uitgevoerd direct binnen het gegevensbestand, dat de analyse kan beduidend versnellen.

Deze optie is momenteel alleen beschikbaar als aan de volgende voorwaarden is voldaan:

* De levering moet een e-mail zijn. De andere kanalen worden momenteel niet ondersteund.
* U moet niet midsourcing of extern verpletteren, slechts bulklevering gebruiken die type verplettert. U kunt de routering controleren die wordt gebruikt op het tabblad **[!UICONTROL General]** van **[!UICONTROL Delivery properties]** .
* U kunt geen populatie richten die uit een extern dossier komt. Voor één levering klikt u op de koppeling **[!UICONTROL To]** in de **[!UICONTROL Email parameters]** en controleert u of de optie **[!UICONTROL Defined in the database]** is geselecteerd. Voor een levering die in een workflow wordt gebruikt, controleert u of de ontvangers **[!UICONTROL Specified by the inbound event(s)]** op het tabblad **[!UICONTROL Delivery]** zijn.
* U moet een PostSQL-database gebruiken.

### De prioriteit van de analyse configureren {#analysis-priority-}

Wanneer de levering onderdeel is van een campagne, biedt het tabblad **[!UICONTROL Advanced]** een extra optie. Zo kunt u de verwerkingsvolgorde voor leveringen in dezelfde campagne ordenen.

Elke levering wordt geanalyseerd voordat deze wordt verzonden. De duur van de analyse is afhankelijk van het extractiebestand van de levering. Hoe groter de grootte van het bestand, des te langer de analyse duurt, waardoor de volgende leveringen wachten.

Met de opties voor de **[!UICONTROL Message preparation by the scheduler]** kunt u prioriteit geven aan de leveringsanalyse in een campagneworkflow.

![](assets/delivery_analysis_priority.png)

Als een levering te groot is, is het beter om een lage prioriteit aan het toe te wijzen om de analyse van andere werkschemaleveringen te vermijden vertragen.

>[!NOTE]
>
>Om ervoor te zorgen dat de grotere leveringsanalyses de vooruitgang van uw werkschema&#39;s niet vertragen, kunt u hun uitvoeringen plannen door **[!UICONTROL Schedule execution for a time of low activity]** te tikken.

## Aflevering {#delivery-sending}

### Opnieuw proberen configureren {#configuring-retries}

Tijdelijk ongeleverde berichten toe te schrijven aan a **Zacht** of **Genegeerde** fout zijn onderworpen aan automatisch opnieuw proberen. De types en de redenen van de leveringsmislukking worden voorgesteld in deze [ sectie ](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Voor ontvangen of hybride installaties, als u aan [ Uitgebreide MTA ](sending-with-enhanced-mta.md) hebt bevorderd, worden de retry montages in de levering niet meer gebruikt door Campagne. De zachte stuitpogingen en de tijdsduur tussen hen worden bepaald door Verbeterde MTA gebaseerd op het type en de strengheid van de stuiteringsreacties die van het e-maildomein van het bericht terugkomen.

Voor on-premise installaties en ontvangen/hybride installaties die de erfenis MTA van de Campagne gebruiken, wijst de centrale sectie van het **[!UICONTROL Delivery]** lusje voor leveringsparameters erop hoeveel herpogingen de dag na de levering en de minimumvertraging tussen herpogingen zouden moeten worden uitgevoerd.

![](assets/s_ncs_user_wizard_retry_param.png)

Door gebrek, zijn vijf herpogingen gepland voor de eerste dag van de levering met een minimuminterval van één uur uitgespreid over de 24 uren van de dag. Elke dag opnieuw proberen wordt geprogrammeerd na die datum en tot de leveringstermijn, die is gedefinieerd op het tabblad **[!UICONTROL Validity]** . Zie [ bepalen de geldigheidsperiode ](#defining-validity-period).

### De geldigheidsperiode definiëren {#defining-validity-period}

Wanneer de levering is gestart, kunnen de berichten (en eventuele nieuwe pogingen) worden verzonden tot de leveringstermijn. Dit wordt aangegeven in de leveringseigenschappen, via het tabblad **[!UICONTROL Validity]** .

![](assets/s_ncs_user_email_del_valid_period.png)

* In het veld **[!UICONTROL Delivery duration]** kunt u de limiet voor algemene leveringspogingen invoeren. Dit betekent dat Adobe Campaign de berichten verzendt die op de begindatum beginnen, en dan, voor berichten die een fout slechts terugkeren, regelmatig, configureerbare herpogingen worden uitgevoerd tot de geldigheidsgrens wordt bereikt.

  U kunt ook datums opgeven. Selecteer **[!UICONTROL Explicitly set validity dates]** om dit te doen. In dit geval kunt u ook de tijd opgeven op basis van de uiterste datum voor levering en geldigheid. De huidige tijd wordt standaard gebruikt, maar u kunt deze rechtstreeks wijzigen in het invoerveld.

  >[!IMPORTANT]
  >
  >Voor ontvangen of hybride installaties, als u aan [ Verbeterde MTA ](sending-with-enhanced-mta.md) hebt bevorderd, zal het **[!UICONTROL Delivery duration]** plaatsen in uw e-mailleveringen van de Campagne slechts als reeks aan **3.5 dagen of minder** worden gebruikt. Als u een waarde definieert die hoger is dan 3,5 dagen, wordt hiermee geen rekening gehouden.

* **grens van de Geldigheid van middelen**: Het **[!UICONTROL Validity limit]** gebied wordt gebruikt voor geuploade middelen, hoofdzakelijk voor de spiegelpagina en beelden. De bronnen op deze pagina zijn gedurende een beperkte tijd geldig (om schijfruimte te besparen).

  De waarden op dit gebied kunnen in de eenheden worden uitgedrukt die in [ worden vermeld deze sectie ](../../platform/using/adobe-campaign-workspace.md#default-units).
