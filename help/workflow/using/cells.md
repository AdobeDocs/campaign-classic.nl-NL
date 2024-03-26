---
product: campaign
title: Cellen
description: Cellen
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: 7b562dba-7e4b-40a7-91db-7b9379de44ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 13%

---

# Cellen{#cells}



De **[!UICONTROL Cells]** de activiteit verstrekt een mening van de diverse ondergroepen in de vorm van gegevenskolommen. Het vergemakkelijkt manipulatie van subsets en is ook ontworpen om personalisatiemogelijkheden aan te moedigen.

![](assets/wf_split_cells.png)

Deze activiteit kan worden gevormd om specifieke parameters in te gaan die op gebruikersbehoeften worden gebaseerd. Standaard worden de details van elke subset in een speciaal venster beschreven via de **[!UICONTROL Selection]** en **[!UICONTROL Advanced]** tabs. In het onderstaande voorbeeld is het formulier gewijzigd: **[!UICONTROL Data]** tab is toegevoegd om het koppelen van een aanbieding en een prioriteitsniveau voor elke subset mogelijk te maken.

![](assets/wf_split_cells_with_customization.png)

Voor deze configuratie is de volgende informatie toegevoegd aan het werkstroomformulier (in het gedeelte **[!UICONTROL Administration > Configurations > Input forms]** knooppunt van de Adobe Campaign-structuur):

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
