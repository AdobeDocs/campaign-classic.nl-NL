---
product: campaign
title: Best practices voor workflows
description: Meer informatie over best practices voor de campagnereschemap
feature: Workflows
exl-id: 39c57f61-2629-4214-91e4-cb97dc039deb
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1381'
ht-degree: 5%

---

# Best practices voor workflows{#workflow-best-practices}



## Uitvoering en prestaties {#execution-and-performance}

Hieronder vindt u algemene richtlijnen voor het optimaliseren van de campagneprestaties, waaronder tips en trucs voor het toepassen op uw workflows.

De richtlijnen van het oplossen van problemen met betrekking tot werkstroomuitvoering zijn ook beschikbaar in [ Campaign Classic v7 de Gids van de Productie ](../../production/using/workflow-execution.md).

### Logboeken {#logs}

De JavaScript-methode **[!UICONTROL logInfo()]** is een ideale oplossing voor foutopsporing in een workflow. Het is nuttig maar het moet zorgvuldig worden gebruikt, vooral voor activiteiten die vaak in werking worden gesteld: het kan de logboeken overladen en beduidend de grootte van de logboeklijst verhogen. Maar misschien hebt u ook meer nodig dan **[!UICONTROL logInfo()]** .

Er zijn twee aanvullende oplossingen beschikbaar om u te helpen:

* **houd het resultaat van tussentijdse populaties tussen twee uitvoeringen**

  Met deze optie blijven tijdelijke tabellen tussen twee uitvoeringen van een workflow staan. Deze vindt u op het tabblad **[!UICONTROL General]** van de eigenschappen van de workflow en kan worden gebruikt voor ontwikkeling en testdoeleinden om gegevens te controleren en de resultaten te controleren. U kunt deze optie in ontwikkelomgevingen gebruiken, maar nooit in productieomgevingen. Het houden van tijdelijke lijsten zou in de grootte van het gegevensbestand kunnen resulteren die beduidend en uiteindelijk de groottegrens wordt bereikt. Bovendien zal het de back-up vertragen.

  Alleen de werktabellen van de laatste uitvoering van de workflow worden bewaard. Werktabellen van vorige uitvoeringen worden leeggemaakt door de **[!UICONTROL cleanup]** -workflow, die dagelijks wordt uitgevoerd.

  >[!CAUTION]
  >
  >Deze optie mag nooit worden ingeschakeld in een productieworkflow. Deze optie wordt gebruikt om de resultaten te analyseren en is alleen ontworpen voor testdoeleinden en moet daarom alleen worden gebruikt in ontwikkelings- of testomgevingen.

* **SQL van het Logboek vragen in het dagboek**

  Deze optie is beschikbaar op het tabblad **[!UICONTROL Execution]** met workfloweigenschappen en registreert alle SQL-query&#39;s die door het gereedschap worden gegenereerd op basis van de verschillende activiteiten. Het is een goede manier om te zien wat er daadwerkelijk door het platform wordt uitgevoerd. Deze optie mag echter alleen tijdelijk tijdens de ontwikkeling worden gebruikt en niet tijdens de productie worden geactiveerd.

Leeg de logboeken als ze niet meer nodig zijn. De historie van de workflow wordt niet automatisch gewist: alle berichten worden standaard bijgehouden. De geschiedenis kan worden gewist via het menu **[!UICONTROL File > Actions]** of door op de knop Handelingen in de werkbalk boven de lijst te klikken. Selecteer Geschiedenis leegmaken.
Leren hoe te om uw logboeken te zuiveren, verwijs naar deze [ documentatie ](starting-a-workflow.md).

### Workflowplanning {#workflow-planning}

* Probeer de dag een stabiel activiteitsniveau te handhaven en pieken te vermijden om te voorkomen dat de instantie overbelast raakt. Hiervoor verdeelt u de werkstroom gelijkmatig over de dag.
* Plan de gegevensbelasting &#39;s nachts om de bronconflict te verminderen.
* De lange werkschema&#39;s kunnen potentieel een effect op de server en gegevensbestandmiddelen hebben. Splits de langste workflows om de verwerkingstijd te verkorten.
* Om de totale uitvoeringstijd te verkorten, vervang tijdrovende activiteiten door vereenvoudigde en snellere activiteiten.
* Gebruik niet meer dan 20 workflows tegelijk. Wanneer te veel werkstromen tegelijkertijd worden uitgevoerd, kan het systeem zonder middelen en instabiel worden. Voor meer informatie over waarom uw werkschema niet kan beginnen, verwijs naar dit [ artikel ](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).


