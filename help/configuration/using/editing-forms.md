---
product: campaign
title: Formulieren bewerken
description: Formulieren bewerken
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: a6549ad4d94b93d65752df66aeec39b90e4c3ec5
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 5%

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

