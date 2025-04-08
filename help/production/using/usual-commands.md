---
product: campaign
title: Gebruikelijke opdrachten
description: Gebruikelijke opdrachten
feature: Monitoring
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 3%

---

# Gebruikelijke opdrachten{#usual-commands}



In deze sectie worden de gebruikelijke opdrachten in Adobe Campaign weergegeven.

Het bevel **nlserver** is het inputbevel voor de volledige toepassing van Adobe Campaign.

Deze opdracht heeft de volgende syntaxis: **nullServer **`<command>`****`<arguments>`****

De parameter **`<command>`** komt overeen met de module.

>[!NOTE]
>
>* In elk geval, kunt u **- noconsole** argument toevoegen om commentaren te schrappen die worden getoond zodra de modules zijn begonnen.
>* Omgekeerd, kunt u het argument **- verbose** toevoegen om meer informatie te tonen.
>

## Bewaking, opdrachten {#monitoring-commands-}

>[!NOTE]
>
>Om van alle modules een lijst te maken, moet u het **bevel gebruiken 0} nlserver van de pomp {.**

U kunt de parameter **- toevoegen wie** om van de lopende verbindingen (gegevensbestand en toepassing) een lijst te maken.

```sql
nlserver pdump -who
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
web@default (9984) - 50.1 Mo
watchdog (2273) - 6.6 Mo
syslogd@default (9931) - 7.0 Mo
trackinglogd@default (9985) - 45.6 Mo
mta@test (9986) - 9.6 Mo
wfserver@test (9987) - 8.8 Mo

Connections ------------------------------------------------------
Last Access IP Instance Login 
DD/MM/YYYY HH:MM:SS 127.0.0.1 default formation_fr|tracking
DD/MM/YYYY HH:MM:SS 127.0.0.1 default internal|monitoring

Connection pool --------------------------------------------------
Datasource Server Provider Login 
default xxxxx myserver myprovider test400
```

Een ander nuttig bevel is **nlserver monitor**. Het maakt een lijst van het dossier van controleXML (dat in de cliënt van Adobe Campaign of via **wordt verkregen monitor.jsp** Web-pagina).

U kunt de parameter **-missing** toevoegen om van de afwezige modules (fout in modules, modules sluiten, enz.) een lijst te maken

```sql
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Dit komt overeen met de modules met automatisch opstarten, maar die nog niet zijn gestart.

## Opdrachten voor het starten van modules {#module-launch-commands}

De syntaxis voor opstartmodules heeft nog steeds de volgende indeling:

```sql
nlserver start <module>@<INSTANCE>
```

```sql
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** beantwoordt aan de naam van de instantie zoals ingegaan in de configuratiedossiers, of **gebrek** voor mono-instantie modules.

## Afsluiten van services {#shut-down-services}

Als u de Adobe Campaign-services wilt stoppen, gebruikt u een van de volgende opdrachten:

* Als u toegang hebt tot de hoofdmap of beheerder:

   * In Linux:

     ```sql
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >Beginnend 20.1, adviseren wij het gebruiken van het volgende bevel in plaats daarvan (voor Linux): **systemctl stop nlserver**

   * In Windows:

     ```sql
     net stop nlserver6
     ```

* Zo niet, dan op de Adobe Campaign-account:

  ```sql
  nlserver shutdown 
  ```

## Herstartservices {#restart-services}

Op dezelfde manier kunt u een van de volgende opdrachten gebruiken om Adobe Campaign opnieuw te starten:

* Als u toegang hebt tot de hoofdmap of beheerder:

   * In Linux: `/etc/init.d/nlserver6 start`

     >[!NOTE]
     >
     >Beginnend 20.1, adviseren wij het gebruiken van het volgende bevel in plaats daarvan (voor Linux): **systeemctl begin nlserver**

   * In Windows: `net start nlserver6`

* Anders, in de rekening van Adobe Campaign: **nlserver waakhond - svc - noconsole**

## Het configuratiebevel {#the-config-command}

Het **config** bevel laat u serverconfiguratie, met inbegrip van de herconfiguratie van de gegevensbestandverbinding beheren.

Gebruik het **config** bevel van het **nlserver** uitvoerbare dossier met de **-setdblogin** parameter.

```sql
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```sql
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Voer het wachtwoord in.

Om het **interne** wachtwoord te veranderen: **nlserver config - intern wachtwoord**

>[!IMPORTANT]
>
>Om met het **Interne** herkenningsteken het programma te openen, moet u een wachtwoord vooraf bepaald hebben. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier) voor meer informatie.

>[!NOTE]
>
>* In het algemeen, in plaats van de configuratiedossiers door hand te wijzigen, kunt u het **config** bevel gebruiken
>* Als u de lijst met parameters wilt ophalen, gebruikt u de lus **-?** parameter: **nlserver config -?**
>* In het geval van een Oracle-database mag u het account niet opgeven. De syntaxis ziet er als volgt uit:
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>

Hier volgt een voorbeeld voor MSSQL:

```sql
nlserver config -setdblogin:mssql:<login>/"<password>"@<server> -instance:<instance_name> 
```

* login (b.v. account:user), en de server kan in de dataSource knoop van config-&lt;instance_name>.xml- dossier worden gevonden.
* Wachtwoord moet tussen aanhalingstekens &quot;&quot; staan.

