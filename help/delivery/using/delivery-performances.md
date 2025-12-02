---
product: campaign
title: Best practices voor leveringen
description: Meer informatie over leveringsprestaties en aanbevolen procedures
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '465'
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

* Personalization in e-mailberichten haalt gegevens uit de database voor elke ontvanger. Als er vele verpersoonlijkingselementen zijn, verhoogt dat de hoeveelheid gegevens nodig om de levering voor te bereiden.

* Indexadressen. Om de prestaties van de SQL vragen te optimaliseren die in de toepassing worden gebruikt, kan een index van het belangrijkste element van het gegevensschema worden verklaard.

>[!NOTE]
>
>ISPs zou adressen na een periode van inactiviteit deactiveren. De berichten van de vlag worden verzonden naar afzenders om hen over deze nieuwe status te informeren.

## Checklist voor prestatieproblemen {#performance-issues}

Als de leveringsprestaties slecht zijn, kunt u controleren:

* **de grootte van de levering**: De grote leveringen kunnen langer duren om te voltooien. De kinderen MTA worden gevormd om een standaardpartijgrootte te behandelen, die voor de meeste instanties werkt, maar moet worden gecontroleerd wanneer de leveringen constant langzaam zijn.
* **het doel van de levering**: Het verbod van de uitvoeringen van de levering wordt beïnvloed door zachte stuiteringsfouten, die volgens de retry configuratie worden behandeld. Hoe groter het aantal fouten, hoe meer pogingen nodig zijn.
* **de algemene platformlading**: Wanneer verscheidene grote leveringen worden verzonden, kan het algemene platform worden beïnvloed. U kunt IP reputatie en leveringsproblemen ook controleren. Voor meer op dit, verwijs naar [ deze sectie ](about-deliverability.md) en naar de [ Gids van de Beste praktijken van de Levering van Adobe ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl).

Het onderhoud van platforms en databases kan ook van invloed zijn op de verzendprestaties van de levering. Raadpleeg [deze pagina](../../production/using/database-performances.md) voor meer informatie.
