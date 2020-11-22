---
solution: Campaign Classic
product: campaign
title: De pijplijn configureren
description: Leer hoe te om de pijpleiding te vormen
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 1%

---


# Pipeline configureren {#configuring-pipeline}

De parameters van de authentificatie zoals klantenidentiteitskaart, de privé sleutel, en het authentificatieeindpunt worden gevormd in de dossiers van de instantieconfiguratie.
De lijst met triggers die moeten worden verwerkt, is geconfigureerd in een optie in JSON-indeling.
De triggers worden gebruikt voor het activeren van een campagneworkflow die e-mails verzendt. De campagne is opgezet zodat een klant die beide triggergebeurtenissen heeft een e-mail ontvangt.

>[!CAUTION]
>
>In het geval van Hybride plaatsing, zorg ervoor dat de pijpleiding op een halverwege instantie wordt gevormd.

## Vereisten {#prerequisites}

Voordat u deze configuratie start, moet u controleren of u deze configuratie gebruikt:

* Minimaal Adobe Campaign 20.3-release
* Adobe Analytics Standard-versie

U hebt ook het volgende nodig:

* Adobe I/O-projectverificatie
* een geldige IMSOrgID, de id van de Experience Cloud-klant met Adobe Analytics toegevoegd
* Een ontwikkelaarstoegang tot de IMS-organisatie
* triggerconfiguratie uitgevoerd in Adobe Analytics

## Verificatie- en configuratiebestanden {#authentication-configuration}

De authentificatie wordt vereist aangezien de pijpleiding in Adobe Experience Cloud wordt ontvangen.
Het gebruikt een paar openbare en privé sleutels. Dit proces heeft dezelfde functie als een gebruiker/wachtwoord, maar is veiliger.
Verificatie wordt ondersteund voor de Marketing Cloud via Adobe I/O-project.

## Stap 1: Adobe I/O-project maken/bijwerken {#creating-adobe-io-project}

Voor Gehoste klanten, kunt u een kaartje van de klantenzorg tot stand brengen om uw organisatie met de Tokens van de Technische Rekening van Adobe I/O voor de integratie van Triggers toe te laten.

Raadpleeg voor klanten op locatie de pagina [Adobe I/O configureren voor Adobe Experience Cloud-triggers](../../integrations/using/configuring-adobe-io.md) . Merk op dat u moet selecteren **[!UICONTROL Adobe Analytics]** terwijl het toevoegen van API aan de Adobe I/O referentie.

## Stap 2: De pijplijnoptie NmsPipeline_Config configureren {#configuring-nmspipeline}

Zodra de authentificatie wordt geplaatst, zal de pijpleiding de gebeurtenissen terugwinnen. Het zal slechts trekkers verwerken die in Adobe Campaign worden gevormd. De trekker moet van Adobe Analytics zijn geproduceerd en aan de pijpleiding geduwd die slechts trekkers zal verwerken die in Adobe Campaign worden gevormd.
De optie kan ook met een vervanging worden gevormd om alle trekkers ongeacht de naam te vangen.

1. In Adobe Campaign opent u het optiemenu onder **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** in de **[!UICONTROL Explorer]**.

1. Selecteer de **[!UICONTROL NmsPipeline_Config]** optie.

