---
product: campaign
title: Seedadressen
description: Aan de slag met zaadadressen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Seed Address
role: User
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 8%

---

# Seedadressen{#about-seed-addresses}

Seed-adressen worden gebruikt om ontvangers die niet aan de gedefinieerde doelcriteria voldoen, doelgericht te benaderen. Op deze manier kunnen ontvangers die buiten het bereik van de levering vallen, de levering ontvangen, net als elke andere doelontvanger.

Een van de belangrijkste redenen voor het gebruik is **beveiliging van je mailinglijst**. Door zaadadressen in te voegen in uw mailinglijst kunt u zien of het door een derde wordt gebruikt, aangezien de zaadadressen het bevat de leveringen ontvangen die naar uw mailinglijst worden verzonden.

Bovendien laten de zaadadressen u toe **de personalisatie van de leveringen en rendering voorvertonen en testen** voordat zij worden verzonden, door hen proefstukken te sturen (zie [zaadadressen gebruiken als proefdruk](steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](steps-defining-the-target-population.md#seeds-and-proofs-video)

De zaadadreseigenschap heeft de volgende voordelen:

* Willekeurige vervanging van velden door gegevens uit ontvangende profielen: hiermee kunt u alleen het e-mailadres invoeren, bijvoorbeeld in de sectie met het zaadadres, en Campagne automatisch de andere velden van het profiel laten invullen (zie [Hoofdlettergebruik: de veldvervanging configureren](use-case-configuring-the-field-substitution.md)).
* Wanneer u een workflow met functies voor gegevensbeheer gebruikt, kunnen de aanvullende gegevens die in leveringen worden verwerkt, op het niveau van het zaadadres worden ingevoerd om waarden af te dwingen: dit verlaagt de vervanging van willekeurige waarden.
* Zaadadressen worden automatisch uitgesloten van rapporten over de volgende leveringsstatistieken: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

De zaadadressen worden toegevoegd aan het doel van leveringen door worden ingevoerd of door in de levering of de campagne direct worden gecreeerd.

>[!NOTE]
>
>De zaadadressen behoren niet tot de ontvangers lijst, zij worden gecreeerd in een afzonderlijke lijst. Als u de lijst van ontvangers met nieuwe gegevens uitbreidt, moet u de lijst van zaadadressen evenals met de zelfde gegevens uitbreiden. Anders, zullen zij uitgebreide gebieden niet in aanmerking worden genomen voor zaadadressen.
>
>Een voorbeeld van hoe te om de zaadadreslijst uit te breiden wordt voorgesteld in deze sectie: [Hoofdlettergebruik: zaadadressen op criteria selecteren](use-case-selecting-seed-addresses-on-criteria.md).

Voor direct-mailleveringen worden de zaadadressen toegevoegd tijdens extractie en gemengd in het uitvoerdocument.

>[!IMPORTANT]
>
>Voor direct-mailleveringen moet de indeling van het extractiebestand voldoen aan de volgende beperkingen:
>
>* De optie mag niet worden gebruikt **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* Als elementverzamelingen worden geëxtraheerd, hebben deze velden een lege waarde voor de zaadadressen, tenzij de velden **[!UICONTROL Single row (expert user)]** is geselecteerd. Raadpleeg [deze sectie](../../platform/using/executing-export-jobs.md#step-7---data-formatting) voor meer informatie.
>
