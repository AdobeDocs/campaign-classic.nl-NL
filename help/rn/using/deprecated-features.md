---
title: Afgekeurde en verwijderde Campagne Classic-functies
description: Deze pagina bevat een lijst met vervangen en verwijderde functies van Adobe Campagne Classic
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
discoiquuid: null
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be148d7cd55097b9014d2f4d3b095c65a5ca8c54
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 0%

---


# Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert voortdurend de productmogelijkheden om oudere eigenschappen te identificeren die met modernere alternatieven zouden moeten worden vervangen om algemene klantenwaarde te verbeteren, altijd onder zorgvuldig onderzoek van achterwaartse verenigbaarheid. Naarmate Adobe Campaign Classic met gereedschappen van derden werkt, wordt de compatibiliteit regelmatig bijgewerkt om alleen ondersteunde versies te implementeren. Versies die niet meer compatibel zijn met Adobe Campagne Classic worden hieronder weergegeven.

Om de aanstaande verwijdering/vervanging van de Klassieke mogelijkheden van de Campagne mee te delen, zijn de volgende regels van toepassing:

* Aankondiging van afkeuring komt voorop. Hoewel verouderde mogelijkheden nog steeds beschikbaar kunnen zijn voor bestaande gebruikers, worden ze niet verder uitgebreid of gedocumenteerd.
* Afgekeurde functies worden ten vroegste uit de volgende release verwijderd. De werkelijke doeldatum voor verwijdering wordt op deze pagina aangekondigd.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

>[!NOTE]
>De Adobe Campagnereleases en nieuwe mogelijkheden worden vermeld in de [releaseopmerkingen](../../rn/using/latest-release.md).


## Verouderde functies {#deprecated-features}

Deze sectie maakt een lijst van eigenschappen en mogelijkheden die als verouderd met recentste Klassieke versies van de Campagne zijn gemerkt.

In het algemeen worden functies die in een toekomstige versie moeten worden verwijderd, eerst vervangen door een alternatief. Deze eigenschappen en mogelijkheden zijn of niet meer beschikbaar voor nieuwe Klassieke klanten van de Campagne, of zouden niet voor om het even welke nieuwe implementatie moeten worden gebruikt. Ze worden ook verwijderd uit de productdocumentatie.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie/mogelijkheid en plannen te maken om hun implementatie te wijzigen en het geboden alternatief te gebruiken. Raadpleeg de verwijderingsdatum van het doel om uw omgeving en projectupdates dienovereenkomstig te plannen.

