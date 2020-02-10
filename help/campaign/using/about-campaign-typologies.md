---
title: Informatie over campagetypologieën
seo-title: Informatie over campagetypologieën
description: Informatie over campagetypologieën
seo-description: null
page-status-flag: never-activated
uuid: ec89fb14-7e2f-4e9f-b7ab-3c2caf93a697
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 72c5151c-ce1e-425a-9aee-beefe9f21a67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Informatie over campagetypologieën{#about-campaign-typologies}

De Optimalisering van de campagne is de module van de Campagne van Adobe die u de verzendende leveringen laat controleren, filtreren en controleren. Om conflicten tussen campagnes te vermijden, kan de Campagne van Adobe diverse combinaties testen door specifieke beperkingsregels toe te passen. Dit garandeert dat de verzonden berichten het best aan de behoeften en de verwachtingen van klanten voldoen, in overeenstemming met het beleid van het bedrijfs communicatie.

>[!NOTE]
>
>Afhankelijk van uw aanbieding kan de optimalisatie van de campagne worden opgenomen of een invoegtoepassing. Controleer uw licentieovereenkomst.

## Typologieregels {#typology-rules}

Met Adobe Campagne kunt u vier typen typologische regels ontwerpen en toepassen:

1. **Filterregels** waarmee u een deel van het doel kunt uitsluiten op basis van criteria. Raadpleeg voor meer informatie de [Filterregels](../../campaign/using/filtering-rules.md).
1. **Regels voor druk** waarmee u de vermoeidheid bij het in de handel brengen kunt regelen. Raadpleeg de [drukregels](../../campaign/using/pressure-rules.md)voor meer informatie.
1. **De regels van de capaciteit** die u ladingen laten beperken om optimale verwerkingsvoorwaarden te verzekeren. Raadpleeg [Beheerscapaciteit](../../campaign/using/consistency-rules.md#controlling-capacity)voor meer informatie hierover.
1. **Regels van de controle** die u de geldigheid van berichten laten controleren alvorens zij worden verzonden. Voor meer op dit, verwijs naar de regels [van de](../../campaign/using/control-rules.md)Controle.

Zodra zij zijn gecreeerd, worden de typologieregels gegroepeerd in campagnetypologieën die in leveringen van verwijzingen worden voorzien. Zie Typologieën [toepassen](#applying-typologies).

## Typologieën {#typologies}

Een campagneretypologie kan verschillende [typologische regels](#typology-rules)bevatten, maar een levering kan slechts naar één typologie verwijzen.

Op het **[!UICONTROL Rules]** tabblad kunt u de toe te passen typologische regels toevoegen, verwijderen of weergeven.

![](assets/campaign_opt_rules_tab.png)

## Typologieën toepassen {#applying-typologies}

De stappen voor het maken en toepassen van een typologie voor uw leveringen worden hieronder weergegeven:

1. Maak typologische regels.

   Typologieregels vindt u in het **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** knooppunt.

   De verschillende regels die beschikbaar zijn in Campagne worden beschreven in de volgende secties: [verkoopdrukregels](../../campaign/using/pressure-rules.md), [capaciteitsregels](../../campaign/using/consistency-rules.md#controlling-capacity), [controleregels](../../campaign/using/control-rules.md) en [filterregels](../../campaign/using/filtering-rules.md).

1. Maak een typologie en verwijs naar de regels die u erin hebt gemaakt.

   Typologieën zijn toegankelijk via het knooppunt **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** .

1. Vorm uw levering om de typologie te gebruiken u creeerde. Zie [deze sectie](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery)voor meer informatie.
1. Test en controleer het gedrag door campagnesimulaties. Raadpleeg [deze sectie](../../campaign/using/campaign-simulations.md)voor meer informatie over campagnesimulaties.

Tijdens de voorbereiding van de levering worden ontvangers uitgesloten wanneer aan het criterium wordt voldaan. U kunt logboeken controleren om uitsluitingen te controleren. In [deze pagina](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules)vindt u voorbeelden van situaties voor de druktypologische regels.

**Verwante onderwerpen**

* [Pas automatische bedrijfsregels op leveringen op om het even welk kanaal toe](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)