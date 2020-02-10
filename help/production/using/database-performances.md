---
title: Databaseprestaties
seo-title: Databaseprestaties
description: Databaseprestaties
seo-description: null
page-status-flag: never-activated
uuid: 47ff7532-1fe7-47c2-bc3b-0f46d3a4a288
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 6358c8fd-2b75-4462-acd1-887ee44d3110
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# Databaseprestaties{#database-performances}

De meeste prestatieproblemen houden verband met databaseonderhoud. Hier volgen vier belangrijke aanwijzingen om u te helpen de oorzaak van langzame prestaties te vinden:

* configuratie,
* Installatie en configuratie van het Adobe Campaign-platform,
* onderhoud van databases,
* Realtime diagnose.

## Configuratie {#configuration}

Controleer of de initiële configuratie van het Adobe Campagne-platform nog steeds geldig is en herzie indien nodig de behoeften van uw klant op het gebied van de leverbaarheid of de databasegrootte. We raden u ook aan een volledige hardwarecontrole uit te voeren (CPU, RAM, IO-systeem).

>[!NOTE]
>
>Raadpleeg de handleiding [voor inzichten van](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html) Adobe Campaign Harware Sizing.

## Platformconfiguratie {#platform-configuration}

Onjuiste configuratie kan de prestaties van het platform beïnvloeden. Wij adviseren dat u netwerkconfiguratie, de opties van de platformleverantie evenals configuratie MTA in het **serverConf.xml** - dossier controleert.

## Database-onderhoud {#database-maintenance}

**Opschoontaak database**

Controleer of de opschoontaak van de database actief is. U doet dit door de logbestanden weer te geven om te zien of deze fouten bevatten. Zie [deze sectie](../../production/using/database-cleanup-workflow.md)voor meer informatie.

**Onderhoudsplannen**

Zorg ervoor dat het databaseonderhoud correct is gepland en uitgevoerd. Neem hiervoor contact op met uw databasebeheerder voor meer informatie over:

* hun onderhoudsschema;
* eerder uitgevoerde onderhoudsplannen;
* bekijk de manuscriptlogboeken.

Zie [deze sectie](../../production/using/recommendations.md)voor meer informatie.

>[!CAUTION]
>
>Als u een midsourcingconfiguratie gebruikt, is het van essentieel belang dat databases regelmatig worden onderhouden. Bij het analyseren van een levering op het marketingplatform stuurt de marketinginstantie informatie naar de instantie voor midsourcing. Als het proces wordt vertraagd, wordt het marketingexemplaar beïnvloed.

**Werktabellen beheren**

Controleer het aantal en de grootte van werktabellen. Wanneer zij een bepaalde grootte overschrijden, worden de gegevensbestandprestaties beïnvloed. Deze tabellen worden gemaakt door workflows en leveringen. Ze blijven in de database terwijl workflows en leveringen actief zijn. Als u de grootte van werktabellen wilt beperken, kunt u de volgende bewerkingen uitvoeren:

* leveringen met de volgende statussen stoppen of verwijderen: **[!UICONTROL Failed]** , **[!UICONTROL In progress]** , **[!UICONTROL Ready for delivery]** of **[!UICONTROL Paused]** .
* werkstromen die wegens een fout zijn gepauzeerd, stoppen of verwijderen;
* alle werkstromen te stoppen die worden gebruikt voor tests die geen **[!UICONTROL End]** activiteit bevatten en waarvan de status derhalve behouden blijft **[!UICONTROL Paused]** .

>[!CAUTION]
>
>Als de bewerking lang duurt en veel ruimte vrijmaakt, betekent dit dat diepgaand onderhoud noodzakelijk is (indexheropbouw, enz.). Zie [deze sectie](../../production/using/recommendations.md)voor meer informatie.

**Bewaking van Adobe-campagneproces**

Afhankelijk van de installatie-instellingen van Adobe Campagne kunnen twee programma&#39;s worden gebruikt voor platformbewaking:

* de pagina voor de productie van exemplaren. Raadpleeg [Handmatige controle](../../production/using/monitoring-processes.md#manual-monitoring)voor meer informatie.
* het netreport script. Raadpleeg [Automatische controle via Adobe Campaign-scripts](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)voor meer informatie.

## Specificaties {#specifics}

Het kan nodig zijn een real-time diagnose uit te voeren om de oorzaak van het probleem vast te stellen. Begin door het proces en de dossiers van het platformlogboek te controleren, dan controlegegevensbestandactiviteit terwijl het ontspannen van de kwestie. Let met name op het volgende:

* het uitvoeringsplan voor het onderhoud;
* SQL query&#39;s die worden uitgevoerd,
* de vraag of er tegelijkertijd externe processen plaatsvinden (reiniging, invoer, berekening van aggregaten, enz.).

