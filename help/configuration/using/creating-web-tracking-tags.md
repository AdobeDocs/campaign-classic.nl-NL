---
product: campaign
title: Webtags voor bijhouden maken
description: Leer hoe u webtrackingtags maakt
feature: Application Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 2%

---

# Webtags voor bijhouden maken{#creating-web-tracking-tags}

Op elke pagina van de site die u wilt bijhouden, moet in uw Adobe Campaign-platform worden verwezen. Deze verwijzing kan op twee manieren worden uitgevoerd:

1. Handmatige definitie van URL&#39;s die moeten worden bijgehouden,
1. Aanmaken van URL&#39;s die u ter plaatse wilt bijhouden.

## De URL&#39;s definiëren die in de toepassing moeten worden bijgehouden {#defining-the-urls-to-be-tracked-in-the-application}

Met deze methode kunt u handmatig de pagina&#39;s definiëren die moeten worden bijgehouden en vervolgens een voorbeeld genereren van de bijbehorende tag voor webtracering. Deze bewerking wordt gedefinieerd in het dialoogvenster **[!UICONTROL Campaign execution>Resources>Web tracking tags]** knooppunt van de clientconsole.

![](assets/d_ncs_integration_webtracking_screen.png)

U genereert de HTML-code die op de pagina moet worden ingevoegd:

* Voer het label van de tag in: het wordt weergegeven in de logboeken voor bijhouden,
* De bron-URL aangeven: dit veld dient ter informatie en u kunt de bijgehouden pagina aangeven (optioneel).
* Voer zo nodig een geldigheidsperiode in.
* Klikken **[!UICONTROL Generate]** HTML-code.

Vervolgens kopieert u de gegenereerde code en plakt u deze in de pagina die u wilt bijhouden.

## Tijdens het maken van URL&#39;s die moeten worden bijgehouden {#on-the-fly-creation-of-urls-to-be-tracked}

U kunt de URL&#39;s voor webtracering direct maken door informatie toe te voegen aan de waarde van de optie **gelabeld** parameter:

* Type bijgehouden pagina: &#39;w&#39; voor WEB of &#39;t&#39; voor TRANSACTIE,
* De interne naam van de map waarin de URL moet worden gemaakt.

Deze twee gegevens moeten worden samengevoegd met de id van de bijgehouden pagina door het teken &#39;|&#39; toe te voegen:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Vergeet niet de waarde van het gereedschap **gelabeld** parameter wanneer deze wordt gebruikt als een URL-parameter.

**Voorbeeld**: het maken van een URL voor webtracking van het type transactie.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
