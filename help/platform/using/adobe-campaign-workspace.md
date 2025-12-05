---
product: campaign
title: Adobe Campaign-werkruimte
description: Leer de werkruimte Campagne gebruiken en aanpassen
feature: Overview
role: Developer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 354fc8fd5d030ed88e2b279ba1dd3eaf2f314d53
workflow-type: tm+mt
source-wordcount: '1166'
ht-degree: 1%

---

# Adobe Campaign-werkruimte {#adobe-campaign-workspace}

## De Adobe Campaign-interface verkennen {#about-adobe-campaign-interface}

Zodra u met het gegevensbestand wordt verbonden, hebt u toegang tot de homepage van Adobe Campaign. Deze pagina is uw dashboard: het bestaat uit verbindingen en kortere weg die u tot mogelijkheden, afhankelijk van uw installatie en algemene platformconfiguraties laten toegang hebben.

Vanuit het centrale gedeelte van de startpagina kunt u koppelingen gebruiken om toegang te krijgen tot het documentatieportaal voor campagnes, de community en de Adobe-website voor klantenservice.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png) ontdekt de werkruimte van de Campagne in [&#x200B; video &#x200B;](#video)

>[!NOTE]
>
>De Adobe Campaign-mogelijkheden die voor uw instantie beschikbaar zijn, zijn afhankelijk van de geïnstalleerde modules en invoegtoepassingen. Sommige zijn mogelijk ook niet beschikbaar, afhankelijk van uw machtigingen en specifieke configuraties.
>
>Voordat u een module of add-on installeert, moet u de licentieovereenkomst controleren of contact opnemen met de Adobe-accountmanager.

### Console en webtoegang {#console-and-web-access}

Het Adobe Campaign-platform is toegankelijk via een console of via een internetbrowser. Zie compatibele browsers in de [&#x200B; verenigbaarheidsmatrijs &#x200B;](../../rn/using/compatibility-matrix.md#Browsers).

De interface van de Webtoegang is gelijkaardig aan de consoleinterface. Vanuit een browser kunt u dezelfde navigatie- en weergavefuncties gebruiken als in de console, maar u kunt slechts een beperkte set acties op campagnes uitvoeren. U kunt bijvoorbeeld campagnes weergeven en annuleren, maar u kunt geen campagnes wijzigen. Voor een bepaalde exploitant, zal een campagne met de volgende opties in de console verschijnen:

![&#x200B; van het dashboard van een campagne, kan de exploitant een campagne bekijken en annuleren, maar ook het wijzigen, en leveringen, documenten, en taken aan het toevoegen.](assets/operation_from_console.png)

Terwijl de opties bij toegang tot het web vooral het weergeven van:

![&#x200B; van browser, kan de zelfde exploitant de campagne slechts bekijken en annuleren.](assets/operation_from_web.png)

Leer meer over het gebruiken van de Webinterface in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-create.html?lang=nl#use-the-web-interface-){target=_blank}.

### Talen {#languages}

De taal wordt geselecteerd wanneer u uw Adobe Campaign Classic-exemplaar installeert.

![](assets/language.png)

U kunt kiezen uit de volgende talen:

* Engels (VK)
* Engels (VS)
* Frans
* Duits
* Japans

De taal die u voor uw Adobe Campaign Classic-exemplaar hebt gekozen, kan van invloed zijn op de datum- en tijdnotatie. Voor meer op dit, verwijs naar de [&#x200B; Campagne v8 (console) documentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

Voor meer informatie over hoe te om een instantie tot stand te brengen, verwijs naar deze [&#x200B; pagina &#x200B;](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>De taal kan na het maken van de instantie niet meer worden gewijzigd.

## Basisbeginselen van navigatie {#navigation-basics}

De verschillende functies van het platform zijn onderverdeeld in kernmogelijkheden: gebruik de verbindingen die u in de hoogste sectie van de interface ziet om tot hen toegang te hebben.

![](assets/overview_home.png)

De lijst met kernmogelijkheden waartoe u toegang hebt, is afhankelijk van de pakketten en invoegtoepassingen die u hebt geïnstalleerd en van uw toegangsrechten.

### Bladeren door pagina&#39;s {#browsing-pages}

Elk vermogen omvat een reeks functionaliteiten die op taak betrekking hebbende behoeften en gebruikscontext worden gebaseerd. Met de koppeling **[!UICONTROL Profiles and targets]** gaat u bijvoorbeeld naar de lijsten met ontvangers, abonnementsservices, bestaande workflows voor activering en de sneltoetsen voor het maken van deze elementen.

De lijsten zijn beschikbaar via de koppeling **[!UICONTROL Lists]** in het linkergedeelte van de interface **[!UICONTROL Profiles and Targets]** .

![](assets/recipient_list_overview.png)

### Tabs gebruiken {#using-tabs}

* Wanneer u op een kernfunctie of een koppeling klikt, wordt de huidige pagina vervangen door de relevante pagina. Klik op de knop **[!UICONTROL Back]** op de werkbalk om terug te gaan naar de vorige pagina. Als u wilt terugkeren naar de startpagina, klikt u op de knop **[!UICONTROL Home]** .

  ![](assets/d_ncs_user_interface_back_home_buttons.png)

* In het geval van een menu of een snelkoppeling naar een scherm (zoals een webtoepassing, programma, levering, rapport, enz.), wordt de bijbehorende pagina weergegeven op een ander tabblad. Op deze manier kunt u van de ene pagina naar de andere bladeren met de tabbladen.

  ![](assets/d_ncs_user_interface_tabs.png)

### Een element maken {#creating-an-element}

In elke sectie met kernmogelijkheden kunt u bladeren door de beschikbare elementen. Gebruik hiervoor de sneltoetsen in de sectie **[!UICONTROL Browsing]** . Met de koppeling **[!UICONTROL Other choices]** hebt u toegang tot alle andere pagina&#39;s, ongeacht de omgeving.

U kunt een nieuw element (levering, webtoepassing, workflow, enz.) maken met de sneltoetsen in de sectie **[!UICONTROL Create]** links van het scherm. Gebruik de knop **[!UICONTROL Create]** boven de lijst om nieuwe elementen aan de lijst toe te voegen.

Gebruik bijvoorbeeld op de leveringspagina de knop **[!UICONTROL Create]** om een nieuwe levering te maken.

![](assets/d_ncs_user_interface_tab_add_del.png)


## Adobe Campaign-verkenner gebruiken {#using-adobe-campaign-explorer}

De Adobe Campaign-verkenner is toegankelijk via het werkbalkpictogram. Hiermee hebt u toegang tot alle Adobe Campaign-mogelijkheden, configuratieschermen en een gedetailleerdere weergave van enkele platformelementen.

Meer over de ontdekkingsreiziger van Adobe Campaign leren, verwijs naar deze pagina&#39;s in de **Campagne v8 (console) documentatie**:

* [&#x200B; overzicht van het gebruikersinterface van de Campagne &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}

* [&#x200B; montages UI van de Campagne &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/ui-settings){target=_blank}

* [&#x200B; beheert omslagen en meningen in de ontdekkingsreiziger &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}


## Werken met gegevens {#work-with-data}

### Gegevens filteren {#filters}

Het filtreren van gegevens is het proces om een dataset aan slechts die verslagen te vernauwen die specifieke criteria aanpassen. Deze subset kan vervolgens worden gebruikt voor doelgerichte acties (zoals updates of het creëren van een publiek) of voor analyse.

Tijdens het bladeren in Campagne worden gegevens weergegeven in lijsten. U kunt ingebouwde filters toepassen om tot een bepaalde ondergroep, zoals quarantined adressen, niet-gerichte ontvangers, of verslagen binnen een specifieke leeftijdswaaier of aanmaakdatum snel toegang te hebben. Bovendien kunt u aangepaste filters maken, deze opslaan voor toekomstig gebruik en deze delen met andere campagnegebruikers.

Leer hoe te **toegang, ontwerp en aandeelfilters** in de [&#x200B; Campagne v8 (console) documentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.

### De database opvragen{#about-queries-in-campaign}

Het vraaghulpmiddel is beschikbaar op diverse niveaus van de toepassing en kan worden gebruikt om doelpopulaties, segmentklanten, extract en filter het volgen logboeken te bepalen, filters, en meer tot stand te brengen.

+++Over de algemene query-editor

Het verstrekt een specifieke medewerker — de generische vraagredacteur — toegankelijk van het **[!UICONTROL Tools > Generic query editor...]** menu. Deze redacteur laat gegevensbestandvragen toe om, informatie te halen te organiseren, te groeperen en te sorteren. Het kan bijvoorbeeld ontvangers ophalen die tijdens een bepaalde periode meer dan n keer op een nieuwsbrief hebben geklikt.

De generische vraagredacteur centraliseert alle het vragen mogelijkheden. Het staat de verwezenlijking en de opslag van beperkingsfilters toe, die dan in andere contexten, zoals het vakje van de Vraag van een het richten werkschema kunnen worden opnieuw gebruikt.

![&#x200B; heb toegang tot de vraagredacteur en selecteer een lijst &#x200B;](assets/query_editor_nveau_21.png)

+++

>[!BEGINTABS]

>[!TAB  Vraag het gegevensbestand ]

De stappen om een vraag tot stand te brengen zijn gedetailleerd in **[Campagne v8 (console) documentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/data/query/query-editor){target=_blank}**


[![afbeelding](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/data/query/query-editor){target=_blank}


>[!TAB  voeg een vraag in een werkschema toe ]

Leer de belangrijkste stappen met betrekking tot de vraagverwezenlijking in de context van een werkschema in de **[Campagne v8 documentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/automation/workflows/wf-activities/targeting-activities/query){target=_blank}**

[![afbeelding](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/nl/docs/campaign/automation/workflows/wf-activities/targeting-activities/query){target=_blank}

>[!TAB  voorwaarden van de Filter ]

Om uw vraag te ontwerpen, moet u de het filtreren voorwaarden in de vraagredacteur selecteren. De beschikbare mogelijkheden en gebruiksgevallen zijn gedetailleerd in de **[documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/data/query/filter-conditions){target=_blank}**

[![afbeelding](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/data/query/filter-conditions){target=_blank}

>[!ENDTABS]

### Lijsten beheren {#manage-and-customize-lists}

In de de cliëntconsole van de Campagne, worden de gegevens getoond in lijsten. U kunt deze lijsten aan uw behoeften aanpassen. U kunt bijvoorbeeld kolommen, filtergegevens, telrecords toevoegen, uw instellingen opslaan en delen.

Leer om lijsten **in de** Campagne v8 (console) documentatie [&#x200B; te beheren en aan te passen.](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/ui-settings#customize-lists){target=_blank}

### Opsommingen beheren{#managing-enumerations}

Een opsomming (ook wel een gedetailleerde lijst genoemd) is een vooraf gedefinieerde lijst met waarden die u kunt gebruiken om bepaalde velden in te vullen. Opsommingen helpen bij het standaardiseren van veldwaarden, het consistenter maken van gegevens en het vereenvoudigen van query&#39;s.

Wanneer deze zijn gedefinieerd, worden de waarden weergegeven in een vervolgkeuzelijst. Een waarde kan rechtstreeks worden geselecteerd of worden ingevoerd met behulp van voorspellende invoer, die overeenkomende items voorstelt en voltooit. Sommige velden bevatten vooraf gedefinieerde opsommingen en indien nodig kunnen aanvullende opsommingen worden gemaakt.

Leer meer hoe te **met opsommingen** in [&#x200B; Adobe Campaign v8 (console) documentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank} werken.

## Video over zelfstudie {#video}

Deze video toont de Campaign Classic-werkruimte.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)
