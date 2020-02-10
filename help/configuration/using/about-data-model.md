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
source-git-commit: 2ce2a1a55e244180a4e62d6f3b5a5ed5bb8aff6e

---


# Informatie over het klassieke gegevensmodel van de campagne{#about-data-model}

In deze sectie worden de grondbeginselen van het klassieke gegevensmodel van de Campagne beschreven, voor een beter begrip van ingebouwde lijsten van de Campagne en hun interactie.

Het conceptuele gegevensmodel van de Adobe Campagne-database bestaat uit een set ingebouwde tabellen en hun interactie.

Om tot de beschrijving van elke lijst toegang te hebben, ga naar **[!UICONTROL Admin > Configuration > Data schemas]**, selecteer een middel van de lijst en klik de **[!UICONTROL Documentation]** tabel.

![](assets/data-model_documentation-tab.png)

Raadpleeg dit [document](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html)voor meer informatie over de standaardbeschrijving van het klassieke gegevensmodel van de campagne.

De fysieke en logische structuur van de gegevens die in de toepassing worden overgedragen, wordt in XML beschreven. Het voert een grammatica specifiek voor de Campagne van Adobe uit, genoemd een schema. Lees deze [sectie](../../configuration/using/about-schema-reference.md)voor meer informatie over Adobe Campagne-schema&#39;s.

## Overzicht {#data-model-overview}

Adobe Campaign is gebaseerd op een relationele database die tabellen bevat die aan elkaar zijn gekoppeld.

De basisstructuur van het gegevensmodel van de Campagne van Adobe kan als volgt worden beschreven.

## Ontvangertabel {#recipient-table}

Het gegevensmodel baseert zich op een hoofdlijst die door gebrek de Ontvangende lijst (**NmsRecipient**) is. In deze tabel kunt u alle marketingprofielen opslaan.

Zie deze [sectie](../../configuration/using/default-recipient-table.md)voor meer informatie over de tabel Ontvanger.

## Afleveringstabel {#delivery-table}

Het gegevensmodel bevat ook een deel dat is gewijd aan de opslag van alle marketingactiviteiten. Meestal is dit de leveringstabel (**NmsDelivery**). Elke record in deze tabel vertegenwoordigt een leveringsactie of een leveringssjabloon. Het bevat alle parameters die nodig zijn voor het uitvoeren van leveringen, zoals doel, inhoud, enz.

## Logtabellen {#log-tables}

Een ander deel van het gegevensmodel laat toe om alle logboeken tijdelijk op te slaan verbonden aan de uitvoering van de campagnes.

De logboeken van de levering zijn alle berichten die naar ontvangers of apparaten over alle kanalen worden verzonden. De hoofdtabel met leveringslogboeken (**NmsBroadLog**) bevat de leveringslogboeken voor alle ontvangers.
In de hoofdtabel Logbestanden voor bijhouden (**NmsTrackingLog**) worden de logbestanden voor bijhouden opgeslagen voor alle ontvangers. De trackinglogboeken verwijzen naar reacties van ontvangers, zoals het openen van e-mail en klikken. Elke reactie komt overeen met een trackinglog.
Logbestanden voor aflevering en tracering worden na een bepaalde periode verwijderd. Deze periode is opgegeven in Adobe Campagne en kan worden gewijzigd. Daarom wordt het ten zeerste aanbevolen de stammen regelmatig uit te voeren.

## Technische tabellen {#technical-tables}

Tot slot bestaat een deel van het gegevensmodel uit technische gegevens die voor het toepassingsproces worden gebruikt, met inbegrip van exploitanten en gebruikersrechten (**NmsGroup**), omslagen (**XtkFolder**).