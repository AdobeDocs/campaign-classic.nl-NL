---
title: Soorten leveringen
seo-title: Soorten leveringen
description: Soorten leveringen
seo-description: null
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 194d2263de0bf98afa0efc7e2e0b4ca433c95b6d

---


# Soorten leveringen{#types-of-deliveries}

Er zijn drie typen leveringsobjecten in campagne:

## Eén levering {#single-delivery}

Een **levering** is een standalone leveringsvoorwerp dat eens wordt uitgevoerd. Het kan worden gedupliceerd, opnieuw worden bereid, maar zolang het in zijn definitieve staat (geannuleerd, gestopt, gebeëindigd) is, kan het niet opnieuw worden gebruikt.

Leveringen kunnen worden gemaakt op basis van de lijst met leveringen of binnen een workflow via een [leveringsactiviteit](../../workflow/using/delivery.md) .

Workflows bieden ook specifieke leveringsactiviteiten op basis van het type kanaal dat u wilt gebruiken. Zie [deze sectie](../../workflow/using/cross-channel-deliveries.md)voor meer informatie over deze activiteiten.

## Terugkerende levering {#recurring-delivery}

Met een **terugkerende levering** kunt u elke keer dat de activiteit wordt uitgevoerd, een nieuwe levering maken. Zo voorkomt u dat u een nieuwe levering moet maken voor terugkerende taken.

Als u dit soort activiteiten bijvoorbeeld eens per maand uitvoert, krijgt u na een jaar 12 leveringen.

De terugkomende leveringen worden gecreeerd binnen werkschema&#39;s via de [Terugkomende leveringsactiviteit](../../workflow/using/recurring-delivery.md). Een voorbeeld van deze activiteit die wordt gebruikt wordt getoond in deze sectie: Een terugkerende levering [maken in een doelworkflow](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Doorlopende levering {#continuous-delivery}

Met een **doorlopende levering** kunt u nieuwe ontvangers aan een bestaande levering toevoegen, zodat u niet telkens een nieuwe levering hoeft te maken wanneer deze wordt uitgevoerd.

Als een informatie in de levering verandert (inhoud, naam, enz.), wordt een nieuw leveringsvoorwerp gecreeerd bij de leveringsuitvoering. Als er geen informatie is gewijzigd, wordt hetzelfde leveringsobject opnieuw gebruikt en worden de logbestanden voor levering en bijhouden toegevoegd aan hetzelfde object.

Als voorbeeld, als u dit type van activiteit eens per maand in werking stelt, zult u eindigen met één enkele levering na een jaar (vooropgesteld u geen verandering in de levering).

De ononderbroken leveringen worden gecreeerd binnen werkschema&#39;s via de [Ononderbroken leveringsactiviteit](../../workflow/using/continuous-delivery.md).
