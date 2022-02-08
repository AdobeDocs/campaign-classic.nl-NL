---
product: campaign
title: Aan de slag met het gegevensmodel Campaign Classic
description: Leer hoe u het gegevensmodel van de campagne kunt uitbreiden, schema's kunt bewerken, API's kunt gebruiken en meer
feature: Data Model
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 4%

---

# Aan de slag met het gegevensmodel van de campagne{#about-data-model}

![](../../assets/v7-only.svg)

Het conceptuele datamodel van de Adobe Campaign-database bestaat uit een reeks ingebouwde tabellen en hun interactie. De belangrijkste lijsten en de concepten worden vermeld in deze pagina.

## Overzicht {#data-model-overview}

Adobe Campaign vertrouwt op een relationele database die tabellen bevat die aan elkaar zijn gekoppeld. De basisstructuur van het Adobe Campaign-gegevensmodel kan als volgt worden beschreven.

### Ontvangertabel {#recipient-table}

Het gegevensmodel is gebaseerd op een hoofdtabel die standaard de tabel Ontvanger is (**NmsRecipient**). In deze tabel kunt u alle marketingprofielen opslaan.

Voor meer informatie over de tabel Ontvanger raadpleegt u [deze sectie](#default-recipient-table).

### Afleveringstabel {#delivery-table}

Het gegevensmodel bevat ook een deel dat is gewijd aan de opslag van alle marketingactiviteiten. Doorgaans is dit de afleveringstabel (**NmsDelivery**). Elke record in deze tabel vertegenwoordigt een leveringsactie of een leveringssjabloon. Het bevat alle parameters die nodig zijn voor het uitvoeren van leveringen, zoals doel, inhoud, enz.

### Logtabellen {#log-tables}

Een ander deel van het gegevensmodel laat toe om alle logboeken tijdelijk op te slaan verbonden aan de uitvoering van de campagnes.

De logboeken van de levering zijn alle berichten die naar ontvangers of apparaten over alle kanalen worden verzonden. De belangrijkste leveringstabel (**NmsBroadLog**) bevat de leveringslogboeken voor alle ontvangers.
De hoofdtabel met trackinglogbestanden (**NmsTrackingLog**) slaat de volgende logboeken voor alle ontvangers op. De trackinglogboeken verwijzen naar reacties van ontvangers, zoals het openen van e-mail en klikken. Elke reactie komt overeen met een trackinglog.
Logbestanden voor aflevering en tracering worden na een bepaalde periode verwijderd, die in Adobe Campaign is opgegeven en kan worden gewijzigd. Daarom wordt het ten zeerste aanbevolen de stammen regelmatig uit te voeren.

### Technische tabellen {#technical-tables}

Tot slot bestaat een deel van het gegevensmodel uit technische gegevens die voor het aanvraagproces worden gebruikt, met inbegrip van exploitanten en gebruikersrechten (**NmsGroup**), mappen (**XtkFolder**).

## De ingebouwde tabel Ontvanger gebruiken {#default-recipient-table}

De ingebouwde Ontvanger lijst in Adobe Campaign verstrekt een goed uitgangspunt voor de bouw van uw gegevensmodel. Het heeft een aantal vooraf bepaalde gebieden en lijstverbindingen die gemakkelijk kunnen worden uitgebreid. Dit is met name nuttig wanneer u zich vooral richt op ontvangers, omdat het een eenvoudig ontvanger-centric gegevensmodel past.

De voordelen van de ingebouwde tabel Ontvanger zijn als volgt:

* Ingebouwd werken met functies zoals abonnementen, zaadlijsten, en meer.
* Het verstrekken van een marketing gegevensbestand van een ontvanger-centric gegevensmodel.
* Snellere implementatie.
* Gemakkelijk onderhoud door steun en partners.

Het is echter mogelijk de tabel Ontvanger uit te breiden, maar niet het aantal velden of koppelingen in de tabel te verminderen.

>[!IMPORTANT]
>
>Het wordt aanbevolen geen velden te verwijderen (zelfs niet als deze onbruikbaar zijn) in de tabel voor ontvangers, omdat dit tot fouten in de ingebouwde modules kan leiden.

Aangezien de tabel Ontvanger deel uitmaakt van het product, veranderen zowel de tabel als het bijbehorende formulier naarmate het product verandert. Daarom is extra onderhoud nodig om te controleren dat om het even welke uitbreidingen nog geldig bij verbetering zijn.

## Het gegevensmodel uitbreiden {#extending-data-model}

Wanneer u begint met Adobe Campaign, moet u het standaardgegevensmodel beoordelen om te controleren welke tabel het meest geschikt is om uw marketinggegevens op te slaan.

Indien relevant, kunt u de standaard Ontvanger lijst met de uit-van-de-doos gebieden gebruiken, zoals die in wordt beschreven [deze sectie](#default-recipient-table).

Indien nodig kunt u het uitbreiden met twee mechanismen:

* Een bestaande tabel uitbreiden met nieuwe velden. U kunt bijvoorbeeld een nieuw veld Loyalty toevoegen aan de tabel Ontvanger.
* Maak een nieuwe tabel, bijvoorbeeld een tabel met de naam Aanschaffen, waarin alle aankopen worden vermeld die door elk profiel van de database zijn gedaan, en koppel deze aan de tabel Ontvanger.

Voor meer bij het vormen van uitbreidingsschema&#39;s om het conceptuele gegevensmodel uit te breiden, zie [Schema-editie](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Het uitbreiden van het gegevensmodel is gereserveerd voor geavanceerde gebruikers.

## Een aangepaste tabel voor ontvangers gebruiken {#custom-recipient-table}

Bij het ontwerpen van uw Adobe Campaign-gegevensmodel kunt u de opdracht [ingebouwde tabel voor ontvangers](#default-recipient-table)of besluit een [aangepaste tabel voor ontvangers](../../configuration/using/about-custom-recipient-table.md) tabel waarin u marketingprofielen worden opgeslagen.

Als uw gegevensmodel niet in de op de ontvanger gerichte structuur past, kunt u andere tabellen instellen als de doeldimensie in Adobe Campaign. Dit kan bijvoorbeeld van belang zijn wanneer u huishoudens, rekeningen (zoals mobiele telefoons) en bedrijven/sites moet aanspreken in plaats van alleen ontvangers.

>[!NOTE]
>
>In dit geval moet u een nieuwe [doeltoewijzing](../../configuration/using/target-mapping.md).

Alle principes en stappen die nodig zijn bij het gebruik van een aangepaste tabel voor ontvangers worden beschreven in [deze sectie](../../configuration/using/about-custom-recipient-table.md).

De voordelen van een aangepaste tabel voor ontvangers zijn als volgt:

* **Flexibel gegevensmodel** - De ingebouwde ontvankelijke lijst is nutteloos als u niet de meeste Ontvankelijke lijstgebieden nodig hebt, of als het gegevensmodel niet ontvanger-centric is.

* **Schaalbaarheid** - Grote volumes vereisen een gestroomlijnde tabel met weinig velden voor een efficiënt ontwerp. De ingebouwde ontvankelijke lijst zou teveel nutteloze gebieden hebben, die prestaties en gebrek aan efficiency zouden kunnen beïnvloeden.

* **Gegevenslocatie** - Als de gegevens op een externe bestaande marketing gegevensbestand verblijven, kan het teveel inspanning vereisen om de ingebouwde ontvankelijke lijst te gebruiken. Het maken van een nieuwe op basis van een bestaande structuur is eenvoudiger.

* **Eenvoudige migratie** - Er is geen onderhoud nodig om te controleren of alle extensies nog geldig zijn na de upgrade.

>[!IMPORTANT]
>
>Het gebruiken van een douane ontvankelijke lijst is gereserveerd voor gevorderde gebruikers en is onderworpen aan sommige beperkingen. Zie [deze sectie](../../configuration/using/about-custom-recipient-table.md)voor meer informatie.

## Verwante onderwerpen

Meer informatie over het gegevensmodel van campagne vindt u in de volgende secties:

* **Beschrijving van de belangrijkste tabellen** - Raadpleeg voor meer informatie over het standaard Campaign Classic gegevensmodel de beschrijving [deze sectie](../../configuration/using/data-model-description.md).

* **Volledige beschrijving van elke tabel** - Ga naar **[!UICONTROL Admin > Configuration > Data schemas]** selecteert u een bron in de lijst en klikt u op de knop **[!UICONTROL Documentation]** tab.

   ![](assets/data-model_documentation-tab.png)


* **Campagne-schema&#39;s** - De fysieke en logische structuur van de gegevens die in de toepassing worden overgedragen, wordt in XML beschreven. Het volgt een grammatica die specifiek is voor Adobe Campaign en een schema wordt genoemd. Lees voor meer informatie over Adobe Campaign-schema&#39;s [deze sectie](../../configuration/using/about-schema-reference.md).

* **Aanbevolen werkwijzen voor gegevensmodellen** - Leer de architectuur van het gegevensmodel van de Campagne en verwante beste praktijken, in [deze sectie](../../configuration/using/data-model-best-practices.md#data-model-architecture).
