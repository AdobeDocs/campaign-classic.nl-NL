---
product: campaign
title: Een pushmelding maken voor iOS-apparaten
description: Meer informatie over het maken van pushmeldingen voor iOS
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Push
role: User, Developer, Data Engineer
exl-id: 4520504a-0d9f-4ea7-a5a8-0c07948af4f0
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 7%

---

# Meldingen maken voor iOS{#create-notifications-ios}

In deze sectie worden de specifieke elementen voor de levering van iOS-berichten beschreven. Algemene concepten voor het creëren van levering worden weergegeven in [deze sectie](steps-about-delivery-creation-steps.md).

Begin door een nieuwe levering te maken.

![](assets/nmac_delivery_1.png)

Voer de volgende stappen uit om een pushmelding voor iOS-apparaten te maken:

1. Selecteer de **[!UICONTROL Deliver on iOS]** leveringssjabloon.

   ![](assets/nmac_delivery_ios_1.png)

1. Als u het doel van het bericht wilt definiëren, klikt u op de knop **[!UICONTROL To]** koppeling en klik vervolgens op **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >Het gedetailleerde proces bij de selectie van de doelpopulatie van een levering wordt weergegeven in [deze sectie](steps-defining-the-target-population.md).
   >
   >Voor meer informatie over het gebruik van verpersoonlijkingsgebieden, verwijs naar [deze sectie](about-personalization.md).
   >
   >Raadpleeg voor meer informatie over het opnemen van een zaadlijst [Informatie over zaadadressen](about-seed-addresses.md).

1. Selecteren **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** Selecteer eerst de service die relevant is voor uw mobiele toepassing (in dit geval Neotrips) en selecteer vervolgens de iOS-versie van de toepassing.

   ![](assets/nmac_delivery_ios_3.png)

1. Kies uw **[!UICONTROL Notification type]** Tussen **[!UICONTROL General notification (Alert, Sound, Badge)]** of **[!UICONTROL Silent notification]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >De **Silent Push** in de modus kan een melding &quot;stil&quot; naar een mobiele toepassing worden verzonden. De gebruiker wordt niet op de hoogte gebracht van de aankomst van de melding. Deze wordt rechtstreeks naar de toepassing overgedragen.

1. In de **[!UICONTROL Title]** Voer in het veld het label in van de titel die u wilt weergeven in de lijst met meldingen die beschikbaar is in het meldingscentrum.

   In dit veld kunt u de waarde van de optie **titel** parameter van de iOS-berichtlading.

1. U kunt een **[!UICONTROL Subtitle]**, waarde van de ondertitelparameter van de iOS-berichtlading. Zie de [deze sectie](configuring-the-mobile-application.md).

1. Voer de inhoud van het bericht in het dialoogvenster **[!UICONTROL Message content]** van de wizard. Het gebruik van personalisatievelden wordt weergegeven in de [Over personalisatie](about-personalization.md) sectie.

   ![](assets/nmac_delivery_ios_5.png)

1. Klik op de knop **[!UICONTROL Insert emoticon]** pictogram om emoticons in te voegen in uw pushmelding. Als u de lijst met emoticonen wilt aanpassen, raadpleegt u [deze sectie](customizing-emoticon-list.md)

