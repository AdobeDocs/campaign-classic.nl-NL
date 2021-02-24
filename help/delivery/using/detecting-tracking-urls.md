---
solution: Campaign Classic
product: campaign
title: URL's bijhouden detecteren
description: Meer informatie over aanbevolen patronen voor het bijhouden van URL's.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# URL&#39;s bijhouden detecteren

## Voorbeeld van niet-detectie

`<%= getURL("http://mynewsletter.com") %>` werkt en verzendt de feitelijke inhoud van de webpagina via e-mail naar de ontvangers. Maar geen van de koppelingen wordt bijgehouden. De reden voor dit is dat MTA `"<%=getURL(..."` voor elke e-mail alvorens uitvoert. Het kan voor elke ontvanger verschillend zijn, zodat kan Adobe Campaign niet de URLs voor het volgen kennen en hen een markeringsidentiteitskaart toewijzen.

Wanneer de pagina die moet worden gedownload voor alle ontvangers gelijk is, kunt u het volgende het beste doen:

`<%@ include url="http://mynewsletter.com" %>`

In dat geval wordt de pagina tijdens de analyse gedownload, voordat de traceringsdetectie wordt uitgevoerd. Zo kan Adobe Campaign de koppelingen detecteren, een tag-id toewijzen en bijhouden.

## Aanbevolen patroon

Na het verwerken van `<%@` instructies heeft de URL die moet worden bijgehouden de volgende syntaxis: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Alle andere patronen worden niet ondersteund door Adobe en moeten worden vermeden om potentiële veiligheidshiaten te voorkomen.

## Waarschuwingen bij http://&lt;%=myURL%>-patroon

De syntaxis `<a href="http://<%=myURL%>">` is niet veilig en wordt niet aanbevolen omdat:

* Tidy kan sommige koppelingen onjuist repareren, wat willekeurig kan gebeuren. Het typische symptoom is een stuk van HTML dat in de e-mailproefdrukken maar niet in de voorproef zichtbaar is.
* Het doorsnijden van de URL is problematisch, sommige tekens in de URL kunnen problemen veroorzaken.
* U kunt geen parameter met de naam ID hebben die in strijd is met een parameter in de URL voor omleiding.
* Het belang van tracering is dan beperkt tot statistieken over de levering, aangezien Adobe Campaign onverschillig alle mogelijke waarden van &quot;myURL&quot; bijhoudt.

Raadpleeg [deze pagina](https://helpx.adobe.com/campaign/kb/acc-security.html#privacy) voor meer informatie.
