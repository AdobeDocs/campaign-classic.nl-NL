---
solution: Campaign Classic
product: campaign
title: Filters maken
description: Filters maken
audience: platform
content-type: reference
topic-tags: filtering-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1974'
ht-degree: 0%

---


# Filters maken{#creating-filters}

## Inleiding {#introduction}

Wanneer u in de boom van Adobe Campaign (van **[!UICONTROL Explorer]** menu in de homepage) navigeert, worden de gegevens in het gegevensbestand getoond in lijsten. Deze lijsten kunnen worden gevormd om slechts de gegevens te tonen die door de exploitant worden vereist. De acties kunnen dan op de gefiltreerde gegevens worden gelanceerd. Met filterconfiguratie kunt u gegevens selecteren in een lijst **[!UICONTROL dynamically]**. Als de gegevens worden gewijzigd, worden de gefilterde gegevens bijgewerkt.

>[!NOTE]
>
>De vertoningsconfiguratie wordt plaatselijk op het werkstationniveau bepaald. Het wordt opgeslagen in verborgen bestanden en soms is het nodig deze gegevens op te schonen, vooral als zich problemen voordoen bij het vernieuwen van gegevens. Hiervoor gebruikt u het menu **[!UICONTROL File > Clear the local cache]**.

## Typologie van beschikbare filters {#typology-of-available-filters}

Met Adobe Campaign kunt u filters toepassen op gegevenslijsten.

Deze filters kunnen eenmaal worden gebruikt of u kunt ze opslaan voor toekomstig gebruik. U kunt meerdere filters tegelijk toepassen.

De volgende filtertypen zijn beschikbaar in Adobe Campaign:

* Standaardfilters

   Het standaardfilter **a1/> is toegankelijk via de velden boven de lijsten.** Hiermee kunt u filteren op vooraf gedefinieerde velden (dit zijn standaard de naam en het e-mailadres voor ontvangerprofielen). U kunt de velden gebruiken om de tekens in te voeren waarop u wilt filteren of om de filtervoorwaarden in een vervolgkeuzelijst te selecteren.

   ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an e-mail address in the domain "yahoo.com".
