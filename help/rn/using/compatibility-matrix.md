---
product: campaign
title: Compatibiliteitsmatrix voor Campaign Classic
description: Campaign Classic-compatibiliteitsmatrix
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 85ec9e22281b9132e499bb6862c8c073871725d6
workflow-type: ht
source-wordcount: '844'
ht-degree: 100%

---

# Compatibiliteitsmatrix {#compatibility-matrix}

De [nieuwste build](../../rn/using/latest-release.md) van Adobe Campaign Classic v7 is compatibel met alle systemen en tools die op deze pagina worden vermeld.  Wanneer specifieke versies van deze externe systemen en tools bij hun respectieve makers het einde van de levensduur bereiken, is Adobe Campaign niet meer compatibel met deze versies. Ze worden dan in de volgende productrelease uit onze compatibiliteitsmatrix verwijderd. Zorg ervoor dat u ondersteunde versies van alle systemen in deze compatibiliteitsmatrix gebruikt om problemen te voorkomen.  Ga naar [deze pagina](../../rn/using/deprecated-features.md) voor meer informatie over verouderde items.

Tenzij anders vermeld worden alle kleine releases ondersteund.

>[!CAUTION]
>
>Deze matrix wordt regelmatig bijgewerkt door toevoeging van nieuwe ondersteunde systemen en tools en verwijdering van verouderde systemen en tools.

## Besturingssystemen {#OperatingSystems}

Als On-Premise/hybride klant moet u Adobe Campaign in een van de hieronder vermelde besturingssystemen installeren. Meer informatie over de installatiestappen van Campaign Classic v7 vindt u op [deze pagina](../../installation/using/application-server.md).

