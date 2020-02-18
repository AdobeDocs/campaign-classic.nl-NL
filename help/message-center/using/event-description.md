---
title: Beschrijving van gebeurtenis
seo-title: Beschrijving van gebeurtenis
description: Beschrijving van gebeurtenis
seo-description: null
page-status-flag: never-activated
uuid: 7b174ffd-28b2-4147-b992-e17b0b2cf733
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 3c8388d8-1a91-4d16-a8ac-016f643c6009
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7c57fb0f2d9867b5ea96185c1984e0b1baeb056a

---


# Beschrijving van gebeurtenis{#event-description}

## Informatie over datamodel voor transactiemeldingen {#about-transactional-messaging-datamodel}

Het transactionele overseinen baseert zich op het datamodel van de Campagne, en gebruikt twee extra afzonderlijke lijsten. Deze tabellen, **NmsRtEvent** en **NmsBatchEvent**, bevatten dezelfde velden en laten u gebeurtenissen in real time aan de ene kant beheren en gebeurtenissen in batch aan de andere kant.

## SOAP-methoden {#soap-methods}

Deze sectie detailleert de methodes van de ZEEP verbonden aan de schema&#39;s van de transactionele berichtmodule.

Twee **PushEvent** - of **PushEvents** SOAP-methoden zijn gekoppeld aan de twee **nms:rtEvent** en **nms:BatchEvent** -gegevensschema&#39;s. Het is het informatiesysteem dat bepaalt of een gebeurtenis een &quot;partij&quot;of &quot;real time&quot;type is.

* **Met PushEvent** kunt u één gebeurtenis in het bericht invoegen.
* **Met PushEvents** kunt u een reeks gebeurtenissen in het bericht invoegen.

Het WSDL-pad voor toegang tot beide methoden is:

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent** om tot het typeschema in real time toegang te hebben.
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:batchEvent** voor toegang tot het batchtypeschema.

Beide methodes bevatten een **`<urn:sessiontoken>`** element voor het het programma openen aan de transactionele overseinenmodule. Wij adviseren gebruikend een identificatiemethode via vertrouwde op IP adressen. Om het zittingsteken terug te winnen, voer een vraag van de ZEEP van de opening van een sessie uit, dan krijgt het teken gevolgd door een logoff. Gebruik het zelfde teken voor verscheidene vraag van RT. De voorbeelden inbegrepen in deze sectie gebruiken de methode van het zittingsteken die geadviseerd is.

Als u een taakgebalanceerde server gebruikt, kunt u de gebruiker/Wachtwoord authentificatie (op het niveau van het bericht van RT) gebruiken. Voorbeeld:

```
<PushEvent xmlns="urn:nms:rtEvent">
<sessiontoken>mc/PASSWORD</sessiontoken>
<domEvent>
<rtEvent wishedChannel="41" type="rt_MobileJourney_iOS_Push" registrationToken="c3ddc8aaecc24822df25d0f49865cca61ea3f86c61bfa53ae4d37294e37f4a1c" hashlpId="27EE7571EC14DBA23B9B5CC0EF79BB782DAECF4C03C88E5D92CC9B9DAC4E5DDA" correlationId="415b7593-4f6f-e911-811f-00505691247c" xmlns="">
<mobileApp uuid="236B24DC-C073-412F-8BCB-AC7207096258" _operation="none"/>
<ctx>...</ctx>
</rtEvent>
</domEvent>
</PushEvent>
```

De **methode PushEvent** bestaat uit een **`<urn:domevent>`** parameter die de gebeurtenis bevat.

De methode **PushEvents** bestaat uit een **`<urn:domeventcollection>`** parameter die gebeurtenissen bevat.

Voorbeeld met PushEvent:

```
<urn:PushEvent>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEvent>
 
   <rtEvent>
   
   ...
   
   </rtEvent>
 
 </urn:domEvent>

</urn:PushEvent>
```

>[!NOTE]
>
>Bij een aanroep van de methode **PushEvents** moeten we een bovenliggend XML-element toevoegen om te voldoen aan standaard-XML. In dit XML-element worden de verschillende **`<rtevent>`** elementen in de gebeurtenis beschreven.

Voorbeeld met PushEvents:

```
<urn:PushEvents>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEventCollection>
 
   <Events>
   
     <rtEvent>... </rtEvent>
     
     <rtEvent>... </rtEvent>
     
     ...
   
   </Events>
 
 </urn:domEventCollection>

</urn:PushEvents>
```

De **`<rtevent>`** en **`<batchevent>`** elementen hebben een set kenmerken en een verplicht onderliggend element: **`<ctx>`** voor het integreren van berichtgegevens.

