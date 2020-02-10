---
title: Een profiellijst maken met een workflow
seo-title: Een profiellijst maken met een workflow
description: Een profiellijst maken met een workflow
seo-description: null
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 681e6ec5fc9ed8c7e46af04f0ed62927b30e1b2e

---


# Een profiellijst maken met een workflow{#creating-a-profile-list-with-a-workflow}

Als u een **[!UICONTROL List]** typelijst wilt maken op basis van de nieuwe tabel voor ontvangers, moet u een doelworkflow maken die de lijst genereert. Raadpleeg [deze sectie](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign)voor meer informatie over lijsten in Campagne.

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

>[!NOTE]
>
>U kunt ook naar de video [Een lijst met ontvangers](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-list-of-recipients.html) maken verwijzen.

