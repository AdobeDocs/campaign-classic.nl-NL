---
product: campaign
title: Integratie via SOAP (serverzijde)
description: Integratie via SOAP (serverzijde)
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 3%

---

# Integratie via SOAP (server-kant){#integration-via-soap-server-side}



De SOAP-webservices die worden aangeboden voor aanbiedingsbeheer, verschillen van de services die gewoonlijk in Adobe Campaign worden gebruikt. U hebt toegang tot deze bestanden via de interactie-URL die in de vorige sectie is beschreven. U kunt nu aanbiedingen voor een bepaalde contactpersoon presenteren of bijwerken.

## Voorstel {#offer-proposition}

Voor een aanbiedingsvoorstel via ZEEP, voeg toe **nms:proposition#propose** gevolgd door de volgende parameters:

* **targetId**: primaire sleutel van de ontvanger (kan een samengestelde sleutel zijn).
* **maxCount**: geeft het aantal voorstellen voor de contactpersoon aan.
* **context**: Hiermee kunt u contextinformatie toevoegen in het ruimteschema. Als het gebruikte schema **nms:interactie**, **`<empty>`** worden toegevoegd.
* **categorieën**: geeft aan tot welke categorie(ën) de aanbiedingen moeten behoren.
* **thema&#39;s**: geeft het thema of de thema&#39;s aan waartoe de aanbieding(en) moeten behoren.
* **uuid**: waarde van het permanente cookie van Adobe Campaign (&quot;uuid230&quot;).
* **nli**: waarde van het Adobe Campaign-sessiecookie (&quot;nlid&quot;).
* **noProp**: gebruik de waarde &quot;true&quot; om de invoeging van een voorstel te deactiveren.

>[!NOTE]
>
>De **targetId** en **maxCount** instellingen zijn verplicht. De andere zijn optioneel.

In antwoord op de vraag, zal de dienst van de ZEEP de volgende parameters terugkeren:

* **interactionId**: ID van de interactie.
* **voorstellen**: XML-element, bevat de lijst met voorstellingen, elk met een eigen id en HTML-representatie.

## Aanbieding bijwerken {#offer-update}

Voeg de **nms:interaction#UpdateStatus** naar de URL, gevolgd door de volgende parameters:

* **voorstel**: tekenreeks met tekens, bevat deze de voorstel-id die als uitvoer is opgegeven tijdens een aanbiedingsvoorstel. Zie [Voorstel](#offer-proposition).
* **status**: type tekenreeks, geeft de nieuwe status van de aanbieding aan. De mogelijke waarden worden vermeld in de **propositionStatus** opsomming, in de **nms:algemeen** schema. Bijvoorbeeld, out-of-the-box, beantwoordt aantal 3 aan **Geaccepteerd** status.
* **context**: Met het XML-element kunt u contextinformatie toevoegen in het ruimteschema. Als het gebruikte schema **nms:interactie**, **`<empty>`** worden toegevoegd.

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
