---
product: campaign
title: SMS verzenden, controleren en volgen
description: Meer informatie over het verzenden, controleren en volgen van SMS in Campagne
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: SMS
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 3%

---

# SMS-leveringen verzenden, controleren en volgen{#sms-properties}



## SMS-berichten verzenden {#sending-sms-messages}

Om uw bericht goed te keuren en het naar de ontvangers van de levering te verzenden die wordt gecreeerd, klik **[!UICONTROL Send]**.

Het gedetailleerde proces voor het valideren en verzenden van een levering wordt in de volgende secties weergegeven:

* [De levering valideren](steps-validating-the-delivery.md)
* [De levering verzenden](steps-sending-the-delivery.md)

## Geavanceerde parameters {#advanced-parameters}

De **[!UICONTROL Properties]** de knoop geeft toegang tot de geavanceerde leveringsparameter. De parameters die specifiek zijn voor SMS-leveringen staan in de **[!UICONTROL SMS parameters]** van de **[!UICONTROL Delivery]** tab.

De volgende opties zijn beschikbaar:

* **Adres van afzender**: Hiermee kunt u de naam van de afzender aanpassen met een reeks alfanumerieke tekens die zijn beperkt tot elf tekens. Het veld mag niet uitsluitend uit cijfers bestaan. U kunt een voorwaarde definiëren om bijvoorbeeld verschillende namen weer te geven op basis van de gebiedscode van de ontvanger:

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >Controleer de wet in je land met betrekking tot het bewerken van namen van afzenders. Vraag de operator ook of deze functionaliteit wordt aangeboden.

* **Transmissiemodus**: berichtenverzending door SMS.
* **Prioriteit**: het niveau van belang dat aan een boodschap wordt toegekend. **[!UICONTROL Normal]** De prioriteit wordt standaard geselecteerd. Vraag uw serviceprovider naar de kosten van SMS-berichten die worden verzonden met **[!UICONTROL High]** prioriteit.
* **Type aanvraag**: Kies de toepassing die u aan uw SMS-levering wilt toewijzen. De **[!UICONTROL Direct Marketing]** Deze optie is standaard geselecteerd en wordt het meest gebruikt.

**Parameters specifiek voor de NetSize-connector**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Verschillende SMS gebruiken voor één bericht**: hiermee kunt u een bericht van meer dan 160 tekens verzenden via verschillende SMS-berichten.

**Parameters specifiek voor een schakelaar SMPP**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Maximum aantal SMS per bericht**: Met deze optie kunt u het aantal SMS instellen dat moet worden gebruikt om een bericht te verzenden. Als het aantal aan 0 wordt geplaatst, kunt u SMS gebruiken om uw bericht te leveren. Als het aantal SMS bijvoorbeeld op 1 of 2 wordt geplaatst, en het bericht deze drempel overschrijdt, zal het niet worden verzonden.

## SMS controleren en volgen {#monitoring-and-tracking-sms-deliveries}

Nadat u berichten hebt verzonden, kunt u de leveringen controleren en volgen. Raadpleeg deze secties voor meer informatie hierover:

* [Een verzending controleren](about-delivery-monitoring.md)
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Berichttracking](about-message-tracking.md)

## Binnenkomende berichten verwerken {#processing-inbound-messages}

De **nlserver-sms** de module vraagt de router van SMS met regelmatige intervallen. Op deze manier kan Adobe Campaign de voortgang van de leveringen volgen en de statusrapporten en aanvragen voor abonnementen bij ontvangers afhandelen.

* **Statusrapporten**: Bekijk leveringslogboeken om de status van uw berichten te controleren.

   >[!NOTE]
   >
   >Elk verzonden SMS-bericht is gekoppeld aan een externe account met de primaire sleutel. Zo:
   >
   > * Statusrapporten van een verwijderde externe SMS-account worden niet correct verwerkt.
   > * Een SMS-account kan alleen aan één externe account worden gekoppeld om ervoor te zorgen dat statusrapporten aan de juiste account worden toegewezen


* **Abonnement opzeggen**: ontvangers die de levering van SMS willen ophouden kunnen een bericht terugkeren dat het woord STOP bevat. Als uw leverancier dit toestaat onder de voorwaarden van het contract, kunt u berichten via **Binnenkomende SMS** workflowactiviteit en maak vervolgens een query om de **Neem geen contact meer op met deze ontvanger** voor de betrokken begunstigden.

   Zie de [Workflows](../../workflow/using/architecture.md) hulplijn.

