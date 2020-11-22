---
solution: Campaign Classic
product: campaign
title: Voordat u de migratie start
description: Voordat u de migratie start
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 1%

---


# Voordat u de migratie start{#before-starting-migration}

>[!NOTE]
>
>In dit document worden aan de database gekoppelde opdrachten als voorbeeld gegeven. Deze kunnen afhankelijk van hun configuratie variëren. Neem contact op met de databasebeheerder.

## Waarschuwingen {#warnings}

* Het migratieproces mag alleen door deskundige gebruikers worden uitgevoerd. U moet door minstens een gegevensbestanddeskundige, een systeembeheerder en een toepassingsontwikkelaar van Adobe Campaign worden bijgestaan.
* Voordat u de migratie start, moet u controleren of de systemen en systeemonderdelen die u gebruikt, in feite compatibel zijn met versie 7. Raadpleeg de [compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).
* Als u Adobe Campaign Cloud Messaging (medio-sourcing) gebruikt, neemt u contact op met Adobe voordat u de gehele migratieprocedure start.
* Voordat u een migratieproces start, **moet** u een back-up maken van uw gegevens.
* Het migratieproces kan enkele dagen duren.
* Adobe Campaign v7 is wat configuratie betreft strenger dan de versies 5.11 en 6.02. Dit is hoofdzakelijk om problemen zoals gegevenscorruptie te vermijden en gegevensintegriteit in het gegevensbestand te bewaren. Bijgevolg werken bepaalde functies die in v5.11 en v6.02 worden aangeboden, mogelijk niet meer in v7 en moeten deze daarom mogelijk na de migratie worden aangepast. Voordat u iets gaat produceren, raden we u aan systematisch alle configuraties te testen, met name workflows die nodig zijn voor het gebruik van Adobe Campaign.

### Geïnstalleerde versie {#installed-version}

Voordat u gaat migreren, moet u de nieuwste build van de huidige versie installeren die u gebruikt.

Controleer de versie op uw server door naar het **[!UICONTROL Help> About]** menu op de cliëntconsole te gaan gebruikend het **nlserver** bevel van de pomp.

### Gegevensback-up {#data-backup}

Voordat u een migratieproces start, **moet** u een back-up maken van uw gegevens.

### Omgeving {#environment}

* Het is niet mogelijk om het type database-engine (DBMS) te wijzigen. U kunt bijvoorbeeld niet schakelen van een PostgreSQL-engine naar een Oracle-engine. U kunt echter schakelen van een Oracle 8-engine naar een Oracle 10-engine.
* Het is niet mogelijk van een niet-Unicode-database naar een Unicode-database te gaan.

### Aanbeveling {#recommendation}

Aangezien de migratieprocedure gevoelig ligt, raden wij u ten zeerste aan dit document grondig te lezen voordat de procedure wordt gestart.

## Migratiestappen {#migration-steps}

De migratieprocedure moet op **alle** servers en in een bepaalde volgorde worden uitgevoerd.

* In het geval van een **zelfstandig platform** (modus Eén computer) wordt de toepassing volledig gemigreerd.
* In het geval van een **standaardplatform** (onderneming) zijn de migratiestappen als volgt:

   1. Migreer de marketingserver.
   1. Migreer de mailserver (mta).
   1. Migreer de omleiding en het volgen servers (Apache/IIS).

* Bij een **Cloud Messaging-platform** worden de uitvoeringsservers gehost op Adobe Campaign. Neem contact op met Adobe Campaign om de migratie tussen verschillende servers te coördineren.
* In het geval van een **Power Booster- of Power Cluster-platform** zijn de migratiestappen als volgt:

   1. Migreer de omleiding en het volgen servers (Apache/IIS).
   1. Migreer de Power Booster/Cluster-servers.
   1. Migreer de marketingserver.

## Gebruikerswachtwoorden {#user-passwords}

In v7 moet de **interne** en **beheerder** operatorverbinding met een wachtwoord worden beveiligd. We raden u ten zeerste aan wachtwoorden toe te wijzen aan deze accounts en alle exploitantaccounts, **voordat u gaat migreren**. Als u geen wachtwoord voor **intern** hebt opgegeven, kunt u geen verbinding maken. Voer de volgende opdracht in om een wachtwoord aan **internal** toe te wijzen:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>Het **interne** wachtwoord moet voor alle volgende servers identiek zijn. Raadpleeg de secties [Interne id](../../installation/using/campaign-server-configuration.md#internal-identifier) en [Informatie over machtigingen](../../platform/using/access-management.md#about-permissions) voor meer informatie.

