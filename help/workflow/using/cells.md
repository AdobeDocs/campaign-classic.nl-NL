---
solution: Campaign Classic
product: campaign
title: Cellen
description: Cellen
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 8%

---


# Cellen{#cells}

De activiteit **[!UICONTROL Cells]** verstrekt een mening van de diverse subsets in de vorm van gegevenskolommen. Het vergemakkelijkt manipulatie van subsets en is ook ontworpen om personalisatiemogelijkheden aan te moedigen.

![](assets/wf_split_cells.png)

Deze activiteit kan worden gevormd om specifieke parameters in te gaan die op gebruikersbehoeften worden gebaseerd. Standaard wordt de details van elke subset in een speciaal venster beschreven via de tabbladen **[!UICONTROL Selection]** en **[!UICONTROL Advanced]**. In het onderstaande voorbeeld is het formulier gewijzigd: Er is een **[!UICONTROL Data]** tabblad toegevoegd om het koppelen van een aanbieding en een prioriteitsniveau voor elke subset mogelijk te maken.

![](assets/wf_split_cells_with_customization.png)

Voor deze configuratie is de volgende informatie toegevoegd aan het werkstroomformulier (in het knooppunt **[!UICONTROL Administration > Configurations > Input forms]** van de Adobe Campaign-structuur):

```
<container img="nms:miniatures/mini-enrich.png" label="Data">
                <input xpath="@code"/>
                <container xpath="select/node[@alias='@numTest']">
                  <input alwaysActive="true" expr="'long'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Priority'" type="expr" xpath="@label"/>
                  <input label="Priority" maxValue="12" minValue="0" type="number"
                         xpath="@value" xpathEditFromType="@type"/>
                </container>
                <container xpath="select/node[@alias='@test']">
                  <input alwaysActive="true" expr="'string'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Identifier'" type="expr" xpath="@label"/>
                  <input label="Cell identifier" xpath="@value"/>
                </container>
                <container xpath="select/node[@alias='linkTest']">
                  <input alwaysActive="true" expr="'link'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'nms:offer'" type="expr" xpath="@dataType"/>
                  <input alwaysActive="true" expr="'Offre'" type="expr" xpath="@label"/>
                  <input computeStringAlias="@valueLabel" label="Offers" notifyPathList="@_cs|@valueLabel"
                         schema="nms:offer" type="linkEdit" xpath="@value"/>
                </container>
```

Personalisatie van formulieren in Adobe Campaign is gereserveerd voor ervaren gebruikers. Raadpleeg deze [sectie](../../configuration/using/identifying-a-form.md) voor meer informatie.