>[!NOTE]
>
>Met het **`<batchevent>`** element kunt u de gebeurtenis toevoegen aan de &quot;batch&quot;-wachtrij. De gebeurtenis **`<rtevent>`** voegt de &quot;real-time&quot; wachtrij toe.

De verplichte kenmerken van de elementen **`<rtevent>`** en **`<batchevent>`** elementen zijn @type en @email. De waarde van @type moet gelijk zijn aan de gespecificeerde lijstwaarde die wordt bepaald wanneer het vormen van de uitvoeringsinstantie. Met deze waarde kunt u de sjabloon definiëren die tijdens de levering aan de inhoud van de gebeurtenis moet worden gekoppeld.

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

In dit voorbeeld zijn twee kanalen beschikbaar: het e-mailadres en het mobiele telefoonnummer. Met **wishedChannel** kunt u het kanaal selecteren dat u wilt gebruiken wanneer u de gebeurtenis omzet in een bericht. De waarde 0 komt overeen met het e-mailkanaal, de waarde 1 voor het mobiele kanaal, enzovoort.

Als u de levering van een gebeurtenis wilt uitstellen, voegt u het **[!UICONTROL scheduled]** veld toe, gevolgd door de datum van voorkeur. De gebeurtenis wordt op deze datum omgezet in een bericht.

We raden u aan de kenmerken @wishedChannel en @emailFormat in te vullen met numerieke waarden. De functietabel die numerieke waarden en labels koppelt, vindt u in de beschrijving van het gegevensschema.

>[!NOTE]
>
>Een gedetailleerde beschrijving van alle toegestane kenmerken en hun waarden is beschikbaar in de beschrijving van de **nms:rtEvent** en **nms:BatchEvent** dataschema.

Het **`<ctx>`** element bevat de berichtgegevens. De XML-inhoud is open, wat betekent dat deze kan worden geconfigureerd op basis van de inhoud die moet worden geleverd.

>[!NOTE]
>
>Het is belangrijk om het aantal en de grootte van de knopen van XML in het bericht te optimaliseren om het overladen van de servers tijdens levering te vermijden.

Voorbeeld van gegevens:

```
   <ctx>
               <client>
                        <firstname>John</firstname>
                        <lastname>Doe</lastname>
               </client>
               <action>
                         <type>Order confirmation</type>
                          <number>CN23453</number>
               </action>
               <orderdetails>
                          <article num="1">
                                   <name>Generic USB key</name>
                                   <price>20</price>
                           </article>
               </orderdetails>
    </ctx>
   
```

## Informatie die wordt geretourneerd door de SOAP-aanroep {#information-returned-by-the-soap-call}

Wanneer Adobe Campaign een gebeurtenis ontvangt, wordt een unieke retour-id gegenereerd. Dit is de id van de gearchiveerde versie van de gebeurtenis.

>[!CAUTION]
>
>Wanneer u SOAP-aanroepen ontvangt, controleert Adobe Campaign de indeling van het e-mailadres. Als een e-mailadres onjuist is opgemaakt, wordt een fout geretourneerd.

* Voorbeeld van een id die door de methode wordt geretourneerd wanneer de gebeurtenisverwerking is geslaagd:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">72057594037935966</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

Als de waarde van de retour-id strikt groter is dan nul, betekent dit dat de gebeurtenis is gearchiveerd in Adobe Campaign.

Als de gebeurtenis echter niet kan worden verwerkt, retourneert de methode een foutbericht of een waarde die gelijk is aan nul.

* Voorbeeld verwerken van een gebeurtenis die is mislukt wanneer de query geen aanmeldingsnaam bevat of de opgegeven operator niet de vereiste rechten heeft:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">Error while reading parameters of method 'PushEvent' of service 'nms:rtEvent'.</faultstring>
            <detail xsi:type="xsd:string">Invalid login or password. Connection denied.</detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Voorbeeld van een gebeurtenis die is mislukt als gevolg van een fout in de query (de XML-classificatie is niet nageleefd):

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">The XML SOAP message is invalid (service 'PushEvent', method 'nms:rtEvent').</faultstring>
            <detail xsi:type="xsd:string"><![CDATA[(16:8) : Expected end of tag 'rtevent'
   Error while parsing XML string '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
      <soapenv:Header/>
      <soapenv:Body>
         <urn:PushEvent>
            <urn:sessiontoken>mc/</urn:sessiontoken>
            <urn:domEvent>
   <rtevent type="create_account" email="esther.hall@adobe.com" origin="eCommerce" wishedChannel="email" 
         externalId="1596" language="english" country="EN" emailFormat="2"
         mobilePhone="+447700123123">
     <ctx>
      <website name="eCommerce" url="http://www.eCo']]></detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Voorbeeld van een gebeurtenis die is mislukt en die een nul-id heeft geretourneerd (onjuiste methodenaam):

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">0</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

