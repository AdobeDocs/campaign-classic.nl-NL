---
product: campaign
title: Een targettoewijzing selecteren
description: Leer hoe u toewijzingen als doel instelt
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Delivery Templates
role: User
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 9%

---

# Een targettoewijzing selecteren{#selecting-a-target-mapping}

Standaard wordt voor leveringssjablonen het doel **[!UICONTROL Recipients]**. Daarom worden bij de vaststelling van hun streefdoelen de gebieden van de **nms:ontvanger** tabel. Adobe Campaign biedt andere doeltoewijzingen voor uw leveringen, die op basis van uw behoeften worden gebruikt.

![](assets/delivery_select_mapping.png)

Deze toewijzingen zijn als volgt:

| Naam | Gebruiken | Standaardschema |
|---|---|---|
| Ontvangers | Leveren aan ontvangers van de Adobe Campaign-database | nms:ontvanger |
| Bezoekers | Leveren aan bezoekers van wie de profielen via verwijzing (virale marketing) of via sociale netwerken (Facebook, X - voorheen bekend als Twitter) zijn verzameld. | mns:bezoeker |
| Lidmaatschappen | Leveren aan ontvangers die zijn geabonneerd op een informatiedienst zoals een nieuwsbrief | nms:abonnement |
| Abonnementen van bezoekers | Leveren aan bezoekers die zijn geabonneerd op een informatiedienst | nms:bezoekerSub |
| Service | Publiceren naar een X-account of een Facebook-pagina | nms:service |
| Operatoren | Leveren aan Adobe Campaign-operatoren | nms:operator |
| Extern bestand | Afleveren via een bestand dat alle benodigde informatie voor levering bevat | Geen gekoppeld schema, geen doel ingevoerd |

>[!NOTE]
>
>U kunt ook nieuwe doeltoewijzingen maken. Deze bewerking is gereserveerd voor professionele gebruikers. Raadpleeg [deze sectie](../../configuration/using/target-mapping.md) voor meer informatie.
