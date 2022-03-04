---
product: campaign
title: Opeenvolging webformulierpagina's definiëren
description: Opeenvolging webformulierpagina's definiëren
feature: Web Forms
exl-id: c5b5c398-c13b-4ebe-88b2-8ff84741422e
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 0%

---

# Opeenvolging webformulierpagina&#39;s definiëren{#defining-web-forms-page-sequencing}

![](../../assets/common.svg)

Het formulier kan een of meer pagina&#39;s bevatten. Het wordt gebouwd door een diagram dat u opeenvolgende pagina&#39;s, het testen, manuscriptuitvoering, paginakijl en opnamestappen laat. De globale wijze van het diagramontwerp is het zelfde als voor een werkschema van de Campagne.

## Vorige pagina en volgende pagina {#about-previous-page-and-next-page}

Voor elke pagina kunt u het dialoogvenster **[!UICONTROL Next]** of **[!UICONTROL Previous]** knoppen. Selecteer hiertoe de betrokken pagina en selecteer de optie **[!UICONTROL Disable next page]** of **[!UICONTROL Disallow returning to the previous page]** .

![](assets/s_ncs_admin_survey_no_next_page.png)

U kunt deze knoppen vervangen door koppelingen. Zie [HTML-inhoud invoegen](static-elements-in-a-web-form.md#inserting-html-content).

## Een sprong invoegen {#inserting-a-jump}

De **[!UICONTROL Jump]** object geeft toegang tot een andere pagina of een ander formulier wanneer de gebruiker klikt **[!UICONTROL Next]**.

De bestemming kan zijn:

* Een andere pagina van het formulier. Selecteer **[!UICONTROL Internal activity]** en geef vervolgens de gewenste pagina op, zoals hieronder:

   ![](assets/s_ncs_admin_jump_param1.png)

* Een ander formulier. Selecteer hiervoor de optie **[!UICONTROL Explicit]** en geeft u het doelformulier op.

   ![](assets/s_ncs_admin_jump_param2.png)

* De bestemming kan in een variabele worden opgeslagen. Selecteer deze optie in dit geval in de vervolgkeuzelijst, zoals hieronder wordt weergegeven:

   ![](assets/s_ncs_admin_jump_param3.png)

* De **[!UICONTROL Comment]** kunt u informatie invoeren die door de operator zichtbaar wordt wanneer deze op het object in het diagram klikt.

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## Voorbeeld: toegang krijgen tot een ander formulier volgens een parameter van de URL {#example--accessing-another-form-according-to-a-parameter-of-the-url}

In het volgende voorbeeld, willen wij een vorm van het Web vormen die, wanneer goedgekeurd, een andere vorm zal tonen die door een parameter van URL wordt aangewezen. Hiervoor voert u de volgende stappen uit:

1. Een sprong invoegen aan het einde van een formulier: dit vervangt de **[!UICONTROL End]** doos.

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. Voeg in de formuliereigenschappen een parameter toe (**next**) opgeslagen in een lokale variabele (**next**). De lokale variabelen worden gedetailleerd in [Gegevens opslaan in een lokale variabele](web-forms-answers.md#storing-data-in-a-local-variable).

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. Bewerk de **[!UICONTROL Jump]** object, selecteert u de **[!UICONTROL Stored in a variable]** en selecteert u de optie **next** in de keuzelijst.

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. De leverings-URL moet de interne naam van het doelformulier bevatten, bijvoorbeeld:

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   Wanneer de gebruiker op de knop **[!UICONTROL Approve]** knop, formulier **APP22** wordt weergegeven.

## Een koppeling naar een andere pagina van het formulier invoegen {#inserting-a-link-to-another-page-of-the-form}

U kunt koppelingen naar andere pagina&#39;s van het formulier invoegen. Hiervoor voegt u een **[!UICONTROL Link]** typ statisch element op de pagina. Raadpleeg voor meer informatie hierover [Een koppeling invoegen](static-elements-in-a-web-form.md#inserting-a-link).

## Voorwaardelijke paginaweergave {#conditional-page-display}

### Weergeven op basis van antwoorden {#display-based-on-responses}

De **[!UICONTROL Test]** kunt u de volgorde van pagina&#39;s in een formulier bepalen. Hiermee kunt u verschillende vertakkingslijnen definiëren, afhankelijk van de testresultaten. Hierdoor kunt u verschillende pagina&#39;s weergeven, afhankelijk van de antwoorden van gebruikers.

U kunt bijvoorbeeld een andere pagina weergeven voor klanten die al online bestellingen hebben geplaatst, en een andere pagina voor klanten die meer dan tien bestellingen hebben geplaatst. Hiervoor voegt u op de eerste pagina van het formulier een **[!UICONTROL Number]** Typ een invoerveld voor de gebruiker waarin wordt aangegeven hoeveel bestellingen de gebruiker heeft geplaatst.

![](assets/s_ncs_admin_survey_test_ex0.png)

U kunt deze informatie opslaan in een veld van de database of een lokale variabele gebruiken.

>[!NOTE]
>
>De opslagmodi worden nader beschreven in [Responsopslagvelden](web-forms-answers.md#response-storage-fields).

In ons voorbeeld, willen wij een variabele gebruiken:

![](assets/s_ncs_admin_survey_test_ex1.png)

Voeg in het diagram van het formulier een testvak in om de voorwaarden te definiëren. Voor elke voorwaarde, zal een nieuwe tak bij de output van de testdoos worden toegevoegd.

![](assets/s_ncs_admin_survey_test_ex2.png)

Selecteer **[!UICONTROL Activate the default branching]** optie om een overgang toe te voegen voor gevallen waarin geen van de voorwaarden waar is. Deze optie is niet nodig als elk mogelijk geval onder de vastgestelde voorwaarden valt.

Definieer vervolgens de volgorde van de pagina wanneer een van de voorwaarden waar is, bijvoorbeeld:

![](assets/s_ncs_admin_survey_test_ex3.png)

### Weergeven op basis van parameters {#display-based-on-parameters}

U kunt de pagina ook personaliseren die volgens de initialisatieparameters van de vorm van het Web of volgens de waarden in het gegevensbestand wordt opgeslagen. Zie [URL-parameters van formulier](defining-web-forms-properties.md#form-url-parameters).

## Scripts toevoegen {#adding-scripts}

De **[!UICONTROL Script]** kunt u een JavaScript-script rechtstreeks invoeren, bijvoorbeeld om de waarde van een veld te wijzigen, gegevens op te halen uit de database of een Adobe Campaign API aan te roepen.

## De eindpagina aanpassen {#personalizing-the-end-page}

U moet een eindpagina aan het eind van het diagram plaatsen. De eindpagina wordt weergegeven wanneer de gebruiker op de knop **[!UICONTROL Approve]** in het webformulier.

Als u deze pagina wilt aanpassen, dubbelklikt u op **[!UICONTROL End]** en voert u de inhoud van de pagina in de centrale editor in.

![](assets/s_ncs_admin_survey_end_page_edit.png)

* U kunt bestaande HTML-inhoud kopiëren en plakken. Klik op **[!UICONTROL Display source code]** en voeg de HTML-code in.
* U kunt een externe URL gebruiken; Hiervoor selecteert u de desbetreffende optie en voert u de URL in van de pagina die u wilt weergeven.
