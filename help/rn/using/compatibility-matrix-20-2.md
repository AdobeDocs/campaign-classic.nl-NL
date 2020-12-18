---
solution: Campaign Classic
product: campaign
title: Compatibiliteitsmatrix
description: Compatibiliteitsmatrix
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: aabab5367ea4a26837fa3dc94a36fbbfa48d59e3
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 83%

---


# Compatibiliteitsmatrix{#compatibility-matrix}

Dit document bevat een lijst met alle systemen en componenten die worden ondersteund voor de nieuwste build van **Adobe Campaign Classic (v6.11 en v7)**. Producten en versies die geen deel uitmaken van deze lijst, zijn niet compatibel met Adobe Campaign.

## Belangrijke opmerkingen{#important-notes}

Deze matrix wordt regelmatig bijgewerkt door toevoeging van nieuwe ondersteunde items en verwijdering van verouderde items.

Tenzij anders vermeld worden alle kleine releases ondersteund.

Adobe Campaign Classic is compatibel met alle systemen en tools die op deze pagina worden vermeld. Wanneer specifieke versies van deze externe systemen en tools het einde van de levensduur bereiken bij hun respectieve makers, is Adobe Campaign niet meer compatibel met deze versies. Ze worden dan in de volgende productrelease uit onze compatibiliteitsmatrix verwijderd. Zorg ervoor dat u ondersteunde versies van alle systemen in de compatibiliteitsmatrix gebruikt om problemen te voorkomen.

Ga naar [deze pagina](../../rn/using/deprecated-features.md) voor meer informatie over verouderde items.

## Besturingssystemen{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>7.x (64 bits)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>8 (64 bits)</p>
<p>9 (64 bits)</p>
<p>10 (64 bits)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 bits)</p>
<p><strong>Belangrijk:</strong> als u RHEL gebruikt, moet u bereid zijn om SELinux uit te schakelen of uw architecten aangepaste SELinux-regels te laten schrijven om te controleren of een ingeschakelde SELinux-versie geen problemen veroorzaakt met Campaign-activiteiten.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2012</p>
<p>2012 R2</p>
<p>2016</p>
</td>
</tr>
</tbody>
</table>

## Webservers{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>8.0 op Windows Server 2012 - Windows 8</p>
<p>8.5 op Windows Server 2012 R2</p>
<p>10.0 op Windows Server 2016</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 voor RHEL7 - CentOS 7, Debian 8/9, Windows (64 bits)</p>
</td>
</tr>
</tbody>
</table>

## Tools{#Tools}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
<p>9</p>
<p>De applicatie is goedgekeurd voor zowel de Java Development Kit (JDK) die is ontwikkeld door Oracle als voor OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (en vorige versies indien ingesloten in uw systeem)</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

## RDBMS-stuurprogramma&#39;s{#RDBMSdrivers}

De volgende RDBMS-stuurprogramma&#39;s worden ondersteund:

* Oracle SQL*Net 11

* Oracle SQL*Net 12

* PostgreSQL (libpq)

* SQLServer

* DB2 (ODBC-stuurprogramma)


>[!NOTE]
>
>Het RDBMS-stuurprogramma moet overeenkomen met de RDBMS-serverversie.

## RDBMS-servers{#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>11g R2</p>
<p>12c</p>
<p>18c</p>
<p>19c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
<p>Opmerking: u kunt ook Amazon RDS voor PostgreSQL gebruiken met de hierboven vermelde versies.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2012 - SP1 en SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
<p>Waarschuwing: Microsoft SQL Server wordt niet als de primaire database ondersteund wanneer de Campaign-server op Linux wordt uitgevoerd. <a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">Meer informatie</a>.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL is de standaard databaseserver voor gehoste omgevingen.

## CRM-connectoren{#CRMconnectors}

<table>
<tbody>
<tr>
<td>Salesforce-connector-API</td>
<td>
<p>API-versie 37</p>
</td>
</tr>
<tr>
<td>SFDC-API</td>
<td>
<p>API-versie 15</p>
<p>API-versie 21</p>
</td>
</tr>
<tr><td>Oracle On-demand-API</td>
<td>
<p>Web Services v1.0-API</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>Soap-API - On-premise: 2007, 2015, 2016</p>
<p>Soap-API - Online: 2015, 2016</p>
<p>Web-API - on-premise en online: 365, 2016, 2016 Update 1</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

<table>
<tbody>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
</tr>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>11g</p>
<p>12 quater</p>
<p>18 quater</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9,4 x</p>
<p>9,5 x</p>
<p>9,6 x</p>
<p>10.x</p>
<p>11.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2012 SP1 en SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>15.0</p>
<p>15.10</p>
<p>16</p>
<p>16.20</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>versie 1 SP12 of hoger</p>
</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
</tr>
</tbody>
</table>

## Besturingssystemen voor clientconsole{#ClientConsoleoperatingsystems}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2012</p>
<p>2016</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>8</p>
<p>10 (aanbevolen voor Japanse instanties)</p>
</td>
</tr>
</tbody>
</table>

## Mobiele SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x</p>
<p>8.x</p>
<p>9,0</p>
<p>met mobiele SDK-build 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9</p>
<p>iOS 10</p>
<p>iOS 11</p>
<p>iOS 12</p>
<p>iOS 13</p>
<p>met mobiele SDK-build 1.0.26, compatibel met de 32-bits en de 64-bits versie.</p>
</td>
</tr>
</tbody>
</table>

## Browsers{#Browsers}

Versie 11 van Internet Explorer wordt ondersteund.

Voor de volgende browsers wordt de nieuwste versie ondersteund:

* Microsoft Edge

* Firefox

* Chroom

* Safari

## Experience Cloud-integraties{#ExperienceCloudintegrations}

Voor integratie met Adobe oplossingen, verwijs naar dit [sectie](https://docs.adobe.com/content/help/en/campaign-classic/using/integrating-with-adobe-experience-cloud/about-campaign-integrations.html#experience-cloud-integrations).

## Wellicht ook interessant{#Morelikethis}

* [Opmerkingen bij de release van Campaign Classic ](https://docs.adobe.com/content/help/nl-NL/campaign-classic/using/release-notes/latest-release.html)
* [Installatiehandleiding](https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/general-architecture.html)
* [Verouderde functies en systemen](https://helpx.adobe.com/nl/campaign/kb/deprecated-and-removed-features.html)
* [Upgradeprocedure opstellen](https://helpx.adobe.com/nl/campaign/kb/acc-build-upgrade.html)
* [Campaign Classic-compatibiliteitsmatrix voor 19.0-release](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix-19-0.html)
* [Campaign Classic-compatibiliteitsmatrix voor 19.1-release](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix-19-1.html)

