---
product: campaign
title: Gebruikelijke opdrachten
description: Gebruikelijke opdrachten
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 3%

---

# Gebruikelijke opdrachten{#usual-commands}



In deze sectie worden de gebruikelijke opdrachten in Adobe Campaign weergegeven.

De opdracht **nlserver** is de invoeropdracht voor de hele Adobe Campaign-toepassing.

Deze opdracht heeft de volgende syntaxis: **nlserver **`<command>`****`<arguments>`****

De parameter **`<command>`** komt overeen met de module.

>[!NOTE]
>
>* In elk geval kunt u de opdracht **-noconsole** argument om opmerkingen te verwijderen die worden weergegeven wanneer de modules zijn gestart.
>* Omgekeerd kunt u het argument toevoegen **-verbose** voor meer informatie.
>


## Bewaking, opdrachten {#monitoring-commands-}

>[!NOTE]
>
>Om van alle modules een lijst te maken, moet u gebruiken **nlserver pdump** gebruiken.

U kunt de parameter toevoegen **-who** om een lijst weer te geven van de lopende verbindingen (database en toepassing).

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

Een andere handige opdracht is **nlserver-monitor**. Het bevat een lijst met XML-controlebestanden (verkregen in de Adobe Campaign-client of via de **monitor.jsp** webpagina).

U kunt de parameter toevoegen **-missing** om de ontbrekende modules (fout in modules, modules gesloten, enz.) op te nemen

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
>**`<instance>`** overeenkomt met de naam van de instantie zoals die is ingevoerd in de configuratiebestanden, of **default** voor mono-instantiemodules.

## Afsluiten van services {#shut-down-services}

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

## Herstartservices {#restart-services}

Op dezelfde manier kunt u een van de volgende opdrachten gebruiken om Adobe Campaign opnieuw te starten:

* Als u toegang hebt tot de hoofdmap of beheerder:

   * In Linux: /etc/init.d/nlserver6 start

      >[!NOTE]
      >
      >Vanaf 20.1 raden we u aan in plaats daarvan de volgende opdracht te gebruiken (voor Linux): **systeemserver voor opstarten**

   * In Windows: netwerkbeginserver6

* Anders, in de rekening van Adobe Campaign: **nlserver watchdog -svc -noconsole**

## Het configuratiebevel {#the-config-command}

De **config** Met deze opdracht kunt u de serverconfiguratie beheren, inclusief de herconfiguratie van de databaseverbinding.

Gebruik de **config** de **nlserver** uitvoerbaar bestand met de **-setdblogin** parameter.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Voer het wachtwoord in.

Als u het dialoogvenster **internal** wachtwoord: **nlserver config - intern wachtwoord**

>[!IMPORTANT]
>
>Als u zich wilt aanmelden met de **Intern** id, moet u vooraf een wachtwoord hebben bepaald. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier) voor meer informatie.

>[!NOTE]
>
>* In het algemeen kunt u in plaats van de configuratiebestanden handmatig te wijzigen de opdracht **config** command
>* Als u de lijst met parameters wilt ophalen, gebruikt u de opdracht **-?** parameter: **nlserver config -?**
>* In het geval van een gegevensbestand van het Oracle, moet u niet de rekening specificeren. De syntaxis ziet er als volgt uit:
>
>  nlserver config -setdblogin:Oracle:test6@dbserver
