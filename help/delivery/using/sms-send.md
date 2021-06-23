---
product: campaign
title: SMS verzenden, controleren en volgen
description: Meer informatie over het verzenden, controleren en volgen van SMS in Campagne
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
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

De **[!UICONTROL Properties]** knoop geeft toegang tot de geavanceerde leveringsparameter. De parameters specifiek voor de levering van SMS zijn in **[!UICONTROL SMS parameters]** sectie van **[!UICONTROL Delivery]** tabel.

De volgende opties zijn beschikbaar:

* **Adres** afzender: Hiermee kunt u de naam van de afzender aanpassen met een reeks alfanumerieke tekens die zijn beperkt tot elf tekens. Het veld mag niet uitsluitend uit cijfers bestaan. U kunt een voorwaarde definiëren om bijvoorbeeld verschillende namen weer te geven op basis van de gebiedscode van de ontvanger:

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >Controleer de wet in je land met betrekking tot het bewerken van namen van afzenders. Vraag de operator ook of deze functionaliteit wordt aangeboden.

* **Transmissiemodus**: berichtenverzending door SMS.
* **Prioriteit**: het niveau van belang dat aan een boodschap wordt toegekend. **[!UICONTROL Normal]** De prioriteit wordt standaard geselecteerd. Vraag uw serviceprovider naar de kosten van SMS-berichten die met de prioriteit **[!UICONTROL High]** worden verzonden.
* **Type aanvraag**: Kies de toepassing die u aan uw SMS-levering wilt toewijzen. De optie **[!UICONTROL Direct Marketing]** is standaard geselecteerd en wordt het meest gebruikt.

**Parameters specifiek voor de NetSize-connector**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Gebruik verschillende SMS-berichten voor één bericht**: hiermee kunt u een bericht van meer dan 160 tekens verzenden via verschillende SMS-berichten.

**Parameters specifiek voor een schakelaar SMPP**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Maximum aantal SMS per bericht**: Met deze optie kunt u het aantal SMS instellen dat moet worden gebruikt om een bericht te verzenden. Als het aantal aan 0 wordt geplaatst, kunt u SMS gebruiken om uw bericht te leveren. Als het aantal SMS bijvoorbeeld op 1 of 2 wordt geplaatst, en het bericht deze drempel overschrijdt, zal het niet worden verzonden.

## SMS controleren en volgen {#monitoring-and-tracking-sms-deliveries}

Nadat u berichten hebt verzonden, kunt u de leveringen controleren en volgen. Raadpleeg deze secties voor meer informatie hierover:

* [Een verzending controleren](about-delivery-monitoring.md)
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Berichttracking](about-message-tracking.md)

## Binnenkomende berichten verwerken {#processing-inbound-messages}

De **nlserver sms** module vraagt de router van SMS met regelmatige intervallen. Op deze manier kan Adobe Campaign de voortgang van de leveringen volgen en de statusrapporten en aanvragen voor abonnementen bij ontvangers afhandelen.

* **Statusrapporten**: Bekijk leveringslogboeken om de status van uw berichten te controleren.

   >[!NOTE]
   >
   >Elk verzonden SMS-bericht is gekoppeld aan een externe account met de primaire sleutel. Zo:
   >
   > * Statusrapporten van een verwijderde externe SMS-account worden niet correct verwerkt.
   > * Een SMS-account kan alleen aan één externe account worden gekoppeld om ervoor te zorgen dat statusrapporten aan de juiste account worden toegewezen


* **Abonnement opzeggen**: ontvangers die de levering van SMS willen ophouden kunnen een bericht terugkeren dat het woord STOP bevat. Als uw leverancier het onder de voorwaarden van het contract toestaat, kunt u berichten via de **Inkomende SMS** werkschemaactiviteit terugwinnen en dan een vraag creëren om **niet meer deze ontvanger** optie voor de betrokken ontvangers toe te laten.

   Raadpleeg de handleiding [Workflows](../../workflow/using/architecture.md).

## InSMS-schema {#insms-schema}

Het InSMS-schema bevat relevante informatie over inkomende SMS. Een beschrijving van deze velden is beschikbaar via het desc-kenmerk.

* **bericht**: inhoud van het ontvangen SMS.
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
* **leveringsdatum**: datumbericht verzonden door SMSC (berichtcentrum).
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
>De volgende gedetailleerde procedure is slechts geldig voor schakelaars SMPP, behalve de uitgebreide generische schakelaar SMPP. Raadpleeg voor meer informatie de sectie [Een externe SMPP-account maken](sms-set-up.md#creating-an-smpp-external-account).
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

1. Geef voor het **name**-kenmerk van de **`<shortcode>`**-tag de korte code op die wordt weergegeven in de plaats van de naam van de berichtafzender.

   In elke **`<reply>`** markering, ga **sleutelwoord** attributen met een sleutelwoord en **text** attributen met het bericht in dat u voor dit sleutelwoord zou willen verzenden.

   >[!NOTE]
   >
   >Elk trefwoord moet in hoofdletters worden geschreven.

   Als u het zelfde bericht voor verscheidene sleutelwoorden wilt verzenden, dupliceer de overeenkomstige lijn.

   Bijvoorbeeld:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. Sla dit bestand op onder de naam **smsAutoReply.xml** als u klaar bent.

   De naam van het bestand is hoofdlettergevoelig in Linux.

1. Kopieer dit bestand naar de map **conf** in Adobe Campaign, op dezelfde plaats als de webserver.

>[!IMPORTANT]
>
>Dit soort automatische berichten houden geen geschiedenis bij. Daarom worden ze niet weergegeven in het leveringsdashboard. [Meer informatie](delivery-dashboard.md).
>
>Met deze berichten wordt in de regels inzake commerciële druk geen rekening gehouden. [Meer informatie](../../campaign/using/pressure-rules.md).
