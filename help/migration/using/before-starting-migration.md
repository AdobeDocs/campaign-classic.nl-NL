---
product: campaign
title: Voordat u de migratie start
description: Voordat u de migratie start
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 1%

---

# Voordat u de migratie start{#before-starting-migration}

![](../../assets/v7-only.svg)

>[!NOTE]
>
>In dit document worden aan de database gekoppelde opdrachten als voorbeeld gegeven. Deze kunnen afhankelijk van hun configuratie variëren. Neem contact op met de databasebeheerder.

## Waarschuwingen {#warnings}

* Het migratieproces mag alleen door deskundige gebruikers worden uitgevoerd. U moet door minstens een gegevensbestanddeskundige, een systeembeheerder en een toepassingsontwikkelaar van Adobe Campaign worden bijgestaan.
* Voordat u de migratie start, moet u controleren of de systemen en systeemonderdelen die u gebruikt, in feite compatibel zijn met versie 7. Raadpleeg de [compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).
* Als u Adobe Campaign Cloud Messaging (medio-sourcing) gebruikt, neemt u contact op met Adobe voordat u de gehele migratieprocedure start.
* Voordat u een migratieproces start, **moet** Maak een back-up van uw gegevens.
* Het migratieproces kan enkele dagen duren.
* Adobe Campaign v7 is wat configuratie betreft strenger dan de versies 5.11 en 6.02. Dit is hoofdzakelijk om problemen zoals gegevenscorruptie te vermijden en gegevensintegriteit in het gegevensbestand te bewaren. Bijgevolg werken bepaalde functies die in v5.11 en v6.02 worden aangeboden, mogelijk niet meer in v7 en moeten deze daarom mogelijk na de migratie worden aangepast. Voordat u iets gaat produceren, raden we u aan systematisch alle configuraties te testen, met name workflows die nodig zijn voor het gebruik van Adobe Campaign.

### Geïnstalleerde versie {#installed-version}

Voordat u gaat migreren, moet u de nieuwste build van de huidige versie installeren die u gebruikt.

Controleer de versie op de server door naar de **[!UICONTROL Help> About]** op de clientconsole met behulp van de **nlserver pdump** gebruiken.

### Gegevensback-up {#data-backup}

Voordat u een migratieproces start, **moet** Maak een back-up van uw gegevens.

### Omgeving {#environment}

* Het is niet mogelijk om het type database-engine (DBMS) te wijzigen. U kunt bijvoorbeeld niet schakelen van een PostgreSQL-engine naar een Oracle-engine. U kunt echter schakelen van een Oracle 8-engine naar een Oracle 10-engine.
* Het is niet mogelijk van een niet-Unicode-database naar een Unicode-database te gaan.

### Aanbeveling {#recommendation}

Aangezien de migratieprocedure gevoelig ligt, raden wij u ten zeerste aan dit document grondig te lezen voordat de procedure wordt gestart.

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

>[!IMPORTANT]
>
>De **internal** wachtwoord moet identiek zijn voor alle volgende servers. Raadpleeg voor meer informatie de [Interne id](../../installation/using/configuring-campaign-server.md#internal-identifier) en [Machtigingen](../../platform/using/access-management.md) secties.
