---
product: campaign
title: Bedrijfsgerichte API’s
description: Bedrijfsgerichte API’s
feature: API
role: Developer
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 1%

---

# Bedrijfsgerichte API’s{#business-oriented-apis}

Bedrijfs-API is specifiek voor elk type object. Zij hebben een effect op:

* Leveringen:

   * Creërend een leveringsactie, verwijs naar [ SubmitDelivery (nms :delivery) ](#submitdelivery--nms-delivery-),
   * het verzenden van een campagne (starten, pauzeren, stoppen, verzenden van bewijzen);
   * leveringslogboeken herstellen.

* Workflows:

   * het starten van een workflow,
   * controleren van processen, enz.

     Verwijs naar [ methodes van SOAP in JavaScript ](../../configuration/using/soap-methods-in-javascript.md).

* Inhoudsbeheer
* Het beheer van het abonnement, verwijs naar [ Abonneren (nms :subscription) ](#subscribe--nms-subscription-) en [ Unsubscribe (nms :subscription) ](#unsubscribe--nms-subscription-).
* Gegevensprocessen: invoer, uitvoer.

In deze sectie wordt het gebruik van de services &quot;Abonneren&quot;, &quot;Unsubscribe&quot; en &quot;VerzendenLevering&quot; beschreven.

>[!IMPORTANT]
>
>[ de documentatie van JSAPI van de Campagne ](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=nl) bevat extra informatie over de vraag van SOAP en het gebruiken van Javascript in Adobe Campaign, evenals een volledige verwijzing naar alle methodes en functies die in de toepassing worden gebruikt.

## Abonneren (nms :subscription) {#subscribe--nms-subscription-}

Met deze service kunt u een ontvanger abonneren op een informatieservice en het profiel van de ontvanger bijwerken.

De volgende parameters worden vereist om de dienst te roepen:

* een verificatie,
* interne naam van de abonnementendienst;
* een XML-document met de ontvangende informatie (uit het schema &quot;nms :recipient&quot;);
* een Booleaanse waarde voor het maken van ontvangers als dat nog niet het geval is.

Beschrijving van de methode &quot;subscribe&quot; in het schema &quot;nms :subscription&quot;:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

De definitie van de verzoeningssleutel moet via de _ **zeer belangrijke** attributen op het `<recipient>` element van het document van XML zijn ingegaan. De inhoud van dit kenmerk is een XPath-lijst met komma&#39;s als scheidingsteken.

Deze aanroep retourneert geen gegevens, behalve fouten.

### Voorbeelden {#examples}

Abonnement met afstemmingssleutel voor ontvangers op het e-mailadres: het XML-invoerdocument moet verwijzen naar het e-mailadres en de definitie van de sleutel in dit veld.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

De ontvanger en het abonnement bijwerken.

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### Voorbeeld van SOAP-berichten {#example-of-soap-messages}

* Query:

  ```
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <m:Subscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <sessiontoken xsi:type='xsd:string'/>
        <service xsi:type='xsd:string'>SVC1</service>
        <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <recipient _key="@email" email= "john.doe@adobe.com/>
        </content>
        <create xsi:type='xsd:boolean'>true</create>
      </m:Subscribe>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* Reactie:

  ```
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
      </m:SubscribeResponse>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

## Abonnement opzeggen (nms :subscription) {#unsubscribe--nms-subscription-}

Met deze service kunt u het abonnement van een ontvanger op een informatieservice opzeggen en het profiel van de ontvanger bijwerken.

De volgende parameters worden vereist om de dienst te roepen:

* een verificatie,
* Interne naam van de dienst waarvan het abonnement moet worden opgezegd;
* een XML-document met de ontvangende informatie (uit het schema &quot;nms :recipient&quot;);

Beschrijving van de methode &quot;Unsubscribe&quot; in het schema &quot;nms :subscription&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

De definitie van de afstemmingssleutel moet worden ingevoerd via het _key-kenmerk op het `<recipient>` -element van het XML-document. De inhoud van dit kenmerk is een XPath-lijst met komma&#39;s als scheidingsteken.

Als de ontvanger niet aanwezig in het gegevensbestand is of niet aan de betrokken informatiedienst geabonneerd, voert de dienst geen actie uit en produceert geen fout.

>[!NOTE]
>
>Als de de dienstnaam niet als parameter wordt gespecificeerd, is de ontvanger dan automatisch op lijst van gewezen personen (@blackList=&quot;1&quot;).

Deze aanroep retourneert geen gegevens, behalve fouten.

### Voorbeeld van SOAP-berichten {#example-of-soap-messages-1}

Query:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:Unsubscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    <sessiontoken xsi:type='xsd:string'/>
    <service xsi:type='xsd:string'>SVC1</service>
    <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
      <recipient _key="@email" email= "john.doe@adobe.com/>
    </content>
  </m:Unsubscribe>
</SOAP-ENV:Body>
```

Reactie:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## SubmitDelivery (nms :delivery) {#submitdelivery--nms-delivery-}

Met deze service kunt u een leveringsactie maken en verzenden.

De volgende parameters worden vereist om de dienst te roepen:

* een verificatie,
* interne naam van de leveringstemplate;
* een optioneel XML-document met aanvullende leveringsgegevens.

Deze API mag niet in volume worden aangeroepen omdat er mogelijk prestatieproblemen optreden.

Beschrijving van de methode in het schema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

Er moet een leveringssjabloon worden gemaakt vanaf de Adobe Campaign-clientconsole. Het bevat de parameters gemeenschappelijk voor alle leveringen (het adres van de afzender of de duur van de geldigheid van het bericht).

Het document van inputXML is een fragment van het leveringsmalplaatje dat de structuur van het &quot;nms :delivery&quot;schema volgt. Het zal alle extra gegevens bevatten die niet statisch in het leveringsmalplaatje (b.v., lijst van ontvangers aan doel) konden worden bepaald.

Deze aanroep retourneert geen gegevens, behalve fouten.

### Voorbeeld van XML-document {#xml-document-example}

Dit voorbeeld is gebaseerd op een aangepaste leveringssjabloon van een externe gegevensbron (in dit geval een bestand). De configuratie wordt volledig beschreven in het leveringsmalplaatje, zodat alles dat moet worden verzonden wanneer de vraag voorkomt is de inhoud van het dossier van het `<externalsource>` element.

```
<delivery>
  <targets fromExternalSource="true">
    <externalSource>
      MsgId|ClientId|Title|Name|FirstName| Mobile|Email| Market_segment|Product_affinity1 |Product_affinity2|Product_affinity3| Product_affinity4| Support_Number|Amount|Threshold1|000001234|M.| Doe|John|0650201020| john.doe@adobe.com
|1| A1|A2|A3|A4|E12|120000|100000
    </externalSource>
  </target>
</delivery>
```

Als u geen leveringsmalplaatje hebt, kunt u het volgende voorbeeld gebruiken:

```
<delivery>
<targets fromExternalSource="true" targetMode="1" noReconciliation="true" addressField="Email" >  
    <fileFormat active="true">  
      <source format="text" type="text">  
        <dataSourceConfig >  
          <dataSourceColumn label="Email" name="Email" type="string"/>  
        </dataSourceConfig>  
      </source>  
      <destination type="xtkDataStore"/>  
    </fileFormat>  
    <externalSource><![CDATA[not-a-repicipient@domain.com]]></externalSource>  
  </targets> 
</delivery> 
```
