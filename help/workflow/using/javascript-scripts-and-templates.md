---
product: campaign
title: JavaScript-scripts en -sjablonen
description: JavaScript-scripts en -sjablonen
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Workflows
exl-id: 4a3647d1-cf8c-4867-871e-472287be7c6a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 2%

---

# JavaScript-scripts en -sjablonen{#javascript-scripts-and-templates}



Met scripts kunt u waarden berekenen, gegevens uitwisselen tussen verschillende taken in het proces en specifieke bewerkingen uitvoeren met SOAP-aanroepen.

Scripts zijn alomtegenwoordig in een workflowdiagram:

* Alle activiteiten hebben initialisatiescripts. Een initialisatiescript wordt uitgevoerd wanneer de activiteit wordt geactiveerd en kan worden gebruikt om variabelen te initialiseren en de eigenschappen te wijzigen.
* De activiteit van de code van &#39;JavaScript&#39; wordt eenvoudig gebruikt om een manuscript uit te voeren.
* De activiteit van de &quot;Test&quot;evalueert uitdrukkingen JavaScript om de aangewezen overgang te activeren.
* De meeste tekstvelden zijn JavaScript-sjablonen: JavaScript-expressies kunnen worden opgenomen tussen &lt;%= en %>. Deze velden bevatten een knop waarmee een vervolgkeuzelijst wordt geopend waarmee u expressies kunt invoeren.

  ![](assets/script-button.png)

## Objecten blootgesteld {#objects-exposed}

JavaScripts die in de context van een werkstroom worden uitgevoerd, hebben toegang tot een reeks extra globale objecten.

* **instance**: Vertegenwoordigt de workflow die wordt uitgevoerd. Het schema van dit object is **xtk:workflow**.
* **taak**: Vertegenwoordigt de taken die worden uitgevoerd. Het schema van dit object is **xtk:workflowTask**.
* **event**: Vertegenwoordigt de gebeurtenissen die de uit te voeren taak hebben geactiveerd. Het schema van dit object is **xtk:workflowEvent**. Dit object is niet geïnitialiseerd voor **AND-join** type activiteiten die zijn geactiveerd via meerdere overgangen.
* **gebeurtenissen**: Vertegenwoordigt de lijst met gebeurtenissen die de huidige taak hebben geactiveerd. Het schema van dit object is **xtk:workflowEvent**. Deze tabel bevat gewoonlijk één element maar kan meerdere elementen bevatten voor **AND-join** type activiteiten die op basis van verschillende overgangen zijn geactiveerd.
* **activiteit**: Vertegenwoordigt het model van de taak die wordt uitgevoerd. Het schema van dit object is afhankelijk van het type activiteit. Dit object kan worden gewijzigd door het initialisatiescript, in andere scripts kunnen wijzigingen met onbepaalbare effecten worden toegepast.

De eigenschappen die voor deze objecten beschikbaar zijn, kunnen in een vervolgkeuzelijst worden weergegeven door op de knop rechts van de scriptwerkbalk te klikken.

>[!CAUTION]
>
>De eigenschappen van deze objecten zijn alleen-lezen, behalve de subeigenschappen van de eigenschap vars.
>  
>De meeste van deze eigenschappen worden alleen bijgewerkt na het uitvoeren van een elementaire taak of wanneer de instantie is gepassioneerd. De waarden die worden gelezen, komen niet noodzakelijkerwijs overeen met de huidige status, maar met de vorige status.

**Voorbeeld**

In dit voorbeeld en in de volgende voorbeelden maakt u een workflow die een **JavaScript-code** en **Einde** activiteit zoals weergegeven in het volgende diagram.

![](assets/script-1.png)

Dubbelklik op de knop **JavaScript-code** activiteit en voeg het volgende manuscript in:

```
logInfo("Label: " + instance.label)
logInfo("Start date: " + task.creationDate)
```

De **[!UICONTROL logInfo(message)]** de functie neemt een bericht in het logboek op.

Klikken **[!UICONTROL OK]** als u de wizard Maken wilt sluiten, start u de workflow met de actieknoppen in de rechterbovenhoek van de lijst met workflows. Raadpleeg het logbestand aan het einde van de uitvoering. Er moeten twee berichten worden weergegeven die overeenkomen met het script: de ene bevat het label van de workflow en de andere de datum waarop het script is geactiveerd.

