---
product: campaign
title: Het serverconfiguratiebestand
description: Het serverconfiguratiebestand
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '7957'
ht-degree: 5%

---

# Het serverconfiguratiebestand{#the-server-configuration-file}

![](../../assets/v7-only.svg)

De algemene configuratie van Adobe Campaign wordt gedefinieerd in het gedeelte **serverConf.xml** bestand, bevindt zich in het **conf** directory van de installatiemap. In deze sectie worden alle verschillende knooppunten en parameters van de **serverConf.xml** bestand.

>[!NOTE]
>
>De server-zijconfiguraties kunnen slechts door Adobe voor plaatsingen worden uitgevoerd die door Adobe worden ontvangen. Voor meer informatie over de verschillende implementaties raadpleegt u de [Hostmodellen](../../installation/using/hosting-models.md) van [deze pagina](../../installation/using/capability-matrix.md). De installatie- en configuratiestappen voor gehoste en hybride modellen worden in deze [sectie](../../installation/using/hosting-models.md).

De eerste parameters bevinden zich in de **gedeeld** knooppunt. Deze zijn gerelateerd aan het exemplaar. Deze worden mogelijk door alle nlserver-opdrachten gebruikt (nlserver, nlserver wfserver, enz.). De andere secties zijn verwant aan een specifiek nlserver sub-bevel.

**Gedeelde parameters**

