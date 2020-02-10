---
title: Aanvullende gegevens
seo-title: Aanvullende gegevens
description: Aanvullende gegevens
seo-description: null
page-status-flag: never-activated
uuid: 81a889ce-b02d-4593-95fa-1de5601182e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 29339aad-fd8e-4dae-8f6e-2db87221ad04
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Aanvullende gegevens{#additional-data}

Tijdens een oproep aan de interactiemotor kunt u contextafhankelijke aanvullende informatie overbrengen. Deze gegevens kunnen afkomstig zijn van de doelgegevens die zijn opgeslagen in de werkentabel van een workflow (uitgaand kanaal) of de vraaggegevens die door de website worden verzonden tijdens de aanroep (binnenkomend kanaal). U kunt deze aanvullende gegevens gebruiken in de toelatingsregels, in het aanbieden van personalisatie, en u kunt het ook opslaan in een propositietabel.

Voor het binnenkomende kanaal, kan het nuttig zijn om informatie zoals de browser taal van de mensen terug te krijgen die de aanbieding raadplegen, of de naam van de agent van het vraagcentrum, bijvoorbeeld. U kunt deze vraaggegevens in de geschiktheidsregels dan gebruiken om een aanbieding slechts aan die mensen te presenteren die de Web-pagina in het Frans of Engels bekijken.

In een gericht werkschema (uitgaand kanaal), kunt u de doelgegevens tijdens een vraag aan de motor gebruiken. Bijvoorbeeld, kunt u het doel met gegevens van een ontvanger verbonden transactie of een extern gegevensbestand, via FDA verrijken.

## Aanvullende gegevensconfiguratie {#additional-data-configuration}

U moet het **nms:interactieschema** uitbreiden verbonden aan het milieu en de lijst van extra gebieden verklaren die tijdens een vraag aan de motor van de Interactie zullen worden gebruikt. Wanneer het creëren van de geschiktheidsregel of het aanpassen van een aanbieding, zullen deze gebieden van de knoop van de **Interactie** toegankelijk worden (verwijs naar het [Gebruiken van extra gegevens](#using-additional-data)).

Voor het binnenkomende kanaal, moet u de gebieden van vraaggegevens in de knoop van de **Interactie** toevoegen.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>De inzamelingen van XML worden gesteund op het binnenkomende kanaal, maar de verbindingen aan andere schema&#39;s zijn niet.

Voor het uitgaande kanaal, moet u een **targetData** element toevoegen dat de extra gebieden in de knoop van de **Interactie** bevat.

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

Als u aanvullende gegevens wilt overbrengen wanneer u de engine aanroept, moet u de variabele **interactionGlobalCtx** toevoegen aan de JavaScript-code van de webpagina. Voeg het knooppunt **Interaction** met de aanroepgegevens in deze variabele in. U moet dezelfde XML-structuur in het **nms:interactieschema** gebruiken. Zie: [Aanvullende gegevensconfiguratie](#additional-data-configuration).

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### Uitvoerkanaal {#output-channel}

U moet een doelworkflow maken waarin aanvullende gegevens in de werktabel worden geladen door dezelfde XML-structuur en dezelfde interne namen als in het **nms:interactieschema** te gebruiken. Zie: [Aanvullende gegevensconfiguratie](#additional-data-configuration).

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

Als u een aanbieding hebt gepersonaliseerd met behulp van aanvullende gegevens, worden deze gegevens standaard niet in de voorvertoning weergegeven omdat ze niet beschikbaar zijn in de database. Op het **[!UICONTROL Example of call data]** tabblad van de omgeving moet u waardevoorbeelden toevoegen die u in de voorvertoning wilt gebruiken. Houd rekening met dezelfde XML-structuur in de extensie **nms:interactieschema** . Voor meer op dit, verwijs naar [Extra gegevensconfiguratie](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

Klik op een waarde in het **[!UICONTROL Content personalization options for the preview]** **[!UICONTROL Call data]** veld en selecteer een waarde in de voorbeeldweergave.

![](assets/ita_calldata_preview2.png)

### Opslag {#storage}

Tijdens een vraag aan de motor, kunt u extra gegevens in de propositietabel opslaan om het gegevensbestand te verrijken. Deze gegevens kunnen worden gebruikt, bijvoorbeeld in rapporten, in ROI-berekeningen of voor latere processen.

>[!NOTE]
>
>U moet het schema **nms:propositionRcp** uitgebreid hebben en de gebieden verklaard die de op te slaan gegevens zullen bevatten. Voor meer informatie hierover: [Aanvullende gegevensconfiguratie](#additional-data-configuration).

Ga in de aanbiedingsruimte naar het **[!UICONTROL Storage]** tabblad en klik op de **[!UICONTROL Add]** knop.

Selecteer in de **[!UICONTROL Storage path]** kolom het opslagveld in de tabel met profielen. Selecteer in de **[!UICONTROL Expression]** kolom het aanvullende veld in het **[!UICONTROL Interaction]** knooppunt.

U kunt vraaggegevens terugwinnen wanneer het voorstel wordt geproduceerd of wanneer het wordt goedgekeurd (wanneer de persoon op de aanbieding klikt).

![](assets/ita_calldata_storage.png)

