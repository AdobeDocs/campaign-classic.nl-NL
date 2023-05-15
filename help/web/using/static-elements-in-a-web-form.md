---
product: campaign
title: Statische elementen in een webformulier
description: Statische elementen in een webformulier
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Forms
exl-id: 364d90af-4b18-4104-8b6a-be80cfde3b0b
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 3%

---

# Statische elementen in een webformulier{#static-elements-in-a-web-form}



U kunt elementen opnemen waarmee de gebruiker geen interactie heeft op de pagina&#39;s van het formulier. Dit zijn statische elementen, zoals afbeeldingen, HTML-inhoud, een horizontale balk of een hypertekstkoppeling. Deze elementen worden gemaakt met de eerste knop op de werkbalk, door **[!UICONTROL Static elements]**.

![](assets/s_ncs_admin_survey_add_static_element.png)

De volgende veldtypen zijn beschikbaar:

* Waarde gebaseerd op eerder gegeven antwoorden (in de context van het formulier) of op de database.
* Hypertext link, HTML, horizontale balk. Zie [HTML-inhoud invoegen](#inserting-html-content).
* Afbeelding opgeslagen in de bronbibliotheek of op een server die toegankelijk is voor gebruikers. Zie [Afbeeldingen invoegen](#inserting-images).
* Script wordt uitgevoerd aan de clientzijde en/of serverzijde. Deze moet in JavaScript zijn geschreven en compatibel zijn met de meeste browsers om een correcte uitvoering op de client te garanderen.

   >[!NOTE]
   >
   >Aan de serverzijde kan het script de functies gebruiken die zijn gedefinieerd in [JSAPI-documentatie voor campagne](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=nl).

## HTML-inhoud invoegen {#inserting-html-content}

U kunt HTML-inhoud opnemen in een formulierpagina: hypertextkoppelingen, afbeeldingen, opgemaakte alinea&#39;s, video&#39;s, enzovoort.

Met de HTML-editor kunt u de inhoud invoeren die u in de formulierpagina wilt invoegen. Als u de editor wilt openen, klikt u op **[!UICONTROL Static elements]** > **[!UICONTROL HTML]** .

U kunt de inhoud rechtstreeks invoeren en opmaken of het venster met de broncode weergeven om deze in externe inhoud te plakken. Als u wilt overschakelen naar de modus &quot;broncode&quot;, klikt u op het eerste pictogram op de werkbalk:

![](assets/s_ncs_admin_survey_html_editor.png)

Om een gegevensbestandgebied op te nemen, gebruik de verpersoonlijkingsknoop.

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>De tekenreeksen die u opgeeft in de HTML-editor worden alleen vertaald als ze zijn gedefinieerd in het dialoogvenster **[!UICONTROL Texts]** subtab. Anders worden ze niet verzameld. Raadpleeg voor meer informatie hierover [Een webformulier vertalen](translating-a-web-form.md).

### Een koppeling invoegen {#inserting-a-link}

Vul de velden in het bewerkingsvenster in, zoals in het volgende voorbeeld wordt getoond:

Ga naar **[!UICONTROL Static elements]** > **[!UICONTROL Link]**.

![](assets/s_ncs_admin_survey_add_link.png)

* De **[!UICONTROL Label]** Dit is de inhoud van de hypertekstkoppeling zoals deze wordt weergegeven op de formulierpagina.
* De **[!UICONTROL URL]** het gewenste adres is, bijvoorbeeld: [https://www.adobe.com](https://www.adobe.com) voor een website, of [info@adobe.com](mailto:info@adobe.com) om een bericht te verzenden.
* De **[!UICONTROL Window]** kunt u in het geval van een site de weergavemodus voor de koppeling selecteren. U kunt de koppeling openen in een nieuw venster, in het huidige venster of in een ander venster.
* U kunt een ToolTip toevoegen, zoals hieronder getoond:

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* U kunt de koppeling weergeven als een knop of als een afbeelding. Selecteer hiertoe het weergavetype in het dialoogvenster **[!UICONTROL Type]** veld.

### Typen koppelingen {#types-of-links}

De koppelingen zijn standaard gekoppeld aan een actie van het type URL, zodat een doeladres van de koppeling kan worden ingevoerd in het veld URL.

![](assets/s_ncs_admin_survey_link_url.png)

U kunt andere acties voor de koppeling definiëren, zodat de gebruiker op de koppeling kan klikken om het volgende te doen:

* De pagina vernieuwen

   Selecteer hiervoor de optie **[!UICONTROL Refresh page]** in de vervolgkeuzelijst van het dialoogvenster **[!UICONTROL Action]** veld.

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* Volgende/vorige pagina weergeven

   Selecteer hiervoor de optie **[!UICONTROL Next page]** of **[!UICONTROL Previous page]** in de vervolgkeuzelijst van het dialoogvenster **[!UICONTROL Action]** veld.

   ![](assets/s_ncs_admin_survey_link_next.png)

   U kunt de **[!UICONTROL Next]** en/of **[!UICONTROL Back]** knoppen als deze moeten worden vervangen door een koppeling. Zie dit [page](defining-web-forms-page-sequencing.md).

   De koppeling vervangt de koppeling **[!UICONTROL Next]** die standaard wordt gebruikt.

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* Een andere pagina weergeven

   De **[!UICONTROL Enable a transition]** Hiermee kunt u een specifieke pagina weergeven die is gekoppeld aan de uitgaande overgang die is geselecteerd in het dialoogvenster **[!UICONTROL Transition]** veld.

   ![](assets/s_ncs_admin_survey_link_viral.png)

   Een pagina heeft standaard maar één uitvoerovergang. Als u nieuwe overgangen wilt maken, selecteert u de pagina en klikt u op de knop **[!UICONTROL Add]** in de **[!UICONTROL Output transitions]** , zoals hieronder weergegeven:

   ![](assets/s_ncs_admin_survey_add_transition.png)

   In het diagram ziet deze toevoeging er als volgt uit:

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >Voor meer op pagina die in een vorm van het Web opeenvolgen, verwijs naar [Opeenvolging van webformulierpagina&#39;s definiëren](defining-web-forms-page-sequencing.md).

### HTML-inhoud aanpassen {#personalizing-html-content}

U kunt de HTML-inhoud van een formulierpagina aanpassen met gegevens die op een vorige pagina zijn opgenomen. U kunt bijvoorbeeld een webformulier voor autoverzekering maken waarvan u op de eerste pagina contactgegevens en het merk van de auto kunt opgeven.

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

Gebruik personalisatievelden om de gebruikersnaam en het geselecteerde merk opnieuw op de volgende pagina te injecteren. De syntaxis die moet worden gebruikt, is afhankelijk van de gegevensopslagmodus. Raadpleeg voor meer informatie hierover [Gezamelde gegevens gebruiken](web-forms-answers.md#using-collected-information).

>[!NOTE]
>
>Om veiligheidsredenen is de waarde die in het dialoogvenster **`<%=`** formule wordt vervangen door beschermde karakters.

In ons voorbeeld, worden de voornaam en de familienaam van de ontvanger opgeslagen in een gebied van het gegevensbestand, terwijl het merk van hun auto in een variabele wordt opgeslagen. De syntaxis van het bericht op bladzijde 2 is als volgt:

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

Dit levert het volgende resultaat op:

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### Tekstvariabelen gebruiken {#using-text-variables}

De **[!UICONTROL Text]** kunt u met de volgende syntaxis variabele velden maken die in de HTML tussen de tekens &lt;%= en %> kunnen worden gebruikt: **$(IDENTIFIER)**.

Gebruik deze methode om uw tekenreeksen eenvoudig te lokaliseren. Zie [Een webformulier vertalen](translating-a-web-form.md)

U kunt bijvoorbeeld een **Contact** veld waarmee u de tekenreeks &quot;Date of last contact:&quot; kunt weergeven voor de inhoud van de HTML. Volg de onderstaande stappen om dit te doen:

1. Klik op de knop **[!UICONTROL Text]** van de tekst HTML.
1. Klik op de knop **[!UICONTROL Add]** pictogram.
1. In de **[!UICONTROL Identifier]** kolom, voert u de naam van de variabele in
1. In de **[!UICONTROL Text]** Voer de standaardwaarde in.

   ![](assets/s_ncs_admin_survey_html_text.png)

1. Voeg deze tekstvariabele in de HTML-inhoud in via de **&lt;%= $(Contact) %>** syntaxis.

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >Als u deze tekens invoert in de HTML editor, wordt **&lt;** en **>** de velden worden vervangen door de escapetekens. In dit geval moet u de broncode corrigeren door op de knop **[!UICONTROL Display source code]** pictogram van de HTML-teksteditor.

1. Open de **[!UICONTROL Preview]** label van het formulier om de waarde weer te geven die in de HTML is ingevoerd:

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

In deze modus kunt u de tekst van webformulieren slechts eenmaal definiëren en vertalingen beheren met het geïntegreerde vertaalgereedschap. Raadpleeg voor meer informatie hierover [Een webformulier vertalen](translating-a-web-form.md).

## Afbeeldingen invoegen {#inserting-images}

Afbeeldingen die u in formulieren wilt opnemen, moeten worden opgeslagen op een server die van buitenaf toegankelijk is.

Selecteer **[!UICONTROL Static elements]** > **[!UICONTROL Image]** -menu.

Selecteer de bron van de afbeelding die u wilt invoegen: het kan uit de openbare middelbibliotheek komen of op een externe server worden opgeslagen die van buiten toegankelijk is.

![](assets/s_ncs_admin_survey_add_img.png)

Als dit een afbeelding uit de bibliotheek is, selecteert u deze in de keuzelijst met invoervak van het veld. Als het in een extern dossier wordt gevestigd, ga de toegangspad in. Het label wordt weergegeven door de cursor boven de afbeelding te plaatsen (valt samen met een ALT-veld in HTML) of wanneer de afbeelding niet wordt weergegeven.

De afbeelding kan worden weergegeven in het centrale gedeelte van de editor.
