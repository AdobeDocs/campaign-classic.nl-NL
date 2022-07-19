---
product: campaign
title: Gegevens laden (bestand)
description: Meer informatie over de activiteiten in de workflow voor het laden van gegevens (bestanden)
feature: Workflows, Data Management Activity
exl-id: a380e486-a40c-4bf6-b7f4-7dcd76c34085
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 15%

---

# Gegevens laden (bestand){#data-loading-file}

![](../../assets/v7-only.svg)

## Gebruiken {#use}

De **[!UICONTROL Data loading (File)]** Met deze activiteit hebt u rechtstreeks toegang tot een bron met externe gegevens en kunt u deze gebruiken in Adobe Campaign. Alle gegevens die vereist zijn voor bewerkingen met het doel als doel, worden niet altijd gevonden in de Adobe Campaign-database: het kan in externe dossiers ter beschikking worden gesteld.

Het bestand dat moet worden geladen, kan worden opgegeven door de overgang of worden berekend tijdens de uitvoering van deze activiteit. Bijvoorbeeld, kan het de lijst van 10 favoriete producten van een cliënt zijn de waarvan aankopen in een extern gegevensbestand worden beheerd.

In het bovenste gedeelte van het configuratievenster voor deze activiteit kunt u de bestandsindeling definiëren. Hiervoor gebruikt u een voorbeeldbestand met dezelfde indeling als het bestand dat u wilt importeren. Dit bestand kan lokaal of op de server worden opgeslagen.

>[!CAUTION]
>
>Alleen &#39;platte&#39; structuurbestanden worden ondersteund (bijvoorbeeld CSV, TXT, enz.). Het gebruik van de XML-indeling wordt afgeraden.

![](assets/s_advuser_wf_etl_file.png)

U kunt een vooraf uitgevoerd proces definiëren tijdens het importeren van bestanden, bijvoorbeeld om het bestand niet op de server uit te pakken (en dus ruimte voor het uitgepakt bestand op te slaan) maar om het uitpakken op te nemen in de bestandsverwerking. Selecteer **[!UICONTROL Pre-process the file]** en kies een van de drie opties: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) of **[!UICONTROL Decrypt]** (gpg).

![](assets/preprocessing-dataloading.png)

Raadpleeg voor meer informatie deze sectie: [Een bestand decoderen of decoderen voordat het wordt verwerkt](../../platform/using/unzip-decrypt.md).

## De bestandsindeling definiëren {#defining-the-file-format}

Wanneer u een bestand laadt, wordt de kolomindeling automatisch gedetecteerd met de standaardparameters voor elk gegevenstype. U kunt deze standaardparameters wijzigen om de specifieke processen op te geven die op uw data moeten worden toegepast, in het bijzonder wanneer er een fout of een lege waarde is.

Selecteer **[!UICONTROL Click here to change the file format...]** in het hoofdvenster van het **[!UICONTROL Data loading (file)]** activiteit. Het venster met de indelingsdetails wordt dan geopend.

![](assets/file_loading_columns_format.png)

Vervolgens kunt u de algemene opmaak van het bestand en de opmaak van elke kolom wijzigen.

Met de algemene bestandsindeling kunt u bepalen hoe de kolommen worden herkend (bestandencodering, gebruikte scheidingstekens, enz.).

Met de kolomopmaak kunt u de waardeverwerking van elke kolom definiëren:

* **[!UICONTROL Ignore column]**: Deze kolom wordt niet verwerkt tijdens het laden van data.
* **[!UICONTROL Data type]**: Deze geeft het type data op dat voor elke kolom wordt verwacht.
* **[!UICONTROL Allow NULLs]**: geeft aan hoe lege waarden moeten worden beheerd.

   * **[!UICONTROL Adobe Campaign default]**: Dit genereert alleen een fout voor numerieke velden. Als dit niet het geval is, wordt een NULL-waarde ingevoegd.
   * **[!UICONTROL Empty value allowed]**: Dit autoriseert lege waarden. De waarde NULL wordt daarom ingevoegd.
   * **[!UICONTROL Always populated]**: Dit genereert een fout als een waarde leeg is.

* **[!UICONTROL Length]**: geeft het maximumaantal tekens voor de **string** gegevenstype.
* **[!UICONTROL Format]**: definieert de notatie voor tijd en datum.
* **[!UICONTROL Data transformation]**: bepaalt of een proces van het karaktergeval op een **string**.

   * **[!UICONTROL None]**: de geïmporteerde tekenreeks wordt niet gewijzigd.
   * **[!UICONTROL First letter in upper case]**: De eerste letter van elk woord van de tekenreeks begint met een hoofdletter.
   * **[!UICONTROL Upper case]**: alle tekens in de tekenreeks zijn in hoofdletters weergegeven.
   * **[!UICONTROL Lower case]**: alle tekens in de tekenreeks zijn in kleine letters weergegeven.

