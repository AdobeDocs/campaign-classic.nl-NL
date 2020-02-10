---
title: Migratiemethode
seo-title: Migratiemethode
description: Migratiemethode
seo-description: null
page-status-flag: never-activated
uuid: 6b954d5b-cfa3-43c6-ac3d-da9185e9e9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-overview
discoiquuid: 3ac779a7-1f91-4c1c-a439-10d01697326a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4437d2ea4e4044245a2b9a5a870267cd1f1c0bc9

---


# Migratiemethode{#migration-method}

## Uw omgeving moderniseren {#modernizing-your-environment}

Het uitvoeren van een migratie kan een kans zijn om uw omgeving (databasemotoren, besturingssystemen) bij te werken. Adobe Campaign raadt u ten zeerste aan uw productieomgevingen te upgraden naar de meest recente versies.

Databases en besturingssystemen van 32-bits versies worden nog steeds ondersteund in versie 7, maar worden niet meer ondersteund in toekomstige versies van Adobe Campagne. We raden u ten zeerste aan uw platform zo snel mogelijk te upgraden naar 64 bits.

In v6.02 was de modus &quot;multi timezone&quot; alleen beschikbaar voor PostgreSQL-databasemotoren. Er wordt nu aangeboden welk type database-engine wordt gebruikt. Wij adviseren sterk dat u uw basis in een &quot;multi timezone&quot;basis omzet. Zie de sectie [Tijdzones](../../migration/using/general-configurations.md#time-zones) voor meer informatie hierover.

>[!CAUTION]
>
>Sommige softwareversies die worden ondersteund in Adobe Campaign 5.11 en 6.02, worden niet meer ondersteund in Adobe Campaign v7.
>
>Raadpleeg de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)voor meer informatie over de versies die door Adobe Campaign worden ondersteund.

## Belangrijke migratiestappen {#key-migration-steps}

De algemene procedure voor het migreren naar Adobe Campagne v7 wordt beschreven in de sectie [Voor het starten van de migratie](../../migration/using/before-starting-migration.md) .

De implementatiestappen voor de migratie naar Adobe Campaign v7 worden beschreven in de sectie [Voorwaarden voor migratie naar Adobe Campagne 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .

De vereiste configuraties zijn afhankelijk van uw bestaande configuraties en de eerste versie van het platform. Deze worden geschetst in de [Algemene configuratiesectie](../../migration/using/general-configurations.md) .

## Specifieke configuraties {#specific-configurations}

De wijzigingen die worden aangebracht door Adobe Campaign v7, kunnen er ook toe leiden dat u bepaalde specifieke configuraties moet aanpassen die zijn ontwikkeld in eerdere versies. Daarom kan het noodzakelijk zijn om een controle op al uw configuraties vóór de migratie uit te voeren: Neem contact op met de Adobe-campagne voor hulp.

Bijvoorbeeld, zou de bijzondere aandacht aan specifieke montages voor de toepassingen van het Web, schemauitbreidingen met SQLdata of uit-van-de-doos schemakolonering moeten worden besteed. Raadpleeg de sectie [Uw platform](../../migration/using/configuring-your-platform.md) configureren voor meer informatie.

Om te reageren op de verhoogde beveiliging in Adobe Campaign, zijn enkele interne mechanismen gewijzigd: u moet deze overeenkomstige configuraties aanpassen.
