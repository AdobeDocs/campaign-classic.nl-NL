---
product: campaign
title: SMS verzenden, controleren en volgen
description: Meer informatie over het verzenden, controleren en volgen van SMS in Campagne
feature: SMS
role: User
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: 41296a0acaee93d31874bf58287e51085c6c1261
workflow-type: tm+mt
source-wordcount: '962'
ht-degree: 3%

---

# SMS-leveringen verzenden, controleren en volgen{#sms-properties}

## SMS-berichten verzenden {#sending-sms-messages}

Klik op **[!UICONTROL Send]** als u uw bericht wilt goedkeuren en verzenden naar de ontvangers van de levering die wordt gemaakt.

Het gedetailleerde proces voor het valideren en verzenden van een levering wordt in de volgende secties weergegeven:

* [De levering valideren](steps-validating-the-delivery.md)
* [De levering verzenden](steps-sending-the-delivery.md)

## Geavanceerde parameters {#advanced-parameters}

Met de knop **[!UICONTROL Properties]** hebt u toegang tot de geavanceerde leveringsparameter. De parameters die specifiek zijn voor SMS-leveringen staan in de sectie **[!UICONTROL SMS parameters]** van het tabblad **[!UICONTROL Delivery]** .

De volgende opties zijn beschikbaar:

* **adres van de Afzender**: laat u de naam van de leveringsafzender personaliseren gebruikend een koord van alfanumerieke karakters die tot elf karakters worden beperkt. Het veld mag niet uitsluitend uit cijfers bestaan. U kunt een voorwaarde definiëren om bijvoorbeeld verschillende namen weer te geven op basis van de gebiedscode van de ontvanger:

  ```
  <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
  ```

  >[!IMPORTANT]
  >
  >Controleer de wet in je land met betrekking tot het bewerken van namen van afzenders. Vraag de operator ook of deze functionaliteit wordt aangeboden.

* **wijze van de Transmissie**: berichttransmissie door SMS.
* **Prioriteit**: niveau van belang dat aan een bericht wordt toegewezen. **[!UICONTROL Normal]** -prioriteit is standaard geselecteerd. Vraag uw serviceprovider naar de kosten van SMS-berichten die met **[!UICONTROL High]** prioriteit zijn verzonden.
* **Type van toepassing**: kies de toepassing u wenst om aan uw levering van SMS toe te wijzen. De optie **[!UICONTROL Direct Marketing]** is standaard geselecteerd en wordt het meest gebruikt.

**Parameters specifiek voor de schakelaar NetSize**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Gebruik verscheidene SMS voor één enkel bericht**: dit laat u een bericht meer dan 160 karakters lang via verscheidene berichten van SMS verzenden.

**Parameters specifiek voor een schakelaar SMPP**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Maximum aantal SMS per bericht**: deze optie laat u het aantal SMS plaatsen om een bericht te verzenden. Als het aantal aan 0 wordt geplaatst, kunt u SMS gebruiken om uw bericht te leveren. Als het aantal SMS bijvoorbeeld op 1 of 2 wordt geplaatst, en het bericht deze drempel overschrijdt, zal het niet worden verzonden.

## SMS controleren en volgen {#monitoring-and-tracking-sms-deliveries}

Nadat u berichten hebt verzonden, kunt u de leveringen controleren en volgen. Raadpleeg deze secties voor meer informatie hierover:

* [Een verzending controleren](about-delivery-monitoring.md)
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Berichttracking](about-message-tracking.md)

## Binnenkomende berichten verwerken {#processing-inbound-messages}

De **nlserver sms** module vraagt de router van SMS met regelmatige intervallen. Op deze manier kan Adobe Campaign de voortgang van de leveringen volgen en de statusrapporten en aanvragen voor abonnementen bij ontvangers afhandelen.

* **de rapporten van de Status**: de logboeken van de meningslevering om het statuut van uw berichten te controleren.

  >[!NOTE]
  >
  >Elk verzonden SMS-bericht is gekoppeld aan een externe account met de primaire sleutel. Op deze manier:
  >
  > * Statusrapporten van een verwijderde externe SMS-account worden niet correct verwerkt.
  > * Een SMS-account kan alleen aan één externe account worden gekoppeld om ervoor te zorgen dat statusrapporten aan de juiste account worden toegewezen