<table> 
<tbody> 
<td><strong>Besturingssysteem</strong></td>
<td><strong>Versie besturingssysteem</strong></td>
<td><strong>Minimale Campaign-versie</strong></td>
<tr>
<td>
<p>Debian</p>
</td>
<td>
<p>11</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Red Hat Enterprise Linux (RHEL)</p>
</td>
<td>
<p>9.x</p>
<p>8.x</p>
<p>7.x</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Windows Server</p>
</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4</p>
<p>v7.2</p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>Met RHEL moet u bereid zijn om [SELinux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#selinux) uit te schakelen of uw architecten aangepaste SELinux-regels te laten schrijven om te controleren of een ingeschakelde SELinux geen problemen veroorzaakt met Campaign-bewerkingen.

## Webservers {#WebServers}

Afhankelijk van uw besturingssysteem moet u als On-Premise/hybride klant Campaign in een van de onderstaande webservers integreren. Meer informatie over configuratiestappen voor webservers vindt u op [deze pagina](../../installation/using/integration-into-a-web-server-for-windows.md) (voor Windows) en [deze pagina](../../installation/using/integration-into-a-web-server-for-linux.md) (voor Linux).

<table>
<tbody>
<td><strong>Webserver</strong></td>
<td><strong>Webserverversie</strong></td>
<tr>
<td>
<p>Microsoft IIS</p>
</td>
<td>
<p>10.0</p>
</td>
</tr>
<tr>
<td>
<p>Apache</p>
</td>
<td>
<p>2.4</p>
</td>
</tr>
</tbody>
</table>

## Tools {#Tools}

Als On-Premise/hybride klant moet u de hieronder vermelde tools installeren en configureren. [Meer informatie](../../installation/using/application-server.md).

<table>
<tbody>
<td><strong>Tool</strong></td>
<td><strong>Versie</strong></td>
<td><strong>Minimale Campaign-versie</strong></td>
<tr>
<td><p>Java Development Kit (JDK)</p>
<p>Meer informatie vindt u <a href="../../installation/using/application-server.md#jdk" target="_blank">op deze pagina</a>.</p>
</td>
<td>
<p>17</p>
<p>11</p>
<p>9</p>
<p>8</p>
<p></p>
</td>
<td>
<p>vereist vanaf v7.4.1</p>
<p>vereist vanaf v7.4.1</p>
<p>tot v7.4.1</p>
<p>tot v7.4.1</p>
</tr>
<tr>
<td><p>Libre Office</p></td>
<td>
<p>7 (en vorige versies indien ingesloten in uw systeem)</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td><p>SpamAssassin</p></td>
<td>
<p>3.4.x</p>
</td>
<td>
<p></p>
</td>
</tbody>
</table>

## Relation Database Management Systems (RDBMS) {#RDBMSservers}

Als On-Premise/hybride klant moet u een van de onderstaande databases installeren en configureren. [Meer informatie](../../installation/using/creating-and-configuring-the-database.md).


<table>
<tbody>
<td><strong>Databasesysteem</strong></td>
<td><strong>Databaseversie</strong></td>
<td><strong>Minimale Campaign-versie</strong></td>
<tr>
<td>
<p>Oracle</p>
</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>PostgreSQL</p>
</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>
<p>v7.3.2</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Microsoft SQL Server</p>
</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* Het RDBMS-stuurprogramma moet overeenkomen met de RDBMS-serverversie.
>
>* Microsoft SQL Server wordt niet als de primaire database ondersteund wanneer de Campaign-server in Linux wordt uitgevoerd. [Meer informatie](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).
>
>* U kunt ook Amazon RDS voor PostgreSQL gebruiken met de hierboven vermelde versies.
>
>* PostgreSQL is de RDBMS voor Hosted/Managed Cloud Services-omgevingen.


## CRM-connectoren {#CRMconnectors}

Hieronder vindt u de Customer Relationship Management-systemen (CRM) die compatibel zijn met Adobe Campaign. [Leer meer](../../platform/using/crm-connectors.md) over de Campaign CRM-connectoren.

<table>
<tbody>
<tr>
<td>
<p>Salesforce-connector-API</p>
</td>
<td>
<p>API-versie 49</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Dynamics-connector</p>
</td>
<td>
<p>Web-API</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

Hieronder vindt u externe databases die compatibel zijn met Adobe Campaign [Federated Data Access-module](../../installation/using/about-fda.md). De compatibiliteit is afhankelijk van uw [hostmodel](../../installation/using/hosting-models.md).

**Managed Services** (gehost), **Hybride** en **on-premise** omgevingen kunnen Campaign verbinden met de volgende externe databasesystemen:

<table>
<tbody>
<td><strong>Databasesysteem</strong></td>
<td><strong>Databaseversie</strong></td>
<td><strong>Minimale Campaign-versie</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>v7.0 19.1.4 </td>
</tr>
</tbody>
</table>

Daarnaast kunnen **Hybride**- en **On-Premise**-omgevingen Campaign ook verbinding maken met de volgende externe databasesystemen. Deze systemen zijn **niet compatibel** met (door) Campaign **Managed Services** (gehoste) omgevingen.

<table>
<tbody>
<td><strong>Databasesysteem</strong></td>
<td><strong>Databaseversie</strong></td>
<td><strong>Minimale Campaign-versie</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td></td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>v7.2</p>
</td>
<td></td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>versie 1 SPS 12</p>
</td>
<td></td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2022 (vanaf Campaign v7.4)</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 en SP2</p>
</td>
<td></td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td></td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (laatste versie)</p>
</td>
<td></td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td></td>
</tr>
</tbody>
</table>


## Clientconsole {#ClientOS}

De volgende besturingssystemen en browsers zijn **vereist** om de [Campaign-clientconsole](../../installation/using/installing-the-client-console.md) te gebruiken.

### Besturingssystemen

<table>
<tbody>
<td><strong>Systeem</strong></td>
<td><strong>Besturingssysteemversie</strong></td>
<td><strong>Minimale Campaign-versie</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4.1</p>
<p>v7.2.1</p>
<p></p>
</tbody>
</table>

### Microsoft WebView2-runtime {#webview}

De nieuwste versie van Microsoft Edge WebView2-runtime is verplicht voor de Campaign-clientconsole.

Download Microsoft Edge WebView2 van [Microsoft Developer-site](https://www.adobe.com/go/acc-ms-webview2-runtime-download).


## Mobiele SDK {#MobileSDK}

U kunt via de Adobe Experience Platform Mobile SDK Campaign gebruiken om [pushmeldingen te verzenden](../../delivery/using/about-mobile-app-channel.md) door de Adobe Campaign-extensie te configureren in de gebruikersinterface voor dataverzameling.

De Campaign SDK is [verouderd](deprecated-features.md) vanaf Campaign v7.4. Om een soepele overgang voor bestaande implementatie naar de AEP Mobile SDK te waarborgen kunt u deze nog steeds gebruiken in de hieronder vermelde besturingssystemen<!--, using the associated [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)-->.


<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>7 - 14</p>
<p>met mobiele SDK-build 1.1.1.</p>
<p>Android 13 en 14 worden ondersteund vanaf Campaign v7.4.</p>
<p>Android 12 wordt ondersteund vanaf Campaign v7.3.</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 17</p>
<p>met mobiele SDK-build 1.0.26.</p>
<p>Apple iOS 15 wordt ondersteund vanaf Campaign v7.3. </p>
<p>Apple iOS 16 en 17 worden ondersteund vanaf Campaign v7.4.</p>
</td>
</tr>
</tbody>
</table>

## Browsers {#Browsers}

De volgende browsers, in hun meest recente versie, zijn compatibel met Campaign voor [Webtoegang](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



>[!MORELIKETHIS]
>
>* [Opmerkingen bij de release van Campaign Classic ](../../rn/using/latest-release.md)
>* [Algemene Campaign-architectuur](../../installation/using/general-architecture.md)
>* [Aanbevelingen voor hardwareaanpassing](../../technotes/using/hardware-sizing.md)
>* [Verouderde functies en systemen](../../rn/using/deprecated-features.md)
>* [Upgradeprocedure opstellen](../../production/using/build-upgrade.md)
