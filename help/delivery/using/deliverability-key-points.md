---
title: Belangrijkste punten bij het beheren van de prestaties in Adobe Campagne Classic
description: Wat zijn de belangrijkste punten om te controleren bij het beheren van de prestaties in Adobe Campaign Classic?
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4582ea496fff35c5b586049b8daa379464bd78fc
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---


# Belangrijkste punten voor de aflevering{#deliverability-key-points}

We raden u aan de onderstaande aanbevolen werkwijzen te gebruiken om de leverbaarheid van uw e-mailberichten voor Adobe Campagne te optimaliseren. De leveringsproblemen zijn over het algemeen verbonden met maatregelen van bescherming tegen spam die door de dienstverleners van Internet en de beheerders van de postserver worden uitgevoerd.

**De e-mailleverbaarheid** verwijst naar de reeks kenmerken die bepalen of een bericht zijn bestemming kan bereiken, via een persoonlijk e-mailadres, binnen een korte tijd, en met de verwachte kwaliteit in termen van inhoud en formaat.

Deze kenmerken vallen in vier hoofdcategorieën:
* Gegevenskwaliteit
* Bericht en inhoud
* Infrastructuur verzenden
* Reputatie

Samen vormen ze de basis voor een succesvol e-mailprogramma.

Het **leveringspercentage** is het aantal verzonden e-mailberichten dat is bezorgd aan de ontvangers.

Het percentage te leveren producten hangt af van een groot aantal factoren, met name:
* Correcte configuratie van uw instanties
* Uw IP adresreputatie
* Kwaliteit van de beoogde adressen
* Lage klachten en harde stuitcijfers
* Uw berichtinhoud
* Berichtverificatie (SPF, DKIM, DMARC)
* Afzender

Hieronder ziet u een lijst met de belangrijkste punten die moeten worden gecontroleerd om te zorgen voor goede prestaties.

## Netwerkconfiguratie controleren {#network-configuration}

Spammers proberen hun echte identiteit te verhullen en maken hun servers daardoor moeilijk te identificeren. Een wettige netwerkconfiguratie die niet probeert om de identiteit van de server te verbergen is essentieel voor het verzenden van e-mails in grote volumes.

## Verzenden naar geldige adressen {#valid-addresses}

Spammers gebruiken vaak adresgeneratoren op basis van lijsten met frequente namen en voornamen; bovendien verwerken zij zelden technische kennisgevingen die door mailservers worden teruggestuurd . Een hoog tarief van ongeldige adressen wordt vaak geïnterpreteerd als teken van spam. Dubbele &quot;opt-in&quot;-mechanismen en een effectieve verwerking van technische &quot;bounce&quot;-berichten maken het mogelijk dit te voorkomen.

## Verminder klachten en stuiterende tarieven {#reduce-complaint-rates}

ISPs heeft gewoonlijk een duidelijk middel om een ontvangen bericht als spam te melden. Hierdoor kunnen onbetrouwbare bronnen worden geïdentificeerd. Door opt-outverzoeken snel na te leven, regelmatig gebruik te maken van een bepaalde lijst, toestemming te controleren via een systeem met dubbele opt-in en terugkoppelingsmogelijkheden te implementeren, kunt u de klachtentarieven verlagen.

## Verzenden naar honingsteunadressen {#honeypot-addresses}

ISP&#39;s en andere organisaties (zie de website van de [Projecthoningpoort](https://www.projecthoneypot.org/) ) maken gebruik van postvakken die niet overeenkomen met fysieke personen maar die zijn gemaakt om spammers te bedriegen. Deze zogenaamde &quot;honingpot&quot;-adressen worden op het web gepubliceerd om door spambots te worden verzameld en aldus illegale afzenders te vangen. Het gebruik van een dubbele opt-in-mechanisme sluit het toevoegen van dit adres aan een lijst uit. Wanneer u een lijst van derden gebruikt, moet u zeker zijn van de methoden die door de onderhoudsleider worden gebruikt.

## De inhoud van het bericht aanpassen {#message-content}

In mindere mate kan de inhoud van bepaalde berichten ertoe leiden dat bepaalde filters de inhoud als spam detecteren. Het gebruik van bepaalde woorden, het gebruik van uitroeptekens in de onderwerpregel en in de berichten worden gelezen als verklikkersignalen van spam. Spammers kunnen ook tekst vervangen door afbeeldingen om te voorkomen dat onregelmatige tekst automatisch wordt geanalyseerd door anti-spamfilters. Als reactie hierop kan een bericht (in HTML-indeling) met een groot aantal afbeeldingen of afbeeldingen als bijlagen worden geblokkeerd.

## Werk met uw reputatie {#reputation}

Spammers maken geprogrammeerde leveringen om hun reputatie in de loop der tijd te behouden. Soms moeten zij hun marketing plan aanpassen om aan de beste praktijken te voldoen die door ISPs worden opgelegd en zo, na een piek in reputatie (oprijving), vormen zij regelmatige leveringen.