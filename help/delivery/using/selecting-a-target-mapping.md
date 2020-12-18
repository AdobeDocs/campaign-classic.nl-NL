---
solution: Campaign Classic
product: campaign
title: Een doeltoewijzing selecteren
description: Een doeltoewijzing selecteren
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 8%

---


# Een doeltoewijzing selecteren{#selecting-a-target-mapping}

Standaard richten leveringssjablonen zich op **[!UICONTROL Recipients]**. Hun doelafbeelding gebruikt daarom de gebieden van **nms:ontvanger** lijst. Adobe Campaign biedt andere doeltoewijzingen voor uw leveringen, die op basis van uw behoeften worden gebruikt.

![](assets/delivery_select_mapping.png)

Deze toewijzingen zijn als volgt:

| Naam | Gebruiken | Standaardschema |
|---|---|---|
| Ontvangers | Leveren aan ontvangers van de Adobe Campaign-database | nms:ontvanger |
| Bezoekers | Leveren aan bezoekers van wie de profielen zijn verzameld via verwijzing (virale marketing) of via sociale netwerken (Facebook, Twitter) bijvoorbeeld. | mns:bezoeker |
| Abonnementen | Leveren aan ontvangers die zijn geabonneerd op een informatiedienst zoals een nieuwsbrief | nms:abonnement |
| Abonnementen van bezoekers | Leveren aan bezoekers die zijn geabonneerd op een informatiedienst | nms:bezoekerSub |
| Service | Publiceren naar een Twitter-account of een Facebook-pagina | nms:service |
| Operatoren | Leveren aan Adobe Campaign-operatoren | nms:operator |
| Extern bestand | Afleveren via een bestand dat alle benodigde informatie voor levering bevat | Geen gekoppeld schema, geen doel ingevoerd |

>[!NOTE]
>
>U kunt ook nieuwe doeltoewijzingen maken. Deze bewerking is gereserveerd voor professionele gebruikers. Voor meer informatie, verwijs naar [de gids van de Configuratie](../../configuration/using/target-mapping.md).
