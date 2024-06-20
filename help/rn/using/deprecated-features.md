---
product: campaign
title: Verouderde en verwijderde functies van Campaign Classic
description: Deze pagina bevat de verouderde en verwijderde functies van Adobe Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '1637'
ht-degree: 93%

---

# Afgeschafte en verwijderde functies {#deprecated-and-removed-features}



Adobe evalueert voortdurend de productmogelijkheden om oudere functies te identificeren die door modernere alternatieven zouden moeten worden vervangen om de algehele klantwaarde te verbeteren. Hierbij wordt altijd zorgvuldig rekening gehouden met achterwaartse compatibiliteit. Aangezien Adobe Campaign Classic met tools van derden werkt, wordt de compatibiliteit regelmatig bijgewerkt, zodat alleen ondersteunde versies kunnen worden geïmplementeerd. Versies die niet meer compatibel zijn met Adobe Campaign Classic, worden hieronder en in de [compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md) vermeld.

Voor het meedelen van de aanstaande verwijdering/vervanging van mogelijkheden van Campaign Classic gelden de volgende regels:

* De aankondiging van de afschaffing komt eerst. Hoewel verouderde mogelijkheden nog steeds beschikbaar en ondersteund kunnen worden voor bestaande gebruikers, worden deze niet verder uitgebreid en niet gedocumenteerd.
* Verouderde functies worden op zijn vroegst uit de volgende release verwijderd. De werkelijke doeldatum voor verwijdering wordt op deze pagina aangekondigd.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen mogelijkheid aan te passen vóór de daadwerkelijke verwijdering.

>[!NOTE]
>Adobe Campaign-releases en nieuwe mogelijkheden worden vermeld in de [Aanvullende informatie](../../rn/using/latest-release.md).

## Afgeschafte functies {#deprecated-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd in de nieuwste Campaign Classic-releases.

In het algemeen worden functies die in een toekomstige versie moeten worden verwijderd, eerst ingesteld op afgeschaft. Deze functies en mogelijkheden zijn niet meer beschikbaar voor nieuwe Campaign Classic-klanten of mogen niet worden gebruikt voor nieuwe implementaties. Ze worden ook verwijderd uit de productdocumentatie.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie of mogelijkheid en plannen te maken om hun implementatie te wijzigen. Raadpleeg de doeldatum voor verwijdering om uw omgeving en projectupdates dienovereenkomstig te plannen.

<table> 
 <tbody> 
   <tr>
   <td><strong>Functie</strong></td>
   <td><strong>Details</strong></td>
  </tr>
  <tr>
 <td>Campagne (Neolane) verouderde SDK</td>
 <td><p>De Campagne (Neolane) SDK voor mobiele toepassingen is nu afgekeurd. Gebruik in plaats daarvan de Adobe Experience Platform Mobile SDK door de Adobe Campaign-extensie te configureren in de gebruikersinterface voor gegevensverzameling. De Adobe Experience Platform Mobile SDK helpt de oplossingen en services van de Adobe voor Experiencen Cloud in uw mobiele apps te ondersteunen. De configuratie SDKs wordt beheerd door de Inzameling UI van Gegevens voor flexibele configuratie en verlengbare, op regels-gebaseerde integratie. Leer hoe u het kanaal voor de mobiele app configureert in <a href="https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/push/push-settings">Campagne v8-documentatie</a>.</p>
<p>Verwachte verwijdering: eind 2024 </p>
</td>
</tr>
<tr>
 <td>Social marketing met Facebook</td>
 <td><p>Social marketing met Facebook is nu afgeschaft. U kunt integratie met X (voorheen Twitter) gebruiken om berichten te plaatsen op sociale media. U kunt ook met Adobe werken om een aangepast kanaal te maken.</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
<tr>
 <td>ACS Connector</td>
 <td><p>ACS Connector (primeaanbieding) is nu afgeschaft. U kunt de export-/importcapaciteiten van Campaign gebruiken voor het extraheren en injecteren van gegevens in beide producten.</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
 </tbody> 
</table>

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die uit Campaign Classic zijn verwijderd.

