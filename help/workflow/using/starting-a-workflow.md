---
title: Een workflow starten
description: Leer hoe u een workflow start en werkstroomhandelingen ontdekt op de werkbalk en met de rechtermuisknop op het menu klikt.
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---


# Een workflow starten {#starting-a-workflow}

Een workflow wordt altijd handmatig gestart. Wanneer begonnen, kan het echter inactief afhankelijk van de informatie blijven die via een planner wordt gespecificeerd (zie [Planner](../../workflow/using/scheduler.md)) of activiteit het plannen.

Acties die betrekking hebben op het uitvoeren van de workflow (starten, stoppen, pauzeren, enz.) zijn **asynchrone** processen: de bestelling wordt opgenomen en is van kracht zodra de server beschikbaar is om deze toe te passen.

Met de werkbalk kunt u de uitvoering van de workflow starten en volgen.

De lijst met opties in het **[!UICONTROL Actions]** menu en in het snelmenu dat met de rechtermuisknop wordt geopend, wordt hieronder beschreven.

## Werkbalk Handelingen {#actions-toolbar}

De werkbalkknoppen worden in deze [sectie](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)beschreven. Met de **[!UICONTROL Actions]** knop hebt u toegang tot extra opties voor het uitvoeren van geselecteerde workflows. U kunt ook het **[!UICONTROL File > Actions]** menu gebruiken of met de rechtermuisknop op een workflow klikken en **[!UICONTROL Actions]** selecteren.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   Met deze actie kunt u de uitvoering van een workflow starten: Als een werkstroom **voltooid** is, **wordt Bewerkt** of **Gepauzeerd** , verandert de status in **Gestart**. De workflow-engine handelt vervolgens de uitvoering van deze workflow af. Als de werkstroom is gepauzeerd, wordt deze hervat, anders wordt de werkstroom van het begin gestart en worden de initiële activiteiten geactiveerd.

   De aanvang is een asynchroon proces: Het verzoek wordt opgeslagen en zo snel mogelijk verwerkt door een workflowserver.

* **[!UICONTROL Pause]**

   Met deze handeling wordt de status van de workflow ingesteld op **Gepauzeerd**. Er worden geen activiteiten geactiveerd totdat de werkstroom wordt hervat; de lopende bewerkingen worden echter niet gepauzeerd .

* **[!UICONTROL Stop]**

   Met deze handeling wordt een workflow gestopt die momenteel wordt uitgevoerd. De status van de instantie is ingesteld op **Voltooid**. Bewerkingen die worden uitgevoerd, worden indien mogelijk gestopt. Importeren en SQL-query&#39;s worden onmiddellijk geannuleerd.

   Stoppen is een asynchroon proces. Het verzoek is geregistreerd en vervolgens worden bewerkingen door de workflowserver of servers geannuleerd. Het stoppen van een werkstroominstantie kan daarom tijd in beslag nemen, vooral als de werkstroom op meerdere servers wordt uitgevoerd, die elk de controle moeten krijgen om de actieve taken te annuleren.

* **[!UICONTROL Restart]**

   Deze actie stopt en start de workflow opnieuw. Doorgaans kunt u sneller opnieuw opstarten. Het is ook nuttig om opnieuw beginnen te automatiseren wanneer het tegenhouden een bepaalde hoeveelheid tijd neemt: De reden hiervoor is dat de opdracht Stoppen niet beschikbaar is wanneer de workflow wordt gestopt.

   De **[!UICONTROL Start / Pause / Stop / Restart]** acties zijn ook beschikbaar via de uitvoeringspictogrammen op de werkbalk. For more on this, refer to this [section](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge history]**

   Met deze handeling kunt u de historie van de workflow wissen. Raadpleeg voor meer informatie de logboeken [leegmaken](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

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

   Met deze actie maakt u een nieuw werkstroomsjabloon op basis van de geselecteerde workflow. U moet de map opgeven waarin deze wordt opgeslagen (in het **[!UICONTROL Folder]** veld).

   De **[!UICONTROL Mass update of selected lines]** en de **[!UICONTROL Merge selected lines]** opties zijn algemene platformopties beschikbaar in alle **[!UICONTROL Actions]** menu&#39;s. For more on this, refer to this [section](../../platform/using/updating-data.md).

## Klikken met rechtermuisknop {#right-click-menu}

Wanneer een of meer workflowactiviteiten zijn geselecteerd, kunt u met de rechtermuisknop klikken om op uw selectie te reageren.

![](assets/contextual_menu.png)

De volgende opties zijn beschikbaar in het klikmenu met de rechtermuisknop:

**[!UICONTROL Open]**: met deze optie hebt u toegang tot de eigenschappen van de activiteit.

**[!UICONTROL Display logs:]** met deze optie kunt u het logboek voor taakuitvoering weergeven voor de geselecteerde activiteit. Zie Logboeken [weergeven](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** met deze actie kunt u taken die in behandeling zijn zo snel mogelijk starten.

**[!UICONTROL Workflow restart from a task:]** met deze optie kunt u de workflow opnieuw starten met de resultaten die eerder voor deze activiteit zijn opgeslagen.

**[!UICONTROL Cut/Copy/Paste/Delete:]** Met deze opties kunt u activiteiten knippen, kopiëren, plakken en verwijderen.

**[!UICONTROL Copy as bitmap:]** met deze optie kunt u een screenshot maken van alle activiteiten.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** deze opties zijn ook beschikbaar op het **[!UICONTROL Advanced]** tabblad van de eigenschappen activity . Ze worden in detail beschreven in [Executie](../../workflow/using/advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** Hiermee kunt u de wijzigingen in een workflow opslaan of annuleren.

>[!NOTE]
>
>U kunt een groep activiteiten selecteren en er een van deze opdrachten op toepassen.

Het contextmenu wordt ook beschreven in deze [sectie](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
