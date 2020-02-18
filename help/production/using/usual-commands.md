---
title: Gebruikelijke opdrachten
seo-title: Gebruikelijke opdrachten
description: Gebruikelijke opdrachten
seo-description: null
page-status-flag: never-activated
uuid: f06df8c0-d4ec-4d6b-84d5-f46d852388a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 90718075-87a7-4e9a-935b-571010908e79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# Gebruikelijke opdrachten{#usual-commands}

In deze sectie worden de gebruikelijke opdrachten in Adobe Campaign weergegeven.

De opdrachtserver **** is de invoeropdracht voor de gehele Adobe Campagne-toepassing.

Deze opdracht heeft de volgende syntaxis: **nlserver **`<command>`****`<arguments>`****

De parameter **`<command>`** komt overeen met de module.

>[!NOTE]
>
>* In elk geval, kunt u het **-noconsole** argument toevoegen om commentaren te schrappen die worden getoond zodra de modules zijn begonnen.
>* Omgekeerd kunt u het argument **-verbose** toevoegen om meer informatie weer te geven.
>



## Bewaking, opdrachten {#monitoring-commands-}

>[!NOTE]
>
>Om van alle modules een lijst te maken, moet u het **nlserver** bevel gebruiken.

U kunt parameter **-wie** toevoegen om van de lopende verbindingen (gegevensbestand en toepassing) een lijst te maken.

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

Een andere handige opdracht is **Nlserver-monitor**. Hier wordt het XML-bestand met controle vermeld (verkregen in de Adobe Campaign-client of via de **website monitor.jsp** ).

U kunt de parameter toevoegen **-mist** om van de afwezige modules (fout in modules, modules sluiten enz.) een lijst te maken

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
>**`<instance>`** komt overeen met de naam van de instantie zoals die is ingevoerd in de configuratiebestanden of **standaard** voor monoinstantiemodules.

## Afsluiten van services {#shut-down-services}

Als u Adobe Campagne wilt stoppen, gebruikt u een van de volgende opdrachten:

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

* Als dat niet het geval is, gaat u naar het Adobe Campaign-account:

   ```
   nlserver shutdown 
   ```

## Herstartservices {#restart-services}

Op dezelfde manier kunt u een van de volgende opdrachten gebruiken om Adobe Campaign opnieuw te starten:

* Als u toegang hebt tot de hoofdmap of beheerder:

   * In Linux: /etc/init.d/nlserver6 start

      >[!NOTE]
      >
      >Vanaf 20.1 raden we u aan in plaats daarvan de volgende opdracht te gebruiken (voor Linux): **systemctl start nlserver**

   * In Windows: netwerkbeginserver6

* Anders in het Adobe Campaign-account: **nlserver watchdog -svc -noconsole**

## Het configuratiebevel {#the-config-command}

Met de **opdracht config** kunt u de serverconfiguratie beheren, inclusief de herconfiguratie van de databaseverbinding.

Gebruik het **config** bevel van het uitvoerbare dossier **nlserver** met de **-vastgestelde parameter** .

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Voer het wachtwoord in.

Het **interne** wachtwoord wijzigen: **nlserver config -internalpassword**

>[!CAUTION]
>
>Als u zich wilt aanmelden met de **interne** id, moet u vooraf een wachtwoord hebben gedefinieerd. Zie [deze sectie](../../installation/using/campaign-server-configuration.md#internal-identifier)voor meer informatie.

>[!NOTE]
>
>* In het algemeen, in plaats van het wijzigen van de configuratiedossiers door hand, kunt u het **config** bevel gebruiken
>* Als u de lijst met parameters wilt ophalen, gebruikt u de **-?** parameter: Configuratie **nlserver -?**
>* In het geval van een Oracle-database moet u de account niet opgeven. De syntaxis ziet er als volgt uit:
>
>  
nlserver config -setdblogin:Oracle:test6@dbserver


