---
product: campaign
title: Implementatiestappen
description: Implementatiestappen voor de module Campagne Interaction
feature: Interaction, Offers
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 1%

---

# Implementatiestappen{#implementation-steps}



## Interactie configureren {#configuring-interaction}

>[!NOTE]
>
>De volgende stappen zouden door een **profiel van de Beheerder** en slechts in ontwerpmilieu&#39;s moeten worden uitgevoerd.

1. Gebruikersprofielen maken. Voor meer op dit, verwijs naar [ profielen van de Exploitant ](../../interaction/using/operator-profiles.md).
1. Creërend een aanbiedingsmilieu door dimensie te richten. Voor meer op dit, verwijs naar [ Creërend een aanbiedingsmilieu ](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Typologische regels maken voor elke omgeving. Voor meer op dit, verwijs naar [ het Creëren van en het van verwijzingen voorzien van een regel van de aanbiedingspresentatie ](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. Het creëren van aanbiedingsruimten voor elke milieu en het vormen van teruggevende functies. Voor meer op dit, verwijs naar [ Creërend aanbiedingsruimten ](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >Als de ruimte door een eenheidkanaal op bepaalde wijze wordt bepaald, moet u de geavanceerde parameters voor deze ruimte specificeren.

1. Het vormen van de aanbiedingsmotor voor binnenkomende interactie om één of verscheidene aanbiedingen voor te stellen en bij te werken.

   De diverse integratiemodi zijn gedetailleerd in [ Ongeveer binnenkomende kanalen ](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >Wanneer een ruimte op het binnenkomende kanaal van het Web wordt gecreeerd, is een configuratie ook noodzakelijk op de plaats waarop de aanbieding zal worden getoond.

## De aanbiedingencatalogus beheren {#managing-the-offer-catalog-}

>[!NOTE]
>
>De volgende stappen zouden door een **manager van de Aanbieding** moeten worden uitgevoerd.

1. Het creëren van aanbiedingscategorieën in ontwerpmilieu&#39;s. Voor meer op dit, verwijs naar [ Creërend aanbiedingscategorieën ](../../interaction/using/creating-offer-categories.md).
1. Aanbiedingen maken in ontwerpomgevingen. Voor meer op dit, verwijs naar [ Creërend een aanbieding ](../../interaction/using/creating-an-offer.md).
1. Aanbiedingen goedkeuren en publiceren op één of meerdere ruimten om deze beschikbaar te maken in live omgevingen voor de leveringsmanager. Voor meer op dit, verwijs naar [ goedkeurend en activerend een aanbieding ](../../interaction/using/approving-and-activating-an-offer.md).

## De aanbiedingencatalogus gebruiken {#using-the-offer-catalog-}

>[!NOTE]
>
>De volgende stappen zouden door het profiel van de manager van de a **Levering** moeten worden uitgevoerd. Ze kunnen alleen aanbiedingen in live omgevingen bewerken.

1. Een campagne maken.
1. Verwijzen naar een aanbieding in een campagne of een campagnelevering. Voor meer op dit, verwijs naar [ Ongeveer uitgaande kanalen ](../../interaction/using/about-outbound-channels.md).
