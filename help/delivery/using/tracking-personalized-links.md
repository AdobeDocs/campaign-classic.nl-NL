---
product: campaign
title: Aan de slag met de tracking van gepersonaliseerde koppelingen
description: Leer hoe u koppelingen schrijft in e-mailberichten die u kunt aanpassen en bijhouden ondersteunt in Campagne
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Personalization
role: User
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 7%

---

# Aan de slag met de tracking van gepersonaliseerde koppelingen {#tracking-personalized-links}

De koppelingen in e-mailinhoud die personalisatie bevatten, moeten specifiek worden gesynchroniseerd om te worden bijgehouden.

Met JavaScript in e-mailinhoud (HTML of Tekst) kunt u dynamische inhoud genereren en verzenden naar de ontvangers, met twee beperkingen:

* Het script heeft niet rechtstreeks toegang tot de database (SQL-functie en API-functies zijn niet beschikbaar).
* Adobe Campaign moet URL&#39;s kunnen detecteren zodat koppelingen kunnen worden bijgehouden. [Meer informatie](detecting-tracking-urls.md)

U kunt specifieke voorbewerkingsinstructies toevoegen om de URL te scripten en bij te houden. [Meer informatie](pre-processing-instructions.md)

Voor traceringsdetectie sluit Adobe Campaign in [Tidy](https://www.html-tidy.org/) om de HTML-bron te parseren en het patroon te detecteren. Alle URL&#39;s van de inhoud worden weergegeven zodat ze afzonderlijk kunnen worden bijgehouden. Adobe Campaign gebruikt Tidy opnieuw om de URL te vervangen (`http://myurl.com`) met een URL die naar de Adobe Campaign-omleidingsserver verwijst.

Bijvoorbeeld in de eerste inhoud: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` wordt voor een bepaalde ontvanger vervangen door: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Waarbij:

* &quot;h&quot; betekent HTML-inhoud (of &quot;t&quot; voor tekstinhoud).
* 617791 is de bericht-id / wideLog-id (hexadecimaal).
* 71ffa3 is NmsDelivery ID (hexadecimaal).
* 71ffa8 is de (hexadecimale) NmsTrackingUrl-id.
* p1, p2, enzovoort, zijn alle parameters die in de URL moeten worden vervangen.
