---
product: campaign
title: De levering configureren en verzenden
description: Leer hoe te vormen en de levering te verzenden
feature: Channel Configuration
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 5%

---

# De levering configureren en verzenden {#configuring-and-sending-the-delivery}

![](../../assets/common.svg)

>[!NOTE]
>
>Alleen de eigenaar van de levering kan een levering starten. Als een andere operator (of een operatorgroep) een levering wil starten, moet u deze als controleurs toevoegen in het dialoogvenster **[!UICONTROL Delivery start:]** veld. Zie voor meer informatie [deze sectie](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## Aanvullende parameters voor levering {#delivery-additiona-parameters}

Voordat u de levering verzendt, kunt u de verzendende parameters in de leveringseigenschappen definiëren via de **[!UICONTROL Delivery]** tab.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: Met deze optie kunt u de verzendvolgorde voor uw leveringen beïnvloeden door hun prioriteitsniveau (normaal, hoog of laag) op te geven. Hierdoor kunt u de volgorde voor bepaalde, meer urgente leveringen voorrang geven boven andere.

* **[!UICONTROL Message batch quantity]**: Met deze optie kunt u het aantal berichten definiëren dat is gegroepeerd binnen hetzelfde XML-leveringspakket. Als de parameter op 0 wordt geplaatst, worden de berichten automatisch gegroepeerd. De pakketgrootte wordt gedefinieerd door de berekening `<delivery size>/1024`, met minimaal 8 en maximaal 256 berichten per pakket.

   >[!IMPORTANT]
   >
   >Wanneer de levering wordt gedupliceerd, wordt de parameter opnieuw ingesteld.

* **[!UICONTROL Send using multiple waves]**: Raadpleeg voor meer informatie hierover [Verzenden met meerdere golven](#sending-using-multiple-waves).

* **[!UICONTROL Test SMTP delivery]**: Deze optie staat u toe om het verzenden van een levering via SMTP te testen. De levering wordt verwerkt tot verbinding aan de server SMTP maar niet verzonden.

   >[!NOTE]
   >
   >Het wordt niet aangeraden deze optie te gebruiken wanneer u medio-sourcing gebruikt om mta niet aan te roepen. Voor meer bij het vormen van een server SMTP, verwijs [aan deze sectie](../../installation/using/configure-delivery-settings.md).

* **[!UICONTROL Email BCC]**: Met deze optie kunt u e-mailberichten op een extern systeem opslaan via BCC door eenvoudig een BCC-e-mailadres toe te voegen aan uw berichtdoel. Raadpleeg [deze sectie](sending-messages.md#archiving-emails) voor meer informatie.

## Levering bevestigen {#confirming-delivery}

Wanneer de levering wordt gevormd en klaar om worden verzonden, zorg ervoor u de leveringsanalyse in werking hebt gesteld.

Klik op **[!UICONTROL Send]** selecteert u de gewenste actie en klikt u op **[!UICONTROL Analyze]**. Zie voor meer informatie [De analyse starten](steps-validating-the-delivery.md#analyzing-the-delivery).

![](assets/s_ncs_user_email_del_send.png)

Als u klaar bent, klikt u op **[!UICONTROL Confirm delivery]** om de levering van berichten te starten.

U kunt de leveringstovenaar dan sluiten en de uitvoering van de levering van volgen **[!UICONTROL Delivery]** , toegankelijk via de details van deze levering of via de lijst van leveringen.

Nadat u berichten hebt verzonden, kunt u de leveringen controleren en volgen. Raadpleeg deze secties voor meer informatie hierover:

* [Een verzending controleren](about-delivery-monitoring.md)
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Berichttracking](about-message-tracking.md)

## De verzending van de levering plannen {#scheduling-the-delivery-sending}

U kunt de levering van berichten uitstellen om de levering te plannen of om de salesdruk te beheren en te voorkomen dat een populatie overbevraagd wordt.

1. Klik op de knop **[!UICONTROL Send]** en selecteert u de **[!UICONTROL Postpone delivery]** optie.

1. Geef een begindatum op in het dialoogvenster **[!UICONTROL Contact date]** veld.

![](assets/dlv_email_del_plan.png)

1. U kunt dan de leveringsanalyse beginnen, dan bevestig de levering verzendend. De verzending van de levering begint echter pas op de in het **[!UICONTROL Contact date]** veld.

>[!IMPORTANT]
>
>Wanneer u met de analyse bent begonnen, is de contactdatum die u hebt bepaald vast. Als u deze datum wijzigt, moet u de analyse opnieuw starten, zodat rekening wordt gehouden met uw wijzigingen.

![](assets/s_ncs_user_email_del_start_delayed.png)

In de leveringslijst wordt de levering weergegeven met **[!UICONTROL Pending]** status.

![](assets/s_ncs_user_email_del_waiting.png)

De planning kan ook upstream via **[!UICONTROL Scheduling]** van de levering.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

U kunt de levering uitstellen tot een latere datum of de levering opslaan in de voorlopige kalender.

* De **[!UICONTROL Schedule delivery (no automatic execution)]** Met deze optie kunt u een voorlopige analyse van de levering plannen.

   Wanneer deze configuratie wordt opgeslagen, verandert de levering in **[!UICONTROL Targeting pending]** status. De analyse wordt op de opgegeven datum gestart.

* De **[!UICONTROL Schedule delivery (automatic execution on planned date)]** kunt u de leveringsdatum opgeven.

   Klikken **[!UICONTROL Send]** en selecteert u **[!UICONTROL Postpone delivery]** start vervolgens de analyse en bevestig de levering . Wanneer de analyse volledig is, is het leveringsdoel klaar en de berichten zullen automatisch worden verzonden op de gespecificeerde datum.

Datums en tijden worden uitgedrukt in de tijdzone van de huidige operator. De **[!UICONTROL Time zone]** Met de vervolgkeuzelijst onder het invoerveld voor de contactdatum kunt u de ingevoerde datum en tijd automatisch omzetten in de geselecteerde tijdzone.

Bijvoorbeeld, als u een levering plant die automatisch om 8 uur de tijd van Londen moet worden uitgevoerd, wordt de tijd automatisch omgezet in de geselecteerde tijdzone:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Verzenden met meerdere golven {#sending-using-multiple-waves}

Als u de lading in evenwicht wilt brengen, kunt u leveringen in verscheidene partijen verdelen. Configureer het aantal partijen en hun verhouding ten opzichte van de volledige levering.

>[!NOTE]
>
>U kunt alleen de grootte en de vertraging tussen twee opeenvolgende golven definiëren. De ontvankelijke selectiecriteria voor elke golf kunnen niet worden gevormd.

1. Open het venster met de leveringseigenschappen en klik op de knop **[!UICONTROL Delivery]** tab.
1. Selecteer **[!UICONTROL Send using multiple waves]** en klik op de knop **[!UICONTROL Define waves...]** koppeling.

   ![](assets/s_ncs_user_wizard_waves.png)

1. Om golven te vormen, kunt u of:

   * Bepaal de grootte voor elke golf. Als u bijvoorbeeld **[!UICONTROL 30%]** op het overeenkomstige gebied, zal elke golf 30% van de berichten vertegenwoordigen inbegrepen in de levering, behalve laatste, die 10% van de berichten zal vertegenwoordigen.

      In de **[!UICONTROL Period]** geeft u de vertraging op tussen het begin van twee opeenvolgende golven. Als u bijvoorbeeld **[!UICONTROL 2d]** De eerste golf begint onmiddellijk, de tweede golf begint over twee dagen, de derde golf over vier dagen, enzovoort.

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Definieer een kalender voor het verzenden van elke golf.

      In de **[!UICONTROL Start]** geeft u de vertraging op tussen het begin van twee opeenvolgende golven. In de **[!UICONTROL Size]** Voer een vast getal of een percentage in.

      In het volgende voorbeeld vertegenwoordigt de eerste golf 25% van het totale aantal berichten inbegrepen in de levering en zal onmiddellijk beginnen. De volgende twee golven voltooien de levering en zijn geplaatst om met intervallen van zes uur te beginnen.

      ![](assets/s_ncs_user_wizard_waves_create.png)
   een specifieke typologieregel; **[!UICONTROL Wave scheduling check]**, zorgt ervoor dat de laatste golf vóór de grens van de leveringsgeldigheid wordt gepland. De typologieën van de campagne en hun regels, die in worden gevormd **[!UICONTROL Typology]** tabblad van de leveringseigenschappen, worden weergegeven in [Validatieproces met typologieën](steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >Zorg ervoor dat de laatste golven de leveringstermijn niet overschrijden, die in het dialoogvenster **[!UICONTROL Validity]** tab. Anders kunnen sommige berichten niet worden verzonden.
   >
   >U moet ook genoeg tijd voor pogingen toestaan wanneer het vormen van de laatste golven. Zie [deze sectie](steps-sending-the-delivery.md#configuring-retries).

1. Ga naar de leveringslogboeken om uw verzendingen te controleren. Zie [deze pagina](delivery-dashboard.md#delivery-logs-and-history).

   De leveringen die al zijn verzonden in de verwerkte golven (**[!UICONTROL Sent]** status) en de in de resterende golven te verzenden leveringen (**[!UICONTROL Pending]** status).

De twee onderstaande voorbeelden zijn de meest gebruikte voorbeelden voor het gebruik van meerdere golven.

* **Tijdens het opvoerproces**

   Wanneer e-mails met een nieuw platform worden verzonden, zijn internetproviders (ISP&#39;s) verdacht van IP-adressen die niet worden herkend. Als er plotseling grote hoeveelheden e-mails worden verzonden, markeren de ISP&#39;s deze vaak als spam.

   Als u wilt voorkomen dat spam wordt gemarkeerd, kunt u het verzonden volume progressief verhogen met golven. Dit zou een vlotte ontwikkeling van de startfase moeten verzekeren en u toelaten om het algemene tarief van ongeldige adressen te verminderen.

   Om dit te doen, gebruik **[!UICONTROL Schedule waves according to a calendar]** optie. Stel bijvoorbeeld de eerste golf in op 10%, de tweede op 15% enzovoort.

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Campagnes die een callcenter impliceren**

   Wanneer het leiden van een campagne van de telefoonloyaliteit, heeft uw organisatie een beperkte capaciteit om het aantal vraag te verwerken om abonnees te contacteren.

   Gebruikend golven, kunt u het aantal berichten tot 20 per dag beperken, die de dagelijkse verwerkingscapaciteit van een vraagcentrum is.

   Selecteer hiervoor de optie **[!UICONTROL Schedule multiple waves of the same size]** optie. Enter **[!UICONTROL 20]** als de grootte van de golf en **[!UICONTROL 1d]** in de **[!UICONTROL Period]** veld.

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Opnieuw proberen configureren {#configuring-retries}

Tijdelijk niet-geleverde berichten vanwege een **Zacht** of **Genegeerd** fout kan automatisch opnieuw worden geprobeerd. De types van leveringsmislukking en de redenen worden voorgesteld in dit [sectie](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Voor gehoste of hybride installaties, als u hebt geüpgraded naar de [Enhanced MTA](sending-with-enhanced-mta.md), worden de instellingen voor opnieuw proberen in de levering niet meer gebruikt door Campagne. De zachte stuitpogingen en de tijdsduur tussen hen worden bepaald door Verbeterde MTA gebaseerd op het type en de strengheid van de stuiteringsreacties die van het e-maildomein van het bericht terugkomen.

Voor installaties op locatie en gehoste/hybride installaties die gebruikmaken van de oude Campagne MTA, het centrale gedeelte van de **[!UICONTROL Delivery]** tab voor leveringsparameters geeft aan hoeveel pogingen moeten worden uitgevoerd op de dag na de levering en de minimale vertraging tussen pogingen.

![](assets/s_ncs_user_wizard_retry_param.png)

Door gebrek, zijn vijf herpogingen gepland voor de eerste dag van de levering met een minimuminterval van één uur uitgespreid over de 24 uren van de dag. Na die datum en tot de uiterste datum van levering, die in de **[!UICONTROL Validity]** tab. Zie [De geldigheidsperiode definiëren](#defining-validity-period).

## De geldigheidsperiode definiëren {#defining-validity-period}

Wanneer de levering is gestart, kunnen de berichten (en eventuele nieuwe pogingen) worden verzonden tot de leveringstermijn. Dit wordt aangegeven in de levereigenschappen, via de **[!UICONTROL Validity]** tab.

![](assets/s_ncs_user_email_del_valid_period.png)

* De **[!UICONTROL Delivery duration]** in dit veld kunt u de limiet voor algemene leveringspogingen invoeren. Dit betekent dat Adobe Campaign de berichten verzendt die op de begindatum beginnen, en dan, voor berichten die een fout slechts terugkeren, regelmatig, configureerbare herpogingen worden uitgevoerd tot de geldigheidsgrens wordt bereikt.

   U kunt ook datums opgeven. Selecteer **[!UICONTROL Explicitly set validity dates]**. In dit geval kunt u ook de leverings- en geldigheidstermijn opgeven. De huidige tijd wordt standaard gebruikt, maar u kunt deze rechtstreeks wijzigen in het invoerveld.

   >[!IMPORTANT]
   >
   >Voor gehoste of hybride installaties, als u hebt geüpgraded naar de [Enhanced MTA](sending-with-enhanced-mta.md)de **[!UICONTROL Delivery duration]** het plaatsen in uw de e-maillevering van de Campagne zal slechts worden gebruikt als reeks aan **3,5 dagen of minder**. Als u een waarde definieert die hoger is dan 3,5 dagen, wordt hiermee geen rekening gehouden.

* **Geldigheidsbeperking van middelen**: De **[!UICONTROL Validity limit]** het veld wordt gebruikt voor geüploade bronnen, voornamelijk voor de spiegelpagina en afbeeldingen. De bronnen op deze pagina zijn gedurende een beperkte tijd geldig (om schijfruimte te besparen).

   De waarden in dit veld kunnen worden uitgedrukt in de in [deze sectie](../../platform/using/adobe-campaign-workspace.md#default-units).