### Uitvoeren in de motoroptie {#execute-in-the-engine-option}

Controleer in het **[!UICONTROL Workflow properties]** -venster nooit de optie **[!UICONTROL Execute in the engine]** . Als deze optie is ingeschakeld, heeft de workflow prioriteit en worden alle andere workflows gestopt door de workflow-engine totdat deze is voltooid.

![](assets/wf-execute-in-engine.png)

## Workfloweigenschappen {#workflow-properties}

### Workflowmappen {#workflow-folders}

Adobe raadt u aan uw workflows in een specifieke map te maken.

Als de workflow van invloed is op het hele platform (bijvoorbeeld op het opschonen van processen), kunt u overwegen een submap toe te voegen in de ingebouwde **[!UICONTROL Technical Workflows]** -map.

### Workflownaamgeving {#workflow-naming}

Om het gemakkelijker te maken om workflows te vinden en problemen op te lossen als ze niet naar behoren functioneren, wordt u aangeraden om uw workflows duidelijke namen en labels te geven. Vul het beschrijvingsveld van de workflow in om het uit te voeren proces samen te vatten, zodat de operator het gemakkelijk kan begrijpen.

Als de workflow deel uitmaakt van een proces waarbij meerdere workflows zijn betrokken, kunt u expliciet zijn wanneer u een label invoert. Het gebruik van nummers is een goede manier om de workflows te bestellen (met Label).

Bijvoorbeeld:

* 001 - Invoer - Ontvangers van de invoer
* 002 - Invoer - Uitvoer
* 003 - Invoer - Gegevens over de verkoop bij invoer
* 010 - Exporteren - Leveringslogboeken exporteren
* 011 - Logbestanden voor bijhouden van export

### Ernst van werkstroom {#workflow-severity}

U kunt de ernst van een workflow configureren in de workfloweigenschappen op het tabblad **[!UICONTROL Execution]** :

* Normaal
* Productie
* Kritiek

Door deze informatie op te geven tijdens het maken van een workflow, kunt u de ernst van het geconfigureerde proces beter begrijpen.

Deze optie heeft geen andere functionele gevolgen voor workflows dan campagneworkflows.

Workflows voor campagnes (workflows die zijn gemaakt als onderdeel van een campagne/bewerking) met een hogere prioriteit worden uitgevoerd als de campagne veel processen heeft die gelijktijdig moeten worden uitgevoerd. Standaard kunnen slechts 10 processen tegelijkertijd worden uitgevoerd in een campagne, volgens de optie NmsOperation_LimitConcurrency. Als een campagne bijvoorbeeld 25 workflows bevat, worden workflows met een hogere ernst uitgevoerd in de eerste pool van 10 processen.

### Workflowbewaking {#workflow-monitoring}

Alle geplande workflows die op productieomgevingen worden uitgevoerd, moeten worden gecontroleerd om te worden gewaarschuwd als er een fout optreedt.

In de werkschemaeigenschappen, selecteer een groep van de Supervisor, of het gebrek **[!UICONTROL Workflow supervisors]** of een douanegroep. Zorg ervoor dat ten minste één operator tot deze groep behoort, met een e-mailinstelling.

