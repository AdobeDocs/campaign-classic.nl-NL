---
title: Uitvoering van controlewerkstroom
seo-title: Uitvoering van controlewerkstroom
description: Uitvoering van controlewerkstroom
seo-description: null
page-status-flag: never-activated
uuid: 4d215ff4-a61d-4294-8f15-17c612022577
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 6a71f5ee-c8e0-4ac4-acae-6dffbf799d0c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e04eb83a7c2e29f8d3ea6458dd3f0e780dfb9c3

---


# Uitvoering van controlewerkstroom {#monitoring-workflow-execution}

Deze sectie geeft informatie over hoe te om de uitvoering van uw werkschema&#39;s te controleren.

In [deze sectie](../../workflow/using/supervising-workflows.md#supervising-workflows)is ook een gebruiksscenario beschikbaar voor het maken van een workflow waarmee u de status kunt controleren van een set werkstromen die worden gepauzeerd, gestopt of &#39;met fouten&#39;.

Daarnaast kunnen beheerders van de instantie het **audittrail** gebruiken om activiteiten en laatste wijzigingen in workflows, de status van uw workflows, te controleren. Raadpleeg de [desbetreffende sectie](../../production/using/audit-trail.md)voor meer informatie hierover.

In [deze pagina](https://helpx.adobe.com/campaign/kb/acc-maintenance.html)worden extra manieren weergegeven om de verschillende campagneprocessen te controleren.

## Voortgang weergeven {#displaying-progress}

U kunt de uitvoering controleren door de voortgang weer te geven met het juiste pictogram op de werkbalk.

Met het **[!UICONTROL Display progress information]** pictogram kunt u de status en het activiteitenresultaat weergeven in het uitvoeringsscherm.

![](assets/s_user_segmentation_toolbar_progr.png)

Als deze optie is geselecteerd, worden uitgevoerde activiteiten in blauw weergegeven, knipperende activiteiten in behandeling, worden waarschuwingen in oranje weergegeven en fouten in rood. Met deze optie geeft u ook het resultaat weer van activiteiten bij de uitgaande overgang, gevolgd door het label van het resultaat zoals gedefinieerd in de eigenschappen activity en de duur van de taak als deze langer is dan één seconde

![](assets/s_user_segmentation_results.png)

## Logboeken weergeven {#displaying-logs}

Het logbestand bevat de geschiedenis of audittrail van de workflow. Hiermee worden alle gebruikersacties, alle uitgevoerde bewerkingen en aangetroffen fouten geregistreerd. U kunt:

* Selecteer het **[!UICONTROL Tracking]** tabblad in het detail. Deze lijst bevat alle workflowberichten.

   ![](assets/new-workflow-display-log-tab.png)

* Filter de logboekberichten door activiteit. Klik hiertoe op **[!UICONTROL Display the tasks and the log]** de werkbalk boven het diagram om de tabbladen **[!UICONTROL Log]** en **[!UICONTROL Tasks]** tabbladen onder het diagram weer te geven. Selecteer een activiteit om alle verwante berichten te bekijken. Deze lijst bevat alle berichten als er geen activiteit is geselecteerd.

   ![](assets/new-workflow-display-log-activity.png)

   >[!NOTE]
   >
   >Klik op de achtergrond van het diagram om de selectie van alle elementen op te heffen.

* Alleen die berichten weergeven die zijn gekoppeld aan een bepaalde taak. Om dit te doen, selecteer het **[!UICONTROL Tasks]** lusje, en selecteer dan een activiteit in het diagram om de lijst te beperken. Dubbelklik op een taak om de informatie weer te geven; het laatste tabblad in het venster bevat het logboek.

   ![](assets/new-workflow-display-tasks-activity.png)

   Met de **[!UICONTROL Details...]** knop kunt u alle aanvullende informatie over de uitvoering van de activiteit weergeven. U kunt bijvoorbeeld de validatieoperator weergeven en, indien van toepassing, de opmerking die ze tijdens de goedkeuring hebben ingevoerd, zoals in het volgende voorbeeld:

   ![](assets/new-workflow-display-tasks-activity-details.png)

>[!NOTE]
>
>Het logbestand wordt niet gewist wanneer een workflow opnieuw wordt gestart. Alle berichten worden bewaard. Als u de berichten van een vorige uitvoering wilt verwijderen, moet u de geschiedenis wissen.

Het logboek toont de chronologische lijst van uitvoeringsberichten met betrekking tot het richten van werkschemaactiviteiten.

* Logboek van een doelgerichte campagne

   Nadat een doelcampagne is uitgevoerd, klikt u op het **[!UICONTROL Tracking]** tabblad om het uitvoeringstraject weer te geven.

   ![](assets/s_user_segmentation_journal.png)

   Alle campagneberichten worden getoond: uitgevoerde campagnes en waarschuwingen of fouten.

* Logboek van een activiteit

   U kunt het uitvoeringslogboek en de details van elke activiteit ook bekijken. Er zijn twee manieren om dit te doen:

   1. Selecteer de doelactiviteit en klik op het **[!UICONTROL Display the tasks and the log]** pictogram.

      ![](assets/s_user_segmentation_show_logs.png)

      In de onderste sectie van het diagram ziet u twee tabbladen: Logboek en taken.

      De activiteiten die binnen het diagram worden geselecteerd handelen als filters op het logboek en de taaklijst.

      ![](assets/s_user_segmentation_logs.png)

   1. Klik met de rechtermuisknop op de doelactiviteit en selecteer **[!UICONTROL Display logs]**.

      ![](assets/s_user_segmentation_logs_menu.png)

      Het logboek wordt getoond in een afzonderlijk venster.

## De logbestanden leegmaken {#purging-the-logs}

Workflowgeschiedenis wordt niet automatisch gewist: alle berichten worden standaard gehouden. De geschiedenis kan worden gewist via het **[!UICONTROL File > Actions]** menu of door op de **[!UICONTROL Actions]** knop in de werkbalk boven de lijst te klikken. Selecteer **[!UICONTROL Purge history]**. De opties in het **[!UICONTROL Actions]** menu worden beschreven in de sectie [Handelingen](../../workflow/using/executing-a-workflow.md#actions-toolbar) .

![](assets/purge_historique.png)

## Worktables and workflow schema {#worktables-and-workflow-schema}

De workflow geeft worktables weer die via bepaalde activiteiten kunnen worden gemanipuleerd. Met Adobe Campaign kunt u via gegevensbeheeractiviteiten de kolommen van worktables in de workflow aanpassen, hernoemen en verrijken, bijvoorbeeld om ze aan te passen aan de nomenclatuur, afhankelijk van de behoeften van de klant, om aanvullende informatie te verzamelen over de co-begunstigde van een contract, enz.

Het is ook mogelijk om verbindingen tussen diverse het werkdimensies tot stand te brengen en afmetingsveranderingen te bepalen. Voor elk contract dat bijvoorbeeld in de database is opgenomen, richt u zich tot de hoofdhouder en gebruikt u de gegevens van de medehouder in de aanvullende informatie.

De werktabellen van de workflow worden automatisch verwijderd wanneer de workflow wordt gepassiveerd. Als u een werktabel wilt behouden, slaat u deze op in een lijst via de **[!UICONTROL List update]** activiteit (zie [Lijstupdate](../../workflow/using/list-update.md)).

## Fouten beheren {#managing-errors}

Wanneer een fout optreedt, wordt de werkstroom gepauzeerd en wordt de activiteit uitgevoerd wanneer de fout optrad met rood. In het workflowoverzicht (**[!UICONTROL Monitoring]** universum > **[!UICONTROL Workflows]** koppeling) kunt u alleen workflows met fouten weergeven, zoals hieronder wordt weergegeven.

![](assets/wf-global-view_filter_only_errors.png)

In de Adobe Campagneverkenner wordt standaard een **[!UICONTROL Failed]** kolom weergegeven in de workflowlijst.

![](assets/wf-explorer_errors_col.png)

Wanneer een workflow een fout bevat, worden de operatoren die tot de groep voor workflowtoezicht behoren, via e-mail op de hoogte gebracht, zolang hun e-mailadres in hun profiel wordt vermeld. Deze groep is geselecteerd in het **[!UICONTROL Supervisor(s)]** veld met de workfloweigenschappen.

![](assets/wf-properties_select-supervisors.png)

De berichtinhoud wordt gevormd in het **[!UICONTROL Workflow manager notification]** standaardmalplaatje: Deze sjabloon is geselecteerd op het **[!UICONTROL Execution]** tabblad van de workfloweigenschappen. Het bericht bevat de naam van de foutworkflow en de betreffende taak.

Voorbeeld van melding:

![](assets/wf-notification_error-msg.png)

Met de koppeling hebt u toegang tot de Adobe Campagne-console in de webmodus en kunt u werken aan de foutworkflow nadat u zich hebt aangemeld.

![](assets/wf-notification_error-console.png)

U kunt de werkstroom zodanig configureren dat deze niet wordt gepauzeerd en verder wordt uitgevoerd in het geval van fouten. Hiervoor bewerkt u de workflow **[!UICONTROL Properties]** en selecteert u in de **[!UICONTROL Error management]** sectie de **[!UICONTROL Ignore]** optie in het **[!UICONTROL In case of error]** veld. Vervolgens kunt u opgeven hoeveel opeenvolgende fouten kunnen worden genegeerd voordat het proces wordt gepauzeerd.

In dit geval wordt de fouttaak afgebroken. Deze modus is vooral geschikt voor workflows die zijn ontworpen om de campagne later weer te geven (periodieke acties).

![](assets/wf_edit_properties_for_error_mgt.png)

>[!NOTE]
>
>U kunt deze configuratie afzonderlijk toepassen voor elke activiteit. Hiervoor bewerkt u de eigenschappen van de activiteit en selecteert u de modus voor foutbeheer op het **[!UICONTROL Advanced]** tabblad.

Raadpleeg de [desbetreffende sectie](../../production/using/workflow-execution.md)voor meer informatie over het oplossen van problemen bij de uitvoering van workflows.

## Verwerkingsfouten {#processing-errors}

Met betrekking tot activiteiten geeft de **[!UICONTROL Process errors]** optie een specifieke overgang weer die wordt ingeschakeld als een fout wordt gegenereerd. In dit geval gaat de workflow niet naar de foutmodus en gaat de uitvoering verder.

Fouten waarmee rekening wordt gehouden, zijn fouten in het bestandssysteem (het bestand kan niet worden verplaatst, de map kan niet worden geopend, enz.).

Deze optie verwerkt geen fouten met betrekking tot activiteitsconfiguratie, d.w.z. ongeldige waarden. Fouten met betrekking tot een onjuiste configuratie maken deze overgang niet mogelijk (map bestaat niet, enz.).

Als een werkstroom wordt gepauzeerd (handmatig of automatisch na een fout), start de **[!UICONTROL Start]** knop de werkstroomuitvoering opnieuw op de plaats waar deze is gestopt. De foutieve activiteit (of gepauzeerde activiteit) wordt opnieuw uitgevoerd. De vorige activiteiten worden niet opnieuw uitgevoerd.

Als u alle workflowactiviteiten opnieuw wilt uitvoeren, gebruikt u de **[!UICONTROL Restart]** knop.

Als u activiteiten wijzigt die al werden uitgevoerd, worden de wijzigingen niet in aanmerking genomen wanneer de werkstroom opnieuw wordt uitgevoerd.

Als u niet-uitgevoerde activiteiten wijzigt, wordt hiermee rekening gehouden wanneer de werkstroom opnieuw wordt uitgevoerd.

Als u gepauzeerde activiteiten wijzigt, kunnen de wijzigingen niet correct worden doorgevoerd wanneer de workflow opnieuw wordt gestart.

Indien mogelijk raden we u aan de workflow opnieuw te starten nadat u wijzigingen hebt aangebracht.

## Instantie controleren {#instance-supervision}

Op de **[!UICONTROL Instance supervision]** pagina kunt u de serveractiviteit van de campagne van Adobe bekijken en de lijst met workflows en leveringen met fouten weergeven.

Ga naar het **[!UICONTROL Monitoring]** universum en klik op de **[!UICONTROL General view]** koppeling om deze pagina te openen.

![](assets/wf-monitoring_from-homepage.png)

Klik op de **[!UICONTROL Workflows]** koppeling om alle workflows weer te geven. Gebruik de vervolgkeuzelijst om de workflows op het platform weer te geven op basis van hun status.

![](assets/wf-monitoring_edit-wf.png)

Klik op de koppeling in een workflow met fouten om deze te openen en het bijbehorende logboek weer te geven.

![](assets/wf-monitoring_edit-task-wf.png)

## Meerdere uitvoeringen voorkomen {#preventing-simultaneous-multiple-executions}

In één workflow kunnen meerdere uitvoeringen tegelijkertijd worden uitgevoerd. In sommige gevallen moet u dit voorkomen.

Bijvoorbeeld, kunt u een planner hebben die de werkschemauitvoering elk uur teweegbrengt, maar soms neemt de uitvoering van het volledige werkschema meer dan een uur. U kunt de uitvoering overslaan als de workflow al wordt uitgevoerd.

Als u een signaalactiviteit aan het begin van het werkschema hebt kunt u het signaal willen overslaan als het werkschema loopt.

Het algemene beginsel is als volgt:

![](assets/workflow-reentrancy-protection-principle.png)

De oplossing is een instantievariabele te gebruiken. Instantievariabelen worden gedeeld door alle parallelle uitvoeringen van de workflows.

Hier volgt een eenvoudige testworkflow:

![](assets/wkf_simultaneous_execution1.png)

De **[!UICONTROL Scheduler]** activeert elke minuut een gebeurtenis. De volgende **[!UICONTROL Test]** activiteit gaat de **isRunning** instantievariabele testen om al dan niet te besluiten om de uitvoering voort te zetten:

![](assets/wkf_simultaneous_execution2.png)

>[!NOTE]
>
>**isRunning** is een variabelenaam die voor dit voorbeeld wordt gekozen. Dit is geen ingebouwde variabele.

De activiteit onmiddellijk na **[!UICONTROL Test]** in de **ja** tak moet de instantievariabele in zijn **Initialisatiescript** plaatsen:

```
instance.vars.isRunning = true
```

De allerlaatste activiteit in de **ja** tak moet de variabele aan vals in zijn **Initialisatiescript** terugkeren:

```
instance.vars.isRunning = false
```

Let op:

* U kunt de huidige waarde van de instantievariabele controleren via het tabblad **Variabelen** in de workflow **Eigenschappen**.
* Instantievariabelen worden opnieuw ingesteld wanneer u een workflow opnieuw start.
* In JavaScript is een ongedefinieerde waarde in een test false, zodat de instantievariabele ook kan worden getest voordat deze is geïnitialiseerd.
* U kunt de activiteiten controleren die niet wegens dit mechanisme door een registrereninstructie aan het initialisatiescript van &quot;geen&quot;beëindigend worden verwerkt toe te voegen.

   ```
   logInfo("Workflow already running, parallel execution not allowed.");
   ```

In deze rubriek wordt een gebruiksgeval weergegeven: Updates [van gegevens](../../workflow/using/coordinating-data-updates.md)coördineren.

## Database-onderhoud {#database-maintenance}

Workflows gebruiken veel werktabellen die ruimte verbruiken en het hele platform vertragen als het niet wordt onderhouden. Raadpleeg deze [sectie](../../production/using/tables-to-maintain.md) voor meer informatie over databaseonderhoud.

Met de workflow voor het opruimen van **databases die toegankelijk is via het knooppunt** Beheer > Productie > Technische workflows **** , kunt u verouderde gegevens verwijderen om exponentiële groei van de database te voorkomen. De workflow wordt automatisch geactiveerd zonder tussenkomst van de gebruiker. Zie deze [sectie](../../production/using/database-cleanup-workflow.md).

U kunt ook specifieke technische workflows maken om overbodige gegevensverbruikende ruimte te wissen. Zie deze [sectie](../../production/using/application-objects.md) en deze [pagina](#purging-the-logs).

## Afhandeling van gepauzeerde workflows {#handling-of-paused-workflows}

Als een werkstroom wordt gepauzeerd, worden de werktabellen standaard niet gewist. Vanaf build 8880 worden workflows die al te lang in een pauzestatus zijn gepauzeerd, automatisch gestopt en worden hun werktabellen gewist. Dit gedrag wordt als volgt geactiveerd:

* De werkschema&#39;s die sinds meer dan 7 dagen zijn gepauzeerd verschijnen als waarschuwing in het controledashboard (en controle API) en een bericht wordt verzonden naar de supervisorgroep.
* Hetzelfde gebeurt elke week wanneer de **[!UICONTROL cleanupPausedWorkflows]** technische workflow wordt geactiveerd. Raadpleeg [deze sectie](../../workflow/using/delivery.md)voor meer informatie over de workflow.
* Na 4 meldingen (dat wil zeggen een maand in de pauzestatus) wordt de workflow onvoorwaardelijk beëindigd. Er wordt een logboek weergegeven in de workflow nadat het is gestopt. De tabellen worden gewist bij de volgende **[!UICONTROL cleanup]** uitvoeringsworkflow

Deze periodes kunnen via de optie NmsServer_PausedWorkflowPeriod worden gevormd.

Workflowtoezichthouders worden op de hoogte gesteld. De maker en laatste gebruiker die de workflow heeft gewijzigd, wordt ook op de hoogte gesteld. Beheerders ontvangen de meldingen niet.

## Workflows filteren op basis van hun status{#filtering-workflows-status}

Met de klassieke interface van Campagne kunt u de uitvoeringsstatus van alle workflows op uw instantie controleren met behulp van vooraf gedefinieerde **weergaven**. U opent deze weergaven door het knooppunt **Beheer**/**Audit**/**Workflows Status** te openen.

De volgende weergaven zijn beschikbaar:

* **Running**: geeft alle actieve workflows weer.
* **Gepauzeerd**: geeft alle gepauzeerde workflows weer.
* **Mislukt**: geeft alle mislukte workflows weer.

<!--Start Pending: lists all workflows that are waiting to be started by the operationMgt process.-->

![](assets/workflow-monitoring-views.png)

<!--The Start Pending view is available with the Marketing campaigns package only. See Installing Campaign standard packages../../installation/using/installing-campaign-standard-packages.md.-->

Deze weergaven zijn standaard toegankelijk in de map **Audit**. U kunt ze echter wel opnieuw maken op de locatie die u kiest in de mappenstructuur. Op deze manier zijn ze beschikbaar voor standaardgebruikers zonder beheerrechten.

Dit doet u als volgt:

1. Klik met de rechtermuisknop op de map waaraan u de weergave wilt toevoegen.
1. Selecteer in **Nieuwe map**/**Beheer** toevoegen de weergave die u wilt toevoegen.
1. Zodra de omslag aan de boom wordt toegevoegd, zorg ervoor u het als mening vormt, zodat het alle werkschema&#39;s, ongeacht hun oorsprongomslag toont.Voor meer op hoe te om meningen te vormen, verwijs naar [deze sectie](../../platform/using/access-management.md#adding-folders-and-creating-views).

Naast deze weergaven kunt u ook mappen met filters instellen waarmee u de lijst met workflows kunt filteren op basis van hun uitvoeringsstatus. Dit doet u als volgt:

1. Open een map van het type workflow en selecteer vervolgens het **[!UICONTROL Filters]** / **[!UICONTROL Advanced filter]** menu.
1. Configureer het filter zodanig dat het **[!UICONTROL @status]** veld van de workflow gelijk is aan de status van uw keuze.
1. Sla het filter op en geef het een naam. Deze functie is dan rechtstreeks beschikbaar in de lijst met filters.

![](assets/workflow-monitoring-filter.png)

Raadpleeg de volgende secties voor meer informatie:

* [Geavanceerde filters maken](../../platform/using/creating-filters.md#creating-an-advanced-filter)
* [Filters opslaan](../../platform/using/creating-filters.md#saving-a-filter)

<!-- need to check if pending status filter will be implemented or not in january release, note, Additionally to these views, a prefedefined filter is available in workflow-type folders. It allows you to display in the list workflows that are waiting to be started by the operationMgt process only.This filter is available with the Marketing campaigns package only. See Installing Campaign standard packages../../installation/using/installing-campaign-standard-packages.md.-->

