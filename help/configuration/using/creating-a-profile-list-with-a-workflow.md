---
solution: Campaign Classic
product: campaign
title: Een profiellijst maken met een workflow
description: Leer hoe u een profiellijst maakt in een workflow
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 10%

---


# Een profiellijst maken met een workflow{#creating-a-profile-list-with-a-workflow}

Als u een **[!UICONTROL List]** typelijst wilt maken op basis van de nieuwe tabel voor ontvangers, moet u een doelworkflow maken die de lijst genereert.

Raadpleeg [deze sectie](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign)voor meer informatie over lijsten in Campagne.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Voer de onderstaande stappen uit om een doelworkflow te maken en ontvangers bij te werken in een aangepaste tabel voor ontvangers:

1. Ga naar het **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** knooppunt van de verkenner.
1. Maak een nieuwe doelworkflow.
1. Plaats een activiteit van de **Vraag** die door een de updateactiviteit **van de** Lijst wordt gevolgd.

   ![](assets/mapping_create_list_workflow01.png)

1. Dubbelklik op de activiteit **Query** en klik vervolgens **[!UICONTROL Edit the query]** om een doeldimensie te kiezen op basis van het schema van de nieuwe tabel voor ontvangers (in ons voorbeeld: **Individueel**). Klik **[!UICONTROL Finish]** om te bevestigen.

   ![](assets/mapping_create_list_workflow03.png)

1. Dubbelklik op de **List-updateactiviteit** en selecteer vervolgens het **[!UICONTROL Create the list if necessary (Computed name)]** keuzerondje.

   ![](assets/mapping_create_list_workflow02.png)

1. Selecteer de aanmaakmap voor de nieuwe lijst.
1. Voer de workflow uit om de lijst te maken.
1. Bekijk het resultaat in de knoop van de boom die u tijdens de **[!UICONTROL List update]** activiteit selecteerde.

   Het dashboard specificeert het schema waarop de lijst gebaseerd is, zoals hieronder getoond:

   ![](assets/mapping_list_view.png)