Voordat u een workflow gaat maken, moet u workflowsupervisors definiëren. Zij zullen per e-mail op de hoogte worden gesteld in het geval van fouten. Voor meer op dit, verwijs naar [ het Leiden fouten ](monitoring-workflow-execution.md#managing-errors).

Controleer regelmatig het tabblad **[!UICONTROL Monitoring]** om de algemene status van de actieve workflows weer te geven. Voor meer op dit, verwijs naar [ toezicht van de Instantie ](monitoring-workflow-execution.md#instance-supervision).

Met de Workflow HeatMap kunnen beheerders van het Adobe Campaign-platform de belasting op de instantie controleren en workflows dienovereenkomstig plannen. Voor meer op dit, verwijs naar [ Controle van het Werkschema ](heatmap.md).

## Werken met activiteiten {#using-activities}

>[!CAUTION]
>
>U kunt activiteiten kopiëren en plakken binnen dezelfde workflow. We raden echter niet aan plakactiviteiten over verschillende workflows te kopiëren. Sommige instellingen die zijn gekoppeld aan activiteiten zoals Leveringen en Planner kunnen leiden tot conflicten en fouten tijdens het uitvoeren van de doelworkflow. In plaats daarvan, adviseerden wij u **** werkschema&#39;s dupliceren. Voor meer informatie, zie [ het Dupliceren werkschema&#39;s ](building-a-workflow.md#duplicating-workflows).

### Naam van de activiteit {#name-of-the-activity}

Tijdens het ontwikkelen van uw workflow hebben alle activiteiten een naam, net als alle Adobe Campaign-objecten. Terwijl de naam door het hulpmiddel wordt geproduceerd, adviseren wij u het met een expliciete naam anders te noemen wanneer het vormen van het. Het risico dat het later gebeurt, is dat het de werkstroom kan onderbreken met activiteiten die de naam van een andere voorgaande activiteit gebruiken. Het zou dus moeilijk zijn om de namen achteraf bij te werken.

U vindt de naam van de activiteit op het tabblad **[!UICONTROL Advanced]** . Laat ze niet met de naam **[!UICONTROL query]** , **[!UICONTROL query1]** , **[!UICONTROL query11]** , maar geef ze expliciete namen, zoals **[!UICONTROL querySubscribedRecipients]** . Deze naam zal in het dagboek, en indien van toepassing in de SQL logboeken verschijnen, en dit zal helpen om het werkschema te zuiveren wanneer het vormen van het.

### Eerste en laatste activiteiten {#first-and-last-activities}

* Start de workflow altijd met een **[!UICONTROL Start]** activiteit of een **[!UICONTROL Scheduler]** activiteit. Indien relevant, kunt u ook een **[!UICONTROL External signal]** activiteit gebruiken.
* Gebruik bij het samenstellen van uw workflow slechts één **[!UICONTROL Scheduler]** activiteit per vertakking. Als de zelfde tak van een werkschema verscheidene planners (verbonden aan elkaar) heeft, zal het aantal uit te voeren taken exponentieel worden vermenigvuldigd, die het gegevensbestand aanzienlijk zou overbelasten. Deze regel is ook van toepassing op alle activiteiten met een tab **[!UICONTROL Scheduling & History]** . Leer meer op [ Plannend ](scheduler.md).

  ![](assets/wf-scheduler.png)

* Gebruik **[!UICONTROL End]** -activiteiten voor elke workflow. Hierdoor kan Adobe Campaign tijdelijke ruimte vrijmaken die wordt gebruikt voor berekeningen binnen workflows. Voor meer op dit, verwijs naar: [ Begin en eind ](start-and-end.md).

### JavaScript binnen een activiteit {#javascript-within-an-activity}

U kunt JavaScript toevoegen bij het initialiseren van een workflowactiviteit. Dit kan op het tabblad **[!UICONTROL Advanced]** van een activiteit van de activiteit worden gedaan.

Om het spotting van het werkschema gemakkelijker te maken, adviseren wij gebruikend dubbele streepjes aan het begin en eind van het activiteitenetiket als volgt: — Mijn etiket —.

### Signaal {#signal}

Meestal zult u niet weten waar het signaal vandaan komt. Om dit probleem te voorkomen, gebruikt u het veld **[!UICONTROL Comment]** op het tabblad **[!UICONTROL Advanced]** van de signaalactiviteit om de verwachte oorsprong van een signaal voor deze activiteit te documenteren.

![](assets/workflow-signal-bp.png)

## Workflow-update {#workflow-update}

Een productiewerkstroom mag niet rechtstreeks worden bijgewerkt. Tenzij het proces bestaat uit het maken van een campagne met sjabloonworkflows, moeten processen eerst op een ontwikkelomgeving worden getest. Na deze validatie kan de workflow worden geïmplementeerd en op productie worden gestart.

Alle tests uitvoeren in ontwikkelings- of testomgevingen, niet in productieomgevingen. In een dergelijk geval kunnen de prestaties niet worden gewaarborgd.

Gearchiveerde workflows kunnen op ontwikkelings- of testplatforms in een gearchiveerde map worden bewaard, maar de productieomgeving moet zo schoon mogelijk blijven. Oude workflows moeten uit de productieomgeving worden verwijderd als ze inactief zijn.
