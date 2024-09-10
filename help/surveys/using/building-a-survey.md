---
product: campaign
title: Een enquête ontwerpen
description: Belangrijke stappen leren om een enquête te ontwerpen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Surveys
exl-id: 8d83dfd5-70ec-4656-965b-f6b5e6f9eec1
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 1%

---

# Een enquête ontwerpen{#building-a-survey}



## Een nieuwe enquête maken {#creating-a-new-survey}

Dit hoofdstuk detailleert het ontwerpen van het type van a **Onderzoek** vorm gebruikend Adobe Campaign, evenals de beschikbare opties en de configuraties. Met Adobe Campaign kunt u deze enquête beschikbaar maken voor gebruikers en antwoorden in de database verzamelen en archiveren.

Webformulieren zijn toegankelijk via het knooppunt **[!UICONTROL Resources > Online > Web applications]** van de structuur. Als u een enquête wilt maken, klikt u op de knop **[!UICONTROL New]** boven de lijst met toepassingen of klikt u met de rechtermuisknop op de lijst en kiest u **[!UICONTROL New]** .

Selecteer het enquêtemalplaatje (**[!UICONTROL newSurvey]** door gebrek).

![](assets/s_ncs_admin_survey_select_template.png)

De pagina&#39;s van het formulier worden gemaakt met een speciale editor waarmee u invoervelden (tekst), selectievelden (lijsten, selectievakjes, enz.) kunt definiëren en configureren. en statische elementen (afbeeldingen, HTML-inhoud, enz.). Zij kunnen worden verzameld in &quot;containers&quot; en worden ingedeeld volgens de vereisten. [ leer meer ](#adding-questions)).

>[!NOTE]
>
>Voor meer op hoe te om inhoud te bepalen en het schermlay-outs voor een vorm van het Web tot stand te brengen, verwijs naar [ dit document ](../../web/using/about-web-forms.md).

## Velden toevoegen {#adding-fields}

Met de velden in een formulier kunnen gebruikers gegevens invoeren en opties selecteren. Voor elke pagina in het formulier worden ze gemaakt met de eerste knop op de werkbalk via het menu **[!UICONTROL Add using the assistant]** .

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>U kunt ook met de rechtermuisknop klikken en een invoerzone invoegen. Standaard wordt de zone ingevoegd aan het einde van de geselecteerde boomstructuur. Gebruik de pijlen in de werkbalk om deze te verplaatsen.

### Typen velden {#types-of-fields}

Wanneer u een veld aan een enquête toevoegt, moet u het type van het veld selecteren. De volgende opties zijn beschikbaar:

