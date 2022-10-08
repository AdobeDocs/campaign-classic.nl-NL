---
product: campaign
title: Pipelineoptie NmsPipeline_Config
description: Pipelineoptie NmsPipeline_Config
audience: integrations
content-type: reference
source-git-commit: 36b10a49fe92853f98beeb9e7d2fea3f59b10b6f
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 3%

---


# Pipelineoptie NmsPipeline_Config {#nmspipeline_config}

![](../../assets/common.svg)

Zodra de authentificatie werkt, [!DNL pipelined] kan de gebeurtenissen ophalen en verwerken. Het verwerkt slechts trekkers die in Adobe Campaign worden gevormd, die anderen negeren. De trigger moet van Analytics zijn gegenereerd en vooraf naar de pijplijn zijn geduwd.
De optie kan ook met een vervanging worden gevormd om alle trekkers ongeacht naam te vangen.

De configuratie van de triggers wordt uitgevoerd in een optie, onder **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. De optienaam is **[!UICONTROL NmsPipeline_Config]**. Het gegevenstype is &#39;lange tekst&#39; in JSON-indeling.

In dit voorbeeld worden twee triggers opgegeven.

Plak de JSON-code van deze sjabloon in de waarde van de optie. Verwijder opmerkingen.

```
{
    "topics": [ // list of "topics" that the pipelined is listening to.
        {
            "name": "triggers", // Name of the first topic: triggers.
            "consumer": "customer_dev", // Name of the instance that listens. 
            "triggers": [ // Array of triggers. 
                {
                    "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                    "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
                }, {
                    "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                    "jsConnector": "cus:triggers.js" // Can use the same JS for all.
                },
            ]
        }
    ]
}
```

In dit tweede voorbeeld worden alle triggers afgevangen.

```
{
 "topics": [
    {
      "name": "triggers",
      "consumer":  "customer_dev",
      "triggers": [
        {
          "name": "*",
          "jsConnector": "cus:pipeline.js"
        }
      ]
    }
 ]
 }
```

>[!NOTE]
>
>De [!DNL Trigger] De waarde UID aan een specifieke trekkernaam in de interface van Analytics kan als deel van de URL querystring parameters in de interface Triggers worden gevonden. De triggerType UID wordt overgegaan in de stroom van pijpleidingsgegevens en de code kan in pipe.JS worden geschreven om trekkerUID aan een gebruikersvriendelijk etiket in kaart te brengen dat in een kolom van de Naam van de Trekker in het pijpleidingsschemaEvents kan worden opgeslagen.

## De parameter voor de consument {#consumer-parameter}

De pijpleiding werkt met een &quot;leverancier en consument&quot;-model. Er kunnen veel consumenten op dezelfde rij staan. Berichten worden alleen voor een individuele consument &quot;verbruikt&quot;. Elke consument krijgt zijn eigen &quot;exemplaar&quot;van de berichten.

De parameter &quot;consument&quot; identificeert het geval als een van deze consumenten. Het is de identiteit van de instantie die de pijpleiding roept. U kunt deze vullen met de instantienaam. De pijpleidingsdienst houdt spoor van de berichten die door elke consument worden teruggewonnen. Het gebruiken van verschillende consumenten voor verschillende instanties zorgt ervoor dat elk bericht wordt verzonden naar elke instantie.

## Hoe te om de optie van de Pijpleiding te vormen {#configure-pipeline-option}

Experience Cloud-triggers toevoegen of bewerken onder de &quot;triggers&quot;-array; de rest niet bewerken.
Ervoor zorgen dat de JSON geldig is met behulp van deze [website](https://jsonlint.com/).

* &quot;name&quot; is de trigger-id. Met een jokerteken &quot;*&quot; worden alle triggers afgevangen.
* &quot;Consumer&quot; is een unieke tekenreeks die de instantie van de server uniek identificeert. Dit kan doorgaans de instantienaam zelf zijn. Voor meerdere omgevingen (dev/stage/prod) dient u ervoor te zorgen dat deze uniek zijn voor elk van deze omgevingen, zodat elke instantie een kopie van het bericht krijgt.
* [!DNL Pipelined] ondersteunt ook het onderwerp &#39;&#39;aliassen&#39;&#39;.

Opnieuw starten [!DNL pipelined] na het aanbrengen van wijzigingen.
