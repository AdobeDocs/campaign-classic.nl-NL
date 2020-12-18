---
solution: Campaign Classic
product: campaign
title: Kubussen gebruiken om data te verkennen
description: Kubussen gebruiken om data te verkennen
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 2%

---


# Kubussen gebruiken om data te verkennen{#using-cubes-to-explore-data}

Met Marketing Analytics kunt u gemakkelijker rapporten maken en gegevens in de database identificeren en selecteren via kubussen. Hierdoor kunt u:

* Maak rapporten op basis van kubussen. Het proces wordt hier nader beschreven: [De gegevens in een rapport ontdekken](#exploring-the-data-in-a-report).
* Verzamel de gegevens in het gegevensbestand en groepeer het in lijsten, bijvoorbeeld om doelstellingen en leveringen te identificeren en te bouwen. Voor meer op dit, verwijs naar [Bouwend een doelpopulatie](#building-a-target-population).
* Voeg een draaitabel in een rapport in en verwijs naar een bestaande kubus in het rapport. Voor meer op dit, verwijs naar [Het opnemen van een spillijst in een rapport](#inserting-a-pivot-table-into-a-report).

>[!NOTE]
>
>Marketing Analytics is nodig om kubussen te maken of te wijzigen. Voor meer op dit, verwijs naar [Ongeveer kubussen](../../reporting/using/about-cubes.md).

## De gegevens in een rapport {#exploring-the-data-in-a-report} verkennen

### Stap 1 - het Creëren van een rapport dat op een kubus {#step-1---creating-a-report-based-on-a-cube} wordt gebaseerd

Als u een rapport wilt maken op basis van een kubus, klikt u op de knop **[!UICONTROL Create]** in het **[!UICONTROL Reports]** universum en selecteert u de kubus die u wilt gebruiken.

Het proces wordt hier nader beschreven: [Een rapport maken op basis van een kubus](../../reporting/using/creating-indicators.md#creating-a-report-based-on-a-cube).

### Stap 2 - Het selecteren van lijnen en kolommen {#step-2---selecting-lines-and-columns}

In de standaardweergave worden de eerste twee afmetingen van de kubus (in dit geval leeftijd en stad) weergegeven.

Met de **[!UICONTROL Add]** knoppen op elke as kunt u afmetingen toevoegen.

![](assets/s_advuser_cube_in_report_03.png)

1. Selecteer de afmetingen die u wilt weergeven in de lijnen en kolommen van de tabel. U doet dit door de beschikbare afmetingen te slepen en neer te zetten, zoals hieronder wordt weergegeven:
1. Selecteer in de lijst de afmetingen die u aan de tabel wilt toevoegen:

   ![](assets/s_advuser_cube_in_report_04.png)

1. Selecteer vervolgens de parameters van deze dimensie.

   ![](assets/s_advuser_cube_in_report_04b.png)

   De parameters zijn afhankelijk van het gegevenstype van de geselecteerde dimensie.

   Voor datums kunnen bijvoorbeeld verschillende niveaus beschikbaar zijn. Voor meer op dit, verwijs naar [Weergavemaatregelen](../../reporting/using/concepts-and-methodology.md#displaying-measures).

   In dit geval worden de volgende opties aangeboden:

   ![](assets/s_advuser_cube_in_report_config2.png)

   U kunt:

   * Gegevens uitbreiden tijdens laden: de waarden zullen door gebrek worden getoond telkens als het rapport wordt bijgewerkt (standaardwaarde: neen).
   * Het totaal aan het einde van de regel weergeven: wanneer de gegevens in kolommen worden weergegeven, kunt u het totaal aan het einde van de regel weergeven met een extra optie: er wordt een kolom aan de tabel toegevoegd (standaardwaarde): ja).
   * Een sortering toepassen: de waarden van de kolom kunnen worden gesorteerd op waarde, label of op basis van een maat (standaardwaarde: op waarde).
   * Geef de waarden weer in oplopende (a-z, 0-9) of aflopende (z-a, 9-0) volgorde.
   * Het aantal kolommen wijzigen dat bij het laden moet worden weergegeven (standaard: 200).

1. Klik **[!UICONTROL Ok]** om te bevestigen: de dimensie wordt toegevoegd aan de bestaande afmetingen.

   De gele banner boven de tabel geeft aan dat u wijzigingen hebt aangebracht: Klik op de knop **[!UICONTROL Save]** om de bestanden op te slaan.

   ![](assets/s_advuser_cube_in_report_04c.png)

### Stap 3 - Vormend de maatregelen om {#step-3---configuring-the-measures-to-display} te tonen

Wanneer de lijnen en kolommen op hun plaats zijn, wijs op de maatregelen u evenals hun vertoningswijze wilt tonen.

Standaard wordt slechts één maat weergegeven. Om maatregelen toe te voegen of te vormen:

1. Klik op de knop **[!UICONTROL Measures]**.

   ![](assets/s_advuser_cube_in_report_05.png)

1. Met de knop **[!UICONTROL Use a measure]** kunt u een van de bestaande maatregelen selecteren.

   ![](assets/s_advuser_cube_in_report_08.png)

   Selecteer de informatie die u wilt weergeven en het type opmaak. De lijst met opties is afhankelijk van het type maatregel dat is geconfigureerd.

   ![](assets/s_advuser_cube_in_report_09.png)

   De algemene maatconfiguratie is ook beschikbaar via het pictogram **[!UICONTROL Edit the configuration of the pivot table]** in de koptekst.

   ![](assets/s_advuser_cube_in_report_config_02.png)

   Vervolgens kunt u kiezen of u maatlabels wilt weergeven of niet. Voor meer op dit, verwijs naar [Het vormen van de vertoning](../../reporting/using/concepts-and-methodology.md#configuring-the-display).

1. Het is mogelijk om nieuwe maatregelen te bouwen gebruikend bestaande. Om dit te doen, klik **[!UICONTROL Create a measure]** en vorm het.

   ![](assets/s_advuser_cube_in_report_config_02a.png)

   De volgende soorten maatregelen zijn beschikbaar:

   * Combinatie van maatregelen: met dit type maatregel kunt u de nieuwe maatregel bouwen met behulp van bestaande maatregelen :

      De beschikbare operatoren zijn: som, verschil, vermenigvuldiging en frequentie.

   * Verhouding: met dit type maatregel kunt u het aantal records berekenen dat voor een bepaalde dimensie wordt gemeten. U kunt de evenredigheid berekenen op basis van een dimensie of subdimensie.
   * Variatie: met deze maatregel kunt u de variatie in waarden van een niveau berekenen.
   * Standaardafwijking: met dit type meting kunt u afwijkingen binnen elke groep cellen berekenen in vergelijking met het gemiddelde van de waarden . U kunt bijvoorbeeld het aankoopvolume voor alle bestaande segmenten vergelijken.

   De gecreëerde maatregel wordt toegevoegd aan het rapport.

   ![](assets/s_advuser_cube_in_report_config_02b.png)

   Nadat u een maatregel hebt gemaakt, kunt u deze bewerken en zo nodig de configuratie ervan wijzigen. Om dit te doen, klik **[!UICONTROL Measures]** knoop, dan ga naar het lusje van de maatregel u wilt uitgeven.

   Klik vervolgens op **[!UICONTROL Edit the dynamic measure]** om het instellingenmenu te openen.

## Een doelpopulatie opbouwen {#building-a-target-population}

De rapporten bouwen gebruikend kubussen laten u toe om gegevens van de lijst te verzamelen en het te bewaren in een lijst.

U doet dit door ze aan een winkelwagentje toe te voegen en de inhoud ervan te verwerken.

Als u een populatie in een lijst wilt groeperen, voert u de volgende stappen uit:

1. Klik op de cellen die de te verzamelen populatie bevatten en selecteer deze. Klik vervolgens op het pictogram **[!UICONTROL Add to cart]**.

   ![](assets/s_advuser_cube_in_report_config_02c.png)

   Om dit zo vaak nodig te doen om diverse profielen te verzamelen

1. Klik op de knop **[!UICONTROL Show cart]** om de inhoud ervan weer te geven voordat u het exporteren uitvoert.

   ![](assets/s_advuser_cube_in_report_config_02d.png)

1. Met de knop **[!UICONTROL Export]** kunt u de items in het winkelwagentje groeperen in een lijst.

   U moet de naam van de lijst opgeven en het type export dat u wilt uitvoeren.

   ![](assets/s-advuser_cube_in_report_config_02e.png)

   Klik op **[!UICONTROL Start]** om het exporteren uit te voeren.

1. Zodra de uitvoer volledig is, bevestigt een bericht zijn uitvoering en het aantal verslagen die zijn verwerkt.

   ![](assets/s_advuser_cube_in_report_config_02f.png)

   U kunt de inhoud van het winkelwagentje opslaan of leeg maken.

   De relevante lijst is toegankelijk via het universum **[!UICONTROL Profiles and targets]**.

   ![](assets/s_advuser_cube_in_report_config_02g.png)

## Een draaitabel invoegen in een rapport {#inserting-a-pivot-table-into-a-report}

Voer de volgende stappen uit om een tabel te maken en de gegevens in een kubus te verkennen:

1. Maak een nieuw rapport met één pagina en voeg er een draaitabel in. Raadpleeg [deze pagina](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table) voor meer informatie.

   ![](assets/s_advuser_cube_in_report_01.png)

1. Selecteer op het tabblad **[!UICONTROL Data]** van de pagina een kubus om de afmetingen ervan te verwerken en berekende metingen weer te geven.

   ![](assets/s_advuser_cube_in_report_02.png)

   Dit laat u het rapport bouwen dat moet worden getoond. Raadpleeg [Stap 2 - Lijnen en kolommen selecteren](#step-2---selecting-lines-and-columns) voor meer informatie.

