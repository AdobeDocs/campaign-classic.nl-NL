---
title: Integratie via SOAP (serverzijde)
seo-title: Integratie via SOAP (serverzijde)
description: Integratie via SOAP (serverzijde)
seo-description: null
page-status-flag: never-activated
uuid: 678371c5-4246-4886-994e-30dbbc70f14a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 477a2c31-0403-4db1-a372-c75dca58380d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Integratie via SOAP (serverzijde){#integration-via-soap-server-side}

De SOAP-webservices die worden aangeboden voor aanbiedingsbeheer, verschillen van de services die gewoonlijk worden gebruikt in Adobe Campaign. U hebt toegang tot deze bestanden via de interactie-URL die in de vorige sectie is beschreven. U kunt nu aanbiedingen voor een bepaalde contactpersoon presenteren of bijwerken.

## Voorstel {#offer-proposition}

Voor een aanbiedingsvoorstel via ZEEP, voeg het **nms:proposition#Propose** bevel toe dat door de volgende parameters wordt gevolgd:

* **targetId**: primaire sleutel van de ontvanger (kan een samengestelde sleutel zijn).
* **maxCount**: geeft het aantal voorstellen voor de contactpersoon aan.
* **context**: Hiermee kunt u contextinformatie toevoegen in het ruimteschema. Als het gebruikte schema **nms:interactie** is, **`<empty>`** zou moeten worden toegevoegd.
* **categorieën**: geeft de categorie(ën) aan waartoe de aanbiedingen moeten behoren.
* **thema**&#39;s: geeft het thema of de thema&#39;s aan waartoe de aanbieding(en) moeten behoren.
* **uuuid**: waarde van het permanente cookie van Adobe Campaign (&quot;uuid230&quot;).
* **nli**: De waarde van het Adobe Campagne-sessiecookie (&quot;null&quot;).
* **noProp**: Gebruik de waarde &quot;true&quot; om de invoeging van een voorstel te deactiveren.

>[!NOTE]
>
>De instellingen **targetId** en **maxCount** zijn verplicht. De andere zijn optioneel.

In antwoord op de vraag, zal de dienst van de ZEEP de volgende parameters terugkeren:

* **interactionId**: Id van de interactie.
* **voorstellen**: XML-element, bevat de lijst met voorstellingen, elk met een eigen id en HTML-representatie.

## Aanbieding bijwerken {#offer-update}

Voeg de **nms:interaction#UpdateStatus** bevel aan URL toe, die door deze parameters wordt gevolgd:

* **voorstel**: Tekenreeks, bevat deze de voorstel-id die als uitvoer is opgegeven tijdens een aanbiedingsvoorstel. Zie Voorstel [voorstel](#offer-proposition).
* **status**: tekenreekstype, geeft het de nieuwe status van de aanbieding aan. De mogelijke waarden worden vermeld in de **propositionStatus** opsomming, in **nms:common** schema. Het getal 3 komt bijvoorbeeld overeen met de status **Geaccepteerd** .
* **context**: Met XML-element kunt u contextinformatie toevoegen in het ruimteschema. Als het gebruikte schema **nms:interactie** is, **`<empty>`** zou moeten worden toegevoegd.

## Voorbeeld met een SOAP-aanroep {#example-using-a-soap-call}

Hier is een voorbeeld van code voor een vraag van de ZEEP:

```
<%
  var space = request.parameters.sp
  var cnx = new HttpSoapConnection(
    "https://" + request.serverName + ":" + request.serverPort + "/interaction/" + env + "/" + space,
    "utf-8",
    HttpSoapConnection.SOAP_12)
  var session = new SoapService(cnx, "nms:interaction")
  var action = request.parameters.a
  if( action == undefined )
    action = 'propose'

  try
  {
    switch( action )
    {
    case "update":
      var proposition = request.parameters.p
      var status      = request.parameters.st
      session.addMethod("UpdateStatus", "nms:interaction#UpdateStatus",
       ["proposition", "string",
        "status",      "string",
        "context",     "NLElement"],
       [])
      session.UpdateStatus(proposition, status, <undef/>)
      var redirect = request.parameters.r
      if( redirect != undefined )
        response.sendRedirect(redirect)
      break;

    case "propose":
      var count = request.parameters.n
      var target = request.parameters.t
      var categorie = request.parameters.c
      var theme = request.parameters.th
      var layout = request.parameters.l
      if( count == undefined )
        count = 1
      session.addMethod("Propose", "nms:proposition#Propose",
       ["targetId",      "string",
        "maxCount",      "string",
         "categories",    "string",
         "themes",        "string",
        "context",       "NLElement"],
       ["interactionId", "string",
        "propositions",  "NLElement"])
      response.setContentType("text/html")
      var result = session.Propose(target, count, category, theme, <empty/>)
      var props = result[1]
  %><table><tr><%
      for each( var propHtml in props.proposition.*.mdSource )
      {
        %><td><%=propHtml%></td><%
      }
  %></tr></table><%
      break;
    }
  }
  catch( e )
  {
  }
  %>
```
