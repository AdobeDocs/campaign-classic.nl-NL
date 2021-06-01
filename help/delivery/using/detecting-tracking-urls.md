---
product: campaign
title: Tracking-URL's detecteren
description: Meer informatie over aanbevolen patronen voor het bijhouden van URL's
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 2%

---

# Tracking-URL&#39;s detecteren

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

## Onbeveiligd patroon

Wanneer u persoonlijke koppelingen toevoegt aan uw inhoud, moet u altijd geen persoonlijke instellingen opgeven in het gedeelte hostnaam van de URL om mogelijke hiaten in de beveiliging te voorkomen. Meer informatie vindt u op [deze pagina](../../installation/using/privacy.md#url-personalization).

De syntaxis `<a href="http://<%=myURL%>">` is bijvoorbeeld **niet beveiligd** en moet worden vermeden.

* Het gebruik van deze syntaxis kan tot beveiligingsproblemen leiden als de koppeling die door Adobe Campaign wordt gegenereerd een of meer parameters bevat.
* Tidy kan sommige koppelingen onjuist repareren, wat willekeurig kan gebeuren. Het typische symptoom is een stuk van HTML dat in de e-mailproefdrukken maar niet in de voorproef zichtbaar is.
* Het doorsnijden van de URL is problematisch, sommige tekens in de URL kunnen problemen veroorzaken.
* U kunt geen parameter met de naam ID hebben die in strijd is met een parameter in de URL voor omleiding.
* Het belang van tracering is dan beperkt tot statistieken over de levering, aangezien Adobe Campaign onverschillig alle mogelijke waarden van &quot;myURL&quot; bijhoudt.
