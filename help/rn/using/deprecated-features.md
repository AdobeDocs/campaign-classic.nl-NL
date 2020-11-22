---
solution: Campaign Classic
product: campaign
title: Verouderde en verwijderde functies van Campaign Classic
description: Deze pagina bevat de verouderde en verwijderde functies van Adobe Campaign Classic
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1621'
ht-degree: 99%

---


# Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert voortdurend de productmogelijkheden om oudere functies te identificeren die door modernere alternatieven zouden moeten worden vervangen om de algehele klantwaarde te verbeteren. Hierbij wordt altijd zorgvuldig rekening gehouden met achterwaartse compatibiliteit. Aangezien Adobe Campaign Classic met tools van derden werkt, wordt de compatibiliteit regelmatig bijgewerkt, zodat alleen ondersteunde versies kunnen worden geïmplementeerd. Versies die niet meer compatibel zijn met Adobe Campaign Classic, worden hieronder en in de [compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md) vermeld.

Voor het meedelen van de aanstaande verwijdering/vervanging van mogelijkheden van Campaign Classic gelden de volgende regels:

* De aankondiging van de afschaffing komt eerst. Hoewel verouderde mogelijkheden nog steeds beschikbaar en ondersteund kunnen worden voor bestaande gebruikers, worden deze niet verder uitgebreid en niet gedocumenteerd.
* Verouderde functies worden op zijn vroegst uit de volgende release verwijderd. De werkelijke doeldatum voor verwijdering wordt op deze pagina aangekondigd.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen mogelijkheid aan te passen vóór de daadwerkelijke verwijdering.

>[!NOTE]
>Adobe Campaign-releases en nieuwe mogelijkheden worden vermeld in de [release-opmerkingen](../../rn/using/latest-release.md).

## Verouderde functies {#deprecated-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd in de nieuwste Campaign Classic-releases.

In het algemeen worden functies die in een toekomstige versie moeten worden verwijderd, eerst ingesteld op afgeschaft. Deze functies en mogelijkheden zijn niet meer beschikbaar voor nieuwe Campaign Classic-klanten of mogen niet worden gebruikt voor nieuwe implementaties. Ze worden ook verwijderd uit de productdocumentatie.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie of mogelijkheid en plannen te maken om hun implementatie te wijzigen. Raadpleeg de doeldatum voor verwijdering om uw omgeving en projectupdates dienovereenkomstig te plannen.