1. **[!UICONTROL Answer a question]** : met deze optie kunt u een nieuw veld (gearchiveerd veld) declareren waarin antwoorden kunnen worden opgeslagen. In dit geval worden alle verzamelde waarden opgeslagen, zelfs wanneer een deelnemer het formulier meerdere keren invult. Deze opslagwijze is slechts beschikbaar in **Enquêtes**. [Meer informatie](../../surveys/using/managing-answers.md#storing-collected-answers).
1. **[!UICONTROL Edit a recipient]** : met deze optie kunt u een veld in de database selecteren. In dit geval worden de gebruikersantwoorden in dit veld opgeslagen. Voor elke deelnemer wordt alleen de laatste opgeslagen waarde behouden en toegevoegd aan de profielgegevens.
1. **[!UICONTROL Add a variable]**: met deze optie kunt u een instelling maken zodat de gegevens niet in de database worden opgeslagen. Lokale variabelen kunnen upstream worden gedeclareerd. U kunt de knoppen ook rechtstreeks toevoegen wanneer u het veld maakt.
1. **[!UICONTROL Import an existing question]** : met deze optie kunt u bestaande vragen importeren die in andere enquêtes zijn gemaakt.

   >[!NOTE]
   >
   >De wijzen van de opslag en de gebiedsinvoer worden gedetailleerd in [ dit sectie ](../../surveys/using/managing-answers.md#storing-collected-answers).

De aard van het veld dat moet worden toegevoegd (vervolgkeuzelijst, tekstveld, selectievakjes, enz.) past zich aan de geselecteerde opslagmodus aan. U kunt dit wijzigen met het veld **[!UICONTROL Type]** van het tabblad **[!UICONTROL General]** , maar zorg dat u consistent blijft met het gegevenstype.

![](assets/s_ncs_admin_survey_change_type.png)

De diverse soorten beschikbare gebieden zijn gedetailleerd in [ deze sectie ](../../web/using/about-web-forms.md).

## Specifieke elementen voor enquêtes {#survey-specific-elements}

De online onderzoeken zijn gebaseerd op de toepassingsmogelijkheden van het Web. De specifieke mogelijkheden voor enquêtes worden hieronder beschreven.

### Meerdere keuzen {#multiple-choice}

Voor **[!UICONTROL Multiple choice]** -besturingselementen voor tekst kunt u een minimum- en maximumaantal selecties definiëren. Bijvoorbeeld, laat deze optie u toe om de selectie aan minstens **te dwingen 2** waarden en hoogstens **4** waarden van de beschikbare opties:

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

Als het aantal selecties te groot of te klein is, wordt het juiste bericht weergegeven.

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>In dit geval worden de opties geselecteerd met behulp van selectievakjes. Wanneer slechts één optie mogelijk is, worden de radioknopen gebruikt.

De bijbehorende configuratie is als volgt:

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

Bovendien moet de opslagplaats voor dit inputgebied a **[!UICONTROL Multiple values]** type **gearchiveerd gebied** zijn:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* Deze functionaliteit is slechts beschikbaar voor **het type van Onderzoek** vormen.
>* Deze optie is niet compatibel met willekeurige vraagweergave. [Meer informatie](#adding-questions).

### Vragen toevoegen {#adding-questions}

Er zijn twee soorten containers: standaard en vraag. De standaardcontainers worden gebruikt om paginalay-out en voorwaardelijke vertoning in een pagina te vormen. [Meer informatie](../../web/using/about-web-forms.md).

Gebruik de container van de Vraag van de a **** om een vraag aan de pagina toe te voegen en de mogelijke antwoorden hieronder in de hiërarchie op te nemen. Antwoorden van gebruikers op vragen in dit type container kunnen worden geanalyseerd in rapporten.

>[!CAUTION]
>
>Neem nooit a **container van de Vraag** onder een andere **container van de Vraag** in de hiërarchie op.

![](assets/s_ncs_admin_question_label.png)

Het label van de vraag wordt ingevoerd in het labelveld. In dit geval wordt de stijl uit het stijlblad van het formulier toegepast. Selecteer de optie **[!UICONTROL Enter the title in HTML format]** om deze aan te passen. Hierdoor hebt u toegang tot de HTML-editor.

>[!NOTE]
>
>Verwijs naar [ dit document ](../../web/using/about-web-forms.md) voor meer bij het gebruiken van de redacteur van HTML.

Bijvoorbeeld:

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

In het bovenstaande voorbeeld ziet de rendering er als volgt uit:

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>Elke vraag heeft het type van a **Vraag** container.

U kunt het willekeurig tekenen van vragen door Adobe Campaign inschakelen. Het is dan mogelijk om het aantal vragen te specificeren dat in de pagina, op het gebied wordt getoond dat bij de bodem van het configuratievenster wordt gevestigd.

![](assets/s_ncs_admin_survey_containers_qu_display.png)

De rendering ziet er als volgt uit:

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

Wanneer de pagina wordt vernieuwd, zijn de weergegeven vragen anders.

>[!CAUTION]
>
>Wanneer u een vraag willekeurig weergeeft (**[!UICONTROL Display randomly]** optie ingeschakeld op de pagina), moet u ervoor zorgen dat u geen meerkeuzevragen gebruikt waarvoor een of meer selecties verplicht zijn.
