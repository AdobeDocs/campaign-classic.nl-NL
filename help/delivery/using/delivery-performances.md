---
product: campaign
title: Best practices voor leveringen
description: Meer informatie over leveringsprestaties en aanbevolen procedures
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
role: User, Data Engineer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 5%

---

# Best practices voor leveringen {#delivery-performances}

We raden u aan de onderstaande richtlijnen te volgen om ervoor te zorgen dat uw leveringen goed functioneren en dat de prestaties worden gecontroleerd als er problemen met leveringen optreden.

**Verwante onderwerpen:**

* [Leveringsdashboard](delivery-dashboard.md)
* [Problemen met een levering oplossen](delivery-troubleshooting.md)
* [Informatie over leverbaarheid](about-deliverability.md)

## Aanbevolen werkwijzen voor prestaties {#best-practices-performance}

* Bewaar de levering niet in mislukte staat, aangezien dit tijdelijke lijsten handhaaft en de prestaties beïnvloedt.

* Leveringen verwijderen die niet meer nodig zijn.

* Inactieve ontvangers in de laatste 12 maanden die uit het gegevensbestand moeten worden verwijderd om adreskwaliteit te handhaven.

* Probeer geen grote leveringen samen te plannen. Er is een tussenruimte van 5-10 minuten om de belasting gelijkmatig over het systeem te spreiden. Coördineer het plannen van leveringen met de andere leden van uw team om de beste prestaties te verzekeren. Wanneer de marketingserver meerdere taken tegelijk uitvoert, kan dit de prestaties vertragen.

* Houd je e-mailadres zo klein mogelijk. De aanbevolen maximale grootte van een e-mailbericht is ongeveer 35 kB. De grootte van een e-maillevering genereert een bepaalde hoeveelheid volume in de verzendende servers.

* De grote leveringen, zoals leveringen aan meer dan één miljoen ontvangers, hebben ruimte in de verzendende rijen nodig. Dit is op zich geen probleem voor de server, maar in combinatie met tientallen andere grote leveringen die allemaal tegelijk worden uitgevoerd, kan er een vertraging bij het verzenden ontstaan.

* Personalisatie in e-mailberichten haalt gegevens uit de database voor elke ontvanger. Als er vele verpersoonlijkingselementen zijn, verhoogt dat de hoeveelheid gegevens nodig om de levering voor te bereiden.

* Indexadressen. Om de prestaties van de SQL vragen te optimaliseren die in de toepassing worden gebruikt, kan een index van het belangrijkste element van het gegevensschema worden verklaard.

>[!NOTE]
>
>ISPs zou adressen na een periode van inactiviteit deactiveren. De berichten van de vlag worden verzonden naar afzenders om hen over deze nieuwe status te informeren.

## Checklist voor prestatieproblemen {#performance-issues}

Als de leveringsprestaties slecht zijn, kunt u controleren:

* **De omvang van de levering**: Het voltooien van grote leveringen kan langer duren. De kinderen MTA worden gevormd om een standaardpartijgrootte te behandelen, die voor de meeste instanties werkt, maar moet worden gecontroleerd wanneer de leveringen constant langzaam zijn.
* **Het doel van de levering**: Het verbod op prestaties bij levering wordt beïnvloed door zachte stuiterfouten, die worden verwerkt volgens de configuratie voor opnieuw uitproberen. Hoe groter het aantal fouten, hoe meer pogingen nodig zijn.
* **De totale platformbelasting**: Wanneer meerdere grote leveringen worden verzonden, kan dit gevolgen hebben voor het hele platform. U kunt IP reputatie en leveringsproblemen ook controleren. Raadpleeg voor meer informatie hierover [deze sectie](about-deliverability.md) en aan de [Handleiding voor beste praktijken bij de levering van Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl).

Het onderhoud van platforms en databases kan ook van invloed zijn op de verzendprestaties van de levering. Raadpleeg [deze pagina](../../production/using/database-performances.md) voor meer informatie.
