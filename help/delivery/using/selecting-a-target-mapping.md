---
product: campaign
title: Een targettoewijzing selecteren
description: Leer hoe u toewijzingen als doel instelt
feature: Delivery Templates
hide: true
hidefromtoc: true
role: User
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 446062946b64c9a4d065b6a56d263914cbe628f8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 9%

---

# Een targettoewijzing selecteren{#selecting-a-target-mapping}

Aanleveringssjablonen zijn standaard gericht op **[!UICONTROL Recipients]** . Hun doelafbeelding gebruikt daarom de gebieden van **nms:ontvankelijke** lijst. Adobe Campaign biedt andere doeltoewijzingen voor uw leveringen, die op basis van uw behoeften worden gebruikt.

![](assets/delivery_select_mapping.png)

Deze toewijzingen zijn als volgt:

| Naam | Gebruiken | Standaardschema |
|---|---|---|
| Ontvangers | Leveren aan ontvangers van de Adobe Campaign-database | nms:ontvanger |
| Bezoekers | Leveren aan bezoekers van wie de profielen via verwijzing (virale marketing) of via sociale netwerken (Facebook, X - voorheen bekend als Twitter) zijn verzameld. | mns:bezoeker |
| Lidmaatschappen | Leveren aan ontvangers die zijn geabonneerd op een informatiedienst zoals een nieuwsbrief | nms:abonnement |
| Abonnementen van bezoekers | Leveren aan bezoekers die zijn geabonneerd op een informatiedienst | nms:bezoekerSub |
| Service | Publish naar een X-account of een Facebook-pagina | nms:service |
| Operatoren | Leveren aan Adobe Campaign-operatoren | nms:operator |
| Extern bestand | Afleveren via een bestand dat alle benodigde informatie voor levering bevat | Geen gekoppeld schema, geen doel ingevoerd |

>[!NOTE]
>
>U kunt ook nieuwe doeltoewijzingen maken. Deze bewerking is gereserveerd voor professionele gebruikers. Raadpleeg [deze sectie](../../configuration/using/target-mapping.md) voor meer informatie.
