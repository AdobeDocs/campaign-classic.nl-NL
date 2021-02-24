---
solution: Campaign Classic
product: campaign
title: Aan de slag met het bijhouden van persoonlijke koppelingen
description: Leer hoe u koppelingen schrijft in e-mailberichten die u kunt aanpassen en het bijhouden van koppelingen ondersteunt in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Ga aan de slag met persoonlijke koppelingen die {#tracking-personalized-links} bijhouden

De koppelingen in e-mailinhoud die personalisatie bevatten, moeten specifiek worden gesynchroniseerd om te worden bijgehouden.

Met JavaScript in e-mailinhoud (HTML of Tekst) kunt u dynamische inhoud genereren en verzenden naar de ontvangers, met twee beperkingen:

* Het script heeft niet rechtstreeks toegang tot de database (SQL-functie en API-functies zijn niet beschikbaar).
* Adobe Campaign moet URL&#39;s kunnen detecteren zodat koppelingen kunnen worden bijgehouden (doel van dit document).

Voor traceringsdetectie sluit Adobe Campaign [Tidy](http://www.html-tidy.org/) in om de HTML-bron te parseren en het patroon te detecteren. Alle URL&#39;s van de inhoud worden weergegeven zodat ze afzonderlijk kunnen worden bijgehouden. Adobe Campaign gebruikt nogmaals Tidy om de URL (`http://myurl.com`) te vervangen door een URL die naar de Adobe Campaign-omleidingsserver wijst.

Bijvoorbeeld in de eerste inhoud: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` wordt voor een bepaalde ontvanger vervangen door: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Waar:

* &quot;h&quot; betekent HTML-inhoud (of &quot;t&quot; voor tekstinhoud).
* 617791 is de bericht-id / wideLog-id (hexadecimaal).
* 71ffa3 is NmsDelivery ID (hexadecimaal).
* 71ffa8 is de (hexadecimale) NmsTrackingUrl-id.
* p1, p2, enzovoort, zijn alle parameters die in de URL moeten worden vervangen.
