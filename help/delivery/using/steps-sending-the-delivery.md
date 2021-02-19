---
solution: Campaign Classic
product: campaign
title: De levering configureren en verzenden
description: De levering configureren en verzenden
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
translation-type: tm+mt
source-git-commit: 72fdac4afba6c786cfbd31f4a916b0539ad833e3
workflow-type: tm+mt
source-wordcount: '1521'
ht-degree: 5%

---


# De levering {#configuring-and-sending-the-delivery} configureren en verzenden

>[!NOTE]
>
>Alleen de eigenaar van de levering kan een levering starten. Als een andere operator (of operatorgroep) een levering wil starten, moet u deze als controleurs toevoegen in het veld **[!UICONTROL Delivery start:]**. Zie [deze sectie](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers) voor meer informatie.

## Aanvullende parameters voor levering {#delivery-additiona-parameters}

Alvorens de levering te verzenden, kunt u de verzendende parameters in de leveringseigenschappen, via **[!UICONTROL Delivery]** tabel bepalen.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: Met deze optie kunt u de verzendvolgorde voor uw leveringen beïnvloeden door hun prioriteitsniveau (normaal, hoog of laag) op te geven. Hierdoor kunt u de volgorde voor bepaalde, meer urgente leveringen voorrang geven boven andere.

* **[!UICONTROL Message batch quantity]**: Met deze optie kunt u het aantal berichten definiëren dat is gegroepeerd binnen hetzelfde XML-leveringspakket. Als de parameter op 0 wordt geplaatst, worden de berichten automatisch gegroepeerd. De pakketgrootte wordt gedefinieerd door de berekening `<delivery size>/1024`, met minimaal 8 en maximaal 256 berichten per pakket.

   >[!IMPORTANT]
   >
   >Wanneer de levering wordt gedupliceerd, wordt de parameter opnieuw ingesteld.