<table> 
 <tbody> 
   <tr>
   <td><strong>Functie</strong></td>
   <td><strong>Vervanging</strong></td>
  </tr>
  <tr>
  <td>CRM-connectoren<br></td>
   <td><p>Vanaf Campaign versie 20.3 zijn de volgende CRM-connectoren afgeschaft:</p>
   <ul>
   <li>Soap-API - On-premise: 2007, 2015, 2016</li>
   <li>Soap-API - Online: 2015, 2016</li>
   <li>Web API - de Dynamica CRM van Microsoft op-gebouw: 2016, 2016 Update 1</li>
   <li>Web API - Microsoft Dynamics CRM Online: 2016, 2016 Update 1</li>
   </ul>
  <p><em>Doeldatum voor verwijdering: 2021</em></p>
  </td>
 </tr>
  <tr>
  <td>Verouderd binair iOS<br></td>
  <td><p>Vanaf Campaign versie 20.3 is de verouderde binaire iOS-connector van iOS afgeschaft.<p>
  <p> Als u deze connector gebruikt, moet u uw implementatie dienovereenkomstig aanpassen.
  <a href="https://helpx.adobe.com/campaign/kb/migrate-to-apns-http2.html">Meer informatie</a></p>
  <p><em>Doeldatum voor verwijdering: 2021</em></p>
  </td>
 </tr>
   <tr>
  <td>Demdex-domein<br></td>
  <td><p> Vanaf Campaign versie 20.3 is het demdex-domein afgeschaft. Dit werd gebruikt voor het importeren en exporteren van doelgroepen naar Adobe Experience Cloud.<p>
  <p>Als u het demdex-domein voor uw externe import/export-accounts gebruikt, moet u uw implementatie dienovereenkomstig aanpassen. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Meer informatie</a></p> 
  <p><em>Doeldatum voor verwijdering: 2021</em></p>
  </td>
  <tr>
  <td>OAuth-verificatie (OAuth en JWT)<br></td>
  <td><p> Vanaf Campaign versie 20.3 is de Triggers-integratieverificatie die oorspronkelijk was gebaseerd op de oAUTH-verificatieset-up voor toegang tot de pipeline gewijzigd en verplaatst naar Adobe I/O. <p>
  <p>Als u Triggers-integratie gebruikt, moet u uw implementatie dienovereenkomstig aanpassen. <a href="../../integrations/using/configuring-adobe-io.md">Meer informatie</a></p> 
  <p>Raadpleeg deze <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">pagina</a> voor meer informatie over de afschaffing van OAuth-verificatie.</p> 
  <p><em>Doeldatum voor verwijdering: april 2021</em></p>
  </td>
  </tr>
  <td>Sms-connectoren<br></td>
  <td><p> Vanaf Campaign-release 20.2 worden de volgende sms-connectoren afgeschaft.<p>
   <ul>
   <li>NetSize</li>
   <li>Generic SMPP (SMPP versie 3.4 die de binaire modus ondersteunt)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>CLX Communications</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>Als u één van deze connectoren gebruikt, moet u uw implementatie dienovereenkomstig aanpassen. <a href="../../delivery/using/sms-channel.md">Meer informatie</a></p> 
  <p>Ontdek in <a href="https://helpx.adobe.com/nl/campaign/kb/sms-connector.html">deze technische opmerking</a> hoe u verouderde connectoren kunt migreren.</p>
  <p><em>Doeldatum voor verwijdering: 2021</em></p>
  </td> 
 </tr>
  <tr>  
   <td>Faxkanaal<br></td>
   <td><p>Vanaf Campaign 20.2-release is het faxkanaal afgeschaft.</p> 
   <p>Als u dit kanaal gebruikt, moet u uw implementatie dienovereenkomstig aanpassen. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Ontdek meer</a> over Campaign-kanalen.</p>
   <p><em>Doeldatum voor verwijdering: 2021</em></p></td>
  </tr>
 </tbody> 
