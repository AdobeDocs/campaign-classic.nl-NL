---
product: campaign
title: Een workflow starten
description: Leer hoe u een workflow start en werkstroomhandelingen ontdekt op de werkbalk en met de rechtermuisknop op het menu klikt
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 2%

---

# Een workflow starten {#starting-a-workflow}

Een workflow wordt altijd handmatig gestart. Wanneer begonnen, kan het echter inactief afhankelijk van de informatie blijven die via een planner wordt gespecificeerd (zie [Planner](../../workflow/using/scheduler.md)) of activiteit het plannen.

Acties die betrekking hebben op het uitvoeren van de workflow (starten, stoppen, pauzeren, enz.) zijn **asynchrone** processen: de bestelling wordt opgenomen en is van kracht zodra de server beschikbaar is om deze toe te passen.

Met de werkbalk kunt u de uitvoering van de workflow starten en volgen.

De lijst met opties die beschikbaar zijn in het menu **[!UICONTROL Actions]** en in het menu Klikken met de rechtermuisknop vindt u hieronder in detail.

>[!IMPORTANT]
>
>Houd er rekening mee dat wanneer een operator een handeling uitvoert op een werkstroom (starten, stoppen, pauzeren, enz.), de handeling niet direct wordt uitgevoerd, maar in plaats daarvan in een wachtrij wordt geplaatst om te worden verwerkt door de [workflowmodule](../../workflow/using/architecture.md).

## Werkbalk Handelingen {#actions-toolbar}

De werkbalkknoppen worden beschreven in deze [sectie](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). Met de knop **[!UICONTROL Actions]** hebt u toegang tot extra uitvoeringsopties voor het werken met geselecteerde workflows. U kunt ook het menu **[!UICONTROL File > Actions]** gebruiken of met de rechtermuisknop op een workflow klikken en **[!UICONTROL Actions]** selecteren.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   Met deze actie kunt u de uitvoering van een workflow starten: Als een workflow **Voltooid**, **Wordt bewerkt** of **Gepauzeerd** de status wijzigt in **Gestart**. De workflow-engine handelt vervolgens de uitvoering van deze workflow af. Als de werkstroom is gepauzeerd, wordt deze hervat, anders wordt de werkstroom van het begin gestart en worden de initiële activiteiten geactiveerd.

   De aanvang is een asynchroon proces: Het verzoek wordt opgeslagen en zo snel mogelijk verwerkt door een workflowserver.

* **[!UICONTROL Pause]**

   Met deze handeling wordt de status van de workflow ingesteld op **Gepauzeerd**. Er worden geen activiteiten geactiveerd totdat de werkstroom wordt hervat; de lopende bewerkingen worden echter niet gepauzeerd .

* **[!UICONTROL Stop]**

   Met deze handeling wordt een workflow gestopt die momenteel wordt uitgevoerd. De status van de instantie wordt ingesteld op **Voltooid**. Bewerkingen die worden uitgevoerd, worden indien mogelijk gestopt. Importeren en SQL-query&#39;s worden onmiddellijk geannuleerd.

   Stoppen is een asynchroon proces. Het verzoek is geregistreerd en vervolgens worden bewerkingen door de workflowserver of servers geannuleerd. Het stoppen van een werkstroominstantie kan daarom tijd in beslag nemen, vooral als de werkstroom op meerdere servers wordt uitgevoerd, die elk de controle moeten krijgen om de actieve taken te annuleren.

* **[!UICONTROL Restart]**

   Deze actie stopt en start de workflow opnieuw. Doorgaans kunt u sneller opnieuw opstarten. Het is ook nuttig om opnieuw beginnen te automatiseren wanneer het tegenhouden een bepaalde hoeveelheid tijd neemt: De reden hiervoor is dat de opdracht Stoppen niet beschikbaar is wanneer de workflow wordt gestopt.

   De **[!UICONTROL Start / Pause / Stop / Restart]** acties zijn ook beschikbaar via de uitvoeringspictogrammen in de toolbar. Raadpleeg deze [sectie](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow) voor meer informatie.

