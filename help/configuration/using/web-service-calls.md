---
solution: Campaign Classic
product: campaign
title: Webserviceaanroepen
description: Webserviceaanroepen
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: a469d275fdd768fbd098a0027b5096872dbf6d89
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 1%

---


# Webserviceaanroepen{#web-service-calls}

## Algemene informatie {#general-information}

Alle API methodes worden voorgesteld in de vorm van de diensten van het Web. Hierdoor kunt u alle Adobe Campaign-functies beheren via SOAP-aanroepen, het native ingangspunt van de Adobe Campaign-toepassingsserver. De Adobe Campaign-console zelf gebruikt alleen SOAP-aanroepen.

De diensten van het Web laten u vele toepassingen van een derdesysteem tot stand brengen:

* Synchrone alarm, bericht, en uitvoering in real time van het leveringsmalplaatje van een achterkantoor of transactiesysteem,
* ontwikkeling van speciale interfaces met vereenvoudigde functionaliteit (webinterfaces, enz.);
* Vervoedering en raadpleging van gegevens in het gegevensbestand terwijl het naleven van handelsregels en het blijven geïsoleerd van het onderliggende fysieke model.

## Definitie van webservices {#definition-of-web-services}

De definitie van de diensten van het Web die op de de toepassingsserver van Adobe Campaign worden uitgevoerd is beschikbaar bij de gegevensschema&#39;s.

Een dienst van het Web wordt beschreven in de grammatica van de gegevensschema&#39;s en is beschikbaar bij het **`<methods>`** element.

```
<methods>
  <method name="GenerateForm" static="true">
    <help>Generates the form in Mail or Web mode</help>
    <parameters>
      <param name="formName" type="string" desc="Name of form"/>
      <param name="mailMode" type="boolean" desc="Generate a form of type Mail"/>
      <param name="result" type="string" inout="out" desc="Result "/>
    </parameters>
  </method>
</methods>
```

Hier hebben wij een voorbeeld van de definitie van de methode genoemd **GenerateForm**.

De beschrijving van de service begint met het element `<method>`. De lijst van parameters van de methode wordt voltooid van het `<parameters>` element. Elke parameter wordt opgegeven door een naam, een type (Boolean, tekenreeks, DOMElement, enz.) en een beschrijving. Het &quot;inout&quot;attribuut met de &quot;uit&quot;waarde laat u specificeren dat de &quot;resultaat&quot;parameter bij de vraagoutput van de ZEEP is.

De aanwezigheid van het attribuut &quot;static&quot; (met de waarde &quot;true&quot;) beschrijft deze methode als statisch, wat betekent dat alle parameters van de methode moeten worden gedeclareerd.

Een &quot;const&quot;methode heeft impliciet een document van XML in het formaat van zijn bijbehorend schema als input.

Een volledige beschrijving van het element `<method>` van een Adobe Campaign-schema is beschikbaar in het hoofdstuk &quot;Schemaverwijzingen&quot; onder <a href="../../configuration/using/schema/method.md)" target="_blank">  `<method>`    element.

Voorbeeld van de methode &quot;const&quot;-type &quot;ExecuteQuery&quot; in het schema &quot;xtk:queryDef&quot;:

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

De invoerparameter van deze methode is een XML-document in de indeling van het schema &quot;xtk:queryDef&quot;.

## Webservicebeschrijving: WSDL {#web-service-description--wsdl}

Een WSDL-bestand (Web Service Description Library) is beschikbaar voor elke service. In dit XML-bestand wordt een metaal gebruikt om de service te beschrijven en de beschikbare methoden, parameters en server op te geven waarmee contact moet worden opgenomen voor het uitvoeren van de service.

### WSDL-bestand genereren {#wsdl-file-generation}

Als u een WSDL-bestand wilt genereren, moet u de volgende URL vanuit een webbrowser invoeren:

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

Met:

* **`<server>`**: de Adobe Campaign-toepassingsserver (nlserver-web)
* **`<schema>`**: schema-id (namespace:schema_name)

### Voorbeeld van de methode &#39;ExecuteQuery&#39; van schema &#39;xtk:queryDef&#39; {#example-on-the--executequery--method-of-schema--xtk-querydef-}

Het WSDL-bestand wordt gegenereerd via de URL:

