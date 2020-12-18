---
solution: Campaign Classic
product: campaign
title: Gebruikelijke opdrachten
description: Gebruikelijke opdrachten
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 3%

---


# Gebruikelijke opdrachten{#usual-commands}

In deze sectie worden de gebruikelijke opdrachten in Adobe Campaign weergegeven.

De opdracht **nlserver** is de invoeropdracht voor de hele Adobe Campaign-toepassing.

Deze opdracht heeft de volgende syntaxis: **nlserver **`<command>`****`<arguments>`****

De parameter **`<command>`** beantwoordt aan de module.

>[!NOTE]
>
>* In elk geval, kunt u **-noconsole** argument toevoegen om commentaren te schrappen die worden getoond zodra de modules zijn begonnen.
>* Omgekeerd, kunt u het argument **-verbose** toevoegen om meer informatie te tonen.

>



## Bewaking, opdrachten {#monitoring-commands-}

>[!NOTE]
>
>Als u alle modules wilt weergeven, moet u de opdracht **nlserver pdump** gebruiken.

U kunt de parameter **-who** toevoegen om van de lopende verbindingen (gegevensbestand en toepassing) een lijst te maken.

```
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

Een andere handige opdracht is **nlserver monitor**. Het bevat het XML-bestand voor controle (verkregen in de Adobe Campaign-client of via de webpagina **monitor.jsp**).

U kunt de parameter **-missing** toevoegen om van de ontbrekende modules (fout in modules, modules sluiten, enz.) een lijst te maken

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Dit komt overeen met de modules met automatisch opstarten, maar die nog niet zijn gestart.

## Opdrachten voor het starten van modules {#module-launch-commands}

De syntaxis voor opstartmodules heeft nog steeds de volgende indeling:

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** komt overeen met de naam van de instantie zoals die is ingevoerd in de configuratiebestanden of  **** standaardinstellingen voor monoinstantiemodules.

## Afsluitservices {#shut-down-services}

Als u de Adobe Campaign-services wilt stoppen, gebruikt u een van de volgende opdrachten:

* Als u toegang hebt tot de hoofdmap of beheerder:

   * In Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >Vanaf 20.1 raden we u aan in plaats daarvan de volgende opdracht te gebruiken (voor Linux): **systemctl stop nlserver**

   * In Windows:

      ```
      net stop nlserver6
      ```

* Zo niet, dan op de Adobe Campaign-account:

   ```
   nlserver shutdown 
   ```

## Services {#restart-services} opnieuw starten

Op dezelfde manier kunt u een van de volgende opdrachten gebruiken om Adobe Campaign opnieuw te starten:

* Als u toegang hebt tot de hoofdmap of beheerder:

   * In Linux: /etc/init.d/nlserver6 start

      >[!NOTE]
      >
      >Vanaf 20.1 raden we u aan in plaats daarvan de volgende opdracht te gebruiken (voor Linux): **systemctl start nlserver**

   * In Windows: netwerkbeginserver6

* Anders, in de rekening van Adobe Campaign: **nlserver watchdog -svc -noconsole**

## Het configuratiebevel {#the-config-command}

Met de opdracht **config** kunt u de serverconfiguratie beheren, inclusief de herconfiguratie van de databaseverbinding.

Gebruik **config** bevel van **nlserver** uitvoerbaar dossier met **-setdblogin** parameter.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Voer het wachtwoord in.

Het **internal** wachtwoord wijzigen: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Als u zich wilt aanmelden met de **Internal**-id, moet u vooraf een wachtwoord hebben gedefinieerd. Raadpleeg [deze sectie](../../installation/using/campaign-server-configuration.md#internal-identifier) voor meer informatie.

>[!NOTE]
>
>* In het algemeen, in plaats van het wijzigen van de configuratiedossiers door hand, kunt u **config** bevel gebruiken
>* Om de lijst van parameters te krijgen, gebruik **-?** parameter:  **nlserver config -?**
>* In het geval van een Oracle-database mag u het account niet opgeven. De syntaxis ziet er als volgt uit:

>
>  
nlserver config -setdblogin:Oracle:test6@dbserver