* **[!UICONTROL Send using multiple waves]**: Raadpleeg  [Verzenden met meerdere golven](#sending-using-multiple-waves) voor meer informatie.

* **[!UICONTROL Test SMTP delivery]**: Deze optie staat u toe om het verzenden van een levering via SMTP te testen. De levering wordt verwerkt tot verbinding aan de server SMTP maar niet verzonden.

   >[!NOTE]
   >
   >Het wordt niet aangeraden deze optie te gebruiken wanneer u medio-sourcing gebruikt om mta niet aan te roepen. Voor meer bij het vormen van een server SMTP, verwijs [naar deze sectie](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

* **[!UICONTROL Email BCC]**: Met deze optie kunt u e-mailberichten op een extern systeem opslaan via BCC door eenvoudig een BCC-e-mailadres toe te voegen aan uw berichtdoel. Raadpleeg [deze sectie](../../delivery/using/sending-messages.md#archiving-emails) voor meer informatie.

## Levering {#confirming-delivery} bevestigen

Wanneer de levering wordt gevormd en klaar om worden verzonden, zorg ervoor u de leveringsanalyse in werking hebt gesteld.

Om dit te doen, klik **[!UICONTROL Send]**, selecteer de gewenste actie en klik **[!UICONTROL Analyze]**. Zie [De analyse starten](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery) voor meer informatie.

![](assets/s_ncs_user_email_del_send.png)

Klik eenmaal op **[!UICONTROL Confirm delivery]** om de levering van berichten te starten.

U kunt de leveringstovenaar dan sluiten en de uitvoering van de levering van het **[!UICONTROL Delivery]** lusje volgen, dat via de details van deze levering of via de lijst van leveringen toegankelijk is.

Nadat u berichten hebt verzonden, kunt u de leveringen controleren en volgen. Raadpleeg deze secties voor meer informatie hierover:

* [Een levering controleren](../../delivery/using/about-delivery-monitoring.md)
* [Leveringsfouten begrijpen](../../delivery/using/understanding-delivery-failures.md)
* [Berichttracering](../../delivery/using/about-message-tracking.md)

## Het plannen van de levering verzendend {#scheduling-the-delivery-sending}

U kunt de levering van berichten uitstellen om de levering te plannen of om de salesdruk te beheren en te voorkomen dat een populatie overbevraagd wordt.

1. Klik op de knop **[!UICONTROL Send]** en selecteer de optie **[!UICONTROL Postpone delivery]**.

1. Geef een begindatum op in het veld **[!UICONTROL Contact date]**.

![](assets/dlv_email_del_plan.png)

1. U kunt dan de leveringsanalyse beginnen, dan bevestig de levering verzendend. De verzending van de levering begint echter pas op de datum die in het veld **[!UICONTROL Contact date]** is opgegeven.

>[!IMPORTANT]
>
>Wanneer u met de analyse bent begonnen, is de contactdatum die u hebt bepaald vast. Als u deze datum wijzigt, moet u de analyse opnieuw starten, zodat rekening wordt gehouden met uw wijzigingen.

![](assets/s_ncs_user_email_del_start_delayed.png)

In de leveringslijst, zal de levering met status **[!UICONTROL Pending]** verschijnen.

![](assets/s_ncs_user_email_del_waiting.png)

De planning kan ook upstream via de **[!UICONTROL Scheduling]** knoop van de levering worden gevormd.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

U kunt de levering uitstellen tot een latere datum of de levering opslaan in de voorlopige kalender.

* Met de optie **[!UICONTROL Schedule delivery (no automatic execution)]** kunt u een voorlopige analyse van de levering plannen.

   Wanneer deze configuratie wordt bewaard, verandert de levering in **[!UICONTROL Targeting pending]** status. De analyse wordt op de opgegeven datum gestart.

* Met de optie **[!UICONTROL Schedule delivery (automatic execution on planned date)]** kunt u de leveringsdatum opgeven.

   Klik op **[!UICONTROL Send]** en selecteer **[!UICONTROL Postpone delivery]** en start vervolgens de analyse en bevestig de levering. Wanneer de analyse volledig is, is het leveringsdoel klaar en de berichten zullen automatisch worden verzonden op de gespecificeerde datum.

Datums en tijden worden uitgedrukt in de tijdzone van de huidige operator. Met de vervolgkeuzelijst **[!UICONTROL Time zone]** onder het invoerveld voor de contactdatum kunt u de ingevoerde datum en tijd automatisch omzetten in de geselecteerde tijdzone.

Bijvoorbeeld, als u een levering plant die automatisch om 8 uur de tijd van Londen moet worden uitgevoerd, wordt de tijd automatisch omgezet in de geselecteerde tijdzone:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Verzenden met meerdere golven {#sending-using-multiple-waves}

Als u de lading in evenwicht wilt brengen, kunt u leveringen in verscheidene partijen verdelen. Configureer het aantal partijen en hun verhouding ten opzichte van de volledige levering.

>[!NOTE]
>
>U kunt alleen de grootte en de vertraging tussen twee opeenvolgende golven definiëren. De ontvankelijke selectiecriteria voor elke golf kunnen niet worden gevormd.

1. Open het venster met leveringseigenschappen en klik op het tabblad **[!UICONTROL Delivery]**.
1. Selecteer de optie **[!UICONTROL Send using multiple waves]** en klik op de koppeling **[!UICONTROL Define waves...]**.

   ![](assets/s_ncs_user_wizard_waves.png)

1. Om golven te vormen, kunt u of:

   * Bepaal de grootte voor elke golf. Bijvoorbeeld, als u **[!UICONTROL 30%]** op het overeenkomstige gebied ingaat, zal elke golf 30% van de berichten vertegenwoordigen inbegrepen in de levering, behalve laatste, die 10% van de berichten zal vertegenwoordigen.

      Geef in het veld **[!UICONTROL Period]** de vertraging op tussen het begin van twee opeenvolgende golven. Als u bijvoorbeeld **[!UICONTROL 2d]** invoert, wordt de eerste golf onmiddellijk gestart, de tweede golf begint over twee dagen, de derde golf over vier dagen enzovoort.

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Definieer een kalender voor het verzenden van elke golf.

      Geef in de kolom **[!UICONTROL Start]** de vertraging op tussen het begin van twee opeenvolgende golven. Voer in de kolom **[!UICONTROL Size]** een vast getal of een percentage in.

      In het volgende voorbeeld vertegenwoordigt de eerste golf 25% van het totale aantal berichten inbegrepen in de levering en zal onmiddellijk beginnen. De volgende twee golven voltooien de levering en zijn geplaatst om met intervallen van zes uur te beginnen.

      ![](assets/s_ncs_user_wizard_waves_create.png)
   Een specifieke typologieregel, **[!UICONTROL Wave scheduling check]**, zorgt ervoor dat de laatste golf vóór de grens van de leveringsgeldigheid wordt gepland. De typologieën van de campagne en hun regels, die op het **[!UICONTROL Typology]** lusje van de leveringseigenschappen worden gevormd, worden voorgesteld in [Validatieproces met typologieën](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >Zorg ervoor de laatste golven niet de leveringsdeadline overschrijden, die in **[!UICONTROL Validity]** tabel wordt bepaald. Anders kunnen sommige berichten niet worden verzonden.
   >
   >U moet ook genoeg tijd voor pogingen toestaan wanneer het vormen van de laatste golven. Zie [deze sectie](../../delivery/using/steps-sending-the-delivery.md#configuring-retries).

1. Ga naar de leveringslogboeken om uw verzendingen te controleren. Zie [deze pagina](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

   U kunt de leveringen zien die reeds in de verwerkte golven (**[!UICONTROL Sent]** status) werden verzonden en de leveringen die in de resterende golven (**[!UICONTROL Pending]** status) moeten worden verzonden.

De twee onderstaande voorbeelden zijn de meest gebruikte voorbeelden voor het gebruik van meerdere golven.

* **Tijdens het opvoerproces**

   Wanneer e-mails met een nieuw platform worden verzonden, zijn internetproviders (ISP&#39;s) verdacht van IP-adressen die niet worden herkend. Als er plotseling grote hoeveelheden e-mails worden verzonden, markeren de ISP&#39;s deze vaak als spam.

   Als u wilt voorkomen dat spam wordt gemarkeerd, kunt u het verzonden volume progressief verhogen met golven. Dit zou een vlotte ontwikkeling van de startfase moeten verzekeren en u toelaten om het algemene tarief van ongeldige adressen te verminderen.

   Gebruik hiervoor de optie **[!UICONTROL Schedule waves according to a calendar]**. Stel bijvoorbeeld de eerste golf in op 10%, de tweede op 15% enzovoort.

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Campagnes die een callcenter impliceren**

   Wanneer het leiden van een campagne van de telefoonloyaliteit, heeft uw organisatie een beperkte capaciteit om het aantal vraag te verwerken om abonnees te contacteren.

   Gebruikend golven, kunt u het aantal berichten tot 20 per dag beperken, die de dagelijkse verwerkingscapaciteit van een vraagcentrum is.

   Selecteer de optie **[!UICONTROL Schedule multiple waves of the same size]** om dit te doen. Typ **[!UICONTROL 20]** als de grootte van de golf en **[!UICONTROL 1d]** in het veld **[!UICONTROL Period]**.

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Opnieuw proberen {#configuring-retries} configureren

Tijdelijk niet-geleverde berichten als gevolg van een fout **Soft** of **Genegeerde** worden automatisch opnieuw geprobeerd. De types en de redenen van de leveringsmislukking worden voorgesteld in dit [sectie](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Voor gehoste of hybride installaties, als u aan [Verbeterde MTA](../../delivery/using/sending-with-enhanced-mta.md) hebt bevorderd, worden de heruitzettingsmontages in de levering niet meer gebruikt door Campagne. De zachte stuitpogingen en de tijdsduur tussen hen worden bepaald door Verbeterde MTA gebaseerd op het type en de strengheid van de stuiteringsreacties die van het e-maildomein van het bericht terugkomen.

Voor installaties op locatie en gehoste/hybride installaties die gebruikmaken van de oude Campagne MTA, geeft het centrale gedeelte van het tabblad **[!UICONTROL Delivery]** voor leveringsparameters aan hoeveel pogingen de dag na de levering moeten worden uitgevoerd en hoeveel vertraging er minimaal is tussen pogingen.

![](assets/s_ncs_user_wizard_retry_param.png)

Door gebrek, zijn vijf herpogingen gepland voor de eerste dag van de levering met een minimuminterval van één uur uitgespreid over de 24 uren van de dag. Elke dag opnieuw proberen wordt geprogrammeerd na dat en tot de leveringsdeadline, die in **[!UICONTROL Validity]** tabel (zie [Geldigheidsperiode bepalen](#defining-validity-period)) wordt bepaald.

## Geldigheidsperiode {#defining-validity-period} definiëren

Wanneer de levering is gestart, kunnen de berichten (en eventuele nieuwe pogingen) worden verzonden tot de leveringstermijn. Dit wordt vermeld in de leveringseigenschappen, via **[!UICONTROL Validity]** tabel.

![](assets/s_ncs_user_email_del_valid_period.png)

* In het veld **[!UICONTROL Delivery duration]** kunt u de limiet voor algemene leveringspogingen invoeren. Dit betekent dat Adobe Campaign de berichten verzendt die op de begindatum beginnen, en dan, voor berichten die een fout slechts terugkeren, regelmatig, configureerbare herpogingen worden uitgevoerd tot de geldigheidsgrens wordt bereikt.

   U kunt ook datums opgeven. Selecteer **[!UICONTROL Explicitly set validity dates]** om dit te doen. In dit geval kunt u ook de tijd opgeven op basis van de uiterste datum voor levering en geldigheid. De huidige tijd wordt standaard gebruikt, maar u kunt deze rechtstreeks wijzigen in het invoerveld.

   >[!IMPORTANT]
   >
   >Als u voor gehoste of hybride installaties een upgrade hebt uitgevoerd naar [Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md), wordt de **[!UICONTROL Delivery duration]**-instelling in uw e-mailleveringen voor campagne alleen gebruikt als deze is ingesteld op **3,5 dagen of minder**. Als u een waarde definieert die hoger is dan 3,5 dagen, wordt hiermee geen rekening gehouden.

* **Geldigheidslimiet van middelen**: Het  **[!UICONTROL Validity limit]** veld wordt gebruikt voor geüploade bronnen, voornamelijk voor de spiegelpagina en afbeeldingen. De bronnen op deze pagina zijn gedurende een beperkte tijd geldig (om schijfruimte te besparen).

   De waarden in dit veld kunnen worden uitgedrukt in de eenheden in [dit deel](../../platform/using/adobe-campaign-workspace.md#default-units).
