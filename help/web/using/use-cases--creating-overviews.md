---
product: campaign
title: '"Gebruiksscenario’s: overzichten maken"'
description: '"Gebruiksscenario’s: overzichten maken"'
feature: Web Apps
exl-id: a1ac3aab-dc81-4533-9207-26d5dc5e1c88
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Gebruik hoofdletters/kleine letters: overzichtspagina&#39;s maken{#use-cases-creating-overviews}

![](../../assets/common.svg)

In het volgende voorbeeld, zullen wij overzicht-type de toepassingen van het Web tot stand brengen om alle toepassingen van het Web in uw gegevensbestand te tonen. Configureer de volgende elementen:

* een filter in de map (raadpleeg [Een filter toevoegen aan een map](#adding-a-filter-on-a-folder)),
* een knop voor het maken van een nieuwe webtoepassing (zie [Een knop toevoegen om een nieuwe webtoepassing te configureren](#adding-a-button-to-configure-a-new-web-application)),
* detailweergave voor elk item in de lijst (zie [Details toevoegen aan een lijst](#adding-detail-to-a-list)),
* één filter per gereedschap voor het bewerken van koppelingen (zie [Een filter maken met een koppelingseditor](#creating-a-filter-using-a-link-editor)),
* een koppeling Vernieuwen (raadpleeg [Een koppeling voor vernieuwen maken](#creating-a-refresh-link)).

![](assets/s_ncs_configuration_webapp_overview.png)

## Een webtoepassing van één pagina maken {#creating-a-single-page-web-application}

1. Eén maken **[!UICONTROL Page]** De toepassing van het Web en maakt uitgaande overgangen en overgangen aan de volgende pagina onbruikbaar.

   ![](assets/s_ncs_configuration_webapp_create.png)

1. De paginatitel wijzigen.

   Deze titel zal in de overzichtskopbal en in het de toepassingsoverzicht van het Web verschijnen.

1. In de de toepassingseigenschappen van het Web, wijzig het teruggeven van uw toepassing door te selecteren **[!UICONTROL Single-page Web application]** sjabloon.

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. Open de **[!UICONTROL Page]** activiteit van uw toepassing van het Web en open een lijst (**[!UICONTROL Static element > List]**).
1. In de **[!UICONTROL Data]** selecteert u het type **[!UICONTROL Web applications]** en de **[!UICONTROL Label]** , **[!UICONTROL Creation date]** en **[!UICONTROL Type of application]** uitvoerkolommen.
1. In de **[!UICONTROL Filter]** subtab, creeer de volgende filter zoals hieronder getoond om de toepassingen van het Web slechts te tonen en malplaatjes van uw mening uit te sluiten.

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. Sluit het configuratievenster van uw pagina en klik **[!UICONTROL Preview]**.

   De lijst van de toepassingen van het Web beschikbaar in uw gegevensbestand wordt getoond.

   ![](assets/s_ncs_configuration_webapp_preview.png)

## Een filter toevoegen aan een map {#adding-a-filter-on-a-folder}

In een overzicht kunt u naar keuze toegang krijgen tot gegevens, afhankelijk van de locatie in de Adobe Campaign-structuur. Dit is een filter op een map. Pas het volgende proces toe om het aan uw overzicht toe te voegen.

1. Plaats de cursor op de knop **[!UICONTROL Page]** knoop van uw toepassing van het Web en voeg een **[!UICONTROL Select folder]** element (**[!UICONTROL Advanced controls > Select folder]**).
1. In de **[!UICONTROL Storage]** venster dat verschijnt, klikt u op de knop **[!UICONTROL Edit variables]** koppeling.
1. Wijzig het label van de variabele naar wens.
1. Wijzig de naam van de variabele met de **map** waarde.

   >[!NOTE]
   >
   >De naam van de variabele moet overeenkomen met de naam van het element dat is gekoppeld aan de map (gedefinieerd in het schema), d.w.z. **map** in dit geval. U moet deze naam opnieuw gebruiken wanneer u naar de tabel verwijst.

1. Pas de **[!UICONTROL XML]** type aan de variabele.

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. Selecteer **[!UICONTROL Refresh page]** interactie.

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. Plaats de cursor in de lijst en in het dialoogvenster **[!UICONTROL Advanced]** tabblad, verwijst u naar de variabele die eerder in het dialoogvenster **[!UICONTROL Folder filter XPath]** van de lijst. U moet de naam gebruiken van het element waarop de mapkoppeling betrekking heeft, d.w.z. **map**.

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >In dit stadium, is de toepassing van het Web niet binnen zijn toepassingscontext, kan het filter daarom niet op de omslag worden getest.

## Een knop toevoegen om een nieuwe webtoepassing te configureren {#adding-a-button-to-configure-a-new-web-application}

1. Plaats de cursor op de knop **[!UICONTROL Page]** -element en een koppeling toevoegen (**[!UICONTROL Static elements > Link]**).
1. Wijzig het koppelingsetiket aangezien het op de knoop in het overzicht zal verschijnen.

   In ons voorbeeld is het label **Nieuw**.

1. Voeg de volgende URL in het URL-veld in: **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**.

   >[!NOTE]
   >
   >**nms:webApp** valt samen met het webtoepassingsschema.
   >
   >**nms:newWebApp** valt samen met de nieuwe wizard voor het maken van webtoepassingen.

1. Kies of u de URL in hetzelfde venster wilt weergeven.
1. Voeg het webtoepassingspictogram toe aan het afbeeldingsveld: **/nms/img/webApp.png**.

   Dit pictogram wordt weergegeven op het tabblad **[!UICONTROL New]** knop.

1. Enter **knop** in de **[!UICONTROL Style]** veld.

   Naar deze stijl wordt verwezen in het dialoogvenster **[!UICONTROL Single-page Web application]** eerder geselecteerde sjabloon.

   ![](assets/s_ncs_configuration_webapp_link.png)

## Details toevoegen aan een lijst {#adding-detail-to-a-list}

Wanneer u een lijst in uw overzicht vormt, kunt u verkiezen om extra details voor elke ingang in uw lijst te tonen.

1. Plaats de cursor op het eerder gemaakte lijstelement.
1. In de **[!UICONTROL General]** selecteert u de **[!UICONTROL Columns and additional detail]** weergavemodus in de vervolgkeuzelijst.

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. In de **[!UICONTROL Data]** tabblad, voegt u de **[!UICONTROL Primary key]** , **[!UICONTROL Internal name]** en **[!UICONTROL Description]** en selecteert u de **[!UICONTROL Hidden field]** voor elke optie.

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   Op die manier is deze informatie alleen zichtbaar in de details van elke vermelding.

1. In de **[!UICONTROL Additional detail]** toevoegen:

   ```
   <div class="detailBox">
     <div class="actionBox">
       <span class="action"><img src="/xtk/img/fileEdit.png"/><a title="Open" class="linkAction" href="xtk://open/?schema=nms:webApp&form=nms:webApp&pk=
       <%=webApp.id%>">Open...</a></span>
       <% 
       if( webApp.@appType == 1 ) { //survey
       %>
       <span class="action"><img src="/xtk/img/report.png"/><a target="_blank" title="Reports" class="linkAction" href="/xtk/report.jssp?_context=selection&
         _schema=nms:webApp&_selection=<%=webApp.@id%>
         &__sessiontoken=<%=document.controller.getSessionToken()%>">Reports</a></span>
       <% 
       } 
       %>
     </div>
     <div>
       Internal name: <%= webApp.@internalName %>
     </div>
     <%
     if( webApp.desc != "" )
     {
     %>
     <div>
       Description: <%= webApp.desc %>
     </div>
     <% 
     } 
     %>
   </div>
   ```

>[!NOTE]
>
>JavaScript-bibliotheken vernieuwen zich vijf minuten op de server. U kunt de server opnieuw starten om te voorkomen dat er op deze vertraging wordt gewacht.

## De lijst filteren en bijwerken {#filtering-and-updating-the-list}

In deze sectie, zult u een filter voor het tonen van het overzicht van de toepassingen creëren van het Web die door een specifieke exploitant worden gecreeerd. Dit filter wordt gemaakt met een koppelingseditor. Nadat u een operator hebt geselecteerd, vernieuwt u de lijst om het filter toe te passen. hiervoor moet een koppeling Vernieuwen worden gemaakt.

Deze twee elementen worden in dezelfde container gegroepeerd om in het overzicht grafisch te worden gegroepeerd.

1. Plaats de cursor op de knop **[!UICONTROL Page]** element en selecteer **[!UICONTROL Container > Standard]**.
1. Aantal kolommen instellen op **2**, zodat de koppelingseditor en de koppeling naast elkaar staan.

   ![](assets/s_ncs_configuration_webapp_container.png)

   Voor informatie over de indeling van elementen raadpleegt u [deze sectie](about-web-forms.md).

1. Toepassen **dottedFilter**.

   Naar deze stijl wordt verwezen in het dialoogvenster **[!UICONTROL Single-page Web application]** eerder geselecteerde sjabloon.

   ![](assets/s_ncs_configuration_webapp_container002.png)

### Een filter maken met een koppelingseditor {#creating-a-filter-using-a-link-editor}

1. Plaats de cursor op de container die u tijdens het vorige werkgebied hebt gemaakt en voeg een koppelingseditor in via de **[!UICONTROL Advanced controls]** -menu.
1. Selecteer in het opslagvenster dat automatisch wordt geopend de optie **[!UICONTROL Variables]** en klikt u op de knop **[!UICONTROL Edit variables]** koppelen en een XML-variabele maken voor het filteren van gegevens.

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. Wijzig het label.

   Het verschijnt naast **[!UICONTROL Filter]** in het overzicht.

1. Kies de lijst van Exploitant als toepassingsschema.

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. Plaats de cursor op het lijstelement en maak een filter via de knop **[!UICONTROL Data > Filter]** tab:

   * **Uitdrukking:** Externe sleutel van de koppeling &#39;Gemaakt door&#39;
   * **Operator:** is gelijk aan
   * **Waarde:** Variabelen (variabelen)
   * **Wordt in aanmerking genomen:** &#39;$(var2/@id)&#39;!=&#39;

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>De gebruiker van de toepassing van het Web moet een geïdentificeerde exploitant met de aangewezen rechten van Adobe Campaign zijn om tot de informatie toegang te hebben. Dit type van configuratie zal niet voor de anonieme toepassingen van het Web werken.

### Een koppeling voor vernieuwen maken {#creating-a-refresh-link}

1. Plaats de cursor op de container en voeg een **[!UICONTROL Link]** via de **[!UICONTROL Static elements]** -menu.
1. Wijzig het label.
1. Selecteer **[!UICONTROL Refresh data in a list]**.
1. Voeg de eerder gemaakte lijst toe.

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. Het pictogram Vernieuwen toevoegen op het tabblad **[!UICONTROL Image]** veld: **/xtk/img/refresh.png**.
1. Gebruikend de soort-orde pijlen, reorganiseer de diverse elementen van uw toepassing van het Web zoals hieronder getoond.

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

De toepassing van het Web wordt nu gevormd. U kunt op de knop **[!UICONTROL Preview]** gebruiken om een voorvertoning weer te geven.

![](assets/s_ncs_configuration_webapp_result.png)
