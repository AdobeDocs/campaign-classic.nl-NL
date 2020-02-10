---
title: Cellen
seo-title: Cellen
description: Cellen
seo-description: null
page-status-flag: never-activated
uuid: 1b18928f-04e1-4268-ab8e-ff74d78599de
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: f7187d42-56e9-4681-b172-22abd43ecd29
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Cellen{#cells}

De **[!UICONTROL Cells]** activiteit verstrekt een mening van de diverse subsets in de vorm van gegevenskolommen. Het vergemakkelijkt manipulatie van subsets en is ook ontworpen om personalisatiemogelijkheden aan te moedigen.

![](assets/wf_split_cells.png)

Deze activiteit kan worden gevormd om specifieke parameters in te gaan die op gebruikersbehoeften worden gebaseerd. Standaard worden de details van elke subset via de tabbladen **[!UICONTROL Selection]** **[!UICONTROL Advanced]** en in een speciaal venster weergegeven. In het onderstaande voorbeeld is het formulier gewijzigd: er is een **[!UICONTROL Data]** tabblad toegevoegd om het koppelen van een aanbieding en een prioriteitsniveau voor elke subset mogelijk te maken.

![](assets/wf_split_cells_with_customization.png)

Voor deze configuratie is de volgende informatie toegevoegd aan het werkstroomformulier (in het **[!UICONTROL Administration > Configurations > Input forms]** knooppunt van de Adobe Campaign-structuur):

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

Personalisatie van formulieren in Adobe Campaign is gereserveerd voor ervaren gebruikers. Zie deze [sectie](../../configuration/using/identifying-a-form.md)voor meer informatie.
