---
product: campaign
title: Problemen met IMS oplossen
description: Problemen met IMS oplossen
feature: Configuration
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# Problemen met IMS oplossen{#ims-troubleshooting}


De volgende tips voor het oplossen van problemen helpen **op locatie** en **hybride** klanten lossen de gemeenschappelijkste problemen op die wanneer het gebruiken van de integratie IMS gebeuren. Voor **gehost** klanten, gelieve Adobe te contacteren.

**Externe account**

Er mag alleen **één** externe account met de volgende instellingen:

* **Interne naam**: Adobe_Marketing_Cloud
* **Type**: ADOBE MARKETING CLOUD

Verwijder gedupliceerde externe accounts die dezelfde instellingen hebben.

**Productcontext**

Als de externe account een **Productcontext** veld, controleer of de waarde ervan is ingesteld op: **dma_campagne_classic**

Zorg ervoor dat de productcontext voor Campagne en Experience Cloud hetzelfde is.

Als de **Productcontext** niet wordt weergegeven, moet de standaardproductcontext **dma_campagne** in zowel Campagne als Experience Cloud. Als de **Productcontext** wordt weergegeven, moet de standaardproductcontext **dma_campagne_classic** in zowel Campagne als Experience Cloud.

**[!UICONTROL IMS Server URL]**

In de campagne **Adobe Marketing Cloud** externe account, controleer of de **[!UICONTROL IMS Server URL]** is ofwel `adobeid-na1.services.adobe.com` of `ims-na1.adobelogin.com`. Zorg ervoor zowel stadium als de productie instanties aan het zelfde IMS productieeindpunt richten.

**Associatiemasker**

* Controleer of de gebruiker die zich probeert aan te melden deel uitmaakt van een operatorgroep op het Enterprise-dashboard.
* Controleer of de **[!UICONTROL Association Mask]** is een voorvoegsel van de naam van de operatorgroep van de gebruiker in het Enterprise-dashboard.
* Zorg ervoor dat er geen witruimten en spelfouten zijn.
* Controleer of de namen van de groepen operatoren in Campagne niet zijn gewijzigd en of ze de volgende syntaxis in acht nemen:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Toepassingsgebied**

De gebieden die in de externe rekening van de Campagne worden bepaald moeten een ondergroep van die zijn provisioned door IMS.

**URL voor terugbellen**

De **URL voor terugbellen** worden toegevoegd aan de lijst van gewenste personen en beginnen met &quot;https://&quot;. Controleer of de **URL voor terugbellen** is gekoppeld aan het overeenkomstige exemplaar. De productie-instantie moet bijvoorbeeld omleiden naar de productie-URL.

**Client-id en geheim**

De client-id komt overeen met de externe account van de campagne en de id die door IMS is ingericht.

Controleer of het ingevoerde clientgeheim juist is.

**De server opnieuw starten**

Start de server opnieuw als er wijzigingen zijn aangebracht in de bovenstaande instellingen in de externe account voor campagne

**Algemene fouttypen en mogelijke oplossingen**

* Gebruiker wordt omgeleid naar adobe.com-pagina:

  Er is een probleem met de **[!UICONTROL Callback URL]**. Raadpleeg de vorige stappen om het dialoogvenster **[!UICONTROL Callback URL]** configuratie.

* Bericht &quot;Login heeft geen recht dat de uitdrukking&quot;aanpast:

  Raadpleeg de vorige stappen om het dialoogvenster **[!UICONTROL Association Mask]** en configuratie van groepen met operatoren.

* De gebruiker heeft geen toegang tot de Adobe ID-aanmeldingspagina:

  Verwijs naar de vorige stappen om de werkingsgebiedconfiguratie te controleren.
