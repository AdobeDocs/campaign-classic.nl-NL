---
product: campaign
title: De pijplijn configureren
description: Leer hoe te om de pijpleiding voor Campagne te vormen - de integratie van Triggers
feature: Triggers
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---

# De pijplijn configureren {#configuring-pipeline}

Verificatieparameters zoals de klant-id, de persoonlijke sleutel en het verificatie-eindpunt worden geconfigureerd in de configuratiebestanden van het exemplaar.

De lijst met te verwerken triggers wordt geconfigureerd in een optie in JSON-indeling.

De triggers worden gebruikt voor targeting door een campagneworkflow die e-mails verzendt. De campagne is zo opgezet dat een klant die beide trigger events heeft, een e-mail ontvangt.

## Vereisten {#prerequisites}

Controleer voordat u deze configuratie start of:

* Een Adobe Developer-project
* Een geldige identiteitskaart van de Organisatie - om uw identiteitskaart van de Organisatie te vinden, verwijs naar [ deze pagina ](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255){_blank}
* Een ontwikkelaar heeft toegang tot uw organisatie
* Een geldige triggerconfiguratie in Adobe Analytics

De authentificatie wordt vereist aangezien de pijpleiding in Adobe Experience Cloud wordt ontvangen. Het gebruikt een authentificatie die voor via een Project van Adobe Developer wordt gesteund.

## Stap 1: uw Adobe Developer-project maken/bijwerken {#creating-adobe-io-project}

Voor de integratie met Triggers moet u uw organisatie inschakelen met Adobe Developer-accounttokens.

Leer hoe te om uw technische rekening van Adobe in [ tot stand te brengen deze pagina ](../../integrations/using/oauth-technical-account.md). U moet **[!UICONTROL Adobe Analytics]** selecteren wanneer u API toevoegt aan de Adobe Developer-referentie.

## Stap 2: Vorm de pijpleidingsoptie {#configuring-nmspipeline}

Zodra de authentificatie wordt geplaatst, zal de pijpleiding de gebeurtenissen terugwinnen. Het verwerkt slechts trekkers die in Adobe Campaign worden gevormd. De trekker moet van Adobe Analytics zijn geproduceerd en aan de pijpleiding geduwd die slechts trekkers zal verwerken die in Adobe Campaign worden gevormd.

De optie kan ook met een vervanging worden gevormd om alle trekkers ongeacht de naam te vangen.

1. In Adobe Campaign opent u het optiemenu onder **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** in de **[!UICONTROL Explorer]** .

1. Selecteer de optie **[!UICONTROL NmsPipeline_Config]** .

1. In het veld **[!UICONTROL Value (long text)]** kunt u de volgende JSON-code plakken, die twee triggers opgeeft. Verwijder opmerkingen.

   ```json
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

   ```json
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

### De parameter Consumenten instellen {#consumer-parameter}

De pijpleiding werkt als een leverancier- en consumentenmodel. Berichten worden alleen voor een individuele consument verbruikt: elke consument krijgt zijn eigen exemplaar van de berichten.

De **consument** parameter identificeert de instantie als één van deze consumenten. De identiteit van de instantie zal de pijpleiding roepen. U kunt deze vullen met de instantienaam die u kunt vinden op de pagina Bewaking van de clientconsole.

De pijpleidingsdienst houdt spoor van de berichten die door elke consument worden teruggewonnen. Door verschillende consumenten voor verschillende instanties te gebruiken, kunt u ervoor zorgen dat elk bericht naar elke instantie wordt verzonden.

### Aanbevelingen voor de optie Pipet {#pipeline-option-recommendation}

Om de optie van de Pijl te vormen, zou u deze aanbevelingen moeten volgen:

