---
solution: Campaign Classic
product: campaign
title: Concepten en methodologie
description: Concepten en methodologie
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1491'
ht-degree: 1%

---


# Aanbevolen werkwijzen voor kubussen{#concepts-and-methodology}

## Gegevensbinding {#data-binning}

Met Binding kunt u de gegevensweergave vereenvoudigen door waarden te groeperen op basis van criteria. Afhankelijk van de informatie beschikbaar aan u, kunt u leeftijdsgroepen, groep e-maildomeinen samen bepalen, tot een waardeopsomming beperken, uitdrukkelijk de gegevens beperken tot vertoning en groepeert alle andere gegevens in een specifieke lijn of een kolom, enz.

Er zijn in totaal drie typen binding beschikbaar:

1. Handmatig gedefinieerde waardebereiken gebruiken. Bijvoorbeeld leeftijd, gemiddelde winkelwagentje, aantal geopende leveringen, enz.). Voor meer op dit, verwijs naar [Bepalend elke bak](#defining-each-bin).
1. Afhankelijk van de waarden van een opsomming, dynamisch: alleen de waarden in de opsomming worden weergegeven, alle andere waarden worden gegroepeerd in &#39;Overige&#39;. Voor meer op dit, verwijs naar [dynamisch het beheren van bins](#dynamically-managing-bins).
1. Met behulp van waardebereiken worden alle andere reeksen gegroepeerd. Bijvoorbeeld 18- tot 25-jarigen, 26- tot 59-jarigen en de andere. Raadpleeg [Waardebereiken maken](#creating-value-ranges) voor meer informatie.

Om het binden toe te laten, controleer de aangewezen doos wanneer het creëren van de afmeting.

![](assets/s_advuser_cube_class_00.png)

U kunt mappen handmatig maken of ze koppelen aan een bestaande opsomming.

Adobe Campaign biedt ook een assistent voor automatisch binden: Waarden kunnen worden opgesplitst in N-groepen of worden gegroepeerd op basis van de meest voorkomende waarden in de database.

### Elke bin {#defining-each-bin} definiëren

Als u elke bin afzonderlijk wilt maken, selecteert u de optie **[!UICONTROL Define each bin]** en gebruikt u de tabel om de verschillende vakken te maken.

![](assets/s_advuser_cube_class_01.png)

Klik op de knop **[!UICONTROL Add]** om een nieuw vak te maken en geef de waarden op die in het vak worden gegroepeerd.

![](assets/s_advuser_cube_class_02.png)

In het volgende voorbeeld worden talen gegroepeerd in drie categorieën: Engels/Duits/Nederlands, Frans/Italiaans/Spaans, en andere.

![](assets/s_advuser_cube_class_03.png)

Met een SQL-masker kunt u verschillende waarden combineren tot een filter. Hiervoor controleert u **[!UICONTROL Yes]** in de kolom **[!UICONTROL Use an SQL mask]** en voert u het SQL-filter in dat in de kolom **[!UICONTROL Value or expression]** moet worden toegepast.

In het onderstaande voorbeeld worden alle e-maildomeinen weergegeven die beginnen met **yahoo** (yahoo.fr, yahoo.com, yahoo.be, enz.) of met **ymail** (ymail.com, ymail.eu, enz.) wordt onder het label **YAHOO!** en adressen met het  **rocketmail.** comdomain.

![](assets/s_advuser_cube_class_03b.png)

### Dynamisch beheren van bins {#dynamically-managing-bins}

Waarden kunnen dynamisch worden beheerd via opsommingen. Dit betekent dat alleen de waarden in de opsomming worden weergegeven. Wanneer de opsommingswaarden worden gewijzigd, wordt de inhoud van de kubus automatisch aangepast.

Voer de volgende stappen uit om dit type waardenbinding te maken:

1. Maak een nieuwe dimensie en schakel het binden in.
1. Selecteer de optie **[!UICONTROL Dynamically link the values to an enumeration]** en selecteer de overeenkomstige opsomming.

   ![](assets/s_advuser_cube_class_04.png)

   Wanneer de opsommingswaarden worden bijgewerkt, worden de overeenkomstige bakken automatisch aangepast.

### Waardebereiken {#creating-value-ranges} maken

U kunt de waarden op basis van een gewenst interval groeperen in bereiken.

Als u bereiken handmatig wilt definiëren, klikt u op de knop **[!UICONTROL Add]** en selecteert u **[!UICONTROL Define a range]**:

![](assets/s_advuser_cube_class_05.png)

Geef vervolgens de onderste en bovenste limiet op en klik op **[!UICONTROL Ok]** om te bevestigen.

### Automatisch bins genereren {#generating-bins-automatically}

Het is ook mogelijk om automatisch bakken te produceren. Klik op de koppeling **[!UICONTROL Generate bins...]** om dit te doen.

![](assets/s_advuser_cube_class_06.png)

U kunt:

* De meest gebruikte waarden herstellen

   In het volgende voorbeeld worden de vier meest gebruikte waarden weergegeven, terwijl de andere worden geteld en gegroepeerd in de categorie &#39;Overige&#39;.

* Banden genereren in de vorm van sleuven

   In het volgende voorbeeld maakt Adobe Campaign automatisch vier sleuven van hetzelfde formaat om de waarden in de database weer te geven.

In dit geval wordt het filter dat in het feitelijke schema is geselecteerd, genegeerd.

### Opsommingen {#enumerations}

Om de relevantie en leesbaarheid van een rapport te verbeteren, kunt u met Adobe Campaign specifieke opsommingen maken om verschillende waarden te groeperen in hetzelfde vak. Deze opsommingen, die voor het binden worden gereserveerd, worden van verwijzingen voorzien in de kubussen dan getoond in de rapporten.

Adobe Campaign biedt ook een opsomming op domeinen aan die u een lijst van de e-maildomeinen van alle contacten in het gegevensbestand laat tonen, die door ISP, zoals aangetoond in het volgende voorbeeld wordt gegroepeerd:

![](assets/nmx_report_sample.png)

Deze is gemaakt met de volgende sjabloon:

![](assets/nmx_enum_domain.png)

Als u een rapport wilt maken met deze opsomming, maakt u een kubus met de **[!UICONTROL Email domain]**-dimensie. Kies de optie **[!UICONTROL Enable binning]** en **[!UICONTROL Dynamically link the values to an enumeration]**. Selecteer vervolgens de opsomming **Domains** zoals hierboven wordt weergegeven. Alle waarden zonder opgegeven alias worden opnieuw gegroepeerd onder het label **Overige**.

![](assets/nmx_add_dimension.png)

Maak vervolgens een rapport op basis van deze kubus om de waarden weer te geven.

U hoeft alleen de opsomming te wijzigen om het verwante rapport bij te werken. Maak bijvoorbeeld de waarde **Adobe** en voeg de alias **adobe.com** toe. Het rapport wordt automatisch bijgewerkt met de waarde Adobe op het opsommingsniveau.

![](assets/nmx_add_alias.png)

De **[!UICONTROL Domains]** opsomming wordt gebruikt om ingebouwde rapporten te produceren die de lijst van domeinen tonen. Als u de inhoud van deze rapporten wilt aanpassen, kunt u deze lijst bewerken.

U kunt andere opsommingen maken die zijn gereserveerd voor binden en deze gebruiken in andere kubussen: alle aliaswaarden worden opnieuw gegroepeerd in de vakken die zijn opgegeven op het eerste tabblad voor opsomming.

## Berekenen en gebruiken van aggregaten {#calculating-and-using-aggregates}

De grootste gegevensvolumes kunnen in aggregaten worden berekend.

Samengevoegde gegevens zijn handig wanneer u grote hoeveelheden gegevens bewerkt. Ze worden automatisch bijgewerkt op basis van de instellingen die in het specifieke werkstroomvak zijn gedefinieerd, zodat de gegevens die het laatst zijn verzameld, worden geïntegreerd in de indicatoren

De aggregaten worden bepaald in het relevante lusje van elke kubus.

![](assets/s_advuser_cube_agregate_01.png)

>[!NOTE]
>
>De workflow voor het bijwerken van geaggregeerde berekeningen kan worden geconfigureerd in het aggregaat zelf, of het aggregaat kan worden bijgewerkt via een externe workflow die is gekoppeld aan de relevante kubus.

Voer de volgende stappen uit om een nieuw aggregaat te maken:

1. Klik op de tab **[!UICONTROL Aggregates]** van de kubus en klik vervolgens op de knop **[!UICONTROL Add]**.

   ![](assets/s_advuser_cube_agregate_02.png)

1. Voer een label in voor het aggregaat en voeg vervolgens de afmetingen toe die moeten worden berekend.

   ![](assets/s_advuser_cube_agregate_03.png)

1. Selecteer een dimensie en een niveau. Herhaal dit proces voor elke dimensie en elk niveau.
1. Klik op het tabblad **[!UICONTROL Workflow]** om de samenvoegingsworkflow te maken.

   ![](assets/s_advuser_cube_agregate_04.png)

   * Met de activiteit **[!UICONTROL Scheduler]** kunt u de frequentie van de berekening-updates definiëren. De planner wordt gedetailleerd in [deze sectie](../../workflow/using/scheduler.md).
   * Met de activiteit **[!UICONTROL Aggregate update]** kunt u de updatemodus selecteren die u wilt toepassen: volledig of gedeeltelijk.

      Standaard wordt bij elke berekening een volledige update uitgevoerd. Als u een gedeeltelijke update wilt inschakelen, selecteert u de desbetreffende optie en definieert u de updatevoorwaarden.

      ![](assets/s_advuser_cube_agregate_05.png)

## Bepalende maatregelen {#defining-measures}

De typen metingen worden gedefinieerd op het tabblad **[!UICONTROL Measures]** van de kubus. U kunt sommen, gemiddelden, afwijkingen, enz. berekenen.

U kunt zoveel maatregelen maken als nodig zijn: Selecteer vervolgens de maatregel die u in de tabel wilt weergeven of verbergen. Voor meer op dit, verwijs naar [Weergavemaatregelen](#displaying-measures).

Voer de volgende stappen uit om een nieuwe maatregel te definiëren:

1. Klik op de knop **[!UICONTROL Add]** boven de lijst met maatregelen en selecteer het type maatregel en de formule die u wilt berekenen.

   ![](assets/s_advuser_cube_create_a_measure.png)

1. Kies zo nodig, en afhankelijk van de operator, de expressie waarop de bewerking betrekking heeft.

   Met de knop **[!UICONTROL Advanced selection]** kunt u complexe berekeningsformules maken. Raadpleeg [deze sectie](../../platform/using/about-queries-in-campaign.md) voor meer informatie.

   ![](assets/s_advuser_cube_create_a_measure_01.png)

1. Met de koppeling **[!UICONTROL Filter the measure data...]** kunt u het berekeningsveld beperken en dit alleen toepassen op specifieke gegevens in de database.

   ![](assets/s_advuser_cube_create_a_measure_02.png)

1. Voer het label van de maatregel in en voeg een beschrijving toe. Klik vervolgens op **[!UICONTROL Finish]** om deze te maken.

## Maatregelen {#displaying-measures} weergeven

U kunt de weergave van maatregelen in de tabel configureren, afhankelijk van uw behoeften:

* de weergavereeks van metingen (zie [Weergavevolgorde](#display-sequence));
* de informatie om in het rapport te tonen/te verbergen (verwijs naar [het Vormen van de vertoning](#configuring-the-display))
* welke maatstaven moeten worden weergegeven: percentage, totaal, aantal decimalen enz. (raadpleeg [Het weergegeven type maat wijzigen](#changing-the-type-of-measure-displayed)).

### Weergavevolgorde {#display-sequence}

De in de kubus berekende metingen worden gevormd via de **[!UICONTROL Measures]** knoop.

Verplaats de lijnen om de weergavereeks te wijzigen. In het volgende voorbeeld worden Franse gegevens naar de onderkant van de lijst verplaatst: dit betekent dat het in de laatste kolom zal worden getoond.

![](assets/s_advuser_cube_in_report_config_04.png)

### De weergave {#configuring-the-display} configureren

De opstelling van maatregelen, lijnen en kolommen kan voor elke maatregel afzonderlijk of in zijn geheel worden uitgevoerd. Met een specifiek pictogram hebt u toegang tot het selectievenster voor de weergavemodus.

* Klik op het pictogram **[!UICONTROL Edit the configuration of the pivot table]** om het configuratievenster te openen.

   U kunt kiezen of u de labels van maatregelen wilt weergeven en de lay-out (lijnen of kolommen) ervan wilt configureren.

![](assets/s_advuser_cube_in_report_config_05.png)

Met de kleuropties kunt u belangrijke waarden markeren, zodat u deze eenvoudig kunt lezen.

![](assets/s_advuser_cube_in_report_config_06.png)

### Het weergegeven type maat wijzigen {#changing-the-type-of-measure-displayed}

Binnen elke meting kunt u de toe te passen eenheid en opmaak definiëren.

![](assets/s_advuser_cube_in_report_config_07.png)

## Een rapport delen {#sharing-a-report}

Zodra het rapport wordt gevormd, kunt u het bewaren en het met andere exploitanten delen.

Klik hiertoe op het pictogram **[!UICONTROL Show the report properties]** en schakel de optie **[!UICONTROL Share this report]** in.

![](assets/cube_share_option.png)

Geef aan tot welke categorie het rapport behoort en wat de relevantie ervan is. Voor meer op dit, verwijs in [deze pagina](../../reporting/using/configuring-access-to-the-report.md#report-display-context) naar **Reeks van de Vertoning** en **Bepalend de het filtreren opties** secties.

Om deze veranderingen te bevestigen, moet u het rapport bewaren.

![](assets/cube_share_confirm.png)

## Filters maken {#creating-filters}

Het is mogelijk filters te maken voor het weergeven van een gedeelte van de gegevens.

Dit doet u als volgt:

1. Klik op het pictogram **[!UICONTROL Add a filter]**.

   ![](assets/neolap_add_filter.png)

1. Selecteer de dimensie waarop het filter betrekking heeft

   ![](assets/neolap_define_filter.png)

1. Selecteer het type filter en de precisie ervan.

   ![](assets/neolap_ceate_filter.png)

1. Zodra het wordt gecreeerd, wordt de filter getoond boven het rapport.

   ![](assets/neolap_filter_zone.png)

   Klik op het filter om het te bewerken.

   Klik op het kruisje om het te verwijderen.

   U kunt zoveel filters combineren als nodig is: zij zullen allemaal op dit gebied worden getoond .

   ![](assets/neolap_multiple_filters.png)

Telkens wanneer een filter wordt gewijzigd (voeg toe, verwijder, verander), moet het rapport worden opnieuw berekend.

U kunt ook filters maken op basis van een selectie. Hiervoor selecteert u de broncellen, -lijnen en -kolommen en klikt u op het pictogram **[!UICONTROL Add a filter]**.

Als u een lijn, kolom of cel wilt selecteren, klikt u er met de linkermuisknop op. Klik nogmaals om de selectie op te heffen.

![](assets/neolap_create_filter_from_selection.png)

Het filter wordt automatisch toegepast en aan de filterstreek boven het rapport toegevoegd.

![](assets/neolap_create_filter_display.png)

