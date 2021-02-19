---
solution: Campaign Classic
product: campaign
title: Velden toevoegen aan een webformulier
description: Velden toevoegen aan een webformulier
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '2457'
ht-degree: 1%

---


# Velden toevoegen aan een webformulier{#adding-fields-to-a-web-form}

In een webformulier kunnen gebruikers in velden informatie invoeren en opties selecteren. Webformulieren kunnen invoervelden, selectievelden, statische en geavanceerde inhoud (bijschriften, abonnementen, enz.) bieden.

Wanneer u velden toevoegt met de wizard, wordt het veldtype automatisch gedetecteerd op basis van het geselecteerde veld of de opslagvariabele. U kunt het uitgeven gebruikend **[!UICONTROL Type]** drop-down doos op **[!UICONTROL General]** tabel.

![](assets/s_ncs_admin_webform_change_type.png)

Selecteer het type veld dat u wilt toevoegen wanneer u de knoppen op de werkbalk gebruikt.

De volgende veldtypen zijn beschikbaar:

* Tekst/nummerinvoer. Zie [Invoervelden toevoegen](#adding-input-fields).
* Selectie vervolgkeuzelijst. Zie [Vervolgkeuzelijsten toevoegen](#adding-drop-down-lists).
* Meerdere keuzen via selectievakjes. Zie [Selectievakjes toevoegen](#adding-checkboxes).
* Exclusieve selectie via keuzerondjes. Zie [Keuzerondjes toevoegen](#adding-radio-buttons).
* Stem in een optieraster. Zie [Rasters toevoegen](#adding-grids).
* Getallen en datums. Zie [Datums en getallen toevoegen](#adding-dates-and-numbers).
* Abonnement/abonnement op een informatieservice. Zie [Selectievakjes voor abonnement](#subscription-checkboxes).
* Captcha-validatie. Zie [Een captcha invoegen](#inserting-a-captcha).
* Knop Downloaden. [Een bestand](#uploading-a-file) uploaden.
* De constante Verborgen. Zie [Een verborgen constante invoegen](#inserting-a-hidden-constant).

Geef de opslagmodus voor reacties op: een veld in de database bijwerken (alleen de laatst opgeslagen waarde wordt opgeslagen) of in een variabele opslaan (het antwoord wordt niet opgeslagen). Voor meer op dit, verwijs naar [De opslaggebieden van de Reactie](../../web/using/web-forms-answers.md#response-storage-fields).

>[!NOTE]
>
>Standaard wordt het veld onder aan de huidige structuur ingevoegd. Gebruik de pijlen in de werkbalk om deze omhoog of omlaag te verplaatsen.

## Wizard Veld maken {#field-creation-wizard}

Voor elke pagina van het formulier kunt u een veld toevoegen met de eerste knop op de werkbalk. Ga hiertoe naar het menu **[!UICONTROL Add using the wizard]**.

![](assets/s_ncs_admin_survey_add_field_menu.png)

Selecteer het type veld dat u wilt maken: U kunt een veld toevoegen aan de database of een variabele of een groep velden importeren die in een ander formulier zijn gemaakt en in een container zijn verzameld.

Klik **[!UICONTROL Next]** en selecteer het opslaggebied of de variabele, of de container u wilt invoeren.

![](assets/s_ncs_admin_webform_wz_confirm_db.png)

Klik **[!UICONTROL Finish]** om het geselecteerde gebied in de pagina op te nemen.

![](assets/s_ncs_admin_webform_wz_insert_field.png)

## Invoervelden {#adding-input-fields} toevoegen

Als u een invoerveld wilt toevoegen, klikt u op de knop **[!UICONTROL Input control]** en kiest u het type veld dat u wilt toevoegen.

![](assets/s_ncs_admin_webform_select_field.png)

### Typen invoervelden {#types-of-input-fields}

U kunt vijf verschillende typen tekstvelden invoegen in een formulierpagina:

* **Tekst**: Hiermee kan de gebruiker een tekst op één regel invoeren.

   ![](assets/s_ncs_admin_survey_txt_ex.png)

* **Getal**: Hiermee kan de gebruiker een getal op één regel invoeren. Raadpleeg [Getallen toevoegen](#adding-numbers) voor meer informatie hierover.

   Wanneer de pagina is goedgekeurd, wordt de inhoud van het veld gecontroleerd om te controleren of de ingevoerde waarde compatibel is met het veld. Raadpleeg [Besturingsinstellingen definiëren](../../web/using/form-rendering.md#defining-control-settings) voor meer informatie hierover.

* **Wachtwoord**: Hiermee kan de gebruiker tekst op één regel invoeren. Tijdens tekstinvoer worden de tekens vervangen door punten:

   ![](assets/s_ncs_admin_survey_passwd_ex.png)

   >[!CAUTION]
   >
   >Wachtwoorden worden niet-gecodeerd opgeslagen in de database.

* **Tekst** met meerdere regels: Hiermee kan de gebruiker tekst op meerdere regels invoeren.

   ![](assets/s_ncs_admin_survey_txtmulti_ex.png)

   >[!CAUTION]
   >
   >Tekstvelden met meerdere regels zijn specifieke velden die regeleinden kunnen bevatten. Hun opslagruimte moet worden gekoppeld aan een veld dat is toegewezen aan een XML-element, niet aan een XML-kenmerk. Raadpleeg het hoofdstuk &quot;Schemaverwijzing&quot; in [deze sectie](../../configuration/using/about-schema-reference.md) voor meer informatie over de typen gegevens in schema&#39;s.
   >   
   >Als u de **Module van het Onderzoek** gebruikt, kunt u dit type van gebied in een gearchiveerd gebied opslaan dat automatisch aan het formaat zal aanpassen. Raadpleeg [deze sectie](../../web/using/about-surveys.md) voor meer informatie.

* **Verrijkte tekst** met meerdere regels: Hiermee kan de gebruiker tekst invoeren met een lay-out die wordt opgeslagen in HTML-indeling.

   ![](assets/s_ncs_admin_survey_txthtmli_ex.png)

   U kunt het type editor selecteren dat gebruikers wordt aangeboden. Hiervoor gebruikt u de vervolgkeuzelijst van het veld **[!UICONTROL HTML editor]** op het tabblad **[!UICONTROL Advanced]**.

   ![](assets/webapp_enrich_text_type.png)

   Het aantal weergegeven pictogrammen is afhankelijk van het type editor. Voor een **[!UICONTROL Advanced]** redacteur, zal het teruggeven als volgt zijn:

   ![](assets/webapp_enrich_text_max.png)

### Invoervelden {#configure-input-fields} configureren

Invoervelden worden allemaal geconfigureerd op basis van dezelfde modus, waarbij de volgende opties worden gebruikt:

![](assets/s_ncs_admin_survey_txt_param.png)

Op het tabblad **[!UICONTROL General]** kunt u de naam van het veld invoeren en er indien nodig een standaardwaarde aan toewijzen.

De antwoordopslagmodus kan worden gewijzigd via de koppeling **[!UICONTROL Edit storage...]**. Waarden kunnen worden opgeslagen in een bestaand veld van de database; of u kunt ervoor kiezen geen informatie in de database op te slaan (gebruik een lokale variabele).

>[!NOTE]
>
>Opslagmodi worden beschreven in [Opslagvelden voor reacties](../../web/using/web-forms-answers.md#response-storage-fields)

Op het tabblad **[!UICONTROL Advanced]** kunt u weergaveparameters voor het veld definiëren (positie van labels, uitlijning, enzovoort). Zie [Opmaak van webformulieren definiëren](../../web/using/defining-web-forms-layout.md).

## Vervolgkeuzelijsten {#adding-drop-down-lists} toevoegen

U kunt een vervolgkeuzelijst invoegen in een enquêtepagina. Hiermee kan de gebruiker een waarde selecteren uit de beschikbare waarden in een vervolgkeuzemenu.

![](assets/s_ncs_admin_survey_dropdown_sample.png)

Als u een vervolgkeuzelijst aan een formulierpagina wilt toevoegen, klikt u op de knop **[!UICONTROL Selection controls > Drop-down list]** op de werkbalk van de pagina-editor.

![](assets/s_ncs_admin_survey_create_dropdown.png)

Selecteer de antwoordopslagmodus en bevestig uw keuze.

Definieer de labels en waarden van de lijst in de onderste sectie van het tabblad **[!UICONTROL General]**. Als de informatie in een bestaand gebied van het gegevensbestand wordt opgeslagen en het een opsommingsgebied is, kunt u de waarden automatisch invullen door **[!UICONTROL Initialize the list of values from the database]**, zoals hieronder getoond te klikken:

![](assets/s_ncs_admin_survey_database_values.png)

>[!NOTE]
>
>Gebruik de pijlen rechts van de lijst met waarden om de volgorde te wijzigen.

Als de gegevens worden opgeslagen in een gekoppelde tabel, kunt u het veld selecteren waarin de waarden worden opgeslagen die in de lijst moeten worden voorgesteld. Als u bijvoorbeeld de lijst met landen selecteert, klikt u op **[!UICONTROL Initialize the list of values from the database...]** en selecteert u het gewenste veld.

![](assets/s_ncs_admin_survey_preload_values.png)

Klik vervolgens op de koppeling **[!UICONTROL Load]** om de waarden op te halen:

![](assets/s_ncs_admin_survey_load_button.png)

>[!CAUTION]
>
>Herhaal deze bewerking telkens wanneer de lijst wordt bijgewerkt om de aangeboden waarden te vernieuwen.

## Selectievakjes {#adding-checkboxes} toevoegen

Als de gebruiker een optie kan selecteren, moet u een selectievakje gebruiken.

![](assets/s_ncs_admin_survey_check_box.png)

Als u een selectievakje aan een formulier wilt toevoegen, klikt u op het pictogram **[!UICONTROL Selection controls > Checkbox...]** op de werkbalk van de pagina-editor.

Selecteer de antwoordopslagmodus en bevestig uw keuze.

Typ het label van het vak in het veld **[!UICONTROL Label]** van het tabblad **[!UICONTROL General]**.

![](assets/s_ncs_admin_survey_check_box_edit.png)

Met een selectievakje kunt u een waarde aan het opslagveld (of de waarde) toewijzen, afhankelijk van het feit of het vak is ingeschakeld. In de sectie **[!UICONTROL Values]** kunt u de waarde invoeren die moet worden toegewezen als het vak is ingeschakeld (in het veld **[!UICONTROL Value]**) en de waarde die moet worden toegewezen als dit niet is ingeschakeld (in het veld **[!UICONTROL Empty value]**). Deze waarden zijn afhankelijk van de indeling voor gegevensopslag.

Als het opslagveld (of de variabele) Booleaans is, wordt de waarde die moet worden toegewezen als het vak niet is ingeschakeld, automatisch afgetrokken. In dit geval wordt alleen het veld **[!UICONTROL Value if checked]** aangeboden, zoals hieronder wordt getoond:

![](assets/s_ncs_admin_survey_check_box_enum.png)

## Voorbeeld: Een waarde toewijzen aan een veld als een selectievakje {#example--assign-a-value-to-a-field-if-a-box-is-checked} is ingeschakeld

We willen een selectievakje in een formulier invoegen om een onderhoudsaanvraag te verzenden, zoals hieronder wordt weergegeven:

![](assets/s_ncs_admin_survey_check_box_ex.png)

De informatie wordt geüpload naar de database en naar een bestaand veld (in dit geval het veld **[!UICONTROL Comment]**):

![](assets/s_ncs_admin_survey_check_box_ex_list.png)

Als het selectievakje &quot;Onderhoud vereist&quot; is ingeschakeld, bevat de kolom **[!UICONTROL Comment]** &quot;Onderhoud vereist&quot;. Als de doos niet wordt gecontroleerd, zal de kolom &quot;Onderhoud niet vereist&quot;tonen. U bereikt dit resultaat door de volgende configuratie toe te passen op het selectievakje op de formulierpagina:

![](assets/s_ncs_admin_survey_check_box_ex_edit.png)

## Keuzerondjes {#adding-radio-buttons} toevoegen

Met keuzerondjes kunt u de gebruiker een aantal exclusieve opties bieden waaruit u kunt kiezen. Dit zijn verschillende waarden voor hetzelfde veld.

![](assets/s_ncs_admin_survey_radio_button.png)

U kunt keuzerondjes afzonderlijk maken (eenheidsknoppen) of via een keuzelijst met meerdere keuzerondjes, maar aangezien het doel van de keuzerondjes is een optie of een andere optie te selecteren, maken we altijd ten minste een paar keuzerondjes, nooit slechts één knop.

>[!CAUTION]
>
>Als u selectie verplicht wilt maken, moet u een keuzelijst met meerdere keuzes maken.

### Enkele knoppen toevoegen {#add-single-buttons}

Als u een keuzerondje aan een formulierpagina wilt toevoegen, gaat u naar het menu **[!UICONTROL Selection controls > Radio button]** op de werkbalk van de pagina-editor en kiest u een opslagmodus.

![](assets/s_ncs_admin_survey_radio_button_sample.png)

Keuzerondjes worden op dezelfde manier geconfigureerd als selectievakjes (zie [Selectievakjes toevoegen](#adding-checkboxes)). Er wordt echter geen waarde toegewezen als de optie niet is geselecteerd. Als u wilt dat verschillende knoppen onderling afhankelijk zijn, de andere automatisch deselecteert, moeten ze in hetzelfde veld worden opgeslagen. Als zij niet in het gegevensbestand worden opgeslagen, moet de zelfde lokale variabele voor tijdelijke opslag worden gebruikt. Zie [Opslagvelden voor reacties](../../web/using/web-forms-answers.md#response-storage-fields).

### Een lijst met knoppen {#add-a-list-of-buttons} toevoegen

Als u keuzerondjes wilt toevoegen via een lijst, gaat u naar het menu **[!UICONTROL Selection controls>Multiple choice]** op de werkbalk van de pagina-editor.

![](assets/s_ncs_admin_survey_radio_button_sample2.png)

Voeg zoveel keuzerondjes toe als er labels zijn. Het voordeel van deze functie is dat u waarden uit een bestaand veld kunt importeren (in het geval van een gespecificeerd veld) en dat de gebruiker één optie kan kiezen. De lay-out van knoppen is echter minder flexibel.

>[!NOTE]
>
>Webformulieren staan de selectie van verschillende waarden niet toe. Meerdere selecties kunnen alleen worden geactiveerd voor formulieren van het type **Beoordeling**. Raadpleeg [deze sectie](../../web/using/about-surveys.md) voor meer informatie.\
>Het is echter mogelijk om een **[!UICONTROL Multiple choice]** typeveld in een toepassing van het Web op te nemen; maar zonder toestemming voor de keuze van verschillende waarden: u kunt de aangeboden opties selecteren met behulp van keuzerondjes.

## Rasters {#adding-grids} toevoegen

Rasters worden gebruikt om stempagina&#39;s te ontwerpen in de toepassingen van het Web. Hier kunt u lijsten met keuzerondjes aanbieden voor het beantwoorden van enquêtes of het beoordelingstype Webformulieren, zoals hieronder wordt getoond:

![](assets/s_ncs_admin_survey_vote_param.png)

Als u dit type element in een formulier wilt gebruiken, maakt u een eenvoudig raster en voegt u een lijn toe voor elk element dat u wilt beoordelen.

![](assets/s_ncs_admin_survey_vote_sample.png)

Het aantal keuzerondjes in elke regel van het raster komt overeen met het aantal waarden dat in het eenvoudige raster is gedefinieerd.

![](assets/s_ncs_admin_survey_vote_ex.png)

Per rasterlijn kan slechts één optie worden geselecteerd.

>[!NOTE]
>
>In ons voorbeeld is het label van het raster verborgen. Hiervoor gaat u naar het tabblad **[!UICONTROL Advanced]** en wordt de weergave **[!UICONTROL Label position]** gedefinieerd als **[!UICONTROL Hidden]**. Zie [De positie van labels definiëren](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels).

## Datums en getallen {#adding-dates-and-numbers} toevoegen

De inhoud van de formuliervelden kan worden opgemaakt op basis van de gegevens die in de database zijn opgeslagen of om aan een bepaalde eis te voldoen. U kunt geschikte velden maken voor het invoeren van getallen en datums.

### Datums {#adding-dates} toevoegen

![](assets/s_ncs_admin_survey_date_calendar.png)

Als u wilt toestaan dat de gebruiker een datum op een formulierpagina invoert, voegt u een invoerveld toe en selecteert u het type **[!UICONTROL Date...]**.

Voer een label in voor het veld en configureer de gegevensopslagmodus.

![](assets/s_ncs_admin_survey_date_edit.png)

In de onderste sectie van het venster kunt u de datum- en tijdnotaties selecteren voor de waarden die in dit veld zijn opgeslagen.

![](assets/s_ncs_admin_survey_date_edit_values.png)

U kunt er ook voor kiezen om de datum (of tijd) niet weer te geven.

Datums kunnen worden geselecteerd via een kalender of een vervolgkeuzelijst. U kunt ze ook rechtstreeks in het veld invoeren, maar ze moeten overeenkomen met de indeling die in het bovenstaande scherm is opgegeven.

>[!NOTE]
>
>De datums die in formulieren worden gebruikt, worden standaard ingevoerd via een kalender. Controleer voor meertalige formulieren of de kalenders beschikbaar zijn in alle gebruikte talen. Zie [Een webformulier vertalen](../../web/using/translating-a-web-form.md).

In sommige gevallen (bijvoorbeeld bij het invoeren van geboortedata) kan het echter gemakkelijker zijn om vervolgkeuzelijsten te gebruiken.

![](assets/s_ncs_admin_survey_date_list_select.png)

Klik hiertoe op de tab **[!UICONTROL Advanced]** en kies de invoermodus met **[!UICONTROL Drop-down lists]**.

![](assets/s_ncs_admin_survey_date_selection.png)

Vervolgens kunt u limieten instellen voor de waarden die worden aangeboden in de lijst.

![](assets/s_ncs_admin_survey_date_first_last_y.png)

### Getallen {#adding-numbers} toevoegen

U kunt geschikte velden maken voor het invoeren van getallen.

![](assets/s_ncs_admin_survey_number.png)

In een numeriek veld kan de gebruiker alleen getallen invoeren. De controle van de ingang wordt automatisch toegepast wanneer de pagina wordt goedgekeurd.

Afhankelijk van het veld waarin gegevens in de database worden opgeslagen, kunnen speciale opmaak of bepaalde beperkingen worden toegepast. U kunt ook maximum- en minimumwaarden opgeven. Dit type veld is als volgt geconfigureerd:

![](assets/s_ncs_admin_survey_number_edit.png)

De standaardwaarde is de waarde die in het veld wordt weergegeven wanneer het formulier wordt gepubliceerd. Deze kan door de gebruiker worden gecorrigeerd.

U kunt een voor- en/of achtervoegsel toevoegen aan het numerieke veld via het tabblad **[!UICONTROL Advanced]**, zoals hieronder wordt weergegeven:

![](assets/s_ncs_admin_survey_number_ex_conf.png)

In de vorm zal de rendering als volgt zijn:

![](assets/s_ncs_admin_survey_number_ex.png)

## Selectievakjes voor abonnement {#subscription-checkboxes}

U kunt besturingselementen toevoegen waarmee gebruikers zich kunnen abonneren op of zich kunnen afmelden bij een of meer informatiediensten (nieuwsbrieven, waarschuwingen, realtime meldingen, enz.). Om zich in te schrijven, controleert de gebruiker de overeenkomstige dienst.

Als u een selectievakje voor een abonnement wilt maken, klikt u op **[!UICONTROL Advanced controls>Subscription]**.

![](assets/s_ncs_admin_survey_subscription_edit.png)

Geef het label voor het selectievakje op en selecteer de desbetreffende informatieservice in het vervolgkeuzemenu **[!UICONTROL Service]**.

>[!NOTE]
>
>De diensten van de informatie zijn gedetailleerd in [deze pagina](../../delivery/using/managing-subscriptions.md).

De gebruiker abonneert zich op de dienst door de relevante optie te controleren.

![](assets/s_ncs_admin_survey_subscribe.png)

>[!CAUTION]
>
>Als de gebruiker al is geabonneerd op een informatieservice en het vak dat aan deze service is gekoppeld, niet is ingeschakeld wanneer hij of zij het formulier goedkeurt, wordt het abonnement opgezegd.

Voorbeelden van abonnementen en verwijzingen zijn beschikbaar in [deze sectie](../../web/using/about-surveys.md).

## Een captcha {#inserting-a-captcha} invoegen

Het doel van **captcha** tests is frauduleus gebruik van uw vormen van het Web te verhinderen.

>[!CAUTION]
>
>Als uw formulier meerdere pagina&#39;s bevat, moet Captcha altijd op de laatste pagina worden geplaatst, vlak voor het opslagvak, om te voorkomen dat de beveiligingsmaatregelen worden omzeild.

Als u een Captcha in een formulier wilt invoegen, klikt u op de eerste knop op de werkbalk en selecteert u **[!UICONTROL Advanced controls>Captcha]**.

![](assets/s_ncs_admin_survey_add_captcha.png)

Voer het label van het veld in. Dit label wordt vóór het weergavegebied van Captcha weergegeven. U kunt de positie van dit label wijzigen op het tabblad **[!UICONTROL Advanced]**.

![](assets/s_ncs_admin_survey_captcha_adv.png)

>[!NOTE]
>
>Voor **[!UICONTROL captcha]** typecontroles, is er geen behoefte om een opslaggebied of een variabele te wijzen.

Captcha wordt opgenomen in de pagina met een inputgebied dat onder visueel wordt geplaatst. Deze twee elementen zijn onscheidbaar en worden voor de paginalay-out als één item beschouwd (ze nemen één cel in beslag).

![](assets/s_ncs_admin_survey_captcha_sample.png)

Wanneer de pagina wordt bevestigd, wordt het invoerveld rood weergegeven als de inhoud van Captcha niet correct is ingevoerd.

![](assets/s_ncs_admin_survey_captcha_error.png)

U kunt een foutbericht maken om weer te geven. Hiervoor gebruikt u de koppeling **[!UICONTROL Personalize the message]** op het tabblad **[!UICONTROL General]**.

![](assets/s_ncs_admin_survey_captcha_error_msg.png)

>[!NOTE]
>
>Hoofdletters zijn altijd 8 tekens lang. U kunt deze waarde niet wijzigen.

## Een bestand {#uploading-a-file} uploaden

U kunt een uploadveld toevoegen aan een pagina. Deze functionaliteit kan bijvoorbeeld nuttig zijn voor het delen van intranetbestanden.

![](assets/s_ncs_admin_survey_download_file.png)

Als u een uploadveld wilt invoegen in een formulierpagina, selecteert u het menu **[!UICONTROL Advanced controls > File...]** op de werkbalk van de pagina-editor.

Standaard worden de geüploade bestanden opgeslagen in bronbestanden die toegankelijk zijn via het menu **[!UICONTROL Resources > Online > Public resources]**. U kunt een script gebruiken om dit gedrag te wijzigen. Dit script kan de functies gebruiken die zijn gedefinieerd in [Campagne JSAPI-documentatie](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html), inclusief functies die betrekking hebben op bestandsmanipulatie.

U kunt de koppeling naar deze bestanden opslaan in een lokale variabele of in een databaseveld. U kunt bijvoorbeeld het ontvangende schema uitbreiden om een koppeling naar op een bestand gebaseerde bronnen toe te voegen.

>[!CAUTION]
>
>* Dit type bestand moet worden gereserveerd voor formulieren met beveiligde toegang (met referenties).
>* Adobe Campaign bepaalt niet de grootte of het type geüploade bron: daarom adviseren wij hoogst gebruikend upload gebieden voor de veilige plaatsen van het typeIntranet slechts.
>* Als verscheidene servers met de instantie (lading het in evenwicht brengen architectuur) worden verbonden, moet u ervoor zorgen vraag aan de vorm van het Web op de zelfde server aankomt.
>* Deze implementaties vereisen de hulp van het Adobe Campaign Consulting-team.

>



## Een verborgen constante {#inserting-a-hidden-constant} invoegen

Wanneer de gebruiker een van de pagina&#39;s van het formulier valideert, kunt u een specifieke waarde instellen op een veld van zijn profiel of op een variabele.

Dit veld is niet zichtbaar voor de gebruiker, maar kan worden gebruikt om de gegevens in het gebruikersprofiel te verrijken.

Hiervoor plaatst u een **constante** op de pagina en geeft u de waarde en de opslaglocatie op.

In het volgende voorbeeld wordt het veld **origin** van het ontvangende profiel automatisch ingevuld wanneer een gebruiker deze pagina goedkeurt. De constante wordt niet weergegeven op de pagina.

![](assets/s_ncs_admin_survey_constante.png)

