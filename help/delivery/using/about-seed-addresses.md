---
product: campaign
title: Seedadressen
description: Seedadressen
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: 1113afb573bad958ec7cc2cf008f71c8e751e8f9
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 9%

---

# Seedadressen{#about-seed-addresses}

![](../../assets/common.svg)

Seed-adressen worden gebruikt om ontvangers die niet aan de gedefinieerde doelcriteria voldoen, doelgericht te benaderen. Op deze manier kunnen ontvangers die buiten het bereik van de levering vallen, de levering ontvangen, net als elke andere doelontvanger.

Één van de belangrijkste reden om hen te gebruiken is **uw het posten lijstbescherming**. Door zaadadressen in te voegen in uw mailinglijst kunt u zien of het door een derde wordt gebruikt, aangezien de zaadadressen het bevat de leveringen ontvangen die naar uw mailinglijst worden verzonden.

Bovendien laten de zaadadressen u **voorproef en test de leveringenverpersoonlijking en het teruggeven** alvorens hun verzenden, door hen proefdrukken te verzenden (zie [De zaadadressen van het Gebruik als proef](steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](steps-defining-the-target-population.md#seeds-and-proofs-video)

De zaadadreseigenschap heeft de volgende voordelen:

* Willekeurige vervanging van velden door gegevens uit ontvangende profielen: hiermee kunt u alleen het e-mailadres invoeren, bijvoorbeeld in de sectie zaadadres, en de overige velden automatisch laten invullen door Campagne (zie [Hoofdlettergebruik: de veldvervanging configureren (](use-case--configuring-the-field-substitution.md)).
* Wanneer u een workflow met functies voor gegevensbeheer gebruikt, kunnen de aanvullende gegevens die in leveringen worden verwerkt, op zaadadresniveau worden ingevoerd om waarden af te dwingen: dit negeert de vervanging van willekeurige waarden .
* Zaadadressen worden automatisch uitgesloten van rapporten over de volgende leveringsstatistieken: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

De zaadadressen worden toegevoegd aan het doel van leveringen door worden ingevoerd of door in de levering of de campagne direct worden gecreeerd.

>[!NOTE]
>
>De zaadadressen behoren niet tot de ontvangers lijst, zij worden gecreeerd in een afzonderlijke lijst. Als u de lijst van ontvangers met nieuwe gegevens uitbreidt, moet u de lijst van zaadadressen evenals met de zelfde gegevens uitbreiden. Anders, zullen zij uitgebreide gebieden niet in aanmerking worden genomen voor zaadadressen.
>
>Een voorbeeld van hoe te om de zaadadreslijst uit te breiden wordt voorgesteld in deze sectie: [Hoofdlettergebruik: zaadadressen op criteria](use-case--selecting-seed-addresses-on-criteria.md) selecteren.

Voor direct-mailleveringen worden de zaadadressen toegevoegd tijdens extractie en gemengd in het uitvoerdocument.

>[!IMPORTANT]
>
>Voor direct-mailleveringen moet de indeling van het extractiebestand voldoen aan de volgende beperkingen:
>
>* De optie **[!UICONTROL Handle groupings (GROUP BY+HAVING)]** mag niet worden gebruikt.
>* Als elementverzamelingen worden geëxtraheerd, hebben deze velden een lege waarde voor de zaadadressen, tenzij de optie **[!UICONTROL Single row (expert user)]** is geselecteerd. Raadpleeg [deze sectie](../../platform/using/executing-export-jobs.md#step-7---data-formatting) voor meer informatie.
>

