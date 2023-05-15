---
product: campaign
title: Een analyserapport gebruiken
description: Een analyserapport gebruiken
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
exl-id: d133efec-33e1-4711-a90f-e40385059386
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 1%

---

# Een analyserapport gebruiken{#processing-a-report}



## Een analyserapport opslaan {#saving-an-analysis-report}

Als u de aangewezen rechten hebt, kunt u een analyserapport bewaren dat van een malplaatje wordt gecreeerd of het uitvoeren in Excel, PDF, of formaat OpenOffice.

Als u uw rapport wilt opslaan, klikt u op **[!UICONTROL Save]** en geef uw rapport een label.

Selecteren **[!UICONTROL Also save data]** als u een geschiedenis van uw rapport wilt tot stand brengen en de waarden van het rapport op het tijdstip van sparen wilt zien. Raadpleeg voor meer informatie hierover [Analyserapporten archiveren](#archiving-analysis-reports).

De **[!UICONTROL Share this report]** andere operatoren toegang tot het rapport geven.

![](assets/s_ncs_user_report_wizard_010.png)

Zodra het is bewaard, kan dit rapport worden opnieuw gebruikt om andere analyserapporten te produceren:

![](assets/s_ncs_user_report_wizard_08a.png)

Als u wijzigingen in dit rapport wilt aanbrengen, bewerkt u de **[!UICONTROL Administration > Configuration > Adobe Campaign tree reports]** knooppunt van de Adobe Campaign-structuur (of de eerste map van het type &#39;Reports&#39; waarvoor de operator bewerkingsrechten heeft). Raadpleeg voor meer informatie hierover [De lay-out van een beschrijvend analyserapport configureren](#configuring-the-layout-of-a-descriptive-analysis-report).

## Aanvullende instellingen voor analyserapport {#analysis-report-additional-settings}

Nadat u een beschrijvend analyserapport hebt opgeslagen, kunt u de eigenschappen ervan bewerken en aanvullende opties openen.

![](assets/s_ncs_user_report_wizard_08b.png)

Deze opties zijn hetzelfde als standaardrapporten en worden beschreven in [deze pagina](../../reporting/using/properties-of-the-report.md).

## De lay-out van een beschrijvend analyserapport configureren {#configuring-the-layout-of-a-descriptive-analysis-report}

U kunt de weergave en lay-out van uw gegevens aanpassen in de grafieken en tabellen van de beschrijvende analyse. Alle opties zijn toegankelijk via de Adobe Campaign-structuur, in de **[!UICONTROL Edit]** van elk rapport.

### Weergavemodus van analyserapport {#analysis-report-display-mode}

Wanneer u een rapport maakt met de opdracht **[!UICONTROL qualitative distribution]** De weergavemodi voor sjablonen, tabellen en grafieken zijn standaard geselecteerd. Als u slechts één weergavemodus wilt, schakelt u het desbetreffende selectievakje uit. Dit betekent dat alleen de tab van de geselecteerde weergavemodus beschikbaar is.

![](assets/s_ncs_advuser_report_display_01.png)

Als u het schema van het rapport wilt wijzigen, klikt u op de knop **[!UICONTROL Select the link]** en selecteer een andere tabel in de database.

![](assets/s_ncs_advuser_report_display_02.png)

### Weergaveinstellingen van analyserapport {#analysis-report-display-settings}

Het is mogelijk om statistieken en subtotalen te verbergen of te tonen evenals de richtlijn van uw statistieken te kiezen.

![](assets/s_ncs_advuser_report_display_05.png)

Wanneer u statistieken creeert kunt u hun etiket personaliseren.

![](assets/s_ncs_advuser_report_display_06.png)

Hun naam zal in het rapport worden getoond.

![](assets/s_ncs_advuser_report_display_07.png)

Als u echter de controle van het label en de optie voor het subtotaal weergeven ongedaan maakt, zijn deze niet zichtbaar in het rapport. De naam wordt als knopinfo weergegeven wanneer u de cursor op een cel van de tabel plaatst.

![](assets/s_ncs_advuser_report_display_08.png)

De statistieken worden standaard online weergegeven. Als u de richting wilt wijzigen, selecteert u de gewenste optie in de vervolgkeuzelijst.

![](assets/s_ncs_advuser_report_wizard_035a.png)

In het volgende voorbeeld worden de statistieken weergegeven in kolommen.

![](assets/s_ncs_advuser_report_wizard_035.png)

### Gegevensindeling van analyserapport {#analysis-report-data-layout}

U kunt de gegevenslay-out rechtstreeks in de beschrijvende analystabel aanpassen. Klik hiertoe met de rechtermuisknop op de variabele waarmee u wilt werken. Selecteer de beschikbare opties in het keuzemenu:

* **[!UICONTROL Pivot]** om de as van de variabele te wijzigen.
* **[!UICONTROL Up]** / **[!UICONTROL Down]** om de variabelen in regels om te wisselen.
* **[!UICONTROL Move to the right]** / **[!UICONTROL Move to the left]** om de variabelen in kolommen te wisselen.
* **[!UICONTROL Turn]** om de assen van variabelen om te keren.
* **[!UICONTROL Sort from A to Z]** als u de variabelewaarden laag tot hoog wilt sorteren.
* **[!UICONTROL Sort from Z to A]** als u de waarden van de variabele hoog naar laag wilt sorteren.

   ![](assets/s_ncs_advuser_report_wizard_016.png)

Als u wilt terugkeren naar de oorspronkelijke weergave, vernieuwt u de weergave.

### Opties in het diagram met analyserapporten {#analysis-report-chart-options}

Het is mogelijk om de weergave van gegevens in het diagram aan te passen. Om dit te doen, klik **[!UICONTROL Variables...]** koppeling beschikbaar tijdens het selectiestadium van het diagramtype.

![](assets/s_ncs_advuser_report_wizard_3c.png)

De volgende opties zijn beschikbaar:

* In de bovenste sectie van het venster kunt u het weergavegebied van het diagram wijzigen.
* Standaard worden labels weergegeven in het diagram. U kunt deze verbergen door het selectievakje **[!UICONTROL Show values]** optie.
* De **[!UICONTROL Accumulate values]** Met deze optie kunt u waarden van de ene reeks toevoegen aan de andere.
* U kunt beslissen of u de legenda van het diagram wilt weergeven: om het te verbergen, uncheck de aangewezen optie. Standaard wordt de legenda buiten het diagram in de rechterbovenhoek weergegeven.

   De legenda kan ook boven op het diagram worden weergegeven om op weergaveruimte te besparen. Selecteer de optie om dit te doen **[!UICONTROL Include in the chart]**

   Selecteer de verticale en horizontale uitlijning in het dialoogvenster **[!UICONTROL Caption position]** vervolgkeuzelijst.

   ![](assets/s_ncs_advuser_report_wizard_3d.png)

## Een analyserapport exporteren {#exporting-an-analysis-report}

Als u gegevens uit een analyserapport wilt exporteren, klikt u op de vervolgkeuzelijst en selecteert u de gewenste uitvoerindeling.

![](assets/s_ncs_user_report_wizard_09.png)

Raadpleeg [deze pagina](../../reporting/using/actions-on-reports.md) voor meer informatie.

## Bestaande rapporten en analyses opnieuw gebruiken {#re-using-existing-reports-and-analyses}

U kunt beschrijvende analyserapporten over gegevens maken met bestaande rapporten die al in Adobe Campaign zijn opgeslagen. Deze modus is mogelijk wanneer analyses zijn opgeslagen of wanneer rapporten zijn gemaakt en geconfigureerd voor toegang via de wizard voor beschrijvende analyse.

Als u wilt weten hoe u beschrijvende analyses kunt opslaan, raadpleegt u [Een analyserapport opslaan](#saving-an-analysis-report).

Als u beschrijvende analyserapporten wilt maken, moet de wizard voor beschrijvende analyse worden uitgevoerd via een workflowovergang of via de **[!UICONTROL Tools > Descriptive analysis]** -menu.

1. Selecteer **[!UICONTROL Existing analyses and reports]** en klik op **[!UICONTROL Next]**.
1. Hiermee hebt u toegang tot de lijst met beschikbare rapporten. Selecteer het rapport dat u wilt genereren.

   ![](assets/s_ncs_user_report_wizard_01.png)

## Analyserapporten archiveren {#archiving-analysis-reports}

Wanneer u een beschrijvende analyse creeert die op een bestaande analyse wordt gebaseerd, kunt u archieven tot stand brengen om gegevens op te slaan en rapportresultaten te vergelijken.

Voer de volgende stappen uit om een historie te maken:

1. Open een bestaande analyse of maak een nieuwe beschrijvende analysewizard.
1. Klik in de pagina met rapportweergave op de knop om een geschiedenis in de werkbalk te maken en bevestig vervolgens zoals hieronder wordt weergegeven:

   ![](assets/reporting_descriptive_historize_icon.png)

1. Met de knop Archieftoegang geeft u vorige analyses weer.

   ![](assets/reporting_descriptive_historize_access.png)
