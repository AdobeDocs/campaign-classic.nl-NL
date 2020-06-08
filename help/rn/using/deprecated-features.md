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
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e46325ab8f68a0b71198aee9cf04f2b1eb97fdd3
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 0%

---


# Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert voortdurend de productmogelijkheden om oudere eigenschappen te identificeren die met modernere alternatieven zouden moeten worden vervangen om algemene klantenwaarde te verbeteren, altijd onder zorgvuldig onderzoek van achterwaartse verenigbaarheid. Naarmate Adobe Campaign Classic met gereedschappen van derden werkt, wordt de compatibiliteit regelmatig bijgewerkt om alleen ondersteunde versies te implementeren. Versies die niet meer compatibel zijn met Adobe Campagne Classic worden hieronder en in de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)weergegeven.

Om de aanstaande verwijdering/vervanging van de Klassieke mogelijkheden van de Campagne mee te delen, zijn de volgende regels van toepassing:

* Aankondiging van afkeuring komt voorop. Hoewel verouderde mogelijkheden nog steeds beschikbaar en ondersteund kunnen worden voor bestaande gebruikers, worden deze niet verder uitgebreid en niet gedocumenteerd.
* Afgekeurde functies worden ten vroegste uit de volgende release verwijderd. De werkelijke doeldatum voor verwijdering wordt op deze pagina aangekondigd.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

>[!NOTE]
>De Adobe Campagnereleases en nieuwe mogelijkheden worden vermeld in de [releaseopmerkingen](../../rn/using/latest-release.md).

## Verouderde functies {#deprecated-features}

Deze sectie maakt een lijst van eigenschappen en mogelijkheden die als verouderd met recentste Klassieke versies van de Campagne zijn gemerkt.

In het algemeen worden functies die in een toekomstige versie moeten worden verwijderd, eerst op afgekeurd ingesteld. Deze eigenschappen en mogelijkheden zijn of niet meer beschikbaar voor nieuwe Klassieke klanten van de Campagne, of zouden niet voor om het even welke nieuwe implementatie moeten worden gebruikt. Ze worden ook verwijderd uit de productdocumentatie.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie/functionaliteit en plannen maken om hun implementatie te wijzigen. Raadpleeg de verwijderingsdatum van het doel om uw omgeving en projectupdates dienovereenkomstig te plannen.

<table> 
 <tbody> 
   <tr>
   <td><strong>Functie</strong></td>
   <td><strong>Vervanging</strong></td> 
  </tr>
   <tr>
  <td>SMS-connectors<br></td>
  <td><p> Vanaf versie 20.2, worden de volgende schakelaars van SMS afgekeurd.<p>
   <ul>
   <li>NetSize</li>
   <li>Generic SMPP (SMPP versie 3.4 die binaire wijze steunt)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>CLX-communicatie</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>Als u één van deze schakelaars gebruikt, moet u uw implementatie dienovereenkomstig aanpassen. <a href="../../delivery/using/sms-channel.md">Meer informatie</a></p> 
  <p>Leer hoe u verouderde connectors in <a href="https://helpx.adobe.com/campaign/kb/sms-connector.html">dit technologie</a>kunt migreren.</p>
  <p><em>Doeldatum verwijdering: 2021</em></p>
  </td> 
 </tr>
  <tr>  
   <td>Faxkanaal<br></td>
   <td><p>Vanaf release 20.2 is het faxkanaal afgekeurd.</p> 
   <p>Als u dit kanaal gebruikt, moet u uw implementatie dienovereenkomstig aanpassen. <a href="../../delivery/using/communication-channels.md">Meer</a> informatie over campagnekanalen.</p>
   <p><em>Doeldatum verwijdering: 2021</em></p></td>
  </tr>
 </tbody> 
