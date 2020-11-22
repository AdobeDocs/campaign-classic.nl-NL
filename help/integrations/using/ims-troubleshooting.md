---
solution: Campaign Classic
product: campaign
title: Problemen met IMS oplossen
description: Problemen met IMS oplossen
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 1%

---


# Problemen met IMS oplossen{#ims-troubleshooting}

De volgende het oplossen van problemenuiteinden zullen **on-premise** klanten helpen de gemeenschappelijkste problemen oplossen die wanneer het gebruiken van de integratie IMS gebeuren. Neem contact op met Adobe voor **gehoste** klanten.

**Externe account**

Er mag slechts **één** externe account met de volgende instellingen zijn:

* **Interne naam**: Adobe_Marketing_Cloud
* **Type**: Adobe Marketing Cloud

Verwijder gedupliceerde externe accounts die dezelfde instellingen hebben.

**Productcontext**

Als het veld **Productcontext** voor de externe account is ingesteld, controleert u of de waarde is ingesteld op: **dma_campagne_classic**

Zorg ervoor dat de productcontext hetzelfde is voor Campagne en Experience Cloud.

Als de **productcontext** bijvoorbeeld niet wordt weergegeven, moet de standaardproductcontext **dma_campagne** zijn in zowel Campagne als Experience Cloud. Als het gebied van de Context **van het** Product verschijnt, zou de standaardproductcontext **dma_campagne_classic** in zowel Campagne als Experience Cloud moeten zijn.

**[!UICONTROL IMS Server URL]**

Controleer in de externe account van Campagne **Adobe Marketing Cloud** of het **[!UICONTROL IMS Server URL]** gaat om [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) of [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/). Zorg ervoor zowel stadium als de productie instanties aan het zelfde IMS productieeindpunt richten.

**Associatiemasker**

* Controleer of de gebruiker die zich probeert aan te melden deel uitmaakt van een operatorgroep op het Enterprise-dashboard.
* Controleer of het voorvoegsel voor de naam van de operatorgroep van de gebruiker in het Enterprise-dashboard **[!UICONTROL Association Mask]** is.
* Zorg ervoor dat er geen witruimten en spelfouten zijn.
* Controleer of de namen van de groepen operatoren in Campagne niet zijn gewijzigd en of ze de volgende syntaxis in acht nemen:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Toepassingsgebied**

De gebieden die in de externe rekening van de Campagne worden bepaald moeten een ondergroep van die zijn provisioned door IMS.

**URL voor terugbellen**

De **Callback URL** zou aan de lijst van gewenste personen moeten worden toegevoegd en met &quot;https://&quot;beginnen. Controleer of de URL **van de** callback is gekoppeld aan de overeenkomstige instantie. De productie-instantie moet bijvoorbeeld omleiden naar de productie-URL.

**Client-id en geheim**

De client-id komt overeen met de externe account van de campagne en de id die door IMS is ingericht.

Controleer of het ingevoerde clientgeheim juist is.

**De server opnieuw starten**

Start de server opnieuw als er wijzigingen zijn aangebracht in de bovenstaande instellingen in de externe account van Campagne

**Veelvoorkomende fouttypen en mogelijke oplossingen**

* De gebruiker wordt omgeleid naar de pagina adobe.com:

   Er is een probleem met het **[!UICONTROL Callback URL]**. Raadpleeg de vorige stappen om de **[!UICONTROL Callback URL]** configuratie te controleren.

* Bericht &quot;Login heeft geen recht dat de uitdrukking&quot;aanpast:

   Verwijs naar de vorige stappen om de configuratie van de **[!UICONTROL Association Mask]** en van de exploitantgroepen te controleren.

* De gebruiker heeft geen toegang tot de Adobe ID-aanmeldingspagina:

   Verwijs naar de vorige stappen om de werkingsgebiedconfiguratie te controleren.