</table>

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die uit Campaign Classic zijn verwijderd.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Gebied - functie</strong></td>
   <td><strong>Vervanging</strong></td> 
  </tr> 
   <tr> 
   <td>Windows NT-verificatie<br></td>
   <td><p>Vanaf Campaign versie 20.3 is de Windows NT-verificatie verwijderd uit de beschikbare verificatiemethodes bij het configureren van een nieuwe database met een Microsoft SQL Server. <a href="../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine">Meer informatie</a></p></td>
  </tr>
   <tr> 
   <td>Archivering van e-mails op basis van bestanden<br></td>
   <td><p>Vanaf de release van Campaign 20.2 is archivering van e-mails op basis van bestanden niet meer beschikbaar. E-mailarchivering is nu beschikbaar via een specifiek BCC-e-mailadres. <a href="../../installation/using/email-archiving.md">Meer informatie</a></p></td>
  </tr> 
   <tr> 
   <td>Beheer van leads</td>
   <td><p>Vanaf de release van Campaign 20.2 is het pakket voor het beheer van leads niet meer beschikbaar. Vergelijkbare functionaliteit kan worden geïmplementeerd via andere native workflowactiviteiten en wijzigingen in datamodellen.</p></td>
   </tr>
   <tr>
   <td>Documentatie van Campaign-API’s - jsapi.chm-bestand</td>
   <td>Vanaf de release van Campaign 19.1 zijn Campaign Classic-API’s beschikbaar op een specifieke pagina. Als u het verouderde bestand jsapi.chm gebruikte, moet u nu naar <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">de nieuwe onlineversie</a> verwijzen.</td>
  </tr> 
  <tr> 
   <td>Campaign-orkestrering - predictive marketing</td>
   <td>Vanaf de release van Campaign 18.10 zijn de mogelijkheden voor predictive marketing niet meer beschikbaar.</td>
  </tr> 
  <tr> 
   <td>Webapplicaties - microsites</td>
   <td>Vanaf de release van Campaign 18.10 zijn microsites niet meer beschikbaar. U kunt de veiligheid verbeteren door de toegang tot alleen specifieke domeinen op Adobe Campaign-configuratiebestanden te beperken, en gepersonaliseerde URL’s in Campaign te gebruiken door DNS-aliassen te gebruiken. <a href="https://helpx.adobe.com/nl/campaign/kb/domain-name-delegation.html">Meer informatie</a></td>
  </tr> 
  <tr> 
   <td>Pushmeldingen - iOS Binary Connector</td>
   <td>Conform de aanbeveling van Apple heeft Adobe de verouderde iOS Binary Connector verwijderd vanaf de release van Campaign 18.10. De meer compatibele en efficiëntere HTTP/2-gebaseerde connector is al beschikbaar.</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>Vanaf de release van Campaign 18.6 is de <em>decryptString</em> API om veiligheidsredenen standaard niet meer beschikbaar voor nieuwe installaties.</p> 
   <p>Na een upgrade naar 18.6 (en hoger) wordt deze API niet meer geactiveerd en is deze vervangen door de functie <em>decryptPassword</em>. <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Meer informatie</a></p></td>
  </tr> 
   <tr> 
   <td>Mobiel kanaal - MMS- en WAP-pushberichten</td>
   <td>Vanaf de release van Campaign 18.4 zijn MMS- en WAP-pushkanalen niet meer beschikbaar. Als vervanging kunt u <a href="../../delivery/using/sms-channel.md">sms</a>- en <a href="../../delivery/using/about-mobile-app-channel.md">push</a>leveringen gebruiken.</td>
  </tr> 
   <tr> 
   <td>Mobiel kanaal - LINE v1</td>
   <td>Vanaf de release van Campaign 18.4 is het pakket LINE Connect niet meer beschikbaar. Adobe raadt u aan het nieuwe LINE-kanaalpakket te gebruiken als vervanging. <a href="../../delivery/using/line-channel.md">Meer informatie</a></td>
  </tr> 
 </tbody> 
</table>

## Verouderde compatibiliteit {#deprecated-compatibility}

De volgende systemen zijn afgeschaft voor Campaign Classic. Raadpleeg de [compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md) om een upgrade naar een nieuwere versie uit te voeren of naar een nieuw systeem over te schakelen voordat de compatibiliteit wordt beëindigd.

### Adobe Campaign 20.2-release {#compat-20-2-release}