1. In het **[!UICONTROL Value (long text)]** veld kunt u de volgende JSON-code plakken, die twee triggers opgeeft. U moet ervoor zorgen dat opmerkingen worden verwijderd.

   ```
   {
   "topics": [ // list of "topics" that the pipelined is listening to.
      {
           "name": "triggers", // Name of the first topic: triggers.
           "consumer": "customer_dev", // Name of the instance that listens.  This value can be found on the monitoring page of Adobe Campaign.
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

1. U kunt ook de volgende JSON-code plakken waarmee alle triggers worden afgevangen.

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

### De parameter Consumenten {#consumer-parameter}

De pijpleiding werkt als een leverancier- en consumentenmodel. Berichten worden alleen voor een individuele consument verbruikt: elke consument krijgt zijn eigen exemplaar van de berichten .

De **consumentenparameter** identificeert het geval als één van deze consumenten. De identiteit van de instantie zal de pijpleiding roepen. U kunt deze vullen met de instantienaam die u kunt vinden op de pagina Bewaking van de clientconsole.

De pijpleidingsdienst houdt spoor van de berichten die door elke consument worden teruggewonnen. Door verschillende consumenten voor verschillende instanties te gebruiken, kunt u ervoor zorgen dat elk bericht naar elke instantie wordt verzonden.

### Aanbevelingen voor de optie Pipet {#pipeline-option-recommendation}

Om de optie van de Pijl te vormen, zou u deze aanbevelingen moeten volgen:

* Voeg triggers toe of bewerk triggers onder **[!UICONTROL Triggers]**, u moet de rest niet bewerken.
* Controleer of de JSON geldig is. U kunt een JSON-validatie gebruiken. Raadpleeg bijvoorbeeld deze [website](http://jsonlint.com/) .
* &quot;name&quot; komt overeen met de trigger-id. Met jokerteken &quot;*&quot; worden alle triggers afgevangen.
* &quot;Consumenten&quot; komt overeen met de naam van de oproepende instantie of toepassing.
* Pijpleidingen ondersteunen ook het onderwerp &quot;aliassen&quot;.
* Nadat u wijzigingen hebt aangebracht, moet u de pipet altijd opnieuw starten.

## Stap 3: Optionele configuratie {#step-optional}

U kunt enkele interne parameters wijzigen op basis van de vereisten voor de belasting, maar zorg dat u deze test voordat u ze in productie neemt.

De lijst met optionele parameters is hieronder te vinden:

| Option | Beschrijving |
|:-:|:-:|
| appName(Legacy) | AppID van de OAuth-toepassing die is geregistreerd in de Legacy Oath-toepassing waar de openbare sleutel is geüpload. Raadpleeg [deze pagina](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.) voor meer informatie |
| authGatewayEndpoint(Legacy) | URL om gatewaytokens te krijgen. Standaard: ```https://api.omniture.com``` |
| authPrivateKey(Verouderd) | De persoonlijke sleutel, het openbare deel dat in de Oudere Oath-toepassing wordt geüpload, AES gecodeerd met de optie XtkKey: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Schakel authentificatie uit, verbindend zonder gatewaytokens slechts door sommige eindpunten van de ontwikkelingsPijpleiding zal worden goedgekeurd. |
| findPipelineEndpoint | URL om het eindpunt te vinden van de Diensten van de Pijpleiding dat voor deze huurder moet worden gebruikt. Standaard: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | De periode tussen twee dumps van het proces van de interne staat in ```var/INSTANCE/pipelined.json.```<br> intern land is hier ook op verzoek toegankelijk: ```http://INSTANCE:7781/pipelined/status``` |
| forcePipelineEndpoint | Maak de opsporing van PipelineServicesEndpoint onbruikbaar om het te dwingen |
| monitorServerPort | Met behulp van een leidinggevend proces wordt naar deze poort geluisterd om het interne statusproces hier te verzorgen: ```http://INSTANCE:PORT/pipelined/status```. <br>Standaard is 7781 |
| pointerFlushMessageCount | Wanneer dit aantal berichten wordt verwerkt, zullen de compensatie in het gegevensbestand worden bewaard. <br> Standaard is 1000 |
| pointerFlushPeriodSec | Na deze periode worden de offsets opgeslagen in de database. <br>Standaard is 5 (sec) |
| processingJSThreads | Aantal specifieke draden verwerkend berichten met de schakelaars van douaneJS. <br> Standaard is 4 |
| processingThreads | Aantal specifieke draden verwerkend berichten met ingebouwde code. <br>Standaard is 4 |
| retryPeriodSec | Vertraging tussen pogingen bij verwerkingsfouten. <br>Standaard is 30 (sec) |
| retryValiditySec | Verwijder het bericht als het na deze periode niet succesvol is verwerkt (te veel pogingen). <br>De standaardwaarde is 300 (sec) |

### Automatische start van het pijplijnproces {#pipelined-process-autostart}

Het pijplijnproces moet automatisch worden gestart.

Voor dit, plaats het &lt; pijpleiding > element in het config dossier aan autostart= &quot;waar&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### Opnieuw opstarten van het pijlproces {#pipelined-process-restart}

De wijzigingen worden pas van kracht als u de toepassing opnieuw start:

```
nlserver restart pipelined@instance
```

## Stap 4: Validatie {#step-validation}

Volg onderstaande stappen om de installatie van de pijplijn voor provisioning te valideren:

* Zorg ervoor dat het [!DNL pipelined] proces wordt uitgevoerd.
* Controleer pipelined.log voor de logboeken van de pijpleidingsverbinding.
* Controleer de verbinding en of pingelt wordt ontvangen. Gehoste klanten kunnen de Controle van de Console van de Cliënt gebruiken.
