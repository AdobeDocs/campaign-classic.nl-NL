---
product: campaign
title: '[!DNL Gold Standard]-releases '
description: Aanvullende informatie en compatibiliteitsmatrix voor Campaign Classic [!DNL Gold Standard]
feature: Release Notes
role: User
level: Beginner
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1774'
ht-degree: 100%

---

# [!DNL Gold Standard]-releases {#gold-standard}



Op deze pagina vindt u aanvullende informatie en compatibiliteitsmatrix voor [!DNL Gold Standard]-releases.

## [!DNL Gold Standard] Aanvullende informatie


### [!DNL Gold Standard] release 12{#gs-12}

[!BADGE Afgeschaft]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Afgeschaft"}

_7 september 2021_

Versie 9032@554dbcd bevat de volgende oplossing:

* Probleem verholpen waarbij een fout 500 optrad wanneer de koppeling naar een webapplicatie werd geopend in de vorm van een levering in een lijn waarbij tracking was ingeschakeld.

_27 augustus 2021_

Versie 9032@99a3894 bevat de volgende oplossingen:

* De functie voor het bijhouden van handtekeningen is verbeterd om fouten te voorkomen die gekoppeld zijn aan tools van derden (klant-e-mail, internetbrowsers, enz.) speciale tekens gebruiken. URL-parameters zijn nu gecodeerd.
* Probleem verholpen met datumpickers waardoor een console een foutbericht over een blokkering weergaf. (NEO-36345)

### [!DNL Gold Standard] Release 11{#gs-11}

[!BADGE Afgeschaft]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Afgeschaft"}

_14 april 2021_

De build 9032@d030c36 bevat de volgende oplossing:

* Er is een probleem met een regressie van de clientconsole opgelost die tot permanente foutberichten op het IMS-verbindingsscherm leidde. (NEO-34821)
* Deze consoleversie is vereist om [IMS-toegang](../../technotes/using/ims-updates.md) te behouden.

**Alleen de console-upgrade is verplicht. Er is geen serverupgrade vereist.**

