---
title: Informatie over het klassieke gegevensmodel van Adobe Campagne
description: In dit document worden de grondbeginselen van het gegevensmodel van Adobe Campaign Classic beschreven.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 580be39d09bd59770d490945c3ba2b29e12fb3c4
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 0%

---


# Informatie over het gegevensmodel van de campagne{#about-data-model}

In deze sectie worden de grondbeginselen van het klassieke gegevensmodel van de Campagne beschreven, voor een beter begrip van ingebouwde lijsten van de Campagne en hun interactie.

Het conceptuele gegevensmodel van de Adobe Campagne-database bestaat uit een set ingebouwde tabellen en hun interactie.

Om tot de beschrijving van elke lijst toegang te hebben, ga naar **[!UICONTROL Admin > Configuration > Data schemas]**, selecteer een middel van de lijst en klik de **[!UICONTROL Documentation]** tabel.

![](assets/data-model_documentation-tab.png)

Raadpleeg [deze sectie](../../configuration/using/data-model-description.md)voor meer informatie over de standaardbeschrijving van het klassieke gegevensmodel van de campagne.

De fysieke en logische structuur van de gegevens die in de toepassing worden overgedragen, wordt in XML beschreven. Het voert een grammatica specifiek voor de Campagne van Adobe uit, genoemd een schema. Lees [deze sectie](../../configuration/using/about-schema-reference.md)voor meer informatie over Adobe Campagne-schema&#39;s.

## Overzicht {#data-model-overview}

Adobe Campaign is gebaseerd op een relationele database die tabellen bevat die aan elkaar zijn gekoppeld. De basisstructuur van het gegevensmodel van de Campagne van Adobe kan als volgt worden beschreven.

