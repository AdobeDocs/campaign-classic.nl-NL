---
title: Gegevens exporteren
seo-title: Gegevens exporteren
description: Gegevens exporteren
seo-description: null
page-status-flag: never-activated
uuid: 818de79a-587f-4735-b333-4bc702c3b450
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: fecadb66-b81d-4fb6-9971-7bfd024d70b7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# Gegevens exporteren{#exporting-data}

## Wizard Exporteren {#export-wizard}

De exportparameters worden opgenomen via een wizard. De algemene exportmodule is standaard beschikbaar en u kunt gegevens uit de database ophalen en benaderen: contacten, cliënten, lijsten, segmenten, enz. Het kan bijvoorbeeld handig zijn om gegevens voor het bijhouden van campagnes te gebruiken (geschiedenis bijhouden, enz.) in een spreadsheet. De uitvoergegevens kunnen de indeling TXT, CSV, TAB of XML hebben.

### Stap 1 - De exportsjabloon kiezen {#step-1---choosing-the-export-template}

Wanneer u de wizard Exporteren start, moet u eerst een sjabloon selecteren. Als voorbeeld, om de uitvoer van ontvangers te vormen die onlangs registreerden, volg de stappen hieronder:

1. Selecteer de **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** map.
1. Klik op **Nieuw** en vervolgens op **Exporteren** om de exportsjabloon te maken.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Klik op de pijl rechts van het **[!UICONTROL Export template]** veld om de sjabloon te selecteren of klik **[!UICONTROL Select link]** om door de structuur te bladeren.

   De native sjabloon is **[!UICONTROL New text export]**. Deze sjabloon moet niet worden gewijzigd, maar u kunt het dupliceren om een nieuwe sjabloon te configureren. Standaard worden exportsjablonen opgeslagen in het **[!UICONTROL Resources > Templates > Job templates]** knooppunt.

1. Voer in het **[!UICONTROL Label]** veld een naam in voor het exporteren. U kunt een beschrijving toevoegen.
1. Selecteer het exporttype. Er zijn twee mogelijke exporttypen: **[!UICONTROL Simple export]** **[!UICONTROL Multiple export]** om slechts één bestand te exporteren en meerdere bestanden in één uitvoering te exporteren, van een of meer typen brondocument.

### Stap 2 - Type bestand dat moet worden geëxporteerd {#step-2---type-of-file-to-export}

Selecteer het type document dat u wilt exporteren, dat wil zeggen het schema van de gegevens die u wilt exporteren.

Wanneer het exporteren wordt gestart vanuit het **[!UICONTROL Jobs]** knooppunt, komen de gegevens standaard uit de tabel met ontvangers. Wanneer het exporteren wordt gestart vanuit een lijst met gegevens (vanuit het **[!UICONTROL right click > Export]** menu), wordt de tabel waartoe de gegevens behoren automatisch ingevuld in het **[!UICONTROL Document type]** veld.

![](assets/s_ncs_user_export_wizard02.png)

* Standaard is de **[!UICONTROL Download the file generated on the server after the export]** optie geselecteerd. Vul in het **[!UICONTROL Local file]** veld de naam en het pad in van het bestand dat u wilt maken, of blader door de lokale schijf door op de map rechts van het veld te klikken. U kunt deze optie deselecteren om het toegangspad en de naam van het uitvoerbestand van de server in te voeren.

   >[!NOTE]
   >
   >Taken voor automatisch importeren en exporteren worden altijd op de server uitgevoerd.
   >
   >Als u slechts een deel van de gegevens wilt exporteren, klikt u **[!UICONTROL Advanced parameters]** en voert u in het desbetreffende veld het aantal regels in dat u wilt exporteren.

* U kunt een differentiële exportbewerking maken om alleen records te exporteren die sinds de laatste uitvoering zijn gewijzigd. Klik hiertoe op de **[!UICONTROL Advanced parameters]** koppeling, klik vervolgens op de **[!UICONTROL Differential export]** tab en selecteer **[!UICONTROL Activate differential export]**.

   ![](assets/s_ncs_user_export_wizard02_b.png)

   U moet de datum van de laatste wijziging invoeren. Deze kan worden opgehaald uit een veld of berekend.

### Stap 3 - De uitvoerindeling definiëren {#step-3---defining-the-output-format}

Selecteer een uitvoerindeling voor het exportbestand. De volgende indelingen kunnen worden gebruikt: tekst, tekst in vaste kolommen, CSV en XML.

![](assets/s_ncs_user_export_wizard03.png)

