---
product: campaign
title: Een workflow starten
description: Leer hoe u een workflow start en werkstroomhandelingen ontdekt op de werkbalk en met de rechtermuisknop op het menu klikt
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Workflows
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 1baf424138c95b16add37d9d556e3a2566a869c2
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 2%

---

# Een workflow starten {#starting-a-workflow}



Een workflow wordt altijd handmatig gestart. Wanneer begonnen, kan het echter inactief afhankelijk van de informatie blijven die via een planner wordt gespecificeerd (zie [Planner](scheduler.md)) of activiteiten plannen.

Acties die betrekking hebben op het uitvoeren van de workflow (starten, stoppen, pauzeren, enz.) zijn **asynchroon** processen: de volgorde wordt vastgelegd en wordt van kracht zodra de server beschikbaar is om deze toe te passen.

Met de werkbalk kunt u de uitvoering van de workflow starten en volgen.

De lijst met opties in het dialoogvenster **[!UICONTROL Actions]** en het contextmenu worden hieronder beschreven.

>[!IMPORTANT]
>
>Houd er rekening mee dat wanneer een operator een handeling uitvoert op een werkstroom (starten, stoppen, pauzeren, enz.), de handeling niet direct wordt uitgevoerd, maar in plaats daarvan in een wachtrij wordt geplaatst om te worden verwerkt door de [workflowmodule](architecture.md).

## Werkbalk Handelingen {#actions-toolbar}

De werkbalkknoppen worden in dit [sectie](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). De **[!UICONTROL Actions]** geeft u toegang tot extra uitvoeringsopties voor het werken met geselecteerde workflows. U kunt ook de opdracht **[!UICONTROL File > Actions]** of klikt u met de rechtermuisknop op een workflow en selecteert u **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

  Met deze handeling kunt u de uitvoering van een workflow starten: een workflow die **Voltooid**, **Wordt bewerkt** of **Gepauzeerd** wijzigt status in **Gestart**. De workflow-engine handelt vervolgens de uitvoering van deze workflow af. Als de werkstroom is gepauzeerd, wordt deze hervat, anders wordt de werkstroom van het begin gestart en worden de initiële activiteiten geactiveerd.

  Starten is een asynchroon proces: de aanvraag wordt opgeslagen en zo snel mogelijk verwerkt door een workflowserver.

* **[!UICONTROL Pause]**

  Met deze handeling wordt de status van de workflow ingesteld op **Gepauzeerd**. Er worden geen activiteiten geactiveerd totdat de werkstroom wordt hervat; de lopende bewerkingen worden echter niet gepauzeerd.

* **[!UICONTROL Stop]**

  Met deze handeling wordt een workflow gestopt die momenteel wordt uitgevoerd. De status van de instantie is ingesteld op **Voltooid**. Bewerkingen die worden uitgevoerd, worden indien mogelijk gestopt. Importeren en SQL-query&#39;s worden onmiddellijk geannuleerd.

  >[!IMPORTANT]
  >
  >Het beëindigen van een workflow is een asynchroon proces: de aanvraag wordt geregistreerd en vervolgens worden bewerkingen door de workflowserver(s) geannuleerd. Het stoppen van een werkstroominstantie kan daarom tijd in beslag nemen, vooral als de werkstroom op meerdere servers wordt uitgevoerd, die elk de controle moeten krijgen om de actieve taken te annuleren. U voorkomt problemen door te wachten tot de stopbewerking is voltooid en geen meerdere stopaanvragen uit te voeren in dezelfde workflow.

* **[!UICONTROL Unconditional stop]**

  Met deze optie wijzigt u de workflowstatus in **[!UICONTROL Finished]**. Deze handeling mag alleen als laatste redmiddel worden gebruikt als het normale stopproces na enkele minuten mislukt. Gebruik de onvoorwaardelijke stop alleen als u zeker weet dat er geen werkstroomtaken worden uitgevoerd.

  >[!CAUTION]
  >
  >Deze optie is gereserveerd voor professionele gebruikers.

* **[!UICONTROL Restart]**

  Deze actie stopt en start de workflow opnieuw. Doorgaans kunt u sneller opnieuw opstarten. Het is ook handig om opnieuw starten te automatiseren wanneer het stoppen enige tijd in beslag neemt. Dit komt omdat de opdracht Stoppen niet beschikbaar is wanneer de workflow wordt gestopt.

  De **[!UICONTROL Start / Pause / Stop / Restart]** acties zijn ook beschikbaar via de uitvoeringspictogrammen op de werkbalk. Raadpleeg deze [sectie](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow) voor meer informatie.