1. Van de **[!UICONTROL Sound and Badge]** kunt u de volgende opties bewerken:

   * **[!UICONTROL Clean Badge]**: schakel deze opties in om de waarde van de badge te vernieuwen.

   * **[!UICONTROL Value]**: stel een getal in dat wordt gebruikt om het aantal nieuwe ongelezen gegevens direct op het toepassingspictogram weer te geven.

   * **[!UICONTROL Critical alert mode]**: schakel deze optie in om geluid toe te voegen aan uw melding, zelfs als de telefoon van de gebruiker is ingesteld op de focusmodus of als de iPhone is gedempt.

   * **[!UICONTROL Name]**: selecteer het geluid dat door de mobiele terminal moet worden afgespeeld wanneer het bericht wordt ontvangen.

   * **[!UICONTROL Volume]**: volume van uw geluid van 0 tot 100.

   >[!NOTE]
   >
   >Geluiden moeten in de toepassing worden opgenomen en worden gedefinieerd wanneer de service wordt gemaakt. Zie [deze sectie](configuring-the-mobile-application.md#configuring-external-account-ios).

   ![](assets/nmac_delivery_ios_6.png)

1. Van de **[!UICONTROL Application variables]** tab, uw **[!UICONTROL Application variables]** automatisch worden toegevoegd. Met deze instructies kunt u bijvoorbeeld het berichtgedrag definiëren. U kunt dan een specifiek toepassingsscherm configureren dat wordt weergegeven wanneer de gebruiker het bericht activeert.

   Raadpleeg [deze sectie](configuring-the-mobile-application.md) voor meer informatie.

1. Van de **[!UICONTROL Advanced]** kunt u de volgende algemene opties bewerken:

   * **[!UICONTROL Mutable content]**: schakel deze optie in zodat de mobiele toepassing media-inhoud kan downloaden.

   * **[!UICONTROL Thread-id]**: ID die wordt gebruikt om gerelateerde meldingen te groeperen.

   * **[!UICONTROL Category]**: naam van de rubriek-id waarin de knoppen voor handelingen worden weergegeven. Met deze meldingen kan de gebruiker sneller verschillende taken uitvoeren als reactie op een melding zonder de applicatie te openen of erin te moeten navigeren.

   ![](assets/nmac_delivery_ios_7.png)

1. Voor meldingen met tijdgevoeligheid kunt u de volgende opties opgeven:

   * **[!UICONTROL Target content ID]**: id die wordt gebruikt om aan te geven welk toepassingsvenster moet worden verzonden wanneer de melding wordt geopend.

   * **[!UICONTROL Launch image]**: naam van het startafbeeldingsbestand dat moet worden weergegeven. Als de gebruiker ervoor kiest de toepassing te starten, wordt de geselecteerde afbeelding weergegeven in plaats van het startscherm van de toepassing.

   * **[!UICONTROL Interruption level]**:

      * **[!UICONTROL Active]**: Standaard ingesteld, geeft het systeem de melding direct weer, licht het scherm omhoog en kan een geluid worden afgespeeld. Meldingen doorbreken niet door de focusmodi.

      * **[!UICONTROL Passive]**: Het systeem voegt het bericht toe aan de meldingslijst zonder het scherm te belichten of een geluid af te spelen. Meldingen doorbreken niet door de focusmodi.

      * **[!UICONTROL Time sensitive]**: Het systeem presenteert de melding direct, licht het scherm op, kan een geluid afspelen en de modus Focus doorbreken. Voor dit niveau is geen speciale toestemming van Apple vereist.

      * **[!UICONTROL Critical]**: Het systeem presenteert de melding direct, licht het scherm op en laat de modi voor demtschakelaar of focus over. Voor dit niveau is een speciale machtiging van Apple vereist.

   * **[!UICONTROL Relevance score]**: stel een relevantiescore in van 0 tot 100. Het systeem gebruikt dit om de berichten in het berichtoverzicht te sorteren.

   ![](assets/nmac_delivery_ios_8.png)

1. Zodra het bericht wordt gevormd, klik **[!UICONTROL Preview]** om een voorvertoning van de melding weer te geven.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >De berichtstijl (banner of waarschuwing) wordt niet gedefinieerd in Adobe Campaign. Het hangt van de configuratie af die door de gebruiker in hun montages van iOS wordt geselecteerd. In Adobe Campaign kunt u echter elk type berichtstijl bekijken. Klik op de pijl rechtsonder om van de ene stijl naar de andere te gaan.
   >
   >In de voorvertoning wordt de iOS 10-look en -feel gebruikt.

Als u een bewijs wilt verzenden en de uiteindelijke levering wilt verzenden, gebruikt u hetzelfde proces als voor e-mailleveringen. [Meer informatie](steps-validating-the-delivery.md)

Nadat u berichten hebt verzonden, kunt u de leveringen controleren en volgen. Raadpleeg deze secties voor meer informatie hierover:

* [Push notification quarantines](understanding-quarantine-management.md#push-notification-quarantines)
* [Een levering controleren](about-delivery-monitoring.md)
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)

## Een rijke iOS-melding maken {#creating-ios-delivery}

Met iOS 10 of hoger is het mogelijk om rijke meldingen te genereren. Adobe Campaign kan meldingen verzenden met behulp van variabelen waarmee het apparaat een uitgebreide melding kan weergeven.

U moet nu een nieuwe levering maken en deze koppelen aan de mobiele toepassing die u hebt gemaakt.

1. Ga naar **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klik op **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecteren **[!UICONTROL Deliver on iOS (ios)]** in de **[!UICONTROL Delivery template]** vervolgkeuzelijst. Voeg een **[!UICONTROL Label]** op uw levering.

1. Klikken **[!UICONTROL To]** om de doelgroep te bepalen. Standaard worden de **[!UICONTROL Subscriber application]** doeltoewijzing wordt toegepast. Klikken **[!UICONTROL Add]** om onze eerder gemaakte service te selecteren.

   ![](assets/nmac_ios_9.png)

1. In de **[!UICONTROL Target type]** venster, selecteert u **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** en klik op **[!UICONTROL Next]**.

1. In de **[!UICONTROL Service]** vervolgkeuzelijst, selecteert u eerst de eerder gemaakte service en vervolgens de toepassing waarvoor u een toepassing wilt maken. Klik vervolgens op **[!UICONTROL Finish]**.

   ![](assets/nmac_ios_6.png)

1. Bewerk uw uitgebreide melding.

   ![](assets/nmac_ios_7.png)

1. Van de **[!UICONTROL Application variables]** tab, uw **[!UICONTROL Application variables]** worden automatisch toegevoegd afhankelijk van wat tijdens de configuratiestappen werd toegevoegd.

   >[!NOTE]
   >
   >Toepassingsvariabelen moeten worden gedefinieerd in de code van de mobiele toepassing en moeten worden ingevoerd tijdens het maken van de service. Raadpleeg [deze sectie](configuring-the-mobile-application.md) voor meer informatie.

   ![](assets/nmac_ios_10.png)

1. Van de **[!UICONTROL Advanced]** tabblad, controleert u de **[!UICONTROL Mutable content]** zodat de mobiele toepassing media-inhoud kan downloaden.

1. Klikken **[!UICONTROL Save]** en verzend uw levering.

De afbeelding en webpagina moeten in de pushmelding worden weergegeven wanneer deze worden ontvangen op de mobiele iOS-apparaten van de abonnees.

![](assets/nmac_ios_8.png)