-->
U kunt het standaardfilter van een lijst veranderen. Voor meer op dit, verwijs naar [Veranderend het standaardfilter](#altering-the-default-filter).

* Eenvoudige filters

   **Eenvoudige** filters zijn eenmalige filters op de kolommen. Ze worden gedefinieerd met een of meer eenvoudige zoekcriteria op de weergegeven kolommen.

   U kunt verschillende eenvoudige filters op dezelfde gegevenslijst combineren om de zoekopdracht te verfijnen. De filtervelden worden onder elkaar weergegeven. Ze kunnen onafhankelijk van elkaar worden verwijderd.

   ![](assets/filters_recipient_simple_filter.png)

   Eenvoudige filters worden beschreven in [Een eenvoudig filter maken](#creating-a-simple-filter).

* Geavanceerde filters

   **Geavanceerde** filters worden gemaakt met behulp van een query of een combinatie van query&#39;s op de gegevens.

   Raadpleeg [Een geavanceerd filter maken](#creating-an-advanced-filter) voor meer informatie over het maken van een geavanceerd filter.

   U kunt functies gebruiken om de inhoud van het filter te bepalen. Raadpleeg [Een geavanceerd filter maken met functies](#creating-an-advanced-filter-with-functions) voor meer informatie.

   >[!NOTE]
   >
   >Raadpleeg [deze sectie](../../platform/using/about-queries-in-campaign.md) voor meer informatie over het samenstellen van query&#39;s in Adobe Campaign.

* Gebruikersfilters

   Een **toepassingsfilter** is een geavanceerd filter dat is opgeslagen, om zijn configuratie met andere exploitanten te gebruiken en te delen.

   De **[!UICONTROL Filters]** knoop die boven de lijsten wordt gevestigd biedt een reeks toepassingsfilters aan die kunnen worden gecombineerd om het filtreren te raffineren. De methode voor het maken van deze filters wordt weergegeven in [Een filter opslaan](#saving-a-filter).

## Het standaardfilter {#altering-the-default-filter} wijzigen

Als u het standaardfilter voor een lijst met ontvangers wilt wijzigen, klikt u op het knooppunt **[!UICONTROL Profiles and Targets > Pre-defined filters]** van de structuur.

Voor alle andere soorten gegevens, vorm de standaardfilter via **[!UICONTROL Administration > Configuration > Predefined filters]** knoop.

Voer de volgende stappen uit:

1. Selecteer het filter dat u standaard wilt gebruiken.
1. Klik op de tab **[!UICONTROL Parameters]** en selecteer **[!UICONTROL Default filter for the associated document type]**.

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >Als er al een standaardfilter op de lijst is toegepast, moet u dit uitschakelen voordat u een nieuw filter toepast. Klik hiertoe op het rode kruis rechts van de filtervelden.

1. Klik **[!UICONTROL Save]** om het filter toe te passen.

   >[!NOTE]
   >
   >Het venster van de filterdefinitie wordt gedetailleerd in [Creërend een geavanceerd filter](#creating-an-advanced-filter) en [Het Opslaan van een filter](#saving-a-filter).

## Een eenvoudig filter maken {#creating-a-simple-filter}

Als u een **eenvoudig filter** wilt maken, voert u de volgende stappen uit:

1. Klik met de rechtermuisknop op het veld waarop u wilt filteren en selecteer **[!UICONTROL Filter on this field]**.

   ![](assets/s_ncs_user_sort_this_field.png)

   De standaardfiltervelden worden boven de lijst weergegeven.

1. Selecteer de filteroptie in de vervolgkeuzelijst of voer de filtercriteria in die u wilt toepassen (de methode voor het selecteren of invoeren van criteria is afhankelijk van het type veld: tekst, opgesomd enz.).

   ![](assets/s_ncs_user_sort_fields.png)

1. Als u het filter wilt activeren, drukt u op Enter op het toetsenbord of klikt u op de groene pijl rechts van de filtervelden.

Als het veld waarop u de gegevens wilt filteren niet in de vorm van het profiel wordt weergegeven, kunt u het veld toevoegen in de weergegeven kolommen en vervolgens op die kolom filteren. Dit doet u als volgt,

1. Klik op het pictogram **[!UICONTROL Configure the list]**.

   ![](assets/s_ncs_user_configure_list.png)

1. Selecteer de kolom die moet worden weergegeven, bijvoorbeeld de leeftijd van de ontvangers.

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. Klik met de rechtermuisknop op de kolom **Leeftijd** in de lijst met ontvangers en selecteer **[!UICONTROL Filter on this column]**.

   ![](assets/s_ncs_user_sort_this_column.png)

   Vervolgens kunt u de filteropties voor leeftijd selecteren.

   ![](assets/s_ncs_user_delete_filter.png)

## Een geavanceerd filter maken {#creating-an-advanced-filter}

Als u een **geavanceerd filter** wilt maken, voert u de volgende stappen uit:

1. Klik op de knop **[!UICONTROL Filters]** en selecteer **[!UICONTROL Advanced filter...]**.

   ![](assets/filters_recipient_create_adv_filter.png)

   U kunt ook met de rechtermuisknop op de lijst met gegevens klikken die u wilt filteren en **[!UICONTROL Advanced filter...]** selecteren.

   Het venster voor filtervoorwaardendefinitie wordt weergegeven.

1. Klik op de kolom **[!UICONTROL Expression]** om de invoerwaarde te definiëren.
1. Klik **[!UICONTROL Edit expression]** om het gebied te selecteren waarop de filter zal worden toegepast.

   ![](assets/s_user_filter_choose_field.png)

1. Selecteer in de lijst het veld waarop de gegevens worden gefilterd. Klik **[!UICONTROL Finish]** om te bevestigen.
1. Klik op de kolom **[!UICONTROL Operator]** en selecteer de operator die u wilt toepassen in de vervolgkeuzelijst.
1. Selecteer een verwachte waarde in de kolom **[!UICONTROL Value]**. U kunt verschillende filters combineren om de query te verfijnen. Als u een filtervoorwaarde wilt toevoegen, klikt u op **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. U kunt een hiërarchie aan de uitdrukkingen toewijzen of de orde van de vraaguitdrukkingen veranderen gebruikend de toolbarpijlen.
1. De standaardoperator tussen expressies is **And**, maar u kunt dit wijzigen door op het veld te klikken. U kunt een **Of** exploitant selecteren.

   ![](assets/s_ncs_user_filter_operator.png)

1. Klik **[!UICONTROL OK]** om filterverwezenlijking te bevestigen en het op de lijst toe te passen.

Het toegepaste filter wordt boven de lijst weergegeven.

![](assets/s_ncs_user_filter_adv_edit.png)

Als u dit filter wilt bewerken of wijzigen, klikt u op het label ervan.

Als u dit filter wilt annuleren, klikt u op het pictogram **[!UICONTROL Remove this filter]** rechts van het filter.

![](assets/s_ncs_user_filter_adv_remove.png)

U kunt een geavanceerd filter opslaan om het voor toekomstig gebruik te houden. Zie [Een filter opslaan](#saving-a-filter) voor meer informatie over dit type filter.

### Een geavanceerd filter maken met functies {#creating-an-advanced-filter-with-functions}

Geavanceerde filters kunnen functies gebruiken; **filters met functies** worden gecreeerd via een uitdrukkingsredacteur die u formules laat tot stand brengen gebruikend de gegevensbestandgegevens en de geavanceerde functies. Als u een filter met functies wilt maken, herhaalt u de stappen 1, 2 en 3 voor het maken van geavanceerde filters en gaat u als volgt te werk:

1. Klik in het venster met veldselectie op **[!UICONTROL Advanced selection]**.
1. Selecteer het type formule dat u wilt gebruiken: aggregaat, bestaand gebruikersfilter of -expressie.

   ![](assets/s_ncs_user_filter_formula_select.png)

   De volgende opties zijn beschikbaar:

   * **[!UICONTROL Field only]** om een veld te selecteren. Dit is de standaardmodus.
   * **[!UICONTROL Aggregate]** om de te gebruiken samengestelde formule te selecteren (tellingen, som, gemiddelde, maximum, minimum).
   * **[!UICONTROL User filter]** om een van de bestaande gebruikersfilters te selecteren. Gebruikersfilters worden gedetailleerd weergegeven in [Een filter opslaan](#saving-a-filter).
   * **[!UICONTROL Expression]** om toegang te krijgen tot de uitdrukkingsredacteur.

      Met de expressieeditor kunt u een geavanceerd filter definiëren. Het ziet er zo uit:

      ![](assets/s_ncs_user_create_exp_exple01.png)

      Hiermee kunt u velden in de databasetabellen selecteren en er geavanceerde functies aan koppelen: Selecteer de functie die u wilt gebruiken in de **[!UICONTROL List of functions]**. De beschikbare functies worden beschreven in [Lijst met functies](../../platform/using/defining-filter-conditions.md#list-of-functions). Selecteer vervolgens het veld of de velden waarop de functies betrekking hebben en klik op **[!UICONTROL OK]** om de expressie goed te keuren.

      >[!NOTE]
      >
      >Voor een voorbeeld van filterverwezenlijking die op een uitdrukking wordt gebaseerd, verwijs naar [Het identificeren van ontvangers de waarvan verjaardag het ](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is) is.

## Een filter opslaan {#saving-a-filter}

Filters zijn specifiek voor elke operator en worden telkens opnieuw geïnitialiseerd wanneer de operator de cache van de clientconsole wist.

U kunt een **toepassingsfilter** tot stand brengen door een geavanceerd filter op te slaan: het kan opnieuw worden gebruikt door met de rechtermuisknop te klikken in om het even welke lijst of via de **[!UICONTROL Filters]** knoop boven de lijsten wordt gevestigd.

Deze filters zijn ook rechtstreeks toegankelijk via de wizard voor levering, in de doelselectiefase (zie [deze sectie](../../delivery/using/creating-an-email-delivery.md) voor meer informatie over het maken van leveringen). Als u het toepassingsfilter wilt maken, kunt u:

* Zet een geavanceerd filter in een toepassingsfilter om. Om dit te doen, klik **[!UICONTROL Save]** alvorens de geavanceerde filterredacteur te sluiten.

   ![](assets/s_ncs_user_filter_save.png)

* Maak dit toepassingsfilter via het knooppunt **[!UICONTROL Administration > Configuration > Predefined filters]** (of **[!UICONTROL Profiles and targets > Predefined filters]** voor ontvangers) van de structuur. Klik hiertoe met de rechtermuisknop op de lijst met filters en selecteer **[!UICONTROL New...]**. De procedure is hetzelfde als voor het maken van geavanceerde filters.

   In het veld **[!UICONTROL Label]** kunt u dit filter een naam geven. Deze naam wordt weergegeven in de keuzelijst met invoervak van de knop **[!UICONTROL Filters...]**.

   ![](assets/user_filter_apply.png)

U kunt alle filters in de huidige lijst verwijderen door met de rechtermuisknop te klikken en **[!UICONTROL No filter]** te selecteren of door het pictogram **[!UICONTROL Filters]** boven de lijst te plaatsen.

U kunt filters combineren door op de knop **[!UICONTROL Filters]** te klikken en het menu **[!UICONTROL And...]** te gebruiken.

![](assets/s_ncs_user_filter_combination.png)

## Ontvangers {#filtering-recipients} filteren

Met vooraf gedefinieerde filters (zie [Een filter opslaan](#saving-a-filter)) kunt u de profielen van ontvangers in de database filteren. U kunt filters van de **[!UICONTROL Profiles and Targets > Predefined filters]** knoop van de boom uitgeven. De filters worden weergegeven in de bovenste sectie van de werkruimte via de knop **[!UICONTROL Filters]**.

Selecteer een filter om de definitie ervan weer te geven en een voorvertoning van de gefilterde gegevens te openen.

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>Raadpleeg [case](../../platform/using/use-case.md) gebruiken voor een gedetailleerd voorbeeld van het maken van vooraf gedefinieerde filters.

De vooraf gedefinieerde filters zijn:

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Query</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Geopend<br /> </td> 
   <td> Selecteert ontvangers die een levering hebben geopend.<br /> </td> 
  </tr> 
  <tr> 
   <td> Geopend maar niet geklikt<br /> </td> 
   <td> Selecteert ontvangers die een levering hebben geopend maar niet op een verbinding geklikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Inactieve ontvangers<br /> </td> 
   <td> Selecteert ontvangers die geen levering in X maanden hebben geopend.<br /> </td> 
  </tr> 
  <tr> 
   <td> Laatste activiteit per apparaattype<br /> </td> 
   <td> Hiermee selecteert u ontvangers die op levering Y hebben geklikt of deze hebben geopend met apparaat X in de laatste Z-dagen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Laatste activiteit per apparaattype (reeksspatiëring)<br /> </td> 
   <td> Hiermee selecteert u ontvangers die op levering Y hebben geklikt of deze hebben geopend met apparaat X in de laatste Z-dagen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Niet-doelontvangers<br /> </td> 
   <td> Hiermee selecteert u ontvangers die nog nooit via kanaal Y zijn aangewezen in X maanden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Zeer actieve ontvangers<br /> </td> 
   <td> Selecteert ontvangers die in een levering minstens x keer in de laatste maanden van Y hebben geklikt.<br /> </td> 
  </tr> 
  <tr> 
 <td> Op de lijst met ongewenste personen staan e-mailadres<br /> </td> 
    <td> Hiermee selecteert u ontvangers waarvan het e-mailadres zich op de lijst van gewezen personen bevindt.<br/> </td>
  </tr> 
  <tr> 
   <td> Gegarandeerd e-mailadres<br /> </td> 
   <td> Hiermee selecteert u ontvangers waarvan het e-mailadres in quarantaine is geplaatst.<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mailadressen gedupliceerd in de map<br /> </td> 
   <td> Hiermee selecteert u ontvangers waarvan het e-mailadres in de map wordt gedupliceerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> Niet geopend en niet geklikt<br /> </td> 
   <td> Selecteert ontvangers die geen levering hebben geopend, of in een levering geklikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nieuwe ontvangers (dagen)<br /> </td> 
   <td> Selecteert ontvangers die in de laatste X dagen werden gecreeerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nieuwe ontvangers (minuten)<br /> </td> 
   <td> Hiermee selecteert u ontvangers die in de laatste X minuten zijn gemaakt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nieuwe ontvangers (maanden)<br /> </td> 
   <td> Selecteert ontvangers die in de laatste maanden van X.<br /> werden gecreeerd. </td> 
  </tr> 
  <tr> 
   <td> Op abonnement<br /> </td> 
   <td> Hiermee selecteert u ontvangers op abonnement.<br /> </td> 
  </tr> 
  <tr> 
   <td> Door op een specifieke koppeling te klikken<br /> </td> 
   <td> Selecteert ontvangers die op bepaalde URL in een levering klikte.<br /> </td> 
  </tr> 
  <tr> 
   <td> Op postbezorgingsgedrag<br /> </td> 
   <td> Selecteert ontvangers op basis van hun gedrag na het ontvangen van een levering.<br /> </td> 
  </tr> 
  <tr> 
   <td> Op aanmaakdatum<br /> </td> 
   <td> Hiermee selecteert u ontvangers op aanmaakdatum, over een periode van X maanden (huidige datum min n maanden) tot Y maanden (huidige datum min n maanden).<br /> </td> 
  </tr> 
  <tr> 
   <td> Op lijst<br /> </td> 
   <td> Hiermee selecteert u ontvangers op lijst.<br /> </td> 
  </tr> 
  <tr> 
   <td> Door aantal kliks<br /> </td> 
   <td> Selecteert ontvangers die in een levering in de laatste maanden van X.<br /> klikte </td> 
  </tr> 
  <tr> 
   <td> Op aantal ontvangen berichten<br /> </td> 
   <td> Hiermee selecteert u ontvangers op basis van het aantal berichten dat ze hebben ontvangen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Door aantal opent<br /> </td> 
   <td> Selecteert ontvangers die tussen de leveringen van X en van Y over de hoeveelheid tijd van Z.<br /> hebben geopend. </td> 
  </tr> 
  <tr> 
   <td> Op naam of e-mail<br /> </td> 
   <td> Hiermee selecteert u ontvangers op basis van hun naam of e-mail.<br /> </td> 
  </tr> 
  <tr> 
   <td> Op leeftijdbereik<br /> </td> 
   <td> Hiermee selecteert u ontvangers op basis van hun leeftijd.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Alle vergelijkingen met betrekking tot tellingen en termijnen moeten in bredere zin worden geïnterpreteerd (ontvangers die overeenkomen met de querylimieten worden in de vergelijking opgenomen).

Voorbeelden van de wijze waarop de gegevens worden berekend:

* Selecteert ontvangers die jonger zijn dan 30 jaar:

   ![](assets/predefined_filters_01.png)

* Selecteert ontvangers die 18 jaar of ouder zijn:

   ![](assets/predefined_filters_03.png)

* Selecteert ontvangers tussen 18 en 30 jaar:

   ![](assets/predefined_filters_02.png)

## Geavanceerde instellingen voor gegevensfilters {#advanced-settings-for-data-filters}

Klik op het tabblad **[!UICONTROL Settings]** voor toegang tot de volgende opties:

* **[!UICONTROL Default filter for the associated document type]**: met deze optie kunt u dit filter standaard voorstellen in de editor van de lijsten waarop de sortering betrekking heeft.

   Het filter **[!UICONTROL By name or login]** wordt bijvoorbeeld toegepast op operatoren. Deze optie is geselecteerd en het filter wordt dus altijd aangeboden in alle operatorlijsten.

* **[!UICONTROL Filter shared with other operators]**: Met deze optie kunt u het filter beschikbaar maken voor alle andere operatoren in de huidige database.
* **[!UICONTROL Use parameter entry form]**: Met deze optie kunt u de filtervelden definiëren die boven de lijst worden weergegeven wanneer dit filter wordt geselecteerd. Met deze velden kunt u de filterinstellingen definiëren. Dit formulier moet worden ingevoerd in XML-indeling via de knop **[!UICONTROL Form]**. Het vooraf geconfigureerde filter **[!UICONTROL Recipients who have opened]**, dat beschikbaar is in de lijst met ontvangers, geeft bijvoorbeeld een filterveld weer waarmee u de levering kunt selecteren waarop het filter is gericht.

   Met de knop **[!UICONTROL Preview]** wordt het resultaat van het geselecteerde filter weergegeven.

* Met de koppeling **[!UICONTROL Advanced parameters]** kunt u aanvullende instellingen definiëren. Met name kunt u een SQL-tabel aan het filter koppelen om deze te gebruiken voor alle editors die de tabel delen.

   Selecteer de optie **[!UICONTROL Do not restrict the filter]** als u wilt voorkomen dat de gebruiker dit filter overschrijft.

   Deze optie is ingeschakeld voor de filters &quot;Ontvangers van een levering&quot; en &quot;Ontvangers van leveringen die tot een map behoren&quot; die in de wizard voor levering worden aangeboden en die niet kunnen worden overgeladen.

   ![](assets/s_ncs_user_filter_advanced_param.png)