* triggers toevoegen of bewerken onder **[!UICONTROL Triggers]** .
* Controleer of de JSON geldig is.
* De **parameter van de Naam** beantwoordt aan trekkeridentiteitskaart Met jokerteken &quot;*&quot; worden alle triggers afgevangen.
* De **consument** parameter beantwoordt aan de naam van de roepende instantie of toepassing.
* het `pipelined` proces steunt ook het &quot;aliassen&quot;onderwerp.
* U moet het proces altijd opnieuw starten `pipelined`nadat u wijzigingen hebt aangebracht.

## (facultatief) Stap 3: Aanvullende configuratie {#step-optional}

U kunt enkele interne parameters wijzigen op basis van de vereisten voor de belasting, maar zorg dat u deze test voordat u ze toepast op de productieomgeving.

De lijst met optionele parameters is:

| Optie | Beschrijving |
|:-:|:-:|
| appName(verouderd) | AppID van de OAuth-toepassing die is geregistreerd in de Legacy Oath-toepassing waar de openbare sleutel is geüpload. Raadpleeg deze [pagina](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) voor meer informatie |
| authGatewayEndpoint(verouderd) | URL om gatewaytokens te krijgen. Standaard: ```https://api.omniture.com``` |
| authPrivateKey(Verouderd) | De persoonlijke sleutel, het openbare gedeelte dat is geüpload in de oude Oath-toepassing, AES gecodeerd met de optie XtkKey: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(verouderd) | Schakel authentificatie uit, verbindend zonder gatewaytokens slechts door sommige eindpunten van de ontwikkelingsPijpleiding zal worden goedgekeurd. |
| findPipelineEndpoint | URL om het eindpunt van Pipeline Services te vinden dat voor deze tenant moet worden gebruikt. Verstek: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | De periode tussen twee dumps van het interne toestandsproces in ```var/INSTANCE/pipelined.json.``` <br> de interne toestand is hier ook on-demand toegankelijk: ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | Maak de opsporing van PipelineServicesEndpoint onbruikbaar om het te dwingen |
| monitorServerPort | Het pipelineproces luistert op deze poort om hier het interne statusproces te bieden: ```http://INSTANCE:PORT/pipelined/status```. <br>De standaardinstelling is 7781 |
| pointerFlushMessageCount | Wanneer dit aantal berichten is verwerkt, worden de offsets opgeslagen in de database. <br> De standaardwaarde is 1000 |
| pointerFlushPeriodSec | Na deze periode worden de offsets opgeslagen in de database. <br> Gebrek is 5 (sec) |
| verwerkingJSThreads | Aantal specifieke draden verwerkend berichten met de schakelaars van douaneJS. <br> Standaard is 4 |
| processingThreads | Aantal specifieke draden verwerkend berichten met ingebouwde code. <br> Standaard is 4 |
| opnieuw proberenPeriodSec | Vertraging tussen pogingen bij verwerkingsfouten. <br> Gebrek is 30 (sec) |
| opnieuw proberenValiditySec | Verwijder het bericht als het na deze periode niet succesvol is verwerkt (te veel pogingen). <br> Gebrek is 300 (sec) |

### Automatische start van het pijplijnproces {#pipelined-process-autostart}

Het `pipelined` -proces moet automatisch worden gestart.

Voor dit, plaats het `<` gepipelleerde `>` element in het config- dossier aan autostart= &quot;waar&quot;:

```sql
 <pipelined autoStart="true" ... "/>
```

### Opnieuw opstarten van het pijlproces {#pipelined-process-restart}

De wijzigingen worden pas van kracht als u de toepassing opnieuw start:

```sql
nlserver restart pipelined@instance
```

## Stap 4: Validatie {#step-validation}

Volg onderstaande stappen om de installatie van de pijplijn voor provisioning te valideren:

* Zorg ervoor dat het `pipelined` -proces wordt uitgevoerd.
* Controleer `pipelined.log` voor de logboeken van de pijpleidingsverbinding.
* Verifieer de verbinding en als pingelt worden ontvangen. Gehoste klanten kunnen de Controle van de Console van de Cliënt gebruiken.
