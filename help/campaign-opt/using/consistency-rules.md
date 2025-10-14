---
product: campaign
title: Consistentieregels
description: Leer hoe u met consistentieregels werkt in Adobe Campaign
role: User, Data Engineer
feature: Typology Rules, Campaigns
hide: true
hidefromtoc: true
exl-id: 757328fa-4698-4f85-a5fa-074b5152ec45
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 3%

---

# Consistentieregels{#consistency-rules}

## Consistentieregels {#about-consistency-rules}

Adobe Campaign garandeert consistente communicatie dankzij een set regels die zijn opgenomen in campagnetypologieën. Zij hebben tot doel de leveringen die aan de ontvangers worden verzonden, te controleren, zoals volume, aard, relevantie, enz.

**de regels van de Capaciteit**, bijvoorbeeld kunnen vermijden overladend het platform betrokken door de levering van berichten. Bijvoorbeeld, moeten de speciale aanbiedingen die een downloadverbinding bevatten niet aan teveel mensen tegelijkertijd worden verzonden, om verzadiging van de server te vermijden; de telefooncampagnes mogen niet de verwerkingscapaciteit van callcenters, enz. overschrijden. Voor meer op dit, verwijs naar [&#x200B; capaciteit van de Controle &#x200B;](#controlling-capacity).

## Besturingscapaciteit {#controlling-capacity}

Alvorens berichten te leveren, moet u ervoor zorgen uw organisatie de capaciteit heeft om de levering (fysieke infrastructuur) te verwerken, de reacties die de levering (binnenkomende berichten) kan produceren, en het aantal vraag die aan contactabonnees (de verwerkingscapaciteit van het vraagcentrum) moet worden gemaakt, bijvoorbeeld.

Hiervoor moet u **[!UICONTROL Capacity]** typologieregels maken.

In het volgende voorbeeld, creëren wij een typologieregel voor een campagne van de telefoonloyaliteit. Wij beperken het aantal berichten tot 20 per dag, d.w.z. de dagelijkse verwerkingscapaciteit van een callcenter. Zodra de regel op twee leveringen van toepassing was, kunnen wij consumptie door logboeken controleren.

Volg onderstaande stappen om een nieuwe capaciteitsregel te ontwerpen:

1. Klik onder het knooppunt **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** op **[!UICONTROL New]** .
1. Selecteer een **[!UICONTROL Capacity]** regeltype.

   ![](assets/campaign_opt_create_capacity_01.png)

1. Maak op het tabblad **[!UICONTROL Capacity]** de beschikbaarheidsregels: in ons voorbeeld zijn dit tijdsperioden waarin aanroepen kunnen worden uitgevoerd. Selecteer een periode van 24 uur en ga 150 in het aanvankelijke aantal in, wat betekent dat het vraagcentrum 150 vraag per dag kan behandelen.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >Beschikbaarheidsregels dienen alleen ter informatie. Als u berichten moet uitsluiten wanneer de capaciteitsgrens wordt bereikt, verwijs naar [&#x200B; deze sectie &#x200B;](#exclude-messages-when-capacity-limit-reached).

1. Koppel deze regel aan een typologie en verwijs de typologie in uw levering om deze capaciteitsregel toe te passen. Raadpleeg [deze sectie](applying-rules.md#applying-a-typology-to-a-delivery) voor meer informatie.
1. U kunt het verbruik controleren met de tabbladen **[!UICONTROL Consumptions]** en **[!UICONTROL Capacity]** .

   Wanneer een regel wordt gebruikt in een levering, bieden de kolommen **[!UICONTROL Consumed]** en **[!UICONTROL Remaining]** informatie over de lading, zoals hieronder wordt getoond:

   ![](assets/campaign_opt_create_capacity_03.png)

   Raadpleeg [deze sectie](#monitoring-consumption) voor meer informatie.

## De maximale belasting definiëren {#defining-the-maximum-load}

Om de maximumlading te bepalen, moet u beschikbaarheidslijnen bepalen. Om dit te doen, zijn twee opties beschikbaar: u kunt één of meerdere beschikbaarheidslijnen manueel tot stand brengen (verwijs naar [&#x200B; beschikbaarheidslijnen één voor één toevoegen &#x200B;](#adding-availability-lines-one-by-one)) of beschikbaarheidswaaiers creëren. De frequentie van deze tijdsperioden kan worden geautomatiseerd (verwijs naar [&#x200B; voegt een reeks beschikbaarheidslijnen &#x200B;](#add-a-set-of-availability-lines) toe).

### Beschikbaarheidsregels een voor een toevoegen {#adding-availability-lines-one-by-one}

Als u een beschikbaarheidsregel wilt maken, klikt u op de knop **[!UICONTROL Add]** en selecteert u **[!UICONTROL Add an availability line]** . Voer de beschikbaarheidsperiode en de beschikbare laadtijd in.

![](assets/campaign_opt_create_capacity_02.png)

Voeg zoveel regels toe als nodig zijn voor uw verwerkingscapaciteit.

### Een set beschikbaarheidsregels toevoegen {#add-a-set-of-availability-lines}

Als u beschikbaarheidsperioden voor een bepaalde tijd wilt definiëren, klikt u op de knop **[!UICONTROL Add]** en selecteert u de optie **[!UICONTROL Add a set of availability lines]** . Geef een tijdsduur voor elke tijdsperiode op en het aantal periodes dat u wilt maken.

Als u de frequentie waarmee pagina&#39;s worden gemaakt wilt automatiseren, klikt u op de knop **[!UICONTROL Change]** en definieert u de tijdsperiode die u wilt plannen.

![](assets/campaign_opt_create_capacity_07.png)

Bijvoorbeeld, bepalen wij een programma om beschikbaarheidsperioden voor alle het werkdagen aan een tarief van 10 vraag per uur tussen 9AM en 5PM tot stand te brengen. Hiervoor voert u de volgende stappen uit:

1. Selecteer het type frequentie en de dagen en uren waarin deze geldig is:

   ![](assets/campaign_opt_create_capacity_08.png)

1. Vermeld de geldigheidsdata:

   ![](assets/campaign_opt_create_capacity_09.png)

1. Controleer het schema voordat u het goedkeurt:

   ![](assets/campaign_opt_create_capacity_10.png)

De **[!UICONTROL Forecasting]** -workflow maakt automatisch alle overeenkomende regels.

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>We raden u aan beschikbaarheidsregels te maken via het importeren van bestanden. Op dit tabblad kunt u verbruikslijnen weergeven en controleren.

## Berichten uitsluiten wanneer capaciteitslimiet is bereikt {#exclude-messages-when-capacity-limit-reached}

Beschikbaarheidsregels dienen uitsluitend ter informatie. Als u overtollige berichten wilt uitsluiten, schakelt u de optie **[!UICONTROL Exclude from the target messages in excess of capacity]** in. Dit voorkomt dat de capaciteit wordt overschreden. Voor dezelfde populatie als in het vorige voorbeeld mogen het verbruik en de resterende capaciteit de initiële hoeveelheid niet overschrijden:

![](assets/campaign_opt_create_capacity_04.png)

Het maximumaantal berichten dat kan worden verwerkt wordt verdeeld gelijkmatig over de bepaalde beschikbaarheidswaaier. Dit is met name relevant voor callcenters, aangezien hun maximumaantal gesprekken per dag beperkt is. In het geval van e-mailleveringen kunt u met de optie **[!UICONTROL Do not limit instantaneous delivery capacity]** dit beschikbaarheidsbereik negeren en tegelijkertijd uw e-mails verzenden.

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>In het geval van een overbelasting worden de opgeslagen berichten geselecteerd volgens de formule die is gedefinieerd in de leveringseigenschappen.

![](assets/campaign_opt_create_capacity_06.png)

## Monitorverbruik {#monitoring-consumption}

Capaciteitsregels zijn standaard alleen ter indicatie. Selecteer de optie **[!UICONTROL Exclude messages in excess of capacity from the target]** om te voorkomen dat de gedefinieerde belasting wordt overschreden. In dit geval worden overtollige berichten automatisch uitgesloten van de leveringen die gebruikmaken van deze typologieregel.

Als u het verbruik wilt controleren, bekijkt u de waarden die worden weergegeven in de kolom **[!UICONTROL Consumed]** van het tabblad **[!UICONTROL Capacity]** in de typologieregel.

![](assets/campaign_opt_create_capacity_04.png)

Als u consumptielijnen wilt weergeven, klikt u op de tab **[!UICONTROL Consumptions]** in de regel.
