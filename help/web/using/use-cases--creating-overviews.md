---
solution: Campaign Classic
product: campaign
title: '"Gebruiksscenario’s: overzichten maken"'
description: '"Gebruiksscenario’s: overzichten maken"'
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 1%

---


# Gebruiksscenario’s: overzichten maken{#use-cases-creating-overviews}

In het volgende voorbeeld, zullen wij overzicht-type de toepassingen van het Web tot stand brengen om alle toepassingen van het Web in uw gegevensbestand te tonen. Configureer de volgende elementen:

* een filter op de omslag (verwijs naar [Toevoegend een filter op een omslag ](#adding-a-filter-on-a-folder)),
* een knoop voor het creëren van een nieuwe toepassing van het Web (verwijs naar [Toevoegend een knoop om een nieuwe toepassing van het Web te vormen](#adding-a-button-to-configure-a-new-web-application)),
* detailweergave voor elk item in de lijst (zie [Details toevoegen aan een lijst](#adding-detail-to-a-list));
* één filter per hulpmiddel voor het bewerken van koppelingen (zie [Een filter maken met een koppelingseditor](#creating-a-filter-using-a-link-editor));
* een verfrist verbinding (verwijder naar [Creërend een verfrist verbinding](#creating-a-refresh-link)).

![](assets/s_ncs_configuration_webapp_overview.png)

## Een webtoepassing van één pagina maken {#creating-a-single-page-web-application}

1. Creeer één enkele **[!UICONTROL Page]** toepassing van het Web en maak uitgaande overgangen en overgangen aan de volgende pagina onbruikbaar.

   ![](assets/s_ncs_configuration_webapp_create.png)

1. De paginatitel wijzigen.

   Deze titel zal in de overzichtskopbal en in het de toepassingsoverzicht van het Web verschijnen.

1. In de de toepassingseigenschappen van het Web, wijzig het teruggeven van uw toepassing door het **[!UICONTROL Single-page Web application]** malplaatje te selecteren.

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. Open de **[!UICONTROL Page]** activiteit van uw toepassing van het Web en open een lijst (**[!UICONTROL Static element > List]**).
1. Selecteer op het tabblad **[!UICONTROL Data]** van uw lijst het type **[!UICONTROL Web applications]**-document en de **[!UICONTROL Label]**-, **[!UICONTROL Creation date]**- en **[!UICONTROL Type of application]**-uitvoerkolommen.
1. In **[!UICONTROL Filter]** sub-tab, creeer de volgende filter zoals hieronder getoond om de toepassingen van het Web slechts te tonen en malplaatjes van uw mening uit te sluiten.

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. Sluit het configuratievenster van uw pagina en klik **[!UICONTROL Preview]**.

   De lijst van de toepassingen van het Web beschikbaar in uw gegevensbestand wordt getoond.

   ![](assets/s_ncs_configuration_webapp_preview.png)

## Een filter toevoegen aan een map {#adding-a-filter-on-a-folder}

In een overzicht kunt u naar keuze toegang krijgen tot gegevens, afhankelijk van de locatie in de Adobe Campaign-structuur. Dit is een filter op een map. Pas het volgende proces toe om het aan uw overzicht toe te voegen.

1. Plaats uw curseur op de **[!UICONTROL Page]** knoop van uw toepassing van het Web en voeg een **[!UICONTROL Select folder]** element (**[!UICONTROL Advanced controls > Select folder]**) toe.
1. Klik in het **[!UICONTROL Storage]**-venster dat verschijnt op de koppeling **[!UICONTROL Edit variables]**.
1. Wijzig het label van de variabele naar wens.
1. Wijzig de naam van de variabele met de waarde **folder**.

   >[!NOTE]
   >
   >De naam van de variabele moet overeenkomen met de naam van het element dat is gekoppeld aan de map (gedefinieerd in het schema), d.w.z. **map** in dit geval. U moet deze naam opnieuw gebruiken wanneer u naar de tabel verwijst.

1. Pas het **[!UICONTROL XML]** type op de variabele toe.

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. Selecteer de interactie **[!UICONTROL Refresh page]**.

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. Plaats de cursor in de lijst en verwijs op het tabblad **[!UICONTROL Advanced]** naar de variabele die eerder op het tabblad **[!UICONTROL Folder filter XPath]** in de lijst is gemaakt. U moet de naam gebruiken van het element waarop de mapkoppeling betrekking heeft, d.w.z. **map**.

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >In dit stadium, is de toepassing van het Web niet binnen zijn toepassingscontext, kan het filter daarom niet op de omslag worden getest.

## Een knop toevoegen om een nieuwe webtoepassing {#adding-a-button-to-configure-a-new-web-application} te configureren

1. Plaats uw curseur op **[!UICONTROL Page]** element en voeg een verbinding (**[!UICONTROL Static elements > Link]**) toe.
1. Wijzig het koppelingsetiket aangezien het op de knoop in het overzicht zal verschijnen.

   In ons voorbeeld is het label **New**.

1. Voeg de volgende URL in het URL-veld in: **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**.

   >[!NOTE]
   >
   >**nms:** webApps valt met het de toepassingsschema van het Web samen.
   >
   >**nms:** newWebApps met de nieuwe tovenaar van de de toepassingsverwezenlijking van het Web.

1. Kies of u de URL in hetzelfde venster wilt weergeven.
1. Voeg het webtoepassingspictogram toe aan het afbeeldingsveld: **/nms/img/webApp.png**.

   Dit pictogram wordt weergegeven op de knop **[!UICONTROL New]**.

1. Typ **button** in het veld **[!UICONTROL Style]**.

   Deze stijl wordt vermeld in **[!UICONTROL Single-page Web application]** eerder geselecteerde malplaatje.

   ![](assets/s_ncs_configuration_webapp_link.png)

## Details toevoegen aan een lijst {#adding-detail-to-a-list}

Wanneer u een lijst in uw overzicht vormt, kunt u verkiezen om extra details voor elke ingang in uw lijst te tonen.

1. Plaats de cursor op het eerder gemaakte lijstelement.
1. Selecteer op het tabblad **[!UICONTROL General]** de weergavemodus **[!UICONTROL Columns and additional detail]** in de vervolgkeuzelijst.

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. Voeg op het tabblad **[!UICONTROL Data]** de kolommen **[!UICONTROL Primary key]**, **[!UICONTROL Internal name]** en **[!UICONTROL Description]** toe en selecteer de optie **[!UICONTROL Hidden field]** voor elke kolom.

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   Op die manier is deze informatie alleen zichtbaar in de details van elke vermelding.

1. Voeg de volgende code toe op het tabblad **[!UICONTROL Additional detail]**:

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
>JavaScript-bibliotheken vernieuwen zich vijf minuten op de server. U kunt de server opnieuw starten om te voorkomen dat wordt gewacht tot deze vertraging optreedt.

## De lijst {#filtering-and-updating-the-list} filteren en bijwerken

In deze sectie, zult u een filter voor het tonen van het overzicht van de toepassingen creëren van het Web die door een specifieke exploitant worden gecreeerd. Dit filter wordt gemaakt met een koppelingseditor. Nadat u een operator hebt geselecteerd, vernieuwt u de lijst om het filter toe te passen. hiervoor moet een koppeling Vernieuwen worden gemaakt.

Deze twee elementen worden in dezelfde container gegroepeerd om in het overzicht grafisch te worden gegroepeerd.

1. Plaats de cursor op het element **[!UICONTROL Page]** en selecteer **[!UICONTROL Container > Standard]**.
1. Plaats het aantal kolommen aan **2**, zodat de verbindingsredacteur en de verbinding naast elkaar zijn.

   ![](assets/s_ncs_configuration_webapp_container.png)

   Voor informatie over elementlay-out, verwijs naar [deze sectie](../../web/using/about-web-forms.md).

1. Pas **dottedFilter** toe.

   Deze stijl wordt vermeld in **[!UICONTROL Single-page Web applicatio]** eerder geselecteerde malplaatje.

   ![](assets/s_ncs_configuration_webapp_container002.png)

### Een filter maken met een koppelingseditor {#creating-a-filter-using-a-link-editor}

1. Plaats de cursor op de container die u tijdens het vorige werkgebied hebt gemaakt en voeg een koppelingseditor in via het menu **[!UICONTROL Advanced controls]**.
1. Selecteer in het opslagvenster dat automatisch wordt geopend de optie **[!UICONTROL Variables]**, klik vervolgens op de koppeling **[!UICONTROL Edit variables]** en maak een XML-variabele voor het filteren van gegevens.

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. Wijzig het label.

   Deze wordt naast het veld **[!UICONTROL Filter]** in het overzicht weergegeven.

1. Kies de lijst van Exploitant als toepassingsschema.

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. Plaats de cursor op het lijstelement en maak een filter via het tabblad **[!UICONTROL Data > Filter]**:

   * **Expressie:** buitenlandse sleutel van de koppeling &#39;Gemaakt door&#39;
   * **Operator:** gelijk aan
   * **Waarde:** variabelen
   * **Hiermee wordt rekening gehouden als:** &#39;$(var2/@id)&#39;!=&#39;&#39;

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>De gebruiker van de toepassing van het Web moet een geïdentificeerde exploitant met de aangewezen rechten van Adobe Campaign zijn om tot de informatie toegang te hebben. Dit type van configuratie zal niet voor de anonieme toepassingen van het Web werken.

### Vernieuwingskoppelingen maken {#creating-a-refresh-link}

1. Plaats de cursor op de container en voeg een **[!UICONTROL Link]** in via het menu **[!UICONTROL Static elements]**.
1. Wijzig het label.
1. Selecteer **[!UICONTROL Refresh data in a list]**.
1. Voeg de eerder gemaakte lijst toe.

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. Voeg het vernieuwingspictogram toe op het **[!UICONTROL Image]** gebied: **/xtk/img/refresh.png**.
1. Gebruikend de soort-orde pijlen, reorganiseer de diverse elementen van uw toepassing van het Web zoals hieronder getoond.

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

De toepassing van het Web wordt nu gevormd. U kunt op het tabblad **[!UICONTROL Preview]** klikken om er een voorvertoning van weer te geven.

![](assets/s_ncs_configuration_webapp_result.png)

