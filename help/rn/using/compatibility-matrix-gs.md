---
solution: Campaign Classic
product: campaign
title: Compatibiliteitsmatrix voor Gold Standard
description: Campaign Classic-compatibiliteitsmatrix voor Gold Standard-release
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: aabab5367ea4a26837fa3dc94a36fbbfa48d59e3
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 15%

---


# Gold Standard Compatibility matrix{#compatibility-matrix-gs}

Dit document bevat een lijst met alle systemen en onderdelen die worden ondersteund voor builds van de **Adobe Campaign Classic Gold Standard** 19.1. Producten en versies die geen deel uitmaken van deze lijst, zijn niet compatibel met Adobe Campaign.

## Belangrijke opmerkingen{#important-notes-gs}

Tenzij anders vermeld, worden alle kleine releases ondersteund.

Adobe Campaign Classic is compatibel met alle systemen en gereedschappen die op deze pagina worden vermeld. Aangezien specifieke versies van deze systemen en hulpmiddelen van derden het einde van de levensduur (EOL) met hun respectieve makers bereiken, zal Adobe Campaign niet meer compatibel zijn met die versies en zullen zij uit onze verenigbaarheidsmatrijs in de verdere productversie worden verwijderd. Zorg ervoor dat u ondersteunde versies van alle systemen in de compatibiliteitsmatrix gebruikt om problemen te voorkomen.

## Operating Systems{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x (64 bits)</p>
<p>7.x (64 bits)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9 (64 bits)</p>
<p>8 (64 bits)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 bits)</p>
<p><strong>Belangrijk:</strong> Als u RHEL gebruikt, moet u bereid zijn om SELinux onbruikbaar te maken of uw architecten te hebben aangepaste SELinux regels schrijven om te controleren dat toegelaten SELinux geen kwesties met de verrichtingen van de Campagne veroorzaakt.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

## Web Servers{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 op Windows Server 2016</p>
<p>8.5 op Windows Server 2012 R2</p>
<p>8.0 op Windows Server 2012 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 voor RHEL7 - CentOS 7, Debian 8/9, Windows (64 bits)</p>
<p>2.2 voor RHEL6 - alleen CentOS 6 (64 bits)</p>
</td>
</tr>
</tbody>
</table>

## Tools{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
<p>De aanvraag is goedgekeurd voor de Java Development Kit (JDK) die is ontwikkeld door Oracle en voor OpenJDK.</p>
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
<p>3,4 x</p>
</td>
</tr>
</tbody>
</table>

## RDBMS-servers{#RDBMSservers-gs}

>[!NOTE]
>
>RDBMS-stuurprogramma moet overeenkomen met RDBMS-serverversie.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9,6 x</p>
<p>9,5 x</p>
<p>9,4 x</p>
<p>Opmerking: u kunt ook Amazon RDS voor PostgreSQL gebruiken met de hierboven gespecificeerde versies.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2018</p>
<p>2018 R2</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 en SP2</p>
<p>Waarschuwing: Microsoft SQL Server wordt niet ondersteund als de primaire database wanneer de Campagneserver op Linux wordt uitgevoerd. <a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">Meer informatie</a>.</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>Waarschuwing: DB2 UDB is niet toegestaan voor nieuwe installaties.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL is de standaarddatabaseserver voor gehoste omgevingen.

## CRM-connectoren{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>Salesforce-connector-API</td>
<td>
<p>API-versie 37</p>
</td>
</tr>
<tr>
<td>SFDC API</td>
<td>
<p>API-versie 21</p>
<p>API-versie 15</p>
</td>
</tr>
<tr><td>Oracle On-demand-API</td>
<td>
<p>Web Services v1.0 API</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>Soap-API - On-premise: 2007, 2015, 2016</p>
<p>Soap-API - Online: 2015, 2016</p>
<p>Web API - Op locatie en online: 365, 2016, 2016 Update 1</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9,6 x</p>
<p>9,4 x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>SP1 en SP2 2012</p>
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
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
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
<p>versie 1 SPS 12</p>
</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
</td>
</tr>
</tbody>
</table>

## Besturingssystemen voor clientconsole{#ClientConsoleoperatingsystems-gs}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>Zeven</p>
<p>8</p>
<p>10 (aanbevolen voor Japanse instanties)</p>
</td>
</tr>
</tbody>
</table>

## Mobile SDK{#MobileSDK-gs}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x, 8.x, 9.0</p>
<p>met mobiele SDK build 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>met mobiele SDK build 1.0.26, compatibel met 32- en 64-bits versies.</p>
</td>
</tr>
</tbody>
</table>

## Browsers{#Browsers-gs}

Voor de volgende browsers wordt de nieuwste versie ondersteund: Microsoft Edge, Mozilla Firefox, Google Chrome, Safari.

Internet Explorer 11 wordt ondersteund.

## Meer als dit{#Morelikethis-gs}

* [Opmerkingen bij de release Campaign Classic](../../rn/using/latest-release.md)
* [Installatiehandleiding](../../installation/using/general-architecture.md)
* [Verouderde functies en systemen](../../rn/using/deprecated-features.md)
* [Upgradeprocedure bouwen](https://helpx.adobe.com/nl/campaign/kb/acc-build-upgrade.html)
