---
product: campaign
title: Compatibiliteitsmatrix voor Campaign Classic
description: Campaign Classic-compatibiliteitsmatrix
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: a94c361c5bdd9d61ae9232224af910a78245a889
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 99%

---

# Compatibiliteitsmatrix{#compatibility-matrix}



Dit document bevat een lijst met alle systemen en onderdelen die worden ondersteund voor [de nieuwste versie](../../rn/using/latest-release.md) van **Adobe Campaign Classic v7**. Producten en versies die niet in deze lijst staan, zijn niet compatibel met Adobe Campaign.

Als u een [!DNL Gold Standard]-gebruiker bent, raadpleegt u de [[!DNL Gold Standard] -compatibiliteitsmatrix](../../rn/using/gold-standard.md#compatibility-matrix-gs).

## Belangrijke opmerkingen{#important-notes}

Tenzij anders vermeld worden alle kleine releases ondersteund.

De [meest recente build](../../rn/using/latest-release.md) van Adobe Campaign Classic is compatibel met alle systemen en tools die op deze pagina worden vermeld. Wanneer specifieke versies van deze externe systemen en tools het einde van de levensduur bereiken bij hun respectieve makers, is Adobe Campaign niet meer compatibel met deze versies. Ze worden dan in de volgende productrelease uit onze compatibiliteitsmatrix verwijderd. Zorg ervoor dat u ondersteunde versies van alle systemen in de compatibiliteitsmatrix gebruikt om problemen te voorkomen.

Ga naar [deze pagina](../../rn/using/deprecated-features.md) voor meer informatie over verouderde items.

>[!CAUTION]
>
>Deze matrix wordt regelmatig bijgewerkt door toevoeging van nieuwe ondersteunde items en verwijdering van verouderde items.

## Besturingssystemen{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>7.x</p>
<p><strong>Belangrijk:</strong> als u RHEL gebruikt, moet u bereid zijn om SELinux uit te schakelen of uw architecten aangepaste SELinux-regels te laten schrijven om te controleren of een ingeschakelde SELinux-versie geen problemen veroorzaakt met Campaign-activiteiten.</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11 (vanaf Campaign v7.3)</p>
<p>10</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x</p>
<p>7.x</p>
<p><strong>Belangrijk:</strong> als u RHEL gebruikt, moet u bereid zijn om SELinux uit te schakelen of uw architecten aangepaste SELinux-regels te laten schrijven om te controleren of een ingeschakelde SELinux-versie geen problemen veroorzaakt met Campaign-activiteiten.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2019 (vanaf Campaign v7.2)</p>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
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
<p>10.0 op Windows Server 2016 en 2019</p>
<p>8.5 op Windows Server 2012 R2</p>
<p>8.0 op Windows Server 2012 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 voor RHEL7 - CentOS 7, Debian 8/9, Windows</p>
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
<p>11</p>
<p>9</p>
<p>8</p>
<p>Campaign ondersteunt de Java Development Kit (JDK) die is ontwikkeld door Oracle, en OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>7 (en vorige versies indien ingesloten in uw systeem)</p>
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

## Relation Database Management Systems (RDBMS){#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x (vanaf Campaign v7.3.2)</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p><strong>Opmerking:</strong> u kunt ook Amazon RDS voor PostgreSQL gebruiken met de hierboven vermelde versies.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 en SP2</p>
<p><strong>Belangrijk:</strong> Microsoft SQL Server wordt niet als de primaire database ondersteund wanneer de Campaign-server op Linux wordt uitgevoerd. <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/installing-campaign-in-linux-/prerequisites-of-campaign-installation-in-linux.html?lang=nl#database-access-layers">Meer informatie</a>.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* Het RDBMS-stuurprogramma moet overeenkomen met de RDBMS-serverversie.
>
>* PostgreSQL is de RDBMS voor gehoste omgevingen.

## CRM-connectoren{#CRMconnectors}

Hieronder vindt u de Customer Relationship Management-systemen (CRM) die compatibel zijn met Adobe Campaign. [Leer meer](../../platform/using/crm-connectors.md) over de Campaign CRM-connectoren.

<table>
<tbody>
<tr>
<td>Salesforce-connector-API</td>
<td>
<p>API-versie 49</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics-connector</td>
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
<td><strong>Campaign-versie</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>v7.0 minimaal 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>Minimaal 7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 minimaal 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>Minimaal 7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>v7.0 minimaal 19.1.4</td>
</tr>
</tbody>
</table>

Daarnaast kunnen **Hybride**- en **On-Premise**-omgevingen Campaign ook verbinding maken met de volgende externe databasesystemen. Deze systemen zijn **niet compatibel** met (door) Campaign **Managed Services** (gehoste) omgevingen.

<table>
<tbody>
<td><strong>Databasesysteem</strong></td>
<td><strong>Databaseversie</strong></td>
<td><strong>Campaign-versie</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td>v7.0 minimaal 19.1.4</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3 minimaal </p>
<p>Minimaal V7.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
<td>Minimaal V7.0</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>Minimaal V7.0</p>
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
<td>Minimaal V7.0</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 en SP2</p>
</td>
<td>Minimaal V7.0</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td>Minimaal V7.0</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (laatste versie)</p>
</td>
<td>Minimaal V7.0</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td>Minimaal V7.0</td>
</tr>
</tbody>
</table>



## Clientconsole {#ClientConsoleoperatingsystems}

De volgende besturingssystemen en browsers zijn **vereist** om de [Campaign-clientconsole](../../installation/using/installing-the-client-console.md) te gebruiken.

### Besturingssystemen

<table>
<tbody>
<td><strong>Systeem</strong></td>
<td><strong>Besturingssysteemversie</strong></td>
<td><strong>Campaign-versie</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
<p>8</p>
</td>
<td>
<p>minimaal v7.3 </p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2019</p>
<p>2016</p>
<p>2012</p>
</td>
<td>
<p>v7.2.1 minimaal </p>
<p></p>
<p></p>
</tbody>
</table>

### Microsoft WebView2-runtime

Microsoft Edge WebView2-runtime de nieuwste versie is verplicht voor de Campaign-clientconsole.

Download Microsoft Edge WebView2 van [Microsoft Developer-site](https://www.adobe.com/go/acc-ms-webview2-runtime-download).


## Mobiele SDK{#MobileSDK}

U kunt Campaign gebruiken om [pushmeldingen](../../delivery/using/about-mobile-app-channel.md) te verzenden op de hieronder vermelde besturingssystemen met de bijbehorende [mobiele SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

U kunt de Adobe Experience Platform Mobile SDK ook gebruiken door de Adobe Campaign-extensie te configureren in de gebruikersinterface voor dataverzameling.

<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>12 (vanaf Campaign v7.3), 9.0, 8.x, 7.x</p>
<p>met mobiele SDK-build 1.1.1</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 15</p>
<p>met mobiele SDK-build 1.0.26, compatibel met de 32-bits en de 64-bits versie. iOS 15 wordt ondersteund vanaf Campaign v7.3</p>
</td>
</tr>
</tbody>
</table>

## Browsers{#Browsers}

De volgende browsers, in hun meest recente versie, zijn compatibel met Campaign voor [Webtoegang](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



## Wellicht ook interessant{#Morelikethis}

* [Aanvullende informatie voor Campaign Classic](../../rn/using/latest-release.md)
* [Algemene Campaign-architectuur](../../installation/using/general-architecture.md)
* [Aanbevelingen voor hardwareaanpassing](../../technotes/using/hardware-sizing.md)
* [Verouderde functies en systemen](../../rn/using/deprecated-features.md)
* [Upgradeprocedure opstellen](../../production/using/build-upgrade.md)
