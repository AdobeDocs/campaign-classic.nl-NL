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
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 1%

---

# Exporttaken configureren {#executing-export-jobs}



Met de exporttaken hebt u toegang tot gegevens in de database en kunt u deze ophalen: contactpersonen, clients, lijsten, segmenten enzovoort.

Het kan bijvoorbeeld handig zijn om gegevens voor het bijhouden van campagnes te gebruiken (geschiedenis bijhouden, enz.) in een spreadsheet. De uitvoergegevens kunnen de indeling TXT, CSV, TAB of XML hebben.

Met de wizard Exporteren kunt u een exportbewerking configureren, de opties ervan definiëren en uitvoering starten. Het is een reeks schermen waarvan de inhoud afhankelijk is van het type export (eenvoudig of meervoudig) en de rechten van de operator.

De wizard Exporteren wordt weergegeven na het maken van een nieuwe exporttaak (zie [Import- en exporttaken maken](../../platform/using/creating-import-export-jobs.md).

## Stap 1 - Kies de exportsjabloon {#step-1---choosing-the-export-template}

Wanneer u de wizard Exporteren start, moet u eerst een sjabloon selecteren. Als voorbeeld, om de uitvoer van ontvangers te vormen die onlangs registreerden, volg de stappen hieronder:

1. Selecteer de **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** map.
1. Klikken **Nieuw** en klik vervolgens op **Exporteren** om de exportsjabloon te maken.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Klik op de pijl rechts van de knop **[!UICONTROL Export template]** te selecteren of klik op **[!UICONTROL Select link]** om door de boomstructuur te bladeren.

   De native sjabloon is **[!UICONTROL New text export]**. Deze sjabloon moet niet worden gewijzigd, maar u kunt het dupliceren om een nieuwe sjabloon te configureren. Exportsjablonen worden standaard opgeslagen in de **[!UICONTROL Resources > Templates > Job templates]** knooppunt.

1. Geef een naam op voor het exporteren in het dialoogvenster **[!UICONTROL Label]** veld. U kunt een beschrijving toevoegen.
1. Selecteer het exporttype. Er zijn twee mogelijke exporttypen: **[!UICONTROL Simple export]** slechts één bestand exporteren, en **[!UICONTROL Multiple export]** om meerdere bestanden in één uitvoering te exporteren, van een of meer typen brondocument.

## Stap 2 - Type bestand dat moet worden geëxporteerd {#step-2---type-of-file-to-export}

Selecteer het type document dat u wilt exporteren, dat wil zeggen het schema van de gegevens die u wilt exporteren.

Wanneer het exporteren wordt gestart vanuit de **[!UICONTROL Jobs]** knoop de gegevens komen uit de ontvankelijke lijst. Wanneer het exporteren wordt gestart vanuit een lijst met gegevens (van de **[!UICONTROL right click > Export]** (menu), wordt de tabel waartoe de gegevens behoren automatisch ingevuld in het dialoogvenster **[!UICONTROL Document type]** veld.

![](assets/s_ncs_user_export_wizard02.png)

* Standaard worden de **[!UICONTROL Download the file generated on the server after the export]** is geselecteerd. In de **[!UICONTROL Local file]** , vult de naam en het pad van het te maken bestand in of blader door de lokale schijf door op de map rechts van het veld te klikken. U kunt deze optie deselecteren om het toegangspad en de naam van het uitvoerbestand van de server in te voeren.

  >[!NOTE]
  >
  >Taken voor automatisch importeren en exporteren worden altijd op de server uitgevoerd.
  >
  >Als u slechts enkele gegevens wilt exporteren, klikt u op **[!UICONTROL Advanced parameters]** en voert u in het desbetreffende veld het aantal uit te voeren lijnen in.

* U kunt een differentiële exportbewerking maken om alleen records te exporteren die sinds de laatste uitvoering zijn gewijzigd. Om dit te doen, klik **[!UICONTROL Advanced parameters]** klikt u op de koppeling **[!UICONTROL Differential export]** tab, dan selecteren **[!UICONTROL Activate differential export]**.

  ![](assets/s_ncs_user_export_wizard02_b.png)

  U moet de datum van de laatste wijziging invoeren. Deze kan worden opgehaald uit een veld of berekend.

## Stap 3 - Bepaal de outputformaat {#step-3---defining-the-output-format}

Selecteer een uitvoerindeling voor het exportbestand. De volgende indelingen kunnen worden gebruikt: tekst, tekst met een vaste kolom, CSV en XML.

![](assets/s_ncs_user_export_wizard03.png)

* Voor **[!UICONTROL Text]** , selecteert u de scheidingstekens om de kolommen (tabs, komma&#39;s, puntkomma&#39;s of aangepaste tekens) en de tekenreeksen (enkele of dubbele aanhalingstekens of geen) van elkaar te scheiden.
* Voor **[!UICONTROL text]** en **[!UICONTROL CSV]**, kunt u de optie selecteren **[!UICONTROL Use first lines as column titles]**.
* Geef de datumnotatie en getalnotatie op. Om dit te doen, klik **[!UICONTROL Edit]** voor het betrokken gebied en gebruik de redacteur.
* Voor velden met opsommingswaarden kunt u **[!UICONTROL Export labels instead of internal values of enumerations]**. De titel kan bijvoorbeeld in het formulier worden opgeslagen **1=Mr.**, **2=Miss**, **3=Mevrouw**. Als deze optie is geselecteerd, **Dhr.**, **Mevrouw** en **Mevrouw** wordt geëxporteerd.

## Stap 4 - Selectie van gegevens {#step-4---data-selection}

Selecteer de te exporteren velden. Dit doet u als volgt:

1. Dubbelklik op de gewenste velden in het dialoogvenster **[!UICONTROL Available fields]** om deze aan de **[!UICONTROL Output columns]** sectie.
1. Gebruik de pijlen rechts van de lijst om de volgorde van de velden in het uitvoerbestand te definiëren.

   ![](assets/s_ncs_user_export_wizard04.png)

1. Klik op de knop **[!UICONTROL Add]** om functies aan te roepen. Raadpleeg voor meer informatie hierover [Lijst met functies](../../platform/using/defining-filter-conditions.md#list-of-functions).

## Stap 5 - Kolommen sorteren {#step-5---sorting-columns}

Selecteer de sorteervolgorde van de kolommen.

![](assets/s_ncs_user_export_wizard05.png)

## Stap 6 - Filtervoorwaarden {#step-6---filter-conditions-}

U kunt filtervoorwaarden toevoegen om het exporteren van alle gegevens te voorkomen. De configuratie van dit het filtreren is het zelfde als ontvankelijke het richten in de leveringstovenaar. Zie [deze pagina](../../delivery/using/steps-defining-the-target-population.md).

![](assets/s_ncs_user_export_wizard05_b.png)

## Stap 7 - Gegevensopmaak {#step-7---data-formatting}

U kunt de volgorde en het label van de velden voor het uitvoerbestand wijzigen en transformaties op de brongegevens toepassen.

* Als u de volgorde van de kolommen die u wilt exporteren wilt wijzigen, selecteert u de desbetreffende kolom en gebruikt u de blauwe pijlen rechts van de tabel.
* Als u het label van een veld wilt wijzigen, klikt u in de cel van het dialoogvenster **[!UICONTROL Label]** de kolom die overeenkomt met het veld dat moet worden gewijzigd, en voert u het nieuwe label in. Druk op Enter op het toetsenbord om te bevestigen.
* Als u een hoofdlettertransformatie wilt toepassen op de inhoud van een veld, selecteert u deze in het menu **[!UICONTROL Transformation]** kolom. U kunt selecteren:

   * Overschakelen naar kleine letters
   * Overschakelen naar hoofdletters
   * Eerste letter in hoofdletters

  ![](assets/s_ncs_user_export_wizard06.png)

* Klikken **[!UICONTROL Add a calculated field]** als u een nieuw berekend veld wilt maken (bijvoorbeeld een kolom met achternaam + voornaam). Raadpleeg voor meer informatie hierover [Berekende velden](../../platform/using/executing-import-jobs.md#calculated-fields).

Als u een verzameling elementen exporteert (bijvoorbeeld abonnementen van ontvangers, lijsten waartoe ze behoren, enz.), moet u het aantal elementen in de verzameling opgeven dat u wilt exporteren.

![](assets/s_ncs_user_export_wizard06_c.png)

## Stap 8 - Voorvertoning gegevens {#step-8---data-preview}

Klikken **[!UICONTROL Start the preview of the data]** voor een voorvertoning van het exportresultaat. Standaard worden de eerste 200 regels weergegeven. Als u deze waarde wilt wijzigen, klikt u op de pijlen rechts van het **[!UICONTROL Lines to display]** veld.

![](assets/s_ncs_user_export_wizard07.png)

Klik op de tabbladen onder aan de wizard om te schakelen van de voorvertoning van de resultaten in kolommen naar de resultaten in XML. U kunt de gegenereerde SQL-query&#39;s ook weergeven.

## Stap 9 - Het exporteren starten {#step-9---launching-the-export}

Klikken **[!UICONTROL Start]** om het exporteren van gegevens te starten.

![](assets/s_ncs_user_export_wizard08.png)

U kunt vervolgens de uitvoering van de importtaak controleren (zie [Uitvoering van taken controleren](../../platform/using/monitoring-jobs-execution.md).