* **[!UICONTROL Purge history]**

   Met deze handeling kunt u de historie van de workflow wissen. Raadpleeg [Logbestanden leegmaken](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs) voor meer informatie.

* **[!UICONTROL Start in simulation mode]**

   Met deze optie kunt u de workflow starten in de simulatiemodus in plaats van in de echte modus. Dit betekent dat wanneer u deze modus inschakelt, alleen activiteiten worden uitgevoerd die geen invloed hebben op de database of het bestandssysteem (bijvoorbeeld **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**, enz.). Activiteiten die wel van invloed zijn (bv. **[!UICONTROL Export]**, **[!UICONTROL Import]**, enz.) en de volgende opdrachten (in dezelfde vertakking) niet worden uitgevoerd.

* **[!UICONTROL Execute pending tasks now]**

   Met deze handeling kunt u alle lopende taken zo snel mogelijk starten. Als u een specifieke taak wilt starten, klikt u met de rechtermuisknop op de desbetreffende activiteit en selecteert u **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Unconditional stop]**

   Met deze optie wijzigt u de workflowstatus in **[!UICONTROL Finished]**. Deze handeling mag alleen als laatste redmiddel worden gebruikt als het normale stopproces na enkele minuten mislukt. Gebruik de onvoorwaardelijke stop alleen als u zeker weet dat er geen werkstroomtaken worden uitgevoerd.

   >[!CAUTION]
   >
   >Deze optie is gereserveerd voor professionele gebruikers.

* **[!UICONTROL Save as template]**

   Met deze actie maakt u een nieuw werkstroomsjabloon op basis van de geselecteerde workflow. U moet de map opgeven waarin deze wordt opgeslagen (in het veld **[!UICONTROL Folder]**).

   De opties **[!UICONTROL Mass update of selected lines]** en **[!UICONTROL Merge selected lines]** zijn algemene platformopties beschikbaar in alle **[!UICONTROL Actions]** menu&#39;s. Raadpleeg deze [sectie](../../platform/using/updating-data.md) voor meer informatie.

## Klikken met rechtermuisknop op menu {#right-click-menu}

Wanneer een of meer workflowactiviteiten zijn geselecteerd, kunt u met de rechtermuisknop klikken om op uw selectie te reageren.

![](assets/contextual_menu.png)

De volgende opties zijn beschikbaar in het klikmenu met de rechtermuisknop:

**[!UICONTROL Open]**: met deze optie hebt u toegang tot de eigenschappen van de activiteit.

**[!UICONTROL Display logs:]** met deze optie kunt u het logboek voor taakuitvoering weergeven voor de geselecteerde activiteit. Zie [Logbestanden weergeven](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** met deze actie kunt u taken die in behandeling zijn zo snel mogelijk starten.

**[!UICONTROL Workflow restart from a task:]** met deze optie kunt u de workflow opnieuw starten met de resultaten die eerder voor deze activiteit zijn opgeslagen.

**[!UICONTROL Cut/Copy/Paste/Delete:]** Met deze opties kunt u activiteiten knippen, kopiëren, plakken en verwijderen.

**[!UICONTROL Copy as bitmap:]** met deze optie kunt u een screenshot maken van alle activiteiten.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** deze opties zijn ook beschikbaar op het  **[!UICONTROL Advanced]** tabblad van de eigenschappen activity . Deze worden beschreven in [Execution](../../workflow/using/advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** Hiermee kunt u de wijzigingen in een workflow opslaan of annuleren.

>[!NOTE]
>
>U kunt een groep activiteiten selecteren en er een van deze opdrachten op toepassen.

Het met de rechtermuisknop aanklikken menu is ook gedetailleerd in dit [sectie](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
