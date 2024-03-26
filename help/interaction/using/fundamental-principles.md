---
product: campaign
title: Grondbeginselen
description: Grondbeginselen
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 3%

---

# Grondbeginselen{#fundamental-principles}



## Omgevingen implementeren {#deploying-environments}

Er zijn twee milieu&#39;s voor elke het richten dimensie die wordt gebruikt wanneer het beheren van aanbiedingen:

* Een ontwerpomgeving waarin de aanbiedingsmanager zorgt voor het maken en categoriseren van aanbiedingen, het bewerken ervan en het starten van het goedkeuringsproces zodat deze kunnen worden gebruikt. De regels voor elke categorie, de aanbiedingsruimten waarop aanbiedingen kunnen worden ingediend en de vooraf gedefinieerde filters die worden gebruikt om te bepalen of een aanbieding in aanmerking komt, worden ook in deze omgeving gedefinieerd.

  Categorieën kunnen ook handmatig worden gepubliceerd in de online omgeving.

  Het proces voor het goedkeuren van aanbiedingen wordt beschreven in het dialoogvenster [Aanbiedingen goedkeuren en activeren](../../interaction/using/approving-and-activating-an-offer.md) sectie.

* Een live omgeving waarin goedgekeurde aanbiedingen van de ontwerpomgeving en de verschillende aanbiedingsruimten, filters, categorieën en regels die in de ontwerpomgeving zijn geconfigureerd, kunnen worden gevonden. Tijdens een vraag aan de aanbiedingsmotor, zal de motor altijd aanbiedingen van het levende milieu gebruiken.

Een aanbieding wordt slechts opgesteld op de aanbiedingsruimten die tijdens het goedkeuringsproces worden geselecteerd. Daarom kan een aanbieding levend maar onbruikbaar op een aanbiedingsruimte zijn die ook levend is.

![](assets/architecture_interaction1.png)

## Interactietypen en contactmethoden {#interaction-types-and-contact-methods}

Er zijn twee mogelijke soorten interactie: binnenkomende interactie (in werking gesteld door een contact) en uitgaande interactie (in werking gesteld door de aanbiedingsontwerper).

Deze twee soorten interactie kunnen worden uitgevoerd in monitaire modus (het aanbod wordt berekend voor één contactpersoon) of in batchmodus (het aanbod wordt berekend voor een reeks contactpersonen). Over het algemeen worden binnenkomende interacties uitgevoerd in monitaire modus en uitgaande interacties in batchmodus. Er kunnen echter bepaalde uitzonderingen zijn, bijvoorbeeld voor transactiemeldingen, waarbij de uitgaande interactie plaatsvindt in de eenheidsmodus (zie [deze sectie](../../message-center/using/about-transactional-messaging.md)).

Zodra een aanbieding kan of moet worden voorgelegd (volgens de uitgevoerde configuraties), speelt de aanbiedingsmotor de intermediaire rol: het berekent automatisch de best mogelijke aanbieding voor een contact tussen de beschikbare aanbieden door ontvangen gegevens over het contact en de verschillende regels te combineren die kunnen worden toegepast zoals gespecificeerd in de toepassing.

![](assets/architecture_interaction2.png)
