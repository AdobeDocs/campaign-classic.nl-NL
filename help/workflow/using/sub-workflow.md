---
product: campaign
title: Subworkflow
description: Meer informatie over de subworkflowactiviteit
feature: Workflows
hide: true
hidefromtoc: true
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# Subworkflow{#sub-workflow}



Met de **[!UICONTROL Sub-workflow]** -activiteit kunt u de uitvoering van een andere workflow starten en het resultaat herstellen. Met deze activiteit kunt u complexe workflows gebruiken terwijl u een vereenvoudigde interface gebruikt.

U kunt meerdere subworkflows aanroepen in één workflow. Subworkflows worden synchroon uitgevoerd.

In het onderstaande voorbeeld roept een primaire workflow een subworkflow aan met behulp van sprongen. Voor meer op sprong-type grafische voorwerpen, zie [ deze sectie ](jump-start-point-and-end-point.md).

1. Maak een workflow die u als een subworkflow in een andere workflow wilt gebruiken.
1. Voeg een **[!UICONTROL Jump (end point)]** -activiteit in met een prioriteit van 1 aan het begin van de werkstroom. Als u meerdere sprongen van het type &quot;eindpunt&quot; hebt, gebruikt Adobe Campaign de sprongen &quot;eindpunt&quot; met het laagste getal.
1. Voeg een **[!UICONTROL Jump (start point)]** -activiteit in met een prioriteit 2 aan het einde van de workflow. Als u meerdere sprongen van het type &quot;beginpunt&quot; hebt, gebruikt Adobe Campaign de sprong &quot;beginpunt&quot; met het hoogste getal.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >Als de subworkflowactiviteit verwijst naar een werkstroom met verschillende **[!UICONTROL Jump]** -activiteiten, wordt de subwerkstroom uitgevoerd tussen de sprongen van het type &quot;eindpunt&quot; met het laagste getal en de sprongen van het type &quot;beginpunt&quot; met het hoogste getal.
   >
   >De subworkflow kan alleen correct worden uitgevoerd als u slechts één sprongreis van het type &quot;eindpunt&quot; met het laagste getal hebt en slechts één sprongreis van het type &quot;beginpunt&quot; met het hoogste getal.

1. Vul deze subworkflow in en sla deze op.
1. Een primaire workflow maken.
1. Voeg een **[!UICONTROL Sub-workflow]** -activiteit in en open deze.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Workflow template]** de workflow die u wilt gebruiken.

   ![](assets/subworkflow_selection.png)

1. U kunt ook een configuratiescript toevoegen om de workflow waarnaar wordt verwezen te wijzigen.
1. Klik op **[!UICONTROL Ok]**. Er wordt automatisch een uitgaande overgang gemaakt met het label van de **[!UICONTROL Jump (start point)]** -activiteit uit de geselecteerde workflow.

   ![](assets/subworkflow_outbound.png)

1. Voer de workflow uit.

Wanneer de workflow eenmaal is uitgevoerd, blijft de status **[!UICONTROL Being edited]** behouden die als een subworkflow is aangeroepen. Dit betekent het volgende:

* U kunt niet met de rechtermuisknop op de overgangen klikken om het doel weer te geven.
* Het aantal intermediaire populaties kan niet worden weergegeven.
* De logboeken van de subworkflow worden weergegeven in de primaire workflow.

  ![](assets/subworkflow_logs.png)

>[!NOTE]
>
>Als er een fout optreedt in de subworkflow, wordt de primaire workflow gepauzeerd en wordt er een kopie van de subworkflow gemaakt.

## Invoerparameters (optioneel) {#input-parameters--optional-}

* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.

## Uitvoerparameters {#output-parameters}

* tableName
* schema
* recCount

Deze reeks van drie waarden identificeert de bevolking die door de vraag wordt gericht. **[!UICONTROL tableName]** is de naam van de tabel waarin de doel-id&#39;s worden vastgelegd. **[!UICONTROL schema]** is het schema van de populatie (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de tabel.

* targetSchema: deze waarde is het schema van de werktabel. Deze parameter is geldig voor alle overgangen met **[!UICONTROL tableName]** en **[!UICONTROL schema]** .
