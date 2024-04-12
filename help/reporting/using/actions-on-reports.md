---
product: campaign
title: Acties voor rapporten
description: Acties voor rapporten
feature: Reporting, Monitoring
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 3%

---

# Acties voor rapporten{#actions-on-reports}



Wanneer u een rapport weergeeft, kunt u op de werkbalk een bepaald aantal handelingen uitvoeren. Deze worden hieronder beschreven.

![](assets/s_ncs_advuser_report_wizard_2.png)

Met de werkbalk kunt u het rapport bijvoorbeeld exporteren, afdrukken, archiveren of weergeven in een webbrowser.

![](assets/s_ncs_advuser_report_wizard_04.png)

## Een rapport exporteren {#exporting-a-report}

Selecteer de indeling waarin u het rapport wilt exporteren in de vervolgkeuzelijst. (.xls, .pdf of .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

Wanneer een rapport meerdere pagina&#39;s bevat, moet u de bewerking voor elke pagina herhalen.

U kunt uw rapport vormen met het oog op het uitvoeren van het in PDF, formaat Excel of formaat OpenOffice. Open de explorator van Adobe Campaign en selecteer het betrokken rapport.

Exportopties zijn toegankelijk via de **[!UICONTROL Page]** activiteiten van het verslag, in het **[!UICONTROL Advanced]** tab.

De instellingen wijzigen van **[!UICONTROL Paper]** en **[!UICONTROL Margins]** aan uw behoeften te voldoen. U kunt het exporteren van een pagina ook alleen in de indeling PDF toestaan. Om dit te doen, uncheck **[!UICONTROL Activate OpenOffice/Microsoft Excel export]** -optie.

![](assets/s_ncs_advuser_report_wizard_021.png)

### Exporteren naar Microsoft Excel {#exporting-into-microsoft-excel}

Voor **[!UICONTROL List with group]** de typerapporten die naar Excel worden uitgevoerd, zijn de volgende aanbevelingen en de beperkingen van toepassing:

* Deze rapporten mogen geen lege regels bevatten.

  ![](assets/export_limitations_remove_empty_line.png)

* De legenda van de lijst moet verborgen zijn.

  ![](assets/export_limitations_hide_label.png)

* In de rapporten hoeft geen specifieke opmaak te worden gebruikt die op celniveau is gedefinieerd. Het verdient de voorkeur **[!UICONTROL Form rendering]** Hiermee definieert u de indeling van de cellen in de tabel. De **[!UICONTROL Form rendering]** kan worden geraadpleegd via **[!UICONTROL Administration > Configuration > Form rendering]**.
* We raden u niet aan HTML-inhoud in te voegen.
* Als een rapport meerdere tabellen, grafieken enzovoort bevat. typeelementen, zullen zij onder andere worden uitgevoerd.
* U kunt de regelterugloop in cellen forceren: deze configuratie wordt in Excel bewaard. Raadpleeg [deze sectie](../../reporting/using/creating-a-table.md#defining-cell-format) voor meer informatie.

### Exporteren uitstellen {#postpone-the-export}

U kunt het uitvoeren van een rapport uitstellen, bijvoorbeeld om op asynchrone vraag te wachten. Hiervoor voert u de volgende parameter in het initialisatiescript van de pagina in:

```
document.nl_waitBeforeRender = true;
```

Als u het exporteren wilt activeren en de conversie naar een PDF wilt starten, gebruikt u de opdracht **document.nl_renderToPdf()** functie zonder enige parameter.

### Geheugentoewijzing {#memory-allocation}

Bij het exporteren van bepaalde grote rapporten kunnen fouten in de geheugentoewijzing optreden.

In bepaalde gevallen is de standaardwaarde **maxMB** (**SKMS** voor gehoste instanties) van de JavaScript-code die wordt aangegeven in de **serverConf.xml** configuratiebestand is ingesteld op 64 MB. Als er onvoldoende geheugenfouten optreden tijdens het exporteren van een rapport, kunt u dit aantal verhogen tot 512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

Als u wijzigingen wilt toepassen die in de configuratie zijn aangebracht, **nlserver** de dienst moet opnieuw worden begonnen.

Meer informatie over de **serverConf.xml** bestand, zie [deze sectie](../../production/using/configuration-principle.md).

Meer informatie over de **nlserver** service, raadpleegt u [deze sectie](../../production/using/administration.md).

## Een rapport afdrukken {#printing-a-report}

U kunt uw rapport afdrukken. Hiervoor klikt u op het printerpictogram: het dialoogvenster wordt geopend.

Voor een beter resultaat bewerkt u de afdrukopties van Verkenner en selecteert u **[!UICONTROL Print background colors and images]**.

![](assets/s_ncs_advuser_report_print_options.png)

## Rapportarchieven maken {#creating-report-archives}

Door een rapport te archiveren kunt u het rapport op verschillende tijdstippen bekijken, bijvoorbeeld om de statistieken voor een bepaalde periode weer te geven.

Als u een archief wilt maken, opent u het desbetreffende rapport en klikt u op het juiste pictogram.

![](assets/s_ncs_advuser_report_wizard_07.png)

Als u bestaande archieven wilt weergeven of verbergen, klikt u op het pictogram voor tonen/verbergen.

![](assets/s_ncs_advuser_report_history_06.png)

De archiefdatums worden weergegeven onder het pictogram voor tonen/verbergen. Klik op het archief om dit weer te geven.

![](assets/s_ncs_advuser_report_history_04.png)

Het is mogelijk om een rapportarchief te schrappen. Ga hiertoe naar het Adobe Campaign-knooppunt waar uw rapporten zijn opgeslagen. Klik op de knop **[!UICONTROL Archives]** selecteert u de tab die u wilt verwijderen en klikt u op **[!UICONTROL Delete]**.

![](assets/s_ncs_advuser_report_history_01.png)