Vanaf release 20.2 zijn oude sms-connectoren afgeschaft. Zie de sectie [Verouderde functies](#deprecated-features)

## Einde van compatibiliteit {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic is compatibel met alle systemen en tools die in de [compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md) worden vermeld. Wanneer specifieke versies van deze systemen en tools van derden het einde van de levensduur bereiken voor hun respectieve makers, is Adobe Campaign niet meer compatibel met deze versies: ze worden aangekondigd als afgeschaft en worden dan uit onze compatibiliteitsmatrix verwijderd in de volgende productrelease. Zorg ervoor dat u ondersteunde versies van alle systemen in de compatibiliteitsmatrix gebruikt om problemen te voorkomen.

### Clientconsole {#client-console-eol}

De Adobe Campaign Classic-clientconsole kan niet meer worden uitgevoerd op de volgende systemen, omdat deze zijn vervangen door hun editor. Klanten die de Campaign-clientconsole op een van deze versies uitvoeren, moeten naar de recentste versie upgraden vóór de doeldatum voor verwijdering. Raadpleeg de [compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008, 2008 R2
* Windows 7, XP, Vista

>[!NOTE]
>Vanaf de release van Campaign 20.1 is de 32-bits Campaign Classic-clientconsole niet meer compatibel met de nieuwste versies van Campaign. U moet de 64-bits clientconsole gebruiken.


### Besturingssystemen {#o-s-eol}

Vanaf release 19.1 is Adobe Campaign niet meer compatibel met de volgende besturingssystemen.

* CentOS 6 [Meer informatie](https://wiki.centos.org/Download)
* Debian 7. [Meer informatie](https://wiki.debian.org/DebianReleases)
* RHEL 6.x. [Meer informatie](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [Meer informatie](https://support.microsoft.com/nl-nl/lifecycle/search/1163)
* SLES 11. [Meer informatie](https://www.suse.com/lifecycle)

### Webservers {#web-server-eol}

Vanaf de lenterelease 19.1 is Adobe Campaign niet meer compatibel met de volgende webserver.

* Apache 2.2. [Meer informatie](https://httpd.apache.org/)
* Microsoft IIS 7. [Meer informatie](https://support.microsoft.com/nl-nl/lifecycle/search/810)

### Tools {#tools-eol}

Vanaf de lenterelease 19.1 is Adobe Campaign niet meer compatibel met de volgende tools.

* Java JDK 7. [Meer informatie](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5/4.3/5.x, behalve wanneer dit is ingesloten in een andere tool. [Meer informatie](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Database-engines {#dbe-eol}

Adobe biedt geen ondersteuning voor de volgende database-engines, omdat deze zijn afgeschaft door de editor. Klanten die met deze versies werken, moeten een upgrade uitvoeren naar de nieuwste versie of naar een andere versie overschakelen.

Raadpleeg de [Campaign-compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md) voor toegang tot de lijst met compatibele versies.

**FEDERATED DATA ACCESS (FDA)**

Vanaf release 20.2 is Adobe Campaign niet meer compatibel met de volgende FDA-server:

* DB2 UDB 10.5

Vanaf de lenterelease 19.1 is Adobe Campaign niet meer compatibel met de volgende FDA-servers:

* PostgreSQL 9.3. [Meer informatie](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [Meer informatie](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [Meer informatie](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 - 14.1. [Meer informatie](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic is niet compatibel met de volgende servers in FDA (Federated Data Access).

* DB2 UDB 9.5, 9.7. Een recentere versie van DB2 wordt ondersteund via FDA (Federated Data Access). [Meer informatie](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i, 10G R2. Recentere versies van Oracle worden ondersteund via FDA (Federated Data Access). [Meer informatie](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Recentere versies van PostgreSQL worden ondersteund via FDA (Federated Data Access). [Meer informatie](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005, 2008 R2. Recentere versies van SQL Server worden ondersteund via FDA (Federated Data Access). [Meer informatie](https://support.microsoft.com/nl-nl/lifecycle/search/1044)
* MySQL 5.1. Recentere versies van MySQL worden ondersteund via FDA (Federated Data Access). [Meer informatie](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB heeft het einde van de levensduur bereikt. [Meer informatie](https://www.mysql.com/support)
* Teradata 13, 13.1. Recentere versies van Teradata worden ondersteund via FDA (Federated Data Access). [Meer informatie](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0. Netezza heeft het einde van de levensduur bereikt. [Meer informatie](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData heeft het einde van de levensduur bereikt. [Meer informatie](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4, 15.5 en Sybase ASE 15.0. Recentere versies van Sybase worden ondersteund via FDA (Federated Data Access). [Meer informatie](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic biedt nog steeds ondersteuning voor de vermelde versies van Hadoop via HiveSQL via FDA (Federated Data Access), maar deze versies zijn samengevoegd met: HortonWorks (HDP 2.4.x, 2.5.x, 2.6.x) en HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS SERVER**

Adobe Campaign is niet compatibel met de volgende RDBMS-servers:
* Oracle 10GR2
* PostgreSQL 9.0 tot 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
