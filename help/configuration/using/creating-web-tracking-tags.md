---
product: campaign
title: Webtags voor bijhouden maken
description: Leer hoe u webtrackingtags maakt
feature: Application Settings
role: Developer
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Webtags voor bijhouden maken{#creating-web-tracking-tags}

Op elke pagina van de site die u wilt bijhouden, moet in uw Adobe Campaign-platform worden verwezen. Deze verwijzing kan op twee manieren worden uitgevoerd:

1. Handmatige definitie van URL&#39;s die moeten worden bijgehouden,
1. Aanmaken van URL&#39;s die u ter plaatse wilt bijhouden.

## De URL&#39;s definiëren die in de toepassing moeten worden bijgehouden {#defining-the-urls-to-be-tracked-in-the-application}

Met deze methode kunt u handmatig de pagina&#39;s definiëren die moeten worden bijgehouden en vervolgens een voorbeeld genereren van de bijbehorende tag voor webtracering. Deze bewerking wordt gedefinieerd in het knooppunt **[!UICONTROL Campaign execution>Resources>Web tracking tags]** van de clientconsole.

![](assets/d_ncs_integration_webtracking_screen.png)

De HTML-code genereren die op de pagina moet worden ingevoegd:

* Voer het label van de tag in: het wordt weergegeven in de logboeken voor bijhouden,
* De bron-URL aangeven: dit veld dient ter informatie en u kunt de bijgehouden pagina aangeven (optioneel).
* Voer zo nodig een geldigheidsperiode in.
* Klik op **[!UICONTROL Generate]** HTML-code.

Vervolgens kopieert u de gegenereerde code en plakt u deze in de pagina die u wilt bijhouden.

## Tijdens het maken van URL&#39;s die moeten worden bijgehouden {#on-the-fly-creation-of-urls-to-be-tracked}

U kunt Web het volgen URLs op de vlucht tot stand brengen door informatie aan de waarde van de **gelabelde** parameter toe te voegen:

* Type bijgehouden pagina: &#39;w&#39; voor WEB of &#39;t&#39; voor TRANSACTIE,
* De interne naam van de map waarin de URL moet worden gemaakt.

Deze twee gegevens moeten worden samengevoegd met de id van de bijgehouden pagina door het teken &#39;|&#39; toe te voegen:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Herinner me om de waarde van de **gelabelde** parameter te coderen wanneer het als parameter URL wordt gebruikt.

**Voorbeeld**: verwezenlijking van een transactie-type web het volgen URL.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
