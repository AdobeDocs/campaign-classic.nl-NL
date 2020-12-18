---
solution: Campaign Classic
product: campaign
title: Statische elementen in een webformulier
description: Statische elementen in een webformulier
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '1269'
ht-degree: 4%

---


# Statische elementen in een webformulier{#static-elements-in-a-web-form}

U kunt elementen opnemen waarmee de gebruiker geen interactie heeft op de pagina&#39;s van het formulier. Dit zijn statische elementen, zoals afbeeldingen, HTML-inhoud, een horizontale balk of een hypertekstkoppeling. Deze elementen worden gemaakt met de eerste knop op de werkbalk door **[!UICONTROL Static elements]** te selecteren.

![](assets/s_ncs_admin_survey_add_static_element.png)

De volgende veldtypen zijn beschikbaar:

* Waarde gebaseerd op eerder gegeven antwoorden (in de context van het formulier) of op de database.
* Hypertext link, HTML, horizontal bar. Zie [HTML-inhoud invoegen](#inserting-html-content).
* Afbeelding opgeslagen in de bronbibliotheek of op een server die toegankelijk is voor gebruikers. Zie [Afbeeldingen invoegen](#inserting-images).
* Script wordt uitgevoerd aan de clientzijde en/of serverzijde. Deze moet in JavaScript zijn geschreven en compatibel zijn met de meeste browsers om een correcte uitvoering op de client te garanderen.

   >[!NOTE]
   >
   >Aan de serverzijde kan het script de functies gebruiken die zijn gedefinieerd in [Campagne JSAPI-documentatie](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

## HTML-inhoud {#inserting-html-content} invoegen

U kunt HTML-inhoud opnemen in een formulierpagina: hypertextkoppelingen, afbeeldingen, opgemaakte alinea&#39;s, video- of Flash-objecten, enz.

Met de HTML-editor kunt u de inhoud invoeren die u in de formulierpagina wilt invoegen. Klik op **[!UICONTROL Static elements]** > **[!UICONTROL HTML]** om de editor te openen.

U kunt de inhoud rechtstreeks invoeren en opmaken of het venster met de broncode weergeven om deze in externe inhoud te plakken. Als u wilt overschakelen naar de modus &quot;broncode&quot;, klikt u op het eerste pictogram op de werkbalk:

![](assets/s_ncs_admin_survey_html_editor.png)

Om een gegevensbestandgebied op te nemen, gebruik de verpersoonlijkingsknoop.

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>De tekenreeksen die in de HTML-editor zijn ingevoerd, worden alleen vertaald als ze op het subtabblad **[!UICONTROL Texts]** zijn gedefinieerd. Anders worden ze niet verzameld. Raadpleeg [Een webformulier vertalen](../../web/using/translating-a-web-form.md) voor meer informatie.

### Een koppeling {#inserting-a-link} invoegen

Vul de velden in het bewerkingsvenster in, zoals in het volgende voorbeeld wordt getoond:

Als u een hypertekstkoppeling wilt toevoegen, gaat u naar **[!UICONTROL Static elements]** > **[!UICONTROL Link]**.

![](assets/s_ncs_admin_survey_add_link.png)

* De **[!UICONTROL Label]** is de inhoud van de hypertekstkoppeling zoals deze wordt weergegeven op de formulierpagina.
* De **[!UICONTROL URL]** is het gewenste adres, bijvoorbeeld: [https://www.adobe.com](https://www.adobe.com) voor een website of [info@adobe.com](mailto:info@adobe.com) om een bericht te verzenden.
* In het veld **[!UICONTROL Window]** kunt u de weergavemodus voor de koppeling selecteren in het geval van een site. U kunt de koppeling openen in een nieuw venster, in het huidige venster of in een ander venster.
* U kunt een ToolTip toevoegen, zoals hieronder getoond:

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* U kunt de koppeling weergeven als een knop of als een afbeelding. Selecteer hiertoe het weergavetype in het veld **[!UICONTROL Type]**.

### Typen koppelingen {#types-of-links}

De koppelingen zijn standaard gekoppeld aan een actie van het type URL, zodat een doeladres van de koppeling kan worden ingevoerd in het veld URL.

![](assets/s_ncs_admin_survey_link_url.png)

U kunt andere acties voor de koppeling definiëren, zodat de gebruiker op de koppeling kan klikken om het volgende te doen:

* De pagina vernieuwen

   Selecteer hiertoe de optie **[!UICONTROL Refresh page]** in de vervolgkeuzelijst van het veld **[!UICONTROL Action]**.

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* Volgende/vorige pagina weergeven

   Om dit te doen, selecteer **[!UICONTROL Next page]** of **[!UICONTROL Previous page]** optie in de drop-down doos van het **[!UICONTROL Action]** gebied.

   ![](assets/s_ncs_admin_survey_link_next.png)

   U kunt de **[!UICONTROL Next]** en/of **[!UICONTROL Back]** knopen verbergen als zij door een verbinding moeten worden vervangen. Zie deze [pagina](../../web/using/defining-web-forms-page-sequencing.md).

   De koppeling vervangt de **[!UICONTROL Next]**-knop die standaard wordt gebruikt.

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* Een andere pagina weergeven

   Met de optie **[!UICONTROL Enable a transition]** kunt u een specifieke pagina weergeven die is gekoppeld aan de uitgaande overgang die is geselecteerd in het veld **[!UICONTROL Transition]**.

   ![](assets/s_ncs_admin_survey_link_viral.png)

   Een pagina heeft standaard maar één uitvoerovergang. Als u nieuwe overgangen wilt maken, selecteert u de pagina en klikt u op de knop **[!UICONTROL Add]** in de sectie **[!UICONTROL Output transitions]**, zoals hieronder wordt getoond:

   ![](assets/s_ncs_admin_survey_add_transition.png)

   In het diagram ziet deze toevoeging er als volgt uit:

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >Voor meer op pagina die in een vorm van het Web in volgorde plaatsen, verwijs naar [het bepalen van Web form pagina het rangschikken](../../web/using/defining-web-forms-page-sequencing.md).

* Velden van het formulier vooraf laden met gegevens uit het Facebook-profiel

   >[!CAUTION]
   >
   >Deze functie is alleen beschikbaar als u de toepassing **[!UICONTROL Social Marketing]** hebt geïnstalleerd. Als u deze optie wilt gebruiken, moet u een Facebook-toepassing maken samen met een externe account van het type **[!UICONTROL Facebook Connect]**. Raadpleeg [deze pagina](../../social/using/creating-a-facebook-application.md#configuring-external-accounts) voor meer informatie.

   Met de optie **[!UICONTROL Preload with Facebook]** kunt u een knop in een formulier invoegen om velden vooraf te laden met Facebook-profielgegevens.

   ![](assets/web_social_webapp_037.png)

   Wanneer een gebruiker op de knop **[!UICONTROL Fill in automatically]** klikt, wordt het venster met bevoegdheden op Facebook geopend.

   ![](assets/web_social_webapp_029.png)

   >[!NOTE]
   >
   >Het is mogelijk om de lijst met uitgebreide rechten te wijzigen wanneer u de externe account configureert. Als u geen uitgebreide rechten opgeeft, stuurt Facebook standaard de basisprofielgegevens door.\
   >Klik hier als u de lijst met uitgebreide rechten en de bijbehorende syntaxis wilt weergeven: [https://developers.facebook.com/docs/reference/api/permissions/](https://developers.facebook.com/docs/reference/api/permissions/)

   Als de gebruiker ermee instemt om zijn gegevens te delen, worden de velden van het formulier vooraf geladen.

   ![](assets/web_social_webapp_030.png)

Voor dit gebruiksgeval, hebben wij een toepassing van het Web gecreeerd die uit de volgende elementen wordt samengesteld:

* een pagina met het formulier
* een **[!UICONTROL Record]**-activiteit
* een **[!UICONTROL End]** activiteit

![](assets/social_webapp_031.png)

Voer de volgende stappen uit om een knop voor vooraf laden toe te voegen:

1. Maak een formulier.

   ![](assets/social_webapp_032.png)

1. Ga naar hetzelfde niveau als de velden in het formulier en voeg een koppeling toe.

   ![](assets/social_webapp_033.png)

1. Voer het label in en selecteer het type **[!UICONTROL Button]**.

   ![](assets/social_webapp_034.png)

1. Ga naar het **[!UICONTROL Action]** gebied en selecteer **[!UICONTROL Preload with Facebook]**.

   ![](assets/social_webapp_035.png)

1. Ga naar het **[!UICONTROL Application]** gebied en selecteer **[!UICONTROL Facebook Connect]** type externe rekening eerder gecreeerd. Raadpleeg [deze pagina](../../social/using/creating-a-facebook-application.md#configuring-external-accounts) voor meer informatie.

   ![](assets/social_webapp_036.png)

### HTML-inhoud aanpassen {#personalizing-html-content}

U kunt de HTML-inhoud van een formulierpagina aanpassen met gegevens die op een vorige pagina zijn opgenomen. U kunt bijvoorbeeld een webformulier voor autoverzekering maken waarvan u op de eerste pagina contactgegevens en het merk van de auto kunt opgeven.

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

Gebruik personalisatievelden om de gebruikersnaam en het geselecteerde merk opnieuw op de volgende pagina te injecteren. De syntaxis die moet worden gebruikt, is afhankelijk van de gegevensopslagmodus. Voor meer op dit, verwijs naar [Gebruikend verzamelde informatie](../../web/using/web-forms-answers.md#using-collected-information).

>[!NOTE]
>
>Om veiligheidsredenen wordt de waarde die in de **`<%=`**-formule is ingevoerd, vervangen door escape-tekens.

In ons voorbeeld, worden de voornaam en de familienaam van de ontvanger opgeslagen in een gebied van het gegevensbestand, terwijl het merk van hun auto in een variabele wordt opgeslagen. De syntaxis van het bericht op bladzijde 2 is als volgt:

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

Dit levert het volgende resultaat op:

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### Tekstvariabelen {#using-text-variables} gebruiken

Op het tabblad **[!UICONTROL Text]** kunt u met de volgende syntaxis variabele velden maken die in de HTML tussen de tekens &lt;%= en %> kunnen worden gebruikt: **$(IDENTIFIER)**.

Gebruik deze methode om uw tekenreeksen eenvoudig te lokaliseren. Zie [Een webformulier vertalen](../../web/using/translating-a-web-form.md)

U kunt bijvoorbeeld een veld **Contact** maken waarmee u de tekenreeks &quot;Date of last contact:&quot; kunt weergeven voor de HTML-inhoud. Volg de onderstaande stappen om dit te doen:

1. Klik op het tabblad **[!UICONTROL Text]** van de HTML-tekst.
1. Klik op het pictogram **[!UICONTROL Add]**.
1. Voer in de kolom **[!UICONTROL Identifier]** de naam van de variabele in
1. Voer in de kolom **[!UICONTROL Text]** de standaardwaarde in.

   ![](assets/s_ncs_admin_survey_html_text.png)

1. Voeg deze tekstvariabele in de HTML-inhoud in via de syntaxis **&lt;%= $(Contact) %>**.

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >Als u deze tekens in de HTML-editor invoert, worden de velden **&lt;** en **** vervangen door de beschermde tekens. In dit geval moet u de broncode corrigeren door op het pictogram **[!UICONTROL Display source code]** van de HTML-teksteditor te klikken.

1. Open het label **[!UICONTROL Preview]** van het formulier om de waarde weer te geven die is ingevoerd in de HTML:

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

In deze modus kunt u de tekst van webformulieren slechts eenmaal definiëren en vertalingen beheren met het geïntegreerde vertaalgereedschap. Raadpleeg [Een webformulier vertalen](../../web/using/translating-a-web-form.md) voor meer informatie.

## Afbeeldingen {#inserting-images} invoegen

Afbeeldingen die u in formulieren wilt opnemen, moeten worden opgeslagen op een server die van buitenaf toegankelijk is.

Selecteer het menu **[!UICONTROL Static elements]** > **[!UICONTROL Image]**.

Selecteer de bron van de afbeelding die u wilt invoegen: het kan uit de openbare middelbibliotheek komen of op een externe server worden opgeslagen die van buiten toegankelijk is.

![](assets/s_ncs_admin_survey_add_img.png)

Als dit een afbeelding uit de bibliotheek is, selecteert u deze in de keuzelijst met invoervak van het veld. Als het in een extern dossier wordt gevestigd, ga de toegangspad in. Het label wordt weergegeven door de cursor boven de afbeelding te plaatsen (valt samen met een ALT-veld in HTML) of wanneer de afbeelding niet wordt weergegeven.

De afbeelding kan worden weergegeven in het centrale gedeelte van de editor.
