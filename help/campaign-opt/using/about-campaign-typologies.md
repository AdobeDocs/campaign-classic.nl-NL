---
product: campaign
title: Campagnetypologieën
description: Campagnetypologieën
role: User, Data Engineer
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Typology Rules, Campaigns
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 14%

---

# Campagnetypologieën{#about-campaign-typologies}

De Optimalisering van de campagne is de module van Adobe Campaign die u de verzendende leveringen laat controleren, filtreren en controleren. Om conflicten tussen campagnes te vermijden kan Adobe Campaign diverse combinaties testen door specifieke beperkingsregels toe te passen. Dit garandeert dat de verzonden berichten voldoen aan de behoeften en verwachtingen van klanten en het communicatiebeleid van het bedrijf.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#typologies-video)

>[!NOTE]
>
>Afhankelijk van uw aanbieding kan de optimalisatie van de campagne worden opgenomen of een invoegtoepassing. Controleer hiervoor uw licentieovereenkomst.

## Typologische regels {#typology-rules}

Met Adobe Campaign kunt u vier typen typologische regels ontwerpen en toepassen:

* **Filteren** regels waarmee u een deel van het doel kunt uitsluiten op basis van criteria. Raadpleeg voor meer informatie hierover [Filterregels](filtering-rules.md).
* **Druk** regels die u in staat stellen om vermoeidheid bij het in de handel brengen te beheersen. Raadpleeg voor meer informatie hierover [Regels voor druk](pressure-rules.md).
* **Capaciteit** regels waarmee u de belasting kunt beperken om optimale verwerkingsomstandigheden te garanderen. Raadpleeg voor meer informatie hierover [Beheerscapaciteit](consistency-rules.md#controlling-capacity).
* **Besturing** regels waarmee u de geldigheid van berichten kunt controleren voordat deze worden verzonden. Raadpleeg voor meer informatie hierover [Controlevoorschriften](control-rules.md).

Zodra zij zijn gecreeerd, worden de typologieregels gegroepeerd in campagnetypologieën die in leveringen van verwijzingen worden voorzien. Zie [Typologieën toepassen](#applying-typologies).

## Typologieën {#typologies}

Een campagnemetypologie kan verschillende [typologieregels](#typology-rules), maar een levering kan slechts naar één typologie verwijzen.

De **[!UICONTROL Rules]** kunt u de toe te passen typologische regels toevoegen, verwijderen of bekijken.

![](assets/campaign_opt_rules_tab.png)

## Typologieën toepassen {#applying-typologies}

De stappen voor het maken en toepassen van een typologie voor uw leveringen worden hieronder weergegeven:

1. Maak typologische regels.

   De typologische regels zijn te vinden in de **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** knooppunt.

   De verschillende regels die beschikbaar zijn in Campagne worden beschreven in de volgende secties: [verkoopdrukregels](pressure-rules.md), [capaciteitsregels](consistency-rules.md#controlling-capacity), [controlevoorschriften](control-rules.md) en [filterregels](filtering-rules.md).

1. Maak een typologie en verwijs naar de regels die u erin hebt gemaakt.

   De typologieën zijn toegankelijk via **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** knooppunt.

1. Vorm uw levering om de typologie te gebruiken u creeerde. Raadpleeg [deze sectie](applying-rules.md#applying-a-typology-to-a-delivery) voor meer informatie.
1. Test en controleer het gedrag door campagnesimulaties. Raadpleeg voor meer informatie over campagnesimulaties [deze sectie](campaign-simulations.md).

Tijdens de voorbereiding van de levering worden ontvangers uitgesloten wanneer aan het criterium wordt voldaan. U kunt logboeken controleren om uitsluitingen te controleren. Er zijn gevallen van monstergebruik voor de druktypologische regels beschikbaar in: [deze pagina](pressure-rules.md#use-cases-on-pressure-rules).

## Zelfstudievideo&#39;s {#typologies-video}

### Hoe stelt u vermoeidheidsbeheer in met behulp van typologische regels

In deze video wordt uitgelegd hoe u vermoeidheidsbeheer in Adobe Campaign kunt implementeren door gebruik te maken van typologische regels.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Hoe stelt u vermoeidheidsbeheer in met behulp van vooraf gedefinieerde filters

Moeheidsbeheer bepaalt de frequentie en de hoeveelheid van de berichten om de ontvangers niet te overspoelen. Als u niet de module van de campagneroptimalisering in uw campagneinstantie hebt, kunt u een vooraf bepaald filter vormen dat de doelbevolking door het aantal ontvangen berichten zal filtreren Deze video verklaart hoe te om vermoeidheidsbeheer in Adobe Campaign Classic uit te voeren door filters te gebruiken.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

Er zijn aanvullende instructievideo&#39;s beschikbaar voor campagnes [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).

**Verwante onderwerpen**

* [Aan de slag met typologieën en moeheidsbeheer](pressure-rules.md)

