---
product: campaign
title: Integratie via SOAP (serverzijde)
description: Integratie via SOAP (serverzijde)
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 3%

---

# Integratie via SOAP (server-side){#integration-via-soap-server-side}



De SOAP-webservices die voor het beheer van aanbiedingen worden aangeboden, verschillen van de services die gewoonlijk in Adobe Campaign worden gebruikt. U hebt toegang tot deze bestanden via de interactie-URL die in de vorige sectie is beschreven. U kunt nu aanbiedingen voor een bepaalde contactpersoon presenteren of bijwerken.

## Voorstel {#offer-proposition}

Voor een aanbiedingsvoorstel via SOAP, voeg **nms toe:proposition#Propose** bevel dat door de volgende parameters wordt gevolgd:

* **targetId**: primaire sleutel van de ontvanger (kan een samengestelde sleutel zijn).
* **maxCount**: specificeert het aantal aanbiedingsvoorstellen voor het contact.
* **context**: laat u contextinformatie in het ruimteschema toevoegen. Als het gebruikte schema **nms is:interactie**, **`<empty>`** zou moeten worden toegevoegd.
* **categorieën**: specificeert de categorie(ën) de aanbiedingen moeten tot behoren.
* **thema&#39;s**: specificeert de thema(s) die de aanbieding(en) moeten behoren tot.
* **uuid**: waarde van het permanente koekje van Adobe Campaign (&quot;uuid230&quot;).
* **nli**: waarde van het de zittingskoekje van Adobe Campaign (&quot;ongeldig&quot;).
* **noProp**: gebruik de &quot;ware&quot;waarde om voorsteltoevoeging te deactiveren.

>[!NOTE]
>
>De **targetId** en **maxCount** montages zijn verplicht. De andere zijn optioneel.

Als antwoord op de vraag, zal de dienst van SOAP de volgende parameters terugkeren:

* **interactionId**: identiteitskaart van de interactie.
* **voorstellen**: Het element van XML, bevat de lijst van voorstellen, elk met hun eigen identiteitskaart en vertegenwoordiging van HTML.

## Aanbieding bijwerken {#offer-update}

Voeg **nms toe:interaction#UpdateStatus** bevel aan URL, die door deze parameters wordt gevolgd:

* **voorstel**: koord van karakters, bevat het propositie identiteitskaart die als output tijdens een aanbiedingsvoorstel wordt gegeven. Verwijs naar [ voorstel van de Aanbieding ](#offer-proposition).
* **status**: koordtype, specificeert het de nieuwe status van de aanbieding. De mogelijke waarden zijn vermeld in de **propositionStatus** opsomming, in **nms:gemeenschappelijk** schema. Bijvoorbeeld, uit-van-de-doos, beantwoordt aantal 3 aan **Toegelaten** status.
* **context**: Het element van XML, laat u contextinformatie in het ruimteschema toevoegen. Als het gebruikte schema **nms is:interactie**, **`<empty>`** zou moeten worden toegevoegd.

## Voorbeeld met een SOAP-aanroep {#example-using-a-soap-call}

Hieronder ziet u een voorbeeld van code voor een SOAP-aanroep.

Hier volgt een voorbeeld van URL:

```
http://<urlOfYourJSSP>?env=liveRcp&sp=<nameSpaceOfferSpace>&t=<targetID>
```

```
<%
  var env = request.getUTF8Parameter("env");
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
      for each( var propHtml in props.proposition.*.htmlSource )
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
