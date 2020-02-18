---
title: Zakelijke API's
seo-title: Zakelijke API's
description: Zakelijke API's
seo-description: null
page-status-flag: never-activated
uuid: ddb6e5cf-dfe0-4dc9-ac5b-fab21827b874
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: e7b3ffca-c85f-498d-89b4-23fcff59de49
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Zakelijke API&#39;s{#business-oriented-apis}

Bedrijfs-API is specifiek voor elk type object. Zij hebben een effect op:

* Leveringen:

   * Creërend een leveringsactie, verwijs naar [SubmitDelivery (nms:levering)](#submitdelivery--nms-delivery-),
   * het verzenden van een campagne (starten, pauzeren, stoppen, verzenden van bewijzen);
   * leveringslogboeken herstellen.

* Workflows:

   * het starten van een workflow,
   * controleren van processen, enz.

      Zie [SOAP-methoden in JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Inhoudsbeheer
* Abonnementsbeheer, zie [Abonneren (nms:abonnement)](#subscribe--nms-subscription-) en [Abonnement opzeggen (nms:abonnement)](#unsubscribe--nms-subscription-).
* Gegevensprocessen: invoer, uitvoer.

In deze sectie wordt het gebruik van de services &quot;Abonneren&quot;, &quot;Unsubscribe&quot; en &quot;VerzendenLevering&quot; beschreven.

>[!IMPORTANT]
>
>[De documentatie](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html) van JSAPI van de campagne bevat extra informatie over de vraag van de ZEEP en het gebruiken van Javascript in de Campagne van Adobe, evenals een volledige verwijzing naar alle methodes en functies die in de toepassing worden gebruikt.

## Abonneren (nms:abonnement) {#subscribe--nms-subscription-}

Met deze service kunt u een ontvanger abonneren op een informatieservice en het profiel van de ontvanger bijwerken.

De volgende parameters worden vereist om de dienst te roepen:

* een verificatie,
* interne naam van de abonnementendienst;
* een XML-document met de informatie over de ontvanger (uit het schema &quot;nms:ontvanger&quot;);
* een Booleaanse waarde voor het maken van ontvangers als dat nog niet het geval is.

Beschrijving van de methode &quot;subscribe&quot; in het schema &quot;nms:subscription&quot;:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

De definitie van de afstemmingssleutel moet worden ingevoerd via het kenmerk _**key** op het `<recipient>` element van het XML-document. De inhoud van dit kenmerk is een XPath-lijst met komma&#39;s als scheidingsteken.

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

## Abonnement opzeggen (nms:abonnement) {#unsubscribe--nms-subscription-}

Met deze service kunt u het abonnement van een ontvanger op een informatieservice opzeggen en het profiel van de ontvanger bijwerken.

De volgende parameters worden vereist om de dienst te roepen:

* een verificatie,
* Interne naam van de dienst waarvan het abonnement moet worden opgezegd;
* een XML-document met de informatie over de ontvanger (uit het schema &quot;nms:ontvanger&quot;);

Beschrijving van de methode &quot;Unsubscribe&quot; in het schema &quot;nms:subscription&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

De definitie van de afstemmingssleutel moet worden ingevoerd via het kenmerk _key op het `<recipient>` element van het XML-document. De inhoud van dit kenmerk is een XPath-lijst met komma&#39;s als scheidingsteken.

Als de ontvanger niet aanwezig in het gegevensbestand is of niet aan de betrokken informatiedienst geabonneerd, voert de dienst geen actie uit en produceert geen fout.

>[!NOTE]
>
>Als de servicenaam niet als parameter is opgegeven, wordt de ontvanger automatisch op de zwarte lijst geplaatst (@blackList=&quot;1&quot;).

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

## VerzendenAflevering (nms:aflevering) {#submitdelivery--nms-delivery-}

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

Er moet een leveringssjabloon worden gemaakt op basis van de Adobe Campaign-clientconsole. Het bevat de parameters gemeenschappelijk voor alle leveringen (het adres van de afzender of de geldigheidsduur van het bericht).

Het invoerXML-document is een leveringssjabloonfragment dat voldoet aan de structuur van het schema &quot;nms:delivery&quot;. Het zal alle extra gegevens bevatten die niet statisch in het leveringsmalplaatje (b.v., lijst van ontvangers aan doel) konden worden bepaald.

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

