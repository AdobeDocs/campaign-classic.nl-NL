---
title: IMS-problemen oplossen
seo-title: IMS-problemen oplossen
description: IMS-problemen oplossen
seo-description: null
page-status-flag: never-activated
uuid: 5db95afc-8cbf-4ec3-b58f-504486fe4a40
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: e31db11a-ad8e-4fd0-bab7-0df1079231c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# IMS-problemen oplossen{#ims-troubleshooting}

De volgende het oplossen van problemenuiteinden zullen **on-premise** klanten helpen de gemeenschappelijkste problemen oplossen die wanneer het gebruiken van de integratie IMS gebeuren. Neem contact op met Adobe voor **gehoste** klanten.

**Externe account**

Er mag slechts **één** externe account met de volgende instellingen zijn:

* **Interne naam**: Adobe_Marketing_Cloud
* **Type**: Adobe Marketing Cloud

Verwijder gedupliceerde externe accounts die dezelfde instellingen hebben.

**Productcontext**

Als het veld **Productcontext** voor de externe account is ingesteld, controleert u of de waarde is ingesteld op: **dma_campagne_classic**

Zorg ervoor dat de productcontext hetzelfde is voor Campagne en Experience Cloud.

Als de **productcontext** bijvoorbeeld niet wordt weergegeven, moet de standaardproductcontext **dma_campagne** zijn in zowel Campagne als Experience Cloud. Als het veld **Productcontext** wordt weergegeven, moet de standaardproductcontext **dma_campagne_classic** zijn in zowel Campagne als Experience Cloud.

**[!UICONTROL IMS Server URL]**

Controleer in de externe account van **Adobe Marketing Cloud** voor campagne of het **[!UICONTROL IMS Server URL]** gaat om [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) of [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/). Zorg ervoor zowel stadium als de productie instanties aan het zelfde IMS productieeindpunt richten.

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

De **callback-URL** moet worden weergegeven en beginnen met &quot;https://&quot;. Controleer of de URL **van de** callback is gekoppeld aan de overeenkomstige instantie. De productie-instantie moet bijvoorbeeld omleiden naar de productie-URL.

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

* De gebruiker heeft geen toegang tot de aanmeldingspagina voor de Adobe-id:

   Verwijs naar de vorige stappen om de werkingsgebiedconfiguratie te controleren.