* Selecteer bij **[!UICONTROL Text]** opmaak de scheidingstekens voor het scheiden van de kolommen (tabs, komma&#39;s, puntkomma&#39;s of aangepaste tekens) en de tekenreeksen (enkele of dubbele aanhalingstekens of geen).
* Voor **[!UICONTROL text]** en **[!UICONTROL CSV]**, kunt u de optie selecteren **[!UICONTROL Use first lines as column titles]**.
* Geef de datumnotatie en getalnotatie op. Klik hiertoe op de **[!UICONTROL Edit]** knop voor het desbetreffende veld en gebruik de editor.
* Voor velden met opsommingswaarden kunt u **[!UICONTROL Export labels instead of internal values of enumerations]** selecteren. De titel kan bijvoorbeeld worden opgeslagen in de notatie **1=Mr.**, **2=Miss**,** 3=Mevrouw**. Als deze optie wordt gekozen, worden **meneer**, **mevrouw** en **mevrouw** geëxporteerd.

### Stap 4 - Selectie van gegevens {#step-4---data-selection}

Selecteer de velden die u wilt exporteren. Dit doet u als volgt:

1. Dubbelklik op de gewenste velden in de **[!UICONTROL Available fields]** lijst om deze aan de **[!UICONTROL Output columns]** sectie toe te voegen.
1. Gebruik de pijlen rechts van de lijst om de volgorde van de velden in het uitvoerbestand te definiëren.

   ![](assets/s_ncs_user_export_wizard04.png)

1. Klik op de **[!UICONTROL Add]** knop om functies aan te roepen. Zie [Lijst met functies](../../platform/using/defining-filter-conditions.md#list-of-functions)voor meer informatie hierover.

### Stap 5 - Kolommen sorteren {#step-5---sorting-columns}

Selecteer de sorteervolgorde van de kolommen.

![](assets/s_ncs_user_export_wizard05.png)

### Stap 6 - Filtervoorwaarden {#step-6---filter-conditions-}

U kunt filtervoorwaarden toevoegen om te voorkomen dat alle gegevens worden geëxporteerd. De configuratie van dit het filtreren is het zelfde als ontvankelijke het richten in de leveringstovenaar. Zie [deze pagina](../../delivery/using/steps-defining-the-target-population.md).

![](assets/s_ncs_user_export_wizard05_b.png)

### Stap 7 - Gegevensopmaak {#step-7---data-formatting}

U kunt de volgorde en het label van de velden voor het uitvoerbestand wijzigen en transformaties op de brongegevens toepassen.

* Als u de volgorde van de kolommen die u wilt exporteren wilt wijzigen, selecteert u de desbetreffende kolom en gebruikt u de blauwe pijlen rechts van de tabel.
* Als u het label van een veld wilt wijzigen, klikt u in de cel van de **[!UICONTROL Label]** kolom die overeenkomt met het te wijzigen veld en voert u het nieuwe label in. Druk op Enter op het toetsenbord om te bevestigen.
* Als u een hoofdlettertransformatie wilt toepassen op de inhoud van een veld, selecteert u deze in de **[!UICONTROL Transformation]** kolom. U kunt selecteren:

   * Overschakelen naar kleine letters
   * Overschakelen naar hoofdletters
   * Eerste letter in hoofdletters
   ![](assets/s_ncs_user_export_wizard06.png)

* Klik **[!UICONTROL Add a calculated field]** als u een nieuw berekend veld wilt maken (bijvoorbeeld een kolom met achternaam + voornaam). Zie [Berekende velden](../../platform/using/importing-data.md#calculated-fields)voor meer informatie.

Als u een verzameling elementen exporteert (bijvoorbeeld abonnementen van ontvangers, lijsten waartoe ze behoren, enz.), moet u het aantal elementen in de verzameling opgeven dat u wilt exporteren.

![](assets/s_ncs_user_export_wizard06_c.png)

### Stap 8 - Voorvertoning van gegevens {#step-8---data-preview}

Klik **[!UICONTROL Start the preview of the data]** voor een voorvertoning van het exportresultaat. Standaard worden de eerste 200 regels weergegeven. Als u deze waarde wilt wijzigen, klikt u op de pijlen rechts van het **[!UICONTROL Lines to display]** veld.

![](assets/s_ncs_user_export_wizard07.png)

Klik op de tabbladen onder aan de wizard om te schakelen van de voorvertoning van de resultaten in kolommen naar de resultaten in XML. U kunt de gegenereerde SQL-query&#39;s ook weergeven.

### Stap 9 - Het exporteren starten {#step-9---launching-the-export}

Klik **[!UICONTROL Start]** om het exporteren van gegevens te starten.

![](assets/s_ncs_user_export_wizard08.png)

## Gegevens exporteren via een workflow {#exporting-data-via-a-workflow}

Workflows kunnen een handige manier zijn om een aantal exportprocessen te automatiseren of om nauwkeurige sets gegevens te exporteren nadat u een aantal van de beschikbare activiteiten voor gegevensbeheer hebt gebruikt om uw gegevens te transformeren.

Raadpleeg [deze sectie](../../workflow/using/how-to-use-workflow-data.md)voor meer informatie over het exporteren van gegevens uit een workflow.
