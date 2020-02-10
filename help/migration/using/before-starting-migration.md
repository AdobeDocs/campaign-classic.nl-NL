---
title: Voordat u de migratie start
seo-title: Voordat u de migratie start
description: Voordat u de migratie start
seo-description: null
page-status-flag: never-activated
uuid: b9325510-2fa5-4be4-9cf0-f37232bbbd8c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: d8877378-fb43-4f32-91c6-60f2f788f916
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f460c79a763c6a207656c54351a4c685f2a78a03

---


# Voordat u de migratie start{#before-starting-migration}

>[!NOTE]
>
>In dit document worden aan de database gekoppelde opdrachten als voorbeeld gegeven. Deze kunnen afhankelijk van hun configuratie variëren. Neem contact op met de databasebeheerder.

## Waarschuwingen {#warnings}

### Geïnstalleerde versie {#installed-version}

Voordat u gaat migreren, moet u de nieuwste build van de huidige versie installeren die u gebruikt.

Controleer de versie op uw server door naar het **[!UICONTROL Help> About]** menu op de cliëntconsole te gaan gebruikend het **nlserver** bevel van de pomp.

### Gegevensback-up {#data-backup}

Voordat u een migratieproces start, **moet** u een back-up maken van uw gegevens.

### Omgeving {#environment}

* Het is niet mogelijk om het type database-engine (DBMS) te wijzigen. U kunt bijvoorbeeld niet schakelen van een PostgreSQL-engine naar een Oracle-engine. U kunt echter overschakelen van een Oracle 8-engine naar een Oracle 10-engine.
* Het is niet mogelijk van een niet-Unicode-database naar een Unicode-database te gaan.

### Aanbeveling {#recommendation}

Aangezien de migratieprocedure bijzonder gevoelig ligt, bevelen wij ten zeerste aan dit document grondig te lezen voordat de procedure wordt gestart.

## Migratiestappen {#migration-steps}

De migratieprocedure moet op **alle** servers en in een bepaalde volgorde worden uitgevoerd.

* In het geval van een **zelfstandig platform** (modus Eén computer) wordt de toepassing volledig gemigreerd.
* In het geval van een **standaardplatform** (onderneming) zijn de migratiestappen als volgt:

   1. Migreer de marketingserver.
   1. Migreer de mailserver (mta).
   1. Migreer de omleiding en het volgen servers (Apache/IIS).

* In het geval van een **Cloud Messaging-platform** worden de uitvoeringsservers gehost in Adobe Campaign. Neem contact op met de Adobe-campagne om de migratie tussen verschillende servers te coördineren.
* In het geval van een **Power Booster- of Power Cluster-platform** zijn de migratiestappen als volgt:

   1. Migreer de omleiding en het volgen servers (Apache/IIS).
   1. Migreer de Power Booster/Cluster-servers.
   1. Migreer de marketingserver.

>[!NOTE]
>
>Communicatie tussen een v6.02-marketingserver en een v7 Cloud Messaging- of Power Booster-/Cluster-server is mogelijk. Als u echter besluit om uw marketingserver voor versie 6.02 te behouden, moet deze worden bijgewerkt met de meest recente build voor versie 6.02 voordat u kunt migreren naar Cloud Messaging of Power Booster/Cluster.

## Gebruikerswachtwoorden {#user-passwords}

In v7 moet de **interne** en **beheerder** operatorverbinding met een wachtwoord worden beveiligd. We raden u ten zeerste aan wachtwoorden toe te wijzen aan deze accounts en alle exploitantaccounts, **voordat u gaat migreren**. Als u geen wachtwoord voor **intern** hebt opgegeven, kunt u geen verbinding maken. Voer de volgende opdracht in om een wachtwoord aan **internal** toe te wijzen:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>Het **interne** wachtwoord moet voor alle volgende servers identiek zijn. Raadpleeg de secties [Interne id](../../installation/using/campaign-server-configuration.md#internal-identifier) en [Informatie over machtigingen](../../platform/using/access-management.md#about-permissions) voor meer informatie.

