---
title: Laatste release
description: Laatste release
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 251244225076dd11a319d1c4b2124c0d05168eaa
workflow-type: tm+mt
source-wordcount: '1976'
ht-degree: 3%

---


# Laatste release{#latest-release}

![](assets/do-not-localize/cp-icon.png) **Nieuwe release** van het Configuratiescherm in juni met controle van actieve profielen, controle van de leverbaarheid van subdomeinen en beheer van GPG-sleutels. [Meer informatie](https://docs.adobe.com/content/help/nl-NL/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/blue_2.png) Release 20.2.2 - build 9180 {#release-20-2-2-build-9180}

_22 juli 2020_

* Probleem verholpen waarbij tracering niet werkte toen de handtekeningfunctie was uitgeschakeld. (NEO-26411)
* Probleem verholpen waarbij niet-ondertekende koppelingen van gepersonaliseerde domeinen werden geblokkeerd op het moment dat ze moesten worden toegestaan. (NEO-25210)
* Probleem verholpen waardoor u URL&#39;s voor bijhouden niet kunt openen of erop kunt klikken wanneer u bepaalde oudere versies van Outlook gebruikt. (NEO-25688)
* Probleem verholpen waarbij URL&#39;s van pagina&#39;s die onjuist zijn gedefinieerd in e-mailleveringen werden gespiegeld. (NEO-26084)
* Probleem met coderen van URL-beheer in de service voor anti-phishing is opgelost. (NEO-25283)
* Probleem verholpen waarbij het bijhouden van URL&#39;s met fragmenten in personalisatieparameters (ankerlabels met hekje) niet werkte. (NEO-25774)
* Probleem met bijhouden opgelost bij het gebruik van specifieke aangepaste volgformules. (NEO-25277) Probleem opgelost waarbij het bijhouden van &quot;meldingskliks&quot; niet werkte (iOS- en Android-pushmeldingen). (NEO-25965)
* Oplossing voor een regressie die invloed had op berekende velden in een werkstroom. (NEO-25194)
* Oplossing voor een regressie die ervoor zorgde dat het direct maken van URL&#39;s voor webtracering niet werkte. (NEO-20999)
* Probleem verholpen met leveringsrapporten buiten de doos die werden afgekapt tijdens het exporteren naar PDF. (NEO-25757)
* Probleem verholpen waarbij de toepassing vastliep in de wizard voor implementatie.
* Probleem verholpen waardoor de workflow voor het melden van voorstellen na een postupgrade niet correct kon werken.
* De iOS HTTP2-connector is verbeterd (updates van derden en foutbeheer). (NEO-25904, NEO-25903)
* De lijst jarsToSkip in catalina.properties is bijgewerkt om de verwijzing naar een jar-bestand te verwijderen dat niet meer werd gebruikt (iOS-meldingen).
* Probleem verholpen waarbij de voorbereiding van de levering na de upgrade werd geblokkeerd.
* Na de schakelaar aan het [nieuwe mechanisme](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)van opeenvolging ID, worden alle Webtoepassingen die de ontvankelijke lijst bijwerken opnieuw gepubliceerd tijdens postupgrade.
* Oplossing voor een mogelijke XSS-kwetsbaarheid in de leveringsinhoud. (NEO-17987, NEO-26073)

## ![](assets/do-not-localize/orange_2.png) Release 20.2.1 - build 9178 {#release-20-2-1-build-9178}

_8 juni 2020_

**Nieuwe functies**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Ondersteuning voor Emoticons</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Wanneer het ontwerpen van een bericht in Campaign, kunt u emoticons in het berichtlichaam nu gemakkelijk opnemen, gebruikend een specifieke knoop. Ze kunnen ook worden toegevoegd aan de onderwerpregel van de e-mail. U kunt de lijst met beschikbare emoticons in de interface aanpassen.</p>
    <p>Raadpleeg de <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">gedetailleerde documentatie</a>voor meer informatie over het toevoegen van emoticons. Leer hoe u de emoticonlijst <a href="../../delivery/using/customizing-emoticon-list.md">in deze sectie</a>aanpast.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>U kunt uw instantie van de Campagne nu met uw externe gegevensbestand van Azure Synapse verbinden. Deze verbinding wordt beheerd via een nieuwe externe account.</p>
    <p>Azure Synapse is alleen beschikbaar voor hybride en on-premise omgevingen. Raadpleeg de <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">gedetailleerde documentatie</a> voor meer informatie.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Thailand- en Braziliaanse privacywetten</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>De Thaise wet inzake de bescherming van persoonsgegevens (PDPA) is de nieuwe privacywet die de vereisten inzake gegevensbescherming voor Thailand harmoniseert en moderniseert. </p>
   <p>Lei Geral de Proteção de Dados (LGPD) is vanaf 16 augustus van kracht voor alle bedrijven die in Brazilië persoonsgegevens verzamelen of verwerken.</p>
   <p>Deze voorschriften zijn van toepassing op Adobe Campaign-klanten die gegevens bewaren voor in deze landen wonende gegevenssubjecten. Naast de privacy mogelijkheden reeds beschikbaar in Campagne (met inbegrip van toestemmingsbeheer, montages van het gegevensbehoud, en gebruikersrollen), nemen wij deze kans aan om extra mogelijkheden te omvatten, helpen uw bereidheid voor PDPA en LGPD vergemakkelijken:</p>
   <ul> 
     <li><p>Recht op toegang en recht op verwijdering: we maken gebruik van de functies die voor de AVG (GDPR) en CCPA zijn toegevoegd. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">Meer informatie</a></p></li> 
     <li> <p>Wanneer u een privacyaanvraag maakt met de Campagne-interface of API, selecteert u nu het <strong>Regeltype</strong> : PDPA, LGPD, GDPR, CCPA. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">Meer informatie</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

* Alle klanten hebben standaard een betere beveiliging bij het bijhouden van koppelingen in e-mail ingeschakeld. Er is een extra, verbeterde beveiligingsfunctie beschikbaar die kan worden ingeschakeld door de klantenservice te bereiken. Meer informatie over de functie en de stappen die niet-gehoste klanten moeten uitvoeren, vindt u in de checklist [voor](https://helpx.adobe.com/campaign/kb/acc-security.html)beveiliging en privacy. (NEO-24232)

* Om de beveiliging te optimaliseren, is het MD5-hash-algoritme waarmee bestandsnamen worden gegenereerd, versterkt met sha256 voor het uploaden van openbare bestanden. (NEO-17044)

* Om veiligheid tegen aanvallen te versterken XSS, worden de cliënt-zijmanuscripten onbruikbaar gemaakt wanneer het uitvoeren van een spiegelpagina. (NEO-17987)

* Probleem verholpen waarbij de technische workflow voor het opschonen van **privacyverzoeken** niet kon worden gebruikt om aanpassingsgegevens te verwijderen. (NEO-25168, NEO-21004)

* Probleem verholpen met de **bestandsoverdrachtactiviteit** waardoor verificatie op basis van SFTP-sleutels niet kon werken op Debian 9. (NEO-23183)

**Verbeteringen op gebied van compatibiliteit**

De volgende systemen worden nu ondersteund met Campagne:
* Besturingssystemen: Debian 10
* RDBMS: Oracle 18c en Oracle 19c
* FDA: Azure Synapse Analytics

Meer informatie over de matrix [Campagne Compatibility](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

**Verbeteringen**

* Transactioneel overseinen is verbeterd voor een betere gebruikerservaring. U kunt nu de publicatie van een transactiemalplaatje ongedaan maken, waardoor dit van de uitvoeringsinstanties wordt verwijderd. [Meer informatie](../../message-center/using/template-unpublication.md).

* Er zijn nieuwe opties beschikbaar om beperkingen in te stellen bij het verzenden van e-mailberichten die afbeeldingen of bijlagen bevatten. Deze gidsen kunnen prestatieskwesties vermijden, die met name met transactioneel overseinen nuttig zijn. [Meer informatie](../../installation/using/configuring-campaign-options.md#delivery)

* Met de nieuwe optie **De leveringsonderdelen in de database** voorbereiden kunt u de levering direct in de database voorbereiden. Hierdoor kan de analyse aanzienlijk worden versneld. Deze optie is alleen beschikbaar voor specifieke configuraties. [Meer informatie](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* De prestaties van de activiteit [van de Schakelaar van](../../workflow/using/crm-connector.md) CRM voor de Dynamica van Microsoft zijn verbeterd. (NEO-13303, NEO-12710)

* De versie van het gedeelde geheugen is verhoogd.

   >[!WARNING]
   >
   >Deze verbetering vereist een extra stap na het uitvoeren van de verbetering. Raadpleeg de onderstaande sectie **Technische ontwikkelingen** .

* De opschoonworkflow is verbeterd. De zwevende werktabellen van alle verwijderde workflows worden nu ook automatisch verwijderd door de opschoonworkflow. [Meer informatie](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Certificaten voor mobiele iOS-toepassingen met de iOS HTTP2-connector worden nu gevalideerd voordat pushmeldingen worden verzonden, zodat leveringen niet mislukken vanwege verlopen certificaten.

* Het beheer van HTTP-proxyverbindingen is verbeterd. [Meer informatie](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**Overige wijzigingen**

* Verouderde sms-connectors zijn nu afgekeurd. Raadpleeg de pagina met [Verouderde functies](../../rn/using/deprecated-features.md).

* U kunt uw eigen Litmus-account niet meer gebruiken voor provisioning en gebruik van Inbox-rendering in Adobe Campaign. [Meer informatie](../../delivery/using/inbox-rendering.md).

* Voor een beter onderscheid tussen weergaven en mappen is de kleur van weergavenamen gewijzigd van donkerblauw in donkercyaan. [Meer informatie](../../platform/using/access-management.md#about-views)

* Campaign Classic kan nu worden verbonden met Microsoft Dynamics CRM-accounts die in het Verenigd Koninkrijk, India en Canada worden gehost. Dit is op Bureau 365 en op gebouw (Dynamiek 2015) plaatsingstypes van toepassing.

* De campagne voert nu een controle van TLS uit om te controleren dat hostname van de server hostname in het verstrekte certificaat aanpast.

* De de statistieklijst van de Levering en het volgen toont nu één ingang per levering voor het kanaal van SMS, in plaats van één ingang per leveringsontvanger.

* Er is een foutbericht toegevoegd in het logbestand om gebruikers te waarschuwen wanneer het gedownloade bestand groter is dan de schijfruimte.

* De volgende functies zijn nu beschikbaar voor de Snowflake-aansluiting: Maandengeleden, DaysAgoInt, ToDateTime, JarenAgo.

**Technische ontwikkelingen**

Deze nieuwe build werkt gedeelde geheugen bij en vereist extra stappen om de upgrade uit te voeren. Als beheerder van de Campagne, moet u geheugensegmenten verwijderen. Deze stappen zijn verplicht, aangezien oude segmenten het starten van NLServer/nlsrvmod verhinderen.

In Windows moet het systeem opnieuw worden opgestart.

Op Debian/CentOs, is de gedeelde geheugenschrapping nodig. Hier volgen de volgende stappen:

Voor de upgrade moet u de volgende stappen uitvoeren:

1. Stop de service apache2 (http2 op CentOS) als deze actief is.
1. Stop de service nlserver (nlserver6 for older builds) als deze actief is.

Na de upgrade:

1. Verwijder het gedeelde geheugen met de **IPcrm** -opdracht als de versie ouder is dan de huidige versie.
1. Start de NLSereservice als deze actief was.
1. Start de service apache2 als deze actief was.

Hier zijn de bevellijnen voor Debian:

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Een voorbeeld voor Linux is beschikbaar op deze [pagina](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**Patches**

* Oplossing voor een kleine regressie in de logboeken van de opschoonworkflow.
* Probleem verholpen met de activiteit **Laden (SOAP)** tijdens het parseren van WSDL-bestanden in de workflow.
* Probleem verholpen dat een fout veroorzaakte bij het upgraden van een groot aantal workflows met behulp van een **enquêteactiviteit** om een groot aantal workflows efficiënt te verwerken.
* Oplossing voor een probleem met intermitterende connectiviteit tijdens de verwerking van InMail-berichten van de verbeterde MTA. (NEO-20380)
* Probleem verholpen waarbij de percentages voor warm klikken niet correct werden weergegeven wanneer afbeeldingen met een breedte van 100% werden weergegeven in de HTML. (NEO-23203)
* Probleem verholpen waardoor de voorwaardelijke inhoud van de levering niet volledig kon worden weergegeven in het rapport met hot click. (NEO-18729)
* Probleem verholpen waarbij de stap voor doelgoedkeuring werd overgeslagen wanneer een workflow werd hervat om een terugkerende levering te verzenden. (NEO-18166)
* Probleem verholpen waardoor de knop Bericht **opnieuw voorbereiden** niet kon worden hervat nadat een fout in de workflow was verholpen. (NEO-13488)
* Probleem verholpen waarbij leveringen in de midsourcingmodus tijdens de oplaadfase konden mislukken, waarbij ontvangers in de Japanse e-mailindeling werden opgenomen. (NEO-23846)
* Probleem met tijdzoneconversie verholpen met de Snowflake-connector (NEO-20105)
* Probleem met externe accounts met FTP via SSL opgelost. (NEO-20498)
* Probleem verholpen waarbij afbeeldingen niet konden worden weergegeven in Lijnleveringen. (NEO-23207)
* Probleem verholpen dat een fout veroorzaakte bij het publiceren van een aanbieding. (NEO-23312)
* Probleem verholpen met pushberichten die het mogelijk maakten testverbindingen te gebruiken in mobiele toepassingen, zelfs als het certificaat verlopen was. (NEO-22991)
* Probleem verholpen dat invloed zou kunnen hebben op pushberichten wanneer deze op een hoge frequentie worden verzonden. (NEO-20516)
* Probleem verholpen waarbij bij de volgende gegevens duplicaten werden opgenomen, ook al zijn de trackinglogboeken niet bijgehouden. (NEO-20040)
* Probleem verholpen waarbij dubbele transactie-e-mails werden verzonden nadat een fout met de communicatie van de trackingserver was verholpen. (NEO-23640)
* Probleem verholpen waarbij de parameterwaarde voor codering tijdens het omleiden van een URL voor reeksspatiëring werd verwijderd. (NEO-25637)
* Probleem verholpen waarbij een query niet werkte bij het vergelijken van floatnummers. (NEO-23243)
* Probleem verholpen waarbij de weergave van de inhoud van de kolom **Gewijzigd door** kolominhoud kon worden verhinderd nadat een werkstroom opnieuw was gestart. (NEO-23035)
* Probleem opgelost waarbij het downloaden van logbestanden uit een tweede container tot mislukken van de technische workflow voor bijhouden leidde. (NEO-23159)
* Probleem verholpen waarbij workflows kunnen mislukken wanneer een **verrijkingsactiviteit** wordt uitgevoerd. (NEO-1738)
* Er is een controle toegevoegd aan de **dubbelepunten om het veld te behouden** in de activiteit van de **deduplicatieworkflow** om te voorkomen dat er ongeldige of negatieve waarden worden ingevoerd.
* De wizard **Planner is verwijderd** uit de terugkerende campagnes om te voorkomen dat uren en minuten worden vermeld. Alleen datums worden in aanmerking genomen.
* Probleem verholpen met extra opslagvelden tijdens het maken van leveringen via de optie **Berekend door een script** in de **scriptworkflowactiviteit** . (NEO-20609)
* Probleem verholpen waardoor spookworkflows niet konden worden verwijderd binnen de opschoningstaken voor de database.
* Probleem opgelost waarbij de technische workflow voor **facturering (actieve profielen)** mislukte. (NEO-1977)
* Probleem verholpen tijdens het testen van de verbinding van de externe account van acsDefaultAccount. (NEO-23433)
* Probleem verholpen waardoor u geen schema-extensie voor een primaire sleutel met meerdere kolommen met een Hadoop-tabel kon maken. (NEO-17390)
* Probleem verholpen in de activiteit **Laden (SOAP)** die ertoe kon leiden dat WSDL-bestanden niet vanaf een URL werden geladen. (NEO-16924)
* Probleem verholpen waardoor u geen **onvoorwaardelijke stop** kon uitvoeren door de console wanneer meerdere actieve workflowservers in evenwicht waren met de taakverdeling. (NEO-1956)
* Oplossing voor een regressie die ertoe leidde dat de opschoonworkflow vastliep.
* Probleem verholpen die kon optreden wanneer een sjabloon op een uitvoeringsinstantie werd gepubliceerd.
* Probleem verholpen waardoor de technische workflow van collectPrivacyRequests niet kon worden uitgevoerd. (NEO-20513, NEO-25169)
* Problemen verholpen die konden optreden wanneer werd geprobeerd verbinding te maken met Audience Manager na uploaden om 9080 te bouwen. (NEO-20511, NEO-25167)
* Problemen verholpen die konden optreden bij het exporteren van rapporten in PDF- of XLS-indeling. (NEO-20982, NEO-23493, NEO-23348)
* Probleem verholpen waarbij een levering twee keer in de leveringslijst kon worden weergegeven nadat deze was verzonden.
* Oplossing een kwestie met leveringsvoorbereiding die kon voorkomen toen de verpletterende configuratie werd geplaatst om de levering via midsourcing te verzenden.
* Probleem verholpen waarbij een foutbericht kon worden weergegeven wanneer op een koppeling voor een webtoepassing in een regelbericht werd geklikt.
* Probleem verholpen waarbij Microsoft Dynamics CRM niet alle entiteiten kon ophalen. (NEO-24528)
* Probleem verholpen waarbij de geschiedenis van de **incrementele query** -activiteit werd verwijderd na het uitvoeren van de opschoonworkflow.
* Probleem verholpen bij het maken van een externe account voor midsourcing waarbij de optie NmsMidSourcing_LastBroadLog_&lt;InternalName> ontbreekt. Dit probleem is nu opgelost.
