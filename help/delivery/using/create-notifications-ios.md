---
product: campaign
title: Een pushmelding maken voor iOS-apparaten
description: Meer informatie over het maken van pushmeldingen voor iOS
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 3%

---

# Meldingen maken voor iOS{#create-notifications-ios}

![](../../assets/common.svg)

In deze sectie worden de elementen beschreven die specifiek zijn voor de levering van iOS-berichten. Algemene concepten voor het maken van leveringen worden weergegeven in [deze sectie](steps-about-delivery-creation-steps.md).

Begin door een nieuwe levering te maken.

![](assets/nmac_delivery_1.png)

Volg onderstaande stappen om een pushmelding voor iOS-apparaten te maken:

1. Selecteer de leveringssjabloon **[!UICONTROL Deliver on iOS]**.

   ![](assets/nmac_delivery_ios_1.png)

1. Als u het doel van de melding wilt definiëren, klikt u op de koppeling **[!UICONTROL To]** en vervolgens op **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >Het gedetailleerde proces wanneer het selecteren van de doelpopulatie van een levering wordt voorgesteld in [deze sectie](steps-defining-the-target-population.md).
   >
   >Raadpleeg [deze sectie](about-personalization.md) voor meer informatie over het gebruik van verpersoonlijkingsvelden.
   >
   >Voor meer op de opneming van een zaadlijst, verwijs naar [Ongeveer zaadadressen](about-seed-addresses.md).

1. Selecteer **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, selecteer de service die relevant is voor uw mobiele toepassing (in dit geval Neotrips) en selecteer vervolgens de iOS-versie van de toepassing.

   ![](assets/nmac_delivery_ios_3.png)

1. Selecteer het berichttype: **[!UICONTROL Alert]**, **[!UICONTROL Badge]**, of **[!UICONTROL Alert and badge]** of **[!UICONTROL Silent Push]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >In de modus **Silent Push** kan een melding &quot;silent&quot; worden verzonden naar een mobiele toepassing. De gebruiker wordt niet op de hoogte gebracht van de aankomst van de melding. Deze wordt rechtstreeks naar de toepassing overgedragen.

1. Voer in het veld **[!UICONTROL Title]** het label in van de titel die u in het bericht wilt weergeven. Deze wordt alleen weergegeven in de lijst met meldingen die beschikbaar zijn in het meldingscentrum. In dit veld kunt u de waarde definiëren van de parameter **title** van de payload van de iOS-melding.

1. Als u de HTTP/2-connector gebruikt, kunt u een ondertitel (waarde van de parameter **subtitle** van de iOS-berichtlading) toevoegen. Zie [deze sectie](configuring-the-mobile-application.md).

1. Voer vervolgens de **[!UICONTROL Message]** en **[!UICONTROL Value of the badge]** in op basis van het gekozen berichttype.

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** en  **[!UICONTROL Alert and badge]** typedeclaraties kunt u de waarde van de badge wijzigen (het nummer boven het logo van de mobiele toepassing). Als u de badge wilt vernieuwen, hoeft u alleen 0 als waarde in te voeren. Als het veld leeg is, verandert de waarde van de badge niet.

1. Klik op het pictogram **[!UICONTROL Insert emoticon]** om emoticons in te voegen bij uw pushmelding. Als u de lijst met emoticonen wilt aanpassen, raadpleegt u [deze sectie](customizing-emoticon-list.md)

