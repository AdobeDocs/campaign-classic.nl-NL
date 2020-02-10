---
title: Taken maken en beheren
seo-title: Taken maken en beheren
description: Taken maken en beheren
seo-description: null
page-status-flag: never-activated
uuid: 1d219ae4-1ca9-42cb-a49e-2b647520bda0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: d71e5ff7-1e81-4c49-9673-c6fae890029b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Taken maken en beheren{#creating-and-managing-tasks}

## Taken {#about-tasks}

Met Adobe Campaign kunt u taken maken en de volledige levenscyclus ervan rechtstreeks in de toepassing beheren. De programma- en campagneimplementatie kan worden onderverdeeld in taken die worden toegewezen aan Adobe Campagnebeheerders of externe serviceproviders. In deze modus kunt u een open samenwerkingsomgeving maken waarin alle deelnemers aan het programma en externe deelnemers zijn opgenomen.

Taken kunnen worden gemaakt, weergegeven en gecontroleerd vanuit de takenlijst of het campagnemdashboard. Zij kunnen ook worden bekeken en bijgehouden in de schema&#39;s van het marketingplan, de programma&#39;s en de campagnes.

Taken worden aan de campagne gekoppeld en kunnen afhankelijkheden, d.w.z. bijbehorende taken, hebben. Elke taak heeft een status, prioriteit, geschatte belasting en bijbehorende kosten.

Alle taken worden gegroepeerd in een lijst die toegankelijk is via het **Campagne** universum. Raadpleeg [Toegang tot taken](#accessing-tasks)voor meer informatie.

Ze kunnen worden weergegeven in het programma waartoe ze behoren.

![](assets/d_ncs_user_tasks_in_planning.png)

## Toegang tot taken {#accessing-tasks}

### Taken weergeven {#displaying-tasks}

De taken worden weergegeven in de takenlijst die toegankelijk is via het **[!UICONTROL Campaigns]** universum.

![](assets/s_ncs_user_task_edit_view.png)

U kunt alle taken van de verbonden exploitant daar bekijken.

Raadpleeg voor meer informatie de status [Uitvoering van een taak](#execution-status-of-a-task) en de status [Voortgang van een taak](#progress-status-of-a-task).

### Filtertaken {#filtering-tasks}

Wanneer u deze weergave weergeeft, wordt deze automatisch gefilterd om alleen weer te geven **[!UICONTROL operator tasks]**. U kunt de taken ook filteren met de velden in de bovenste sectie van het venster.

![](assets/s_ncs_user_task_filter_from_view.png)

### Taken bewerken {#editing-tasks}

Klik op een taak om deze te bewerken.

![](assets/s_ncs_user_task_edit_from_view.png)

## Een nieuwe taak maken {#creating-a-new-task}

Als u een taak wilt maken, klikt u op de **[!UICONTROL Tasks]** koppeling in het universum Campagnes en selecteert u **[!UICONTROL Create]**.

![](assets/s_ncs_user_task_create_new.png)

Voer ten minste de naam van de taak in en selecteer de campagne waaraan de taak is gekoppeld. U moet ook de begin- en einddatum opgeven. Deze drie gegevens zijn verplicht.

Klik **[!UICONTROL Save]** om de taak te maken.

![](assets/s_ncs_user_task_create_simple.png)

U kunt ook een taak maken via het dashboard van een campagne: in dit geval wordt de steun automatisch gekoppeld aan de campagne die zij heeft opgezet .

![](assets/s_ncs_user_task_create_new_from_op.png)

Nadat een taak wordt gecreeerd, wordt het toegevoegd aan het campagneprogramma en de lijst van taken. Als u een taak wilt bewerken, selecteert u de taak in de planning of klikt u op de naam in het taakoverzicht en klikt u op de **[!UICONTROL Open]** koppeling.

![](assets/s_ncs_user_task_edit_simple.png)

Om het te vormen, moet u wijzen op:

* De manager en de deelnemers: Raadpleeg [Manager en deelnemers](#manager-and-participants).
* Het schema voor het maken: zie [Uitvoeringsschema](#execution-schedule).
* Toegezegde kosten: zie [Uitgaven en opbrengsten](#expenses-and-revenues).

Het is ook mogelijk om revisoren toe te voegen (zie [Reviewers](#reviewers)) en documenten waarnaar wordt verwezen (zie [Documenten waarnaar wordt verwezen](#documents-referenced)).

De levenscyclus van taken wordt gepresenteerd in de [levenscyclus](#life-cycle).

### Manager en deelnemers {#manager-and-participants}

Alleen de exploitant die met een taak is belast, mag deze sluiten.

Wanneer een Adobe Campagne-operator een taak maakt, wordt deze standaard automatisch toegewezen aan deze beheerders. Gebruik het **[!UICONTROL Assigned to]** veld om een andere operator te selecteren.

![](assets/s_ncs_user_task_edit_simple_general_tab.png)

>[!NOTE]
>
>Operator management wordt in [deze sectie](../../platform/using/access-management.md)weergegeven.

U kunt aangeven welke operatoren bij de uitvoering van de taak betrokken zijn. Deze operatoren zijn niet geautoriseerd om de taak te sluiten. Zij kunnen alleen de hun toegewezen taak goedkeuren.

Ze worden geselecteerd met het **[!UICONTROL Resources]** pictogram op de taakwerkbalk. Klik **[!UICONTROL Add]** en selecteer de betrokken exploitanten.

![](assets/s_ncs_user_task_add_resources.png)

Klik **[!UICONTROL Ok]** en voer vervolgens de gebruiksfrequentie in: dit vertegenwoordigt de lading die aan de exploitant voor de duur van taakuitvoering wordt toegewezen. Dit percentage is slechts een indicatie en wordt uitgedrukt als een percentage.

Voor een taak waarvan het uitvoeringsschema op 10 dagen wordt vastgesteld, zal bijvoorbeeld een exploitant met een gebruiksgraad van 50% op deze taak voor de helft van zijn werktijd voor de tien dagen worden gemobiliseerd.

Voor elke operator kunt u een geplande werkbelasting en een werkelijke werkbelasting invoeren. Deze tijdsduur is ook uitsluitend ter informatie.

Het is mogelijk om een herinnering te vormen, die automatisch zal worden verzonden naar alle exploitanten betrokken bij de taak vóór zijn einddatum.

U kunt het Adobe Campaign-operatorprofiel weergeven via het **[!UICONTROL Edit link]** pictogram.

![](assets/s_ncs_user_task_edit_resource_profile.png)

Met het operatordashboard kunt u de werkbelasting controleren (andere lopende taken).

![](assets/s_ncs_user_task_edit_resource_planning.png)

### Revisoren {#reviewers}

Naast de deelnemers kunt u ook operatoren definiëren die de taak evalueren wanneer deze is gesloten door de verantwoordelijke persoon. Klik hiertoe op de **[!UICONTROL Enable task approval]** optie in het gedeelte linksonder van het **[!UICONTROL Resources]** venster. Dit kan een individuele exploitant, een groep exploitanten of een lijst van exploitanten zijn.

![](assets/s_ncs_user_task_edit_resource_validation.png)

Als u een lijst met operatoren wilt opgeven, klikt u op de **[!UICONTROL Edit...]** koppeling rechts van de eerste controleur en voegt u zoveel operatoren toe als nodig is, zoals hieronder wordt getoond:

![](assets/s_ncs_user_task_edit_resource_operators.png)

U kunt een goedkeuringsschema voor de taak definiëren in de onderste sectie van het configuratievenster voor de controleur. Standaard hebben revisoren drie dagen vanaf de verzenddatum om de taak goed te keuren. Het is mogelijk om een herinnering te vormen, die automatisch aan de betrokken exploitanten vóór de goedkeuringstermijn zal worden verzonden.

![](assets/s_ncs_user_edit_op_valid_calendar.png)

De persoon die met de taak is belast, kan zichzelf de taak toevertrouwen om de taak goed te keuren, ook al zijn hiervoor al andere exploitanten aangewezen. Als er geen controleur is gedefinieerd, worden de meldingen verzonden naar de persoon die verantwoordelijk is voor de taak. Alle andere Adobe Campagneontwikkelaars met **[!UICONTROL Administrator]** rechten kunnen de taak ook goedkeuren. Ze ontvangen echter geen meldingen.

### Documenten waarnaar wordt verwezen {#documents-referenced}

Het is mogelijk om documenten en marketing middelen aan een taak toe te voegen (voor meer op dit, verwijs naar het [Beheer van marketing middelen](../../campaign/using/managing-marketing-resources.md)). Open hiertoe de taak en klik op het **[!UICONTROL Documents]** pictogram op de taakwerkbalk.

Klik **[!UICONTROL Add]** en selecteer het document dat aan uw taak moet worden toegevoegd. Hetzelfde proces toepassen voor marketingbronnen.

![](assets/s_ncs_user_task_edit_documents.png)

Documenten waarnaar wordt verwezen, worden weergegeven in de meldingen die worden verzonden naar de bij de taak betrokken exploitanten en op het taakdashboard.

![](assets/s_ncs_user_task_notification_documents.png)

### Uitvoeringsschema {#execution-schedule}

De geldigheidsperiode van een taak wordt vermeld op de **[!UICONTROL Start]** en de **[!UICONTROL End]** gebieden. De geplande belasting geeft de werklast weer die gedurende de periode moet worden uitgevoerd. Het wordt uitgedrukt in dagen of uren.

>[!NOTE]
>
>De levenscyclus van een taak wordt gepresenteerd in de [levenscyclus](#life-cycle).

Het **[!UICONTROL Workload performed]** veld wordt ook uitgedrukt in dagen en uren. Hiermee kunt u de voortgang van de taak handmatig bijwerken ten opzichte van de geplande werkbelasting.

![](assets/s_ncs_user_task_percentage_done_enter.png)

De takenlijst, uitgedrukt als een percentage, wordt automatisch bijgewerkt op basis **[!UICONTROL Progress status]** van de door de betrokken marktdeelnemers uitgevoerde taken. U kunt de gegevens handmatig invoeren.

Deze informatie kan in het taakdashboard worden bekeken.

![](assets/s_ncs_user_task_percentage_done_from_dashboard.png)

Het is ook zichtbaar in het campagnelusje.

![](assets/s_ncs_user_task_percentage_done_from_op.png)

Als de einddatum van de planning voor het uitvoeren van de taak is bereikt maar de taak niet is voltooid, wordt de taak **[!UICONTROL Late]** uitgevoerd. Er wordt ook een waarschuwingsbericht weergegeven voor waarschuwingsoperatoren.

Raadpleeg voor meer informatie de [status Voortgang van een taak](#progress-status-of-a-task).

### Uitgaven en ontvangsten {#expenses-and-revenues}

U kunt gerelateerde uitgaven en verwachte inkomsten voor elke taak definiëren. Deze worden berekend en vervolgens geconsolideerd voor de campagne waaraan de taak is gekoppeld.

Klik op het **[!UICONTROL Expenses and revenue]** pictogram op de taakwerkbalk om deze informatie op te geven.

![](assets/s_ncs_user_task_edit_costs.png)

De begroting die standaard in rekening wordt gebracht, is de begroting van de campagne waaraan de taak is gekoppeld. Deze wordt weergegeven in de taakdetails.

>[!NOTE]
>
>Voor meer informatie over uitgaven en begrotingen, zie [kostenvastlegging, berekening en het in rekening brengen](../../campaign/using/controlling-costs.md#cost-commitment--calculation-and-charging).

In dit venster kunt u ook de te bereiken doelstellingen definiëren. De doelstellingen worden uitgedrukt in de geraamde ontvangsten voor de taak.

### Serviceproviders {#service-providers}

Een externe dienstverlener kan bij het beheer van een taak worden betrokken.

Hiervoor bewerkt u de taakeigenschappen en selecteert u de betreffende serviceprovider. De kostencategorieën verbonden aan de dienstverlener worden automatisch vermeld in de centrale sectie van het venster.

Voor meer op dit, verwijs naar het [Creëren van een dienstverlener en zijn kostencategorieën](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories).

Selecteer de kostencategorieën met betrekking tot de uitvoering van de taak. Hiervoor selecteert u het type kosten en voegt u, indien nodig, een toeslag toe.

![](assets/s_ncs_user_task_edit_simple_costs_tab.png)

>[!NOTE]
>
>De methode voor het beheer van budgetten en kosten wordt gepresenteerd in de vorm van [beheerskosten](../../campaign/using/controlling-costs.md).

Wanneer een dienstverlener wordt geselecteerd, wordt het getoond in het taakdashboard:

![](assets/s_ncs_user_task_supplier_view.png)

### Te late taken {#late-tasks}

Een taak is te laat als het zijn einddatum heeft bereikt zonder zijn status te veranderen in **[!UICONTROL Finished]**. Standaard wordt geen enkele operator gewaarschuwd wanneer een taak te laat is. U kunt de levering van een bericht-e-mail configureren: alle exploitanten kunnen op de hoogte worden gesteld , ook al zijn zij niet bij de taak betrokken .

Ga naar het **[!UICONTROL Resources]** vak en voeg de operator toe aan het **[!UICONTROL Assignation]** veld. Selecteer een groep operatoren om meerdere personen op de hoogte te stellen.

![](assets/mrm_task_alert_if_late.png)

### Eerste meldingen {#initial-notifications}

Wanneer u een taak maakt of wijzigt met een begindatum in de toekomst, biedt Adobe Campaign u aan een e-mail te sturen naar de persoon die verantwoordelijk is voor de taak om hem te laten weten wanneer de taak wordt gestart.

![](assets/mrm_task_first_notif.png)

Nochtans, als de taak u creeert ver weg is, kan het verkieslijk zijn om het bericht te plannen dat moet worden verzonden alvorens de taak begint. Als de taak bijvoorbeeld binnen een maand begint, kunt u de verantwoordelijke persoon één week voordat deze begint op de hoogte stellen.

Als u een melding wilt plannen, gaat u naar het **[!UICONTROL Resources]** vak en gebruikt u het **[!UICONTROL Initial notification]** veld.

![](assets/mrm_task_alert_before.png)

* Voor taken binnen campagnes, selecteer een specifieke datum en een tijd.
* Voor taken binnen campagnemalplaatjes, wordt de berichttijd uitgedrukt als resterende tijd alvorens de taak begint (bijvoorbeeld, als u 2d op het **[!UICONTROL Initial notification]** gebied ingaat, zal e-mail 2 dagen vóór de datum van de taakaanvang worden verzonden).

Als u een melding hebt gepland, kunt u tijdens het opslaan van de taak nog steeds een melding verzenden. U kunt besluiten om het te verzenden en dit zal niet het geplande bericht vervangen.

### Aan een programma gekoppelde taak {#task-linked-to-a-program}

U kunt taken rechtstreeks in een programma maken om acties te beheren die betrekking hebben op de algehele organisatie en niet op een specifieke campagne (bijvoorbeeld een vergadering om het thema van komende campagnes binnen het programma te bespreken). De taak wordt weergegeven in het programma.

Een taak maken die rechtstreeks aan een programma is gekoppeld:

1. Open het programma: ga naar de startpagina **[!UICONTROL Campaigns > Browse > Other choices > Programs]**. Het algemene programma wordt geopend in het rechtergedeelte van het venster.
1. Klik in het programma op het gewenste programma: er verschijnt een venster met het programma erin .
1. Klik in dit venster op **[!UICONTROL Open]**. Het programma wordt geopend.
1. Klik op de **[!UICONTROL Add]** knop boven het schema aan de rechterkant en klik vervolgens op **[!UICONTROL Add a task]**.

![](assets/mrm_task_create_from_prg.png)

### Beschikbaarheid van bedieners {#operator-availability}

In het taakdashboard, wijst een pictogram naast de naam van de exploitant erop dat zij reeds aan een andere taak of een gebeurtenis tijdens de periode werken die door de taak wordt behandeld. (Taak die de exploitant belast is met of betrokken is bij: hij verschijnt in het **[!UICONTROL Assigned to]** veld of in het **[!UICONTROL Resources]** taakvak).

![](assets/mrm_task_alert_operator_busy.png)

### Taak in een werkstroom {#task-in-a-workflow}

Als u een **[!UICONTROL Task]** element in een campagneworkflow gebruikt, kunt u twee scenario&#39;s definiëren, afhankelijk van het feit of de taak is goedgekeurd of niet.

![](assets/mrm_task_in_workflow.png)

In de campagneworkflows vindt u de **[!UICONTROL Task]** activiteit op het **[!UICONTROL Flow control]** tabblad.

## Typen taken {#types-of-task}

Wanneer u taken maakt via een campagne, kunt u specifieke taken maken. Het taaktype wordt gedefinieerd in de geselecteerde sjabloon.

![](assets/s_ncs_user_task_select_template.png)

De volgende taken kunnen worden gepland:

* **[!UICONTROL Control task]**, verwijst naar [controletaken](#control-tasks),
* **[!UICONTROL Marketing resource creation task]**, verwijst naar de [groeperingstaak](#grouping-task),
* **[!UICONTROL Grouping task]**, verwijst naar de [groeperingstaak](#grouping-task),
* **[!UICONTROL Notification task]**, verwijs naar de [Meldingstaak](#notification-task).

>[!NOTE]
>
>**[!UICONTROL Control task]** en **[!UICONTROL Grouping]** taken kunnen **alleen** via het campagnemdashboard worden gemaakt .\
>Zij worden getoond in de taakkaart van de exploitant waaraan zij worden toegewezen. Zie [Toegang krijgen tot taken](#accessing-tasks).

### Taken beheren {#control-tasks}

A **[!UICONTROL Control task]** is gekoppeld aan de goedkeuring van de levering: goedkeuring van de bestemming, de inhoud, het extractiebestand, het budget of het bewijs.

![](assets/s_ncs_user_task_new_control.png)

Zodra het wordt gecreeerd, wordt de taak toegevoegd aan het campagnesdashboard.

![](assets/s_ncs_user_task_edit_from_board.png)

U kunt het vervolgens bewerken en de parameters ervan opgeven.

### Taak voor het maken van marketingmiddelen {#marketing-resource-creation-task}

Een marketing middelaanmaaktaak kan worden gebruikt om de verwezenlijking en de publicatie van een marketing middel te beheren. Als u een bron beheert via een taak en niet via de bron zelf, kunt u:

* Beheer het proces voor het maken van bronnen via een campagne.
* Bekijk het proces van de middelverwezenlijking in een programma.
* Het maken van bronnen beheren (herinneringen, meldingen).
* Berekenen en controleren van de kosten in verband met het creëren van bronnen.
* Goedkeuren en publiceren van de bron via de taak (als de relevante optie is ingeschakeld).

#### Interactie tussen de taak en de daaraan gekoppelde bron {#interaction-between-the-task-and-its-linked-resource}

De het creëren van marketingmiddelen taak staat in wisselwerking met het middel verbonden aan het. Dit betekent:

* Het programma voor het aanmaken van bronnen en de bijbehorende kosten worden via de taak beheerd.
* Operatoren kunnen aan de bron werken zoals normaal (downloaden of uploaden, vergrendelen en ontgrendelen): dit heeft geen invloed op de taak .
* Goedkeuring en publicatie van bronnen kunnen worden uitgevoerd via de taak: als de **[!UICONTROL Publish the marketing resource]** optie wordt toegelaten, wordt het middel goedgekeurd en automatisch gepubliceerd zodra de taak wordt gebeëindigd. Als de optie niet wordt toegelaten, werken de taak en het middel niet: de ene actie heeft geen invloed op de andere.

   U kunt een reeks gekoppelde taken gebruiken om een volledige goedkeuringscyclus te definiëren. Schakel de **[!UICONTROL Publish the marketing resource]** optie alleen in voor de laatste taak: alle taken moeten zijn voltooid om de bron te kunnen publiceren . Bovendien wanneer u een kind marketing middeltaak creeert, zal het middel automatisch in de kindtaak worden geselecteerd.

   * **Via de bron**: als u de bron ter goedkeuring voorlegt of goedkeurt , hebben deze acties geen invloed op de taak .
   * **Via de taak**: als de **[!UICONTROL Publish the marketing resource]** optie in de taak wordt gecontroleerd, wordt het middel goedgekeurd en automatisch gepubliceerd zodra de taak (zie hierboven) wordt gebeëindigd. Als de optie niet wordt gecontroleerd, zullen de taak en het middel niet in wisselwerking staan: de ene actie heeft geen invloed op de andere.

#### Het vormen van een marketing middelaanmaaktaak {#configuring-a-marketing-resource-creation-task}

De persoon die de taak controleert is niet noodzakelijk de zelfde persoon die de inhoud controleert die in het middel wordt bepaald. Nochtans, als de **[!UICONTROL Publish the marketing resource]** optie wordt gecontroleerd (zie hieronder), wordt de taakrecensent gemachtigd om de middelinhoud goed te keuren, aangezien het voltooien van de taak automatisch het middel goedkeurt (of, als geen recensent wordt bepaald, de taakmanager).

![](assets/mrm_task_asset_creation.png)

Definieer in het **[!UICONTROL Marketing resource]** veld de bron die u via deze taak wilt beheren. U kunt:

* Selecteer een bestaande bron: de vervolgkeuzelijst bevat alle bronnen met de status **[!UICONTROL Being edited]**.
* Een bron maken: Klik op het **[!UICONTROL Select the link]** pictogram en klik vervolgens op het **[!UICONTROL Create]** pictogram.

Met de **[!UICONTROL Publish the marketing resource]** optie kunt u het publiceren van bronnen automatiseren: zodra de taak is **[!UICONTROL Finished]**, schakelt de status van de bron automatisch over naar **[!UICONTROL Published]**, zelfs als deze niet ter goedkeuring of goedkeuring is ingediend, inclusief als de controleur die de taak voltooit, niet de inhoudscontroleur is die in de bron is gedefinieerd.

De **[!UICONTROL Publish the resource]** knop wordt beschikbaar gesteld en de revisor van de publicatie-resource ontvangt een e-mailbericht om hem te laten weten dat deze klaar is om te worden gepubliceerd. Op het **[!UICONTROL Edit > Tracking]** tabblad wordt het reviseren en publiceren door de taakcontroleur zichtbaar. Als een workflow voor de naverwerking van bronnen is gedefinieerd, wordt deze nu uitgevoerd.

![](assets/mrm_resource_audit_tab.png)

### Groeperingstaak {#grouping-task}

Met de **[!UICONTROL Grouping task]** typetaak kunt u verschillende taken groeperen en het beheer van hun voortgang en goedkeuring synchroniseren.

Groeperingstaken hebben geen gekoppelde uitgaven of middelen.

Alle taken die aan een groeperingstaak worden gegroepeerd kunnen op zijn eigen dashboard worden gezien. Hiermee kunt u de lijst met taken filteren en alleen de taken weergeven die u interesseren.

Groeperingstaken hebben een koppeling waarmee u eenvoudig een gegroepeerde taak kunt maken.

Als u een gegroepeerde taak wilt maken op basis van een groeperingstaak, gaat u naar het campagnemashboard en klikt u op de naam van de groeperingstaak om de beschrijving weer te geven. Klik vervolgens op **[!UICONTROL Add a task]**.

![](assets/mrm_task_grouped_create.png)

Als u echter al een taak hebt gemaakt die u aan een groeperingstaak wilt koppelen, kunt u deze taak uitvoeren via het **[!UICONTROL Linked to]** veld van het **[!UICONTROL Properties]** vak.

![](assets/s_ncs_user_task_group_with.png)

### Meldingstaak {#notification-task}

Met behulp van meldingstaken kunt u e-mailleveringen plannen (aan een operator, een groep operatoren, een serviceprovider, enzovoort). Hiermee kunt u herinneringen plannen, bijvoorbeeld om iemand te laten weten dat een campagne binnenkort wordt voltooid, of om documenten te verzenden voordat een campagne wordt gestart, zodat exploitanten deze kunnen voorbereiden. Dit betekent dat u uw communicatie binnen uw campagne of programma kunt bijhouden en de uitgevoerde acties beter in het oog kunt houden.

#### Levenscyclus {#life-cycle}

De taken van het bericht vereisen geen goedkeuring. Dit betekent dat hun levenscyclus eenvoudiger is dan die van een standaardtaak:

![](assets/mrm_task_notif_lifecycle.png)

Een meldingstaak kan de volgende statussen hebben:

* **[!UICONTROL Scheduled]** totdat het e-mailbericht is verzonden
* **[!UICONTROL In progress]** zodra het e-mailbericht is verzonden en tot de einddatum is bereikt
* **[!UICONTROL Finished]** wanneer de einddatum is bereikt.

#### Configuratie {#configuration}

![](assets/mrm_task_notif_dashboard.png)

Tijdens het creëren, moeten de volgende elementen in de taak zijn ingegaan:

* **[!UICONTROL Assigned to]** : de exploitant of de groep exploitanten die de e-mail zullen ontvangen. Als u de taak opnieuw toewijst nadat de e-mail is verzonden, wordt de e-mail niet verzonden naar de nieuwe operator (hiervoor moet u de taak opnieuw initialiseren en de begindatum wijzigen).
* **Begindatum** taak: de datum waarop de e-mail met de melding wordt verzonden. Deze datum moet in de toekomst plaatsvinden op het moment van de registratie van de taak.
* **Einddatum** taak: datum waarop de taakstatus verandert in **[!UICONTROL Finished]**. Standaard is de einddatum gelijk aan de begindatum. Nochtans, laat het toewijzen van een duur aan de taak u de hoeveelheid tijd symboliseren die de exploitant in het programma moet handelen, indien nodig.
* **[!UICONTROL Description]** : de hier ingevoerde tekst wordt in de tekst van het e-mailbericht vermeld .

   ![](assets/mrm_task_notif_dashboard_msg.png)

U kunt een bijlage aan de taak en aan het bericht e-mail toevoegen. Klik hiertoe op het **[!UICONTROL Documents]** pictogram in de werkbalk in de rechterbovenhoek.

## Levenscyclus {#life-cycle-1}

### Koppelingen tussen taken {#links-between-tasks}

Met de **[!UICONTROL Properties]** knop in elke taak kunt u de koppelingen tussen taken in een campagne definiëren. U kunt taken in subtaken verdelen gebruikend een groeperende taak (zie [Gekoppelde taken](#linked-tasks)), of gebiedsdelen tussen de taken bepalen (zie de taken [van de](#grouping-tasks)Groepering).

#### Gekoppelde taken {#linked-tasks}

Gebruik het **[!UICONTROL Linked task]** veld om taken te koppelen aan een groeperingstaak. Zie [Taaktypen](#types-of-task).

In het volgende voorbeeld wordt de goedkeuring van het richten opgesplitst in vier subtaken.

![](assets/s_ncs_user_task_linked_tasks.png)

Elke subtaak is een standaardtaak die is gekoppeld aan de hoofdtaak.

![](assets/s_ncs_user_task_depends_on.png)

#### Groeperingstaken {#grouping-tasks}

Gebruik het **[!UICONTROL Grouped to]** veld om te zorgen dat de uitvoering van een taak afhankelijk is van de uitvoering van een andere taak.

![](assets/s_ncs_user_task_group_with.png)

De afhankelijkheid tussen taken wordt vertegenwoordigd door pijlen in het campagnedashboard.

![](assets/s_ncs_user_task_dependencies_from_board.png)

In het geval van gegroepeerde taken wijst Adobe Campaign automatisch de einddatum van de bovenliggende taak toe aan de onderliggende taak als begindatum. Als een **Uitnodigingstaak** maken bijvoorbeeld eindigt op 15 oktober om 15.30 uur, wordt de taak **Uitnodiging-mail** verzenden voor het uitvoeren van een onderliggende taak gestart op 15 oktober om 15.30 uur.

Bovendien als u het eind van een oudertaak uitstelt, kunnen sommige van zijn kindtaken worden beïnvloed: dit zijn de kindtaken waarvan status is **[!UICONTROL Scheduled]** en de waarvan begindatum vroeger dan de nieuwe einddatum van de oudertaak is. De duur van de taak blijft ongewijzigd. Als de begindatum van een kindtaak later dan de nieuwe einddatum van de oudertaak is, wordt de kindtaak niet beïnvloed.

**Voorbeeld**

Een oudertaak die op 9 oktober om 5PM wordt gepland te beëindigen heeft twee kindtaken, taak A en taak B. Taak A moet op 10 oktober om 2 uur beginnen en taak B moet op 12 oktober om 8.00 uur beginnen.

Laten we de bovenliggende taak uitstellen: het loopt nu af op 11 oktober om 13.00 uur. Alleen taak A wordt uitgesteld en begint op 11 oktober om 13.00 uur.

![](assets/mrm_task_parent_postpones_child.png)

### Uitvoerstatus van een taak {#execution-status-of-a-task}

De status van de taak kan in de taakkaart worden bekeken. De uitvoeringsstatus van een taak wordt automatisch bijgewerkt op basis van de acties van de operator.

Een taak kan zijn: **[!UICONTROL Scheduled]**, **[!UICONTROL In progress]**, **[!UICONTROL Finished]**, **[!UICONTROL Canceled]**, **[!UICONTROL Pending approval]** of **[!UICONTROL Rejected]**.

* Wanneer een taak wordt gecreeerd, is het **[!UICONTROL Scheduled]** of zijn begindatum in de toekomst is. Deze status blijft behouden totdat de begindatum is bereikt.
* Zodra het is begonnen, is de taak **[!UICONTROL In progress]**. Wanneer de persoon die verantwoordelijk is voor de taak het sluit, verandert het in **[!UICONTROL Finished]**.
* Als er een controleur is gedefinieerd, wordt de taak uitgevoerd **[!UICONTROL Pending approval]** zodra de persoon die verantwoordelijk is voor het sluiten ervan en totdat de controleur het goedkeurt. Als de controleur het afwijst, wordt de taak **[!UICONTROL Rejected]** uitgevoerd.
* Een taak kan door de verantwoordelijke persoon via het dashboard of het **[!UICONTROL Task map]** door de **[!UICONTROL Cancel]** knoop worden geannuleerd.
* Als u een taak wilt plannen, voert u in de toekomst een begindatum in. Vervolgens kunt u een eerste melding verzenden naar de Adobe Campagneontwikkelaars die bij het uitvoeren van de taak zijn betrokken. Zie [Volledige levenscyclus](#complete-task-life-cycle)van de taak.

>[!NOTE]
>
>* De taakstatus wordt automatisch bijgewerkt.
>* Zelfs als de geldigheidsperiode is voltooid, worden taken die niet zijn afgesloten, nog steeds opgenomen in de lijst met actieve taken. Een waarschuwing waarschuwt exploitanten dat de taak laat is.
>



### Voortgangsstatus van een taak {#progress-status-of-a-task}

Naast de uitvoeringsstatus kan een taak worden gekoppeld aan een vorderingsstatus: **[!UICONTROL Late]**, **[!UICONTROL To approve]**, **[!UICONTROL To do today]** of **[!UICONTROL To do this week]**. Deze informatie wordt automatisch ingevoerd volgens het taakprogramma.

U kunt de lijst met taken filteren op processtatus of voortgangsstatus.

Raadpleeg [Toegang tot taken](#accessing-tasks)voor meer informatie.

### Volledige levenscyclus van taken {#complete-task-life-cycle}

Hieronder staan de fasen van een volledige taaklevenscyclus waarvoor de verantwoordelijke persoon deelnemers en revisoren heeft gedefinieerd.

1. De verantwoordelijke persoon creëert de taak en voert de verschillende velden in. Raadpleeg [Een nieuwe taak](#creating-a-new-task)maken voor meer informatie.

   Wanneer het creëren van en het uitgeven van een taak die in de toekomst **(zolang de datum van de taakaanvang niet wordt bereikt) wordt** gepland, is het mogelijk om een bericht naar deelnemers en managers te verzenden om hen te laten weten dat een nieuwe taak is gepland.

   ![](assets/s_ncs_user_task_planed_send_message.png)

   Klik op **[!UICONTROL Yes]** deze eerste melding verzenden. Deze melding geeft uitleg over de volgende taak en bevat informatie over de inhoud en het aantal dagen dat resteert tot de deadline.

   Wanneer een taak wordt gecreeerd en voor de toekomst gepland, is zijn status **[!UICONTROL Scheduled]**.

1. Op de datum van de taakaanvang, ontvangen de verantwoordelijke persoon en de deelnemers een bericht om hen te vertellen dat de taak is begonnen. De status verandert in **[!UICONTROL In progress]**.
1. Na de voltooiing van de sectie die aan hen wordt toegewezen, kunnen de deelnemers de taak goedkeuren, of:

   * via het e-mailbericht.
   * via de console of de webinterface, in het taakdashboard.

      ![](assets/s_ncs_user_task_start_rea.png)

1. Telkens wanneer een deelnemer een taak goedkeurt, wordt de voortgangsstatus van de taak bijgewerkt.

   ![](assets/s_ncs_user_task_percentage_done_op.png)

1. De controleur ontvangt een e-mail met een bericht dat hij of zij de hem toegewezen sectie heeft voltooid.

   Zij kunnen de vooruitgang op het taakdashboard volgen.

   ![](assets/s_ncs_user_task_follow_from_dashboard.png)

1. Zodra de persoon die verantwoordelijk is voor de taak besluit dat het wordt gebeëindigd, kunnen zij het sluiten, gebruikend of de verbinding in het bericht e-mail die werd verzonden toen de taak werd begonnen, de console, of de interface.

   ![](assets/s_ncs_user_task_console_ressource_validation.png)

   >[!NOTE]
   >
   >De persoon die verantwoordelijk is voor een taak kan deze op elk moment sluiten, zelfs als er geen goedkeuringen zijn. De vorderingsstatus wordt automatisch gewijzigd in 100%.

1. De taakstatus verandert in **[!UICONTROL To approve]** en er wordt een melding naar de controleur verzonden.

   Ze keuren de taak goed via de e-mail met meldingen, de console of de webinterface.

   Ze kunnen actie ondernemen via het campagnedashboard:

   ![](assets/s_ncs_user_task_console_validation.png)

   Zij kunnen de knoop van de taakgoedkeuring ook gebruiken:

   ![](assets/s_ncs_user_task__validation.png)

   >[!NOTE]
   >
   >De taakstatus verandert alleen in **[!UICONTROL To approve]** als u de **[!UICONTROL Enable task validation]** optie hebt ingeschakeld in het **[!UICONTROL Resources]** venster van de taak.\
   >Als de controleur de taak weigert, verandert de status in **[!UICONTROL Rejected]** en wordt de levenscyclus van de taak automatisch hervat.

1. De taakstatus verandert in **[!UICONTROL Finished]**. Aan alle betrokkenen wordt een kennisgeving gezonden.

   >[!NOTE]
   >
   >Als een taak is voltooid, kan de levenscyclus ervan opnieuw worden geïnitialiseerd door de verantwoordelijke persoon. U doet dit door de taak te openen en op de **[!UICONTROL Reset task to execute it again...]** koppeling onder aan het dashboard te klikken.