* [verificatie](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [ims](#ims)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [module](#module)
* [toezicht](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [xtkJobs](#xtkjobs)

**Andere parameters**

* [archivering](#archiving)
* [inMail](#inmail)
* [interactief](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [gelijnd](#pipelined)
* [repareren](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [bijhouden](#tracking)
* [trackinglogd](#trackinglogd)
* [web](#web)
* [wfserver](#wfserver)

## verificatie {#authentication}

Hier zijn de verschillende parameters van **verificatie** knooppunt:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> checkIPConsistent<br /> </td> 
   <td> Controleren van IP-adressen inschakelen.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> Standaardidentificatiemodus.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'nl'<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> Time-out van lange sessies in seconden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1296000<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Time-out beveiligingstoken in seconden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Cacheduur: cache van sessiegegevens in seconden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Time-out sessie in seconden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

Hier zijn de verschillende parameters van **verificatie > XTK** knooppunt:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> internalPassword<br /> </td> 
   <td> Wachtwoord voor interne account.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> Veilige zone interne rekening: zone met bevoegdheden voor de interne rekening.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Hier zijn de verschillende parameters van **dataStore** knooppunt. Hier worden de gegevensbronnen van de server gedefinieerd.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportDirectory<br /> </td> 
   <td> Exportmap: pad van doelmap voor de geëxporteerde gegevens.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxDirectories<br /> </td> 
   <td> Extra sandboxmappen: andere paden die in de sandbox moeten worden toegevoegd (gescheiden door coma's).<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '/home/customer/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Vertraging bij verlopen van formuliercache: onderbreking in seconden waarna een cachevermelding ongeldig wordt gemaakt. O betekent dat cachemarangen alleen worden vernieuwd op het moment van publicatie.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> gastheren<br /> </td> 
   <td> DNS-maskers: lijst met DNS-maskers die in deze instantie worden gebruikt (gescheiden door komma's), kan * en ? patronen).<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '*'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> Vertraging bij JSSP-cache van interactie: onderbreking in seconden waarna een cachevermelding ongeldig wordt gemaakt. Een negatieve waarde betekent dat de cache altijd ongeldig wordt gemaakt. '0', lege of ongeldige waarden worden beschouwd als 60.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Instantietaal (opsomming). Mogelijke waarden zijn 'fr_FR' (Français), 'en_GB' (English (UK)), 'en_US' (English (US)), 'de_DE' (Deutsch) en 'ja_JP' (Japans).<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'nl_NL'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> Map uploaden: pad van doelmap voor de geüploade gegevens.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> Geautoriseerde bestanden die moeten worden gedownload, gescheiden door ','. De tekenreeks moet een geldige, reguliere Java-expressie zijn. Zie <a href="file-res-management.md" target="_blank">Uploadbare bestanden beperken</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Bewaar geheimen in Vault: Gebruik Hashicorp Vault.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Secret path in Vault<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '/v1/geheime/campagne/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Het lokale pad van het bestand dat de vault-token bevat. $(HOME) kan in dit pad worden gebruikt (maar niet andere env-variabelen).<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Hashicorp Vault URL <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Geldigheidsperiode van weergavecache: onderbreking in seconden waarna een cachevermelding ongeldig wordt gemaakt. Een negatieve waarde betekent dat de cache altijd ongeldig wordt gemaakt. '0', lege of ongeldige waarden worden beschouwd als 60.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> XPath van de werkmap.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> workingDirectory : XPath van de werkmap. Standaard: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

Hier zijn de verschillende parameters van **dataStore > proxyAdjust** knooppunt. URL&#39;s die overeenkomen met de reguliere expressie, worden opnieuw gegenereerd op basis van de URL die is gedefinieerd in urlBase.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> urlBase<br /> </td> 
   <td> Gebaseerd op gebruik bij het genereren van externe URL's. Voorbeeld: https://server.domain.com<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Gewone expressie die overeenkomt met URL's. Voorbeeld: http://server\.lan\.net.*<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

Hier zijn de verschillende parameters van **dataStore > dataSource** knooppunt.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Naam gegevensbron<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> default<br /> </td> 
  </tr> 
 </tbody> 
</table>

In de **dataStore > dataSource > dbcnx** knoop, vorm de verbindingsmontages:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NChar<br /> </td> 
   <td> Unicode-opslag<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Werkruimte<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> gecodeerd<br /> </td> 
   <td> Gecodeerd wachtwoord<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> aanmelden<br /> </td> 
   <td> Account<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Wachtwoord<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> provider<br /> </td> 
   <td> Type (opsomming). Mogelijke waarden zijn 'Oracle', 'MSSQL' (Microsoft SQL Server), 'PostgreSQL' (PostgreSQL), 'Teradata', 'DB2', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA' (SAP HANA), 'RedShift' (Amazon Redshift), 'ODBC' (ODBC (Sybase ASE, Sybase IQ)), 'Relay' (HTTP relay aan verre gegevensbestand).<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'Oracle'<br /> </td> 
  </tr> 
  <tr> 
   <td> server<br /> </td> 
   <td> Server<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> tijdzone<br /> </td> 
   <td> Tijdzone: zie <a href="../../installation/using/time-zone-management.md" target="_blank">Tijdzonebeheer</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> Unicode-gegevens in de database<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> Datumvelden met tijdzone: zie <a href="../../installation/using/time-zone-management.md" target="_blank">Tijdzonebeheer</a>.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

In de **dataStore > dataSource > sqlParams** knoop, vorm de SQL parameters:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> funcPrefix<br /> </td> 
   <td> Functievoorvoegsel<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
 </tbody> 
</table>

In de **dataStore > dataSource > pool** knoop, vorm de parameters van bijbehorende verbindingspool:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> liveTestDelaySec<br /> </td> 
   <td> Vertraging tussen geldigheidscontroles van de verbinding.<br /> </td> 
   <td> Kort<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Aantal vrije verbindingen die in de pool worden gehouden.<br /> </td> 
   <td> Kort<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Maximum aantal toegestane verbindingen voordat een nieuwe verbinding wordt geweigerd. Zie dit <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">technote</a>.<br /> </td> 
   <td> Kort<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Maximale inactieve tijd van verbinding. 0 staat voor standaardwaarde.<br /> </td> 
   <td> Kort<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Hier zijn de verschillende parameters van **dataStore > virtualDir** knooppunt. Dit is de configuratie van de virtuele folder aan echte folderafbeelding.

Raadpleeg voor meer informatie [Openbare middelen beheren](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Naam van de virtuele map <br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> pad<br /> </td> 
   <td> Volledig pad van de feitelijke map<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
 </tbody> 
</table>

Hier is de standaardconfiguratie:

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

Hier zijn de verschillende parameters van **dataStore > preprocessCommand** knooppunt. Dit zijn de geoorloofde opdrachten voor het voorbewerken van de workflowactiviteit &#39;Bestand laden&#39;.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> Opdrachtregel <br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Label van opdrachtregel<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Naam opdrachtregel<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
 </tbody> 
</table>

Hier is de standaardconfiguratie:

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

Hier zijn de verschillende parameters van **dnsConfig** (DNS-configuratie).

Raadpleeg voor meer informatie deze [sectie](../../installation/using/configuring-campaign-server.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Domeinnaam: standaarddomeinnaam. Gebruikt door het bevel van de HELO SMTP. Gebruikt standaard de netwerkparameters van de eerste netwerkinterface die in Windows is gedeclareerd; of parseert de file/etc/resolv.conf onder Linux (domein of zoekingang). <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS-server: door komma's gescheiden lijst met domeinnaamservers (DNS). Zie de onderstaande opmerking.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> opnieuw proberen<br /> </td> 
   <td> Aantal pogingen voor een DNS vraag opnieuw.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Time-out in milliseconden voor een DNS-query.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Opmerking over **nameSevers**: gebruikt standaard het netwerk
>parameters van de eerste netwerkinterface die in Windows is gedeclareerd
>niet gedefinieerd in UNIX. Definieert de domeinnaamservers (DNS)
>gebruikt door MTA om de Uitwisseling van de Post te krijgen voor
>een domein.
>
>Als deze waarde niet wordt bepaald, zoekt MTA deze informatie in de configuratie van het gastheernetwerk. Als verscheidene DNS mogelijk zijn, moeten de verschillende DNS adressen door een komma worden gescheiden (voorbeeld: 212.15.207.1.212.15.207.2). Als uw leveringsserver verscheidene netwerkinterfaces heeft, is de DNS lijst die door MTA wordt gebruikt eerste. In dit geval raden we u aan de **nameServer** om dubbelzinnigheid te voorkomen.

>[!CAUTION]
>
>Als uw configuratie van de netwerkgastheer DHCP gebruikt, zal MTA niet de DNS lijst vinden die door DHCP wordt verstrekt. In dit geval, adviseren wij specificerend de DNS lijst in de netwerkparameters van het de controlepaneel van Vensters.

## exec {#exec}

Hier zijn de verschillende parameters van **exec** node (opdrachtuitvoering).

Raadpleeg voor meer informatie [Toegestane externe opdrachten beperken](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> blacklistFile<br /> </td> 
   <td> Pad naar het bestand met de opdrachten die aan de lijst van gewenste personen moeten worden toegevoegd. <br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> user<br /> </td> 
   <td> Opdrachten uitvoeren als een andere gebruiker.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Hier zijn de verschillende parameters van **htmlToPdf** knooppunt. Dit is de configuratie van de service voor het converteren van webpagina&#39;s naar PDF-documenten.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> Opdrachtregel voor het uitvoeren van de conversie (in de modus 'Andere').<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max. aantal conversieprocessen dat op een computer tegelijkertijd is toegestaan.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> mode<br /> </td> 
   <td> Gereedschap voor conversie. Mogelijke waarden zijn: phantomjs, wkhtmltopdf, andere, uitgeschakeld<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Time-out voor conversie: maximale conversietijd in seconden. Buiten deze drempelwaarde wordt het conversieproces gestopt en een fout opgetreden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> uitgebreid<br /> </td> 
   <td> Modus Uitgebreid: begin in uitgebreide wijze om mogelijke fouten te diagnostiseren.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Vertraging bij wachten op een proces: vertraging in seconden, wanneer alle processen tegelijkertijd worden gebruikt en wanneer het wachten op een proces om omhoog vrij te maken. Als deze vertraging wordt overschreden, wordt de omzetting tegengehouden en een fout wordt opgeheven. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Voorbeeld voor fantomjs:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## ims {#ims}

Hier zijn de verschillende parameters van **ims** knooppunt. Dit is de configuratie voor Campagne die met een andere dienst verbindt gebruikend [IMS](../../integrations/using/about-adobe-id.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> authIMSClientId<br /> </td> 
   <td> Client-id<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> Geheime sleutel (gecodeerd in AES)<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> Autorisatiecode (gecodeerd in AES)<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSEndpoint<br /> </td> 
   <td> URL IMS-server<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'https://ims-na1.adobelogin.com'<br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientId<br /> </td> 
   <td> Client-id voor technische account<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> Key technisch-accountgeheim (gecodeerd in AES)<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAId<br /> </td> 
   <td> Technisch account-id<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAPrivateKey<br /> </td> 
   <td> Persoonlijke sleutel technische account (gecodeerd in AES)<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

Hier zijn de verschillende parameters van **javaScript** knooppunt. Dit is de configuratie van de JavaScript-interpreter.

Raadpleeg voor meer informatie de [Rapportagedocumentatie](../../reporting/using/actions-on-reports.md#memory-allocation).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxMB<br /> </td> 
   <td> Maximale grootte in megabytes voordat de afvalophaler wordt uitgevoerd.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> Grootte van elk stapelsegment in kilo-octetten. Dit is een afstemmingsparameter voor geheugenbeheer die de meeste gebruikers niet zouden moeten aanpassen. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

Hier zijn de verschillende parameters van **mailExchanger** knooppunt. Dit is de configuratie van de server SMTP.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mxAddress<br /> </td> 
   <td> SMTP-server: IP adres van server SMTP voor de overdracht van e-mails.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> De haven van TCP van server SMTP die voor de E-mailoverdracht wordt gebruikt.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## module {#module}

Hier zijn de verschillende parameters van **module** knooppunt. Dit is de configuratie voor de namespaces beperkingsmodule xtk.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> defaultNameSpace<br /> </td> 
   <td> Standaardnaamruimte die wordt gebruikt bij het maken van een nieuwe entiteit.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## toezicht {#monitoring}

Hier zijn de verschillende parameters van **toezicht** knooppunt. Dit is de configuratie van de controledienst.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPreparationJobsSec<br /> </td> 
   <td> Maximale bereidingstijd: duur in seconden waarna een leveringsactie niet langer moet worden voorbereid.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> Unix script uitgevoerd door de bewakingsservice.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> Het manuscript van vensters dat door de controledienst moet worden uitgevoerd.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

Hier zijn de verschillende parameters van **ooconv** knooppunt. Dit is de configuratie van de documentconversieserver.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxConversions<br /> </td> 
   <td> Maximum aantal omzettingen die een server OpenOffice wordt toegestaan uit te voeren. Buiten dit getal wordt de server opnieuw gestart.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Maximale inactieve tijd van de OpenOffice-server voordat deze geforceerd wordt gesloten.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Het interval van havens waarop de servers OpenOffice luisteren.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL van de documentconversieserver.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Hier zijn de verschillende parameters van **proxyConfig** knooppunt. Dit is de configuratie van proxyparameters.

Raadpleeg voor meer informatie [Configuratie proxyverbinding](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabled<br /> </td> 
   <td> Gebruik een proxyserver.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> override<br /> </td> 
   <td> Uitzonderingen: lijst van adressen waarvoor proxyparameters worden genegeerd.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'localhost*' <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> Unieke proxyserver: gebruik de zelfde configuratie voor alle types van volmacht.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP-proxy / Veilige proxy {#http-proxy---secure-proxy-}

In de **proxyConfig > HTTP-proxy / Secure-proxy** knoop, vorm de volgende parameters.

Raadpleeg voor meer informatie [Configuratie proxyverbinding](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> adres<br /> </td> 
   <td> Adres van proxyserver<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> aanmelden<br /> </td> 
   <td> Aanmelden voor verbinding met proxyserver<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> password<br /> </td> 
   <td> Wachtwoord voor verbinding met proxyserver<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> poort<br /> </td> 
   <td> Poort proxyserver<br /> </td> 
   <td> Kort<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

Hier zijn de verschillende parameters van **threadPool** knooppunt.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxThreadCount<br /> </td> 
   <td> Maximum aantal draden in pool. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Hier zijn de verschillende parameters van **urlPermission** knooppunt. Dit is de lijst met URL&#39;s waartoe de JavaScript-code toegang heeft.

Lijst met domeinen en reguliere expressies die aangeven of een URL die in de JavaScript-code wordt aangetroffen, door de Adobe Campaign-server kan worden gebruikt of niet.

Als de URL niet kan worden gevonden, wordt de standaardactie uitgevoerd volgens de opgegeven standaardmodus.

Raadpleeg voor meer informatie [Uitgaande verbindingsbeveiliging](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> action<br /> </td> 
   <td> Standaardactie als de URL niet in de geoorloofde lijst (opsomming) staat. Mogelijke waarden zijn 'ignore' (autoriseren zonder waarschuwingsbericht, dit vereist het uitschakelen van de beveiliging), 'warn' (autoriseer en geef een waarschuwingsbericht op) en 'deny' (belemmert toegang tot de URL).<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> ontkennen<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Foutopsporingsspoor van het URL-selectiemechanisme: geeft extra berichten tijdens het URL-verificatieproces uit.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### url {#url}

Voeg voor elke URL een **url** knooppunt met de volgende parameters:

Raadpleeg voor meer informatie [Uitgaande verbindingsbeveiliging](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dnsSuffix<br /> </td> 
   <td> Domeinnaam, of bovenliggende domein, waarop de URL betrekking heeft: het volledige of gedeeltelijke domein van URL te verifiëren, om de controle te versnellen. De URL wordt alleen geverifieerd met betrekking tot de reguliere expressie als het domein ervan dsnSuffix bevat.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Gewone expressie voor het verfijnen van validatie van URL's die tot dit domein behoren: reguliere expressie die door de URL moet worden geverifieerd, voor het geval deze overeenkomt met dnsSuffix.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
 </tbody> 
</table>

Indien een record voldoet **dnsSuffix** maar niet **urlRegEx**, wordt de volgende record onderzocht.

Bijvoorbeeld, om toegang tot alle URLs van het domein business.com te verlenen, kunnen wij twee verslagen bepalen:

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.&#42;&quot;

en

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.&#42;&quot;

Hier is de standaardconfiguratie:

```
<url dnsSuffix="api.omniture.com" urlRegEx="https://api.omniture.com/genesis/i/3.1.*"   />
<url dnsSuffix="omniture.com" urlRegEx="https://api[1-5].omniture.com/genesis/i/3.1.*"  />
<url dnsSuffix="marketing.adobe.com"                     urlRegEx="https://.*"                                    />
<url dnsSuffix="fcm.googleapis.com"                      urlRegEx="https://fcm.googleapis.com/fcm/send.*"       />
<url dnsSuffix="graph.facebook.com"                      urlRegEx="https://.*"                                    />
<url dnsSuffix="api.line.me"                             urlRegEx="https://api.line.me/.*"                      />
<url dnsSuffix="api.twitter.com"                         urlRegEx="https://api.twitter.com/1.1.*"              />
<url dnsSuffix="adobeid-na1.services.adobe.com"          urlRegEx="https://.*"                                    />
<url dnsSuffix="adobeid-na1-stg1.services.adobe.com"     urlRegEx="https://.*"                                    />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/jssp/dm/renderingSeed.jssp" />
<url dnsSuffix="deliverability.neolane.net"              urlRegEx="https://deliverability.neolane.net/nl/jsp/soaprouter.jsp" />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

Hier zijn de verschillende parameters van **xtkJobs** knooppunt. Dit is de configuratie van de servertaken.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Vernieuwingsperiode voor serververwerking (in ms) voor geheugenstatus.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## archivering {#archiving}

Hier zijn de verschillende parameters van **archivering** knooppunt. Dit is de configuratie van de uitgevoerde archiveringsbewerkingen op de achtergrond.

Raadpleeg voor meer informatie [E-mailarchivering activeren (op locatie)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> verwervingLimit<br /> </td> 
   <td> Aantal te verwerken EML's<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> Archiveringsstrategie voor verzonden berichten (opsomming). Mogelijke waarden zijn '0' (geen archivering) en '1' (het archiveren van verzonden berichten naar een SMTP-server).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Opstartparameters<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisch starten<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> Grootte van een gecomprimeerd archief: max. aantal bestanden in een gecomprimeerd archief.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Compressie-indeling die wordt gebruikt tijdens archivering (opsomming). Mogelijke waarden zijn '0' (geen compressie) en '1' (verzonden berichten comprimeren met de ZIP-indeling).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> Vertraging voordat onverwerkte e-mails automatisch worden gearchiveerd: aantal dagen voordat onverwerkte e-mails worden gearchiveerd.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id van JavaScript die moet worden uitgevoerd wanneer het proces wordt gestart.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Vertraging (in seconden) tussen elke update-gebeurtenis.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tijdstip van de dag waarop het proces automatisch opnieuw wordt gestart. Zie <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisch proces opnieuw opstarten</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Aantal dagen voordat onverwerkte e-mails worden verwijderd.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioriteit aan het begin. Modules met lage prioriteit worden eerst gestart en voor het laatst gestopt. De module syslogd moet daarom prioriteit 0 hebben.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> Doel archiveren<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> Ondersteuning voor SMTPS activeren: Hiermee activeert u de levering van e-mailberichten in de veilige modus (STARTTLS/SMTPS) wanneer deze worden ondersteund door de externe server.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Aantal verbindingen met de archiverende server SMTP.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> Lijst met door komma's gescheiden DNS-namen of IP-adressen van te gebruiken SMTP-relais. <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> IP-poort van SMTP-server.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Hier zijn de verschillende parameters van **inMail** knooppunt. Dit is de configuratie van de binnenkomende e-mailbeheermodule.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Opstartparameters<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisch starten<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> Instantienaam controleren: Indien true, moet de naam van de Adobe Campaign-instantie in de Message-ID-headers gelijk zijn aan de huidige instantie. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Adres doorsturen: standaard e-mailadres wordt niet verwerkt door een regel. <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> Adres voor fouten: standaardadres dat wordt gebruikt om ongeldige e-mails over te brengen (onjuiste MIME-codering). <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Berichtgrootte negeren: wordt gebruikt om de grootte van een bericht te negeren dat door POP3 servers is teruggekeerd. In dit geval verwacht de module een '.' aan het einde van de berichten. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Leesperiode bericht: de stemfrequentie van de berichtrij.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id van JavaScript die moet worden uitgevoerd wanneer het proces wordt gestart.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Maximumaantal bij te werken logboeken: bepaalt het maximumaantal logboekberichten in geheugen te houden alvorens het gegevensbestand bij te werken.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Maximumaantal berichten dat tijdens POP3-sessie kan worden gelezen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Sessieduur: maximale duur van berichtverwerkingssessie.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3-stemperiode<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Wachtrijgrootte voor leesberichten<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Communicatie onderbreking met POP3 server. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tijdstip van de dag waarop het proces automatisch opnieuw wordt gestart. Zie <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisch proces opnieuw opstarten</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> Herlaadfrequentie database voor te pollen accounts.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioriteit aan het begin. Modules met lage prioriteit worden eerst gestart en voor het laatst gestopt. De module syslogd moet daarom prioriteit 0 hebben.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

In de **inMail > msgDump** knoop, vorm de volgende parameters. Dit is de configuratie van de stortplaats van verwerkte berichten.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> stortplaats<br /> </td> 
   <td> Sla alle binnenkomende berichten op in tekstopmaak. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> Berichtstortpad.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '/tmp/inMail'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactief {#interactiond}

Hier zijn de verschillende parameters van **interactief** knooppunt. Dit is de configuratie van schrijven daemon voor binnenkomende gebeurtenissen van de Interactie.

Raadpleeg voor meer informatie [Interactie - Gegevensbuffer](../../installation/using/interaction---data-buffer.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Opstartparameters<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisch starten<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Max. aantal tekens dat in het gedeelde geheugen is opgeslagen voor aanroepgegevens.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id van JavaScript dat moet worden uitgevoerd wanneer het proces wordt gestart<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEntry<br /> </td> 
   <td> Max. aantal gebeurtenissen dat is opgeslagen in het gedeelde geheugen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Maximumaantal in aanmerking komende aanbiedingen dat recht na voorstellen wordt gesorteerd en dat voor statistieken wordt opgeslagen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tijdstip van de dag waarop het proces automatisch opnieuw wordt gestart. Zie <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisch proces opnieuw opstarten</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioriteit aan het begin. Modules met lage prioriteit worden eerst gestart en voor het laatst gestopt. De module syslogd moet daarom prioriteit 0 hebben.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> De duur van de samenvoeging in seconden voor de statistieken van de reactietijd. 0 betekent dat de statistische opslag is gedeactiveerd.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max. aantal tekens dat in het gedeelde geheugen is opgeslagen om personen te identificeren.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

Hier zijn de verschillende parameters van **mta** knooppunt. Dit is de configuratie van leveringsagenten.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Opstartparameters<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '-tracefilter:nlmta' <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisch starten<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> Pad van verzonden e-mailberichten opslaan: als niet leeg, het pad waar alle bronbestanden van verzonden e-mails worden opgeslagen. <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Map dumpen:iIf not empty, copy MIME envelopes of sent mail messages in this directory. Wordt gebruikt voor het oplossen van problemen. <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMS<br /> </td> 
   <td> DNS-vertraging voor querylogbestanden: tijd in milliseconden om de logbestanden weer te geven.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Frequentie foutstatistieken: tijd tussen de productie van statistieken en de opslag in de database. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id van JavaScript die moet worden uitgevoerd wanneer het proces wordt gestart.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Genereer foutstatistieken en sla deze op in de database.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Geef het niveau van logberichten weer. Prioriteitsniveau van de logs die in de database zijn geschreven. De berichten van het logboek die door MTA worden geproduceerd worden niet altijd geschreven in het gegevensbestand. Met deze parameter, kunt u het niveau bepalen waarvan u van mening bent dat een bericht in het gegevensbestand moet worden geschreven. Als u niveau 2 bepaalt, worden de berichten van niveau 1 en 0 ook geschreven, terwijl als u niveau 1 bepaalt, slechts worden de berichten van niveau 1 en 0 geschreven. Mogelijke waarden zijn: 0 (fouten), 1 (waarschuwing), 2 (info)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Maximale geheugengrootte (in MB) die een mta-proces kan gebruiken. Boven deze limiet wordt het proces opnieuw gestart, zodat het gebruikte geheugen naar het systeem wordt vrijgegeven.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Verbindingsdrempel waarmee rekening moet worden gehouden. Er worden geen foutstatistieken gegenereerd voor een bepaald pad als het totale aantal verbindingen voor de door errorPeriodSec opgegeven periode strikt onder de drempel ligt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Foutdrempel waarmee rekening moet worden gehouden: Er worden geen foutstatistieken gegenereerd voor een bepaald pad als het totale aantal fouten voor de door errorPeriodSec opgegeven periode strikt onder de drempel ligt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Berichtdrempel waarmee rekening moet worden gehouden. Er worden geen foutstatistieken gegenereerd voor een bepaald pad als het totale aantal berichten dat gedurende de door errorPeriodSec opgegeven periode wordt verzonden, strikt onder de drempel ligt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Meldingsrelais: HostName:Haven die aan relaisberichten wordt gebruikt.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tijdstip van de dag waarop het proces automatisch opnieuw wordt gestart. Zie <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisch proces opnieuw opstarten</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Vertraging voordat gearchiveerde e-mailberichten worden verwijderd: aantal dagen voordat gearchiveerde e-mailberichten in de map die in dataLogPath is opgegeven, worden gewist.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> Verloren berichten opnieuw proberen: delen van leveringen worden opnieuw geprobeerd als het onderliggende proces dood is.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioriteit aan het begin. Modules met lage prioriteit worden eerst gestart en voor het laatst gestopt. De module syslogd moet daarom prioriteit 0 hebben.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> Schakel het handtekeningmechanisme in. Hierdoor wordt de beveiliging bij het bijhouden van koppelingen in e-mail verbeterd.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Adres van de server van de leveringsstatistiek, die als wordt gegeven 
    &lt;dns or="" ip=""&gt; 
      <code>[</code>: 
     &lt;port&gt; 
       <code>]</code>. Zie 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Coördinaten van de statistiekserver</a>. 
      <br /> 
     </td> 
   <td> Tekenreeks<br /> </td> 
   <td> Indien niet gedefinieerd, is de standaardpoort 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> statServerTLSSupport<br /> </td> 
   <td> TLS inschakelen op domein: laat TLS toe configureerbaar door MX (vereist een bijgewerkte statistiekserver).<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <tr> 
   <td> statServerVersion<br /> </td> 
   <td> Gebruikte versie protocol: versie van communicatieprotocol (1 voor een v5.11- en 6.0.2-server, 2 voor een v6.1-server).<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> Indien niet gedefinieerd, wordt de laatste versie gebruikt. <br /> </td> 
  </tr> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Indien ingesteld op "true", gebruikt uw instantie de <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">Enhanced MTA</a>.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Verificatiemodus: activeert de controlemodus (geen fysieke transmissie van berichten); gebruikt voor simulatie en tests).<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> Werkmap: locatie van tijdelijke bestanden die door de MTA worden gebruikt om te communiceren met onderliggende processen.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> Veld X-Mailer: waarde van veld 'X-Mailer' in SMTP-mailheader.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cachegeheugen {#cache}

In de **cachegeheugen** knoop, vorm de volgende parameters. Dit is de lokale configuratie van het dossiergeheime voorgeheugen.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPeriodSec<br /> </td> 
   <td> Gerecycled na: punt, uitgedrukt in seconden, waarna het bestand automatisch van de cache wordt verwijderd om de opslag terug te winnen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Maximale cachegrootte (MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Frequentie leegmaken: periode in seconden tussen de executies van het mechanisme voor het leegmaken van de cache.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### doorgeven {#relay}

In de **mta > relais** knoop, vorm de volgende parameters. Dit is de configuratie van de postserver voor de berichtlevering.

De lijst zal op de zelfde manier worden behandeld zoals een lijst van MX door een MX DNS vraag is teruggekeerd, gewoonlijk eerste MX wordt gebruikt zolang het beschikbaar is, dan volgende wordt gebruikt, etc.

Raadpleeg voor meer informatie [SMTP-relais](../../installation/using/configuring-campaign-server.md#smtp-relay).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> adres<br /> </td> 
   <td> Lijst met door komma's gescheiden DNS-namen of IP-adressen van te gebruiken SMTP-relais. <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> poort<br /> </td> 
   <td> IP-poort van SMTP-server.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### master {#master}

In de **mta > master** knoop, vorm de volgende parameters. Dit is de configuratie van de hoofdserver.

Raadpleeg voor meer informatie deze [sectie](../../installation/using/configuring-campaign-server.md#mta-child-processes).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> De opiniepeilingsfrequentie van het gegevensbestand van de te leveren banen. Deze waarde geeft de opiniepeilingsfrequentie van de database aan (in seconden). Om de lijst van banen te verkrijgen die op levering wachten, opiniepeilt de MTA regelmatig het gegevensbestand. Wanneer er geen baan wacht, wordt de opiniepeilingsperiode bepaald door deze waarde. Als een taak naar een onderliggende server is overgebracht, wordt deze opiniepeilingduur automatisch tot één seconde verminderd zodat een nieuwe baan zo spoedig mogelijk opnieuw kan worden verwerkt, d.w.z. zodra een kindserver opnieuw beschikbaar is. Dit betekent niet dat de gegevensbestandvraag elke seconde zal worden gedaan tot een kindserver opnieuw beschikbaar is. In feite, wordt een gegevensbestandtoegang slechts gedaan wanneer minstens één kindserver beschikbaar wordt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Wachten op periode na fout met databaseverbinding. Een fout in de databaseverbinding wordt meestal veroorzaakt door de databaseserver zelf. De server kan bijvoorbeeld ook voor onderhoudsdoeleinden worden gestopt. De parameter DataBaseRetryDelay bepaalt de duur tussen twee verbindingspogingen in het geval van een mislukking van de gegevensbestandverbinding.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Geldigheidsperiode voor de cache van persoonlijke sleutels (DomainKeys). De privé sleutels die worden gebruikt om e-mails na de aanbeveling DomainKeys (http://antispam.yahoo.com/domainkeys) te ondertekenen worden opgeslagen als opties in het gegevensbestand. De domainKeysReloadPeriodSec parameter bepaalt hoeveel seconden MTA deze sleutels in een geheime voorgeheugen kan houden. Na deze vertraging moeten alle toetsen opnieuw uit de database worden geladen.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Maximum aantal onderliggende servers. Vertegenwoordigt het maximumaantal servers dat wordt uitgevoerd. U wordt aangeraden dit aantal te beperken tot een optimaal niveau dat compatibel is met de geheugenbronnen van de server. Dit kan tijdens een levering worden gecontroleerd. Het gebruikte geheugen mag niet groter zijn dan een derde van het beschikbare fysieke geheugen, anders wordt de wisselaar gebruikt. Zie <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">MTA onderliggende processen</a>.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Minimum aantal onderliggende servers. MTA probeert om minstens dit aantal servers in werking te houden. Als er minder zijn, start het elke seconde opnieuw nieuwe servers totdat deze waarde wordt bereikt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Aantal onderliggende server bij opstarten. Het aantal onderliggende servers wordt dynamisch gecontroleerd; wanneer MTA begint, leidt het tot zo vele kindservers zoals die door deze waarde worden vermeld. Onderliggende servers kunnen gewoonlijk niet sneller dan één server per seconde worden gestart om hostbronnen op te slaan. Nochtans, wanneer MTA begint, wordt deze beperking genegeerd zodat de kindservers beschikbaar zijn zo spoedig mogelijk.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### onderliggend {#child}

In de **mta > child** knoop, vorm de volgende parameters. Dit is de configuratie van kindservers.

Raadpleeg voor meer informatie [Optimalisatie van e-mailverzending](../../installation/using/email-deliverability.md#email-sending-optimization).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> extraArgs<br /> </td> 
   <td> Optionele opdrachtregelargumenten <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> Time-out totdat inactieve onderliggende servers worden gestopt. Als een kindserver een nutteloze tijd groter dan deze parameter heeft, zal het automatisch doden om gastheermiddelen vrij te maken.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Maximale tijd voor berichtbehoud. Als een voorbereid bericht niet kon worden verzonden wegens throttling of niet met het doel MTA kon verbinden, wordt het bericht verlaten en zal bij volgende opnieuw proberen worden verwerkt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Maximum van parallelle Http- verzoeken aan FCM die door elke kindserver in werking wordt gesteld.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Maximum aantal berichten per kindserver. Elk kind MTA verwerkt dit aantal berichten en sterft. Het is belangrijk om een aantal te specificeren zodat geheugen of middellekken in MTA (typisch een paar duizenden) onschadelijk zijn. Zelfs als er geen bekende geheugenlekken in de MTA-code zijn, zijn de ingesloten JavaScript- en XSL-engines niet volledig betrouwbaar.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitingMessages<br /> </td> 
   <td> In behandeling zijnde berichten: maximumaantal berichten dat in het geheugen wacht om te worden afgeleverd. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Maximale geheugengrootte (in MB) die een onderliggend proces kan gebruiken. Boven deze limiet wordt het proces gestopt, zodat het gebruikte geheugen naar het systeem wordt vrijgegeven. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> Timeout (in seconden) waarna een verbinding van de ZEEP voor een leveringsschakelaar wordt verlaten.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> Begin altijd met de hoogste prioriteit MX.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximumaantal opeenvolgende pogingen bij hervatting.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

In de **mta > child > smtp** knoop, vorm de volgende parameters. Dit is de configuratie van zittingen SMTP.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enableTLS<br /> </td> 
   <td> Hiermee activeert u de levering van e-mailberichten in de veilige modus (STARTTLS/SMTPS) wanneer deze worden ondersteund door de externe server.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> Time-out niet-actieve sessie. Deze parameter wordt slechts gebruikt als de zitting voor het overbrengen van verscheidene berichten naar een bepaald domein wordt opnieuw gebruikt. Wanneer MTA de berichttransmissie heeft voltooid, wordt de zitting SMTP het heeft gebruikt niet systematisch gesloten. Als een bericht klaar is om voor dit zelfde domein te worden verzonden dan zal de zelfde zitting SMTP opnieuw worden gebruikt en dit is waarom de zitting niet automatisch wordt gesloten. De parameter IdleSessionTimeout laat u de tijd bepalen waarin een zitting SMTP actief kan blijven wachtend op een ander bericht. Nadat de duur is verstreken, wordt de sessie automatisch gesloten.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Oorspronkelijke vertraging voordat de verbinding opnieuw wordt geprobeerd. Deze vertraging wordt verdubbeld telkens als de verbinding ontbreekt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Maximum aantal zittingen SMTP door kindserver. Om een bericht te leveren, initialiseert MTA een verbinding SMTP met ontvankelijke MTA. Het maximumaantal gelijktijdige en actieve zittingen SMTP voor een bepaalde kindserver wordt beperkt door deze waarde. Als u deze waarde met maxSpareServers vermenigvuldigt, krijgt u het maximumaantal berichten dat gelijktijdig door een bepaalde kindserver kan worden verwerkt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

In de **mta > child > smtp > IPAffinity** knoop, vorm de volgende parameters. Dit is de configuratie van het beheer van affiniteiten met IP adressen voor geoptimaliseerd uitgaand verkeer SMTP.

Raadpleeg voor meer informatie [Lijst met IP-adressen die moeten worden gebruikt](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) en [Het leiden van uitgaand verkeer SMTP met affiniteiten](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Domeinnaam: lokale domeinnaam die aan het IP-adres is gekoppeld. Wordt gebruikt wanneer een SMTP-opdracht HELO wordt uitgegeven.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Logische naam: namen die door gebruikers zijn gekoppeld aan de affiniteit. Namen worden met puntkomma's van elkaar gescheiden;<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
 </tbody> 
</table>

In de **mta > child > smtp > IP** knoop, vorm de volgende parameters.

Raadpleeg voor meer informatie [Lijst met IP-adressen die moeten worden gebruikt](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> adres<br /> </td> 
   <td> Gekoppeld fysiek adres. Voorbeeld: "192.168.0.1"<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> Bijbehorende id van openbare adres. Gebruikt als sleutel voor de statistiekserver. Moet numeriek zijn. Zie dit <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">sectie</a>.<br /> </td> 
   <td> Lang<br /> </td> 
  </tr> 
  <tr> 
   <td> gewicht<br /> </td> 
   <td> Specificeert de frequentie van gebruik voor dit IP, met betrekking tot andere IPs (grotere gewichten leiden tot hogere frequenties).<br /> </td> 
   <td> Lang<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> Door komma's gescheiden lijst met domeinmaskers die moeten worden opgenomen.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> Door komma's gescheiden lijst met domeinmaskers die moeten worden uitgesloten.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> De naam van de computer verbonden aan het IP adres. Wordt gebruikt wanneer een SMTP-opdracht HELO wordt uitgegeven.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

Hier zijn de verschillende parameters van **nmac** knooppunt. Dit is de configuratie van voor de levering van de pushmelding.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> useHTTPProxy<br /> </td> 
   <td> Gebruik HTTP-proxy gedefinieerd in shared/proxyHTTP. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### doorgeven {#relay-1}

Hier zijn de verschillende parameters van **nmac > relais** knooppunt. Dit vormt het gebruik van een relais voor de berichtlevering (ios http2 schakelaar).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> adres<br /> </td> 
   <td> DNS-adres of naam van het relais dat moet worden gebruikt. <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> poort<br /> </td> 
   <td> Relaispoort<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> Certificaatketen (PEM-bestand). Nuttig bij gebruik van een modelserver.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## gelijnd {#pipelined}

Hier zijn de verschillende parameters van **gelijnd** knooppunt. Dit is de configuratie van de module van de gebeurtenisverwerking voor de Diensten van de Pijpleiding.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> appName<br /> </td> 
   <td> Naam van de toepassing die in de verbinding van de Ontwikkelaar wordt geproduceerd wanneer de openbare sleutel wordt bewaard. <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Opstartparameters<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> URL om een gatewaytoken te verkrijgen.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> Persoonlijke sleutel voor het verkrijgen van tokens (gecodeerd in AES met de optie XtkKey).<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisch starten <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> Verificatie uitschakelen: Verbind met de Diensten van de Pijpleiding zonder authentificatie. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> findPipelineEndpoint<br /> </td> 
   <td> URL om de URL van de Diensten van de Pijpleiding te ontdekken.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Opslagperiode status: frequentie waarmee de interne informatie van het proces in een bestand wordt opgeslagen. Inactief als 0. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forcePipelineEndpoint<br /> </td> 
   <td> URL luisteren: forceer het luisteren URL van de Diensten van de Pijpleiding. <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id van JavaScript die moet worden uitgevoerd wanneer het proces wordt gestart.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Statusserverpoort: De serverhaven van HTTP die u toestaat om de status van het proces te vragen. Inactief als 0.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> De wijzer zal in het gegevensbestand worden opgeslagen telkens als dat aantal berichten wordt verwerkt.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushPeriodSec<br /> </td> 
   <td> Vertraging voordat de aanwijzer is opgeslagen: de aanwijzer wordt minstens één keer in de database opgeslagen gedurende deze periode (nuttig in het geval van een lage activiteit).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tijdstip van de dag waarop het proces automatisch opnieuw wordt gestart. Zie <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisch proces opnieuw opstarten</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> Aantal threads voor gebeurtenisverwerking met een gepersonaliseerde JavaScript-connector.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> Aantal threads voor gebeurtenisverwerking.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> Vertraging tussen de verwerking bij een fout.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Na deze periode vervalt: de gebeurtenis te beëindigen als de verwerking na deze periode nog steeds mislukt.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioriteit aan het begin. Modules met lage prioriteit worden eerst gestart en voor het laatst gestopt. De module syslogd moet daarom prioriteit 0 hebben.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## repareren {#repair}

Hier zijn de verschillende parameters van **repareren** knooppunt. Dit is de configuratie van de module van de gegevensbestandreparatie.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> RepareerActionDelayMin<br /> </td> 
   <td> Herstellingsmodule voor leveringsacties: vertraging (in minuten) waarna de leveringsacties door de reparatiemodule kunnen worden verwerkt. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Hier zijn de verschillende parameters van **securityZone** knooppunt.

Raadpleeg voor meer informatie [Beveiligingszones definiëren](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> allowDebug<br /> </td> 
   <td> Autoriseer zuivert wijze voor de toepassingen van het Web.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> Geef de gebruiker toestemming om de toepassing zonder wachtwoord te gebruiken.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> Geef het gebruik van HTTP voor aanmeldingsgegevens voor de operator toe.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> Het gebruik van SQLDATA in expressies toestaan.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Tokens voor gebruikers-/wachtwoordsessies autoriseren<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Label<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Interne naam<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> Gebruik het beveiligingstoken niet.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> Foutdetails weergeven<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

Hier is de standaardconfiguratie:

```
<securityZone allowDebug="false" allowHTTP="false" allowSQLInjection="false" label="Public Network" name="public">
  <subNetwork name="all" label="All addresses" mask="*" proxy="127.0.0.1, ::1"/>

  <securityZone allowDebug="true" allowHTTP="false" allowSQLInjection="false" label="Private Network (VPN)"
                name="vpn" showErrors="true">

    <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" allowUserPassword="false"
                  allowSQLInjection="false" label="Private Network (LAN)" name="lan" sessionTokenOnly="true"
                  showErrors="true">
      <subNetwork name="lan1" label="Lan 1" mask="192.168.0.0/16" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan2" label="Lan 2" mask="172.16.0.0/12" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan3" label="Lan 3" mask="10.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost" label="Localhost" mask="127.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6"  label="Lan (IPv6)" mask="fc00::/7" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6b" label="Lan (IPv6)" mask="fe80::/10" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost6" label="Localhost (IPv6)" mask="::1/128" proxy="127.0.0.1, ::1"/>
    </securityZone>

  </securityZone>
</securityZone>
```

### subNetwork {#subnetwork}

Hier zijn de verschillende parameters van **securityZone > subNetwork** knooppunt.

Raadpleeg voor meer informatie [Beveiligingszones definiëren](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> label<br /> </td> 
   <td> Label<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> masker<br /> </td> 
   <td> Masker of adres<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Interne naam<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> proxy<br /> </td> 
   <td> Masker of adres van (omgekeerde) volmacht die door dit subnetwerk wordt gebruikt om tot de instantie toegang te hebben. In dit geval wordt de header 'X-Forwarded-For' getest in plaats van deze proxy.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Hier zijn de verschillende parameters van **sms** knooppunt. Dit is de configuratie van de binnenkomende het beheersmodule van SMS.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Opstartparameters<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisch starten<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> Maximumaantal dagen dat bestanden werkbestanden zijn die door de SMPP-connector worden bewaard.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Maximale grootte in MB van de SMPP-werkbestanden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id van JavaScript die moet worden uitgevoerd wanneer het proces wordt gestart.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Herhaling van het sessiecontinuïteitskader: max. periode in seconden tussen twee frames om aan te geven dat de ontvangende sessie nog steeds is ingeschakeld.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Zoekfrequentie: Periode voor opiniepeiling van SMS-accounts.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tijdstip van de dag waarop het proces automatisch opnieuw wordt gestart. Zie <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisch proces opnieuw opstarten</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> Frequentie voor opnieuw laden van account: opnieuw laden van de database van rekeningen die moeten worden gepolled.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioriteit aan het begin. Modules met lage prioriteit worden eerst gestart en voor het laatst gestopt. De module syslogd moet daarom prioriteit 0 hebben.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Aantal seconden vertraging bij SR-verwerking: alleen SRs met een terugwinningsdatum vroeger dan de huidige tijd minus de duur in seconden die door srReadDelay wordt gegeven. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Communicatie onderbreking met de gateway van SMS.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

Hier zijn de verschillende parameters van **sms > netsize** knooppunt.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> netsizeConnectionTimeout<br /> </td> 
   <td> Time-out in seconden bij het tot stand brengen van een verbinding met Netsize.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

Hier zijn de verschillende parameters van **stat** knooppunt. Dit is de configuratie van de MTA statistiekmodule.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Opstartparameters<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisch starten<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id van JavaScript die moet worden uitgevoerd wanneer het proces wordt gestart.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> poort<br /> </td> 
   <td> Server luisterpoort. Zie dit <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">sectie</a>.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tijdstip van de dag waarop het proces automatisch opnieuw wordt gestart. Zie <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisch proces opnieuw opstarten</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioriteit aan het begin. Modules met lage prioriteit worden eerst gestart en voor het laatst gestopt. De module syslogd moet daarom prioriteit 0 hebben.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Hier zijn de verschillende parameters van **syslogd** knooppunt. Dit is de configuratie van de het beheersmodule van het Logboek.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Opstartparameters<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisch starten<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id van JavaScript die moet worden uitgevoerd wanneer het proces wordt gestart.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Maximale grootte in MB voor een logbestand. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Maximumaantal logins.log-bestanden dat behouden moet blijven. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tijdstip van de dag waarop het proces automatisch opnieuw wordt gestart. Zie <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisch proces opnieuw opstarten</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioriteit aan het begin. Modules met lage prioriteit worden eerst gestart en voor het laatst gestopt. De module syslogd moet daarom prioriteit 0 hebben.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## bijhouden {#tracking}

Hier zijn de verschillende parameters van **bijhouden** knooppunt. Dit is de configuratie van de volgende server.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Opstartparameters<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisch starten<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> Schakel onjuist gevormde URL's die zijn gegenereerd uit vorige builds uit.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> consolidatiePeriodSec<br /> </td> 
   <td> Consolidatieperiode<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Deduplicatieopeningen: Verwijder dubbele open het volgen logboeken om de gevolgen van postvoorproeven in postlezers zoals Vooruitzichten te beperken.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Tot X% fouten negeren: de volgindicatoren niet bijwerken zolang de verhouding van tijdschriften die nog niet in aanmerking zijn genomen deze waarde niet bereikt. <br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Foutindicatoren bijwerken: maximale duur voordat de foutindicatoren opnieuw worden berekend.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indicatorDuration<br /> </td> 
   <td> Indicatoren berekenen tijdens: duur na de geldigheidsdatum van een levering waarna de geconsolideerde indicatoren niet langer worden berekend.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id van JavaScript dat moet worden uitgevoerd wanneer het proces wordt gestart <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Aantal logboeken die door vraag aan de verre volgende server worden gevraagd.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> API sleutel voor de Integratie van het Eindpunt van de Dienst Phishbowl. Hierdoor wordt omleiding van onjuist gevormde URL's die zijn gegenereerd op basis van oudere builds beschermd. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Eindpunt voor de Integratie van het Eindpunt van de Dienst Phishbowl. Hierdoor wordt omleiding van onjuist gevormde URL's die zijn gegenereerd op basis van oudere builds beschermd.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tijdstip van de dag waarop het proces automatisch opnieuw wordt gestart. Zie <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisch proces opnieuw opstarten</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioriteit aan het begin. Modules met lage prioriteit worden eerst gestart en voor het laatst gestopt. De module syslogd moet daarom prioriteit 0 hebben.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Tot X% van tekstspatiëring negeren: de volgindicatoren niet bijwerken zolang de verhouding van tijdschriften die nog niet in aanmerking zijn genomen deze waarde niet bereikt.<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Trackingindicatoren bijwerken: maximumduur voordat de traceerindicatoren opnieuw worden berekend.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Grootte van browserid-cache.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Hier zijn de verschillende parameters van **trackinglogd** knooppunt. Dit is de configuratie van het volgende logboek schrijvend daemon.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Opstartparameters<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisch starten<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id van JavaScript dat moet worden uitgevoerd wanneer het proces wordt gestart <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Max. schrijfpogingen: maximumaantal bestanden dat kan worden gemaakt in geval van een schrijffout in logbestanden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Maximale loggrootte: maximale ruimte die wordt gebruikt door het aanmelden op de schijf (in MB). Mag niet minder dan 100 MB zijn. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Maximum aantal logbestanden: maximumaantal logbestanden dat in het gedeelde geheugen is opgeslagen. Kan niet kleiner zijn dan 10000. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tijdstip van de dag waarop het proces automatisch opnieuw wordt gestart. Zie <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisch proces opnieuw opstarten</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Aantal stammen vóór zuivering: Het aantal logbestanden dat is ingevoegd voordat de logbestanden worden gewist. Mag niet lager zijn dan 50000.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioriteit aan het begin. Modules met lage prioriteit worden eerst gestart en voor het laatst gestopt. De module syslogd moet daarom prioriteit 0 hebben.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Maximumaantal tekens dat in gedeeld geheugen is opgeslagen voor extra parameters voor webtracking.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## web {#web}

Hier zijn de verschillende parameters van **web** knooppunt. Dit is de configuratie van de Module van het Web.

Raadpleeg voor meer informatie deze [sectie](configuring-campaign-server.md#default-port-for-tomcat).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> JVMOptions<br /> </td> 
   <td> Opties van de JVM worden doorgegeven als een tekenreeks.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> Maximum aantal draden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> Minimum aantal draden.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Opstartparameters<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisch starten<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Tomcat-luistercontrolepoort: verwijzen naar <a href="configure-tomcat.md" target="_blank">Tomcat configureren</a>.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP-luisterpoort: verwijzen naar <a href="configure-tomcat.md" target="_blank">Tomcat configureren</a>.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id van JavaScript die moet worden uitgevoerd wanneer het proces wordt gestart.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> Grootte van de rij voor Vraag SubmitDelivery: maximumaantal vraag van de ZEEP SubmitDelivery die een rij kan worden gevormd.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB)<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Meldingsrelais: HostName:Port die relais van berichten toelaat.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tijdstip van de dag waarop het proces automatisch opnieuw wordt gestart. Zie <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisch proces opnieuw opstarten</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioriteit aan het begin. Modules met lage prioriteit worden eerst gestart en voor het laatst gestopt. De module syslogd moet daarom prioriteit 0 hebben.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> Begin de router van de ZEEP op modulewijze.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

Hier zijn de verschillende parameters van **web > jsp** knooppunt. Dit is de configuratie van de parameters die door JSPs worden gebruikt.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> foutopsporing<br /> </td> 
   <td> Uitvoering van JSP in foutopsporingsmodus of niet.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> Downloadmap: downloadpad van installatieprogramma's voor de clientconsoles.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> Pad van .fo-bestand.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> URL van de router van de ZEEP (http://myserver/xxx, http://jni of mailto:xxx).<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

De **web > jsp > classpath** knooppunt bevat de lijst met alle klassenpaden die moeten worden gebruikt bij het starten van JVM. Hier is de standaardconfiguratie:

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat7-websocket.jar
          $(XTK_INSTALL_DIR)/java/lib/pdfbox-2.0.4.jar
          $(XTK_INSTALL_DIR)/java/lib/FontBox-0.1.0.jar
          $(XTK_INSTALL_DIR)/java/lib/AGJavaEndpoint.22.jar
          $(XTK_INSTALL_DIR)/java/lib/NSGConstants.jar
          $(XTK_INSTALL_DIR)/java/lib/smpp.jar
          $(XTK_INSTALL_DIR)/java/lib/nlweb.jar
          $(XTK_INSTALL_DIR)/java/lib/jcaptcha-all.jar
          $(XTK_INSTALL_DIR)/java/lib/apns-1.0.0.Beta6-jar-with-dependencies.jar
          $(XTK_INSTALL_DIR)/java/lib/commons-collections-3.2.2.jar
          $(XTK_INSTALL_DIR)/java/lib/jcommon-1.0.16.jar
          $(XTK_INSTALL_DIR)/java/lib/jfreechart-1.0.13.jar
          $(XTK_INSTALL_DIR)/java/lib/barcode4j-light.jar
          $(XTK_INSTALL_DIR)/java/lib/zxing.jar
          $(XTK_INSTALL_DIR)/java/lib/raztec.jar
          $(XTK_INSTALL_DIR)/java/lib/gson-2.7.jar
          $(XTK_INSTALL_DIR)/java/lib/alpn-api-1.1.3.v20160715.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-all-4.1.6.Final.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-tcnative-boringssl-static-1.1.33.Fork22.jar
          $(XTK_INSTALL_DIR)/java/lib/pushy-0.8.1.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-api-1.7.21.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-simple-1.7.21.jar'
```

### jssp {#jssp}

Hier zijn de verschillende parameters van **web > jssp** knooppunt. Dit is de configuratie van de parameters die door JSSPs worden gebruikt.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> collectsGarbageAfterRequest<br /> </td> 
   <td> Schakelt de opschoonfunctie van de JavaScript-context na elke query in.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximumaantal pagina's dat door een JavaScript-context wordt aangeboden. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

De **web > jsp > classpath** knooppunt bevat de lijst met alle klassenpaden die moeten worden gebruikt bij het starten van JVM.

### doorgeven {#relay-2}

Hier zijn de verschillende parameters van **web > relais** knooppunt. Dit is de configuratie van het relais voor HTTP- verzoeken tussen twee streken.

Raadpleeg voor meer informatie deze [sectie](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debugRelay<br /> </td> 
   <td> Begin de HTTP relaismodule binnen de server van het Web op zuivert wijze.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Verboden teken(s) (domein): lijst met verboden tekens in de sectie 'gezag' van een URI.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> Verboden teken(s) (pad): lijst met verboden tekens in de sectie 'path' van een URI.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Waarde van de module 'mod_dir'-optie: lijst met bestanden die moeten worden gebruikt tijdens een query op een map.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 'index.md' <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> Start de HTTP relay module.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Begin de HTTP relaismodule binnen de server van het Web. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Wacht even voordat u de verboden URL verwijdert.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "60"<br /> </td> 
  </tr> 
 </tbody> 
</table>

Voeg een **web > relais > url** knooppunt voor elke URL die moet worden doorgestuurd (invoegvolgorde definieert prioriteit) met de volgende parameters.

Raadpleeg voor meer informatie [Dynamische paginabeveiliging en -bedekkingen](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) en [sectie](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IPMask<br /> </td> 
   <td> Erkende IP's: komma's gescheiden lijst van bronIP adressen toegestaan om het relais voor dit masker te gebruiken.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ontkennen<br /> </td> 
   <td> Toegang tot deze URL's weigeren (een HTTP 403-fout retourneren)<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> DNS-alias naar relais: door komma's gescheiden lijst met DNS-aliasmaskers die moeten worden doorgestuurd (bijv. "*.adobe.com").<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> De toegang van HTTP erkende geen kwestie wat de veiligheidsstreek (zoals webApps). <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relaisHost<br /> </td> 
   <td> Oorspronkelijke host toevoegen: gebruik de HTTP 'Host'-header van de oorspronkelijke aanvraag bij het opnieuw afspelen.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relaisPath<br /> </td> 
   <td> Eerste URL-pad toevoegen: voeg het volledige pad van de URL's toe om door te geven aan de URL van de doelpagina. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> Synchronisatiestatus van een openbare bron (opsomming). Mogelijke waarden zijn 'normal' (normal execute), 'blacklist' (url added to lijst van gewezen personen in case of error 404) en 'reserve' (file upload on reserve server if existing).<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> normaal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> URL van de doelpagina: verwijzen naar <a href="configure-tomcat.md" target="_blank">Tomcat configureren</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Maximale uitvoeringstijd (in seconden) van de aanvraag die wordt afgespeeld.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> Masker van URL's die moeten worden doorgestuurd (bijvoorbeeld: '/nl*', '*.jsp').<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Hier is de standaardconfiguratie:

```
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true"
     status="normal" targetUrl="http://localhost:7781" timeout="" urlPath="/pipelined/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/view/*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="*ooconv.jsp*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/res/*.jsp*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/sc.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/interactionProposal.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/zoneJson.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/barcode.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/captcha.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/webForm.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/xtk/jsp/zoneinfo.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/facebookCallback.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/m.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/s.jsp"/>

<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nms/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/xtk/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nl/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="*.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="true" urlPath="/webApp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/report/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/jssp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/strings/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/interaction/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/barcode/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/lineImage/*"/>

<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/favicon.*"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.md"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.png"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.jpg"/>
```

Voeg een **web > relais > responseHeader** knoop voor elke kopbal van HTTP aan antwoorden toe te voegen die aan het relais door:sturen.

Raadpleeg voor meer informatie [HTTP-headers beheren](../../installation/using/configuring-campaign-server.md#managing-http-headers).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Naam koptekst<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
  <tr> 
   <td> value<br /> </td> 
   <td> Waarde koptekst <br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
 </tbody> 
</table>

Hier is de standaardconfiguratie:

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### omleiding {#redirection}

Hier zijn de verschillende parameters van **web > omleiden** knooppunt. Dit is de configuratie van de omleidingsmodule.

Raadpleeg voor meer informatie deze [sectie](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IMSOrgId<br /> </td> 
   <td> Organisatie-id: unieke organisatie-id binnen de Adobe Experience Cloud, met name gebruikt voor de VisitorID-service en de IMS SSO. <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Waarde die het beleid beschrijft dat voor permanente koekjes wordt gebruikt (volgzaam met het PP3P Compacte formaat van het Beleid). <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Door komma's gescheiden lijst met domeinen die moeten worden geconfigureerd om expliciet aan te geven welk domein moet worden ingesteld. <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Database-id die is gekoppeld aan de volgende instantie.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Aantal logbestanden per aanroep: aantal logboeken die door gebrek op een vraag van methode GetTrackingLogs zijn teruggekeerd.<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Pagina voor verlopen omleidingen: URL van Web-pagina die door gebrek door de redirection server wordt gebruikt wanneer redirection voor een leveringsactie is verlopen.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Maximum aantal taken: maximumaantal leveringsacties in cache. Mag niet lager zijn dan 50. <br /> </td> 
   <td> Lang<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> Start de omleidingsservice.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> Start de omleidingsservice in de modulemodus.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Webspatiëring: het maken van logboeken voor de pagina's die door onbekende gebruikers worden bezocht. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> Wachtwoord dat wordt gebruikt door de omleidingsserver.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Hier zijn de verschillende parameters van **web > redirection > reserveServer** knooppunt.

Raadpleeg voor meer informatie [Overbodige tekstspatiëring](../../installation/using/configuring-campaign-server.md#redundant-tracking).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabledIf<br /> </td> 
   <td> Wordt in aanmerking genomen: de volgende server wordt in aanmerking genomen als de uitdrukking waar terugkeert. <br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> id<br /> </td> 
   <td> Naam<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL van extra omleidingsserver<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

Hier zijn de verschillende parameters van **web > spamCheck** knooppunt. Dit is de configuratie de anti-spam het scoren van e-mail evaluatieparameters.

Raadpleeg voor meer informatie [SpamAssassin configureren](../../installation/using/configuring-spamassassin.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> command<br /> </td> 
   <td> Uit te voeren opdracht om de anti-spamscore van een e-mail te evalueren (bijvoorbeeld "perl spamcheck.pl").<br /> </td> 
   <td> Tekenreeks<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Hier zijn de verschillende parameters van **wfserver** knooppunt. Dit is de configuratie van het werkschemaproces.

Raadpleeg voor meer informatie [Workflows en affiniteiten met hoge beschikbaarheid](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beschrijving </th> 
   <th> Type </th> 
   <th> Standaardwaarde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> affiniteit<br /> </td> 
   <td> affiniteit<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Opstartparameters<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisch starten<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Periode<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> Id van JavaScript die moet worden uitgevoerd wanneer het proces wordt gestart.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Waarschuwing geheugenverbruik: waarschuwing over de hoeveelheid RAM die door een bepaald proces wordt verbruikt (in MB).<br /> </td> 
   <td> Lang<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Meldingsrelais: HostName:Port die relais van berichten toelaat.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tijdstip van de dag waarop het proces automatisch opnieuw wordt gestart. Zie <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisch proces opnieuw opstarten</a>.<br /> </td> 
   <td> Tekenreeks<br /> </td> 
   <td> "06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioriteit aan het begin. Modules met lage prioriteit worden eerst gestart en voor het laatst gestopt. De module syslogd moet daarom prioriteit 0 hebben.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
