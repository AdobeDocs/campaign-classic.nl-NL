---
product: campaign
title: Aanvullende gegevens
description: Aanvullende gegevens
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 01adb584-5308-4d41-a6f1-223a97efa10f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# Aanvullende gegevens{#additional-data}



Tijdens een oproep aan de interactiemotor kunt u contextafhankelijke aanvullende informatie overbrengen. Deze gegevens kunnen afkomstig zijn van de doelgegevens die zijn opgeslagen in de werkentabel van een workflow (uitgaand kanaal) of de vraaggegevens die door de website worden verzonden tijdens de aanroep (binnenkomend kanaal). U kunt deze aanvullende gegevens gebruiken in de toelatingsregels, in het aanbieden van personalisatie, en u kunt het ook opslaan in een propositietabel.

Voor het binnenkomende kanaal, kan het nuttig zijn om informatie zoals de browser taal van de mensen terug te krijgen die de aanbieding raadplegen, of de naam van de agent van het vraagcentrum, bijvoorbeeld. U kunt deze vraaggegevens in de geschiktheidsregels dan gebruiken om een aanbieding slechts aan die mensen te presenteren die de Web-pagina in het Frans of Engels bekijken.

In een gericht werkschema (uitgaand kanaal), kunt u de doelgegevens tijdens een vraag aan de motor gebruiken. Bijvoorbeeld, kunt u het doel met gegevens van een ontvanger verbonden transactie of een extern gegevensbestand, via FDA verrijken.

## Aanvullende gegevensconfiguratie {#additional-data-configuration}

U moet het dialoogvenster **nms:interactie** schema verbonden aan het milieu en verklaar de lijst van extra gebieden die tijdens een vraag aan de motor van de Interactie zullen worden gebruikt. Wanneer u de toelatingsregel maakt of een aanbieding personaliseert, worden deze velden toegankelijk via de **Interactie** node (verwijzing naar [Extra gegevens gebruiken](#using-additional-data)).

Voor het binnenkomende kanaal, moet u de gebieden van vraaggegevens in toevoegen **Interactie** knooppunt.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>De inzamelingen van XML worden gesteund op het binnenkomende kanaal, maar de verbindingen aan andere schema&#39;s zijn niet.

Voor het uitgaande kanaal moet u een **targetData** element met de aanvullende velden in het dialoogvenster **Interactie** knooppunt.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>Verzamelingen worden niet ondersteund voor het uitgaande kanaal. U kunt echter koppelingen naar andere schema&#39;s maken.

Als u deze gegevens in de tabel met voorstellen wilt opslaan, moet u ook de opties **nms:propositionRcp** en declareer deze velden.

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## Aanvullende gegevensimplementatie {#additional-data-implementation}

### Invoerkanaal (webpagina) {#input-channel--web-page-}

Als u aanvullende gegevens wilt overbrengen wanneer u de engine aanroept, moet u de opdracht **interactionGlobalCtx** in de JavaScript-code van de webpagina. Voeg de **Interactie** knoop die de vraaggegevens in deze variabele bevatten. U moet dezelfde XML-structuur gebruiken als in het dialoogvenster **nms:interactie** schema. Zie: [Aanvullende gegevensconfiguratie](#additional-data-configuration).

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### Uitvoerkanaal {#output-channel}

U moet een doelworkflow maken waarin aanvullende gegevens in de werktabel worden geladen door dezelfde XML-structuur en dezelfde interne namen als in de werktabel te gebruiken **nms:interactie** schema. Zie: [Aanvullende gegevensconfiguratie](#additional-data-configuration).

## Extra gegevens gebruiken {#using-additional-data}

### Subsidiabiliteitsregels {#eligibility-rules}

U kunt de aanvullende gegevens gebruiken in de subsidiabiliteitsregels voor voorstellen, categorieën en gewichten.

U kunt bijvoorbeeld het aanbod alleen laten weergeven aan mensen die de pagina in het Engels bekijken.

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>U moet de regel beperken op de kanalen waarvoor de gegevens worden bepaald. In ons voorbeeld beperken we de regel voor het binnenkomende webkanaal (**[!UICONTROL Taken into account if]** veld).

### Personalisatie {#personalization}

U kunt deze extra gegevens ook gebruiken wanneer u een aanbieding personaliseert. U kunt bijvoorbeeld een voorwaarde toevoegen voor de navigatietaal

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>U moet de personalisatie op de kanalen beperken waarvoor de gegevens worden bepaald. In ons voorbeeld beperken we de regel voor het binnenkomende webkanaal.

Als u een aanbieding hebt gepersonaliseerd met behulp van aanvullende gegevens, worden deze gegevens standaard niet in de voorvertoning weergegeven omdat ze niet beschikbaar zijn in de database. In het milieu **[!UICONTROL Example of call data]** kunt gebruiken, moet u waardesteekproeven toevoegen in de voorproef. Neem dezelfde XML-structuur in acht als in de **nms:interactie** schema-extensie. Raadpleeg voor meer informatie hierover [Aanvullende gegevensconfiguratie](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

Klik tijdens het voorvertonen op **[!UICONTROL Content personalization options for the preview]** en selecteer een waarde in het dialoogvenster **[!UICONTROL Call data]** veld.

![](assets/ita_calldata_preview2.png)

### Opslag {#storage}

Tijdens een vraag aan de motor, kunt u extra gegevens in de propositietabel opslaan om het gegevensbestand te verrijken. Deze gegevens kunnen worden gebruikt, bijvoorbeeld in rapporten, in ROI-berekeningen of voor latere processen.

>[!NOTE]
>
>U moet de **nms:propositionRcp** en declareert de velden die de op te slaan gegevens bevatten. Voor meer informatie hierover: [Aanvullende gegevensconfiguratie](#additional-data-configuration).

Ga in de aanbiedingsruimte naar de **[!UICONTROL Storage]** en klik op de knop **[!UICONTROL Add]** knop.

In de **[!UICONTROL Storage path]** selecteert u het opslagveld in de tabel met profielen. In de **[!UICONTROL Expression]** de kolom, selecteer het extra gebied in **[!UICONTROL Interaction]** knooppunt.

U kunt vraaggegevens terugwinnen wanneer het voorstel wordt geproduceerd of wanneer het wordt goedgekeurd (wanneer de persoon op de aanbieding klikt).

![](assets/ita_calldata_storage.png)