<table> 
 <tbody>
  <tr> 
   <td><strong>Functie</strong></td>
   <td><strong>Details</strong></td>
  <tr>  
      <tr>
  <td>Adobe Analytics Data Connector<br></td>
   <td><p>De Adobe Analytics Data Connector is verwijderd op 17 augustus 2022. Deze is vervangen door de release van Campaign 21.1.3.</p>
   <p>Als u deze connector gebruikt, moet u uw implementatie dienovereenkomstig aanpassen. <a href="../../integrations/using/gs-aa.md">Meer informatie</a></p>
  </td>
 </tr>
    <tr>
  <td>Rapport Technical Deliverability Monitoring<br></td>
   <td><p>Het rapport Technical Deliverability Monitoring is niet meer beschikbaar. Deze is vervangen door de release van Campaign 21.1.3.</p>
   <!--p>If needed, you can receive this report daily by email until the feature removal date. To request it, open a specific <a href="https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">Support Case</a> and specify the name of the instance and the email address(es) to send the report to.</p--> 
  </td>
 </tr>
  <tr>
  <td>OAuth-verificatie (OAuth en JWT)<br></td>
  <td><p> De de integratieauthentificatie van trekkers oorspronkelijk gebaseerd op OAuth authentificatieconfiguratie aan toegangspijpleiding is nu veranderd en verplaatst naar Adobe I/O. Deze authentificatiemodus was verouderd met de versie van Campagne 20.3.<p>
  <p>Als u Triggers-integratie hebt gebruikt, leest u <a href="../../integrations/using/about-triggers.md#implement">op deze pagina</a> hoe u uw implementatie kunt aanpassen.</p> 
  <p>Raadpleeg deze <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">pagina</a> voor meer informatie over de afschaffing van OAuth-verificatie.</p> 
  <!--p><em>Target removal date: October 20, 2021. Hosted environments benefit from an extension until May 25, 2022. </em></p-->
  </td>
  </tr>
   <td>Rapportage<br></td>
   <td><p>Na Adobe Flash Player EOL zijn het Gauge-rapport en de Chart-rendering-engine niet meer beschikbaar. <a href="../../reporting/using/creating-a-new-report.md">Meer informatie</a></p>
  </tr>
  <tr>  
   <td>Faxkanaal<br></td>
   <td><p>Vanaf Campaign 21.1.3 is het faxkanaal niet meer beschikbaar. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Meer informatie</a></p>
  </tr>
  <tr>
  <td>Demdex-domein<br></td>
  <td><p> Vanaf Campaign 21.1.3 is het demdex-domein afgeschaft. Dit werd gebruikt voor het importeren en exporteren van doelgroepen naar Adobe Experience Cloud. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Meer informatie</a></p> 
  </td>
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
   <td>Vanaf de release van Campaign 19.1 zijn Campaign Classic-API’s beschikbaar op een specifieke pagina. Als u het verouderde bestand jsapi.chm gebruikte, moet u nu naar <a href="https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=nl">de nieuwe onlineversie</a> verwijzen.</td>
  </tr> 
  <tr> 
   <td>Campaign-orkestrering - predictive marketing</td>
   <td>Vanaf de release van Campaign 18.10 zijn de mogelijkheden voor predictive marketing niet meer beschikbaar.</td>
  </tr> 
  <tr> 
   <td>Webapplicaties - microsites</td>
   <td>Vanaf de release van Campaign 18.10 zijn microsites niet meer beschikbaar. U kunt de veiligheid verbeteren door de toegang tot alleen specifieke domeinen op Adobe Campaign-configuratiebestanden te beperken, en gepersonaliseerde URL’s in Campaign te gebruiken door DNS-aliassen te gebruiken.</td>
  </tr> 
  <tr> 
   <td>Pushmeldingen - iOS Binary Connector</td>
   <td>Conform de aanbeveling van Apple heeft Adobe de verouderde iOS Binary Connector verwijderd vanaf de release van Campaign 18.10. De meer compatibele en efficiëntere HTTP/2-gebaseerde connector is al beschikbaar.</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>Vanaf de release van Campaign 18.6 is de <em>decryptString</em> API om veiligheidsredenen standaard niet meer beschikbaar voor nieuwe installaties.</p> 
   <p>Na een upgrade naar 18.6 (en hoger) wordt deze API niet meer geactiveerd en is deze vervangen door de functie <em>decryptPassword</em>. <a href="https://experienceleague.adobe.com/developer/campaign-api/api/f-decryptPassword.html?hl=decrypt">Meer informatie</a></p></td>
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

<!--## Deprecated compatibility {#deprecated-compatibility}

The following systems are deprecated for Campaign Classic. Please refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md) to upgrade to a newer version or move to a new system before the compatibility ends.-->

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