1. Met **[!UICONTROL Action button]** kunt u een label definiëren voor de actieknop die wordt weergegeven in de waarschuwingsberichten (**action_loc_key** veld van de payload). Als uw iOS-toepassing landinstellbare tekenreeksen beheert (**Localizable.strings**), voert u de bijbehorende sleutel in dit veld in. Als uw toepassing geen landinstellbare tekst beheert, voert u het label in dat u wilt zien op de actieknop. Raadpleeg de [documentatie van Apple](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) voor meer informatie over landinstellbare tekenreeksen.
1. Selecteer in het veld **[!UICONTROL Play a sound]** het geluid dat door de mobiele terminal moet worden afgespeeld wanneer het bericht wordt ontvangen.

   >[!NOTE]
   >
   >Geluiden moeten in de toepassing worden opgenomen en worden gedefinieerd wanneer de service wordt gemaakt. Zie [deze sectie](configuring-the-mobile-application.md#configuring-external-account-ios).

1. Voer in het veld **[!UICONTROL Application variables]** de waarde van elke variabele in. Met toepassingsvariabelen kunt u berichtgedrag definiëren: U kunt bijvoorbeeld een specifiek toepassingsscherm configureren dat moet worden weergegeven wanneer de gebruiker het bericht activeert.

   >[!NOTE]
   >
   >Toepassingsvariabelen moeten worden gedefinieerd in de code van de mobiele toepassing en moeten worden ingevoerd tijdens het maken van de service. Raadpleeg [deze sectie](configuring-the-mobile-application.md) voor meer informatie.

1. Zodra het bericht wordt gevormd, klik **[!UICONTROL Preview]** lusje om voorproef de bericht.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >De berichtstijl (banner of waarschuwing) wordt niet gedefinieerd in Adobe Campaign. Het hangt van de configuratie af die door de gebruiker in hun iOS montages wordt geselecteerd. In Adobe Campaign kunt u echter elk type berichtstijl bekijken. Klik op de pijl rechtsonder om van de ene stijl naar de andere te gaan.
   >
   >In de voorvertoning wordt de iOS 10-vormgeving gebruikt.

Als u een bewijs wilt verzenden en de uiteindelijke levering wilt verzenden, gebruikt u hetzelfde proces als voor e-mailleveringen.

Nadat u berichten hebt verzonden, kunt u de leveringen controleren en volgen. Raadpleeg deze secties voor meer informatie hierover:

* [Push notification quarantines](understanding-quarantine-management.md#push-notification-quarantines)
* [Een levering controleren](about-delivery-monitoring.md)
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)


## Een rijke melding voor iOS maken {#creating-ios-delivery}

Met iOS 10 of hoger is het mogelijk om rijke meldingen te genereren. Adobe Campaign kan meldingen verzenden met behulp van variabelen waarmee het apparaat een uitgebreide melding kan weergeven.

U moet nu een nieuwe levering maken en deze koppelen aan de mobiele toepassing die u hebt gemaakt.

1. Ga naar **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klik op **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Selecteer **[!UICONTROL Deliver on iOS (ios)]** in **[!UICONTROL Delivery template]** drop-down. Voeg een **[!UICONTROL Label]** aan uw levering toe.

1. Klik op **[!UICONTROL To]** om de doelpopulatie te definiëren. Standaard wordt de **[!UICONTROL Subscriber application]**-doeltoewijzing toegepast. Klik **[!UICONTROL Add]** om onze eerder gecreeerde dienst te selecteren.

   ![](assets/nmac_ios_9.png)

1. Selecteer **[!UICONTROL Target type]** in het venster **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** en klik **[!UICONTROL Next]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Service]** de eerder gemaakte service, selecteer vervolgens de toepassing die u als doel wilt instellen en klik op **[!UICONTROL Finish]**.
**[!UICONTROL Application variables]** worden automatisch toegevoegd afhankelijk van wat tijdens de configuratiestappen werd toegevoegd.

   ![](assets/nmac_ios_6.png)

1. Bewerk uw uitgebreide melding.

   ![](assets/nmac_ios_7.png)

1. Schakel het vakje **[!UICONTROL Mutable content]** in het meldingsvenster Bewerken in zodat de mobiele toepassing media-inhoud kan downloaden.

1. Klik **[!UICONTROL Save]** en verzend uw levering.

De afbeelding en webpagina moeten in de pushmelding worden weergegeven wanneer deze worden ontvangen op de mobiele iOS-apparaten van de abonnees.

![](assets/nmac_ios_8.png)
