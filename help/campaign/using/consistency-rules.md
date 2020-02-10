---
title: Consistentieregels
seo-title: Consistentieregels
description: Consistentieregels
seo-description: null
page-status-flag: never-activated
uuid: 9b497460-ba42-4bc7-98e0-55c1b4be5e44
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 9bcb5dc1-8cb4-4781-a8cd-8d072ff28b1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Consistentieregels{#consistency-rules}

## Consistentieregels {#about-consistency-rules}

De Campagne van Adobe verzekert verenigbare mededelingen dankzij een reeks regels in campagnemypologieën. Zij hebben tot doel de leveringen die aan de ontvangers worden verzonden, te controleren, zoals volume, aard, relevantie, enz.

**Met capaciteitsregels** kunt u bijvoorbeeld voorkomen dat het platform waarop de levering van berichten betrekking heeft, wordt overbelast. Bijvoorbeeld, speciale aanbiedingen die een downloadverbinding bevatten mogen niet aan teveel mensen tegelijkertijd worden verzonden, om verzadiging van de server te vermijden; de telefooncampagnes mogen niet de verwerkingscapaciteit van callcenters, enz. overschrijden. Raadpleeg [Beheerscapaciteit](#controlling-capacity)voor meer informatie hierover.

## Beheerscapaciteit {#controlling-capacity}

Alvorens berichten te leveren, moet u ervoor zorgen uw organisatie de capaciteit heeft om de levering (fysieke infrastructuur) te verwerken, de reacties die de levering (binnenkomende berichten) kan produceren, en het aantal vraag die aan contactabonnees (de verwerkingscapaciteit van het vraagcentrum) moet worden gemaakt, bijvoorbeeld.

Hiervoor moet u **[!UICONTROL Capacity]** typologische regels maken.

In het volgende voorbeeld, creëren wij een typologieregel voor een campagne van de telefoonloyaliteit. Wij beperken het aantal berichten tot 20 per dag, d.w.z. de dagelijkse verwerkingscapaciteit van een callcenter. Zodra de regel op twee leveringen van toepassing was, kunnen wij consumptie door logboeken controleren.

Volg onderstaande stappen om een nieuwe capaciteitsregel te ontwerpen:

1. Klik onder het **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** knooppunt **[!UICONTROL New]**.
1. Selecteer een **[!UICONTROL Capacity]** regeltype.

   ![](assets/campaign_opt_create_capacity_01.png)

1. Maak op het **[!UICONTROL Capacity]** tabblad de beschikbaarheidsregels: in ons voorbeeld zijn dit tijdsperiodes waarin oproepen kunnen worden gedaan . Selecteer een periode van 24 uur en ga 150 in het aanvankelijke aantal in, wat betekent dat het vraagcentrum 150 vraag per dag kan behandelen.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >Beschikbaarheidsregels dienen alleen ter informatie. Als u berichten moet uitsluiten wanneer de capaciteitslimiet is bereikt, raadpleegt u [deze sectie](#exclude-messages-when-capacity-limit-reached).

1. Koppel deze regel aan een typologie en verwijs de typologie in uw levering om deze capaciteitsregel toe te passen. Zie [deze sectie](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery)voor meer informatie.
1. U kunt de consumptie controleren via de regel **[!UICONTROL Consumptions]** en de **[!UICONTROL Capacity]** tabbladen.

   Wanneer een regel in een levering wordt gebruikt, verstrekken de **[!UICONTROL Consumed]** en **[!UICONTROL Remaining]** kolommen informatie over de lading, zoals hieronder getoond:

   ![](assets/campaign_opt_create_capacity_03.png)

   Zie [deze sectie](#monitoring-consumption)voor meer informatie.

## De maximumbelasting definiëren {#defining-the-maximum-load}

Om de maximumlading te bepalen, moet u beschikbaarheidslijnen bepalen. Hiervoor zijn twee opties beschikbaar: u kunt manueel één of meerdere beschikbaarheidslijnen tot stand brengen (verwijs naar het [Toevoegen van beschikbaarheidslijnen één voor één](#adding-availability-lines-one-by-one)) of beschikbaarheidswaaiers tot stand brengen. De frequentie van deze tijdsperiodes kan worden geautomatiseerd (zie een reeks beschikbaarheidslijnen [](#add-a-set-of-availability-lines)toevoegen).

### Beschikbaarheidsregels een voor een toevoegen {#adding-availability-lines-one-by-one}

Als u een beschikbaarheidsregel wilt maken, klikt u op de **[!UICONTROL Add]** knop en selecteert u **[!UICONTROL Add an availability line]**. Voer de beschikbaarheidsperiode en de beschikbare laadtijd in.

![](assets/campaign_opt_create_capacity_02.png)

Voeg zoveel regels toe als nodig zijn voor uw verwerkingscapaciteit.

### Een set beschikbaarheidsregels toevoegen {#add-a-set-of-availability-lines}

Als u beschikbaarheidsperioden voor een bepaalde tijd wilt definiëren, klikt u op de **[!UICONTROL Add]** knop en selecteert u de **[!UICONTROL Add a set of availability lines]** optie. Geef een duur voor elke tijdsperiode op en het aantal periodes dat u wilt maken.

Als u de frequentie waarmee pagina&#39;s worden gemaakt wilt automatiseren, klikt u op de **[!UICONTROL Change]** knop en definieert u de tijdsperiode die u wilt plannen.

![](assets/campaign_opt_create_capacity_07.png)

Bijvoorbeeld, bepalen wij een programma om beschikbaarheidsperioden voor alle het werkdagen aan een tarief van 10 vraag per uur tussen 9AM en 5PM tot stand te brengen. Hiervoor voert u de volgende stappen uit:

1. Selecteer het type frequentie en de dagen en uren waarin deze geldig is:

   ![](assets/campaign_opt_create_capacity_08.png)

1. Vermeld de geldigheidsdata:

   ![](assets/campaign_opt_create_capacity_09.png)

1. Controleer het schema voordat u het goedkeurt:

   ![](assets/campaign_opt_create_capacity_10.png)

Alle overeenkomende regels worden automatisch door de **[!UICONTROL Forecasting]** workflow gemaakt.

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>We raden u aan beschikbaarheidsregels te maken via het importeren van bestanden. Op dit tabblad kunt u verbruikslijnen weergeven en controleren.

## Berichten uitsluiten wanneer capaciteitslimiet is bereikt {#exclude-messages-when-capacity-limit-reached}

Beschikbaarheidsregels dienen uitsluitend ter informatie. Als u overtollige berichten wilt uitsluiten, schakelt u de **[!UICONTROL Exclude from the target messages in excess of capacity]** optie in. Dit voorkomt dat de capaciteit wordt overschreden. Voor dezelfde populatie als in het vorige voorbeeld mogen het verbruik en de resterende capaciteit de initiële hoeveelheid niet overschrijden:

![](assets/campaign_opt_create_capacity_04.png)

Het aantal berichten dat moet worden verwerkt, wordt gelijkmatig verdeeld over het gedefinieerde beschikbaarheidsbereik. Dit is met name relevant voor callcenters, aangezien hun maximumaantal gesprekken per dag beperkt is. In het geval van e-mailleveringen kunt u dit beschikbaarheidsbereik negeren en tegelijkertijd uw e-mails verzenden. **[!UICONTROL Do not limit instantaneous delivery capacity]**

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>In het geval van een overbelasting worden de opgeslagen berichten geselecteerd volgens de formule die is gedefinieerd in de leveringseigenschappen.

![](assets/campaign_opt_create_capacity_06.png)

## Toezicht op het verbruik {#monitoring-consumption}

Capaciteitsregels zijn standaard alleen ter indicatie. Selecteer de **[!UICONTROL Exclude messages in excess of capacity from the target]** optie om te voorkomen dat de gedefinieerde belasting wordt overschreden. In dit geval worden overtollige berichten automatisch uitgesloten van de leveringen die gebruikmaken van deze typologieregel.

Als u het verbruik wilt controleren, bekijkt u de waarden die worden weergegeven in de **[!UICONTROL Consumed]** kolom van het **[!UICONTROL Capacity]** tabblad in de typologieregel.

![](assets/campaign_opt_create_capacity_04.png)

Klik op de **[!UICONTROL Consumptions]** tab in de regel om de consumptielijnen weer te geven.
