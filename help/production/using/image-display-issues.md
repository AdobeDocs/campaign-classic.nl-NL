---
product: campaign
title: Problemen met weergave van afbeeldingen
description: Problemen met weergave van afbeeldingen
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# Problemen met weergave van afbeeldingen{#image-display-issues}



Als er problemen optreden met de weergave van afbeeldingen in een verzonden bericht, kunnen er redenen zijn voor een onjuiste locatie:

* Locaties komen mogelijk niet overeen of afbeeldingen zijn mogelijk niet correct geduwd op de gedupliceerde trackingserver: controleer uw configuratie.
* Afbeeldingen bevinden zich mogelijk niet in de map met openbare bronnen op de marketinginstantie: upload de afbeeldingen naar de bronnenmap om het probleem op te lossen.
* Als u werkt in een architectuur voor midsourcing: controleer of afbeeldingen zonder fouten worden geüpload wanneer proefdrukken worden verzonden (informatie wordt weergegeven in de analyselogboeken).

Hoe te om problemen op te lossen:

1. Stuur een proefdruk waarin de afbeeldingen worden weergegeven.
1. Valideer de middelenconfiguratie in de instantie opstelling correct is.
1. Controleer de map met openbare bronnen of, als deze zich niet in de map met openbare bronnen bevindt, de map waarnaar in de levering wordt verwezen.
