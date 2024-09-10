---
product: campaign
title: JavaScript-scripts en -sjablonen
description: JavaScript-scripts en -sjablonen
feature: Workflows
exl-id: 4a3647d1-cf8c-4867-871e-472287be7c6a
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1247'
ht-degree: 1%

---

# JavaScript-scripts en -sjablonen{#javascript-scripts-and-templates}



Met scripts kunt u waarden berekenen, gegevens uitwisselen tussen verschillende taken in het proces en specifieke bewerkingen uitvoeren met behulp van SOAP aanroepen.

Scripts zijn alomtegenwoordig in een workflowdiagram:

* Alle activiteiten hebben initialisatiescripts. Een initialisatiescript wordt uitgevoerd wanneer de activiteit wordt geactiveerd en kan worden gebruikt om variabelen te initialiseren en de eigenschappen te wijzigen.
* De activiteit van de code van &#39;JavaScript&#39; wordt eenvoudig gebruikt om een manuscript uit te voeren.
* De &#39;Test&#39;-activiteit evalueert JavaScript-expressies om de juiste overgang te activeren.
* De meeste tekstvelden zijn JavaScript-sjablonen: JavaScript-expressies kunnen worden opgenomen tussen &lt;%= en %>. Deze velden bevatten een knop waarmee een vervolgkeuzelijst wordt geopend waarmee u expressies kunt invoeren.

  ![](assets/script-button.png)

## Objecten blootgesteld {#objects-exposed}

JavaScripts die in de context van een werkstroom worden uitgevoerd, hebben toegang tot een reeks extra globale objecten.

* **instantie**: Vertegenwoordigt het werkschema dat wordt uitgevoerd. Het schema van dit voorwerp is **xtk:werkschema**.
* **taak**: Vertegenwoordigt de taken die worden uitgevoerd. Het schema van dit voorwerp is **xtk:workflowTask**.
* **gebeurtenis**: Vertegenwoordigt de gebeurtenissen die de taak activeerde die wordt uitgevoerd. Het schema van dit voorwerp is **xtk:workflowEvent**. Dit voorwerp wordt niet geïnitialiseerd voor **EN** type activiteiten die van veelvoudige overgangen zijn geactiveerd.
* **gebeurtenissen**: Vertegenwoordigt de lijst van gebeurtenissen die de huidige taak activeerde. Het schema van dit voorwerp is **xtk:workflowEvent**. Deze lijst bevat gewoonlijk één element maar kan verscheidene voor **bevatten EN-sluit zich** typeactiviteiten aan die gebaseerd op verscheidene overgangen zijn geactiveerd.
* **activiteit**: Vertegenwoordigt het model van de taak die wordt uitgevoerd. Het schema van dit object is afhankelijk van het type activiteit. Dit object kan worden gewijzigd door het initialisatiescript, in andere scripts kunnen wijzigingen met onbepaalbare effecten worden toegepast.

De eigenschappen die voor deze objecten beschikbaar zijn, kunnen in een vervolgkeuzelijst worden weergegeven door op de knop rechts van de scriptwerkbalk te klikken.

>[!CAUTION]
>
>De eigenschappen van deze objecten zijn alleen-lezen, behalve de subeigenschappen van de eigenschap vars.
>  
>De meeste van deze eigenschappen worden alleen bijgewerkt na het uitvoeren van een elementaire taak of wanneer de instantie is gepassioneerd. De waarden die worden gelezen, komen niet noodzakelijkerwijs overeen met de huidige status, maar met de vorige status.

**Voorbeeld**

In dit voorbeeld, en in de volgende voorbeelden, creeer een werkschema dat de code van a **JavaScript** activiteit en a **Eind** activiteit zoals aangetoond in het volgende diagram omvat.

![](assets/script-1.png)

Dubbelklik de **code van JavaScript** activiteit en neem het volgende manuscript op:

```
logInfo("Label: " + instance.label)
logInfo("Start date: " + task.creationDate)
```

De functie **[!UICONTROL logInfo(message)]** voegt een bericht in het logbestand in.

Klik op **[!UICONTROL OK]** om de assistent voor maken te sluiten en start de workflow met de actieknoppen in de rechterbovenhoek van de lijst met workflows. Raadpleeg het logbestand aan het einde van de uitvoering. Er moeten twee berichten worden weergegeven die overeenkomen met het script: de ene bevat het label van de workflow en de andere de datum waarop het script is geactiveerd.

## Variabelen {#variables}

De variabelen zijn de vrije eigenschappen van de objecten **[!UICONTROL instance]** , **[!UICONTROL task]** en **[!UICONTROL event]** . De JavaScript-typen die voor deze variabelen zijn geautoriseerd, zijn **[!UICONTROL string]** , **[!UICONTROL number]** en **[!UICONTROL Date]** .

### Instantievariabelen {#instance-variables}

De instantievariabelen (**[!UICONTROL instance.vars.xxx]**) zijn vergelijkbaar met globale variabelen. Ze worden door alle activiteiten gedeeld.

### Taakvariabelen {#task-variables}

De taakvariabelen (**[!UICONTROL task.vars.xxx]**) zijn vergelijkbaar met lokale variabelen. Ze worden alleen gebruikt door de huidige taak. Deze variabelen worden gebruikt door permanente activiteiten om gegevens te bewaren en worden soms gebruikt om gegevens tussen de verschillende manuscripten van een zelfde activiteit uit te wisselen.

