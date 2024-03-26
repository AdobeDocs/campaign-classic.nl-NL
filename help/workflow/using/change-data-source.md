---
title: Databron wijzigen
description: Meer informatie over de activiteit van de gegevensbron van de Verandering
feature: Workflows, Data Management, Federated Data Access
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# Databron wijzigen {#change-data-source}

>[!NOTE]
>
> De **[!UICONTROL Change data source]** activiteit is alleen beschikbaar bij de **[!UICONTROL Access to external data (Federated Data Access)]** pakket. Raadpleeg deze voor meer informatie over ingebouwde Adobe Campaign Classic-pakketten [page](../../installation/using/installing-campaign-standard-packages.md).

De **[!UICONTROL Change data source]** activiteit staat u toe om de gegevensbron van een werkschema te veranderen **[!UICONTROL Working table]**. Dit biedt meer flexibiliteit voor het beheer van gegevens in verschillende gegevensbronnen, zoals FDA, FFDA en de lokale database.

De **[!UICONTROL Working table]** staat Adobe Campaign Classic-workflow toe om gegevens te verwerken en gegevens te delen met de workflowactiviteiten.
Standaard worden de **[!UICONTROL Working table]** wordt gecreeerd in het zelfde gegevensbestand zoals de bron van de gegevens wij waarvragen.

Wanneer u bijvoorbeeld het **[!UICONTROL Profiles]** tabel, opgeslagen in de Cloud-database, maakt u een **[!UICONTROL Working table]** in dezelfde Cloud-database.
Als u dit wilt wijzigen, kunt u de opdracht **[!UICONTROL Change Data Source]** activiteit om een verschillende gegevensbron voor uw te kiezen **[!UICONTROL Working table]**.

Wanneer u de opdracht **[!UICONTROL Change Data Source]** is, moet u terugschakelen naar de Cloud-database om door te gaan met de uitvoering van de workflow.

Als u de opdracht **[!UICONTROL Change Data Source]** activiteit:

1. Maak een workflow.

1. Vraag uw beoogde ontvangers om een query met een **[!UICONTROL Query]** activiteit.

   Voor meer informatie over de **[!UICONTROL Query]** activiteit, verwijs naar deze [page](../../workflow/using/query.md#creating-a-query).

1. Van de **[!UICONTROL Targeting]** tabblad, voegt u een **[!UICONTROL Change data source]** activiteit.

   ![](assets/change-data-source.png)

1. Dubbelklik op de knop **[!UICONTROL Change data source]** te selecteren activiteit **[!UICONTROL Default data source]**.

   De het werk lijst, die het resultaat van uw vraag bevat, wordt dan bewogen aan het gebrek PostSQL- gegevensbestand.

   ![](assets/change-data-source_2.png)

1. Van de **[!UICONTROL Actions]** tabblad, slepen en neerzetten **[!UICONTROL JavaScript code]** activiteit om unitaire verrichtingen op de werkende lijst uit te voeren.

   Voor meer informatie over de **[!UICONTROL JavaScript code]** activiteit, verwijs naar [JavaScript-code en geavanceerde JavaScript-code](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) pagina.

1. Nog een toevoegen **[!UICONTROL Change data source]** om terug te schakelen naar de Cloud-database.

1. Dubbelklik op uw activiteit en selecteer **[!UICONTROL Active FDA external account]** dan de overeenkomstige **[!UICONTROL External database]** externe rekening.

   ![](assets/change-data-source_3.png)

1. U kunt nu uw workflow starten.
