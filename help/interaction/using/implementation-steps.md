---
product: campaign
title: Implementatiestappen
description: Implementatiestappen
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 3%

---

# Implementatiestappen{#implementation-steps}

![](../../assets/v7-only.svg)

## Interactie configureren {#configuring-interaction}

>[!NOTE]
>
>De volgende stappen moeten worden uitgevoerd door een **Beheerder** en alleen in ontwerpomgevingen.

1. Gebruikersprofielen maken. Raadpleeg voor meer informatie hierover [Operatorprofielen](../../interaction/using/operator-profiles.md).
1. Creërend een aanbiedingsmilieu door dimensie te richten. Raadpleeg voor meer informatie hierover [Een aanbiedingsomgeving maken](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Typologische regels maken voor elke omgeving. Raadpleeg voor meer informatie hierover [Een presentatieregel voor aanbiedingen maken en ernaar verwijzen](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. Het creëren van aanbiedingsruimten voor elke milieu en het vormen van teruggevende functies. Raadpleeg voor meer informatie hierover [Aanbiedingsruimten maken](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >Als de ruimte door een eenheidkanaal op bepaalde wijze wordt bepaald, moet u de geavanceerde parameters voor deze ruimte specificeren.

1. Het vormen van de aanbiedingsmotor voor binnenkomende interactie om één of verscheidene aanbiedingen voor te stellen en bij te werken.

   De verschillende integratiemodi worden nader beschreven in [Over binnenkomende kanalen](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >Wanneer een ruimte op het binnenkomende kanaal van het Web wordt gecreeerd, is een configuratie ook noodzakelijk op de plaats waarop de aanbieding zal worden getoond.

## De aanbiedingencatalogus beheren {#managing-the-offer-catalog-}

>[!NOTE]
>
>De volgende stappen moeten worden uitgevoerd door **Aanbiedingsmanager**.

1. Het creëren van aanbiedingscategorieën in ontwerpmilieu&#39;s. Raadpleeg voor meer informatie hierover [Categorieën voorstellen maken](../../interaction/using/creating-offer-categories.md).
1. Aanbiedingen maken in ontwerpomgevingen. Raadpleeg voor meer informatie hierover [Een aanbieding maken](../../interaction/using/creating-an-offer.md).
1. Aanbiedingen goedkeuren en publiceren op één of meerdere ruimten om deze beschikbaar te maken in live omgevingen voor de leveringsmanager. Raadpleeg voor meer informatie hierover [Een aanbieding goedkeuren en activeren](../../interaction/using/approving-and-activating-an-offer.md).

## De aanbiedingencatalogus gebruiken {#using-the-offer-catalog-}

>[!NOTE]
>
>De volgende stappen moeten worden uitgevoerd door een **Leveringsmanager** profiel. Ze kunnen alleen aanbiedingen in live omgevingen bewerken.

1. Een campagne maken.
1. Verwijzen naar een aanbieding in een campagne of een campagnelevering. Raadpleeg voor meer informatie hierover [Informatie over uitgaande kanalen](../../interaction/using/about-outbound-channels.md).
