---
product: campaign
title: Soorten publiek importeren en exporteren
description: Soorten publiek importeren en exporteren
feature: Audiences
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---


# Soorten publiek importeren en exporteren{#importing-and-exporting-audiences}



## Een publiek importeren {#importing-an-audience}

U kunt soorten publiek/segmenten vanuit Audience Manager importeren in Adobe Campaign via de lijsten met ontvangers.

1. Ga naar het knooppunt **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** in de Adobe Campaign Explorer.
1. Selecteer **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]** op de actiebalk.

   ![](assets/aam_import_audience.png)

1. Klik in het venster dat wordt geopend op **[!UICONTROL Select a shared audience]** om naar de lijst met gedeelde soorten publiek/segmenten te gaan die beschikbaar zijn in de andere Adobe Experience Cloud-oplossingen.
1. Selecteer een publiek en bevestig het. De publieksinformatie wordt automatisch voltooid.

   Als u een gedeeld publiek wilt importeren, moet u het **[!UICONTROL Audience library]** -product in de beheerconsole toewijzen en een beheerder in Audience Manager zijn. Voor meer op dit, verwijs naar de [&#x200B; Admin consoledocumentatie &#x200B;](https://helpx.adobe.com/nl/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Selecteer de AMC-gegevensbron in het veld **[!UICONTROL AMC Data source]** om het type gegevens te definiëren dat wordt verwacht.

   ![](assets/aam_import_audience_2.png)

1. Sla het publiek op.

Het publiek wordt geïmporteerd via een technische workflow. De geïmporteerde lijst bevat elementen die met behulp van de AMC-gegevensbron met elkaar in overeenstemming kunnen worden gebracht. De elementen die niet door Adobe Campaign worden herkend, worden niet geïmporteerd.

Het importeren duurt 24 tot 36 uur voordat u het programma synchroniseert wanneer segmenten rechtstreeks uit Audience Manager worden geïmporteerd. Na deze periode kun je het nieuwe publiek in Adobe Campaign vinden en gebruiken.

>[!NOTE]
>
>Als u soorten publiek importeert van Adobe Analytics naar Adobe Campaign, moeten deze soorten publiek eerst worden gedeeld in Audience Manager. Dit proces duurt 12-24 uur en moet worden toegevoegd aan de synchronisatie van 24-36 uur met Campagne.
>
>In dat specifieke geval kan de tijd voor het delen van het publiek maximaal 60 uur bedragen. Voor meer informatie over het publiek dat van Adobe Analytics in de manager van het Publiek deelt, verwijs naar [&#x200B; documentatie van Adobe Analytics &#x200B;](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=nl-NL){target="_blank"}.

De publieksgegevens worden volledig vervangen telkens als het wordt gesynchroniseerd. Alleen segmenten kunnen worden geïmporteerd. De korrelige gegevens met inbegrip van zeer belangrijk-waardeparen, eigenschappen en regels worden niet gesteund.

## Een publiek exporteren {#exporting-an-audience}

U kunt een publiek van Adobe Campaign naar Audience Manager uitvoeren gebruikend een werkschema. De processen voor het creëren van en het gebruiken van een werkschema zijn gedetailleerd in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=nl-NL){target="_blank"}. Het geëxporteerde publiek wordt opgeslagen als segmenten:

1. Maak een nieuwe doelworkflow.
1. Wijs op een reeks ontvangers aan de hand van de verschillende beschikbare activiteiten.
1. Nadat u een **[!UICONTROL Update shared audience]** -activiteit hebt geselecteerd, sleept u deze en zet u de activiteit vervolgens neer.

   ![](assets/aam_export_example.png)

1. Definieer het publiek dat u wilt exporteren met de optie **[!UICONTROL Select a shared audience]** . In het venster dat wordt geopend, kunt u een bestaand publiek selecteren of een nieuw publiek maken.

   Als u een bestaand publiek selecteert, worden alleen de nieuwe records aan het publiek toegevoegd.

   Als u de lijst met ontvangers wilt exporteren naar een nieuw publiek, vult u het veld **[!UICONTROL Segment name]** in en klikt u op **[!UICONTROL Create]** voordat u het nieuwe publiek selecteert.

   Voltooi de bewerking door te klikken op het symbool boven in het venster en vervolgens op de knop **[!UICONTROL OK]** .

1. Selecteer **[!UICONTROL AMC Data source]** om het verwachte gegevenstype op te geven. Het schema wordt automatisch bepaald.

   ![](assets/aam_export_audience_activity.png)

1. Sla het publiek op.

Het publiek wordt vervolgens geëxporteerd. De activiteit van het sparen publiek heeft twee uitgaande overgangen. De hoofdovergang bevat de ontvangers die zijn geëxporteerd. De aanvullende overgang bevat de ontvangers die niet met een bezoekersidentiteitskaart of gedeclareerde identiteitskaart konden in kaart worden gebracht.

Synchronisatie tussen oplossingen duurt 24-36 uur. Na deze periode kunt u uw nieuwe publiek vinden en opnieuw gebruiken in andere Adobe Experience Cloud-oplossingen. Voor meer informatie bij het gebruiken van een Adobe Campaign gedeeld publiek, verwijs naar deze [&#x200B; documentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/core-services/interface/services/audiences/create){target="_blank"}.

>[!NOTE]
>
>Om met elkaar in overeenstemming te kunnen worden gebracht, moeten de records een Adobe Experience Cloud-id (&#39;bezoeker-id&#39; of &#39;gedeclareerde id&#39;) hebben. De records zonder Adobe Experience Cloud-id worden genegeerd bij het exporteren en importeren van soorten publiek.
