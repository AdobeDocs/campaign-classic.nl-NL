---
title: Databron wijzigen
description: Meer informatie over de activiteit van de gegevensbron van de Verandering
feature: Workflows, Data Management, Federated Data Access
hide: true
hidefromtoc: true
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# Databron wijzigen {#change-data-source}

>[!NOTE]
>
> De **[!UICONTROL Change data source]** -activiteit is alleen beschikbaar in het **[!UICONTROL Access to external data (Federated Data Access)]** -pakket. Voor meer informatie over ingebouwde pakketten Adobe Campaign Classic, verwijs naar deze [ pagina ](../../installation/using/installing-campaign-standard-packages.md).

Met de **[!UICONTROL Change data source]** -activiteit kunt u de gegevensbron van een workflow wijzigen **[!UICONTROL Working table]** . Dit biedt meer flexibiliteit voor het beheer van gegevens in verschillende gegevensbronnen, zoals FDA, FFDA en de lokale database.

Met **[!UICONTROL Working table]** kan Adobe Campaign Classic gegevens verwerken en gegevens delen met de workflowactiviteiten.
Standaard wordt **[!UICONTROL Working table]** gemaakt in dezelfde database als de bron van de gegevens waarop we een query uitvoeren.

Als u bijvoorbeeld een query uitvoert op de tabel **[!UICONTROL Profiles]** die is opgeslagen in de Cloud-database, maakt u een **[!UICONTROL Working table]** in dezelfde Cloud-database.
Als u dit wilt wijzigen, voegt u de **[!UICONTROL Change Data Source]** -activiteit toe en kiest u een andere gegevensbron voor uw **[!UICONTROL Working table]** .

Wanneer u de **[!UICONTROL Change Data Source]** -activiteit gebruikt, moet u terugschakelen naar de Cloud-database om door te gaan met de workflowuitvoering.

De **[!UICONTROL Change Data Source]** -activiteit gebruiken:

1. Maak een workflow.

1. Vraag de beoogde ontvangers naar een **[!UICONTROL Query]** -activiteit.

   Voor meer informatie over de **[!UICONTROL Query]** activiteit, verwijs naar deze [ pagina ](../../workflow/using/query.md#creating-a-query).

1. Voeg op het tabblad **[!UICONTROL Targeting]** een **[!UICONTROL Change data source]** -activiteit toe.

   ![](assets/change-data-source.png)

1. Dubbelklik op de **[!UICONTROL Change data source]** -activiteit om **[!UICONTROL Default data source]** te selecteren.

   De het werk lijst, die het resultaat van uw vraag bevat, wordt dan bewogen aan het gebrek PostSQL- gegevensbestand.

   ![](assets/change-data-source_2.png)

1. Sleep vanaf het tabblad **[!UICONTROL Actions]** een **[!UICONTROL JavaScript code]** -activiteit om eenheidsbewerkingen uit te voeren op de werktabel.

   Voor meer informatie over de **[!UICONTROL JavaScript code]** activiteit, verwijs naar de [ code van JavaScript en Geavanceerde de code van JavaScript ](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) pagina.

1. Voeg nog een **[!UICONTROL Change data source]** -activiteit toe om terug te schakelen naar de Cloud-database.

1. Dubbelklik op uw activiteit en selecteer **[!UICONTROL Active FDA external account]** en vervolgens het corresponderende **[!UICONTROL External database]** externe account.

   ![](assets/change-data-source_3.png)

1. U kunt nu uw workflow starten.
