---
title: Gegevensbron wijzigen
description: Meer informatie over de activiteit van de gegevensbron van de Verandering
audience: workflow
content-type: reference
topic-tags: targeting-activities
source-git-commit: 9fc4add3f12e3f06b031c4969bd8409c67e4359e
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# Gegevensbron wijzigen {#change-data-source}

>[!NOTE]
>
> De **[!UICONTROL Change data source]** activiteit is slechts beschikbaar met het **[!UICONTROL Access to external data (Federated Data Access)]** pakket. Raadpleeg deze [pagina](../../installation/using/installing-campaign-standard-packages.md) voor meer informatie over ingebouwde Adobe Campaign Classic-pakketten.

Met de **[!UICONTROL Change data source]**-activiteit kunt u de gegevensbron van een workflow **[!UICONTROL Working table]** wijzigen. Dit biedt meer flexibiliteit voor het beheer van gegevens in verschillende gegevensbronnen, zoals FDA, FFDA en de lokale database.

Met de **[!UICONTROL Working table]** kan Adobe Campaign Classic-workflow gegevens verwerken en gegevens delen met de workflowactiviteiten.
Door gebrek, wordt **[!UICONTROL Working table]** gecreeerd in het zelfde gegevensbestand zoals de bron van de gegevens die wij vragen.

Als u bijvoorbeeld een **[!UICONTROL Profiles]**-tabel opvraagt die is opgeslagen in de Cloud-database, maakt u een **[!UICONTROL Working table]** op dezelfde Cloud-database.
Om dit te veranderen, kunt u **[!UICONTROL Change Data Source]** activiteit toevoegen om een verschillende gegevensbron voor uw **[!UICONTROL Working table]** te kiezen.

Wanneer u de **[!UICONTROL Change Data Source]**-activiteit gebruikt, moet u terugschakelen naar de Cloud-database om door te gaan met de uitvoering van de workflow.

De **[!UICONTROL Change Data Source]**-activiteit gebruiken:

1. Een workflow maken.

1. Vraag uw beoogde ontvangers om een **[!UICONTROL Query]** activiteit.

   Raadpleeg deze [pagina](../../workflow/using/query.md#creating-a-query) voor meer informatie over de **[!UICONTROL Query]**-activiteit.

1. Voeg op het tabblad **[!UICONTROL Targeting]** een **[!UICONTROL Change data source]**-activiteit toe.

   ![](assets/change-data-source.png)

1. Dubbelklik op uw **[!UICONTROL Change data source]**-activiteit om **[!UICONTROL Default data source]** te selecteren.

   De het werk lijst, die het resultaat van uw vraag bevat, wordt dan bewogen aan het gebrek PostSQL- gegevensbestand.

   ![](assets/change-data-source_2.png)

1. Van **[!UICONTROL Actions]** lusje, sleep en laat vallen **[!UICONTROL JavaScript code]** activiteit om unitaire verrichtingen op de het werk lijst uit te voeren.

   Raadpleeg de pagina [JavaScript-code en Geavanceerde JavaScript-code](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) voor meer informatie over de **[!UICONTROL JavaScript code]**-activiteit.

1. Voeg nog een **[!UICONTROL Change data source]** activiteit toe om naar het gegevensbestand van de Wolk terug te schakelen.

1. Dubbelklik op uw activiteit en selecteer **[!UICONTROL Active FDA external account]** dan de corresponderende **[!UICONTROL External database]** externe account.

   ![](assets/change-data-source_3.png)

1. U kunt nu uw workflow starten.
