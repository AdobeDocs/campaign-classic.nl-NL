---
title: Doelgroepen importeren en exporteren
seo-title: Doelgroepen importeren en exporteren
description: Doelgroepen importeren en exporteren
seo-description: null
page-status-flag: never-activated
uuid: af03ce68-8a58-4909-83e9-23c385820284
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f26cc65a-76be-4b7a-bde3-d0cbe3eedaaf
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 4%

---


# Doelgroepen importeren en exporteren{#importing-and-exporting-audiences}

## Een publiek importeren {#importing-an-audience}

U kunt soorten publiek/segmenten vanuit Audience Manager of People core-service importeren in Adobe Campaign via de lijst met ontvangers.

1. Ga naar het knooppunt **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** in de Adobe Campaign Explorer.
1. Selecteer in de actiebalk **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. Klik in het venster dat wordt geopend **[!UICONTROL Select a shared audience]** om naar de lijst met gedeelde soorten publiek/segmenten te gaan die beschikbaar zijn in de andere Adobe Experience Cloud-oplossingen.
1. Selecteer een publiek en bevestig het. De publieksinformatie wordt automatisch voltooid.

   Houd er rekening mee dat als u een gedeeld publiek wilt importeren, u het **[!UICONTROL Audience library]** product in de beheerconsole moet krijgen en beheerder in Audience Manager moet zijn. Raadpleeg de documentatie bij de [Admin Console voor meer informatie](https://helpx.adobe.com/nl/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Selecteer de gegevensbron van AMC van het **[!UICONTROL AMC Data source]** gebied om het type van gegevens te bepalen die worden verwacht.

   ![](assets/aam_import_audience_2.png)

1. Sla het publiek op.

Het publiek wordt geïmporteerd via een technische workflow. De geïmporteerde lijst bevat elementen die met behulp van de AMC-gegevensbron met elkaar in overeenstemming kunnen worden gebracht. De elementen die niet door Adobe Campaign worden herkend, worden niet geïmporteerd.

Het importproces duurt 24-36 uur om te synchroniseren, wanneer de segmenten direct uit de de kerndienst of Audience Manager van Mensen worden ingevoerd. Na deze periode kun je het nieuwe publiek in Adobe Campaign vinden en gebruiken.

>[!NOTE]
>
>Als u soorten publiek importeert van Adobe Analytics naar Adobe Campaign, moeten deze soorten publiek eerst worden gedeeld in People Core Service of Audience Manager. Dit proces duurt 12-24 uur en moet worden toegevoegd aan de synchronisatie van 24-36 uur met Campagne.
>
>In dat specifieke geval kan de tijd voor het delen van het publiek maximaal 60 uur bedragen. Raadpleeg deze [documentatie voor meer informatie over het delen van Adobe Analytics-publiek in People Core-service en Audience Manager](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-publish.html).

De publieksgegevens worden volledig vervangen telkens als het wordt gesynchroniseerd. Alleen segmenten kunnen worden geïmporteerd. De korrelige gegevens met inbegrip van zeer belangrijk-waardeparen, eigenschappen en regels worden niet gesteund.

## Een publiek exporteren {#exporting-an-audience}

U kunt een publiek van Adobe Campaign naar Audience Manager of de de kerndienst van Mensen uitvoeren gebruikend een werkschema. De processen voor het maken en gebruiken van een werkstroom worden beschreven in [dit document](../../workflow/using/building-a-workflow.md). Het geëxporteerde publiek wordt opgeslagen als segmenten in de hoofdservice Personen:

1. Maak een nieuwe doelworkflow.
1. Wijs op een reeks ontvangers aan de hand van de verschillende beschikbare activiteiten.
1. Na het richten, sleep en laat vallen een **[!UICONTROL Update shared audience]** activiteit, dan open het.

   ![](assets/aam_export_example.png)

1. Definieer het publiek dat u wilt exporteren met de **[!UICONTROL Select a shared audience]** optie. In het venster dat wordt geopend, kunt u een bestaand publiek selecteren of een nieuw publiek maken.

   Als u een bestaand publiek selecteert, worden alleen de nieuwe records aan het publiek toegevoegd.

   Als u de lijst met ontvangers wilt exporteren naar een nieuw publiek, vult u het **[!UICONTROL Segment name]** veld in en klikt u **[!UICONTROL Create]** voordat u het nieuwe publiek selecteert.

   Voltooi de bewerking door op het symbool boven in het venster en vervolgens op de **[!UICONTROL OK]** knop te klikken.

1. Selecteer het **[!UICONTROL AMC Data source]** om het verwachte gegevenstype op te geven. Het schema wordt automatisch bepaald.

   ![](assets/aam_export_audience_activity.png)

1. Sla het publiek op.

Het publiek wordt vervolgens geëxporteerd. Het sparen publieksactiviteit heeft twee uitgaande overgangen. De hoofdovergang bevat de ontvangers die zijn geëxporteerd. De aanvullende overgang bevat de ontvangers die niet met een bezoekersidentiteitskaart of gedeclareerde identiteitskaart konden in kaart worden gebracht.

De synchronisatie tussen Adobe Campaign en de kerndienst van Mensen vergt 24-36 uur. Na deze periode, zult u uw nieuw publiek in de de kerndienst van Mensen kunnen vinden en het in andere oplossingen van Adobe Experience Cloud hergebruiken. Raadpleeg deze [documentatie](https://docs.adobe.com/content/help/en/core-services/interface/audiences/t-audience-create.html)voor meer informatie over het gebruik van een Adobe Campaign-publiek dat door anderen wordt gebruikt in de kernservice van Adobe People.

>[!NOTE]
>
>Om met elkaar in overeenstemming te kunnen worden gebracht, moeten de records een Adobe Experience Cloud-id (&#39;bezoeker-id&#39; of &#39;gedeclareerde id&#39;) hebben. De records zonder Adobe Experience Cloud-id worden genegeerd bij het exporteren en importeren van soorten publiek.