</table>

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn verwijderd uit Campagne Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Gebied - functie</strong></td>
   <td><strong>Vervanging</strong></td> 
  </tr> 
   <tr> 
   <td>Archivering van e-mailberichten op basis van bestanden<br></td>
   <td><p>Vanaf de release van Campagne 20.2 is archivering van e-mailbestanden niet meer beschikbaar. E-mailarchivering is nu beschikbaar via een specifiek BCC-e-mailadres. <a href="../../installation/using/email-archiving.md">Meer informatie</a></p></td>
  </tr> 
   <tr> 
   <td>Beheer van leads</td>
   <td><p>Vanaf de release van Campagne 20.2 is het Leads Management-pakket niet meer beschikbaar. Vergelijkbare functionaliteit kan worden geïmplementeerd via andere native workflowactiviteiten en wijzigingen in gegevensmodellen.</p></td>
   </tr>
   <tr>
   <td>Campagne-APIs-documentatie - jsapi.chm-bestand</td>
   <td>Vanaf de startversie van Campagne 19.1 zijn de klassieke API's van de Campagne beschikbaar in een specifieke pagina. Als u het oudere bestand jsapi.chm gebruikte, moet u nu naar <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">de nieuwe onlineversie</a>verwijzen.</td>
  </tr> 
  <tr> 
   <td>Campagnestructuur - Predictieve marketing</td>
   <td>Vanaf de release van Campagne 18.10 zijn de voorspellende marketingmogelijkheden niet meer beschikbaar.</td>
  </tr> 
  <tr> 
   <td>Webtoepassingen - Microsites</td>
   <td>Vanaf de startversie van Campagne 18.10 zijn microsites niet meer beschikbaar. U kunt de beveiliging verbeteren door toegang te beperken tot alleen specifieke domeinen in de configuratiebestanden van Adobe Campagne en gepersonaliseerde URL's in Campagne te gebruiken met behulp van DNS-aliassen. <a href="https://helpx.adobe.com/campaign/kb/domain-name-delegation.html">Meer informatie</a></td>
  </tr> 
  <tr> 
   <td>Push Notifications - iOS Binary Connector</td>
   <td>Conform de aanbeveling van Apple heeft Adobe de oudere iOS Binary Connector verwijderd, die versie 18.10 voor Campaign startte. De meer capabele en efficiëntere HTTP/2-gebaseerde schakelaar is reeds beschikbaar.</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>De aanvang van de versie van Campagne 18.6, om veiligheidsredenen, <em>decryptString</em> API is niet meer beschikbaar door gebrek voor nieuwe installaties.</p> 
   <p>In de context van een postupgrade naar 18.6 (en hoger), wordt deze API niet meer geactiveerd en is deze vervangen door de functie <em>decryptPassword</em> . <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Meer informatie</a></p></td>
  </tr> 
   <tr> 
   <td>Mobiel kanaal - MMS- en WAP-pushberichten</td>
   <td>Vanaf de startversie van Campagne 18.4 zijn MMS- en Wap Push-kanalen niet meer beschikbaar. Als vervanging kunt u <a href="../../delivery/using/sms-channel.md">SMS</a> - en <a href="../../delivery/using/about-mobile-app-channel.md">push</a> -leveringen gebruiken.</td>
  </tr> 
   <tr> 
   <td>Mobiel kanaal - LINE v1</td>
   <td>Vanaf de startversie van Campagne 18.4 is het pakket LINE Connect niet meer beschikbaar. Adobe raadt u aan het nieuwe LINE-kanaalpakket te gebruiken als vervanging. <a href="../../delivery/using/line-channel.md">Meer informatie</a></td>
  </tr> 
 </tbody> 
</table>

## Verouderde compatibiliteit {#deprecated-compatibility}

De volgende systemen zijn verouderd voor Campaign Classic. Raadpleeg de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) om een upgrade naar een nieuwere versie uit te voeren of naar een nieuw systeem te gaan voordat de compatibiliteit wordt beëindigd.

### Adobe Campaign 20.2-release {#compat-20-2-release}

Vanaf versie 20.2 is het volgende systeem verouderd voor Campaign Classic. De compatibiliteit loopt af in 20.3 release - september 2020.

* Clientconsole: Windows 7
* Verouderde SMS-connectors (zie sectie Verouderde functies hieronder)

### Adobe Campaign 19.2-release  {#compat-19-2-release}

Vanaf release 19.2 zijn de volgende besturingssystemen verouderd voor Campaign Classic. De verenigbaarheid zal in 2020 EOY eindigen.

* Webserver: Apache 2.2.
* Besturingssysteem: CentOS 6.

Raadpleeg de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) om een upgrade naar een nieuwere versie uit te voeren of naar een nieuw systeem te gaan.

