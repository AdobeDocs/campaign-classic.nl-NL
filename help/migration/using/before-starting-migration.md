---
product: campaign
title: Voordat u de migratie start
description: Voordat u de migratie start
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 80cf56e330731237d5e7b394381b737f30f8b350
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# Vereisten{#before-starting-migration}

![](../../assets/v7-only.svg)

Deze pagina bevat specifieke stappen die moeten worden uitgevoerd voordat het migratieproces wordt gestart. U moet ook verwijzen naar [deze pagina](about-migration.md) voor meer richtsnoeren.

>[!NOTE]
>
>In dit document worden opdrachten als voorbeelden gegeven. Zij kunnen afhankelijk van uw configuratie variëren.

1. Controleer uw Adobe Campaign-versie: voordat u gaat migreren, installeert u de meest recente build van de huidige versie die u gebruikt.
1. Maak een back-up van uw gegevens.
1. Controleer uw omgeving: u kunt het systeem van de gegevensbestandmotor (DBMS) niet veranderen. U kunt bijvoorbeeld niet schakelen van een PostgreSQL-engine naar een Oracle-engine. U kunt echter wel overschakelen naar de meest recente versie van de database-engine. Het is niet mogelijk van een niet-Unicode-database naar een Unicode-database te gaan.

## Migratiestappen {#migration-steps}

De migratieprocedure moet worden uitgevoerd **alles** en in een bepaalde volgorde.

* In het geval van een **zelfstandig platform** (modus Eén computer), wordt de toepassing in zijn geheel gemigreerd.
* In het geval van een **standaardplatform** (onderneming) zijn de migratiestappen als volgt:

   1. Migreer de marketingserver.
   1. Migreer de mailserver (mta).
   1. Migreer de omleiding en het volgen servers (Apache/IIS).

* In het geval van een **Cloud Messaging-platform**, worden de uitvoeringsservers gehost op Adobe Campaign. Neem contact op met Adobe Campaign om de migratie tussen verschillende servers te coördineren.
* In het geval van een **Power Booster- of Power Cluster-platform**, zijn de migratiestappen als volgt:

   1. Migreer de omleiding en het volgen servers (Apache/IIS).
   1. Migreer de Power Booster/Cluster-servers.
   1. Migreer de marketingserver.

## Gebruikerswachtwoorden {#user-passwords}

In v7: **internal** en **beheerder** De verbinding van de exploitant moet door een wachtwoord worden beveiligd. Wij adviseren sterk wachtwoorden aan deze rekeningen en alle exploitantrekeningen toe te wijzen, **voor migratie**. Als u geen wachtwoord hebt opgegeven voor **internal**, kunt u geen verbinding maken. Een wachtwoord toewijzen aan **internal** voert u de volgende opdracht in:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>De **internal** wachtwoord moet identiek zijn voor alle volgende servers. Raadpleeg voor meer informatie de [Interne id](../../installation/using/configuring-campaign-server.md#internal-identifier) en [Machtigingen](../../platform/using/access-management.md) secties.