* **[!UICONTROL White space management]**: Geeft aan of bepaalde spaties in een tekenreeks moeten worden genegeerd. De **[!UICONTROL Ignore spaces]** Met waarde kunnen spaties alleen aan het begin en het einde van een tekenreeks worden genegeerd.
* **[!UICONTROL Error processings]**: Dit definieert het gedrag als een fout optreedt.

   * **[!UICONTROL Ignore the value]**: De waarde wordt genegeerd. Er wordt een waarschuwing gegenereerd in het logboek voor workflowuitvoering.
   * **[!UICONTROL Reject line]**: De volledige regel wordt niet verwerkt.
   * **[!UICONTROL Use a default value in case of error]**: Dit vervangt de waarde die de fout veroorzaakt door een standaardwaarde, die in het veld **[!UICONTROL Default value]** is gedefinieerd.
   * **[!UICONTROL Reject the line when there is no remapping value]**: de gehele lijn wordt alleen verwerkt als een toewijzing voor de onjuiste waarde is gedefinieerd (zie **[!UICONTROL Mapping]** hieronder).
   * **[!UICONTROL Use a default value in case the value is not remapped]**: vervangt de waarde die de fout veroorzaakt door een standaardwaarde, die in **[!UICONTROL Default value]** veld, tenzij een toewijzing voor de onjuiste waarde is gedefinieerd (zie de **[!UICONTROL Mapping]** hieronder).

* **[!UICONTROL Default value]**: Hiermee geeft u de standaardwaarde op op basis van de gekozen foutverwerking.
* **[!UICONTROL Mapping]**: dit veld is alleen beschikbaar in de configuratie van de kolomdetails (toegankelijk via een dubbelklik of via de opties rechts van de kolomlijst). Hiermee worden bepaalde waarden getransformeerd wanneer ze worden geïmporteerd. U kunt bijvoorbeeld ‘three’ omzetten in ‘3’.

## Voorbeeld: Gegevens verzamelen en laden in de database {#example--collecting-data-and-loading-it-in-the-database}

In het volgende voorbeeld kunt u elke dag een bestand op de server verzamelen, de inhoud van het bestand laden en de gegevens in de database bijwerken, afhankelijk van de informatie die het bevat. Het te verzamelen bestand bevat informatie over klanten die mogelijk aankopen hebben gedaan (voor meer of minder dan 3000 euro), om terugbetaling hebben gevraagd bij een aankoop of de winkel hebben bezocht zonder iets te kopen. Afhankelijk van deze informatie worden verschillende processen toegepast op hun profiel in de database.

![](assets/s_advuser_load_file_sample_0.png)

1. Met de bestandscollector kunt u bestanden herstellen die in een map zijn opgeslagen, afhankelijk van de opgegeven frequentie.

   De **[!UICONTROL Directory]** bevat informatie over het terug te winnen bestand of de bestanden. In ons voorbeeld worden alle bestanden in tekstopmaak waarvan de namen het woord &#39;klanten&#39; bevatten en die zijn opgeslagen in de map tmp/Adobe/Data/files van de server, hersteld.

   Met de **[!UICONTROL File collector]** wordt in het [Bestandsverzamelaar](file-collector.md) sectie.

   ![](assets/s_advuser_load_file_sample_1.png)

   De **[!UICONTROL Schedule]** kunt u de uitvoering van de verzamelaar plannen, met andere woorden de frequentie opgeven waarmee de aanwezigheid van deze bestanden wordt gecontroleerd.

   Hier, willen wij de inzamelaar elke werkdag teweegbrengen om 9PM.

   ![](assets/s_advuser_load_file_sample_2.png)

   Om dit te doen, klik **[!UICONTROL Change...]** in de lagere rechtersectie van het het uitgeven hulpmiddel wordt gevestigd en vorm het programma dat.

   Raadpleeg voor meer informatie hierover [Planner](scheduler.md).

1. Configureer vervolgens de activiteit voor het laden van gegevens (bestand) om aan te geven hoe de verzamelde bestanden moeten worden gelezen. Selecteer hiertoe een voorbeeldbestand met dezelfde structuur als de bestanden die u wilt laden.

   ![](assets/s_advuser_load_file_sample_3.png)

   Hier bevat het bestand vijf kolommen:

   * de eerste kolom bevat een code die samenvalt met de gebeurtenis: aankoop (meer of minder dan 3000 euro), geen aankoop of terugbetaling voor een of meer aankopen.
   * de vier volgende kolommen bevatten de voornaam, achternaam, e-mail en het rekeningnummer van de klant.

   De indelingsconfiguratie van het te laden bestand valt samen met de configuratie die is gedefinieerd tijdens het importeren van gegevens in Adobe Campaign. Raadpleeg deze [sectie](../../platform/using/executing-import-jobs.md#step-2---source-file-selection) voor meer informatie.

1. Geef in de splitsingsactiviteit de subsets op die u wilt maken, volgens de **Gebeurtenis** kolomwaarde.

   De activiteit Splitsen wordt gedetailleerd beschreven in de sectie.

   ![](assets/s_advuser_load_file_sample_4.png)

   Geef voor elke subset een van de waarden op in het dialoogvenster **Gebeurtenis** kolom.

   ![](assets/s_advuser_load_file_sample_5.png)

   De **[!UICONTROL Split]** de activiteit zal derhalve de volgende informatie bevatten :

   ![](assets/s_advuser_load_file_sample_6.png)

1. Geef vervolgens aan welke processen voor elk type bevolking moeten worden uitgevoerd. In ons voorbeeld gaan we **[!UICONTROL Update the data]** in de database. Om dit te doen, plaats een **[!UICONTROL Update data]** activiteit aan het eind van elke uitgaande overgang van de splitsingsactiviteit.

   De **[!UICONTROL Update data]** de activiteit wordt in de [Gegevens bijwerken](update-data.md) sectie.
