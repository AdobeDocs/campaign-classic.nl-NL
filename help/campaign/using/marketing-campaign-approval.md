---
product: campaign
title: Het goedkeuringsproces instellen en beheren
description: Leer hoe u goedkeuringen van marketingcampagnes beheert
role: User
feature: Approvals, Campaigns
hide: true
hidefromtoc: true
exl-id: 8cbb2445-f5e4-4a25-ba7e-56e39ca9d3ce
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '2437'
ht-degree: 1%

---

# Het goedkeuringsproces instellen en beheren {#approving-marketing-campaigns}


Elke leveringsstap kan worden goedgekeurd om te zorgen voor volledige controle en controle op de verschillende processen van de campagne: gericht, inhoudelijk, budgettair, extractie en het verzenden van een bewijs.

De berichten van het bericht worden verzonden naar de exploitanten van Adobe Campaign die aangewezen recensenten zijn om hen van een goedkeuringsverzoek op de hoogte te brengen. Controleer dat de recensenten de **aangewezen toestemmingen** voor het goedkeuren hebben, en dat hun veiligheidsstreek correct wordt bepaald. [Meer informatie](#selecting-reviewers).

De goedkeuringsprocedure wordt voorgesteld in [ deze sectie ](#checking-and-approving-deliveries).

>[!NOTE]
>
>Alleen de eigenaar van de levering kan een levering starten. Als een andere operator (of operatorgroep) een levering wil starten, moet u deze als controleurs toevoegen in het veld **[!UICONTROL Delivery start:]** .\
>[Meer informatie](#selecting-reviewers).

## Werkwijze {#operating-principle-}

Het standaardbericht voor goedkeuring van de begroting is bijvoorbeeld als volgt:

![](assets/s_user_validation_link_in_mail.png)

De revisorexploitanten kunnen dan kiezen of zij de begroting goedkeuren of niet.

![](assets/s_user_validation_page_confirm.png)

Nadat de operator is gevalideerd, wordt de goedkeuring of afwijzing van de taak doorgestuurd naar het dashboard voor de levering.

![](assets/s_user_validation_link_in_op_board.png)

De informatie is ook beschikbaar in de goedkeuringslogboeken van de campagne. Deze logboeken zijn toegankelijk via het tabblad **[!UICONTROL Edit > Tracking > Approvals]** .

![](assets/s_user_validation_log_in_op_edit_tab.png)

Deze meldingen worden verzonden naar de betrokken marktdeelnemers voor elk proces waarvoor goedkeuring is ingeschakeld.

De goedkeuringen kunnen voor het campagnemalplaatje, voor elke campagne individueel, of voor een levering worden toegelaten.

Alle taken waarvoor goedkeuring is vereist, worden geselecteerd in de campagnemplate ( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** tab), evenals de operatoren die verantwoordelijk zijn voor goedkeuring (ze ontvangen meldingen, tenzij deze optie niet is ingeschakeld). Raadpleeg [deze sectie](#approving-processes) voor meer informatie.

Deze instellingen kunnen worden overschreven voor elke campagne die met deze sjabloon wordt gemaakt en afzonderlijk voor elke levering van de campagne: klik op de knop **[!UICONTROL Properties]** en vervolgens op de tab **[!UICONTROL Approvals]** .

In het volgende voorbeeld is voor de leveringsinhoud geen goedkeuring vereist:

![](assets/s_user_validation_select_process_from_del.png)

## Revisoren selecteren {#selecting-reviewers}

Voor elk type goedkeuring worden de voor de goedkeuring verantwoordelijke exploitanten of groepen van marktdeelnemers geselecteerd uit de vervolgkeuzelijst in de levering. Met de koppeling **[!UICONTROL Edit...]** kunt u meer operatoren toevoegen. In dit venster kunt u ook de deadline van de goedkeuring bewerken.

![](assets/s_user_validation_add_operator.png)

Als er geen controleur is opgegeven, is de campagnemanager verantwoordelijk voor de goedkeuring en ontvangt deze de meldingen. Het campagneremanager wordt opgegeven op het tabblad **[!UICONTROL Edit > Properties]** van de campagne:

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>Alle andere Adobe Campaign-operatoren met **[!UICONTROL Administrator]** -rechten kunnen ook taken goedkeuren, maar ze ontvangen geen berichten.\
>Standaard kan de campagnemanager de goedkeuring niet uitvoeren of de leveringen starten als er goedkeuringsoperatoren zijn gedefinieerd. U kunt dit gedrag wijzigen en de campagnemanager machtigen om leveringen goed te keuren/te beginnen door **NmsCampaign_Activate_OwnerConfirmation** optie met **1** als waarde te creëren.

## Goedkeuringsmodi {#approval-modes}

### Goedkeuring via het dashboard {#approval-via-the-dashboard}

Als u een taak wilt goedkeuren via de console of de webinterface, klikt u op de desbetreffende koppeling op het campagnemdashboard. Taken kunnen ook worden goedgekeurd via het volgen van de levering of via het leveringsdashboard.

![](assets/s_user_validation_from_console.png)

Controleer de informatie die u wilt goedkeuren, kies of u de goedkeuring wilt accepteren of afwijzen en voer zo nodig een opmerking in. Klik op **[!UICONTROL Ok]** om op te slaan.

>[!NOTE]
>
>Als een proces reeds door een andere exploitant is goedgekeurd, is de goedkeuringsverbinding niet beschikbaar.

### Goedkeuring via kennisgevingsberichten {#approval-via-notification-messages}

Klik de verbinding beschikbaar in het berichtbericht (zie [ Meldingen ](#notifications)). U moet zich aanmelden, zoals hieronder wordt weergegeven:

![](assets/s_user_validation__log_in.png)

Selecteer **[!UICONTROL Accept]** of **[!UICONTROL Reject]** en voer indien nodig een opmerking in.

![](assets/s_user_validation_save_target_validation.png)

Klik op **[!UICONTROL Validate]**.

>[!NOTE]
>
>Als tijdens het proces waarschuwingen zijn weergegeven, wordt een waarschuwing weergegeven in het bericht.

### Goedkeuring bijhouden {#approval-tracking}

De informatie is op verschillende plaatsen beschikbaar:

* In het logboek voor campagnegoedkeuring, **[!UICONTROL Approvals]** subtab van het tabblad **[!UICONTROL Edit > Tracking]** :

  ![](assets/s_user_validation_log_from_op.png)

* In het leveringslogboek van de campagne, **[!UICONTROL Deliveries]** subtab van **[!UICONTROL Edit > Tracking]** tabel:

  ![](assets/s_user_validation_log_from_delivery_list.png)

* De goedkeuringsstatus voor elke levering kan worden weergegeven door op de optie **[!UICONTROL Hide/show log]** van het tabblad **[!UICONTROL Summary]** te klikken.

  ![](assets/s_user_validation_log_delivery.png)

* Deze informatie is ook toegankelijk via het tabblad **[!UICONTROL Tracking > Approvals]** van elke levering:

  ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>Wanneer een exploitant een taak heeft goedgekeurd of geweigerd, kunnen de andere beoordelende exploitanten niet langer op de goedkeuring reageren.

### Automatische en handmatige goedkeuring {#automatic-and-manual-approval}

Als Adobe Campaign bij het maken van een doelworkflow automatisch goedkeurt (de standaardmodus), wordt de goedkeuringskoppeling weergegeven of wordt een melding verzonden zodra goedkeuring is vereist.

Als u de goedkeuringsmodus wilt kiezen (handmatig of automatisch), klikt u op het tabblad **[!UICONTROL Edit > Properties]** van de campagne- of campagnemalplaatje en vervolgens op **[!UICONTROL Advanced campaign settings...]** en ten slotte op het tabblad **[!UICONTROL Approvals]** .

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>De geselecteerde goedkeuringsmodus is van toepassing op alle leveringen van de campagne.

Wanneer een doelworkflow wordt gemaakt, kunt u met handmatige goedkeuring voorkomen dat er goedkeuringskoppelingen worden gemaakt of dat meldingen automatisch worden verzonden. Het campagnemdashboard bevat vervolgens een **[!UICONTROL Submit targeting for approval]** -koppeling waarmee het goedkeuringsproces handmatig kan worden gestart.

Met een bevestigingsbericht kunt u goedkeuringen autoriseren voor de taken die voor deze levering zijn geselecteerd.

De goedkeuringsknoppen worden vervolgens weergegeven op het campagnemdashboard (voor deze levering), op het leveringsdashboard en in het bijhouden van de levering. Als meldingen zijn ingeschakeld, worden ze parallel verzonden.

Met deze methode voor het inschakelen van goedkeuringen kunt u doelgericht werken zonder dat u onjuiste meldingen naar revisoren verzendt.

## Meldingen {#notifications}

Meldingen zijn specifieke e-mailberichten die naar revisoren worden verzonden om hen te laten weten dat een proces in afwachting is van goedkeuring. Wanneer de exploitant de verbinding in het bericht klikt, verschijnt een authentificatiepagina en, na het programma openen, kan de exploitant de informatie bekijken en de baan goedkeuren of verwerpen. U kunt ook een opmerking invoeren in het goedkeuringsvenster.

De inhoud van e-mailberichten voor meldingen kan worden aangepast. Zie [ inhoud van het Bericht ](#notification-content).

### Melding in-/uitschakelen {#enabling-disabling-notification}

Door gebrek, worden de berichtberichten verzonden als de goedkeuring van de verwante baan in het campagnemalplaatje, de campagne, of de levering wordt toegelaten. Meldingen kunnen echter alleen via de console worden uitgeschakeld.

Hiervoor bewerkt u het goedkeuringsvenster van de sjabloon voor de campagne of de campagne ( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** ) en selecteert u **[!UICONTROL Do not enable notification sending]** .

![](assets/s_user_validation_notif_desactivate.png)

### Inhoud voor meldingen {#notification-content}

De inhoud van berichten wordt gedefinieerd in een specifieke sjabloon: **[!UICONTROL Notification of validations for the marketing campaign]** . Deze sjabloon wordt opgeslagen in de map **[!UICONTROL Administration > Campaign management > Technical delivery templates]** van de Adobe Campaign-structuur.

## Leveringen controleren en goedkeuren {#checking-and-approving-deliveries}

Met Adobe Campaign kunt u goedkeuringsprocessen instellen voor de belangrijkste fasen van de marketingcampagne in de samenwerkingsmodus.

Voor directe postleveringen, kunnen de exploitanten van Adobe Campaign het extractiedossier bekijken alvorens het naar de router wordt verzonden, en indien nodig kunnen zij het formaat veranderen en extractie opnieuw lanceren. Zie [ een extractiedossier ](#approving-an-extraction-file) goedkeuren.

Voor elke campagne kunt u het leveringsdoel, inhoud (zie [ goedkeuren inhoud ](#approving-content)) en kosten goedkeuren. Adobe Campaign-operatoren die met de goedkeuring zijn belast, kunnen via e-mail op de hoogte worden gesteld en kunnen goedkeuring van de console of via een webverbinding accepteren of afwijzen. Zie [ Stappen om een levering ](#approving-processes) goed te keuren.

Wanneer deze validatiefasen zijn voltooid, kan de levering worden gestart. [Meer informatie](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery).

### Stappen om een levering goed te keuren {#approving-processes}

De stadia die goedkeuring vereisen verschijnen op het campagnesdashboard (via de console van de Webinterface). Zij verschijnen ook in de levering volgende lijst en op het leveringsdashboard.

Op dit punt is de status van de campagne **[!UICONTROL To validate]** .

>[!NOTE]
>
>Om de processen te selecteren die een goedkeuring vereisen, wijzig het campagnemalplaatje. Voor meer op dit, verwijs naar [ malplaatjes van de Campagne ](../../campaign/using/marketing-campaign-templates.md#campaign-templates).
>

![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>Als tijdens de voorbereiding van berichten een fout optreedt die is gekoppeld aan een configuratieprobleem, wordt in een doelworkflow de koppeling **[!UICONTROL Restart message preparation]** weergegeven op het dashboard. Corrigeer de fout en klik op deze koppeling om de berichtvoorbereiding opnieuw te starten terwijl het doelwerkgebied wordt overgeslagen.

![](assets/s_user_validation_relaunch_message_preparation.png)

Voor elke levering in de campagne, kunt u de volgende processen goedkeuren:

* **het richten, inhoud en begroting**

  Wanneer de opties **[!UICONTROL Enable target approval]** , **[!UICONTROL Enable content approval]** of **[!UICONTROL Enable budget approval]** zijn geselecteerd in het venster met taakgoedkeurinstellingen, worden de relevante koppelingen weergegeven in het campagnemarkeerteken voor de desbetreffende leveringen.

  >[!NOTE]
  >
  >De goedkeuring van de begroting is slechts beschikbaar als gericht goedkeuring in het venster van goedkeuringsmontages wordt toegelaten. De koppeling voor goedkeuring van de begroting wordt pas weergegeven nadat het doel is geanalyseerd. Deze koppeling wordt ook samen met de koppeling voor doelgoedkeuring weergegeven.

  Als de opties **[!UICONTROL Assign content editing]** of **[!UICONTROL External content approval]** zijn geselecteerd in het venster met goedkeuringsinstellingen, worden op het dashboard de koppelingen **[!UICONTROL Available content]** en **[!UICONTROL External content approval]** weergegeven.

  Met Goedkeuring van inhoud hebt u toegang tot de verzonden proefdrukken.

* **de goedkeuring van de Uitwinning (directe postlevering)**

  Wanneer **[!UICONTROL Enable extraction approval]** in het venster van goedkeuringsmontages wordt geselecteerd, moet het gehaalde dossier worden goedgekeurd alvorens de router kan worden meegedeeld.

  Een koppeling **[!UICONTROL Approve content]** is beschikbaar op het campagnemdashboard, zoals hieronder wordt getoond:

  ![](assets/s_ncs_user_edit_file_valid.png)

  U kunt een voorvertoning weergeven van de extractiebestanden via het goedkeuringsvak. U kunt de bestanden vervolgens accepteren of afwijzen.

  ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

  >[!NOTE]
  >
  >De voorvertoning van het extractiebestand heeft alleen betrekking op een gegevensvoorbeeld. Het volledige uitvoerbestand wordt niet geladen.

* **goedkeurend bijbehorende leveringen**

  De optie **[!UICONTROL Enable individual approval of each associated delivery]** wordt gebruikt voor één hoofdlevering die aan secundaire leveringen is gekoppeld. Deze optie is standaard niet geselecteerd, zodat een algemene goedkeuring van de hoofdlevering kan worden uitgevoerd. Als deze optie is geselecteerd, moet elke levering afzonderlijk worden goedgekeurd.

  ![](assets/s_ncs_user_task_valid_associate.png)

### Goedkeuren van processen selecteren {#choosing-the-processes-to-be-approved}

De goedkeuringsfasen worden bepaald met het malplaatje verbonden aan de campagne. U moet de goed te keuren onderdelen selecteren in het model en de Adobe Campaign-operatoren specificeren die verantwoordelijk zijn voor deze goedkeuringen. Voor meer op campagnemalplaatjes, verwijs naar [ deze sectie ](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

>[!NOTE]
>
>De goedkeuringsconfiguratie voor de campagne (of het campagnemalplaatje) is van toepassing op alle toekomstige leveringen met betrekking tot deze campagne. Wijzigingen in de configuratie worden niet toegepast op vorige leveringen.

Deze informatie kan voor elke campagne en elke levering worden overschreven.

Voor een campagne klikt u op het tabblad **[!UICONTROL Edit > Properties]** , vervolgens op de koppeling **[!UICONTROL Advanced campaign settings...]** en ten slotte op het subtabblad **[!UICONTROL Approvals]** voor toegang tot de pagina voor configuratie van goedkeuringen.

U kunt de processen selecteren en deselecteren om Adobe Campaign-operatoren die met de goedkeuring zijn belast, goed te keuren en aan te wijzen. Dit kunnen individuele operatoren, een groep operatoren of een lijst met operatoren zijn.

Als u een lijst met operatoren wilt selecteren, klikt u op de koppeling **[!UICONTROL Edit...]** rechts van het veld waarin de eerste controleur wordt aangewezen en voegt u zoveel operatoren toe als nodig is, zoals hieronder wordt getoond:

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* Als een lijst met revisoren is gedefinieerd, wordt een taak goedgekeurd wanneer één revisor deze heeft geaccepteerd. De desbetreffende goedkeuringsverbinding wordt dan niet meer aangeboden in het dashboard. Wanneer het verzenden van meldingen is ingeschakeld en een andere controleur op de goedkeuringskoppeling in het meldingsbericht klikt, wordt hem meegedeeld dat een andere operator de taak al heeft goedgekeurd.
>* U kunt een goedkeuringsschema voor de campagne definiëren in de onderste sectie van het revisiebewerkingsvenster. Standaard hebben revisoren drie dagen vanaf de verzenddatum om een proces goed te keuren. Het is mogelijk om een herinnering te vormen die automatisch naar de betrokken exploitanten vóór de goedkeuringstermijn wordt verzonden.
>* U kunt vanuit deze sectie herinneringen toevoegen.
>

![](assets/s_ncs_user_edit_op_valid_calendar.png)

Klik voor elke levering op de knop **[!UICONTROL Audit]** en het tabblad **[!UICONTROL Approvals]** om goedkeuringsdatums en automatische herinneringen weer te geven en te bewerken.

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>Dit tabblad is beschikbaar nadat het goedkeuringsproces voor inhoud is gestart.

### Inhoud goedkeuren {#approving-content}

>[!CAUTION]
>
>Voor het goedkeuren van een inhoud is een proefcyclus verplicht. Met proefdrukken kunt u de weergave van gegevens, aanpassingsgegevens en de werking van koppelingen goedkeuren. Leer hoe te om een proef in [ tot stand te brengen deze sectie ](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).
>
>De hieronder beschreven functies voor inhoudsgoedkeuring hebben betrekking op de levering van het bewijs.

Het is mogelijk om een cyclus van de inhoudsgoedkeuring te vormen. Selecteer hiertoe de optie **[!UICONTROL Enable content approval]** in het venster met goedkeuringsinstellingen. De belangrijkste stappen van de cyclus voor inhoudsgoedkeuring zijn:

1. Na het maken van een nieuwe levering klikt de campagnemanager op de koppeling **[!UICONTROL Submit content]** op het campagnedashboard om de goedkeuringcyclus voor de inhoud te starten.

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >Als de optie **[!UICONTROL Enable the sending of proofs]** (voor e-mailleveringen) of **[!UICONTROL Enable the sending and approval of proofs]** (voor directe mailleveringen) is geselecteerd in het venster met goedkeuringsinstellingen, worden automatisch proefdrukken verzonden.

1. Er wordt een meldingsbericht verzonden naar de persoon die verantwoordelijk is voor de inhoud, die kan kiezen of u de inhoud wilt goedkeuren of niet:

   * via het e-mailbericht:

     ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

     >[!NOTE]
     >
     >Het bericht e-mail bevat een verbinding aan de reeds verzonden proeven, en misschien aan een teruggevende van het bericht voor de diverse webmails als de **optie van de Leverbaarheid** voor deze instantie wordt toegelaten.

   * via de console of webinterface, het bijhouden van de levering, het bezorgdashboard of het campagnemdashboard:

     ![](assets/s_ncs_user_validation_content_bat_op.png)

     >[!NOTE]
     >
     >In dit campagnemdashboard kunt u de lijst met proefdrukken weergeven die zijn verzonden door op de koppeling **[!UICONTROL Inbox rendering...]** te klikken. Als u hun inhoud wilt weergeven, klikt u op het pictogram **[!UICONTROL Detail]** rechts van de lijst.

     ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. Aan de voor de campagne verantwoordelijke persoon wordt een meldingsbericht gezonden waarin deze wordt meegedeeld of de inhoud al dan niet is goedgekeurd.

   >[!NOTE]
   >
   >De persoon die verantwoordelijk is voor de campagne kan de cyclus voor het goedkeuren van inhoud op elk gewenst moment opnieuw starten. Klik hiertoe op de koppeling op de regel **[!UICONTROL Content status]** van het campagnemdashboard (op leveringsniveau) en klik vervolgens op **[!UICONTROL Reset content approval to submit it again]** .

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### Inhoud bewerken toewijzen {#assign-content-editing}

Met deze optie kunt u iemand definiëren die verantwoordelijk is voor het bewerken van inhoud, zoals een webstramien. Als de optie **[!UICONTROL Assign content editing]** is geselecteerd in het venster met goedkeuringsinstellingen, worden verschillende goedkeuringsstappen toegevoegd tussen het maken van de verzending en het verzenden van het e-mailbericht aan de persoon die de inhoud beheert:

1. Na het maken van een nieuwe levering klikt de persoon die verantwoordelijk is voor de campagne op de koppeling **[!UICONTROL Submit content editing]** in het campagnedashboard om de bewerkingscyclus van de inhoud te starten.

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. De persoon die verantwoordelijk is voor het bewerken van inhoud ontvangt een e-mail met de mededeling dat de inhoud beschikbaar is.

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. Vervolgens kunnen zij zich aanmelden bij de console, de levering openen en deze bewerken met een vereenvoudigde assistent om het onderwerp, de HTML en de tekstinhoud te wijzigen en proefdrukken te verzenden.

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >Als de optie **[!UICONTROL Enable the sending of proofs]** (voor e-mailleveringen) of **[!UICONTROL Enable the sending and approval of proofs]** (voor directe mailleveringen) is geselecteerd in het venster met goedkeuringsinstellingen, worden automatisch proefdrukken verzonden.

1. Nadat de persoon die verantwoordelijk is voor het bewerken van inhoud alle wijzigingen in de inhoud van de levering heeft aangebracht, kan hij of zij de inhoud beschikbaar stellen.

   Om dit te doen, kunnen zij:

   * Klik op de koppeling **[!UICONTROL Available content]** via de Adobe Campaign-console.

     ![](assets/s_ncs_user_validation_submit_content_available.png)

   * Klik op de koppeling in het meldingsbericht en geef vervolgens de beschikbaarheid van de inhoud goed.

     ![](assets/s_ncs_user_validation_submit_content_available2.png)

     De exploitant kan een commentaar toevoegen alvorens de inhoud aan de persoon voor te leggen die de campagne leidt.

     ![](assets/s_ncs_user_validation_submit_content_available3.png)

     Met het meldingsbericht kan de revisor de inhoud goedkeuren of afwijzen.

     ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### Goedkeuring van externe inhoud {#external-content-approval}

Met deze optie kunt u een externe operator definiëren die verantwoordelijk is voor het goedkeuren van rendering van leveringen, zoals consistentie in de communicatie van het merk, snelheden, enzovoort. Wanneer de optie **[!UICONTROL External content approval]** is geselecteerd in het venster met goedkeuringsinstellingen, worden verschillende goedkeuringsstappen toegevoegd tussen de goedkeuring van inhoud en de verzending van het bericht aan de persoon die verantwoordelijk is voor de campagne:

1. De externe contentmanager ontvangt een bericht via e-mail waarin wordt gemeld dat de inhoud is goedgekeurd en waarmee externe goedkeuring wordt aangevraagd.
1. Het e-mailbericht bevat koppelingen naar de verzonden proefdrukken, waarmee u rendering van de levering kunt weergeven en een knop voor het goedkeuren of afwijzen van de leveringsinhoud.

   >[!NOTE]
   >
   >Deze koppelingen zijn alleen beschikbaar als een of meer proefdrukken zijn verzonden. Anders is rendering van levering alleen beschikbaar via de console of de webinterface.

   ![](assets/s_user_validation_external_content.png)

### Een extractiebestand goedkeuren {#approving-an-extraction-file}

Voor off-line leveringen, produceert Adobe Campaign een extractiedossier dat, afhankelijk van hoe het opstelling is, naar de router wordt verzonden. De inhoud ervan is afhankelijk van de gebruikte exportsjabloon.

Wanneer de inhoud, de bestemming en het budget zijn goedgekeurd, verandert de levering in **[!UICONTROL Extraction pending]** totdat de extractieworkflow voor de campagnes wordt gestart.

![](assets/s_ncs_user_waiting_file_extraction.png)

Op de datum van het extractieverzoek wordt het extractiebestand gemaakt en verandert de leveringsstatus in **[!UICONTROL File to approve]** .

![](assets/s_ncs_user_file_extract_to_valid.png)

U kunt de inhoud van het geëxtraheerde bestand weergeven (door op de naam ervan te klikken), goedkeuren of, indien nodig, de indeling wijzigen en de extractie opnieuw starten met de koppelingen op het dashboard.

Zodra het dossier is goedgekeurd, kunt u het bericht e-mail naar de router verzenden. Voor meer op dit, verwijs naar [ Begin een off-line levering ](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery).