* Vanaf release 22.1 is Adobe Campaign niet meer compatibel met CentOs 8.x (64-bits). CentOS Linux 8 heeft op 31 december 2021 het einde van de levensduur (EOL) bereikt. [Meer informatie](https://www.centos.org/centos-linux-eol/).

  Als u dit besturingssysteem hebt gebruikt, past u de implementatie dienovereenkomstig aan. CentOS 7.x (64-bits) en RHEL 8.x/7.x (64-bits) worden nog ondersteund.

* Vanaf release 21.1.3 is Adobe Campaign niet meer compatibel met Debian 8.

* Vanaf release 19.1 is Adobe Campaign niet meer compatibel met de volgende besturingssystemen.

   * CentOS 6. [Meer informatie](https://wiki.centos.org/Download)
   * Debian 7. [Meer informatie](https://wiki.debian.org/DebianReleases)
   * RHEL 6.x. [Meer informatie](https://access.redhat.com/support/policy/updates/errata)
   * Windows Server 2008. [Meer informatie](https://support.microsoft.com/nl-nl/lifecycle/search/1163)
   * SLES 11. [Meer informatie](https://www.suse.com/lifecycle)

### Webservers {#web-server-eol}

Vanaf lenterelease 19.1 is Adobe Campaign niet meer compatibel met de volgende webserver.

* Apache 2.2. [Meer informatie](https://httpd.apache.org/)
* Microsoft IIS 7. [Meer informatie](https://support.microsoft.com/nl-nl/lifecycle/search/810)

### Tools {#tools-eol}

Vanaf de lenterelease 19.1 is Adobe Campaign niet meer compatibel met de volgende tools.

* Java JDK 7. [Meer informatie](https://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5/4.3/5.x, behalve wanneer het is ingesloten in een andere tool. [Meer informatie](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Database-engines {#dbe-eol}

Adobe biedt geen ondersteuning voor de volgende database-engines, omdat deze zijn afgeschaft door de editor. Klanten die met deze versies werken, moeten een upgrade uitvoeren naar de nieuwste versie of naar een andere versie overschakelen.

Raadpleeg de [Campaign-compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md) voor toegang tot de lijst met compatibele versies.

**FEDERATED DATA ACCESS (FDA)**

Vanaf release 20.2 is Adobe Campaign niet meer compatibel met de volgende FDA-server:

* DB2 UDB 10.5

Vanaf de lenterelease 19.1 is Adobe Campaign niet meer compatibel met de volgende FDA-servers:

* PostgreSQL 9.3.
* MySQL 5.5.
* DB2 9.5.
* Teradata 14 - 14.1.

Campaign Classic is niet compatibel met de volgende servers in FDA (Federated Data Access). Gebruik recentere versies of systemen.

* DB2 UDB 9.5, 9.7.
* Oracle 9i, 10G R2.
* PostgreSQL-versies tot 9.6 hebben het einde van hun gebruiksduur bereikt.
* MSSQL 2000, 2005, 2008 R2.
* MySQL 5.1.
* InfiniDB heeft het einde van de gebruiksduur bereikt.
* Teradata 13, 13.1.
* Netezza 6.02, 7.0. Netezza heeft het einde van de gebruiksduur bereikt.
* AsterData 5.0. AsterData heeft het einde van de gebruiksduur bereikt.
* Sybase IQ 15.2, 15.4, 15.5 en Sybase ASE 15.0.
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic biedt nog steeds ondersteuning voor de vermelde versies van Hadoop via HiveSQL via Federated Data Access (FDA), maar deze versies zijn samengevoegd met: HortonWorks (HDP 2.4.x, 2.5.x, 2.6.x) en HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS SERVER**

Vanaf de lenterelease 19.1 is Adobe Campaign niet meer compatibel met de volgende FDA-servers:

* Oracle 10GR2
* PostgreSQL 9.0 tot 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

PostgreSQL-versies tot 9.6 hebben het einde van de levensduur bereikt. Ze worden daarom niet ondersteund door Adobe Campaign.

### Sms-connectoren {#sms-eol}

Vanaf release 20.2 zijn oude sms-connectoren afgeschaft. Adobe Campaign is niet compatibel met:

* Generic SMPP (SMPP versie 3.4 die de binaire modus ondersteunt)
* Sybase365 (SAP SMS 365)
* CLX Communications
* Tele2
* O2
* iOS

### CRM-connectoren {#crm-connectors}

Met ingang van release 21.1 van Campaign zijn de volgende CRM-connectoren niet langer compatibel met Campaign:

* Soap-API - On-premise: 2007, 2015, 2016
* Soap-API - Online: 2015, 2016
* Web-API – Microsoft Dynamics CRM 2016
* Web-API – Microsoft Dynamics CRM 2016 Update 1
* Oracle on demand-API
