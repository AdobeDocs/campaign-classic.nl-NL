---
title: De integratie configureren
seo-title: De integratie configureren
description: De integratie configureren
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 3%

---


# Pipeline configureren {#configuring-pipeline}

De parameters van de authentificatie zoals klantenidentiteitskaart, de privé sleutel, en het authentificatieeindpunt worden gevormd in de dossiers van de instantieconfiguratie.
De lijst van te verwerken trekkers wordt gevormd in een optie. Het heeft de JSON-indeling.
De trigger wordt direct verwerkt met JavaScript-code. Deze wordt opgeslagen in een databasetabel zonder dat er in realtime verdere verwerking plaatsvindt.
De triggers worden gebruikt voor het activeren van een campagneworkflow die e-mails verzendt. De campagne is opgezet zodat een klant die beide triggergebeurtenissen heeft een e-mail ontvangt.

## Vereisten {#prerequisites}

Het gebruik [!DNL Experience Cloud Triggers] in Campagne vereist:

* Adobe Campaign versie 6.11 build 8705 of hoger.
* Adobe Analytics Ultimate, Premium, Foundation, OD, Select, Prime, Mobile Apps, Select of Standard.

Voorwaardelijke configuraties zijn:

* Maak een bestand met een persoonlijke sleutel en maak vervolgens de Auth-toepassing die met die sleutel is geregistreerd.
* Configuratie van de triggers in Adobe Analytics.

De Adobe Analytics-configuratie valt buiten het bereik van dit document.

Adobe Campaign vereist de volgende informatie van Adobe Analytics:

* De naam van de Auth-toepassing.
* De IMSOrgId, de id van de Experience Cloud-klant.
* De namen van de triggers die in Analytics zijn geconfigureerd.
* De naam en indeling van de gegevensvelden die moeten worden afgestemd op de marketingdatabase.

Een deel van deze configuratie is een aangepaste ontwikkeling en vereist het volgende:

* Werken met kennis van JSON-, XML- en Javascript-parsering in Adobe Campaign.
* Werken met kennis van de API&#39;s QueryDef en Writer.
* Werken met codering en verificatie met persoonlijke sleutels.

>[!NOTE]
>
>Aangezien voor het bewerken van de JS-code technische vaardigheden vereist zijn, moet u er niet naar streven zonder het juiste begrip. <br>Triggers worden opgeslagen in een databasetabel. Daarom kunnen triggergegevens veilig worden gebruikt door marketingmedewerkers voor het maken van doelgerichte workflows.

## Verificatie- en configuratiebestanden {#authentication-configuration}

De authentificatie wordt vereist aangezien de Pijpleiding in Adobe Experience Cloud wordt ontvangen.
Als de server van de Marketing op gebouw wordt ontvangen, wanneer het aan Pijpleiding het programma opent, moet het voor authentiek verklaren om een veilige verbinding te hebben.
Het gebruikt een paar openbare en privé sleutels. Dit proces is dezelfde functie als een gebruiker/wachtwoord, maar alleen veiliger.

### IMSOrgId {#imsorgid}

De IMSOrgId is de id van de klant op de Adobe Experience Cloud.
Stel het bestand in het bestand instance serverConf.xml in onder het kenmerk IMSOrgId.
Voorbeeld:

```
<redirection IMSOrgId="C5E715(…)98A4@AdobeOrg" (…)
```

### Sleutelgeneratie {#key-generation}

De sleutel is een paar bestanden. Het heeft in het formaat RSA en 4096 lange bytes. Deze kan worden gegenereerd met een opensource-hulpprogramma zoals OpenSSL. Elke keer dat het gereedschap wordt uitgevoerd, wordt een nieuwe toets willekeurig gegenereerd.
Voor het gemak worden de volgende stappen beschreven:

* ```openssl genrsa -out <private_key.pem> 4096```

* ```openssl rsa -pubout -in <private_key.pem> -out <public_key.pem>```

Voorbeeld van het bestand private_key.pem:

```
----BEGIN RSA PRIVATE KEY----
MIIEowIBAAKCAQEAtqcYzt5WGGABxUJSfe1Xy8sAALrfVuDYURpdgbBEmS3bQMDb
(…)
64+YQDOSNFTKLNbDd+bdAA+JoYwUCkhFyvrILlgvlSBvwAByQ2Lx
----END RSA PRIVATE KEY----
```

Voorbeeld van het bestand public_key.pem:

```
----BEGIN PUBLIC KEY----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtqcYzt5WGGABxUJSfe1X
(…)
EwIDAQAB
----END PUBLIC KEY----
```

>[!NOTE]
>
>Toetsen moeten niet door PuttyGen worden gegenereerd, OpenSSL is de beste keuze.

### Auth client creation in Adobe Experience Cloud {#oauth-client-creation}

Een toepassing van het type JWT moet worden gemaakt door u aan te melden bij de Adobe Analytics in de juiste organisatie-account onder **[!UICONTROL Admin]** > **[!UICONTROL User Management]** > **[!UICONTROL Legacy Oath application]**.

