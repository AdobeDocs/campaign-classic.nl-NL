---
product: campaign
title: Acties voor rapporten
description: Acties voor rapporten
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---

# Acties voor rapporten{#actions-on-reports}

Wanneer u een rapport weergeeft, kunt u op de werkbalk een bepaald aantal handelingen uitvoeren. Deze worden hieronder beschreven.

![](assets/s_ncs_advuser_report_wizard_2.png)

Met de werkbalk kunt u het rapport bijvoorbeeld exporteren, afdrukken, archiveren of weergeven in een webbrowser.

![](assets/s_ncs_advuser_report_wizard_04.png)

## Een rapport {#exporting-a-report} exporteren

Selecteer de indeling waarin u het rapport wilt exporteren in de vervolgkeuzelijst. (.xls, .pdf of .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

Wanneer een rapport meerdere pagina&#39;s bevat, moet u de bewerking voor elke pagina herhalen.

U kunt uw rapport configureren met het oog op het exporteren ervan in PDF-, Excel- of OpenOffice-indeling. Open de explorator van Adobe Campaign en selecteer het betrokken rapport.

Exportopties zijn toegankelijk via de **[!UICONTROL Page]**-activiteiten van het rapport op het tabblad **[!UICONTROL Advanced]**.

Wijzig de instellingen van **[!UICONTROL Paper]** en **[!UICONTROL Margins]** om aan uw wensen te voldoen. U kunt het exporteren van een pagina alleen in PDF-indeling toestaan. Om dit te doen, uncheck de **[!UICONTROL Activate OpenOffice/Microsoft Excel export]** optie.

![](assets/s_ncs_advuser_report_wizard_021.png)

### Exporteren naar Microsoft Excel {#exporting-into-microsoft-excel}

Voor **[!UICONTROL List with group]** typerapporten die bestemd zijn om naar Excel te worden uitgevoerd, zijn de volgende aanbevelingen en beperkingen van toepassing:

* Deze rapporten mogen geen lege regels bevatten.

   ![](assets/export_limitations_remove_empty_line.png)

* De legenda van de lijst moet verborgen zijn.

   ![](assets/export_limitations_hide_label.png)

* In de rapporten hoeft geen specifieke opmaak te worden gebruikt die op celniveau is gedefinieerd. Het is raadzaam **[!UICONTROL Form rendering]** te gebruiken om de indeling van de cellen in de tabel te definiëren. De **[!UICONTROL Form rendering]** kan via **[!UICONTROL Administration > Configuration > Form rendering]** worden betreden.
* We raden u niet aan HTML-inhoud in te voegen.
* Als een rapport meerdere tabellen, grafieken enzovoort bevat. typeelementen, zullen zij onder andere worden uitgevoerd.
* U kunt de regelterugloop in cellen forceren: deze configuratie zal in Excel worden gehouden. Voor meer op dit, verwijs naar [Bepalend celformaat](../../reporting/using/creating-a-table.md#defining-cell-format).

### Exporteren {#postpone-the-export} uitstellen

U kunt het uitvoeren van een rapport uitstellen, bijvoorbeeld om op asynchrone vraag te wachten. Hiervoor voert u de volgende parameter in het initialisatiescript van de pagina in:

```
document.nl_waitBeforeRender = true;
```

Als u het exporteren wilt activeren en de conversie naar een PDF wilt starten, gebruikt u de functie **document.nl_renderToPdf()** zonder parameter.

### Geheugentoewijzing {#memory-allocation}

Bij het exporteren van bepaalde grote rapporten kunnen fouten in de geheugentoewijzing optreden.

In bepaalde gevallen is de standaardwaarde **maxMB** (**SKMS** voor gehoste instanties) van het JavaScript dat wordt aangegeven in het configuratiebestand **serverConf.xml** ingesteld op 64 MB. Als er onvoldoende geheugenfouten optreden tijdens het exporteren van een rapport, kunt u dit aantal verhogen tot 512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

Als u wijzigingen wilt toepassen die in de configuratie zijn aangebracht, moet de service **nlserver** opnieuw worden gestart.

Raadpleeg [deze sectie](../../production/using/configuration-principle.md) voor meer informatie over het bestand **serverConf.xml.**

Raadpleeg [deze sectie](../../production/using/administration.md) voor meer informatie over de **nlserver** service.

## Een rapport {#printing-a-report} afdrukken

U kunt uw rapport afdrukken: Klik hiertoe op het printerpictogram: hiermee wordt het dialoogvenster geopend.

Voor een beter resultaat bewerkt u de afdrukopties van Internet Explorer en selecteert u **[!UICONTROL Print background colors and images]**.

![](assets/s_ncs_advuser_report_print_options.png)

## Rapportarchieven maken {#creating-report-archives}

Door een rapport te archiveren kunt u het rapport op verschillende tijdstippen bekijken, bijvoorbeeld om de statistieken voor een bepaalde periode weer te geven.

Als u een archief wilt maken, opent u het desbetreffende rapport en klikt u op het juiste pictogram.

![](assets/s_ncs_advuser_report_wizard_07.png)

Klik op het pictogram voor tonen/verbergen om bestaande archieven weer te geven of te verbergen.

![](assets/s_ncs_advuser_report_history_06.png)

De archiefdatums worden weergegeven onder het pictogram voor tonen/verbergen. Klik op het archief om dit weer te geven.

![](assets/s_ncs_advuser_report_history_04.png)

Het is mogelijk om een rapportarchief te schrappen. Ga hiertoe naar het Adobe Campaign-knooppunt waar uw rapporten zijn opgeslagen. Klik op de tab **[!UICONTROL Archives]**, selecteer de tab die u wilt verwijderen en klik op **[!UICONTROL Delete]**.

![](assets/s_ncs_advuser_report_history_01.png)
