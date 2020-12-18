---
solution: Campaign Classic
product: campaign
title: Campagnetypologieën
description: Campagnetypologieën
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 13%

---


# Campagnetypologieën{#about-campaign-typologies}

De Optimalisering van de campagne is de module van Adobe Campaign die u de verzendende leveringen laat controleren, filtreren en controleren. Om conflicten tussen campagnes te vermijden kan Adobe Campaign diverse combinaties testen door specifieke beperkingsregels toe te passen. Dit garandeert dat de verzonden berichten voldoen aan de behoeften en verwachtingen van klanten en het communicatiebeleid van het bedrijf.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#typologies-video)

>[!NOTE]
>
>Afhankelijk van uw aanbieding kan de optimalisatie van de campagne worden opgenomen of een invoegtoepassing. Controleer hiervoor uw licentieovereenkomst.

## Typologieregels {#typology-rules}

Met Adobe Campaign kunt u vier typen typologische regels ontwerpen en toepassen:

* **Regels voor** filteren waarmee u een deel van het doel kunt uitsluiten op basis van criteria. Raadpleeg [Regels filteren](../../campaign/using/filtering-rules.md) voor meer informatie hierover.
* **** Drukvoorschriften die u in staat stellen vermoeidheid bij het in de handel brengen te beheersen. Voor meer op dit, verwijs naar [Drukregels](../../campaign/using/pressure-rules.md).
* **Met** capaciteitsregels kunt u de belasting beperken om optimale verwerkingsomstandigheden te garanderen. Raadpleeg [Capaciteit bepalen](../../campaign/using/consistency-rules.md#controlling-capacity) voor meer informatie hierover.
* **De regels van** de Controle die u de geldigheid van berichten laten controleren alvorens zij worden verzonden. Voor meer op dit, verwijs naar [Regels van de Controle](../../campaign/using/control-rules.md).

Zodra zij zijn gecreeerd, worden de typologieregels gegroepeerd in campagnetypologieën die in leveringen van verwijzingen worden voorzien. Zie [Typologieën toepassen](#applying-typologies).

## Typologieën {#typologies}

Een campagneretypologie kan verscheidene [typologieregels](#typology-rules) bevatten, maar een levering kan slechts één typologie van verwijzingen voorzien.

Met het tabblad **[!UICONTROL Rules]** kunt u de toe te passen typologische regels toevoegen, verwijderen of weergeven.

![](assets/campaign_opt_rules_tab.png)

## Typologieën {#applying-typologies} toepassen

De stappen voor het maken en toepassen van een typologie voor uw leveringen worden hieronder weergegeven:

1. Maak typologische regels.

   Typologische regels vindt u in het knooppunt **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**.

   De verschillende regels die beschikbaar zijn in Campagne worden beschreven in de volgende secties: [Regels voor verkoopdruk](../../campaign/using/pressure-rules.md), [capaciteitsregels](../../campaign/using/consistency-rules.md#controlling-capacity), [regelregels](../../campaign/using/control-rules.md) en [filterregels](../../campaign/using/filtering-rules.md).

1. Maak een typologie en verwijs naar de regels die u erin hebt gemaakt.

   Typologieën zijn toegankelijk via het knooppunt **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**.

1. Vorm uw levering om de typologie te gebruiken u creeerde. Raadpleeg [deze sectie](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery) voor meer informatie.
1. Test en controleer het gedrag door campagnesimulaties. Raadpleeg [deze sectie](../../campaign/using/campaign-simulations.md) voor meer informatie over campagnesimulaties.

Tijdens de voorbereiding van de levering worden ontvangers uitgesloten wanneer aan het criterium wordt voldaan. U kunt logboeken controleren om toezicht te houden op uitsluitingen. Voorbeelden van gebruiksgevallen voor druktypologische regels zijn beschikbaar op [deze pagina](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules).

## Tutorialvideo’s {#typologies-video}

### Hoe stelt u vermoeidheidsbeheer in met behulp van typologische regels

In deze video wordt uitgelegd hoe u vermoeidheidsbeheer in Adobe Campaign Classic kunt implementeren door gebruik te maken van typologische regels.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Hoe stelt u vermoeidheidsbeheer in met behulp van vooraf gedefinieerde filters

Het beheer van de vermoeidheid controleert frequentie en hoeveelheid overseinen om te vermijden overdrijving van ontvangers. Als u niet de module van de campagnoptimalisering in uw campagneinstantie hebt, kunt u een vooraf bepaald filter vormen dat de doelbevolking door het aantal ontvangen berichten zal filtreren
In deze video wordt uitgelegd hoe u vermoeidheidsbeheer in Adobe Campaign Classic kunt implementeren met behulp van filters.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

Er zijn [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl) extra Campaign Classic hoe kan ik-video&#39;s beschikbaar.

**Verwant onderwerp**

* [Pas automatische bedrijfsregels op leveringen op om het even welk kanaal toe](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [Campagnetypologieën](../../campaign/using/pressure-rules.md)

* [Vermoediging van het op de markt brengen met drukregels beheren](https://docs.adobe.com/content/help/en/campaign-classic/using/orchestrating-campaigns/campaign-optimization/pressure-rules.html)