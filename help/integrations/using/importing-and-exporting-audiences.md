---
solution: Campaign Classic
product: campaign
title: Doelgroepen importeren en exporteren
description: Doelgroepen importeren en exporteren
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 4%

---


# Doelgroepen importeren en exporteren{#importing-and-exporting-audiences}

## Een publiek {#importing-an-audience} importeren

U kunt soorten publiek/segmenten vanuit Audience Manager of People core-service importeren in Adobe Campaign via de lijst met ontvangers.

1. Ga naar **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** knoop in de explorator van Adobe Campaign.
1. Selecteer **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]** op de actiebalk.

   ![](assets/aam_import_audience.png)

1. Klik in het venster dat wordt geopend op **[!UICONTROL Select a shared audience]** om naar de lijst met gedeelde soorten publiek/segmenten te gaan die beschikbaar zijn in de andere Adobe Experience Cloud-oplossingen.
1. Selecteer een publiek en bevestig het. De publieksinformatie wordt automatisch voltooid.

   Houd er rekening mee dat u het **[!UICONTROL Audience library]**-product in de beheerconsole moet krijgen en beheerder in Audience Manager moet zijn om het gedeelde publiek te kunnen importeren. Raadpleeg de documentatie bij de [Admin Console voor meer informatie](https://helpx.adobe.com/nl/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Selecteer de AMC-gegevensbron in het veld **[!UICONTROL AMC Data source]** om het type gegevens te definiëren dat wordt verwacht.

   ![](assets/aam_import_audience_2.png)

1. Sla het publiek op.

Het publiek wordt geïmporteerd via een technische workflow. De geïmporteerde lijst bevat elementen die met behulp van de AMC-gegevensbron met elkaar in overeenstemming kunnen worden gebracht. De elementen die niet door Adobe Campaign worden herkend, worden niet geïmporteerd.

Het importproces duurt 24-36 uur om te synchroniseren, wanneer de segmenten direct uit de de kerndienst of Audience Manager van Mensen worden ingevoerd. Na deze periode kun je het nieuwe publiek in Adobe Campaign vinden en gebruiken.

>[!NOTE]
>
>Als u soorten publiek importeert van Adobe Analytics naar Adobe Campaign, moeten deze soorten publiek eerst worden gedeeld in People Core Service of Audience Manager. Dit proces duurt 12-24 uur en moet worden toegevoegd aan de synchronisatie van 24-36 uur met Campagne.
>
>In dat specifieke geval kan de tijd voor het delen van het publiek maximaal 60 uur bedragen. Raadpleeg de volgende [documentatie](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-publish.html) voor meer informatie over het delen van Adobe Analytics-publiek in People Core-service en Audience Manager.

De publieksgegevens worden volledig vervangen telkens als het wordt gesynchroniseerd. Alleen segmenten kunnen worden geïmporteerd. De korrelige gegevens met inbegrip van zeer belangrijk-waardeparen, eigenschappen en regels worden niet gesteund.

## Een publiek {#exporting-an-audience} exporteren

U kunt een publiek van Adobe Campaign naar Audience Manager of de de kerndienst van Mensen uitvoeren gebruikend een werkschema. De processen voor het maken en gebruiken van een werkstroom worden beschreven in [dit document](../../workflow/using/building-a-workflow.md). Het geëxporteerde publiek wordt opgeslagen als segmenten in de hoofdservice Personen:

1. Maak een nieuwe doelworkflow.
1. Wijs op een reeks ontvangers aan de hand van de verschillende beschikbare activiteiten.
1. Na het richten, sleep en laat vallen een **[!UICONTROL Update shared audience]** activiteit, dan open het.

   ![](assets/aam_export_example.png)

1. Definieer het publiek dat u wilt exporteren via de optie **[!UICONTROL Select a shared audience]**. In het venster dat wordt geopend, kunt u een bestaand publiek selecteren of een nieuw publiek maken.

   Als u een bestaand publiek selecteert, worden alleen de nieuwe records aan het publiek toegevoegd.

   Als u de lijst met ontvangers wilt exporteren naar een nieuw publiek, vult u het veld **[!UICONTROL Segment name]** in en klikt u op **[!UICONTROL Create]** voordat u het nieuwe publiek selecteert.

   Voltooi de bewerking door op het symbool boven in het venster te klikken en vervolgens op de knop **[!UICONTROL OK]**.

1. Selecteer **[!UICONTROL AMC Data source]** om het verwachte gegevenstype te specificeren. Het schema wordt automatisch bepaald.

   ![](assets/aam_export_audience_activity.png)

1. Sla het publiek op.

Het publiek wordt vervolgens geëxporteerd. Het sparen publieksactiviteit heeft twee uitgaande overgangen. De hoofdovergang bevat de ontvangers die zijn geëxporteerd. De aanvullende overgang bevat de ontvangers die niet met een bezoekersidentiteitskaart of gedeclareerde identiteitskaart konden in kaart worden gebracht.

De synchronisatie tussen Adobe Campaign en de kerndienst van Mensen vergt 24-36 uur. Na deze periode, zult u uw nieuw publiek in de de kerndienst van Mensen kunnen vinden en het in andere oplossingen van Adobe Experience Cloud hergebruiken. Raadpleeg de volgende [documentatie](https://docs.adobe.com/content/help/en/core-services/interface/audiences/t-audience-create.html) voor meer informatie over het gebruik van een Adobe Campaign-gedeeld publiek in de kernservice Adobe Personen.

>[!NOTE]
>
>Om met elkaar in overeenstemming te kunnen worden gebracht, moeten de records een Adobe Experience Cloud-id (&#39;bezoeker-id&#39; of &#39;gedeclareerde id&#39;) hebben. De records zonder Adobe Experience Cloud-id worden genegeerd bij het exporteren en importeren van soorten publiek.