[https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef](https://my_serveur/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef)

Een beschrijving WSDL begint door de types te bepalen die aan vormberichten, verbonden in &quot;havens&quot;worden gebruikt, met een protocol door &quot;banden&quot;het vormen de diensten van het Web worden verbonden.

#### Typen {#types}

De typedefinities zijn gebaseerd op de schema&#39;s van XML. In ons voorbeeld gebruikt de methode &quot;ExecuteQuery&quot; een tekenreeks &quot;s:string&quot; en een XML-document (`<s:complextype>`) als parameters. De geretourneerde waarde van de methode (&quot;ExecuteQueryResponse&quot;) is een XML-document ( `<s:complextype>`).

```
<types>
<s:schema elementFormDefault="qualified" targetNamespace="urn:xtk:queryDef">
  <s:element name="ExecuteQuery">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="sessiontoken" type="s:string"/>
        <s:element maxOccurs="1" minOccurs="1" name="entity">
          <s:complexType>
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="ExecuteQueryResponse">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="pdomOutput">
          <s:complexType mixed="true">
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
```

#### Berichten {#messages}

Met `<message>` worden de namen en typen beschreven van een set velden die moeten worden verzonden. De methode gebruikt twee berichten om als parameter (&quot;ExecuteQueryIn&quot;) en de terugkeerwaarde (&quot;ExecuteQueryOut&quot;) over te gaan.

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### PortType {#porttype}

`<porttype>` associeert de berichten op de &quot;UitvoerenQuery&quot;verrichting die door de vraag (&quot;input&quot;) wordt teweeggebracht die een reactie (&quot;output&quot;produceren).

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### Binding {#binding}

Het `<binding>` deel specificeert het de communicatie protocol van de ZEEP ( `<soap:binding>`), gegevensvervoer in HTTP (waarde van het &quot;vervoer&quot;attribuut) en het gegevensformaat voor de &quot;UitvoerenQuery&quot;verrichting. De hoofdtekst van de SOAP-envelop bevat de berichtsegmenten direct zonder transformatie.

```
<binding name="queryDefMethodsSoap" type="tns:queryDefMethodsSoap">
  <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="ExecuteQuery">
    <soap:operation soapAction="xtk:queryDef#ExecuteQuery" style="document"/>
    <input>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </input>
    <output>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </output>
  </operation>
</binding>
```

#### Service {#service}

In het deel `<service>` wordt de service &quot;XtkQueryDef&quot; beschreven met de URI op de URL van de Adobe Campaign-toepassingsserver.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## Connectiviteit {#connectivity}

Adobe Campaign heeft de beveiliging voor verificatiemechanismen verhoogd door beveiligingszones in te voeren (zie het hoofdstuk **Beveiligingszones definiëren** in [deze sectie](../../installation/using/configuring-campaign-server.md#defining-security-zones)) en door instellingen voor sessiebeheer in te voeren.

Er zijn twee beschikbare verificatiemodi:

* **via een aanroep van de aanmeldingsmethode()**. In deze modus worden een sessietoken en een beveiligingstoken gegenereerd. Het is de veiligste modus en daarom de meest aanbevolen.

of

* **via Adobe Campaign login +** wachtwoord dat tot een zittingsteken leidt. Het sessietoken verloopt automatisch na een ingestelde periode. Deze modus wordt niet aanbevolen en vereist dat de beveiligingsinstellingen van de toepassing voor bepaalde zone-instellingen worden verminderd (allowUserPassword=&quot;true&quot; en sessionTokenOnly=&quot;true&quot;).

### Kenmerken van sessietoken {#session-token-characteristics}

Het zittingsteken heeft de volgende kenmerken:

* een levenscyclus van X uur (de levenscyclus kan worden geconfigureerd in het bestand &#39;serverConf.xml&#39;; de standaardperiode is 24 uur)
* een willekeurige constructie (deze bevat niet langer de gebruikersaanmelding en het wachtwoord)
* indien toegankelijk via het web:

   * het sessietoken wordt een permanent token, het wordt niet vernietigd wanneer de browser wordt gesloten
   * het wordt geplaatst in een HTTP-ONLY koekje (de koekjes moeten voor exploitanten worden geactiveerd)

### Kenmerken van beveiligingstoken {#security-token-characteristics}

Het beveiligingstoken heeft de volgende kenmerken:

* het wordt gegenereerd op basis van het sessietoken
* de server heeft een levenscyclus van 24 uur (configureerbaar in het bestand &#39;serverConf.xml&#39;; de standaardperiode is 24 uur)
* wordt opgeslagen in de Adobe Campaign-console
* indien toegankelijk via het web:

   * wordt opgeslagen in een document._securityToken, eigenschap
   * de pagina-URL&#39;s worden bijgewerkt om het beveiligingstoken bij te werken
   * de formulieren worden ook bijgewerkt via een verborgen veld dat de token bevat

#### Beweging van beveiligingstoken {#security-token-movement}

Wanneer deze via de console wordt benaderd, is de volgende code beschikbaar:

* verzonden in de openings van een sessierespons (in de kopbal van HTTP)
* gebruikt in elke query (in de HTTP-header)

Van een POST en GET HTTP:

* de server voltooit de koppelingen met het token
* de server voegt een verborgen veld toe aan formulieren

Van een SOAP-aanroep:

* het wordt toegevoegd aan vraagkopballen

### Voorbeelden van oproepen {#call-examples}

* Met **HttpSoapConnection/SoapService**:

```
  
    var cnx = new HttpSoapConnection("https://serverURL/nl/jsp/soaprouter.jsp");
  var session = new SoapService(cnx, 'urn:xtk:session');
  session.addMethod("Logon", "xtk:session#Logon",
                      ["sessiontoken", "string", "Login", "string", "Password", "string", "Parameters", "NLElement"],
                      ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
  
  var res = session.Logon("", "admin", "pwd", <param/>);
  var sessionToken = res[0];
  var securityToken = res[2];
  
  cnx.addTokens(sessionToken, securityToken);
  var query = new SoapService(cnx, 'urn:xtk:queryDef');
  query.addMethod("ExecuteQuery", "xtk:queryDef#ExecuteQuery",
                      ["sessiontoken", "string", "entity", "NLElement"],
                      ["res", "NLElement"]);
  
  var queryRes = query.ExecuteQuery("", <queryDef operation="select" schema="nms:recipient">
            <select>
              <node expr="@email"/>
              <node expr="@lastName"/>
              <node expr="@firstName"/>
            </select>
            <where>
              <condition expr="@email = 'joe.doe@aol.com'"/>
            </where>
          </queryDef>);
  logInfo(queryRes[0].toXMLString())
```

* Met **HttpServletRequest**:

>[!NOTE]
>
>De URL&#39;s die in de volgende **HttpServletRequest**-aanroepen worden gebruikt, moeten zich op de lijst van gewenste personen bevinden in de sectie met url-machtigingen van het bestand **serverConf.xml**. Dit geldt ook voor de URL van de server zelf.

Uitvoering aanmelding():

```
var req = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req.header["Content-Type"] = "text/xml; charset=utf-8";
req.header["SOAPAction"] =   "xtk:session#Logon";
req.method = "POST";
req.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:session">' +
    '<soapenv:Header/>' +
    '<soapenv:Body>' +
        '<urn:Logon>' +
            '<urn:sessiontoken></urn:sessiontoken>' +
            '<urn:strLogin>LOGIN_HERE</urn:strLogin>' +
            '<urn:strPassword>PASSWORD_HERE</urn:strPassword>' +
            '<urn:elemParameters></urn:elemParameters>' +
        '</urn:Logon>' +
    '</soapenv:Body>' +
'</soapenv:Envelope>';
req.execute();
           
var resp = req.response;
var xmlRes = new XML(String(resp.body).replace("<?xml version='1.0'?>",""));
var sessionToken = String(xmlRes..*::pstrSessionToken);;
var securityToken = String(xmlRes..*::pstrSecurityToken);
```

Uitvoering query:

```
var req2 = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req2.header["Content-Type"] = "text/xml; charset=utf-8";
req2.header["SOAPAction"] =   "xtk:queryDef#ExecuteQuery";req2.header["X-Security-Token"] = securityToken;
req2.header["cookie"]           = "__sessiontoken="+sessionToken;
req2.method = "POST";
req2.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:queryDef">' +
             '<soapenv:Header/><soapenv:Body><urn:ExecuteQuery><urn:sessiontoken/><urn:entity>' +
                '<queryDef operation="select" schema="nms:recipient">' +
                  '<select><node expr="@email"/><node expr="@lastName"/><node expr="@firstName"/></select>' +
                  '<where><condition expr="@email = \'john.doe@aol.com\'"/></where>' +
                '</queryDef>' +
           '</urn:entity></urn:ExecuteQuery></soapenv:Body></soapenv:Envelope>';
req2.execute();
var resp2 = req2.response;
logInfo(resp2.body)
```
