---
title: Soorten publiek importeren en exporteren
seo-title: Soorten publiek importeren en exporteren
description: Soorten publiek importeren en exporteren
seo-description: null
page-status-flag: never-activated
uuid: af03ce68-8a58-4909-83e9-23c385820284
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f26cc65a-76be-4b7a-bde3-d0cbe3eedaaf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Soorten publiek importeren en exporteren{#importing-and-exporting-audiences}

## Een publiek importeren {#importing-an-audience}

U kunt soorten publiek/segmenten vanuit Audience Manager of de hoofdservice Personen importeren in Adobe Campagne via de lijsten met ontvangers.

1. Ga naar het knooppunt **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** in de Adobe Campaign Explorer.
1. Selecteer in de actiebalk **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. Klik in het venster dat wordt geopend **[!UICONTROL Select a shared audience]** om naar de lijst met gedeelde soorten publiek/segmenten te gaan die beschikbaar zijn in de andere Adobe Experience Cloud-oplossingen.
1. Selecteer een publiek en bevestig het. De publieksinformatie wordt automatisch voltooid.

   Houd er rekening mee dat als u een gedeeld publiek wilt importeren, u het **[!UICONTROL Audience library]** product in de beheerconsole moet krijgen en beheerder moet zijn in Audience Manager. Raadpleeg de documentatie bij de [beheerconsole voor meer informatie](https://helpx.adobe.com/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Selecteer de gegevensbron van AMC van het **[!UICONTROL AMC Data source]** gebied om het type van gegevens te bepalen die worden verwacht.

   ![](assets/aam_import_audience_2.png)

1. Sla het publiek op.

Het publiek wordt geïmporteerd via een technische workflow. De geïmporteerde lijst bevat elementen die met behulp van de AMC-gegevensbron met elkaar in overeenstemming kunnen worden gebracht. De elementen die niet worden herkend door Adobe Campaign, worden niet geïmporteerd.

Het importproces duurt 24-36 uur om te synchroniseren, wanneer de segmenten direct uit de kernservice van Mensen of de Manager van het publiek worden ingevoerd. Na deze periode kunt u uw nieuwe publiek zoeken en gebruiken in Adobe Campaign.

>[!NOTE]
>
>Als u soorten publiek importeert van Adobe Analytics naar Adobe Campaign, moeten deze soorten publiek eerst worden gedeeld in People Core Service of Audience Manager. Dit proces duurt 12-24 uur en moet worden toegevoegd aan de synchronisatie van 24-36 uur met Campagne.
>
>In dat specifieke geval kan de tijd voor het delen van het publiek maximaal 60 uur bedragen. Raadpleeg deze [documentatie voor meer informatie over het delen van publiek in de People Core-service en Audience Manager van Adobe Analytics](https://marketing.adobe.com/resources/help/en_US/mcloud/t_publish_audience_segment.html).

De publieksgegevens worden volledig vervangen telkens als het wordt gesynchroniseerd. Alleen segmenten kunnen worden geïmporteerd. De korrelige gegevens met inbegrip van zeer belangrijk-waardeparen, eigenschappen en regels worden niet gesteund.

## Een publiek exporteren {#exporting-an-audience}

U kunt een publiek van de Campagne van Adobe naar de Manager van het Publiek of de kerndienst van Mensen uitvoeren gebruikend een werkschema. De processen voor het maken en gebruiken van een werkstroom worden beschreven in [dit document](../../workflow/using/building-a-workflow.md). Het geëxporteerde publiek wordt opgeslagen als segmenten in de hoofdservice Personen:

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

De synchronisatie tussen Adobe Campaign en de People core-service duurt 24 tot 36 uur. Na deze periode kunt u uw nieuwe doelgroep vinden in de hoofdservice Personen en deze opnieuw gebruiken in andere Adobe Experience Cloud-oplossingen. Raadpleeg deze [documentatie](https://marketing.adobe.com/resources/help/en_US/mcloud/t_audience_create.html)voor meer informatie over het gebruik van een gedeelde Adobe-campagne in de Adobe People core-service.

>[!NOTE]
>
>Om met elkaar in overeenstemming te kunnen worden gebracht, moeten de records een Adobe Experience Cloud-id (&#39;bezoeker-id&#39; of &#39;gedeclareerde id&#39;) hebben. De records die geen Adobe Experience Cloud-id hebben, worden genegeerd bij het exporteren en importeren van soorten publiek.

