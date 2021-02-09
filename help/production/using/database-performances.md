---
solution: Campaign Classic
product: campaign
title: Databaseprestaties
description: Databaseprestaties
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 8%

---


# Databaseprestaties{#database-performances}

De meeste prestatieproblemen houden verband met databaseonderhoud. Hier volgen vier belangrijke aanwijzingen om u te helpen de oorzaak van langzame prestaties te vinden:

* Configuratie
* Installatie en configuratie van het Adobe Campaign-platform
* Databaseonderhoud
* Realtime diagnose

## Configuratie {#configuration}

Controleer of de eerste configuratie van het Adobe Campaign-platform nog geldig is en herzie indien nodig de behoeften van uw klant op het gebied van de leverbaarheid of de databasegrootte. We raden u ook aan een volledige hardwarecontrole uit te voeren (CPU, RAM, IO-systeem).

>[!NOTE]
>
>U kunt [Adobe Campaign Harware Sizing guide](https://helpx.adobe.com/nl/campaign/kb/hardware-sizing-guide.html) voor inzichten raadplegen.

## Configuratie van Platform {#platform-configuration}

Onjuiste configuratie kan de prestaties van het platform beïnvloeden. Wij adviseren dat u netwerkconfiguratie, de opties van de platformLeesbaarheid evenals configuratie MTA in het **serverConf.xml** dossier controleert.

## Databaseonderhoud {#database-maintenance}

**Opschoontaak database**

Controleer of de opschoontaak van de database actief is. U doet dit door de logbestanden weer te geven om te zien of deze fouten bevatten. Raadpleeg [deze sectie](../../production/using/database-cleanup-workflow.md) voor meer informatie.

**Onderhoudsplannen**

Zorg ervoor dat het databaseonderhoud correct is gepland en uitgevoerd. Neem hiervoor contact op met uw databasebeheerder voor meer informatie over:

* Hun onderhoudsschema
* Eerder uitgevoerde onderhoudsplannen
* Scriptlogboeken weergeven

Raadpleeg [deze sectie](../../production/using/recommendations.md) voor meer informatie.

>[!IMPORTANT]
>
>Als u een midsourcingconfiguratie gebruikt, is het van essentieel belang dat databases regelmatig worden onderhouden. Bij het analyseren van een levering op het marketingplatform stuurt de marketinginstantie informatie naar de instantie voor midsourcing. Als het proces wordt vertraagd, wordt het marketingexemplaar beïnvloed.

**Werktabellen beheren**

Controleer het aantal en de grootte van werktabellen. Wanneer zij een bepaalde grootte overschrijden, worden de gegevensbestandprestaties beïnvloed. Deze tabellen worden gemaakt door workflows en leveringen. Ze blijven in de database terwijl workflows en leveringen actief zijn. Als u de grootte van werktabellen wilt beperken, kunt u de volgende bewerkingen uitvoeren:

* Leveringen met de volgende statussen stoppen of verwijderen: **[!UICONTROL Failed]**, **[!UICONTROL In progress]**, **[!UICONTROL Ready for delivery]** of **[!UICONTROL Paused]**.
* Workflows stoppen of verwijderen die zijn gepauzeerd vanwege een fout.
* Stop alle workflows die worden gebruikt voor tests die geen **[!UICONTROL End]**-activiteit bevatten en waarvan de status daarom **[!UICONTROL Paused]** blijft.

>[!IMPORTANT]
>
>Als de bewerking lang duurt en veel ruimte vrijmaakt, betekent dit dat diepgaand onderhoud noodzakelijk is (indexheropbouw, enz.). Raadpleeg [deze sectie](../../production/using/recommendations.md) voor meer informatie.

**Adobe Campaign-procesbewaking**

Afhankelijk van de installatie-instellingen van Adobe Campaign kunnen twee tools worden gebruikt voor platformbewaking:

* De pagina voor instantieproductie. Raadpleeg [Handmatige bewaking](../../production/using/monitoring-processes.md#manual-monitoring) voor meer informatie.
* Het *netreport* manuscript. Raadpleeg [Automatische bewaking via Adobe Campaign-scripts](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) voor meer informatie.

## Specificaties {#specifics}

Het kan nodig zijn een real-time diagnose uit te voeren om de oorzaak van het probleem vast te stellen. Begin door het proces en de dossiers van het platformlogboek te controleren, dan controlegegevensbestandactiviteit terwijl het ontspannen van de kwestie. Let met name op het volgende:

* Uitvoeringsplan voor onderhoud
* SQL-query&#39;s uitgevoerd
* Of de externe processen tegelijkertijd worden uitgevoerd (reiniging, invoer, berekening van aggregaten, enz.).
