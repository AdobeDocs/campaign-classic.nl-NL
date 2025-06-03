---
product: campaign
title: De levering configureren en verzenden
description: Leer hoe te vormen en de levering te verzenden
feature: Channel Configuration
role: User
hide: true
hidefromtoc: true
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '1517'
ht-degree: 3%

---

# De levering configureren en verzenden {#configuring-and-sending-the-delivery}

## Machtigingen{#delivery-permissions}

Alleen de eigenaar van de levering kan een levering starten. Andere operatoren (of groepen operatoren) kunnen pas een levering starten nadat ze als controleurs in het veld **[!UICONTROL Delivery start:]** zijn toegevoegd. [Meer informatie](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## Aanvullende parameters voor levering {#delivery-additiona-parameters}

Voordat u de levering verzendt, kunt u via het tabblad **[!UICONTROL Delivery]** de verzendende parameters in de leveringseigenschappen definiëren.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: gebruik deze optie om de verzendvolgorde voor uw leveringen te wijzigen door het prioriteitsniveau in te stellen op Normaal, Hoog of Laag.

* **[!UICONTROL Message batch quantity]**: gebruik deze optie om het aantal berichten te definiëren dat binnen hetzelfde XML-leveringspakket wordt gegroepeerd. Als de parameter op 0 wordt geplaatst, worden de berichten automatisch gegroepeerd. De pakketgrootte wordt gedefinieerd door de berekening `<delivery size>/1024` , met minimaal 8 en maximaal 256 berichten per pakket.

  >[!IMPORTANT]
  >
  >Wanneer de levering door bestaande wordt gecreeerd te dupliceren, wordt deze parameter teruggesteld.

* **[!UICONTROL Send using multiple waves]** : gebruik deze optie om uw berichten batchgewijs te verzenden in plaats van naar het gehele publiek tegelijk. [Meer informatie](#sending-using-multiple-waves).

* **[!UICONTROL Test SMTP delivery]**: gebruik deze optie om het verzenden via SMTP te testen. De levering wordt verwerkt tot verbinding aan de server SMTP maar niet verzonden: voor elke ontvanger van de levering, verbindt de Campagne met de SMTP leverancierserver, voert SMTP RCPT aan bevel uit, en sluit de verbinding vóór het bevel SMTP DATA.

  >[!NOTE]
  >
  >* Deze optie mag niet worden ingesteld in mid-sourcing.
  >
  >* Leer meer over SMTP serverconfiguratie, in [ deze sectie ](../../installation/using/configure-delivery-settings.md).

* **[!UICONTROL Email BCC]**: gebruik deze optie om e-mails op te slaan op een extern systeem via BCC door gewoon een BCC-e-mailadres toe te voegen aan uw berichtdoel. [Meer informatie](sending-messages.md#archiving-emails).

## Levering bevestigen {#confirming-delivery}

Wanneer de levering wordt gevormd en klaar om worden verzonden, voer de leveringsanalyse uit.

Klik hiertoe op **[!UICONTROL Send]** , selecteer de gewenste actie en klik op **[!UICONTROL Analyze]** . [Meer informatie](steps-validating-the-delivery.md#analyzing-the-delivery).

![](assets/s_ncs_user_email_del_send.png)

Klik eenmaal op **[!UICONTROL Confirm delivery]** om de levering van berichten te starten.

U kunt de leveringsassistent vervolgens sluiten en de uitvoering van de levering volgen vanaf het tabblad **[!UICONTROL Delivery]** , dat toegankelijk is via de details van deze levering of via de lijst met leveringen.

Nadat u berichten hebt verzonden, kunt u de leveringen controleren en volgen. Raadpleeg deze secties voor meer informatie hierover:

* [Een verzending controleren](about-delivery-monitoring.md)
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Berichttracking](about-message-tracking.md)

## De verzending van de levering plannen {#scheduling-the-delivery-sending}

U kunt het verzenden van het bericht uitstellen door de levering te plannen.

1. Klik op **[!UICONTROL Send]** en selecteer de optie **[!UICONTROL Postpone delivery]** .

1. Geef een begindatum op in het veld **[!UICONTROL Contact date]** .

![](assets/dlv_email_del_plan.png)

1. U kunt dan de leveringsanalyse beginnen, dan bevestig de levering verzendend. De verzending van de levering begint echter pas op de datum die in het veld **[!UICONTROL Contact date]** is opgegeven.

>[!IMPORTANT]
>
>Wanneer u met de analyse bent begonnen, is de contactdatum die u hebt bepaald vast. Als u deze datum wijzigt, moet u de analyse opnieuw beginnen zodat uw wijzigingen in overweging worden genomen.

![](assets/s_ncs_user_email_del_start_delayed.png)

In de leveringslijst wordt de levering weergegeven met de status **[!UICONTROL Pending]** .

![](assets/s_ncs_user_email_del_waiting.png)

Planning kan ook upstream worden geconfigureerd via de knop **[!UICONTROL Scheduling]** van de levering.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

U kunt de levering uitstellen tot een latere datum of de levering opslaan in de voorlopige kalender.

* Met de optie **[!UICONTROL Schedule delivery (no automatic execution)]** kunt u een voorlopige analyse van de levering plannen.

  Wanneer deze configuratie wordt opgeslagen, verandert de levering in **[!UICONTROL Targeting pending]** status. De analyse wordt op de opgegeven datum gestart.

* Met de optie **[!UICONTROL Schedule delivery (automatic execution on planned date)]** kunt u de leveringsdatum opgeven.

  Klik op **[!UICONTROL Send]** en selecteer **[!UICONTROL Postpone delivery]** . Start vervolgens de analyse en bevestig de levering. Wanneer de analyse volledig is, is het leveringsdoel klaar en de berichten zullen automatisch worden verzonden op de gespecificeerde datum.

Datums en tijden worden uitgedrukt in de tijdzone van de huidige operator. Met de vervolgkeuzelijst **[!UICONTROL Time zone]** onder het invoerveld voor de contactdatum kunt u de ingevoerde datum en tijd automatisch omzetten in de geselecteerde tijdzone.

Bijvoorbeeld, als u een levering plant die automatisch om 8 uur de tijd van Londen moet worden uitgevoerd, wordt de tijd automatisch omgezet in de geselecteerde tijdzone:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Verzenden met meerdere golven {#sending-using-multiple-waves}

Als u de lading in evenwicht wilt brengen, kunt u leveringen in verscheidene partijen verdelen. Configureer het aantal partijen en hun verhouding ten opzichte van de volledige levering.

>[!NOTE]
>
>U kunt alleen de grootte en de vertraging tussen twee opeenvolgende golven definiëren. De ontvankelijke selectiecriteria voor elke golf kunnen niet worden gevormd.

1. Open het venster met de leveringseigenschappen en klik op de tab **[!UICONTROL Delivery]** .
1. Selecteer de optie **[!UICONTROL Send using multiple waves]** en klik op de koppeling **[!UICONTROL Define waves...]** .

   ![](assets/s_ncs_user_wizard_waves.png)

1. Om golven te vormen, kunt u of:

   * Bepaal de grootte voor elke golf. Als u bijvoorbeeld **[!UICONTROL 30%]** invoert in het corresponderende veld, vertegenwoordigt elke golf 30% van de berichten die worden geleverd, behalve de laatste, die 10% van de berichten vertegenwoordigt.

     Geef in het veld **[!UICONTROL Period]** de vertraging op tussen het begin van twee opeenvolgende golven. Als u bijvoorbeeld **[!UICONTROL 2d]** invoert, wordt de eerste golf onmiddellijk gestart, de tweede golf begint over twee dagen, de derde golf over vier dagen enzovoort.

     ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Definieer een kalender voor het verzenden van elke golf.

     Geef in de kolom **[!UICONTROL Start]** de vertraging op tussen het begin van twee opeenvolgende golven. Voer in de kolom **[!UICONTROL Size]** een vast getal of een percentage in.

     In het volgende voorbeeld vertegenwoordigt de eerste golf 25% van het totale aantal berichten inbegrepen in de levering en zal onmiddellijk beginnen. De volgende twee golven voltooien de levering en zijn geplaatst om met intervallen van zes uur te beginnen.

     ![](assets/s_ncs_user_wizard_waves_create.png)

   Een specifieke typologieregel, **[!UICONTROL Wave scheduling check]** , zorgt ervoor dat de laatste golf vóór de geldigheidsgrens van de levering wordt gepland. De typologieën van de campagne en hun regels, die in het **[!UICONTROL Typology]** lusje van de leveringseigenschappen worden gevormd, worden voorgesteld in [ proces van de Bevestiging met typologieën ](steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >Zorg ervoor dat de laatste golven de leveringstermijn niet overschrijden, die is gedefinieerd op het tabblad **[!UICONTROL Validity]** . Anders kunnen sommige berichten niet worden verzonden.
   >
   >U moet ook genoeg tijd voor pogingen toestaan wanneer het vormen van de laatste golven. Zie [deze sectie](steps-sending-the-delivery.md#configuring-retries).

1. Ga naar de leveringslogboeken om uw verzendingen te controleren. Zie [deze pagina](delivery-dashboard.md#delivery-logs-and-history).

   U kunt de leveringen zien die reeds in de verwerkte golven (**[!UICONTROL Sent]** status) werden verzonden en de te verzenden leveringen in de resterende golven (**[!UICONTROL Pending]** status).

De twee onderstaande voorbeelden zijn de meest gebruikte voorbeelden voor het gebruik van meerdere golven.

* **tijdens op helling-up proces**

  Wanneer e-mails met een nieuw platform worden verzonden, zijn internetproviders (ISP&#39;s) verdacht van IP-adressen die niet worden herkend. Als er plotseling grote hoeveelheden e-mails worden verzonden, markeren de ISP&#39;s deze vaak als spam.

  Als u wilt voorkomen dat spam wordt gemarkeerd, kunt u het verzonden volume progressief verhogen met golven. Dit zou een vlotte ontwikkeling van de startfase moeten verzekeren en u toelaten om het algemene tarief van ongeldige adressen te verminderen.

  Gebruik hiervoor de optie **[!UICONTROL Schedule waves according to a calendar]** . Stel bijvoorbeeld de eerste golf in op 10%, de tweede op 15% enzovoort.

  ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Campagnes die een callcenter** impliceren

  Wanneer het leiden van een loyaliteitscampagne telefonisch, heeft uw organisatie een beperkte capaciteit om het aantal vraag te verwerken om abonnees te contacteren.

  Gebruikend golven, kunt u het aantal berichten tot 20 per dag beperken, bijvoorbeeld, gezien de dagelijkse verwerkingscapaciteit van een vraagcentrum.

  Selecteer hiervoor de optie **[!UICONTROL Schedule multiple waves of the same size]** . Voer **[!UICONTROL 20]** in als de grootte van de golf en **[!UICONTROL 1d]** in het veld **[!UICONTROL Period]** .

  ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Opnieuw proberen configureren {#configuring-retries}

Tijdelijk ongeleverde berichten toe te schrijven aan a **Zacht** of **Genegeerde** fout zijn onderworpen aan automatisch opnieuw proberen. De types en de redenen van de leveringsmislukking worden voorgesteld in deze [ sectie ](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Voor ontvangen of hybride installaties, als u aan [ Uitgebreide MTA ](sending-with-enhanced-mta.md) hebt bevorderd, worden de retry montages in de levering niet meer gebruikt door Campagne. De zachte stuitpogingen en de tijdsduur tussen hen worden bepaald door Verbeterde MTA gebaseerd op het type en de strengheid van de stuiteringsreacties die van het e-maildomein van het bericht terugkomen.

Voor on-premise installaties en ontvangen/hybride installaties die de erfenis MTA van de Campagne gebruiken, wijst de centrale sectie van het **[!UICONTROL Delivery]** lusje voor leveringsparameters erop hoeveel herpogingen de dag na de levering en de minimumvertraging tussen herpogingen zouden moeten worden uitgevoerd.

![](assets/s_ncs_user_wizard_retry_param.png)

Door gebrek, zijn vijf herpogingen gepland voor de eerste dag van de levering met een minimuminterval van één uur uitgespreid over de 24 uren van de dag. Elke dag opnieuw proberen wordt geprogrammeerd na die datum en tot de leveringstermijn, die is gedefinieerd op het tabblad **[!UICONTROL Validity]** . Zie [ bepalen de geldigheidsperiode ](#defining-validity-period).

## De geldigheidsperiode definiëren {#defining-validity-period}

Wanneer de levering is gestart, kunnen de berichten (en eventuele nieuwe pogingen) worden verzonden tot de leveringstermijn. Dit wordt aangegeven in de leveringseigenschappen, via het tabblad **[!UICONTROL Validity]** .

![](assets/s_ncs_user_email_del_valid_period.png)

* In het veld **[!UICONTROL Delivery duration]** kunt u de limiet voor algemene leveringspogingen invoeren. Dit betekent dat Adobe Campaign de berichten verzendt die op de begindatum beginnen, en dan, voor berichten die een fout slechts terugkeren, regelmatig, configureerbare herpogingen worden uitgevoerd tot de geldigheidsgrens wordt bereikt.

  U kunt ook datums opgeven. Selecteer **[!UICONTROL Explicitly set validity dates]** om dit te doen. In dit geval kunt u ook de tijd opgeven op basis van de uiterste datum voor levering en geldigheid. De huidige tijd wordt standaard gebruikt, maar u kunt deze rechtstreeks wijzigen in het invoerveld.

  >[!IMPORTANT]
  >
  >Voor ontvangen of hybride installaties, als u aan [ Verbeterde MTA ](sending-with-enhanced-mta.md) hebt bevorderd, zal het **[!UICONTROL Delivery duration]** plaatsen in uw e-mailleveringen van de Campagne slechts als reeks aan **3.5 dagen of minder** worden gebruikt. Als u een waarde definieert die hoger is dan 3,5 dagen, wordt hiermee geen rekening gehouden.

* **grens van de Geldigheid van middelen**: Het **[!UICONTROL Validity limit]** gebied wordt gebruikt voor geuploade middelen, hoofdzakelijk voor de spiegelpagina en beelden. De bronnen op deze pagina zijn gedurende een beperkte tijd geldig (om schijfruimte te besparen).

  De waarden op dit gebied kunnen in de eenheden worden uitgedrukt die in [ worden vermeld deze sectie ](../../platform/using/adobe-campaign-workspace.md#default-units).
