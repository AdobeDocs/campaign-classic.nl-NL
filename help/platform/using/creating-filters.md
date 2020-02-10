---
title: Filters maken
seo-title: Filters maken
description: Filters maken
seo-description: null
page-status-flag: never-activated
uuid: 9fa4a80d-8f03-4f24-92a1-44f6ae2a2337
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: filtering-data
discoiquuid: 066e730b-2527-4257-b11f-2e73f746a8a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Filters maken{#creating-filters}

## Inleiding {#introduction}

Wanneer u in de Adobe Campagne boom (van het **[!UICONTROL Explorer]** menu in de homepage) navigeert, worden de gegevens in het gegevensbestand getoond in lijsten. Deze lijsten kunnen worden gevormd om slechts de gegevens te tonen die door de exploitant worden vereist. De acties kunnen dan op de gefiltreerde gegevens worden gelanceerd. Met de filterconfiguratie kunt u gegevens in een lijst selecteren **[!UICONTROL dynamically]**. Als de gegevens worden gewijzigd, worden de gefilterde gegevens bijgewerkt.

>[!NOTE]
>
>De vertoningsconfiguratie wordt plaatselijk op het werkstationniveau bepaald. Het wordt opgeslagen in verborgen bestanden en soms is het nodig deze gegevens op te schonen, vooral als zich problemen voordoen bij het vernieuwen van gegevens. Gebruik dit **[!UICONTROL File > Clear the local cache]** menu.

## Typologie van beschikbare filters {#typology-of-available-filters}

Met Adobe Campaign kunt u filters toepassen op gegevenslijsten.

Deze filters kunnen eenmaal worden gebruikt of u kunt ze opslaan voor toekomstig gebruik. U kunt meerdere filters tegelijk toepassen.

De volgende filtertypen zijn beschikbaar in Adobe Campagne:

* Standaardfilters

   Het **standaardfilter** is toegankelijk via de velden boven de lijsten. Hiermee kunt u filteren op vooraf gedefinieerde velden (dit zijn standaard de naam en het e-mailadres voor ontvangerprofielen). U kunt de velden gebruiken om de tekens in te voeren waarop u wilt filteren of om de filtervoorwaarden in een vervolgkeuzelijst te selecteren.

   ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an e-mail address in the domain "yahoo.com".
-->
U kunt het standaardfilter van een lijst veranderen. Zie Het standaardfilter [wijzigen voor meer informatie](#altering-the-default-filter).

* Eenvoudige filters

   **Eenvoudige filters** zijn eenmalige filters op de kolommen. Ze worden gedefinieerd met een of meer eenvoudige zoekcriteria op de weergegeven kolommen.

   U kunt verschillende eenvoudige filters op dezelfde gegevenslijst combineren om de zoekopdracht te verfijnen. De filtervelden worden onder elkaar weergegeven. Ze kunnen onafhankelijk van elkaar worden verwijderd.

   ![](assets/filters_recipient_simple_filter.png)

   Eenvoudige filters worden gedetailleerd weergegeven in [Een eenvoudig filter](#creating-a-simple-filter)maken.

* Geavanceerde filters

   **Geavanceerde filters** worden gemaakt met behulp van een query of een combinatie van query&#39;s op de gegevens.

   Raadpleeg Een geavanceerd filter [maken voor meer informatie over het maken van een geavanceerd filter](#creating-an-advanced-filter).

   U kunt functies gebruiken om de inhoud van het filter te bepalen. Zie [Een geavanceerd filter met functies](#creating-an-advanced-filter-with-functions)maken voor meer informatie hierover.

   >[!NOTE]
   >
   >Raadpleeg [deze sectie](../../platform/using/about-queries-in-campaign.md)voor meer informatie over het maken van query&#39;s in Adobe Campaign.

* Gebruikersfilters

   Een **toepassingsfilter** is een geavanceerd filter dat is opgeslagen, om zijn configuratie met andere exploitanten te gebruiken en te delen.

   De **[!UICONTROL Filters]** knoop die boven de lijsten wordt gevestigd biedt een reeks toepassingsfilters aan die kunnen worden gecombineerd om het filtreren te raffineren. De methode voor het maken van deze filters wordt weergegeven bij het [opslaan van een filter](#saving-a-filter).

## Het standaardfilter wijzigen {#altering-the-default-filter}

Als u het standaardfilter voor een lijst met ontvangers wilt wijzigen, klikt u op het **[!UICONTROL Profiles and Targets > Pre-defined filters]** knooppunt van de structuur.

Voor alle andere soorten gegevens, vorm de standaardfilter via de **[!UICONTROL Administration > Configuration > Predefined filters]** knoop.

Voer de volgende stappen uit:

1. Selecteer het filter dat u standaard wilt gebruiken.
1. Klik op het **[!UICONTROL Parameters]** tabblad en selecteer **[!UICONTROL Default filter for the associated document type]**.

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >Als er al een standaardfilter op de lijst is toegepast, moet u dit uitschakelen voordat u een nieuw filter toepast. Klik hiertoe op het rode kruis rechts van de filtervelden.

1. Klik **[!UICONTROL Save]** om het filter toe te passen.

   >[!NOTE]
   >
   >Het venster van de filterdefinitie is gedetailleerd in het [Creëren van een geavanceerd filter](#creating-an-advanced-filter) en het [Opslaan van een filter](#saving-a-filter).

## Een eenvoudig filter maken {#creating-a-simple-filter}

Voer de volgende stappen uit om een **eenvoudig filter** te maken:

1. Klik met de rechtermuisknop op het veld dat u wilt filteren en selecteer **[!UICONTROL Filter on this field]**.

   ![](assets/s_ncs_user_sort_this_field.png)

   De standaardfiltervelden worden boven de lijst weergegeven.

1. Selecteer de filteroptie in de vervolgkeuzelijst of voer de filtercriteria in die u wilt toepassen (de methode voor het selecteren of invoeren van criteria is afhankelijk van het type veld: tekst, opgesomd enz.).

   ![](assets/s_ncs_user_sort_fields.png)

1. Als u het filter wilt activeren, drukt u op Enter op het toetsenbord of klikt u op de groene pijl rechts van de filtervelden.

Als het veld waarop u de gegevens wilt filteren niet in de vorm van het profiel wordt weergegeven, kunt u het veld toevoegen in de weergegeven kolommen en vervolgens op die kolom filteren. Om dit te doen,

1. Klik op het **[!UICONTROL Configure the list]** pictogram.

   ![](assets/s_ncs_user_configure_list.png)

1. Selecteer de kolom die moet worden weergegeven, bijvoorbeeld de leeftijd van de ontvangers.

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. Klik met de rechtermuisknop op de kolom **Leeftijd** in de lijst met ontvangers en selecteer **[!UICONTROL Filter on this column]**.

   ![](assets/s_ncs_user_sort_this_column.png)

   Vervolgens kunt u de filteropties voor leeftijd selecteren.

   ![](assets/s_ncs_user_delete_filter.png)

## Een geavanceerd filter maken {#creating-an-advanced-filter}

Voer de volgende stappen uit om een **geavanceerd filter** te maken:

1. Klik op de **[!UICONTROL Filters]** knop en selecteer **[!UICONTROL Advanced filter...]**.

   ![](assets/filters_recipient_create_adv_filter.png)

   U kunt ook met de rechtermuisknop op de lijst met gegevens klikken die u wilt filteren en selecteren **[!UICONTROL Advanced filter...]**.

   Het venster voor filtervoorwaardendefinitie wordt weergegeven.

1. Klik op de **[!UICONTROL Expression]** kolom om de invoerwaarde te definiëren.
1. Klik **[!UICONTROL Edit expression]** om het veld te selecteren waarop het filter wordt toegepast.

   ![](assets/s_user_filter_choose_field.png)

1. Selecteer in de lijst het veld waarop de gegevens worden gefilterd. Klik **[!UICONTROL Finish]** om te bevestigen.
1. Klik op de **[!UICONTROL Operator]** kolom en selecteer de operator die u wilt toepassen in de vervolgkeuzelijst.
1. Selecteer een verwachte waarde in de **[!UICONTROL Value]** kolom. U kunt verschillende filters combineren om de query te verfijnen. Klik op een filtervoorwaarde om deze toe te voegen **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. U kunt een hiërarchie aan de uitdrukkingen toewijzen of de orde van de vraaguitdrukkingen veranderen gebruikend de toolbarpijlen.
1. De standaardoperator tussen expressies is **And**, maar u kunt deze wijzigen door op het veld te klikken. U kunt een operator **Of** selecteren.

   ![](assets/s_ncs_user_filter_operator.png)

1. Klik **[!UICONTROL OK]** om het maken van filters te bevestigen en deze toe te passen op de lijst.

Het toegepaste filter wordt boven de lijst weergegeven.

![](assets/s_ncs_user_filter_adv_edit.png)

Als u dit filter wilt bewerken of wijzigen, klikt u op het label ervan.

Als u dit filter wilt annuleren, klikt u op het **[!UICONTROL Remove this filter]** pictogram rechts van het filter.

![](assets/s_ncs_user_filter_adv_remove.png)

U kunt een geavanceerd filter opslaan om het voor toekomstig gebruik te houden. Zie Een filter [opslaan voor meer informatie over dit type filter](#saving-a-filter).

### Een geavanceerd filter met functies maken {#creating-an-advanced-filter-with-functions}

Geavanceerde filters kunnen functies gebruiken; Er worden **filters met functies** gemaakt via een expressie-editor waarmee u formules kunt maken met behulp van de databasegegevens en geavanceerde functies. Als u een filter met functies wilt maken, herhaalt u de stappen 1, 2 en 3 voor het maken van geavanceerde filters en gaat u als volgt te werk:

1. Klik in het venster Veldselectie op **[!UICONTROL Advanced selection]**.
1. Selecteer het type formule dat u wilt gebruiken: aggregaat, bestaand gebruikersfilter of -expressie.

   ![](assets/s_ncs_user_filter_formula_select.png)

   De volgende opties zijn beschikbaar:

   * **[!UICONTROL Field only]** om een veld te selecteren. Dit is de standaardmodus.
   * **[!UICONTROL Aggregate]** om de te gebruiken samengestelde formule te selecteren (tellingen, som, gemiddelde, maximum, minimum).
   * **[!UICONTROL User filter]** om een van de bestaande gebruikersfilters te selecteren. Gebruikerfilters worden gedetailleerd weergegeven bij het [opslaan van een filter](#saving-a-filter).
   * **[!UICONTROL Expression]** om toegang te krijgen tot de uitdrukkingsredacteur.

      Met de expressieeditor kunt u een geavanceerd filter definiëren. Het ziet er zo uit:

      ![](assets/s_ncs_user_create_exp_exple01.png)

      Hiermee kunt u velden in de databasetabellen selecteren en er geavanceerde functies aan koppelen: Selecteer de functie die u wilt gebruiken in de **[!UICONTROL List of functions]**. De beschikbare functies worden beschreven in [Lijst met functies](../../platform/using/defining-filter-conditions.md#list-of-functions). Selecteer vervolgens het veld of de velden waarop de functies betrekking hebben en klik **[!UICONTROL OK]** om de expressie goed te keuren.

      >[!NOTE]
      >
      >Voor een voorbeeld van filterverwezenlijking die op een uitdrukking wordt gebaseerd, verwijs naar het [Identificeren van ontvangers de waarvan verjaardag het is](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is).

## Een filter opslaan {#saving-a-filter}

Filters zijn specifiek voor elke operator en worden telkens opnieuw geïnitialiseerd wanneer de operator de cache van de clientconsole wist.

U kunt een **toepassingsfilter** maken door een geavanceerd filter op te slaan: het kan opnieuw worden gebruikt door met de rechtermuisknop in om het even welke lijst of via de **[!UICONTROL Filters]** knoop boven de lijsten te klikken.

Deze filters zijn ook rechtstreeks toegankelijk via de wizard voor levering, in de doelselectiefase (raadpleeg [deze sectie](../../delivery/using/creating-an-email-delivery.md) voor meer informatie over het maken van leveringen). Als u het toepassingsfilter wilt maken, kunt u:

* Zet een geavanceerd filter in een toepassingsfilter om. Om dit te doen, klik **[!UICONTROL Save]** alvorens de geavanceerde filterredacteur te sluiten.

   ![](assets/s_ncs_user_filter_save.png)

* Maak dit toepassingsfilter via het knooppunt **[!UICONTROL Administration > Configuration > Predefined filters]** (of **[!UICONTROL Profiles and targets > Predefined filters]** voor ontvangers) van de boomstructuur. Klik hiertoe met de rechtermuisknop op de lijst met filters en selecteer **[!UICONTROL New...]**. De procedure is hetzelfde als voor het maken van geavanceerde filters.

   In het **[!UICONTROL Label]** veld kunt u dit filter een naam geven. Deze naam wordt weergegeven in het keuzemenu met invoervak van de **[!UICONTROL Filters...]** knop.

   ![](assets/user_filter_apply.png)

U kunt alle filters in de huidige lijst verwijderen door met de rechtermuisknop te klikken en deze te selecteren **[!UICONTROL No filter]** of door het **[!UICONTROL Filters]** pictogram boven de lijst te kiezen.

U kunt filters combineren door op de **[!UICONTROL Filters]** knop te klikken en het **[!UICONTROL And...]** menu te gebruiken.

![](assets/s_ncs_user_filter_combination.png)

## Ontvangers filteren {#filtering-recipients}

Met vooraf gedefinieerde filters (zie Een filter [opslaan](#saving-a-filter)) kunt u de profielen filteren van ontvangers in de database. U kunt filters van de **[!UICONTROL Profiles and Targets > Predefined filters]** knoop van de boom uitgeven. De filters worden via de **[!UICONTROL Filters]** knop weergegeven in de bovenste sectie van de werkruimte.

Selecteer een filter om de definitie ervan weer te geven en een voorvertoning van de gefilterde gegevens te openen.

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>Zie [Hoofdletters](../../platform/using/use-case.md)gebruiken voor een gedetailleerd voorbeeld van het maken van vooraf gedefinieerde filters.

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
   <td> Hiermee selecteert u ontvangers die een levering hebben geopend maar nog niet op een koppeling hebben geklikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Inactieve ontvangers<br /> </td> 
   <td> Selecteert ontvangers die geen levering hebben geopend in X maanden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Laatste activiteit per apparaattype<br /> </td> 
   <td> Hiermee selecteert u ontvangers die de laatste Z-dagen op levering Y hebben geklikt of deze hebben geopend met apparaat X.<br /> </td> 
  </tr> 
  <tr> 
   <td> Laatste activiteit per apparaattype (reeksspatiëring)<br /> </td> 
   <td> Hiermee selecteert u ontvangers die de laatste Z-dagen op levering Y hebben geklikt of deze hebben geopend met apparaat X.<br /> </td> 
  </tr> 
  <tr> 
   <td> Niet-doelontvangers<br /> </td> 
   <td> Hiermee selecteert u ontvangers die nog nooit via kanaal Y zijn aangewezen in X maanden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Zeer actieve ontvangers<br /> </td> 
   <td> Hiermee selecteert u ontvangers die in de afgelopen maanden ten minste x maal op een levering hebben geklikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mailadres in zwarte lijst<br /> </td> 
   <td> Hiermee selecteert u ontvangers wier e-mailadres op de zwarte lijst staat.<br /> </td> 
  </tr> 
  <tr> 
   <td> Gegarandeerd e-mailadres<br /> </td> 
   <td> Hiermee selecteert u ontvangers wier e-mailadres in quarantaine is geplaatst.<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mailadressen die in de map zijn gedupliceerd<br /> </td> 
   <td> Hiermee selecteert u ontvangers waarvan het e-mailadres in de map wordt gedupliceerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> Niet geopend en niet geklikt<br /> </td> 
   <td> Hiermee selecteert u ontvangers die geen levering hebben geopend of op een levering hebben geklikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nieuwe ontvangers (dagen)<br /> </td> 
   <td> Hiermee selecteert u ontvangers die in de laatste X dagen zijn gemaakt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nieuwe ontvangers (minuten)<br /> </td> 
   <td> Hiermee selecteert u ontvangers die in de laatste X minuten zijn gemaakt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nieuwe ontvangers (maanden)<br /> </td> 
   <td> Hiermee selecteert u ontvangers die in de laatste X maanden zijn gemaakt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Op abonnement<br /> </td> 
   <td> Hiermee selecteert u ontvangers op abonnement.<br /> </td> 
  </tr> 
  <tr> 
   <td> Door op een specifieke koppeling te klikken<br /> </td> 
   <td> Selecteert ontvangers die op een bepaalde URL in een levering hebben geklikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Per postbezorging<br /> </td> 
   <td> Hiermee worden ontvangers geselecteerd op basis van hun gedrag na ontvangst van een levering.<br /> </td> 
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
   <td> Op aantal klikken<br /> </td> 
   <td> Selecteert ontvangers die in een levering in de laatste maanden van X klikte.<br /> </td> 
  </tr> 
  <tr> 
   <td> Op aantal ontvangen berichten<br /> </td> 
   <td> Hiermee selecteert u ontvangers op basis van het aantal berichten dat ze hebben ontvangen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Op aantal wordt geopend<br /> </td> 
   <td> Selecteert ontvangers die tussen de leveringen van X en van Y over de hoeveelheid tijd van Z opende.<br /> </td> 
  </tr> 
  <tr> 
   <td> Op naam of e-mail<br /> </td> 
   <td> Hiermee selecteert u ontvangers op basis van hun naam of e-mail.<br /> </td> 
  </tr> 
  <tr> 
   <td> Op leeftijdbereik<br /> </td> 
   <td> Hiermee worden ontvangers geselecteerd op basis van hun leeftijd.<br /> </td> 
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

Klik op het **[!UICONTROL Settings]** tabblad voor toegang tot de volgende opties:

* **[!UICONTROL Default filter for the associated document type]**: met deze optie kunt u dit filter standaard voorstellen in de editor van de lijsten waarop de sortering betrekking heeft.

   Het **[!UICONTROL By name or login]** filter wordt bijvoorbeeld toegepast op operatoren. Deze optie is geselecteerd en het filter wordt dus altijd aangeboden in alle operatorlijsten.

* **[!UICONTROL Filter shared with other operators]**: Met deze optie kunt u het filter beschikbaar maken voor alle andere operatoren in de huidige database.
* **[!UICONTROL Use parameter entry form]**: Met deze optie kunt u de filtervelden definiëren die boven de lijst worden weergegeven wanneer dit filter wordt geselecteerd. Met deze velden kunt u de filterinstellingen definiëren. Dit formulier moet met de **[!UICONTROL Form]** knop in XML-indeling worden ingevoerd. Het vooraf geconfigureerde filter, dat beschikbaar is in de lijst met ontvangers, geeft bijvoorbeeld een filterveld weer waarmee u de levering kunt selecteren waarop het filter is gericht. **[!UICONTROL Recipients who have opened]**

   De **[!UICONTROL Preview]** knop geeft het resultaat van het geselecteerde filter weer.

* Met de **[!UICONTROL Advanced parameters]** koppeling kunt u aanvullende instellingen definiëren. Met name kunt u een SQL-tabel aan het filter koppelen om deze te gebruiken voor alle editors die de tabel delen.

   Selecteer de **[!UICONTROL Do not restrict the filter]** optie als u wilt voorkomen dat de gebruiker dit filter overschrijft.

   Deze optie is ingeschakeld voor de filters &quot;Ontvangers van een levering&quot; en &quot;Ontvangers van leveringen die tot een map behoren&quot; die in de wizard voor levering worden aangeboden en die niet kunnen worden overgeladen.

   ![](assets/s_ncs_user_filter_advanced_param.png)

