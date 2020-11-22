---
solution: Campaign Classic
product: campaign
title: Belangrijkste punten voor de aflevering
description: belangrijke punten om te controleren om uw leverbaarheid te verbeteren
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 2%

---


# Belangrijkste punten voor de aflevering{#deliverability-key-points}

We raden u aan de onderstaande aanbevolen procedures te gebruiken om de leverbaarheid van je Adobe Campaign-e-mails te optimaliseren. De leveringsproblemen zijn over het algemeen verbonden met maatregelen van bescherming tegen spam die door de dienstverleners van Internet en de beheerders van de postserver worden uitgevoerd.

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

## Aanbevolen procedures {#best-practices}

Leer de beste praktijken met betrekking tot leverbaarheid met Adobe Campaign. Gebruik de onderstaande koppelingen om door onderwerpen te navigeren en hulp te zoeken.

<table>
<tr>
  <td>
    <a href="starting-new-platform.md">
      <img alt="Starten" src="assets/do-not-localize/start.svg" width="60px"/>
    </a>
    <div>
      <a href="starting-new-platform.md">
    <strong>Start</strong>
    </a>
    </div>
    <p>
    <em>Een nieuw platform starten</em>
    <p>
  </td>
   <td>
    <a href="control-message-content.md">
      <img alt="Ontwerp" src="assets/do-not-localize/design.svg" width="60px"/>
    </a>
    <div>
      <a href="control-message-content.md">
    <strong>Ontwerp</strong>
    </a>
    </div>
    <p>
    <em>Content van controleberichten</em>
    <p>
  </td>
  <td>
    <a href="improve-reputation.md">
      <img alt="Ontwerp" src="assets/do-not-localize/check.svg" width="60px"/>
    </a>
    <div>
      <a href="improve-reputation.md">
    <strong>Verzenden</strong>
    </a>
    </div>
    <p>
    <em>Uw reputatie verbeteren</em>
    <p>
  </td>
</tr>
<tr>
  <td>
    <a href="technical-recommendations.md">
      <img alt="Optimaliseren" src="assets/do-not-localize/optimize.svg" width="60px"/>
    </a>
    <div>
      <a href="technical-recommendations.md">
    <strong>Optimaliseren</strong>
    </a>
    </div>
    <p>
    <em>Technische aanbevelingen</em>
    <p>
  </td>
   <td>
    <a href="monitoring-deliverability.md">
      <img alt="Controleren" src="assets/do-not-localize/monitor.svg" width="60px"/>
    </a>
    <div>
      <a href="monitoring-deliverability.md">
    <strong>Monitor</strong>
    </a>
    </div>
    <p>
    <em>Monitoringinstrumenten</em>
    <p>
  </td>
  <td>
    <a href="deliverability-faq.md">
      <img alt="Optimaliseren" src="assets/do-not-localize/troubleshoot.svg" width="60px"/>
    </a>
    <div>
      <a href="deliverability-faq.md">
    <strong>Problemen oplossen</strong>
    </a>
    </div>
    <p>
    <em>Oplossen van problemen</em>
    <p>
  </td>
</tr>
</table>