### Adobe Campaign 18.6-release {#ac-18-6-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Gebied</strong></td>
   <td><strong>Functie</strong></td> 
   <td><strong>Vervanging</strong></td> 
  </tr> 
   <tr> 
   <td>Javascript SDK-beveiliging<br> </td>
   <td>decryptString<br> </td>
   <td><p>Om veiligheidsredenen is de <em>decryptString</em> -API niet meer standaard beschikbaar voor nieuwe installaties.</p> 
   <p>In de context van een postupgrade naar 18.6 (en hoger), wordt deze API niet meer geactiveerd en is deze vervangen door de functie <em>decryptPassword</em> .</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign 18.4-release {#ac-18-4-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Gebied</strong></td>
   <td><strong>Functie</strong></td> 
   <td><strong>Vervanging</strong></td> 
  </tr> 
   <tr> 
   <td>E-mailarchivering<br> </td>
   <td>Archivering op basis van bestanden<br> </td>
   <td><p>E-mailarchivering is nu beschikbaar via een specifiek BCC-e-mailadres. <a href="../../installation/using/email-archiving.md">Meer</a>informatie.</p> 
   <p><em>Doeldatum verwijdering: Release van campagne 20.2 - juni 2020</em></p><br> </td>
  </tr> 
   <tr> 
   <td>Beheer van leads<br> </td>
   <td>Leads<br> </td>
   <td><p>Het beheerpakket voor leads in Adobe Campaign Classic vereenvoudigt het proces voor het maken en onderhouden van de volledige levenscyclus van het leads-beheer. Vergelijkbare functionaliteit kan worden geïmplementeerd via andere native workflowactiviteiten en wijzigingen in gegevensmodellen.</p> 
   <p><em>Doeldatum verwijdering: Release van campagne 20.2 - juni 2020</em></p><br> </td>
  </tr> 
 </tbody> 
</table>


## Verouderde compatibiliteit {#deprecated-compatibility}

### Adobe Campaign 20.1-release {#compat-20-1-release}

Vanaf 20.1 Februari Versie, is het volgende systeem verouderd voor de Klassieke Campagne. De compatibiliteit loopt af in de release van 20.2 - juni 2020.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Gebied</strong></td>
   <td><strong>Vervanging</strong></td> 
  </tr> 
   <tr> 
   <td>Campagne Classic Client Console 32 bits<br> </td>
   <td><p>Campagne Classic Client Console 64 bits</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign 19.2-release  {#compat-19-2-release}

Vanaf 19.2 Fall Release zijn de volgende besturingssystemen verouderd voor Campaign Classic. De verenigbaarheid zal in 2020 EOY eindigen.

* Webserver: Apache 2.2. [Meer informatie](https://wiki.centos.org/About/Product)
* Besturingssysteem: CentOS 6. [Meer informatie](https://wiki.centos.org/About/Product)

Raadpleeg de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) om een upgrade naar een nieuwere versie uit te voeren of naar een nieuw systeem te gaan.

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn verwijderd uit Campagne Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Gebied - functie</strong></td>
   <td><strong>Vervanging</strong></td> 
   <td><strong>Versie</strong></td> 
  </tr> 
   <tr> 
   <td>Campagne-APIs-documentatie - jsapi.chm-bestand<br> </td>
   <td>Klassieke API's voor campagnes zijn nu beschikbaar in een speciale pagina. Als u het bestand jsapi.chm gebruikte, moet u nu naar <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">de nieuwe onlineversie</a>verwijzen.</td>
   <td>19.1</td>
  </tr> 
  <tr> 
   <td>Campagnestructuur - Predictieve marketing</td>
   <td>Een groot deel van de voorspellende marketingmogelijkheden in Adobe Campaign Classic is het gebruik van voorspellende modellen. Hoewel de voorspellende activiteit van de marketing werkschemaactiviteit in een aanstaande versie zal worden verwijderd, zal de Campagne van Adobe het gebruik en het gebruik van voorspellende modellen uit externe bronnen door andere werkschemaactiviteiten blijven steunen.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Webtoepassingen - Microsites</td>
   <td>Verbeter de beveiliging door de toegang te beperken tot alleen specifieke domeinen in de configuratiebestanden van Adobe Campagne. U kunt gepersonaliseerde URLs in Campagne nog gebruiken door DNS aliassen te gebruiken. <a href="https://helpx.adobe.com/campaign/kb/domain-name-delegation.html">Meer</a>informatie.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Push Notifications - iOS Binary Connector<br> </td>
   <td>Conform de aanbeveling van Apple verwijdert Adobe de oudere iOS Binary Connector. De meer capabele en efficiëntere HTTP/2-gebaseerde schakelaar is reeds beschikbaar.</td>
   <td>18.10</td>
  </tr> 
   <tr> 
   <td>Mobiel kanaal - MMS- en WAP-pushberichten</td>
   <td>MMS- en Wap Push-kanalen zijn niet meer beschikbaar. Als vervanging kunt u <a href="../../delivery/using/sms-channel.md">SMS</a> - en <a href="../../delivery/using/about-mobile-app-channel.md">push</a> -leveringen gebruiken.</td>
   <td>18.4</td>
  </tr> 
   <tr> 
   <td>Mobiel kanaal - LINE v1</td>
   <td>Het pakket LINE Connect kan niet meer worden geïnstalleerd in Adobe Campagne Classic. Adobe raadt u aan het nieuwe LINE-kanaalpakket te gebruiken voor het verzenden van LINE-berichten. <a href="../../delivery/using/line-channel.md">Meer</a>informatie.</td>
   <td>18.4</td>
  </tr> 
 </tbody> 
</table>

## Einde van compatibiliteit {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic is compatibel met alle systemen en gereedschappen die in de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)worden vermeld. Wanneer specifieke versies van deze systemen en programma&#39;s van derden het einde van de levensduur (EOL) bereiken met hun respectievelijke makers, is Adobe Campagne niet meer compatibel met die versies: ze worden aangekondigd als afgekeurd en worden dan uit onze compatibiliteitsmatrix verwijderd in de volgende productrelease. Zorg ervoor dat u ondersteunde versies van alle systemen in de compatibiliteitsmatrix gebruikt om problemen te voorkomen.

### Clientconsole {#client-console-eol}

Adobe Campaign Classic Client Console kan niet meer worden uitgevoerd op de volgende systemen, omdat deze zijn vervangen door de editor. Klanten die de Console van de Cliënt van de Campagne op één van deze versies in werking stellen moeten aan recentste versie vóór de datum van de doelverwijdering bevorderen. Raadpleeg de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

### Besturingssystemen {#o-s-eol}

Vanaf release 19.1 is Adobe Campaign niet meer compatibel met de volgende besturingssystemen.

* Debian 7. [Meer](https://wiki.debian.org/DebianReleases)informatie.
* RHEL 6.x. [Meer](https://access.redhat.com/support/policy/updates/errata)informatie.
* Windows Server 2008. [Meer](https://support.microsoft.com/en-us/lifecycle/search/1163)informatie.
* SLES 11. [Meer](https://www.suse.com/lifecycle)informatie.

### Webservers {#web-server-eol}

Vanaf de release van 19.1 Spring is Adobe Campaign niet meer compatibel met de volgende webserver.

* Microsoft IIS 7. [Meer](https://support.microsoft.com/en-us/lifecycle/search/810)informatie.

### Gereedschappen {#tools-eol}

Vanaf de release van 19.1 Lente is Adobe Campaign niet meer compatibel met de volgende programma&#39;s.

* Java JDK 7. [Meer](http://www.oracle.com/technetwork/java/javase/eol-135779.html)informatie.
* Libre Office 3.5 / 4.3 / 5.x, behalve wanneer ingesloten in een ander gereedschap. [Meer](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)informatie.

### Databasemotoren {#dbe-eol}

Adobe biedt geen ondersteuning voor de volgende database-engines, omdat deze zijn vervangen door de editor. Klanten die in deze versies werken, moeten een upgrade uitvoeren naar de nieuwste versie of naar een andere versie.

Verwijs naar de [Klassieke matrijs](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) van de Verenigbaarheid van de Campagne om tot de lijst van compatibele versies toegang te hebben.

**FEDERATED DATA ACCESS (FDA)**

Vanaf de 19.1-lenteversie is Adobe-campagne niet meer compatibel met de volgende FDA-servers.

* Oracle 11G. [Meer](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)informatie.
* PostgreSQL 9.3. [Meer](https://www.postgresql.org/support/versioning)informatie.
* MySQL 5.5. &lt;[Meer](http://www.fromdual.com/support-for-mysql-from-oracle)informatie.
* DB2 9.5. [Meer](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)informatie.
* Gegevens 14 - 14.1. [Meer](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)informatie.

Campagne Classic is niet compatibel met de volgende servers in FDA (Federated Data Access).

* DB2 UDB 9.5, 9.7. Recentere versie van DB2 wordt gesteund door Federated Data Access (FDA). [Meer](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)informatie.
* Oracle 9i, 10G R2. Recentere versies van Oracle worden ondersteund via FDA (Federated Data Access). [Meer](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)informatie.
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Recentere versies van PostgreSQL worden gesteund door Federated Data Access (FDA). [Meer](https://www.postgresql.org/support/versioning)informatie.
* MSSQL 2000, 2005, 2008 R2. Recentere versies van SQL Server worden gesteund door Federated Data Access (FDA). [Meer](https://support.microsoft.com/en-us/lifecycle/search/1044)informatie.
* MySQL 5.1. Recentere versies van MySQL worden ondersteund via FDA (Federated Data Access). [Meer](https://en.wikipedia.org/wiki/InfiniDB)informatie.
* InfiniDB heeft het einde van de levensduur bereikt. [Meer](https://www.mysql.com/support)informatie.
* Gegevens 13, 13.1. Recentere versies van Teradata worden ondersteund via FDA (Federated Data Access). [Meer](https://www.info.teradata.com/download.cfm?ItemID=1007255)informatie.
* Netezza 6.02, 7.0. Netezza bereikte het einde van zijn leven. [Meer](https://en.wikipedia.org/wiki/Netezza)informatie.
* AsterData 5.0. AsterData bereikte het einde van de levensduur. [Meer](https://en.wikipedia.org/wiki/Aster_Data_Systems)informatie.
* Sybase IQ 15.2, 15.4, 15.5 en Sybase ASE 15.0. Recentere versies van Sybase worden ondersteund via FDA (Federated Data Access). [Meer](https://sites.google.com/site/dbatipsandtricks/time-tracker)informatie.
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic biedt nog steeds ondersteuning voor de vermelde versies van Hadoop via HiveSQL via FDA (Federated Data Access), maar deze versies zijn samengevoegd met: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) en HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS SERVER**

Adobe Campagne is niet compatibel met de volgende RDBMS-servers:
* Oracle 10GR2, 11G
* PostgreSQL 9.0 tot 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
