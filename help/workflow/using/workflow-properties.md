---
title: Workflow-eigenschappen
seo-title: Workflow-eigenschappen
description: Workflow-eigenschappen
seo-description: null
page-status-flag: never-activated
uuid: bd576cc0-2db8-4519-bcb5-52bf5c811f42
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: 71969b30-cc01-4358-9597-f17939720684
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Workflow-eigenschappen{#workflow-properties}

## Tabblad Uitvoering {#execution-tab}

Het **[!UICONTROL Execution]** tabblad van het **[!UICONTROL Properties]** venster in een workflow wordt opgedeeld in drie secties:

![](assets/wf_execution_tab.png)

### Planner {#scheduler}

Deze sectie wordt alleen weergegeven in workflows voor campagnes.

* **[!UICONTROL Priority]**

   De workflowengine verwerkt de uit te voeren workflows op basis van het prioriteitscriterium op dit gebied. Bijvoorbeeld, zullen alle werkschema&#39;s met een **[!UICONTROL Average]** prioriteit worden uitgevoerd vóór die met een **[!UICONTROL Low]** prioriteit.

* **[!UICONTROL Schedule execution for a time of low activity]**

   Met deze optie wordt het begin van de workflow uitgesteld tot een minder drukke periode. Sommige workflows kunnen kostbaar zijn in termen van resources voor de database-engine. We raden aan uitvoering te plannen in een tijd van lage activiteit (bijvoorbeeld &#39;s nachts). In de **[!UICONTROL Processes on campaigns]** technische werkstroom worden perioden met lage activiteit gedefinieerd.

### Uitvoering {#execution}

* **[!UICONTROL Default affinity]**

   Als uw installatie meerdere workflowservers bevat, gebruikt u dit veld om de computer te kiezen waarop de workflow wordt uitgevoerd. Als de waarde die in dit veld wordt gedefinieerd, op geen enkele server bestaat, blijft de workflow in behandeling.

   Zie deze [sectie](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

* **[!UICONTROL History in days]**

   De het werklijsten van het gegevensbestand houden een geschiedenis van uitvoeringen (taken, gebeurtenissen, logboek). Hier kunt u het aantal dagen definiëren dat voor deze workflow moet worden gearchiveerd: het schoonmaakproces zal de oudste archieven eenmaal per dag verwijderen . Als de waarde in dit veld nul is, wordt het archief nooit verwijderd.

* **[!UICONTROL Log SQL queries in the journal]**

   Deze functionaliteit is gereserveerd voor geavanceerde gebruikers. Het heeft betrekking op werkstromen die gericht activiteiten (vraag, vereniging, doorsnede, enz.) bevatten. Als deze optie is ingeschakeld, worden de SQL-query&#39;s die tijdens de workflowuitvoering naar de database worden verzonden, weergegeven in Adobe Campagne: dit betekent dat u ze kunt analyseren om query&#39;s te optimaliseren of problemen te diagnosticeren.

   De vragen worden getoond op een **[!UICONTROL SQL logs]** **[!UICONTROL Properties]** lusje dat aan het werkschema (behalve campagnewerkschema&#39;s) en aan de activiteit wordt toegevoegd wanneer de optie wordt toegelaten. Het **[!UICONTROL Audit]** tabblad bevat ook SQL-query&#39;s.

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   Deze optie mag alleen worden gebruikt voor foutopsporing en nooit in productie. Wanneer deze optie is ingeschakeld, heeft de workflow prioriteit en worden alle andere workflows gestopt totdat deze is voltooid.

### Foutbeheer {#error-management}

* **[!UICONTROL Troubleshooting]**

   In dit veld kunt u de acties definiëren die moeten worden uitgevoerd als een workflowtaak fouten bevat. Er zijn twee mogelijke opties:

   * **[!UICONTROL Stop the process]**: de workflow wordt automatisch gepauzeerd. de workflowstatus verandert in **[!UICONTROL Failed]**. Als het probleem is opgelost, start u de workflow opnieuw met de **[!UICONTROL Start]** knoppen of de **[!UICONTROL Restart]** knoppen.
   * **[!UICONTROL Ignore]**: de status van de taak die de fout heeft veroorzaakt, verandert in **[!UICONTROL Failed]**, maar de werkstroom behoudt de **[!UICONTROL Started]** status. Deze configuratie is relevant voor terugkerende taken: als de tak een planner omvat, zal het normaal beginnen volgende tijd het werkschema wordt uitgevoerd.

* **[!UICONTROL Consecutive errors]**

   Dit veld wordt beschikbaar wanneer de **[!UICONTROL Ignore]** waarde in het **[!UICONTROL In case of errors]** veld is geselecteerd. U kunt opgeven hoeveel fouten kunnen worden genegeerd voordat het proces wordt gestopt. Zodra dit aantal wordt bereikt, verandert de werkschemastatus in **[!UICONTROL Failed]**. Als de waarde van dit veld 0 is, wordt de workflow nooit gestopt, ongeacht het aantal fouten.

* **[!UICONTROL Template]**

   In dit veld kunt u de berichtsjabloon selecteren die naar de workflowtoezichthouders moet worden verzonden wanneer de status van de sjabloon verandert in **[!UICONTROL Failed]**.

   De betrokken operatoren worden via e-mail op de hoogte gesteld als hun profiel een e-mailadres bevat. Ga naar het **[!UICONTROL Supervisor(s)]****[!UICONTROL General]** veld van de eigenschappen (tabblad) om workflowsupervisors te definiëren.

   ![](assets/wf-properties_select-supervisors.png)

   Het **[!UICONTROL Notification to a workflow supervisor]** standaardmalplaatje omvat een verbinding voor de toegang tot van de console van de Campagne van Adobe via het Web zodat de ontvanger aan de kwestie kan werken zodra zij het programma worden geopend.

   Ga naar **[!UICONTROL Administration>Campaign management>Technical deliveries and templates]** om een gepersonaliseerde sjabloon te maken.