* **[!UICONTROL Purge history]**

  Met deze handeling kunt u de historie van de workflow wissen. Raadpleeg voor meer informatie hierover [De logbestanden leegmaken](monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

  Met deze optie kunt u de workflow starten in de simulatiemodus in plaats van in de echte modus. Dit betekent dat wanneer u deze modus inschakelt, alleen activiteiten worden uitgevoerd die geen invloed hebben op de database of het bestandssysteem (bijvoorbeeld **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**, enz.). Activiteiten die wel van invloed zijn (bv. **[!UICONTROL Export]**, **[!UICONTROL Import]**, enz.) en de volgende opdrachten (in dezelfde vertakking) niet worden uitgevoerd.

* **[!UICONTROL Execute pending tasks now]**

  Met deze handeling kunt u alle lopende taken zo snel mogelijk starten. Als u een specifieke taak wilt starten, klikt u met de rechtermuisknop op de desbetreffende activiteit en selecteert u **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Save as template]**

  Met deze actie maakt u een nieuw werkstroomsjabloon op basis van de geselecteerde workflow. U moet de map opgeven waarin deze wordt opgeslagen (in het dialoogvenster **[!UICONTROL Folder]** veld).

  De **[!UICONTROL Mass update of selected lines]** en **[!UICONTROL Merge selected lines]** opties zijn algemene platformopties beschikbaar in alle **[!UICONTROL Actions]** menu&#39;s. Raadpleeg deze [sectie](../../platform/using/updating-data.md) voor meer informatie.


## Best practices voor workflowuitvoering {#workflow-execution-best-practices}

**Een workflow niet meer dan om de 15 minuten plannen** omdat het algemene systeemprestaties kan belemmeren en blokken in het gegevensbestand kan creëren.

**Laat uw workflows niet in een pauzestatus staan**. Als u een tijdelijke werkstroom creeert, zorg ervoor het correct zal kunnen voltooien en niet in een **[!UICONTROL paused]** status. Als het wordt gepauzeerd, zou het impliceren dat u de tijdelijke lijsten moet houden en zo de grootte van het gegevensbestand verhogen. Wijs onder Workfloweigenschappen workflowtoezichthouders toe om een waarschuwing te verzenden wanneer een workflow mislukt of wordt gepauzeerd door het systeem.

U voorkomt als volgt dat workflows worden gepauzeerd:

* Controleer uw workflows regelmatig om te controleren of er geen onverwachte fouten zijn.
* Houd uw workflows zo eenvoudig mogelijk, bijvoorbeeld door grote workflows te splitsen in verschillende workflows. U kunt **[!UICONTROL External signal]** activiteiten worden uitgevoerd op basis van de uitvoering van andere workflows.
* Vermijd het hebben van gehandicapte activiteiten met stromen in uw werkschema&#39;s die draden open verlaten en tot vele tijdelijke lijsten leiden die veel ruimte kunnen verbruiken. Bewaar activiteiten niet in **[!UICONTROL Do not enable]** of **[!UICONTROL Enable but do not execute]** in uw workflows.

**Ongebruikte workflows stoppen**. Workflows die actief blijven, onderhouden verbindingen met de database.

**Alleen onvoorwaardelijke stop gebruiken in de zeldzame gevallen**. Deze handeling niet regelmatig gebruiken. Het niet uitvoeren van een schone sluiting op verbindingen die door werkstromen aan het gegevensbestand worden geproduceerd beïnvloedt prestaties.

**Geen meerdere stopverzoeken uitvoeren op dezelfde werkstroom**. Het beëindigen van een workflow is een asynchroon proces: de aanvraag wordt geregistreerd en vervolgens worden bewerkingen door de workflowserver(s) geannuleerd. Het stoppen van een werkstroominstantie kan daarom tijd in beslag nemen, vooral als de werkstroom op meerdere servers wordt uitgevoerd, die elk de controle moeten krijgen om de actieve taken te annuleren. U voorkomt problemen door te wachten tot de stopbewerking is voltooid en te voorkomen dat een workflow meerdere keren wordt gestopt.

## Klikken met rechtermuisknop {#right-click-menu}

Wanneer een of meer workflowactiviteiten zijn geselecteerd, kunt u met de rechtermuisknop klikken om op uw selectie te reageren.

![](assets/contextual_menu.png)

De volgende opties zijn beschikbaar in het klikmenu met de rechtermuisknop:

**[!UICONTROL Open]**: met deze optie hebt u toegang tot de eigenschappen van de activiteit.

**[!UICONTROL Display logs:]** met deze optie kunt u het logboek voor taakuitvoering weergeven voor de geselecteerde activiteit. Zie [Logboeken weergeven](monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** met deze actie kunt u taken die in behandeling zijn zo snel mogelijk starten.

**[!UICONTROL Workflow restart from a task:]** met deze optie kunt u de workflow opnieuw starten met de resultaten die eerder voor deze activiteit zijn opgeslagen.

**[!UICONTROL Cut/Copy/Paste/Delete:]** Met deze opties kunt u activiteiten knippen, kopiëren, plakken en verwijderen.

**[!UICONTROL Copy as bitmap:]** met deze optie kunt u een screenshot maken van alle activiteiten.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** deze opties zijn ook beschikbaar in het gedeelte **[!UICONTROL Advanced]** tabblad van de eigenschappen van de activiteit. Deze worden nader beschreven in [Uitvoering](advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** Hiermee kunt u de wijzigingen in een workflow opslaan of annuleren.

>[!NOTE]
>
>U kunt een groep activiteiten selecteren en er een van deze opdrachten op toepassen.

Het contextmenu wordt ook in dit gedeelte weergegeven [sectie](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
