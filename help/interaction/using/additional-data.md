---
solution: Campaign Classic
product: campaign
title: Aanvullende data
description: Aanvullende data
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---


# Aanvullende data{#additional-data}

Tijdens een oproep aan de interactiemotor kunt u contextafhankelijke aanvullende informatie overbrengen. Deze gegevens kunnen afkomstig zijn van de doelgegevens die zijn opgeslagen in de werkentabel van een workflow (uitgaand kanaal) of de vraaggegevens die door de website worden verzonden tijdens de aanroep (binnenkomend kanaal). U kunt deze aanvullende gegevens gebruiken in de toelatingsregels, in het aanbieden van personalisatie, en u kunt het ook opslaan in een propositietabel.

Voor het binnenkomende kanaal, kan het nuttig zijn om informatie zoals de browser taal van de mensen terug te krijgen die de aanbieding raadplegen, of de naam van de agent van het vraagcentrum, bijvoorbeeld. U kunt deze vraaggegevens in de geschiktheidsregels dan gebruiken om een aanbieding slechts aan die mensen te presenteren die de Web-pagina in het Frans of Engels bekijken.

In een gericht werkschema (uitgaand kanaal), kunt u de doelgegevens tijdens een vraag aan de motor gebruiken. Bijvoorbeeld, kunt u het doel met gegevens van een ontvanger verbonden transactie of een extern gegevensbestand, via FDA verrijken.

## Aanvullende gegevensconfiguratie {#additional-data-configuration}

U moet het **nms:interaction** schema uitbreiden verbonden aan het milieu en de lijst van extra gebieden verklaren die tijdens een vraag aan de motor van de Interactie zullen worden gebruikt. Wanneer het creëren van de geschiktheidsregel of het aanpassen van een aanbieding, zullen deze gebieden van de **knoop Interaction** toegankelijk worden (verwijs naar [het Gebruiken van extra gegevens](#using-additional-data)).

Voor het binnenkomende kanaal, moet u de gebieden van vraaggegevens in **Interaction** knoop toevoegen.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>De inzamelingen van XML worden gesteund op het binnenkomende kanaal, maar de verbindingen aan andere schema&#39;s zijn niet.

Voor het uitgaande kanaal, moet u een **targetData** element toevoegen die de extra gebieden in **Interaction** knoop bevatten.

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

Als u deze gegevens in de propositietabel wilt opslaan, moet u ook het schema **nms:propositionRcp** uitbreiden en deze velden declareren.

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## Aanvullende gegevensimplementatie {#additional-data-implementation}

### Invoerkanaal (webpagina) {#input-channel--web-page-}

Als u aanvullende gegevens wilt overbrengen wanneer u de engine aanroept, moet u de variabele **interactionGlobalCtx** toevoegen aan de JavaScript-code van de webpagina. Voeg de **Interaction** knoop in die de vraaggegevens in deze variabele bevat. U moet de zelfde xml structuur respecteren die in **nms:interaction** schema is. Zie: [Aanvullende gegevensconfiguratie](#additional-data-configuration).

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### Uitvoerkanaal {#output-channel}

U moet een doelworkflow maken waarin aanvullende gegevens in de werktabel worden geladen door dezelfde XML-structuur en dezelfde interne namen als in het schema **nms:interaction** te respecteren. Zie: [Aanvullende gegevensconfiguratie](#additional-data-configuration).

## Extra gegevens {#using-additional-data} gebruiken

### Subsidiabiliteitsregels {#eligibility-rules}

U kunt de aanvullende gegevens gebruiken in de subsidiabiliteitsregels voor voorstellen, categorieën en gewichten.

U kunt bijvoorbeeld het aanbod alleen laten weergeven aan mensen die de pagina in het Engels bekijken.

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>U moet de regel beperken op de kanalen waarvoor de gegevens worden bepaald. In ons voorbeeld, beperken wij de regel op het binnenkomende Webkanaal (**[!UICONTROL Taken into account if]** gebied).

### Personalisatie {#personalization}

U kunt deze extra gegevens ook gebruiken wanneer u een aanbieding personaliseert. U kunt bijvoorbeeld een voorwaarde toevoegen voor de navigatietaal

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>U moet de personalisatie op de kanalen beperken waarvoor de gegevens worden bepaald. In ons voorbeeld beperken we de regel voor het binnenkomende webkanaal.

Als u een aanbieding hebt gepersonaliseerd met behulp van aanvullende gegevens, worden deze gegevens standaard niet in de voorvertoning weergegeven omdat ze niet beschikbaar zijn in de database. Op het **[!UICONTROL Example of call data]** lusje van het milieu, moet u waardesteekproeven toevoegen om in de voorproef te gebruiken. Gelieve te respecteren de zelfde xml structuur die in **nms:interaction** schemauitbreiding is. Voor meer op dit, verwijs naar [Aanvullende gegevensconfiguratie](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

Klik tijdens het voorvertonen op **[!UICONTROL Content personalization options for the preview]** en selecteer een waarde in het veld **[!UICONTROL Call data]**.

![](assets/ita_calldata_preview2.png)

### Opslag {#storage}

Tijdens een vraag aan de motor, kunt u extra gegevens in de propositietabel opslaan om het gegevensbestand te verrijken. Deze gegevens kunnen worden gebruikt, bijvoorbeeld in rapporten, in ROI-berekeningen of voor latere processen.

>[!NOTE]
>
>U moet het schema **nms:propositionRcp** hebben uitgebreid en de gebieden verklaard die de op te slaan gegevens zullen bevatten. Voor meer informatie hierover: [Aanvullende gegevensconfiguratie](#additional-data-configuration).

Ga in de aanbiedingsruimte naar het tabblad **[!UICONTROL Storage]** en klik op de knop **[!UICONTROL Add]**.

Selecteer in de kolom **[!UICONTROL Storage path]** het opslagveld in de tabel met profielen. Selecteer in de kolom **[!UICONTROL Expression]** het extra veld in het knooppunt **[!UICONTROL Interaction]**.

U kunt vraaggegevens terugwinnen wanneer het voorstel wordt geproduceerd of wanneer het wordt goedgekeurd (wanneer de persoon op de aanbieding klikt).

![](assets/ita_calldata_storage.png)