## Variabelen {#variables}

De variabelen zijn de vrije eigenschappen van de **[!UICONTROL instance]**, **[!UICONTROL task]** en **[!UICONTROL event]** objecten. De JavaScript-typen die voor deze variabelen zijn geautoriseerd, zijn: **[!UICONTROL string]**, **[!UICONTROL number]** en **[!UICONTROL Date]**.

### Instantievariabelen {#instance-variables}

De instantievariabelen (**[!UICONTROL instance.vars.xxx]**) zijn vergelijkbaar met algemene variabelen. Ze worden door alle activiteiten gedeeld.

### Taakvariabelen {#task-variables}

De taakvariabelen (**[!UICONTROL task.vars.xxx]**) zijn vergelijkbaar met lokale variabelen. Ze worden alleen gebruikt door de huidige taak. Deze variabelen worden gebruikt door permanente activiteiten om gegevens te bewaren en worden soms gebruikt om gegevens tussen de verschillende manuscripten van een zelfde activiteit uit te wisselen.

### Gebeurtenisvariabelen {#event-variables}

De gebeurtenisvariabelen (**[!UICONTROL vars.xxx]**) de uitwisseling van gegevens mogelijk maken tussen de elementaire taken van een werkstroomproces. Deze variabelen worden doorgegeven door de taak die de actieve taak heeft geactiveerd. Het is mogelijk deze te wijzigen en nieuwe te definiëren. Deze worden vervolgens doorgegeven aan de volgende activiteiten.

>[!CAUTION]
>
>In het geval van [AND-join](and-join.md) type activiteiten, worden de variabelen samengevoegd maar als een zelfde variabele tweemaal wordt bepaald, is er een conflict en de waarde blijft onbepaald.

Gebeurtenissen zijn de meest gebruikte variabelen en moeten bij voorkeur worden gebruikt in plaats van instantievariabelen.

Bepaalde gebeurtenisvariabelen worden door de verschillende activiteiten gewijzigd of gelezen. Dit zijn allemaal tekenreeksvariabelen. Met een exportbewerking stelt u bijvoorbeeld de **[!UICONTROL vars.filename]** variabele met de volledige naam van het bestand dat zojuist is geëxporteerd. Al deze gelezen of gewijzigde variabelen worden beschreven in [Informatie over activiteiten](about-activities.md)in de afdelingen **Invoerparameters** en **Uitvoerparameters** van de activiteiten.

### Gebruiksscenario’s {#example}

>[!NOTE]
>
>Er zijn meer gevallen van workflowgebruik beschikbaar in [deze sectie](about-workflow-use-cases.md).

**Voorbeeld 1**

In dit voorbeeld wordt een instantievariabele gebruikt om dynamisch het gesplitste percentage te berekenen dat op een populatie moet worden toegepast.

1. Maak een workflow en voeg een activiteit Start toe.

1. Voeg een JavaScript-codeactiviteit toe en configureer deze om een instantievariabele te definiëren.

   Bijvoorbeeld: `instance.vars.segmentpercent = 10;`

   ![](assets/js_ex1.png)

1. Voeg een activiteit van de Vraag en doelontvangers volgens uw behoeften toe.

1. Voeg een gesplitste activiteit toe en vorm het om een willekeurige steekproef van de inkomende bevolking uit te voeren. U kunt het gewenste percentage kiezen. Deze wordt in dit voorbeeld ingesteld op 50%.

   Dit percentage wordt dynamisch bijgewerkt dankzij de eerder gedefinieerde instantievariabele.

   ![](assets/js_ex2.png)

1. Definieer een JS-voorwaarde in de sectie Initialisatiescript op het tabblad Geavanceerd van de activiteit Splitsen. De voorwaarde JS selecteert het willekeurige steekproefpercentage van de eerste overgang die uit de Gesplitste activiteit komt en werkt het aan een waarde bij die door de eerder gecreeerd instantievariabele wordt geplaatst.

   ```
   activity.transitions.extractOutput[0].limiter.percent = instance.vars.segmentpercent;
   ```

   ![](assets/js_ex3.png)

