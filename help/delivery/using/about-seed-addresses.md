---
solution: Campaign Classic
product: campaign
title: Seed-adressen
description: Seed-adressen
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 9237e11edec4114b2bd0932e6128775f36aad27c
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 9%

---


# Seed-adressen{#about-seed-addresses}

Seed-adressen worden gebruikt om ontvangers die niet aan de gedefinieerde doelcriteria voldoen, doelgericht te benaderen. Op deze manier kunnen ontvangers die buiten het bereik van de levering vallen, de levering ontvangen, net als elke andere doelontvanger.

Één van de belangrijkste reden om hen te gebruiken is **uw het posten lijstbescherming**. Door zaadadressen in te voegen in uw mailinglijst kunt u zien of het door een derde wordt gebruikt, aangezien de zaadadressen het bevat de leveringen ontvangen die naar uw postingslijst worden verzonden.

Bovendien laten de zaadadressen u **voorproef en test de leveringenverpersoonlijking en het teruggeven** alvorens hun het verzenden, door hen proefdrukken te verzenden (zie [Gebruik zaadadressen als proef](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof).

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](../../delivery/using/steps-defining-the-target-population.md#seeds-and-proofs-video)

De zaadadreseigenschap heeft de volgende voordelen:

* Willekeurige vervanging van velden door gegevens uit ontvangende profielen: hiermee kunt u alleen het e-mailadres invoeren, bijvoorbeeld in de sectie zaadadres, en de overige velden automatisch laten invullen door Campagne (zie [Hoofdlettergebruik: de veldvervanging configureren (](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* Wanneer u een workflow met functies voor gegevensbeheer gebruikt, kunnen de aanvullende gegevens die in leveringen worden verwerkt, op zaadadresniveau worden ingevoerd om waarden af te dwingen: dit negeert de vervanging van willekeurige waarden .
* Zaadadressen worden automatisch uitgesloten van rapporten over de volgende leveringsstatistieken: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

De zaadadressen worden toegevoegd aan het doel van leveringen door worden ingevoerd of door in de levering of de campagne direct worden gecreeerd.

>[!NOTE]
>
>De zaadadressen behoren niet tot de ontvangers lijst, zij worden gecreeerd in een afzonderlijke lijst. Als u de lijst van ontvangers met nieuwe gegevens uitbreidt, moet u de lijst van zaadadressen evenals met de zelfde gegevens uitbreiden. Anders, zullen zij uitgebreide gebieden niet in aanmerking worden genomen voor zaadadressen.
>
>Een voorbeeld van hoe te om de zaadadreslijst uit te breiden wordt voorgesteld in deze sectie: [Hoofdlettergebruik: zaadadressen selecteren op criteria](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

Voor direct-mailleveringen worden de zaadadressen toegevoegd tijdens extractie en gemengd in het uitvoerdocument.

>[!IMPORTANT]
>
>Voor direct-mailleveringen moet de indeling van het extractiebestand voldoen aan de volgende beperkingen:
>
>* De optie **[!UICONTROL Handle groupings (GROUP BY+HAVING)]** mag niet worden gebruikt.
>* Als elementverzamelingen worden geëxtraheerd, hebben deze velden een lege waarde voor de zaadadressen, tenzij de optie **[!UICONTROL Single row (expert user)]** is geselecteerd. Raadpleeg [deze sectie](../../platform/using/executing-export-jobs.md#step-7---data-formatting) voor meer informatie.

>