* **Unsubscription**: de ontvangers die willen ophouden ontvangend de leveringen van SMS kunnen een bericht terugkeren die het woord STOP bevatten. Als uw leverancier het onder de voorwaarden van het contract toestaat, kunt u berichten via de **Binnenkomende het werkschemaactiviteit van SMS** terugwinnen en dan een vraag creëren om **toe te laten niet meer deze ontvankelijke** optie voor de betrokken ontvangers contacteren.

  Verwijs naar de [ gids van de Werkschema&#39;s ](../../workflow/using/architecture.md).

## InSMS-schema {#insms-schema}

Het InSMS-schema bevat relevante informatie over inkomende SMS. Een beschrijving van deze velden is beschikbaar via het desc-kenmerk.

* **bericht**: inhoud van ontvangen SMS.
* **oorsprong**: mobiel aantal bij de oorsprong van bericht.
* **providerId**: herkenningsteken van het bericht dat door SMSC (berichtcentrum) is teruggekeerd.
* **gecreeerd**: datum het inkomende bericht werd opgenomen in Adobe Campaign.
* **extAccount**: Externe rekening van Adobe Campaign.

  >[!IMPORTANT]
  >
  >De volgende velden zijn specifiek voor NetSize.
  >
  >Als de gebruikte operator geen NetSize is, worden deze velden als leeg beschouwd.

* **alias**: alias van inkomend bericht.
* **separator**: separator tussen alias en het lichaam van het bericht.
* **messageDate**: berichtdatum die door exploitant wordt gegeven.
* **receivalDate**: datumbericht van exploitant werd ontvangen door SMSC (berichtcentrum).
* **deliveryDate**: datumbericht dat door SMSC (berichtcentrum) wordt verzonden.
* **largeAccount**: de code van de klantenrekening verbonden met inkomende SMS.
* **countryCode**: de code van het exploitantland.
* **operatorCode**: de code van het exploitantnetwerk.
* **linkedSmsId**: Het herkenningsteken van Adobe Campaign (broadlogId) verbonden aan uitgaande SMS, waar dit SMS de reactie is.

## Automatische antwoorden beheren (Amerikaanse regelgeving) {#managing-automatic-replies--american-regulation-}

Wanneer de abonnees op een bericht van SMS antwoorden dat werd verzonden naar hen via Adobe Campaign, en zij gebruiken een sleutelwoord zoals STOP, HELP, of JA, is het noodzakelijk, op de markt van de V.S., om berichten te vormen die automatisch zijn teruggekeerd.

Als ontvangers bijvoorbeeld het trefwoord STOP verzenden, ontvangen ze automatisch een bevestigingsbericht met de mededeling dat ze het abonnement hebben opgezegd.

De afzendernaam voor dit type van bericht is een korte code gewoonlijk wordt gebruikt om leveringen te verzenden.

>[!IMPORTANT]
>
>De volgende gedetailleerde procedure is slechts geldig voor schakelaars SMPP, behalve de uitgebreide generische schakelaar SMPP. Voor meer op dit, verwijs naar [ creeer een externe rekening SMPP ](sms-set-up.md#creating-an-smpp-external-account) sectie.
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

1. Voor het **naam** attribuut van de **`<shortcode>`** markering, specificeer de korte code die in de plaats van de naam van de berichtafzender zal worden getoond.

   In elke **`<reply>`** markering, ga het **sleutelwoord** attribuut met een sleutelwoord en het **tekst** attribuut met het bericht in dat u voor dit sleutelwoord zou willen verzenden.

   >[!NOTE]
   >
   >Elk trefwoord moet in hoofdletters worden geschreven.

   Als u het zelfde bericht voor verscheidene sleutelwoorden wilt verzenden, dupliceer de overeenkomstige lijn.

   Bijvoorbeeld:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. Zodra voltooid, bewaar dit dossier onder de naam **smsAutoReply.xml**.

   De naam van het bestand is hoofdlettergevoelig in Linux.

1. Kopieer dit dossier in de **conf** folder in Adobe Campaign, bij de zelfde plaats zoals de server van het Web.

>[!IMPORTANT]
>
>Dit soort automatische berichten houden geen geschiedenis bij. Daarom worden ze niet weergegeven in het leveringsdashboard. [Meer informatie](delivery-dashboard.md).
>
>Met deze berichten wordt in de regels inzake commerciële druk geen rekening gehouden. [Meer informatie](../../campaign-opt/using/pressure-rules.md).