1. Zorg ervoor dat de aanvulling in een afzonderlijke overgang van de Gesplitste activiteit wordt geproduceerd en voeg de activiteiten van het Eind na elk van de uitgaande overgangen toe.

1. Sla de workflow op en voer deze uit. De dynamische sampling wordt toegepast volgens de instantievariabele.

   ![](assets/js_ex4.png)

**Voorbeeld 2**

1. Haal de workflow uit het vorige voorbeeld en vervang het script van het dialoogvenster **JavaScript-code** activiteit met het volgende manuscript:

   ```
   instance.vars.foo = "bar1"
   vars.foo = "bar2"
   task.vars.foo = "bar3"
   ```

1. Voeg het volgende script toe aan het initialisatiescript van het dialoogvenster **Einde** activiteit:

   ```
   logInfo("instance.vars.foo = " + instance.vars.foo)
   logInfo("vars.foo = " + vars.foo)
   logInfo("task.vars.foo = " + task.vars.foo)
   ```

1. Begin het werkschema, en bekijk dan het logboek.

   ```
   Workflow finished
   task.vars.foo = undefined
   vars.foo = bar2
   instance.vars.foo = bar1
   Starting workflow (operator 'admin')
   ```

In dit voorbeeld wordt getoond dat de volgende activiteit **JavaScript-code** Hiermee krijgt u toegang tot instantievariabelen en gebeurtenisvariabelen, maar de taakvariabelen zijn niet van buitenaf toegankelijk (&#39;undefined&#39;).

### Een instantievariabele in een query aanroepen {#calling-an-instance-variable-in-a-query}

Nadat u een instantievariabele hebt opgegeven in een activiteit, kunt u deze opnieuw gebruiken in een workflowquery.

Zo, om een variabele te roepen **instance.vars.xxx = &quot;yyy&quot;** in een filter typt u **$(instance/vars/xxx)**.

Bijvoorbeeld:

1. Maak een instantievariabele die de interne naam van een levering definieert via de **[!UICONTROL JavaScript code]**: **instance.vars.deliveryIN = &quot;DM42&quot;**.

   ![](assets/wkf_js_activity_1.png)

1. Creeer een vraag het waarvan richten en het filtreren dimensies de ontvangers zijn. In de voorwaarden, specificeer dat u alle ontvangers zou willen vinden die de levering werden verzonden die door de variabele wordt gespecificeerd.

   Ter herinnering, deze informatie wordt opgeslagen in de leveringslogboeken.

   Als u naar de instantievariabele in het dialoogvenster **[!UICONTROL Value]** kolom, Enter **$(instance/vars/@deliveryIN)**.

   Het werkschema zal de ontvangers van de levering terugkeren DM42.

   ![](assets/wkf_var_in_query.png)

## Geavanceerde functies {#advanced-functions}

Naast de standaard JavaScript-functies zijn er speciale functies beschikbaar voor het bewerken van bestanden, het lezen of wijzigen van gegevens in de database of het toevoegen van berichten aan het logbestand.

### Dagboek {#journal}

**[!UICONTROL logInfo(message)]** in de bovenstaande voorbeelden nader toegelicht. Deze functie voegt een informatiebericht aan het dagboek toe.

**[!UICONTROL logError(message)]** voegt een foutbericht toe aan het logbestand. Het script onderbreekt de uitvoering en de workflow verandert in de status van een fout (de instantie wordt standaard gepauzeerd).

## Initialisatiescript {#initialization-script}

Onder bepaalde voorwaarden kunt u een eigenschap van een activiteit wijzigen op het moment van uitvoering.

De meeste eigenschappen van activiteiten kunnen dynamisch worden berekend met behulp van een JavaScript-sjabloon of omdat de workfloweigenschappen expliciet toestaan dat de waarde door een script wordt berekend.

Voor andere eigenschappen moet u het initialisatiescript echter gebruiken. Dit script wordt geëvalueerd voordat de taak wordt uitgevoerd. De **[!UICONTROL activity]** variabele verwijst naar de activiteit die overeenkomt met de taak. De eigenschappen van deze activiteit kunnen worden gewijzigd en zullen slechts deze taak beïnvloeden.

**Verwante onderwerpen**
[Voorbeelden van JavaScript-code in workflows](javascript-in-workflows.md)
