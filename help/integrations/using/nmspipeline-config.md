---
title: Integratie configureren
seo-title: Integratie configureren
description: Integratie configureren
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9957dabca4c63d504a3d06cf527a97b79fee46d5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# Pipeline, optie NmsPipeline_Config {#nmspipeline_config}

Zodra de authentificatiewerken, kunnen de pijpleiding de gebeurtenissen terugwinnen en hen verwerken. Het verwerkt slechts trekkers die in Adobe Campaign worden gevormd, die anderen negeren. De trigger moet uit Analytics zijn gegenereerd en vooraf naar de pijpleiding zijn geduwd.
De optie kan ook met een vervanging worden gevormd om alle trekkers ongeacht naam te vangen.

De triggers worden geconfigureerd in een optie onder **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. De optienaam is **[!UICONTROL NmsPipeline_Config]**. Het gegevenstype is &#39;lange tekst&#39; in JSON-indeling.

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
>De waarde [!DNL Trigger] UID voor een specifieke triggernaam in de Analytics-interface kan worden gevonden als onderdeel van de parameters van de URL-querytekenreeks in de Triggers-interface. De triggerType UID wordt overgegaan in de stroom van pijpleidingsgegevens en de code kan in pipe.JS worden geschreven om trekkerUID aan een gebruikersvriendelijk etiket in kaart te brengen dat in een kolom van de Naam van de Trekker in het pijpleidingsschemaEvents kan worden opgeslagen.

## De parameter voor de consument {#consumer-parameter}

De pijpleiding werkt met een &quot;leverancier en consument&quot;-model. Er kunnen veel consumenten op dezelfde rij staan. Berichten worden alleen voor een individuele consument &quot;verbruikt&quot;. Elke consument krijgt zijn eigen &quot;exemplaar&quot;van de berichten.

De parameter &quot;consument&quot; identificeert het geval als een van deze consumenten. Het is de identiteit van de instantie die de pijpleiding roept. U kunt deze vullen met de instantienaam. De pijpleidingsdienst houdt spoor van de berichten die door elke consument worden teruggewonnen. Het gebruiken van verschillende consumenten voor verschillende instanties zorgt ervoor dat elk bericht wordt verzonden naar elke instantie.

## Hoe te om de optie van de Pijpleiding te vormen {#configure-pipeline-option}

Voeg Experience Cloud-triggers toe of bewerk ze onder de &quot;triggers&quot;-array. de rest niet bewerken.
Controleer of de JSON geldig is met behulp van deze [website](http://jsonlint.com/).

* &quot;name&quot; is de trigger-id. Met een jokerteken &quot;*&quot; worden alle triggers afgevangen.
* &quot;Consumer&quot; is een unieke tekenreeks die de instantie van de server uniek identificeert. Dit kan doorgaans de instantienaam zelf zijn. Voor meerdere omgevingen (dev/stage/prod) dient u ervoor te zorgen dat deze uniek zijn voor elk van deze omgevingen, zodat elke instantie een kopie van het bericht krijgt.
* Pijpleidingen ondersteunen ook het onderwerp &quot;aliassen&quot;.

Start de pijplijn opnieuw nadat u wijzigingen hebt aangebracht.
