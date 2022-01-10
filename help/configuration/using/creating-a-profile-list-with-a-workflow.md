---
product: campaign
title: Een profiellijst maken met een workflow
description: Leer hoe u een profiellijst maakt in een workflow
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: fb4b4c42b907e86813ea570f912312fccf893bfe
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 10%

---

# Een profiellijst maken met een workflow{#creating-a-profile-list-with-a-workflow}

![](../../assets/common.svg)

Als u een **[!UICONTROL List]** typelijst die op de nieuwe ontvankelijke lijst wordt gebaseerd, moet u een het richten werkschema tot stand brengen dat de lijst zal produceren.

Voor meer informatie over lijsten in Campagne, verwijs naar [deze sectie](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Voer de onderstaande stappen uit om een doelworkflow te maken en ontvangers bij te werken in een aangepaste tabel voor ontvangers:

1. Ga naar de **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** knooppunt van de verkenner.
1. Maak een nieuwe doelworkflow.
1. Een **Query** activiteit gevolgd door een **Lijstupdate** activiteit.

   ![](assets/mapping_create_list_workflow01.png)

1. Dubbelklik op de knop **Query** activiteit, dan klik **[!UICONTROL Edit the query]** om een het richten dimensie te kiezen die op het schema van de nieuwe ontvankelijke lijst wordt gebaseerd (in ons voorbeeld: **Individueel**). Klikken **[!UICONTROL Finish]** ter bevestiging.

   ![](assets/mapping_create_list_workflow03.png)

1. Dubbelklik op de knop **Lijstupdate** activiteit, dan selecteer **[!UICONTROL Create the list if necessary (Computed name)]** keuzerondje.

   ![](assets/mapping_create_list_workflow02.png)

1. Selecteer de aanmaakmap voor de nieuwe lijst.
1. Voer de workflow uit om de lijst te maken.
1. Het resultaat weergeven in het knooppunt van de structuur dat u hebt geselecteerd tijdens het dialoogvenster **[!UICONTROL List update]** activiteit.

   Het dashboard specificeert het schema waarop de lijst gebaseerd is, zoals hieronder getoond:

   ![](assets/mapping_list_view.png)
