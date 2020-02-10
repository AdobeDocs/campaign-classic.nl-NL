---
title: Uitvoeringsstappen
seo-title: Uitvoeringsstappen
description: Uitvoeringsstappen
seo-description: null
page-status-flag: never-activated
uuid: 11582071-00a2-4245-af3e-bc81174ce223
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: general-operation
discoiquuid: 7f79c0d8-77b0-4cc6-a888-7dbd32d2f3b6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Uitvoeringsstappen{#implementation-steps}

## Interactie configureren {#configuring-interaction}

>[!NOTE]
>
>De volgende stappen moeten worden uitgevoerd door een **beheerdersprofiel** en alleen in ontwerpomgevingen.

1. Gebruikersprofielen maken. Raadpleeg de profielen [van](../../interaction/using/operator-profiles.md)operatoren voor meer informatie.
1. Creërend een aanbiedingsmilieu door dimensie te richten. Raadpleeg [Een aanbiedingsomgeving](../../interaction/using/live-design-environments.md#creating-an-offer-environment)maken voor meer informatie hierover.
1. Typologische regels maken voor elke omgeving. Voor meer op dit, verwijs naar het [Creëren van en het van verwijzingen voorzien van een de presentatieregel](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule)van de aanbieding.
1. Het creëren van aanbiedingsruimten voor elke milieu en het vormen van teruggevende functies. Raadpleeg [Aanbiedingsruimten](../../interaction/using/creating-offer-spaces.md)maken voor meer informatie hierover.

   >[!NOTE]
   >
   >Als de ruimte door een eenheidkanaal op bepaalde wijze wordt bepaald, moet u de geavanceerde parameters voor deze ruimte specificeren.

1. Het vormen van de aanbiedingsmotor voor binnenkomende interactie om één of verscheidene aanbiedingen voor te stellen en bij te werken.

   De verschillende integratiemodi worden gedetailleerd beschreven in [Over binnenkomende kanalen](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >Wanneer een ruimte op het binnenkomende kanaal van het Web wordt gecreeerd, is een configuratie ook noodzakelijk op de plaats waarop de aanbieding zal worden getoond.

## De aanbiedingencatalogus beheren {#managing-the-offer-catalog-}

>[!NOTE]
>
>De volgende stappen moeten worden uitgevoerd door een **Offertenbeheerder**.

1. Het creëren van aanbiedingscategorieën in ontwerpmilieu&#39;s. Zie Aanbiedingscategorieën [maken voor meer informatie](../../interaction/using/creating-offer-categories.md).
1. Aanbiedingen maken in ontwerpomgevingen. Raadpleeg [Een aanbieding](../../interaction/using/creating-an-offer.md)maken voor meer informatie.
1. Aanbiedingen goedkeuren en publiceren op één of meerdere ruimten om deze beschikbaar te maken in live omgevingen voor de leveringsmanager. Raadpleeg [Goedkeuring en activering van een aanbieding](../../interaction/using/approving-and-activating-an-offer.md)voor meer informatie.

## De aanbiedingencatalogus gebruiken {#using-the-offer-catalog-}

>[!NOTE]
>
>De volgende stappen moeten worden uitgevoerd door een **Delivery Manager** -profiel. Ze kunnen alleen aanbiedingen in live omgevingen bewerken.

1. Een campagne maken.
1. Verwijzen naar een aanbieding in een campagne of een campagnelevering. Voor meer op dit, verwijs naar [Ongeveer uitgaande kanalen](../../interaction/using/about-outbound-channels.md).

