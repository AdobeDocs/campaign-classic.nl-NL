---
product: campaign
title: Campagnetypologieën
description: Campagnetypologieën
role: User, Data Engineer
feature: Typology Rules, Campaigns
hide: true
hidefromtoc: true
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 12%

---

# Campagnetypologieën{#about-campaign-typologies}

De Optimalisering van de campagne is de module van Adobe Campaign die u de verzendende leveringen laat controleren, filtreren en controleren. Om conflicten tussen campagnes te vermijden kan Adobe Campaign diverse combinaties testen door specifieke beperkingsregels toe te passen. Dit garandeert dat de verzonden berichten voldoen aan de behoeften en verwachtingen van klanten en het communicatiebeleid van het bedrijf.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#typologies-video)

>[!NOTE]
>
>Afhankelijk van uw aanbieding kan de optimalisatie van de campagne worden opgenomen of een invoegtoepassing. Controleer hiervoor uw licentieovereenkomst.

## Typologische regels {#typology-rules}

Met Adobe Campaign kunt u vier typen typologische regels ontwerpen en toepassen:

* **het Filtreren** regels die u een deel van het doel laten uitsluiten dat op criteria wordt gebaseerd. Voor meer op dit, verwijs naar [ het Filtreren regels ](filtering-rules.md).
* **Druk** regels die u marketing moeheid laten controleren. Voor meer op dit, verwijs naar [ Regels van de Druk ](pressure-rules.md).
* **de regels van de Capaciteit** die u ladingen laten beperken om optimale verwerkingsvoorwaarden te waarborgen. Voor meer op dit, verwijs naar [ Controlerend capaciteit ](consistency-rules.md#controlling-capacity).
* **de regels van de Controle** die u de geldigheid van berichten laten controleren alvorens zij worden verzonden. Voor meer op dit, verwijs naar [ Regels van de Controle ](control-rules.md).

Zodra zij zijn gecreeerd, worden de typologieregels gegroepeerd in campagnetypologieën die in leveringen van verwijzingen worden voorzien. Zie [ Toepassend typologies ](#applying-typologies).

## Typologieën {#typologies}

Een campagnetypologie kan verscheidene [ typologische regels ](#typology-rules) bevatten, maar een levering kan slechts één typologie van verwijzingen voorzien.

Op het tabblad **[!UICONTROL Rules]** kunt u de toe te passen typologische regels toevoegen, verwijderen of bekijken.

![](assets/campaign_opt_rules_tab.png)

## Typologieën toepassen {#applying-typologies}

De stappen voor het maken en toepassen van een typologie voor uw leveringen worden hieronder weergegeven:

1. Maak typologische regels.

   Typologieregels vindt u in het knooppunt **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** .

   De verschillende regels beschikbaar in Campagne worden beschreven in de volgende secties: [ de regels van de verkoopdruk ](pressure-rules.md), [ capaciteitsregels ](consistency-rules.md#controlling-capacity), [ controleregels ](control-rules.md) en [ het filtreren regels ](filtering-rules.md).

1. Maak een typologie en verwijs naar de regels die u erin hebt gemaakt.

   Typologieën zijn toegankelijk via het knooppunt **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** .

1. Vorm uw levering om de typologie te gebruiken u creeerde. Raadpleeg [deze sectie](applying-rules.md#applying-a-typology-to-a-delivery) voor meer informatie.
1. Test en controleer het gedrag door campagnesimulaties. Voor meer op campagnesimulaties, verwijs naar [ deze sectie ](campaign-simulations.md).

Tijdens de voorbereiding van de levering worden ontvangers uitgesloten wanneer aan het criterium wordt voldaan. U kunt logboeken controleren om uitsluitingen te controleren. De gebruiksgevallen van de steekproef op druktypologische regels zijn beschikbaar in [ deze pagina ](pressure-rules.md#use-cases-on-pressure-rules).

## Zelfstudievideo&#39;s {#typologies-video}

### Hoe stelt u vermoeidheidsbeheer in met behulp van typologische regels

In deze video wordt uitgelegd hoe u vermoeidheidsbeheer in Adobe Campaign kunt implementeren door gebruik te maken van typologische regels.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Hoe stelt u vermoeidheidsbeheer in met behulp van vooraf gedefinieerde filters

Moeheidsbeheer bepaalt de frequentie en de hoeveelheid van de berichten om de ontvangers niet te overspoelen. Als u niet de module van de campagnoptimalisering in uw campagneinstantie hebt, kunt u een vooraf bepaald filter vormen dat de doelbevolking door het aantal ontvangen berichten zal filtreren
In deze video wordt uitgelegd hoe u vermoeidheidsbeheer in Adobe Campaign Classic kunt implementeren met behulp van filters.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

De extra campagne hoe-aan video&#39;s is beschikbaar [ hier ](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).

**Verwante onderwerp**

* [Aan de slag met typologieën en moeheidsbeheer](pressure-rules.md)

