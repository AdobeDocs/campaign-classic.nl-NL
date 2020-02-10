---
title: Een doeltoewijzing selecteren
seo-title: Een doeltoewijzing selecteren
description: Een doeltoewijzing selecteren
seo-description: null
page-status-flag: never-activated
uuid: 29a666a3-2ecc-4732-b068-c93935929771
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: e2c6e273-1640-4f46-a80e-0cecb06e2769
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Een doeltoewijzing selecteren{#selecting-a-target-mapping}

Standaard wordt voor leveringssjablonen het doel **[!UICONTROL Recipients]**. Hun doelafbeelding gebruikt daarom de gebieden van de **nms:ontvankelijke** lijst. Adobe Campaign biedt andere doeltoewijzingen voor uw leveringen die u op basis van uw behoeften wilt gebruiken.

![](assets/delivery_select_mapping.png)

Deze toewijzingen zijn als volgt:

| Naam | Gebruiken | Standaardschema |
|---|---|---|
| Ontvangers | Leveren aan ontvangers van de Adobe Campagne-database | nms:ontvanger |
| Bezoekers | Leveren aan bezoekers van wie de profielen zijn verzameld via verwijzing (virale marketing) of via sociale netwerken (Facebook, Twitter) bijvoorbeeld. | mns:bezoeker |
| Abonnementen | Leveren aan ontvangers die zijn geabonneerd op een informatiedienst zoals een nieuwsbrief | nms:abonnement |
| Abonnementen van bezoekers | Leveren aan bezoekers die zijn geabonneerd op een informatiedienst | nms:bezoekerSub |
| Service | Publiceren naar een Twitter-account of een Facebook-pagina | nms:service |
| Operatoren | Afleveren aan Adobe Campagneontwikkelaars | nms:operator |
| Extern bestand | Afleveren via een bestand dat alle benodigde informatie voor levering bevat | Geen gekoppeld schema, geen doel ingevoerd |

>[!NOTE]
>
>U kunt ook nieuwe doeltoewijzingen maken. Deze bewerking is gereserveerd voor professionele gebruikers. Voor meer informatie, verwijs naar de gids [van de](../../configuration/using/target-mapping.md)Configuratie.
