---
solution: Campaign Classic
product: campaign
title: De volgorde van webformulierpagina’s definiëren
description: De volgorde van webformulierpagina’s definiëren
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 2%

---


# De volgorde van webformulierpagina’s definiëren{#defining-web-forms-page-sequencing}

Het formulier kan een of meer pagina&#39;s bevatten. Het wordt gebouwd door een diagram dat u opeenvolgende pagina&#39;s, het testen, manuscriptuitvoering, paginakijl en opnamestappen laat. De globale wijze van het diagramontwerp is het zelfde als voor een werkschema van de Campagne.

## Informatie over vorige en volgende pagina {#about-previous-page-and-next-page}

Voor elke pagina kunt u de knoppen **[!UICONTROL Next]** of **[!UICONTROL Previous]** verwijderen. Selecteer hiertoe de betrokken pagina en selecteer de optie **[!UICONTROL Disable next page]** of **[!UICONTROL Disallow returning to the previous page]**.

![](assets/s_ncs_admin_survey_no_next_page.png)

U kunt deze knoppen vervangen door koppelingen. Zie [HTML-inhoud invoegen](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

## Een sprong {#inserting-a-jump} invoegen

Met het object **[!UICONTROL Jump]** hebt u toegang tot een andere pagina of een ander formulier wanneer de gebruiker op **[!UICONTROL Next]** klikt.

De bestemming kan zijn:

* Een andere pagina van het formulier. Selecteer **[!UICONTROL Internal activity]** om dit te doen en geef vervolgens de gewenste pagina op, zoals hieronder:

   ![](assets/s_ncs_admin_jump_param1.png)

* Een ander formulier. Hiervoor selecteert u de optie **[!UICONTROL Explicit]** en geeft u het doelformulier op.

   ![](assets/s_ncs_admin_jump_param2.png)

* De bestemming kan in een variabele worden opgeslagen. Selecteer deze optie in dit geval in de vervolgkeuzelijst, zoals hieronder wordt weergegeven:

   ![](assets/s_ncs_admin_jump_param3.png)

* Op het tabblad **[!UICONTROL Comment]** kunt u informatie invoeren die zichtbaar is voor de operator wanneer deze op het object in het diagram klikt.

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## Voorbeeld: een ander formulier openen volgens een parameter van de URL {#example--accessing-another-form-according-to-a-parameter-of-the-url}

In het volgende voorbeeld, willen wij een vorm van het Web vormen die, wanneer goedgekeurd, een andere vorm zal tonen die door een parameter van URL wordt aangewezen. Hiervoor voert u de volgende stappen uit:

1. Een sprong invoegen aan het einde van een formulier: dit vervangt **[!UICONTROL End]** doos.

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. Voeg in de formuliereigenschappen een parameter (**next**) toe die is opgeslagen in een lokale variabele (**next**). Lokale variabelen worden beschreven in [Gegevens opslaan in een lokale variabele](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable).

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. Bewerk het object **[!UICONTROL Jump]**, selecteer de optie **[!UICONTROL Stored in a variable]** en selecteer de variabele **next** in het keuzemenu.

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. De leverings-URL moet de interne naam van het doelformulier bevatten, bijvoorbeeld:

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   Wanneer de gebruiker **[!UICONTROL Approve]** knoop klikt, vorm **APP22** wordt getoond.

## Een koppeling invoegen naar een andere pagina van het formulier {#inserting-a-link-to-another-page-of-the-form}

U kunt koppelingen naar andere pagina&#39;s van het formulier invoegen. Om dit te doen, voeg een **[!UICONTROL Link]** type statisch element aan de pagina toe. Raadpleeg [Een koppeling invoegen](../../web/using/static-elements-in-a-web-form.md#inserting-a-link) voor meer informatie.

## Voorwaardelijke paginaweergave {#conditional-page-display}

### Weergeven op basis van antwoorden {#display-based-on-responses}

Met het vak **[!UICONTROL Test]** kunt u de volgorde van pagina&#39;s in een formulier bepalen. Hiermee kunt u verschillende vertakkingslijnen definiëren, afhankelijk van de testresultaten. Hierdoor kunt u verschillende pagina&#39;s weergeven, afhankelijk van de antwoorden van gebruikers.

U kunt bijvoorbeeld een andere pagina weergeven voor klanten die al online bestellingen hebben geplaatst, en een andere pagina voor klanten die meer dan tien bestellingen hebben geplaatst. Hiervoor voegt u op de eerste pagina van het formulier een invoerveld **[!UICONTROL Number]** in waarmee de gebruiker kan aangeven hoeveel bestellingen hij of zij heeft geplaatst.

![](assets/s_ncs_admin_survey_test_ex0.png)

U kunt deze informatie opslaan in een veld van de database of een lokale variabele gebruiken.

>[!NOTE]
>
>De opslagmodi worden beschreven in [Opslagvelden voor reacties](../../web/using/web-forms-answers.md#response-storage-fields).

In ons voorbeeld, willen wij een variabele gebruiken:

![](assets/s_ncs_admin_survey_test_ex1.png)

Voeg in het diagram van het formulier een testvak in om de voorwaarden te definiëren. Voor elke voorwaarde, zal een nieuwe tak bij de output van de testdoos worden toegevoegd.

![](assets/s_ncs_admin_survey_test_ex2.png)

Selecteer de optie **[!UICONTROL Activate the default branching]** om een overgang toe te voegen voor gevallen waarin geen van de voorwaarden waar is. Deze optie is niet nodig als elk mogelijk geval onder de vastgestelde voorwaarden valt.

Definieer vervolgens de volgorde van de pagina wanneer een van de voorwaarden waar is, bijvoorbeeld:

![](assets/s_ncs_admin_survey_test_ex3.png)

### Weergeven op basis van parameters {#display-based-on-parameters}

U kunt de pagina ook personaliseren die volgens de initialisatieparameters van de vorm van het Web of volgens de waarden in het gegevensbestand wordt opgeslagen. Zie [Formulier-URL-parameters](../../web/using/defining-web-forms-properties.md#form-url-parameters).

## Scripts {#adding-scripts} toevoegen

Met het object **[!UICONTROL Script]** kunt u een JavaScript-script rechtstreeks invoeren, bijvoorbeeld om de waarde van een veld te wijzigen, gegevens op te halen uit de database of een Adobe Campaign API aan te roepen.

## De eindpagina {#personalizing-the-end-page} aanpassen

U moet een eindpagina aan het eind van het diagram plaatsen. De eindpagina wordt weergegeven wanneer de gebruiker op de knop **[!UICONTROL Approve]** in het webformulier klikt.

Als u deze pagina wilt aanpassen, dubbelklikt u op **[!UICONTROL End]** en voert u de inhoud van de pagina in de centrale editor in.

![](assets/s_ncs_admin_survey_end_page_edit.png)

* U kunt bestaande HTML-inhoud kopiëren en plakken. Klik hiertoe op **[!UICONTROL Display source code]** en voeg de HTML-code in.
* U kunt een externe URL gebruiken; Hiervoor selecteert u de desbetreffende optie en voert u de URL in van de pagina die u wilt weergeven.