>[!CAUTION]
>
> * Als u verbinding maakt met Campaign met uw Adobe ID, via Adobe Identity Management Service (IMS), is een upgrade verplicht voor zowel de Campaign-server als de klantconsole om verbinding te kunnen maken met Campaign na **30 juni 2021**. [Meer informatie](../../technotes/using/ims-updates.md)
> * Deze release wordt geleverd met een [oplossing voor een beveiligingsprobleem](https://helpx.adobe.com/nl/security/products/campaign/apsb21-04.html): een upgrade is verplicht om de beveiliging van uw IT-omgeving te versterken.
> * Als u via oAuth-verificatie de Experience Cloug Triggers-integratie gebruikt, moet u overstappen op Adobe I/O zoals [op deze pagina](../../integrations/using/configuring-adobe-io.md) wordt beschreven. De verouderde oAuth-authentificatiemodus met Campaign [is beëindigd](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) in **september 2021**. Gehoste omgevingen profiteren van een verlenging tot **23 februari 2022**. Als een on-premise of hybride klant neemt u contact op met de klantenservice van Adobe om de ondersteuning te verlengen tot februari 2022. U moet de [AppID van de OAuth-applicatie](../../integrations/using/configuring-pipeline.md#step-optional) aan Adobe verstrekken.
>
>Meer informatie in de [[!DNL Gold Standard] sectie](../../rn/using/gold-standard.md)

_2 maart 2021_

De build 9032@10c2709 bevat de volgende oplossing:

* Er is een regressie opgelost die verhinderde dat bepaalde onderdelen van de console konden worden gebruikt, zoals de datumkiezer en afbeeldingsbeheer in verzendingen. (NEO-31453, NEO-31454)

**Alleen de console-upgrade is verplicht. Er is geen serverupgrade vereist.**

>[!NOTE]
>
> Maak verbinding met [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) om de nieuwe versie te downloaden. [Op deze pagina ](../../installation/using/client-console-availability-for-windows.md) leert u hoe u de console-update aan alle eindgebruikers kunt voorstellen.

_22 december 2020_

De build 9032@d3b452f bevat de volgende verbeteringen en oplossingen:

* Het verbindingsprotocol is bijgewerkt en aangepast aan het nieuwe IMS-verificatiemechanisme.

* De Triggers-integratieverificatie die oorspronkelijk was gebaseerd op de oAUTH-verificatieset-up voor toegang tot de pipeline is nu gewijzigd en verplaatst naar Adobe I/O. [Meer informatie](../../integrations/using/configuring-adobe-io.md)

* Nu het [verouderde binaire protocol voor iOS APN’s niet meer wordt ondersteund](https://developer.apple.com/news/?id=c88acm2b), zijn alle instanties die dit protocol gebruiken, bijgewerkt naar het HTTP/2-protocol tijdens de postupgrade.

* Er is een beveiligingsprobleem opgelost ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-27777)

* Probleem verholpen waarbij workflows konden mislukken wanneer een activiteit **Verrijking** werd uitgevoerd. (NEO-17338)

### [!DNL Gold Standard] Release 10{#gs-10}

[!BADGE Afgeschaft]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Afgeschaft"}

_7 juli 2020_

De build 9032@efd8a94 bevat de volgende oplossing:

Er is een probleem verholpen waarbij tracking niet werkte als de handtekeningfunctie was uitgeschakeld. (NEO-26411)

>[!CAUTION]
>
>Wij adviseren u de clientconsole bij te werken met de beschikbare console in deze release. Zie [deze pagina](../../installation/using/installing-the-client-console.md)

### [!DNL Gold Standard] Release 9{#gs-9}

[!BADGE Afgeschaft]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Afgeschaft"}

_22 juni 2020_

De build 9032@800be2e bevat de volgende oplossingen:

* De iOS HTTP2-connector is verbeterd (updates van derden en foutbeheer). (NEO-25904, NEO-25903, NEO-25799)

De volgende correcties betreffen het beveiligingsmechanisme voor koppelingen bijhouden (meer informatie vindt u in de [checklist voor beveiliging en privacy](https://helpx.adobe.com/nl/campaign/kb/acc-security.html#signature-mechanism)):

* Er is een probleem verholpen waardoor tracking van ‘berichtklikken’ niet kon worden uitgevoerd (iOS- en Android-pushmeldingen). (NEO-25965)
* Er is een probleem verholpen waardoor u tracking-URL’s niet kon openen of er niet op kon klikken bij gebruik van bepaalde oudere versies van Outlook. (NEO-25688)
* Er is een probleem verholpen waarbij de tracking van URL’s met fragmenten in personalisatieparameters (ankerlabels met pondteken) niet werkte. (NEO-25774)
* Er is een probleem verholpen met de antiphishingservice. (NEO-25283)
* Er is een probleem verholpen met tracking bij gebruik van specifieke aangepaste trackingformules. (NEO-25277)

### [!DNL Gold Standard] release 8{#gs-8}

[!BADGE Afgeschaft]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Afgeschaft"}

_29 april 2020_

De build 9032@3a9dc9c bevat de volgende oplossingen:

* Verbeterde beveiliging voor tracking van koppelingen in e-mails. Dit is standaard ingeschakeld voor alle klanten. Er is een extra, verbeterde beveiligingsfunctie beschikbaar die kan worden ingeschakeld door contact op te nemen met de klantenservice. Meer informatie over de functie en de stappen die niet-gehoste klanten moeten uitvoeren, vindt u in de [Controlelijst voor beveiliging en privacy](https://helpx.adobe.com/nl/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Als u problemen hebt met pushmeldingen via trackingkoppelingen, of leveringen die ankerlabels gebruiken, raden we u aan het nieuwe handtekeningmechanisme voor tracking van koppelingen uit te schakelen. De procedure wordt [op deze pagina](https://helpx.adobe.com/nl/campaign/kb/acc-security.html#signature-mechanism) nader beschreven

* Er is een probleem verholpen waarbij afbeeldingen niet konden worden weergegeven in Line-leveringen. (NEO-23207)
* Probleem verholpen met de activiteit **Bestand overdragen** waardoor verificatie op basis van SFTP-sleutels niet kon werken op Debian 9. (NEO-23183)
* Er is een probleem verholpen in verband met pushmeldingen wanneer deze op een hoge frequentie werden verzonden. (NEO-20516)
* Er is een probleem verholpen in responsbeheer voor aanbiedingen waardoor de webserver kon vastlopen. (NEO-19482)
* Er is een fout verholpen in het beheer van LibreOffice waardoor u rapporten niet kon exporteren. (NEO-20982)
* Er is een probleem verholpen dat een fout veroorzaakte bij het upgraden van een groot aantal workflows via een enquêteactiviteit.
* LibreOffice-beheer is verbeterd om fouten in de voorvertoning van e-mails met .odt-bestanden te voorkomen.
* Beheer van de Apache-verbinding is verbeterd om latentie op de webservice te voorkomen.
* De weergave van versietags (7 cijfers) in het menu **Info** is verbeterd.
* Er is een regressie verholpen in lijstbeheer waardoor aanbiedingen niet konden worden gepubliceerd.
* Oplossing voor een regressie die ertoe leidde dat de opschoningsworkflow vastliep.
* Oplossing voor een kleine regressie in de logboeken van de opschoningsworkflow.

### [!DNL Gold Standard] release 6{#gs-6}

[!BADGE Afgeschaft]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Afgeschaft"}

_9 maart 2020_

De build 9032@19f73c5 bevat de volgende oplossing:

* Probleem met externe accounts met FTP via SSL opgelost. (NEO-20498)

### [!DNL Gold Standard] release 5{#gs-5}

[!BADGE Afgeschaft]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Afgeschaft"}

_17 december 2019_

De build 9032@d6b8062 bevat de volgende oplossing:

* Er is een trackingprobleem verholpen op de volgende communicatiekanalen: mobiel (sms, mms), push (iOS, Android) en sociale netwerken (Facebook, X, voorheen Twitter). (NEO-19595)

### [!DNL Gold Standard] release 4{#gs-4}

[!BADGE Afgeschaft]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Afgeschaft"}

_11 december 2019_

De build 9032@bc4a935 bevat de volgende oplossing:

* Er is een prestatieprobleem verholpen met het verzenden van berichten met een MSSQL-database. (NEO-17558)

### [!DNL Gold Standard] release 3{#gs-3}

[!BADGE Afgeschaft]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Afgeschaft"}

_20 november 2019_

De build 9032@3468c7b bevat de volgende oplossingen:

* Er is een aanmeldingsprobleem via IMS-verificatie verholpen. (NEO-17312)
* Er is een probleem verholpen met het weergeven van cumulatieve rapporten over meerdere leveringen. (NEO-18165)
* Er is een probleem verholpen waarbij de webserver geblokkeerd kon raken of vastlopen.

### [!DNL Gold Standard] release 2{#gs-2}

[!BADGE Afgeschaft]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Afgeschaft"}

_19 september 2019_

De build 9032@cee805c bevat de volgende oplossingen:

* Er is een probleem verholpen met het gebruik van de CRM-connector voor Salesforce. (NEO-17712)
* Er is een indexprobleem verholpen dat prestatieproblemen kon veroorzaken bij het verzenden van transactieberichten.

### Release 19.1.4 - build 9032{#release-19-1-4-build-9032}

[!BADGE Afgeschaft]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Afgeschaft"}

_13 augustus 2019_

De eerste 19.1.4-build bevat de volgende oplossingen:

* Er is een probleem verholpen met de planneractiviteit die ongewenste foutberichten genereerde tijdens de configuratie van de wizard. Update van NEO-11662 is teruggedraaid. (NEO-17097)
* Er is een regressie verholpen die werd veroorzaakt door NEO-12727 en die kon leiden tot het stoppen van workflows als een Test-activiteit tweemaal werd uitgevoerd. (NEO-16835)
* Er is een probleem verholpen waardoor een onjuiste HTTP-code werd geretourneerd (HTTP 200 OK in plaats van HTTP 403 Verboden) wanneer een ongeldig of verlopen sessietoken werd gebruikt in API-aanroepen. (NEO-16826)
* Er is een probleem verholpen met de DKIM-sleutel die niet meer in e-mails werd ingesloten, waardoor leveringsproblemen ontstonden. (NEO-16804)
* Er zijn diverse problemen met workflowplanning verholpen. Workflows werden gepland om één keer per dag te worden uitgevoerd zonder rekening te houden met de plannerconfiguratie. (NEO-16619, NEO-16426)


## [!DNL Gold Standard] Compatibiliteitsmatrix{#compatibility-matrix-gs}

Dit gedeelte bevat een lijst met alle systemen en onderdelen die worden ondersteund voor **Adobe Campaign Classic[!DNL Gold Standard]** 19.1-builds. Producten en versies die niet in deze lijst staan, zijn niet compatibel met deze versie van Adobe Campaign.

>[!CAUTION]
>Tenzij anders vermeld worden alle kleine releases ondersteund.
>
>Adobe Campaign Classic is compatibel met alle systemen en tools die op deze pagina worden vermeld. Wanneer specifieke versies van deze externe systemen en tools het einde van de levensduur bereiken bij hun respectieve makers, is Adobe Campaign niet meer compatibel met deze versies. Ze worden dan in de volgende productrelease uit onze compatibiliteitsmatrix verwijderd. Zorg ervoor dat u ondersteunde versies van alle systemen in de compatibiliteitsmatrix gebruikt om problemen te voorkomen.
>

### Besturingssystemen{#OperatingSystems-gs}

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
<p><strong>Belangrijk:</strong> als u RHEL gebruikt, moet u bereid zijn om SELinux uit te schakelen of uw architecten aangepaste SELinux-regels te laten schrijven om te controleren of een ingeschakelde SELinux-versie geen problemen veroorzaakt met Campaign-activiteiten.</p>
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

### Webservers{#WebServers-gs}

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

### Tools{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
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

### RDBMS-servers{#RDBMSservers-gs}

>[!NOTE]
>
>Het RDBMS-stuurprogramma moet overeenkomen met de RDBMS-serverversie.

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
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>Opmerking: u kunt ook Amazon RDS voor PostgreSQL gebruiken met de hierboven vermelde versies.</p>
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
<p>Waarschuwing: Microsoft SQL Server wordt niet als de primaire database ondersteund wanneer de Campaign-server op Linux wordt uitgevoerd.</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>Waarschuwing: DB2 UDB is voor nieuwe installaties niet toegestaan.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL is de standaard databaseserver voor gehoste omgevingen.

### CRM-connectoren{#CRMconnectors-gs}

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
<p>API-versie 21</p>
<p>API-versie 15</p>
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

### Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
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
<p>9.6.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 en SP2</p>
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

### Clientconsole {#ClientConsoleoperatingsystems}

`:warning:` De volgende besturingssystemen en browser zijn vereist om de Campaign Client Console te gebruiken.

#### Besturingssystemen

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10 (aanbevolen voor Japanse instanties)</p>
</td>
</tr>
</tbody>
</table>

#### Browser

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

### Mobiele SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x, 8.x, 9.0</p>
<p>met mobiele SDK-build 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>met mobiele SDK-build 1.0.26, compatibel met de 32-bits en de 64-bits versie.</p>
</td>
</tr>
</tbody>
</table>

### Browsers{#Browsers}

De volgende browsers zijn compatibel met Campaign voor toegang tot internet.

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>Laatste versie</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>Laatste versie</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>Laatste versie</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>Laatste versie</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>