### Gebeurtenisvariabelen {#event-variables}

De gebeurtenisvariabelen (**[!UICONTROL vars.xxx]**) laten de uitwisseling van gegevens tussen de elementaire taken van een werkschemaproces toe. Deze variabelen worden doorgegeven door de taak die de actieve taak heeft geactiveerd. Het is mogelijk deze te wijzigen en nieuwe te definiëren. Deze worden vervolgens doorgegeven aan de volgende activiteiten.

>[!CAUTION]
>
>In het geval van [ AND-sluit zich ](and-join.md) typeactiviteiten aan, worden de variabelen samengevoegd maar als een zelfde variabele tweemaal wordt bepaald, is er een conflict en de waarde blijft onbepaald.

Gebeurtenissen zijn de meest gebruikte variabelen en moeten bij voorkeur worden gebruikt in plaats van instantievariabelen.

Bepaalde gebeurtenisvariabelen worden door de verschillende activiteiten gewijzigd of gelezen. Dit zijn allemaal tekenreeksvariabelen. Met een exportbewerking wordt bijvoorbeeld de variabele **[!UICONTROL vars.filename]** ingesteld met de volledige naam van het bestand dat zojuist is geëxporteerd. Al deze gelezen of gewijzigde variabelen worden gedocumenteerd in [ Ongeveer activiteiten ](about-activities.md), in de secties **parameters van de Input** en **parameters van de Output** van de activiteiten.

### Gebruiksscenario’s {#example}

>[!NOTE]
>
>De extra gevallen van het werkschemagebruik zijn beschikbaar in [ deze sectie ](about-workflow-use-cases.md).

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

1. Neem het werkschema van het voorafgaande voorbeeld en vervang het manuscript van de **activiteit van de Code van JavaScript** met het volgende manuscript:

   ```
   instance.vars.foo = "bar1"
   vars.foo = "bar2"
   task.vars.foo = "bar3"
   ```

1. Voeg het volgende manuscript aan het initialiseringsmanuscript van de **Eindactiviteit** toe:

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

Dit voorbeeld toont aan dat de activiteit na **Code van JavaScript** tot de instantievariabelen en gebeurtenisvariabelen toegang heeft, maar de taakvariabelen zijn niet toegankelijk van de buitenkant (&quot;niet gedefiniëerd&quot;).

### Een instantievariabele in een query aanroepen {#calling-an-instance-variable-in-a-query}

Nadat u een instantievariabele hebt opgegeven in een activiteit, kunt u deze opnieuw gebruiken in een workflowquery.

Aldus, om een veranderlijke **instance.vars.xxx te roepen = &quot;yyy&quot;** in een filter, ga **$ (instantie/vars/xxx)** in.

Bijvoorbeeld:

1. Creeer een instantievariabele die de interne naam van een levering via **[!UICONTROL JavaScript code]** bepaalt: **instance.vars.deliveryIN = &quot;DM42&quot;**.

   ![](assets/wkf_js_activity_1.png)

1. Creeer een vraag het waarvan richten en het filtreren dimensies de ontvangers zijn. In de voorwaarden, specificeer dat u alle ontvangers zou willen vinden die de levering werden verzonden die door de variabele wordt gespecificeerd.

   Ter herinnering, deze informatie wordt opgeslagen in de leveringslogboeken.

   Om de instantievariabele in de **[!UICONTROL Value]** kolom van verwijzingen te voorzien, ga **$ (instantie/vars/@deliveryIN)** in.

   Het werkschema zal de ontvangers van de levering terugkeren DM42.

   ![](assets/wkf_var_in_query.png)

## Geavanceerde functies {#advanced-functions}

Naast de standaard JavaScript-functies zijn er speciale functies beschikbaar voor het bewerken van bestanden, het lezen of wijzigen van gegevens in de database of het toevoegen van berichten aan het logbestand.

### Dagboek {#journal}

**[!UICONTROL logInfo(message)]** is in de bovenstaande voorbeelden uitgebreid. Deze functie voegt een informatiebericht aan het dagboek toe.

**[!UICONTROL logError(message)]** voegt een foutbericht toe aan het logbestand. Het script onderbreekt de uitvoering en de workflow verandert in de status van een fout (de instantie wordt standaard gepauzeerd).

## Initialisatiescript {#initialization-script}

Onder bepaalde voorwaarden kunt u een eigenschap van een activiteit wijzigen op het moment van uitvoering.

De meeste eigenschappen van activiteiten kunnen dynamisch worden berekend, of gebruikend een malplaatje van JavaScript of omdat de werkschemaeigenschappen uitdrukkelijk toestaan dat de waarde door een manuscript wordt berekend.

Voor andere eigenschappen moet u het initialisatiescript echter gebruiken. Dit script wordt geëvalueerd voordat de taak wordt uitgevoerd. De variabele **[!UICONTROL activity]** verwijst naar de activiteit die overeenkomt met de taak. De eigenschappen van deze activiteit kunnen worden gewijzigd en zullen slechts deze taak beïnvloeden.

**Verwante onderwerpen**
[ Voorbeelden van code van JavaScript in werkschema&#39;s ](javascript-in-workflows.md)
