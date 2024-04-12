---
product: campaign
title: Werkwijze
description: Werkwijze
feature: Monitoring
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 1%

---

# Werkwijze{#operating-principle}



Technisch gezien is het Adobe Campaign-platform gebaseerd op verschillende modules.

Er zijn veel Adobe Campaign-modules. Sommige werken onophoudelijk, terwijl anderen af en toe worden opgestart om beheertaken uit te voeren (bijvoorbeeld om de databaseverbinding te configureren) of om een terugkerende taak uit te voeren (bijvoorbeeld het consolideren van trackinggegevens).

Er zijn drie typen Adobe Campaign-modules:

* Modules met meerdere instanties: één proces wordt voor alle instanties uitgevoerd. Dit geldt voor de volgende modules: **web**, **syslogd**, **trackinglogd** en **waakhond** (activiteiten van de **config-default.xml** bestand).
* Mono-instance modules: één proces wordt in werking gesteld per instantie. Dit geldt voor de volgende modules: **mta**, **wfserver**, **inMail**, **sms** en **stat** (activiteiten van de **config-`<instance>`.xml** bestand).
* Hulpprogrammamodules: dit zijn modules die soms worden uitgevoerd om incidentele of terugkerende bewerkingen uit te voeren (**opruimen**, **config**, trackinglogboeken downloaden, enz.).

Het beheer van de module wordt uitgevoerd met het opdrachtregelprogramma **nlserver** geïnstalleerd in de **bin** directory van de installatiemap.

De algemene syntaxis van de **nlserver** is als volgt:

**nlserver `<command>``<command arguments>`**

Voor de lijst van beschikbare modules, gebruik **nlserver** gebruiken.

De beschikbare modules worden in de volgende tabel beschreven:

| Opdracht | Beschrijving |
|---|---|
| aliasCleansing | Opsommingswaarden standaardiseren |
| facturering | Het rapport over de systeemactiviteit verzenden naar billing@neolane.net |
| opruimen | Het ontruimen van het gegevensbestand: schrapt verouderde gegevens uit het gegevensbestand en stelt een update van de statistieken in werking die door de optimizer van de gegevensbestandmotor worden gebruikt. |
| config | Serverconfiguratie wijzigen |
| export | Exporteren naar opdrachtregel: hiermee kunt u een exportmodel dat in de Adobe Campaign-clientconsole is gemaakt, naar de opdrachtregel verzenden |
| fileconvert | Een bestand met een ingestelde grootte omzetten |
| import | Importeren naar opdrachtregel: hiermee kunt u een importmodel dat in de Adobe Campaign-clientconsole is gemaakt, naar de opdrachtregel verzenden. |
| inMail | Binnenkomende analyse van e-mail |
| installatieprogramma | Beschikbaarheid van het installatiebestand van de klant |
| javascript | JavaScript-scripts uitvoeren, met toegang tot SOAP API&#39;s. |
| baan | Opdrachtregelverwerking |
| samenvoegen | Formuliersamenvoeging |
| midSourcing | Herstel van leveringsinformatie in de modus voor midsourcing |
| monitor | XML die de status van serverprocessen en geplande taken, door instantie toont. |
| mta | HoofdAgent overdrachtsbericht |
| package | Eenheidspakketbestanden importeren of exporteren |
| spuiten | Status van serverprocessen weergeven |
| voorbereid | Een leveringsactie voorbereiden |
| opnieuw opstarten | Gedeeltelijk opnieuw starten van server |
| runwf | Uitvoering van een werkstroominstantie |
| afsluiten | Volledige systeemuitschakeling |
| sms | Verwerking van SMS-berichten |
| sql | SQL-scriptuitvoering |
| start | Extra start |
| stat | Handhaaft MTA verbindingsstatistieken |
| stoppen | Gedeeltelijke systeemuitschakeling |
| submitda | Een leveringsactie indienen |
| syslogd | Schrijfserver voor logbestanden en traceringen |
| bijhouden | Logbestanden voor bijhouden consolideren en ophalen |
| trackinglogd | Logboek bijhouden bij schrijven en wissen van server |
| waakhond | Instantie voor opstarten en controleren |
| web | Toepassingsserver (HTTP en SOAP) |
| wfserver | Workflowserver |

>[!IMPORTANT]
>
>Er is één laatste module: de tracerings- en relaismodule die is gekoppeld aan de toepassingsserver en die, omwille van de prestaties, via native mechanismen is geïntegreerd in een Apache- of IIS-webserver via een dynamische bibliotheek. Er is geen Adobe Campaign-opdracht waarmee u deze module kunt starten of beheren. U moet daarom de bevelen van de server van het Web zelf gebruiken.

Het gebruik van de module en de syntaxis van zijn parameters worden getoond gebruikend het volgende bevel: **nlserver `[module]` -?**

Voorbeeld:

**nlserver config -?**

```
Usage: nlserver [-verbose:<verbose mode>] [-?|h|H] [-version] [-noconsole]
 [-tracefile:<file>] [-tracefilter:<[type|!type],...>]
 [-instance:<instance>] [-low] [-high] [-queryplans] [-detach]
 [-internalpassword:<[password/newpassword]>] [-postupgrade]
 [-nogenschema] [-force] [-allinstances]
 [-addinstance:<instance/DNS masks[/language]>]
 [-setdblogin:<[dbms:]account[:database][/password]@server>]
 [-monoinstance]
 [-addtrackinginstance:<instance/masks DNS[/databaseId/[/language[/password]]]>]
 [-trackingpassword:<[password][/newpassword]>]
 [-setproxy:<protocol/server:port[/login]>] [-reload]
 [-applyxsl:<schema/file.xsl>] [-filter:<file>]
 [-setactivationkey:<activation key>]
 [-getactivationkey:<client identifier>]
-verbose : verbose mode
-? : display this help message
-version : display version number
-noconsole : no longer display logs and traces on the console
-tracefile : name of trace file to be generated (without extension)
-tracefilter : filter for the traces to be generated e.g.: wdbc,soap,!xtkquery.
-instance : instance to be used (default instance if this option is not present).
-low : start up with low priority
-high : start up with high priority (not recommended)
-queryplans : generate traces with the execution plans of SQL queries.
-detach : detaches the process from its parent (internal option)
-internalpassword : changes the password of the server internal account.
-postupgrade : updates the database following upgrade to a higher version. 
-nogenschema : does not recompute the schemas during database update
-force : updates the database even if this has already been done with the current build 
-allinstances : updates the database over all configured instances
-addinstance : adds a new instance.
-setdblogin : sets the parameters for connection to the database of an instance. The DBMS can be 'oracle', 'postgresql', 'mssql' or 'odbc' (default=postgresql)
-monoinstance : initializes for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
