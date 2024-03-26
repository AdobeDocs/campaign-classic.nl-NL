---
product: campaign
title: Soorten publiek importeren en exporteren
description: Soorten publiek importeren en exporteren
feature: Audiences, People Core Service Integration
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# Soorten publiek importeren en exporteren{#importing-and-exporting-audiences}



## Een publiek importeren {#importing-an-audience}

U kunt soorten publiek/segmenten vanuit Audience Manager of People core-service importeren in Adobe Campaign via de lijst met ontvangers.

1. Ga naar de **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** in de Adobe Campaign Explorer.
1. Selecteer in de actiebalk de optie **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. Klik in het venster dat wordt geopend op **[!UICONTROL Select a shared audience]** om naar de lijst van gedeelde publiek/segmenten te gaan beschikbaar bij de andere oplossingen van Adobe Experience Cloud.
1. Selecteer een publiek en bevestig het. De publieksinformatie wordt automatisch voltooid.

   Houd er rekening mee dat als u een gedeeld publiek wilt importeren, u de opdracht **[!UICONTROL Audience library]** in de beheerconsole en als beheerder in Audience Manager. Raadpleeg voor meer informatie de [Documentatie voor beheerconsole](https://helpx.adobe.com/nl/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Selecteer de AMC-gegevensbron in het menu **[!UICONTROL AMC Data source]** veld om het type te definiëren van de gegevens die worden verwacht.

   ![](assets/aam_import_audience_2.png)

1. Sla het publiek op.

Het publiek wordt geïmporteerd via een technische workflow. De geïmporteerde lijst bevat elementen die met behulp van de AMC-gegevensbron met elkaar in overeenstemming kunnen worden gebracht. De elementen die niet door Adobe Campaign worden herkend, worden niet geïmporteerd.

Het importproces duurt 24-36 uur om te synchroniseren, wanneer de segmenten direct uit de de kerndienst of Audience Manager van Mensen worden ingevoerd. Na deze periode kun je het nieuwe publiek in Adobe Campaign vinden en gebruiken.

>[!NOTE]
>
>Als u soorten publiek importeert van Adobe Analytics naar Adobe Campaign, moeten deze soorten publiek eerst worden gedeeld in People Core Service of Audience Manager. Dit proces duurt 12-24 uur en moet worden toegevoegd aan de synchronisatie van 24-36 uur met Campagne.
>
>In dat specifieke geval kan de tijd voor het delen van het publiek maximaal 60 uur bedragen. Raadpleeg voor meer informatie over het delen van Adobe Analytics-publiek in People Core-service en Audience Manager de volgende bronnen: [Adobe Analytics-documentatie](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html).

De publieksgegevens worden volledig vervangen telkens als het wordt gesynchroniseerd. Alleen segmenten kunnen worden geïmporteerd. De korrelige gegevens met inbegrip van zeer belangrijk-waardeparen, eigenschappen en regels worden niet gesteund.

## Een publiek exporteren {#exporting-an-audience}

U kunt een publiek van Adobe Campaign naar Audience Manager of de de kerndienst van Mensen uitvoeren gebruikend een werkschema. De processen voor het maken en gebruiken van een workflow worden beschreven in [dit document](../../workflow/using/building-a-workflow.md). Het geëxporteerde publiek wordt opgeslagen als segmenten in de hoofdservice Personen:

1. Maak een nieuwe doelworkflow.
1. Wijs op een reeks ontvangers aan de hand van de verschillende beschikbare activiteiten.
1. Na het richten, sleep en laat vallen **[!UICONTROL Update shared audience]** en open deze vervolgens.

   ![](assets/aam_export_example.png)

1. Bepaal het publiek dat u via wilt uitvoeren **[!UICONTROL Select a shared audience]** -optie. In het venster dat wordt geopend, kunt u een bestaand publiek selecteren of een nieuw publiek maken.

   Als u een bestaand publiek selecteert, worden alleen de nieuwe records aan het publiek toegevoegd.

   Als u de lijst met ontvangers wilt exporteren naar een nieuw publiek, voltooit u de opdracht **[!UICONTROL Segment name]** veld en klik op **[!UICONTROL Create]** voordat u het nieuwe publiek selecteert.

   Voltooi de bewerking door op het symbool boven in het venster te klikken en vervolgens op de knop **[!UICONTROL OK]** knop.

1. Selecteer de **[!UICONTROL AMC Data source]** om het verwachte gegevenstype op te geven. Het schema wordt automatisch bepaald.

   ![](assets/aam_export_audience_activity.png)

1. Sla het publiek op.

Het publiek wordt vervolgens geëxporteerd. De activiteit van het sparen publiek heeft twee uitgaande overgangen. De hoofdovergang bevat de ontvangers die zijn geëxporteerd. De aanvullende overgang bevat de ontvangers die niet met een bezoekersidentiteitskaart of gedeclareerde identiteitskaart konden in kaart worden gebracht.

De synchronisatie tussen Adobe Campaign en de kerndienst van Mensen vergt 24-36 uur. Na deze periode, zult u uw nieuw publiek in de de kerndienst van Mensen kunnen vinden en het in andere oplossingen van Adobe Experience Cloud hergebruiken. Voor meer informatie over het gebruiken van een Adobe Campaign gedeeld publiek in de kerndienst van de Mensen van de Adobe, verwijs naar dit [documentatie](https://experienceleague.adobe.com/docs/core-services/interface/audiences/t-audience-create.html).

>[!NOTE]
>
>Om met elkaar in overeenstemming te kunnen worden gebracht, moeten de records een Adobe Experience Cloud-id (&#39;bezoeker-id&#39; of &#39;gedeclareerde id&#39;) hebben. De records zonder Adobe Experience Cloud-id worden genegeerd bij het exporteren en importeren van soorten publiek.
