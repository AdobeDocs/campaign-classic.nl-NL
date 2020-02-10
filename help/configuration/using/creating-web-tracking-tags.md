---
title: Tags voor webtracking maken
seo-title: Tags voor webtracking maken
description: Tags voor webtracking maken
seo-description: null
page-status-flag: never-activated
uuid: c5599bdd-e6b8-4db4-b0ca-aaee2adc1919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 647ca037-4efb-4524-9642-11056d096aea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Tags voor webtracking maken{#creating-web-tracking-tags}

Op elke pagina van de site die u wilt bijhouden, moet in het Adobe Campagneplatform worden verwezen. Deze verwijzing kan op twee manieren worden uitgevoerd:

1. Handmatige definitie van URL&#39;s die moeten worden bijgehouden,
1. Aanmaken van URL&#39;s die u ter plaatse wilt bijhouden.

## De URL&#39;s definiëren die in de toepassing moeten worden bijgehouden {#defining-the-urls-to-be-tracked-in-the-application}

Met deze methode kunt u handmatig de pagina&#39;s definiëren die moeten worden bijgehouden en vervolgens een voorbeeld genereren van de bijbehorende webtrackingtag. Deze bewerking wordt gedefinieerd in het **[!UICONTROL Campaign execution>Resources>Web tracking tags]** knooppunt van de clientconsole.

![](assets/d_ncs_integration_webtracking_screen.png)

De HTML-code genereren die op de pagina moet worden ingevoegd:

* Voer het label in: het wordt weergegeven in de trackinglogboeken;
* Geef de bron-URL op: dit veld dient ter informatie en geeft de bijgehouden pagina aan (optioneel);
* Voer zo nodig een geldigheidsperiode in.
* Klik op **[!UICONTROL Generate]** HTML-code.

Vervolgens kopieert u de gegenereerde code en plakt u deze in de pagina die u wilt bijhouden.

## Tijdens het maken van URL&#39;s die moeten worden bijgehouden {#on-the-fly-creation-of-urls-to-be-tracked}

U kunt URL&#39;s voor webspatiëring direct maken door informatie toe te voegen aan de waarde van de parameter **tagid** :

* Type bijgehouden pagina: &quot;w&quot; voor WEB of &quot;t&quot; voor TRANSACTIE,
* De interne naam van de map waarin de URL moet worden gemaakt.

Deze twee gegevens moeten worden samengevoegd met de id van de bijgehouden pagina door het teken &#39;|&#39; toe te voegen:

```
tagid=<identifier>|<type>|<foldername>
```

>[!CAUTION]
>
>Vergeet niet de waarde van de **tagid** -parameter te coderen wanneer deze wordt gebruikt als een URL-parameter.

**Voorbeeld**: het maken van een URL voor webtracering van het transactietype.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
