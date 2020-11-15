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
translation-type: tm+mt
source-git-commit: 99d766cb6234347ea2975f3c08a6ac0496619b41
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 2%

---


# Migratiemethode{#migration-method}

## Uw omgeving moderniseren {#modernizing-your-environment}

Het uitvoeren van een migratie kan een kans zijn om uw omgeving (databasemotoren, besturingssystemen) bij te werken. Adobe Campaign raadt u ten zeerste aan uw productieomgevingen te upgraden naar de meest recente versies.

Databases en besturingssystemen van 32-bits versies worden nog steeds ondersteund in versie 7, maar worden niet meer ondersteund in toekomstige versies van Adobe Campaign. We raden u ten zeerste aan uw platform zo snel mogelijk te upgraden naar 64 bits.

In v6.02 was de modus &quot;multi timezone&quot; alleen beschikbaar voor PostgreSQL-databasemotoren. Er wordt nu aangeboden welk type database-engine wordt gebruikt. Wij adviseren sterk dat u uw basis in een &quot;multi timezone&quot;basis omzet. Zie de sectie [Tijdzones](../../migration/using/general-configurations.md#time-zones) voor meer informatie hierover.

>[!IMPORTANT]
>
>Sommige softwareversies die worden ondersteund in Adobe Campaign 5.11 en 6.02, worden niet meer ondersteund in Adobe Campaign v7.
>
>Raadpleeg de [compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md)voor meer informatie over de versies die door Adobe Campaign worden ondersteund.

## Belangrijke migratiestappen {#key-migration-steps}

De algemene procedure voor migratie naar Adobe Campaign v7 wordt beschreven in het gedeelte [Voor aanvang van de migratie](../../migration/using/before-starting-migration.md) .

Implementatiestappen voor de migratie naar Adobe Campaign v7 worden beschreven in de sectie [Voorwaarden voor migratie naar Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .

De vereiste configuraties zijn afhankelijk van uw bestaande configuraties en de eerste versie van het platform. Deze worden geschetst in de [Algemene configuratiesectie](../../migration/using/general-configurations.md) .

## Specifieke configuraties {#specific-configurations}

Door de wijzigingen die Adobe Campaign v7 aanbrengt, moet u mogelijk ook bepaalde specifieke configuraties aanpassen die in eerdere versies zijn ontwikkeld. Daarom kan het noodzakelijk zijn om een controle op al uw configuraties vóór de migratie uit te voeren: Neem contact op met Adobe Campaign voor hulp.

Bijvoorbeeld, zou de bijzondere aandacht aan specifieke montages voor de toepassingen van het Web, schemauitbreidingen met SQLdata of uit-van-de-doos schemakolonering moeten worden besteed. Raadpleeg de sectie [Uw platform](../../migration/using/configuring-your-platform.md) configureren voor meer informatie.

Om te reageren op de toegenomen veiligheid in Adobe Campaign zijn ook enkele interne mechanismen gewijzigd: u moet deze overeenkomstige configuraties aanpassen.
