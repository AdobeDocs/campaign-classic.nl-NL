---
product: campaign
title: Exporttaken configureren
description: Leer hoe u exporttaken configureert en uitvoert in Campagne
feature: Overview
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 94fc473a-dc49-41e8-b572-51c162b09996
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 1%

---

# Exporttaken configureren {#executing-export-jobs}



Met de exporttaken hebt u toegang tot gegevens in de database en kunt u deze ophalen: contactpersonen, clients, lijsten, segmenten enzovoort.

Het kan bijvoorbeeld handig zijn om gegevens voor het bijhouden van campagnes te gebruiken (geschiedenis bijhouden, enz.) in een spreadsheet. De uitvoergegevens kunnen de indeling TXT, CSV, TAB of XML hebben.

Met de exportassistent kunt u een exportbewerking configureren, opties definiëren en uitvoering starten. Het is een reeks schermen waarvan de inhoud afhankelijk is van het type export (eenvoudig of meervoudig) en de rechten van de operator.

De vertoningen van de uitvoermedewerker na het creëren van een nieuwe de uitvoerbaan (zie [ invoer en de uitvoerbanen ](../../platform/using/creating-import-export-jobs.md) creëren.

## Stap 1 - Kies de exportsjabloon {#step-1---choosing-the-export-template}

Wanneer u de exportassistent start, moet u eerst een sjabloon selecteren. Als voorbeeld, om de uitvoer van ontvangers te vormen die onlangs registreerden, volg de stappen hieronder:

1. Selecteer de map **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** .
1. Klik **Nieuw** en klik dan **Uitvoer** om het uitvoermalplaatje tot stand te brengen.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Klik op de pijl rechts van het veld **[!UICONTROL Export template]** om de sjabloon te selecteren of klik op **[!UICONTROL Select link]** om door de structuur te bladeren.

   De native sjabloon is **[!UICONTROL New text export]** . Deze sjabloon moet niet worden gewijzigd, maar u kunt het dupliceren om een nieuwe sjabloon te configureren. Exportsjablonen worden standaard opgeslagen in het knooppunt **[!UICONTROL Resources > Templates > Job templates]** .

1. Voer in het veld **[!UICONTROL Label]** een naam in voor het exporteren. U kunt een beschrijving toevoegen.
1. Selecteer het exporttype. Er zijn twee mogelijke exporttypen: **[!UICONTROL Simple export]** om slechts één bestand te exporteren en **[!UICONTROL Multiple export]** om meerdere bestanden in één uitvoering uit een of meer typen brondocument te exporteren.

## Stap 2 - Type bestand dat moet worden geëxporteerd {#step-2---type-of-file-to-export}

Selecteer het type document dat u wilt exporteren, dat wil zeggen het schema van de gegevens die u wilt exporteren.

Wanneer het exporteren wordt gestart vanuit het knooppunt **[!UICONTROL Jobs]** , komen de gegevens standaard uit de tabel met ontvangers. Wanneer het exporteren wordt gestart vanuit een lijst met gegevens (vanuit het menu **[!UICONTROL right click > Export]** ), wordt de tabel waartoe de gegevens behoren automatisch ingevuld in het veld **[!UICONTROL Document type]** .

![](assets/s_ncs_user_export_wizard02.png)

* Standaard is de optie **[!UICONTROL Download the file generated on the server after the export]** geselecteerd. Vul in het veld **[!UICONTROL Local file]** de naam en het pad in van het bestand dat u wilt maken, of blader door de lokale schijf door op de map rechts van het veld te klikken. U kunt deze optie deselecteren om het toegangspad en de naam van het uitvoerbestand van de server in te voeren.

  >[!NOTE]
  >
  >Taken voor automatisch importeren en exporteren worden altijd op de server uitgevoerd.
  >
  >Als u slechts enkele gegevens wilt exporteren, klikt u op **[!UICONTROL Advanced parameters]** en voert u in het desbetreffende veld het aantal regels in dat u wilt exporteren.

* U kunt een differentiële exportbewerking maken om alleen records te exporteren die sinds de laatste uitvoering zijn gewijzigd. Klik hiertoe op de koppeling **[!UICONTROL Advanced parameters]** , klik vervolgens op de tab **[!UICONTROL Differential export]** en selecteer **[!UICONTROL Activate differential export]** .

  ![](assets/s_ncs_user_export_wizard02_b.png)

  U moet de datum van de laatste wijziging invoeren. Deze kan worden opgehaald uit een veld of berekend.

## Stap 3 - Bepaal de outputformaat {#step-3---defining-the-output-format}

Selecteer een uitvoerindeling voor het exportbestand. De volgende indelingen kunnen worden gebruikt: tekst, tekst met een vaste kolom, CSV en XML.

![](assets/s_ncs_user_export_wizard03.png)

* Selecteer bij de notatie **[!UICONTROL Text]** de scheidingstekens tussen de kolommen (tabs, komma&#39;s, puntkomma&#39;s of aangepast) en de tekenreeksen (enkele of dubbele aanhalingstekens of geen).
* Voor **[!UICONTROL text]** en **[!UICONTROL CSV]** kunt u de optie **[!UICONTROL Use first lines as column titles]** selecteren.
* Geef de datumnotatie en getalnotatie op. Klik hiertoe op de knop **[!UICONTROL Edit]** voor het desbetreffende veld en gebruik de editor.
* Voor velden met opsommingswaarden kunt u **[!UICONTROL Export labels instead of internal values of enumerations]** selecteren. Bijvoorbeeld, kan de titel in de vorm **worden opgeslagen 1=Mr.**, **2=Onjuffrouw**, **3=Mevrouw.**. Als deze optie wordt geselecteerd, **Mr.**, **juf** en **mevrouw** zal worden uitgevoerd.

## Stap 4 - Selectie van gegevens {#step-4---data-selection}

Selecteer de te exporteren velden. Dit doet u als volgt:

1. Dubbelklik op de gewenste velden in de lijst **[!UICONTROL Available fields]** om deze toe te voegen aan de sectie **[!UICONTROL Output columns]** .
1. Gebruik de pijlen rechts van de lijst om de volgorde van de velden in het uitvoerbestand te definiëren.

   ![](assets/s_ncs_user_export_wizard04.png)

1. Klik op de knop **[!UICONTROL Add]** om functies aan te roepen. Voor meer op dit, verwijs naar [ Lijst van functies ](../../platform/using/defining-filter-conditions.md#list-of-functions).

## Stap 5 - Kolommen sorteren {#step-5---sorting-columns}

Selecteer de sorteervolgorde van de kolommen.

![](assets/s_ncs_user_export_wizard05.png)

## Stap 6 - Filtervoorwaarden {#step-6---filter-conditions-}

U kunt filtervoorwaarden toevoegen om het exporteren van alle gegevens te voorkomen. De configuratie van dit het filtreren is het zelfde als ontvankelijke het richten in de leveringsmedewerker. Zie [deze pagina](../../delivery/using/steps-defining-the-target-population.md).

![](assets/s_ncs_user_export_wizard05_b.png)

## Stap 7 - Gegevensopmaak {#step-7---data-formatting}

U kunt de volgorde en het label van de velden voor het uitvoerbestand wijzigen en transformaties op de brongegevens toepassen.

* Als u de volgorde van de kolommen die u wilt exporteren wilt wijzigen, selecteert u de desbetreffende kolom en gebruikt u de blauwe pijlen rechts van de tabel.
* Als u het label van een veld wilt wijzigen, klikt u in de cel van de kolom **[!UICONTROL Label]** die overeenkomt met het veld dat u wilt wijzigen, en voert u het nieuwe label in. Druk op Enter op het toetsenbord om te bevestigen.
* Als u een hoofdlettertransformatie wilt toepassen op de inhoud van een veld, selecteert u deze in de kolom **[!UICONTROL Transformation]** . U kunt selecteren:

   * Overschakelen naar kleine letters
   * Overschakelen naar hoofdletters
   * Eerste letter in hoofdletters

  ![](assets/s_ncs_user_export_wizard06.png)

* Klik op **[!UICONTROL Add a calculated field]** als u een nieuw berekend veld wilt maken (bijvoorbeeld een kolom met de achternaam en de voornaam). Voor meer op dit, verwijs naar [ Berekende gebieden ](../../platform/using/executing-import-jobs.md#calculated-fields).

Als u een verzameling elementen exporteert (bijvoorbeeld abonnementen van ontvangers, lijsten waartoe ze behoren, enz.), moet u het aantal elementen in de verzameling opgeven dat u wilt exporteren.

![](assets/s_ncs_user_export_wizard06_c.png)

## Stap 8 - Voorvertoning gegevens {#step-8---data-preview}

Klik op **[!UICONTROL Start the preview of the data]** voor een voorvertoning van het exportresultaat. Standaard worden de eerste 200 regels weergegeven. Als u deze waarde wilt wijzigen, klikt u op de pijlen rechts van het veld **[!UICONTROL Lines to display]** .

![](assets/s_ncs_user_export_wizard07.png)

Klik de lusjes bij de bodem van de medewerker om van de voorproef van resultaten in kolommen aan de resultaten in XML over te schakelen. U kunt de gegenereerde SQL-query&#39;s ook weergeven.

## Stap 9 - Het exporteren starten {#step-9---launching-the-export}

Klik op **[!UICONTROL Start]** om het exporteren van gegevens te starten.

![](assets/s_ncs_user_export_wizard08.png)

U kunt de uitvoering van de de invoerbaan dan controleren (zie [ de baanuitvoering van de Monitor ](../../platform/using/monitoring-jobs-execution.md).