Voer de volgende stappen uit:

1. Selecteer **[!UICONTROL Service Account (JWT Assertion)]**.
1. Enter the **[!UICONTROL Application Name]**.
1. Registreer de **[!UICONTROL Public key]**.
1. Selecteer de trigger-s **[!UICONTROL Scopes]**.

   ![](assets/triggers_5.png)

1. Klik op **[!UICONTROL Create]** en controleer het **[!UICONTROL Application ID]** en **[!UICONTROL Application Secret]** gemaakte bestand.

   ![](assets/triggers_6.png)

### Registratie van toepassingsnamen in Adobe Campaign Classic {#application-name-registration}

De toepassings-id van de gemaakte Auth-client moet in Adobe Campaign zijn geconfigureerd. U kunt dit doen door het instantie config-bestand in het [!DNL pipelined] element te bewerken, met name het kenmerk appName.

Voorbeeld:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Sleutelversleuteling {#key-encription}

De persoonlijke sleutel moet worden versleuteld om door [!DNL pipelined]te kunnen worden gebruikt. De encryptie wordt gedaan gebruikend de cryptString functie Javascript en moet op de zelfde instantie worden uitgevoerd zoals [!DNL pipelined].

In deze [pagina](../../integrations/using/pipeline-troubleshooting.md)vindt u een voorbeeld van versleuteling met persoonlijke sleutels in JavaScript.

De gecodeerde persoonlijke sleutel moet zijn geregistreerd in Adobe Campaign. U kunt het doen door het instantie config dossier in het [!DNL pipelined] element, specifiek het authPrivateKey attribuut uit te geven.

Voorbeeld:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Automatische start van het pijplijnproces {#pipelined-auto-start}

Het [!DNL pipelined] proces moet automatisch worden gestart.
Om het te doen, plaats het element in het configuratiedossier aan autostart= &quot;waar&quot;:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Opnieuw opstarten van het pijlproces {#pipelined-restart}

U kunt de toepassing ook handmatig starten met de opdrachtregel:

```
nlserver start pipelined@instance
```

De wijzigingen worden pas van kracht als u de toepassing opnieuw start:

```
nlserver restart pipelined@instance
```

Als er fouten optreden, zoekt u naar fouten in de standaarduitvoer (als u deze handmatig hebt gestart) of in het [!DNL pipelined] logbestand. Raadpleeg de sectie Problemen oplossen in dit document voor meer informatie over het oplossen van problemen.

### Opties voor configuratie met pijplijn {#pipelined-configuration-options}

| Option | Beschrijving |
|:-:|:-:|
| appName | Id van de OAuth-toepassing (toepassings-id) die is geregistreerd in Adobe Analytics (waar de openbare sleutel is geüpload): Beheer > Gebruikersbeheer > Oudere Oath-toepassing. Refer to this [section](../../integrations/using/configuring-pipeline.md#oauth-client-creation). |
| authGatewayEndpoint | URL om &quot;gatewaytokens&quot;te krijgen. <br> Standaard: https://api.omniture.com |
| authPrivateKey | Persoonlijke sleutel (openbaar onderdeel geüpload in Adobe Analytics (zie deze sectie). AES gecodeerd met de optie XtkSecretKey: xtk.session.EncryptPassword(&quot;PRIVATE_KEY&quot;); |
| disableAuth | De authentificatie van de onbruikbaar maken (het verbinden zonder gatewaytokens wordt slechts goedgekeurd door sommige eindpunten van de ontwikkelingsPijpleiding) |
| findPipelineEndpoint | URL om het eindpunt te ontdekken van de Diensten van de Pijpleiding dat voor deze huurder moet worden gebruikt. Standaard: https://producer-pipeline-pnw.adobe.net |
| dumpStatePeriodSec | Periode tussen twee dumps van het proces interne staat in var/INSTANCE/pipelined.json Interne staat is ook toegankelijk op bestelling op http://INSTANCE/pipelined/status (haven 7781). |
| forcePipelineEndpoint | Maak de ontdekking van PipelineServicesEndpoint onbruikbaar en forceer het |
| monitorServerPort | Het [!DNL pipelined] proces luistert op deze haven om de proces interne staat in http://INSTANCE/pipelined/status (haven 7781) te verstrekken. |
| pointerFlushMessageCount | Wanneer dit aantal berichten wordt verwerkt, worden de compensaties opgeslagen in het gegevensbestand. Standaard is 1000 |
| pointerFlushPeriodSec | Na deze periode worden de offsets opgeslagen in de database. Standaard is 5 (sec) |
| processingJSThreads | Aantal specifieke draden verwerkend berichten met de schakelaars van douaneJS. Standaard is 4 |
| processingThreads | Aantal specifieke draden verwerkend berichten met ingebouwde code. Standaard is 4 |
| retryPeriodSec | Vertraging tussen pogingen (als er verwerkingsfouten zijn). Standaard is 30 (sec) |
| retryValiditySec | Verwijder het bericht als het na deze periode niet succesvol is verwerkt (te veel pogingen). De standaardwaarde is 300 (sec) |