>[!NOTE]
>
>Raadpleeg [deze sectie](../../configuration/using/data-model-best-practices.md#data-model-architecture)voor meer informatie over de architectuur van het gegevensmodel van de campagne en de bijbehorende best practices.

### Ontvangertabel {#recipient-table}

Het gegevensmodel baseert zich op een hoofdlijst die door gebrek de Ontvangende lijst (**NmsRecipient**) is. In deze tabel kunt u alle marketingprofielen opslaan.

Zie [deze sectie](#default-recipient-table)voor meer informatie over de tabel Ontvanger.

### Afleveringstabel {#delivery-table}

Het gegevensmodel bevat ook een deel dat is gewijd aan de opslag van alle marketingactiviteiten. Meestal is dit de leveringstabel (**NmsDelivery**). Elke record in deze tabel vertegenwoordigt een leveringsactie of een leveringssjabloon. Het bevat alle parameters die nodig zijn voor het uitvoeren van leveringen, zoals doel, inhoud, enz.

### Logtabellen {#log-tables}

Een ander deel van het gegevensmodel laat toe om alle logboeken tijdelijk op te slaan verbonden aan de uitvoering van de campagnes.

De logboeken van de levering zijn alle berichten die naar ontvangers of apparaten over alle kanalen worden verzonden. De hoofdtabel met leveringslogbestanden (**NmsBroadLog**) bevat de leveringslogboeken voor alle ontvangers.
In de hoofdtabel Logbestanden voor bijhouden (**NmsTrackingLog**) worden de logbestanden voor bijhouden opgeslagen voor alle ontvangers. De trackinglogboeken verwijzen naar reacties van ontvangers, zoals het openen van e-mail en klikken. Elke reactie komt overeen met een trackinglog.
Logbestanden voor aflevering en tracering worden na een bepaalde periode verwijderd. Deze periode is opgegeven in Adobe Campagne en kan worden gewijzigd. Daarom wordt het ten zeerste aanbevolen de stammen regelmatig uit te voeren.

### Technische tabellen {#technical-tables}

Tot slot bestaat een deel van het gegevensmodel uit technische gegevens die voor het toepassingsproces worden gebruikt, met inbegrip van exploitanten en gebruikersrechten (**NmsGroup**), omslagen (**XtkFolder**).

## De standaardtabel Ontvanger gebruiken {#default-recipient-table}

De out-of-the-box Ontvangerlijst in de Campagne van Adobe verstrekt een goed uitgangspunt voor de bouw van uw gegevensmodel. Het heeft een aantal vooraf bepaalde gebieden en lijstverbindingen die gemakkelijk kunnen worden uitgebreid. Dit is met name nuttig wanneer u zich vooral richt op ontvangers, omdat het een eenvoudig ontvanger-centric gegevensmodel past.

De standaardtabel met ontvangers biedt de volgende voordelen:

* Uitgebreide functionaliteit met functies zoals abonnementen, zaadlijsten, enquêtes, sociale functies enzovoort.
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

Indien relevant, kunt u de standaard Ontvanger lijst met de uit-van-de-doos gebieden gebruiken, zoals die in [deze sectie](#default-recipient-table)wordt beschreven.

Indien nodig kunt u het uitbreiden met twee mechanismen:

* Een bestaande tabel uitbreiden met nieuwe velden. U kunt bijvoorbeeld een nieuw veld Loyalty toevoegen aan de tabel Ontvanger.
* Maak een nieuwe tabel, bijvoorbeeld een tabel met de naam Aanschaffen, waarin alle aankopen worden vermeld die door elk profiel van de database zijn gedaan, en koppel deze aan de tabel Ontvanger.

Voor meer bij het vormen van uitbreidingsschema&#39;s om het conceptuele gegevensmodel uit te breiden, zie [Ongeveer schemageditie](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Het uitbreiden van het gegevensmodel is gereserveerd voor geavanceerde gebruikers.

## Een aangepaste tabel voor ontvangers gebruiken {#custom-recipient-table}

Bij het ontwerpen van uw Adobe Campagne-gegevensmodel kunt u de [out-of-the-box Ontvanger tabel](#default-recipient-table)gebruiken of besluiten om een niet-standaard ontvangende tabel te maken waarin u marketingprofielen kunt opslaan.

Als uw gegevensmodel niet in de op de ontvanger gerichte structuur past, kunt u in Adobe Campagne andere tabellen instellen als de doeldimensie. Dit kan bijvoorbeeld van belang zijn wanneer u huishoudens, rekeningen (zoals mobiele telefoons) en bedrijven/sites moet aanspreken in plaats van alleen ontvangers.

>[!NOTE]
>
>In dit geval moet u een nieuwe [doeltoewijzing](../../configuration/using/target-mapping.md)maken.

Alle principes en stappen nodig wanneer het gebruiken van een lijst van de douaneontvanger zijn gedetailleerd in [deze sectie](../../configuration/using/about-custom-recipient-table.md).

De voordelen van een aangepaste tabel voor ontvangers zijn als volgt:

### Flexibel gegevensmodel {#flexible-data-model}

De tabel Ontvanger uit de doos is niet bruikbaar als u de meeste tabelvelden Ontvanger niet nodig hebt of als het gegevensmodel niet op de ontvanger is gericht.

### Schaalbaarheid {#scalability}

Grote volumes vereisen een gestroomlijnde tabel met weinig velden voor een efficiënt ontwerp. De out-of-the-box ontvangertabel zou te veel nutteloze velden hebben, wat van invloed kan zijn op de prestaties en een gebrek aan efficiëntie.

### Gegevenslocatie {#data-location}

Als de gegevens op een extern bestaand marketing gegevensbestand verblijven, kan het teveel inspanning vereisen om de uit-van-de-doos Lijst van de Ontvanger te gebruiken. Het maken van een nieuwe op basis van een bestaande structuur is eenvoudiger.

### Eenvoudige migratie {#easy-migration}

Er is geen onderhoud nodig om te controleren of alle extensies nog geldig zijn na de upgrade.

>[!IMPORTANT]
>
>Het gebruiken van een douane ontvankelijke lijst is gereserveerd voor gevorderde gebruikers en is onderworpen aan sommige beperkingen. Zie [deze sectie](../../configuration/using/about-custom-recipient-table.md)voor meer informatie.
