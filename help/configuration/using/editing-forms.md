---
product: campaign
title: Formulieren bewerken
description: Formulieren bewerken
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: f4b9ac3300094a527b5ec1b932d204f0e8e5ee86
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 4%

---


# Formulieren bewerken{#editing-forms}

![](../../assets/common.svg)

## Overzicht

Marktdeelnemers en operatoren gebruiken invoerformulieren om records te maken, te wijzigen en voor te vertonen. Forms geeft een visuele weergave van informatie weer.

U kunt invoerformulieren maken en wijzigen:

* U kunt de fabrieksinvoerformulieren wijzigen die standaard worden geleverd. De fabrieksinvoerformulieren zijn gebaseerd op de fabrieksgegevensschema&#39;s.
* U kunt aangepaste invoerformulieren maken op basis van gegevensschema&#39;s die u definieert.

Forms zijn entiteiten van `xtk:form` type. U kunt de invoerformulierstructuur bekijken in het dialoogvenster `xtk:form` schema. Kies **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** in het menu. Meer informatie over [formulierstructuur](form-structure.md).

Kies **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** in het menu:

![](assets/d_ncs_integration_form_arbo.png)

Als u formulieren wilt ontwerpen, bewerkt u de XML-inhoud in de XML-editor:

![](assets/d_ncs_integration_form_edit.png)

[Meer informatie](form-structure.md#formatting).

Als u een voorbeeld van een formulier wilt bekijken, klikt u op de knop **[!UICONTROL Preview]** tab:

![](assets/d_ncs_integration_form_preview.png)

## Formuliertypen

U kunt verschillende typen invoerformulieren maken. Het formuliertype bepaalt hoe gebruikers door het formulier navigeren:

* Consolescherm

   Dit is het standaardformuliertype. Het formulier bestaat uit één pagina.

   ![](assets/console_screen_form.png)

* Contentmanagement

   Gebruik dit formuliertype voor inhoudsbeheer. Zie dit [use case](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Wizard

   Dit formulier bestaat uit meerdere zwevende schermen die in een bepaalde reeks zijn geordend. Gebruikers navigeren van het ene scherm naar het andere. [Meer informatie](form-structure.md#wizards).

* Iconbox

   Dit formulier bestaat uit meerdere pagina&#39;s. Gebruikers kunnen door het formulier navigeren door pictogrammen links van het formulier te selecteren.

   ![](assets/iconbox_form_preview.png)

* Laptop

   Dit formulier bestaat uit meerdere pagina&#39;s. Als gebruikers in het formulier willen navigeren, selecteren ze boven aan het formulier tabbladen.

   ![](assets/notebook_form_preview.png)

* Verticaal deelvenster

   In dit formulier wordt een boomstructuur weergegeven.

* Horizontaal venster

   Dit formulier bevat een lijst met items.

## Containers

In formulieren kunt u containers voor verschillende doeleinden gebruiken:

* Inhoud indelen in formulieren
* Toegang tot invoervelden definiëren
* Formulieren nesten in andere formulieren

[Meer informatie](form-structure.md#containers).

### Inhoud ordenen

Gebruik containers om inhoud in formulieren te ordenen:

* U kunt velden groeperen in secties.
* U kunt pagina&#39;s toevoegen aan formulieren met meerdere pagina&#39;s.

Als u een container wilt invoegen, gebruikt u de `<container>` element. [Meer informatie](form-structure.md#containers).

#### Velden groeperen

Gebruik containers om invoervelden te groeperen in georganiseerde secties.

Gebruik dit element om een sectie in een formulier in te voegen: `<container type="frame">`. Als u een sectietitel wilt toevoegen, kunt u desgewenst de opdracht `label` kenmerk.

Syntaxis: `<container type="frame" label="`*section_title*`"> […] </container>`

In dit voorbeeld definieert een container de **Maken** , die de **[!UICONTROL Created by]** en **[!UICONTROL Name]** invoervelden:

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### Pagina&#39;s toevoegen aan formulieren met meerdere pagina&#39;s

Voor formulieren met meerdere pagina&#39;s gebruikt u een container om een formulierpagina te maken.

In dit voorbeeld worden containers voor de **Algemeen** en **Details** pagina&#39;s van een formulier:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Toegang tot velden definiëren

Gebruik containers om te definiëren wat zichtbaar is en om de toegang tot velden te definiëren. U kunt groepen velden in- of uitschakelen.

### Formulieren nesten

Gebruik containers om formulieren in andere formulieren te nesten. [Meer informatie](#add-pages-to-multipage-forms).

## Verwijzingen naar afbeeldingen

Kies **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** in het menu.

Als u een afbeelding wilt koppelen aan een element in het formulier, bijvoorbeeld een pictogram, kunt u een verwijzing naar een afbeelding toevoegen. Gebruik de `img` in het dialoogvenster `<container>` element.

Syntaxis: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

In dit voorbeeld worden verwijzingen naar de `book.png` en `detail.png` afbeeldingen van de `ncm` naamruimte:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

Deze afbeeldingen worden gebruikt voor pictogrammen waarop gebruikers klikken om door een formulier met meerdere pagina&#39;s te navigeren:

![](assets/nested_forms_preview.png)
