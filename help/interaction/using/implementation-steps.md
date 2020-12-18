---
solution: Campaign Classic
product: campaign
title: Implementatiestappen
description: Implementatiestappen
audience: interaction
content-type: reference
topic-tags: general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 3%

---


# Implementatiestappen{#implementation-steps}

## Interactie {#configuring-interaction} configureren

>[!NOTE]
>
>De volgende stappen moeten worden uitgevoerd door een profiel **Administrator** en alleen in ontwerpomgevingen.

1. Gebruikersprofielen maken. Raadpleeg [Operator-profielen](../../interaction/using/operator-profiles.md) voor meer informatie.
1. Creërend een aanbiedingsmilieu door dimensie te richten. Voor meer op dit, verwijs naar [Creërend een aanbiedingsmilieu](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Typologische regels maken voor elke omgeving. Raadpleeg [Een aanbiedingspresentatieregel maken en ernaar verwijzen](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule) voor meer informatie.
1. Het creëren van aanbiedingsruimten voor elke milieu en het vormen van teruggevende functies. Raadpleeg [Aanbiedingsruimten maken](../../interaction/using/creating-offer-spaces.md) voor meer informatie.

   >[!NOTE]
   >
   >Als de ruimte door een eenheidkanaal op bepaalde wijze wordt bepaald, moet u de geavanceerde parameters voor deze ruimte specificeren.

1. Het vormen van de aanbiedingsmotor voor binnenkomende interactie om één of verscheidene aanbiedingen voor te stellen en bij te werken.

   De verschillende integratiemodi worden gedetailleerd in [Info over binnenkomende kanalen](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >Wanneer een ruimte op het binnenkomende kanaal van het Web wordt gecreeerd, is een configuratie ook noodzakelijk op de plaats waarop de aanbieding zal worden getoond.

## De aanbiedingscatalogus beheren {#managing-the-offer-catalog-}

>[!NOTE]
>
>De volgende stappen moeten worden uitgevoerd door een **Aanbiedingsmanager**.

1. Het creëren van aanbiedingscategorieën in ontwerpmilieu&#39;s. Raadpleeg [Aanbiedingscategorieën maken](../../interaction/using/creating-offer-categories.md) voor meer informatie.
1. Aanbiedingen maken in ontwerpomgevingen. Raadpleeg [Een aanbieding maken](../../interaction/using/creating-an-offer.md) voor meer informatie.
1. Aanbiedingen goedkeuren en publiceren op één of meerdere ruimten om deze beschikbaar te maken in live omgevingen voor de leveringsmanager. Raadpleeg [Een aanbieding goedkeuren en activeren](../../interaction/using/approving-and-activating-an-offer.md) voor meer informatie.

## De aanbiedingscatalogus {#using-the-offer-catalog-} gebruiken

>[!NOTE]
>
>De volgende stappen moeten worden uitgevoerd door een profiel **Delivery Manager**. Ze kunnen alleen aanbiedingen in live omgevingen bewerken.

1. Een campagne maken.
1. Verwijzen naar een aanbieding in een campagne of een campagnelevering. Voor meer op dit, verwijs naar [Ongeveer uitgaande kanalen](../../interaction/using/about-outbound-channels.md).