## Einde van compatibiliteit {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic is compatibel met alle systemen en gereedschappen die in de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)worden vermeld. Wanneer specifieke versies van deze systemen en programma&#39;s van derden het einde van de levensduur (EOL) bereiken met hun respectievelijke makers, is Adobe Campagne niet meer compatibel met die versies: ze worden aangekondigd als afgekeurd en worden dan uit onze compatibiliteitsmatrix verwijderd in de volgende productrelease. Zorg ervoor dat u ondersteunde versies van alle systemen in de compatibiliteitsmatrix gebruikt om problemen te voorkomen.

### Clientconsole {#client-console-eol}

Adobe Campaign Classic Client Console kan niet meer worden uitgevoerd op de volgende systemen, omdat deze zijn vervangen door de editor. Klanten die de Console van de Cliënt van de Campagne op één van deze versies in werking stellen moeten aan recentste versie vóór de datum van de doelverwijdering bevorderen. Raadpleeg de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

>[!NOTE]
>Vanaf de release Campagne 20.1 zijn de Classic Client Console 32-bits van Campagne niet meer compatibel met de nieuwste versies van Campagne. U moet de Console van de Cliënt van 64 beetjes gebruiken.


### Besturingssystemen {#o-s-eol}

Vanaf release 19.1 is Adobe Campaign niet meer compatibel met de volgende besturingssystemen.

* Debian 7. [Meer informatie](https://wiki.debian.org/DebianReleases)
* RHEL 6.x. [Meer informatie](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [Meer informatie](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11. [Meer informatie](https://www.suse.com/lifecycle)

### Webservers {#web-server-eol}

Vanaf de release van 19.1 Spring is Adobe Campaign niet meer compatibel met de volgende webserver.

* Microsoft IIS 7. [Meer informatie](https://support.microsoft.com/en-us/lifecycle/search/810)

### Gereedschappen {#tools-eol}

Vanaf de release van 19.1 Lente is Adobe Campaign niet meer compatibel met de volgende programma&#39;s.

* Java JDK 7. [Meer informatie](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x, behalve wanneer ingesloten in een ander gereedschap. [Meer informatie](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Databasemotoren {#dbe-eol}

Adobe biedt geen ondersteuning voor de volgende database-engines, omdat deze zijn vervangen door de editor. Klanten die in deze versies werken, moeten een upgrade uitvoeren naar de nieuwste versie of naar een andere versie.

Verwijs naar de [Klassieke matrijs](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) van de Verenigbaarheid van de Campagne om tot de lijst van compatibele versies toegang te hebben.

**FEDERATED DATA ACCESS (FDA)**

Vanaf de 19.1-lenteversie is Adobe-campagne niet meer compatibel met de volgende FDA-servers.

* PostgreSQL 9.3. [Meer informatie](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [Meer informatie](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [Meer informatie](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Gegevens 14 - 14.1. [Meer informatie](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campagne Classic is niet compatibel met de volgende servers in FDA (Federated Data Access).

* DB2 UDB 9.5, 9.7. Recentere versie van DB2 wordt gesteund door Federated Data Access (FDA). [Meer informatie](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i, 10G R2. Recentere versies van Oracle worden ondersteund via FDA (Federated Data Access). [Meer informatie](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Recentere versies van PostgreSQL worden gesteund door Federated Data Access (FDA). [Meer informatie](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005, 2008 R2. Recentere versies van SQL Server worden gesteund door Federated Data Access (FDA). [Meer informatie](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1. Recentere versies van MySQL worden ondersteund via FDA (Federated Data Access). [Meer informatie](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB heeft het einde van de levensduur bereikt. [Meer informatie](https://www.mysql.com/support)
* Gegevens 13, 13.1. Recentere versies van Teradata worden ondersteund via FDA (Federated Data Access). [Meer informatie](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0. Netezza bereikte het einde van zijn leven. [Meer informatie](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData bereikte het einde van de levensduur. [Meer informatie](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4, 15.5 en Sybase ASE 15.0. Recentere versies van Sybase worden ondersteund via FDA (Federated Data Access). [Meer informatie](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic biedt nog steeds ondersteuning voor de vermelde versies van Hadoop via HiveSQL via FDA (Federated Data Access), maar deze versies zijn samengevoegd met: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) en HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS SERVER**

Adobe Campagne is niet compatibel met de volgende RDBMS-servers:
* Oracle 10GR2
* PostgreSQL 9.0 tot 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
