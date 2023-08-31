---
product: campaign
title: Een profiellijst maken met een workflow
description: Leer hoe u een profiellijst maakt in een workflow
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 12%

---

# Een profiellijst maken met een workflow{#creating-a-profile-list-with-a-workflow}


Een **[!UICONTROL List]** typelijst die op de nieuwe ontvankelijke lijst wordt gebaseerd, moet u een het richten werkschema tot stand brengen dat de lijst zal produceren.

Raadpleeg voor meer informatie over lijsten in campagne [deze sectie](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Voer de onderstaande stappen uit om een doelworkflow te maken en ontvangers bij te werken in een aangepaste tabel voor ontvangers:

1. Ga naar de **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** knooppunt van de verkenner.
1. Maak een nieuwe doelworkflow.
1. Een **Query** activiteit gevolgd door een **Lijstupdate** activiteit.

   ![](assets/mapping_create_list_workflow01.png)

1. Dubbelklik op de knop **Query** activiteit, dan klik **[!UICONTROL Edit the query]** om een het richten dimensie te kiezen die op het schema van de nieuwe ontvankelijke lijst wordt gebaseerd (in ons voorbeeld: **Individueel**). Klik op **[!UICONTROL Finish]** om te bevestigen.

   ![](assets/mapping_create_list_workflow03.png)

1. Dubbelklik op de knop **Lijstupdate** activiteit, dan selecteer **[!UICONTROL Create the list if necessary (Computed name)]** keuzerondje.

   ![](assets/mapping_create_list_workflow02.png)

1. Selecteer de aanmaakmap voor de nieuwe lijst.
1. Voer de workflow uit om de lijst te maken.
1. Het resultaat weergeven in het knooppunt van de structuur dat u hebt geselecteerd tijdens het dialoogvenster **[!UICONTROL List update]** activiteit.

   Het dashboard geeft het schema aan waarop de lijst is gebaseerd, zoals hieronder wordt weergegeven:

   ![](assets/mapping_list_view.png)
