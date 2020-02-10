---
title: Een enquête maken
seo-title: Een enquête maken
description: Een enquête maken
seo-description: null
page-status-flag: never-activated
uuid: 50d501b9-2b4f-48d1-b394-f7f71c413990
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 6850851d-1dbe-44f0-bbff-18dbac2cad9a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Een enquête maken{#building-a-survey}

## Een nieuwe enquête maken {#creating-a-new-survey}

In dit hoofdstuk worden het ontwerpen van een formulier van het type **enquête** met Adobe Campaign beschreven, evenals de beschikbare opties en configuraties. Met Adobe Campaign kunt u deze enquête beschikbaar stellen aan gebruikers en antwoorden in de database verzamelen en archiveren.

Webformulieren zijn toegankelijk via het **[!UICONTROL Resources > Online > Web applications]** knooppunt van de structuur. Als u een enquête wilt maken, klikt u op de **[!UICONTROL New]** knop boven de lijst met toepassingen of klikt u met de rechtermuisknop op de lijst en kiest u **[!UICONTROL New]**.

Selecteer het enquêtemalplaatje (**[!UICONTROL newSurvey]** door gebrek).

![](assets/s_ncs_admin_survey_select_template.png)

De pagina&#39;s van het formulier worden gemaakt met een speciale editor waarmee u invoervelden (tekst), selectievelden (lijsten, selectievakjes, enz.) kunt definiëren en configureren. en statische elementen (afbeeldingen, HTML-inhoud, enz.). Ze kunnen worden verzameld in &quot;containers&quot; en worden ingedeeld volgens de vereisten (zie Vragen [](#adding-questions)toevoegen).

>[!NOTE]
>
>Raadpleeg [deze sectie](../../web/using/about-web-forms.md)voor meer informatie over het definiëren van inhoud en het maken van schermlay-outs voor een webformulier.

## Velden toevoegen {#adding-fields}

Met de velden in een formulier kunnen gebruikers gegevens invoeren en opties selecteren. Voor elke pagina in het formulier worden ze gemaakt met de eerste knop op de werkbalk via het **[!UICONTROL Add using the wizard]** menu.

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>U kunt ook met de rechtermuisknop klikken en een invoerzone invoegen. Standaard wordt de zone ingevoegd aan het einde van de geselecteerde boomstructuur. Gebruik de pijlen in de werkbalk om deze te verplaatsen.

### Typen velden {#types-of-fields}

Wanneer u een veld aan een enquête toevoegt, moet u het type van het veld selecteren. De volgende opties zijn beschikbaar:

1. **[!UICONTROL Answer a question]**: Met deze optie kunt u een nieuw veld (gearchiveerd veld) declareren waarin antwoorden kunnen worden opgeslagen. In dit geval worden alle verzamelde waarden opgeslagen, zelfs wanneer een deelnemer het formulier meerdere keren invult. Deze opslagmodus is alleen beschikbaar in **enquêtes**. Raadpleeg [Opgeslagen antwoorden](../../web/using/managing-answers.md#storing-collected-answers)opslaan.
1. **[!UICONTROL Edit a recipient]**: met deze optie kunt u een veld in de database selecteren. In dit geval worden de gebruikersantwoorden in dit veld opgeslagen. Voor elke deelnemer wordt alleen de laatste opgeslagen waarde behouden en toegevoegd aan de profielgegevens.
1. **[!UICONTROL Add a variable]**: Met deze optie kunt u een instelling maken die ervoor zorgt dat informatie niet in de database wordt opgeslagen. Lokale variabelen kunnen upstream worden gedeclareerd. U kunt de knoppen ook rechtstreeks toevoegen wanneer u het veld maakt.
1. **[!UICONTROL Import an existing question]**: met deze optie kunt u bestaande vragen importeren die in andere enquêtes zijn gemaakt.

   >[!NOTE]
   >
   >De opslagwijzen en de gebiedsimporten worden gedetailleerd in het [Opslaan van verzamelde antwoorden](../../web/using/managing-answers.md#storing-collected-answers).

De aard van het veld dat moet worden toegevoegd (vervolgkeuzelijst, tekstveld, selectievakjes, enz.) wordt aangepast aan de geselecteerde opslagmodus. U kunt het veranderen gebruikend het **[!UICONTROL Type]** gebied van het **[!UICONTROL General]** lusje, maar zorg ervoor verenigbaar met het gegevenstype te blijven.

![](assets/s_ncs_admin_survey_change_type.png)

De verschillende typen beschikbare velden worden in [deze sectie](../../web/using/about-web-forms.md)beschreven.

## Specifieke elementen {#survey-specific-elements}

De online onderzoeken gebruiken de toepassingsmogelijkheden van het Web. De specifieke kenmerken van enquêtevelden worden hieronder nader beschreven.

### Meerdere keuzen {#multiple-choice}

Voor **[!UICONTROL Multiple choice]** tekstbesturingselementen kunt u een minimum- en maximumaantal selecties definiëren. Met deze optie kunt u bijvoorbeeld de selectie op ten minste **2** waarden en ten hoogste **4** waarden van de beschikbare opties instellen:

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

Als het aantal selecties te groot of te klein is, wordt het juiste bericht weergegeven.

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>In dit geval worden de opties geselecteerd met behulp van selectievakjes. Wanneer slechts één optie mogelijk is, worden de radioknopen gebruikt.

De bijbehorende configuratie is als volgt:

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

Daarnaast moet de opslaglocatie voor dit invoerveld een **[!UICONTROL Multiple values]** gearchiveerd **veld** zijn:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* Deze functionaliteit is alleen beschikbaar voor formulieren van het type **Beoordeling** .
>* Deze optie is niet compatibel met willekeurige vraagweergave. Raadpleeg [Vragen](#adding-questions)toevoegen voor meer informatie.


### Vragen toevoegen {#adding-questions}

Er zijn twee typen containers: standaard en vraag. De standaardcontainers worden gebruikt om paginalay-out en voorwaardelijke vertoning in een pagina te vormen. Deze worden in [deze sectie](../../web/using/about-web-forms.md)beschreven.

Gebruik een container voor **vragen** om een vraag aan de pagina toe te voegen en om de mogelijke antwoorden hieronder in de hiërarchie in te voegen. Antwoorden van gebruikers op vragen in dit type container kunnen worden geanalyseerd in rapporten.

>[!CAUTION]
>
>Plaats nooit een **vraagcontainer** onder een andere **vraagcontainer** in de hiërarchie.

![](assets/s_ncs_admin_question_label.png)

Het label van de vraag wordt ingevoerd in het labelveld. In dit geval wordt de stijl uit het stijlblad van het formulier toegepast. Selecteer de **[!UICONTROL Enter the title in HTML format]** optie om deze aan te passen. Hierdoor hebt u toegang tot de HTML-editor.

>[!NOTE]
>
>Raadpleeg [deze sectie](../../web/using/about-web-forms.md) voor meer informatie over het gebruik van de HTML-editor.

Bijvoorbeeld:

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

In het bovenstaande voorbeeld ziet de rendering er als volgt uit:

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>Elke vraag heeft een container van het type **Vraag** .

U kunt het willekeurig tekenen van vragen door de Campagne van Adobe toelaten. Het is dan mogelijk om het aantal vragen te specificeren dat in de pagina, op het gebied wordt getoond dat bij de bodem van het configuratievenster wordt gevestigd.

![](assets/s_ncs_admin_survey_containers_qu_display.png)

De rendering ziet er als volgt uit:

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

Wanneer de pagina wordt vernieuwd, zijn de weergegeven vragen anders.

>[!CAUTION]
>
>Wanneer u een vraag willekeurig weergeeft (**[!UICONTROL Display randomly]** optie ingeschakeld op de pagina), moet u ervoor zorgen dat u geen meerkeuzevragen gebruikt waarvoor een of meer selecties verplicht zijn.

