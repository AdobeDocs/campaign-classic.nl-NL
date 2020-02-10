---
title: Logboekprecisie
seo-title: Logboekprecisie
description: Logboekprecisie
seo-description: null
page-status-flag: never-activated
uuid: 8396bc4f-2954-40bb-b511-61802e60e123
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: c6c39b7d-7bbd-4789-b1ea-b938153e9679
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# Logboekprecisie{#log-precision}

U kunt dit proces op alle modules van de Campagne van Adobe toepassen om logboekprecisie te verhogen.

Het betekent dat de processen opnieuw moeten worden gestart met een hoger logbestand.

>[!CAUTION]
>
>Deze procedure annuleert de diensten lopend op deze module.

Adobe Campagne kan werken met twee niveaus van logbestand:

1. De **modus Uitgebreid** is het eerste niveau na het standaardniveau. Met de volgende opdracht activeert u deze:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Controleer of de fout daadwerkelijk is opgetreden en start het proces op de normale manier opnieuw:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. De **modus TraceFilter** waarmee u het grootste aantal logbestanden kunt opslaan. Het wordt geactiveerd door het volgende bevel:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Als u **tracefilter:*** gebruikt, worden alle logboektypes geactiveerd: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   De nuttigste logboektypes zijn: **wdbc** (toont alle SQL vragen), **zeep** (toont alle vraag van de ZEEP), **ldap** (toont alle vragen LDAP na authentificatie), **xtkquery** (toont de lijst van al querydef).\
   U kunt ze afzonderlijk gebruiken (bijvoorbeeld **tracefilter:soap,wdbc** ). U kunt ze ook allemaal activeren en ervoor kiezen bepaalde andere opties uit te sluiten: **-tracefilter:*,!soap**

   Controleer of de fout daadwerkelijk is opgetreden en start het proces op de normale manier opnieuw:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!CAUTION]
De logboeken van deze bevelen worden opgeslagen in het logboekdossier van de module.

Hier is een voorbeeld specifiek voor de module van het Web. De overige modules werken zoals hierboven aangegeven.

Voordat u deze opdracht verzendt, moet u controleren of de actieve taak hierdoor niet wordt beïnvloed.

```
nlserver pdump -who
```

Vervolgens sluit u de module af en start u deze opnieuw in de **modus TraceFilter** .

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Een ander voorbeeld:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
In de modus **Tracefile** kunt u de logbestanden opslaan. In de bovenstaande voorbeelden worden de logbestanden opgeslagen in de bestanden **var/`<instance-name>`/mta_debug.log** en **var/default/web_debug.log** .

>[!CAUTION]
Voeg in Windows de optie LD_PRELOAD niet toe. De volgende opdracht volstaat:\
nlserver web -tomcat -verbose -tracefilter:*

Controleer of het probleem zich opnieuw voordoet en start de module opnieuw:

```
nlserver restart web -tomcat -noconsole
```

Alle informatie is beschikbaar in het bestand **/usr/local/neolane/nl6/var/default/log/web.log**.
