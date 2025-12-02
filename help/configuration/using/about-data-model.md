---
product: campaign
title: Aan de slag met het Campaign Classic-gegevensmodel
description: Leer hoe u het Campaign-datamodel kunt uitbreiden, schema's kunt bewerken, API's kunt gebruiken en meer
feature: Data Model, Configuration
role: Developer
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 5%

---

# Aan de slag met het gegevensmodel van de campagne{#about-data-model}

Het conceptuele datamodel van de Adobe Campaign-database bestaat uit een reeks ingebouwde tabellen en hun interactie. De belangrijkste lijsten en de concepten worden vermeld in deze pagina.

## Overzicht {#data-model-overview}

Adobe Campaign vertrouwt op een relationele database die tabellen bevat die aan elkaar zijn gekoppeld. De basisstructuur van het Adobe Campaign-gegevensmodel kan als volgt worden beschreven.

### Ontvangertabel {#recipient-table}

Het gegevensmodel baseert zich op een belangrijkste lijst die door gebrek de Ontvankelijke lijst (**NmsRecipient**) is. In deze tabel kunt u alle marketingprofielen opslaan.

Voor meer op de Ontvankelijke lijst, zie [&#x200B; deze sectie &#x200B;](#default-recipient-table).

### Afleveringstabel {#delivery-table}

Het gegevensmodel bevat ook een deel dat is gewijd aan de opslag van alle marketingactiviteiten. Gewoonlijk is het de lijst van de Levering (**NmsDelivery**). Elke record in deze tabel vertegenwoordigt een leveringsactie of een leveringssjabloon. Het bevat alle parameters die nodig zijn voor het uitvoeren van leveringen, zoals doel, inhoud, enz.

### Logtabellen {#log-tables}

Een ander deel van het gegevensmodel laat toe om alle logboeken tijdelijk op te slaan verbonden aan de uitvoering van de campagnes.

De logboeken van de levering zijn alle berichten die naar ontvangers of apparaten over alle kanalen worden verzonden. De belangrijkste lijst van Logboeken van de Levering (**NmsBroadLog**) bevat de leveringslogboeken voor alle ontvangers.
De belangrijkste het Volgen logboeklijst (**NmsTrackingLog**) slaat het volgen logboeken voor alle ontvangers op. De trackinglogboeken verwijzen naar reacties van ontvangers, zoals het openen van e-mail en klikken. Elke reactie komt overeen met een trackinglog.
Logbestanden voor aflevering en tracering worden na een bepaalde periode verwijderd, die in Adobe Campaign is opgegeven en kan worden gewijzigd. Daarom wordt het ten zeerste aanbevolen de stammen regelmatig uit te voeren.

### Technische tabellen {#technical-tables}

Tot slot bestaat een deel van het gegevensmodel in technische gegevens die voor het toepassingsproces worden gebruikt, met inbegrip van exploitanten en gebruikersrechten (**NmsGroup**), omslagen (**XtkFolder**).

## De ingebouwde tabel Ontvanger gebruiken {#default-recipient-table}

De ingebouwde Ontvanger lijst in Adobe Campaign verstrekt een goed uitgangspunt voor de bouw van uw gegevensmodel. Het heeft een aantal vooraf bepaalde gebieden en lijstverbindingen die gemakkelijk kunnen worden uitgebreid. Dit is met name nuttig wanneer u zich vooral richt op ontvangers, omdat het een eenvoudig ontvanger-centric gegevensmodel past.

De voordelen van de ingebouwde tabel Ontvanger zijn als volgt:

* Ingebouwd werken met functies zoals abonnementen, zaadlijsten, en meer.
* Het verstrekken van een marketing gegevensbestand van een ontvanger-centric gegevensmodel.
* Snellere implementatie
* Gemakkelijk onderhoud door steun en partners.

Het is echter mogelijk de tabel Ontvanger uit te breiden, maar niet het aantal velden of koppelingen in de tabel te verminderen.

>[!IMPORTANT]
>
>Het wordt aanbevolen geen velden te verwijderen (zelfs niet als deze onbruikbaar zijn) in de tabel voor ontvangers, omdat dit tot fouten in de ingebouwde modules kan leiden.

Aangezien de tabel Ontvanger deel uitmaakt van het product, veranderen zowel de tabel als het bijbehorende formulier naarmate het product verandert. Daarom is extra onderhoud nodig om te controleren dat om het even welke uitbreidingen nog geldig bij verbetering zijn.

## Het gegevensmodel uitbreiden {#extending-data-model}

Wanneer u begint met Adobe Campaign, moet u het standaardgegevensmodel beoordelen om te controleren welke tabel het meest geschikt is om uw marketinggegevens op te slaan.

Als relevant, kunt u de standaard Ontvanger lijst met de uit-van-de-doos gebieden gebruiken, zoals die in [&#x200B; wordt beschreven deze sectie &#x200B;](#default-recipient-table).

Indien nodig, kunt u het uitbreiden met twee mechanismen:

* Een bestaande tabel uitbreiden met nieuwe velden. U kunt bijvoorbeeld een nieuw veld Loyalty toevoegen aan de tabel Ontvanger.
* Maak een nieuwe tabel, bijvoorbeeld een tabel met de naam Aanschaffen, waarin alle aankopen worden vermeld die door elk profiel van de database zijn gedaan, en koppel deze aan de tabel Ontvanger.

Voor meer bij het vormen van uitbreidingsschema&#39;s om het conceptuele gegevensmodel uit te breiden, zie [&#x200B; Ongeveer schemageditie &#x200B;](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Het uitbreiden van het gegevensmodel is gereserveerd voor geavanceerde gebruikers.

## Een aangepaste tabel voor ontvangers gebruiken {#custom-recipient-table}

Wanneer het ontwerpen van uw de gegevensmodel van Adobe Campaign, kunt u de [&#x200B; ingebouwde ontvankelijke lijst &#x200B;](#default-recipient-table) gebruiken, of besluiten om a [&#x200B; douane ontvankelijke lijst &#x200B;](../../configuration/using/about-custom-recipient-table.md) te creëren lijst om u marketing profielen op te slaan.

Als uw gegevensmodel niet in de op de ontvanger gerichte structuur past, kunt u andere tabellen instellen als de doeldimensie in Adobe Campaign. Dit kan bijvoorbeeld van belang zijn wanneer u huishoudens, rekeningen (zoals mobiele telefoons) en bedrijven/sites moet aanspreken in plaats van alleen ontvangers.

>[!NOTE]
>
>In dit geval, zult u een nieuwe [&#x200B; doelafbeelding &#x200B;](../../configuration/using/target-mapping.md) moeten creëren.

Alle principes en stappen nodig wanneer het gebruiken van een douane ontvankelijke lijst zijn gedetailleerd in [&#x200B; deze sectie &#x200B;](../../configuration/using/about-custom-recipient-table.md).

De voordelen van een aangepaste tabel voor ontvangers zijn als volgt:

* **Flexibel gegevensmodel** - de ingebouwde ontvankelijke lijst is nutteloos als u de meeste Ontvankelijke lijstgebieden niet nodig hebt, of als het gegevensmodel niet ontvankelijk-centric is.

* **Schaalbaarheid** - de grote volumes vereisen een gestroomlijnde lijst met weinig gebieden voor een efficiënt ontwerp. De ingebouwde ontvankelijke lijst zou teveel nutteloze gebieden hebben, die prestaties en gebrek aan efficiency zouden kunnen beïnvloeden.

* **plaats van Gegevens** - als de gegevens op een extern bestaand marketing gegevensbestand verblijven, kan het teveel inspanning vereisen om de ingebouwde ontvankelijke lijst te gebruiken. Het is eenvoudiger om een nieuwe te maken op basis van een bestaande structuur.

* **Gemakkelijke migratie** - Geen onderhoud is nodig om te controleren dat alle uitbreidingen nog op verbetering geldig zijn.

>[!IMPORTANT]
>
>Het gebruiken van een douane ontvankelijke lijst is gereserveerd voor gevorderde gebruikers en is onderworpen aan sommige beperkingen. Zie [deze sectie](../../configuration/using/about-custom-recipient-table.md)voor meer informatie.

## Verwante onderwerpen

Meer informatie over het gegevensmodel van campagne vindt u in de volgende secties:

* **Beschrijving van de belangrijkste lijsten** - voor meer op de standaardbeschrijving van het gegevensmodel van Campaign Classic, verwijs naar [&#x200B; deze sectie &#x200B;](../../configuration/using/data-model-description.md).

* **Volledige beschrijving van elke lijst** - om tot de volledige beschrijving van elke lijst toegang te hebben, ga **[!UICONTROL Admin > Configuration > Data schemas]**, selecteer een middel van de lijst en klik **[!UICONTROL Documentation]** tabel.

  ![](assets/data-model_documentation-tab.png)


* **schema&#39;s van de Campagne** - de fysieke en logische structuur van de gegevens die in de toepassing worden gedragen wordt beschreven in XML. Het volgt een grammatica die specifiek is voor Adobe Campaign en een schema wordt genoemd. Voor meer op de schema&#39;s van Adobe Campaign, lees uit [&#x200B; deze sectie &#x200B;](../../configuration/using/about-schema-reference.md).

* **modelbeste praktijken van Gegevens** - leer de architectuur van het het gegevensmodel van de Campagne en verwante beste praktijken, in [&#x200B; deze sectie &#x200B;](../../configuration/using/data-model-best-practices.md#data-model-architecture).