## InSMS-schema {#insms-schema}

Het InSMS-schema bevat relevante informatie over inkomende SMS. Een beschrijving van deze velden is beschikbaar via het desc-kenmerk.

* **message**: inhoud van het ontvangen SMS.
* **oorsprong**: mobiel nummer bij de oorsprong van het bericht.
* **providerId**: Identificatiecode van het door het SMSC geretourneerde bericht (berichtcentrum).
* **gemaakt**: datum waarop het inkomende bericht in Adobe Campaign is ingevoegd.
* **extAccount**: Adobe Campaign externe account.

   >[!IMPORTANT]
   >
   >De volgende velden zijn specifiek voor NetSize.
   >
   >Als de gebruikte operator geen NetSize is, worden deze velden als leeg beschouwd.

* **alias**: alias van binnenkomend bericht.
* **scheidingsteken**: scheidingsteken tussen de alias en de hoofdtekst van het bericht.
* **messageDate**: berichtdatum gegeven door de exploitant.
* **receivalDate**: databericht van de exploitant is ontvangen door SMSC (berichtcentrum).
* **deliveryDate**: datumbericht verzonden door SMSC (berichtcentrum).
* **largeAccount**: de code van de klantenrekening verbonden aan inkomende SMS.
* **countryCode**: de landcode van de exploitant.
* **operatorCode**: netcode van de exploitant.
* **linkedSmsId**: Adobe Campaign-id (broadlogId) gekoppeld aan uitgaande SMS, waarbij dit SMS het antwoord is.

## Automatische antwoorden beheren (Amerikaanse regelgeving) {#managing-automatic-replies--american-regulation-}

Wanneer de abonnees op een bericht van SMS antwoorden dat werd verzonden naar hen via Adobe Campaign, en zij gebruiken een sleutelwoord zoals STOP, HELP, of JA, is het noodzakelijk, op de markt van de V.S., om berichten te vormen die automatisch zijn teruggekeerd.

Als ontvangers bijvoorbeeld het trefwoord STOP verzenden, ontvangen ze automatisch een bevestigingsbericht met de mededeling dat ze het abonnement hebben opgezegd.

De afzendernaam voor dit type van bericht is een korte code gewoonlijk wordt gebruikt om leveringen te verzenden.

>[!IMPORTANT]
>
>De volgende gedetailleerde procedure is slechts geldig voor schakelaars SMPP, behalve de uitgebreide generische schakelaar SMPP. Raadpleeg voor meer informatie de [Een SMPP-externe account maken](sms-set-up.md#creating-an-smpp-external-account) sectie.
>
>Het maakt deel uit van het certificeringsproces dat door Amerikaanse marktdeelnemers wordt uitgevoerd voor marketingcampagnes in de VS. Deze reacties op SMS-berichten van abonnees die het trefwoord bevatten, moeten onmiddellijk na ontvangst van een bericht van de abonnee worden teruggestuurd naar de abonnee.

1. Dit type XML-bestand maken:

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. Voor de **name** kenmerk van de **`<shortcode>`** -tag, geeft u de korte code op die wordt weergegeven in de plaats van de naam van de afzender van het bericht.

   In elke **`<reply>`** -tag, voert u de **trefwoord** kenmerk met een trefwoord en de **text** kenmerk met het bericht dat u voor dit trefwoord wilt verzenden.

   >[!NOTE]
   >
   >Elk trefwoord moet in hoofdletters worden geschreven.

   Als u het zelfde bericht voor verscheidene sleutelwoorden wilt verzenden, dupliceer de overeenkomstige lijn.

   Bijvoorbeeld:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. Sla dit bestand op onder de naam als u klaar bent **smsAutoReply.xml**.

   De naam van het bestand is hoofdlettergevoelig in Linux.

1. Kopieer dit bestand naar de **conf** in Adobe Campaign, op dezelfde plaats als de webserver.

>[!IMPORTANT]
>
>Dit soort automatische berichten houden geen geschiedenis bij. Daarom worden ze niet weergegeven in het leveringsdashboard. [Meer informatie](delivery-dashboard.md).
>
>Met deze berichten wordt in de regels inzake commerciële druk geen rekening gehouden. [Meer informatie](../../campaign-opt/using/pressure-rules.md).
