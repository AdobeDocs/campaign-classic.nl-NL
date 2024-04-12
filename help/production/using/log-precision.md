---
product: campaign
title: Logboekprecisie
description: Logboekprecisie
feature: Monitoring
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 2%

---

# Logboekprecisie{#log-precision}



U kunt dit proces op alle modules van Adobe Campaign toepassen om logboekprecisie te verhogen.

Het betekent dat de processen opnieuw moeten worden opgestart met een hoger logbestand.

>[!IMPORTANT]
>
>Deze procedure annuleert de diensten lopend op deze module.

Adobe Campaign kan werken met twee logniveaus:

1. De **Verbose** De modus is het eerste niveau na het standaardniveau. Met de volgende opdracht activeert u deze:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Controleer of de fout daadwerkelijk is opgetreden en start het proces op de normale manier opnieuw:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. De **TraceFilter** , waarmee u het grootste aantal logbestanden kunt opslaan. Het wordt geactiveerd door het volgende bevel:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Als u **trekfilter:&#42;**, worden alle logboektypes geactiveerd: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   De nuttigste logboektypes zijn: **wdbc** (geeft alle SQL-query&#39;s weer), **zeep** (geeft alle SOAP-aanroepen weer), **ldap** (geeft alle LDAP-query&#39;s weer na verificatie), **xtkquery** (toont de lijst van al querydef).\
   U kunt ze afzonderlijk gebruiken (**tracefilter:zeep,wdbc** bijvoorbeeld). U kunt ze ook allemaal activeren en ervoor kiezen bepaalde andere opties uit te sluiten: **-tracefilter:&#42;,!soap**

   Controleer of de fout daadwerkelijk is opgetreden en start het proces op de normale manier opnieuw:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
De logboeken van deze bevelen worden opgeslagen in het logboekdossier van de module.

Hier is een voorbeeld specifiek voor de module van het Web. De overige modules werken zoals hierboven aangegeven.

Voordat u deze opdracht verzendt, controleert u of dit invloed heeft op geen actieve taak:

```
nlserver pdump -who
```

Vervolgens sluit u de module af en start u deze opnieuw in **TraceFilter** modus:

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Een ander voorbeeld:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
De **Tracefile** in de modus kunt u de logbestanden opslaan. In de bovenstaande voorbeelden worden de logbestanden opgeslagen in het dialoogvenster **var/`<instance-name>`/mta_debug.log** en **var/default/web_debug.log** bestanden.

>[!IMPORTANT]
>
Voeg in Windows de optie LD_PRELOAD niet toe. De volgende opdracht volstaat:\
nlserver web -tomcat -verbose -tracefilter:&#42;

Controleer of het probleem zich opnieuw voordoet en start de module opnieuw:

```
nlserver restart web -tomcat -noconsole
```

Alle informatie is beschikbaar in het bestand **/usr/local/neolane/nl6/var/default/log/web.log**.
