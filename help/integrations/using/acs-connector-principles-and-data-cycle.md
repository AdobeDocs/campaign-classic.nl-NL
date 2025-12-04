---
product: campaign
title: Aan de slag met ACS-connector
description: ACS-verbindingsbeginselen en gegevenscyclus
feature: ACS Connector
hide: true
hidefromtoc: true
exl-id: 689b6117-5143-4f85-8582-2c74cae72ca2
source-git-commit: 2186b8a30449cb023cb07305ba64d53f2c8adab1
workflow-type: tm+mt
source-wordcount: '2034'
ht-degree: 0%

---

# Aan de slag met ACS-connector{#acs-connector-gs}



ACS Connector bridges Adobe Campaign v7 en Adobe Campaign Standard. Het is een geïntegreerde functie in Campagne v7 die automatisch gegevens aan Campaign Standard repliceert, die het beste van beide toepassingen verenigt. Campagne v7 heeft geavanceerde hulpmiddelen om het primaire marketing gegevensbestand te beheren. Dankzij de gegevensreplicatie van Campaign v7 kan Campaign Standard de rijke gegevens benutten in een gebruiksvriendelijke omgeving.

![](assets/acs_connect_puzzle_link_01.png)

Met de Schakelaar ACS, blijft Campaign Standard door digitale marketers worden gebruikt om, campagnes te ontwerpen te richten en uit te voeren terwijl Campaign v7 voor gegeven-georiënteerde gebruikers zoals gegevensbestandmarketers wordt gemaakt.

>[!IMPORTANT]
>
>ACS Connector is alleen beschikbaar als onderdeel van het Adobe Campaign Prime-aanbod. Neem contact op met uw accountmanager voor meer informatie over het in licentie geven van Adobe Campaign Prime.
>
>ACS Connector is slechts beschikbaar voor ontvangen en hybride architecturen. Het is niet beschikbaar voor volledige installaties op locatie.
>
>Als u deze functie wilt gebruiken, moet u verbinding maken met een campagne met een Adobe ID (IMS). Zie [ Verbindend via Adobe ID ](../../integrations/using/about-adobe-id.md).

Dit document stelt de mogelijkheden ACS-Connector voor. In de volgende secties vindt u informatie over de manier waarop de functie gegevens en instructies over het werken met gerepliceerde profielen retourneert.

* [ Proces ](#process): Overzicht van de Schakelaar ACS en hoe de gegevensreplicatie wordt beheerd.
* [ Implementatie ](#implementation): Overzicht van hoe te om met Schakelaar ACS evenals instructies op te worden begonnen hoe te om basis en geavanceerde gegevens te herhalen.
* [ synchroniseer profielen ](../../integrations/using/synchronizing-profiles.md): Instructies op hoe te profielen te herhalen en hoe te om leveringen met hen tot stand te brengen.
* [ synchroniseer publiek ](../../integrations/using/synchronizing-audiences.md): Instructies op hoe te om een lijst van ontvangers in Campagne v7 te richten en dan de lijst aan Campaign Standard als publiek te herhalen.
* [ synchroniseer Webtoepassingen ](../../integrations/using/synchronizing-web-applications.md): Instructies op hoe te om het Webtoepassingen van de Campagne v7 aan Campaign Standard te verbinden.
* [ het Oplossen van problemen de Schakelaar ACS ](../../integrations/using/troubleshooting-the-acs-connector.md): De antwoorden van het overzicht aan gemeenschappelijke problemen.

>[!NOTE]
>
>De Schakelaar ACS is inbegrepen met Campaign v7 onder vergunningsovereenkomst. Om de Schakelaar ACS te gebruiken, zorg ervoor dat u tussen Campagne v7 en Campaign Standard kunt schakelen. Neem contact op met de beheerder als u niet zeker weet van uw versie en de opgenomen functies.

## Proces {#process}

### Gegevensreplicatie {#data-replication}

![](assets/acs_connect_flows_01.png)

De Schakelaar ACS herhaalt periodiek de volgende punten van Campagne v7 aan Campaign Standard:

* **Ontvangers**
* **Abonnementen**
* **de Diensten**
* **het Bestaan pagina&#39;s**

Door gebrek, is de periodieke replicatie voor Schakelaar ACS eens om de 15 minuten. De periode van de periodieke replicatie kan aan uw behoeften worden aangepast. Neem contact op met uw consultant als er wijzigingen nodig zijn.

Gegevensreplicatie voor ontvangers, abonnementen, services en bestemmingspagina&#39;s is incrementeel, wat betekent dat alleen nieuwe ontvangers en wijzigingen aan bestaande ontvangers worden gerepliceerd van Campagne v7 naar Campaign Standard. Nochtans, komt de replicatie voor een publiek in één enkele instantie voor. U kunt een publiek maken in Campaign v7 en dit vervolgens één keer repliceren naar Campaign Standard. De replicatie is direct en kan niet voor regelmatige updates worden gevormd. Voor instructies, zie [ Synchroniserend publiek ](../../integrations/using/synchronizing-audiences.md).

>[!NOTE]
>
>Wees geduldig met de eerste replicatie van een grote database, omdat dit enkele uren kan duren. De volgende replicaties worden echter steeds sneller uitgevoerd.

De Schakelaar ACS repliceert periodiek de volgende punten van Campaign Standard aan Campaign v7:

* **[!UICONTROL Delivery IDs]**
* **[!UICONTROL Email broad logs]**
* **[!UICONTROL Email tracking logs]**

Dankzij replicatie van bezorgings-id&#39;s en e-maillogboeken hebt u toegang tot de geschiedenis van leveringen en traceringsgegevens voor uw v7-ontvangers vanuit Campagne v7.

>[!IMPORTANT]
>
>Alleen e-mailuitzendingen en trackinglogboeken worden gerepliceerd van Campaign Standard naar Campaign v7.

### Gegevenssynchronisatie {#data-synchronization}

![](assets/acs_connect_flows_02.png)

De Schakelaar ACS synchroniseert quarantines tussen Campagne v7 en Campaign Standard.

Een profiel dat is gerepliceerd van Campagne v7 naar Campaign Standard, bevat bijvoorbeeld een e-mailadres. Als het e-mailadres door Campaign Standard in quarantaine wordt geplaatst, worden de gegevens overgegaan tot Campagne v7 tijdens de volgende synchronisatie. Voor meer informatie over quarantines, zie [ het beheer van de Quarantaine ](../../delivery/using/delivery-failures-quarantine.md) en [ Quarantines van Campaign Standard ](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html).

### Gepliceerde profielen gebruiken {#using-replicated-profiles}

De gekopieerde profielen kunnen door Campaign Standard en Campagne v7 voor doelgerichte werkschema&#39;s in marketing campagnes worden gebruikt.

Voor instructie op hoe te om een levering in Campaign Standard te verzenden gebruikend gerepliceerde profielen, zie [ Synchroniserend profielen ](../../integrations/using/synchronizing-profiles.md). Er zijn aanvullende instructies beschikbaar voor het delen van de gegevens voor abonnementen tussen Campagne v7 en Campaign Standard.

### Beperkingen {#limitations}

Gedetailleerde profielen zijn gemakkelijk beschikbaar voor leveringen, maar hebben bepaalde beperkingen in Campaign Standard. Bekijk de onderstaande objecten voor meer informatie over hoe u ze het beste kunt beheren.

* **read-only profielen voor Campaign Standard**: De gekopieerde profielen zijn read-only in Campaign Standard. Nochtans, kunt u ontvangers in Campagne v7 uitgeven en de wijzigingen worden automatisch bijgewerkt in Campaign Standard door Schakelaar ACS.
* **Profielen die in Campaign Standard** worden gecreeerd: De Schakelaar ACS herhaalt ontvankelijke gegevens in één richting, van Campagne v7 aan Campaign Standard. Daarom worden profielen die afkomstig zijn uit Campaign Standard niet gerepliceerd naar Campaign v7.
* **Basis ontvankelijke gegevens voor Campaign Standard**: De Schakelaar ACS herhaalt ontvankelijke gegevens die voor Campaign Standard geschikt zijn. Hieronder vallen namen, adressen, e-mailadressen, mobiele telefoonnummers, thuistelefoonnummers en andere relevante contactgegevens van ontvangers. Neem contact op met uw consultant als extra ontvangende velden en aangepaste doeltabellen in Campagne v7 van essentieel belang zijn voor uw workflow.
* **het Invoeren van quarantined profielen**: De lijsten van profielen die niet willen worden gecontacteerd kunnen in Campagne v7 of Campaign Standard als quarantined profielen worden ingevoerd. De status voor de profielen wordt opgenomen in de quarantainesynchronisatie tussen de toepassingen en wordt niet gebruikt in leveringen.
* **Unsubscribe aan de dienst in Campaign Standard**: De keus aan unsubscribe aan een levering wordt niet gesynchroniseerd van Campaign Standard aan Campagne v7. Nochtans, kunt u een levering van Campaign Standard vormen om zijn unsubscription verbinding aan Campaign v7 te richten. Het profiel voor een ontvanger die op de koppeling voor het opzeggen van abonnementen klikt, wordt bijgewerkt in Campagne v7 en de gegevens worden naar Campaign Standard gerepliceerd. Zie [ Verandering de unsubscription verbinding ](../../integrations/using/synchronizing-profiles.md#changing-the-unsubscription-link).
* Alleen e-mailuitzendingen en trackinglogboeken worden gerepliceerd van Campaign Standard naar Campaign v7.

### Facturering {#billing}

Het factureren wordt niet beïnvloed door uw keuze voor een toepassing voor het verzenden van leveringen, Campaign v7 of Campaign Standard. Factureringsgegevens worden afgestemd tussen Campagne v7 en Campaign Standard. Daarom als u leveringen naar de zelfde ontvanger verzendt gebruikend beide toepassingen, wordt het nog geteld als één actief profiel.

## Implementatie {#implementation}

Er bestaan twee soorten implementatie voor ACS-connector. Beide worden altijd uitgevoerd door het Adobe Campaign Consulting-team.

>[!IMPORTANT]
>
>Deze sectie is alleen bedoeld voor professionele gebruikers, zodat zij een algemeen overzicht krijgen van het implementatieproces en de belangrijkste stappen ervan.
>
>Probeer op geen enkele manier zelf een van deze implementaties uit te voeren. Het is uitsluitend voorbehouden aan de consultants van Adobe Campaign.

De **basisimplementatie** staat u toe om ontvangers (uit-van-de-doos gebieden), de diensten en abonnementen, Webtoepassingen en publiek te herhalen. Dit is een eenmalige replicatie van Campaign v7 naar Campaign Standard.

De **geavanceerde implementatie** zal u toestaan om complexere gebruiksgevallen uit te voeren, bijvoorbeeld als u extra ontvankelijke gebieden of douane ontvankelijke lijsten (transactietabel bijvoorbeeld) hebt. Zie [ Geavanceerde implementatie ](#advanced-implementation).

### Het pakket installeren {#installing-the-package}

Als u deze functie wilt gebruiken, moet het pakket **[!UICONTROL ACS Connector]** zijn geïnstalleerd. Dit wordt altijd uitgevoerd door de technische beheerder of consultant van Adobe.

Alle technische elementen met betrekking tot de Schakelaar ACS zijn beschikbaar in de **[!UICONTROL Administration > ACS Connector]** knoop van de ontdekkingsreiziger.

### Technische en replicatieworkflows {#technical-and-replication-workflows}

Na de installatie van het pakket zijn twee technische workflows beschikbaar onder **[!UICONTROL Administration > ACS Connector > Process]** .

>[!IMPORTANT]
>
>Probeer nooit deze workflows te wijzigen. Ze mogen nooit fout zijn of gepauzeerd zijn. Neem contact op met uw Adobe Campaign-consultant als dit gebeurt.

![](assets/acs_connect_implementation_3.png)

* **[!UICONTROL `[ACS] Quarantine synchronization`]** (quarantaineSync): deze workflow synchroniseert alle quarantainegegevens. Alle nieuwe quarantines in Campagne v7 worden herhaald in Campaign Standard. Alle nieuwe quarantines uit Campaign Standard worden gerepliceerd naar Campaign v7. Dit garandeert dat alle uitsluitingsregels worden gesynchroniseerd tussen Campagne v7 en Campaign Standard.
* **[!UICONTROL `[ACS] Security group synchronization`]** (securityGroupSync): deze workflow wordt gebruikt voor rechtenconversie. Zie [ de omzetting van Rechten ](#rights-conversion).

De volgende replicatiewerkschema&#39;s zijn beschikbaar als &quot;klaar om&quot;malplaatjes worden gebruikt. Ze moeten worden geïmplementeerd door uw Adobe Campaign-consultant.

![](assets/acs_connect_implementation_2.png)

* **[!UICONTROL `[ACS] Profile replication`]** (newProfileReplication): deze incrementele workflow dupliceert ontvangers naar Campaign Standard. Standaard worden alle ontvangende velden buiten het vak gerepliceerd. Zie [ Gebrek ontvankelijke gebieden ](#default-recipient-fields).
* **[!UICONTROL `[ACS] Service replication`]** (newServiceReplication): deze incrementele workflow repliceert de gekozen services naar Campaign Standard. Zie het gebruiksgeval [ synchroniserend Webtoepassingen ](../../integrations/using/synchronizing-web-applications.md).
* **[!UICONTROL `[ACS] Landing pages replication`]** (newLandingPageReplication): deze incrementele workflow repliceert de gekozen webtoepassingen naar Campaign Standard. De Campagne v7-webtoepassingen worden weergegeven als bestemmingspagina&#39;s in Campaign Standard. Zie het gebruiksgeval [ synchroniserend Webtoepassingen ](../../integrations/using/synchronizing-web-applications.md).
* **[!UICONTROL `[ACS] New replication`]** (newReplication): deze incrementele workflow is een voorbeeld dat kan worden gebruikt om een aangepaste tabel te repliceren. Zie [ Geavanceerde implementatie ](#advanced-implementation).
* **[!UICONTROL `[ACS] Delivery-message replication`]** (newDlvMsgQualification): deze incrementele workflow repliceert leveringsberichten van Campaign Standard naar Campagne v7.
* **[!UICONTROL `[ACS] Profile delivery log replication`]** (newRcpDeliveryLogReplication): deze incrementele workflow repliceert bezorgings-id&#39;s, e-mailbrede logboeken en e-mailtrackinglogboeken van Campaign Standard naar Campagne v7. Het houdt slechts rekening met leveringen die van Campaign Standard naar profielen worden verzonden die deel van de nms :recipients lijst van Campagne v7 uitmaken.

  >[!NOTE]
  >
  > Als zowel Campaign Classic- als Campaign Standard-instanties worden gebruikt om e-mails met bijgehouden URL&#39;s te verzenden, kan er tijdens de synchronisatie een probleem met dubbele URL-tagID&#39;s optreden. Om dit te verhinderen gebeuren, werk de **het volgen URLs van de Update** (writerTrackingUrls) activiteit in het werkschema bij en voeg het &quot;ACS&quot;prefix aan de @tagId bronuitdrukking toe.

* **[!UICONTROL `[ACS] New delivery log replication`]** (newRcpDeliveryLogReplication): deze incrementele workflow repliceert bezorgings-id&#39;s, e-mailbrede logboeken en e-mailtrackinglogboeken van Campaign Standard naar Campagne v7. Het houdt slechts rekening met leveringen die van Campaign Standard naar profielen worden verzonden die deel van een specifieke lijst (om te bepalen, buiten nms :recipients) van Campagne v7 uitmaken.

### Standaardvelden voor ontvangers {#default-recipient-fields}

Als u extra velden of aangepaste tabellen hebt (bijvoorbeeld een tabel met transacties), worden deze niet standaard gerepliceerd. Geavanceerde configuratie moet worden uitgevoerd. Zie [ Geavanceerde implementatie ](#advanced-implementation).

U vindt onder de lijst met ontvangende velden die worden gerepliceerd met de basisimplementatie. Dit zijn de velden buiten het vak:

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong> Interne naam </strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Source-id <br /> </td> 
   <td> @sourceId<br /> </td> 
  </tr> 
  <tr> 
   <td> Aanmaakdatum <br /> </td> 
   <td> @created<br /> </td> 
  </tr> 
  <tr> 
   <td> Wijzigingsdatum <br /> </td> 
   <td> @lastModified<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mail <br /> </td> 
   <td> @email<br /> </td> 
  </tr> 
  <tr> 
   <td> Achternaam <br /> </td> 
   <td> @lastName<br /> </td> 
  </tr> 
  <tr> 
   <td> Voornaam <br /> </td> 
   <td> @firstName<br /> </td> 
  </tr> 
  <tr> 
   <td> Middennaam <br /> </td> 
   <td> @middleName<br /> </td> 
  </tr> 
  <tr> 
   <td> Mobiel <br /> </td> 
   <td> @mobilePhone <br /> </td> 
  </tr> 
  <tr> 
   <td> Geboortedatum <br /> </td> 
   <td> @bornDate<br /> </td> 
  </tr> 
  <tr> 
   <td> Geslacht <br /> </td> 
   <td> @gender<br /> </td> 
  </tr> 
  <tr> 
   <td> Aanhef <br /> </td> 
   <td> @salutation <br /> </td> 
  </tr> 
  <tr> 
   <td> Niet meer contact (door om het even welk kanaal) <br /> </td> 
   <td> @blackList <br /> </td> 
  </tr> 
  <tr> 
   <td> Geen contact meer per e-mail <br /> </td> 
   <td> @blackListEmail<br /> </td> 
  </tr> 
  <tr> 
   <td> Geen contact meer door SMS <br /> </td> 
   <td> @blackListMobile <br /> </td> 
  </tr> 
  <tr> 
   <td> Telefoon <br /> </td> 
   <td> @phone<br /> </td> 
  </tr> 
  <tr> 
   <td> Fax <br /> </td> 
   <td> @fax<br /> </td> 
  </tr> 
  <tr> 
   <td> Adres 1 (appartement) <br /> </td> 
   <td> [locatie/@adres1]<br /> </td> 
  </tr> 
  <tr> 
   <td> Adres 2 <br /> </td> 
   <td> [locatie/@adres2]<br /> </td> 
  </tr> 
  <tr> 
   <td> Adres 3 (Aantal en straat) <br /> </td> 
   <td> [location/@address3]<br /> </td> 
  </tr> 
  <tr> 
   <td> Adres 4 (county) <br /> </td> 
   <td> [locatie/@adres4]<br /> </td> 
  </tr> 
  <tr> 
   <td> Postcode <br /> </td> 
   <td> [location/@zipCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> Plaats <br /> </td> 
   <td> [location/@city]<br /> </td> 
  </tr> 
  <tr> 
   <td> Provincie-/staatcode <br /> </td> 
   <td> [location/@stateCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> Landcode <br /> </td> 
   <td> [location/@countryCode]<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Omzetting van rechten {#rights-conversion}

De rechten worden verschillend behandeld in Campaign v7 en Campaign Standard. In Campaign v7 is het rechtenbeheer gebaseerd op mappen, terwijl het in Campaign Standard gebaseerd is op eenheidstoegang (organisatorische/geografische eenheden). Een Campaign Standard-gebruiker behoort tot een beveiligingsgroep die de beperkingscontext bevat. Daarom moet het systeem van de rechten van de Campagne v7 worden omgezet om Campaign Standard aan te passen. Er zijn verschillende manieren om de rechtenconversie uit te voeren. Hieronder ziet u een voorbeeld van implementatie.

1. Gebruik onder **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]** de knop **[!UICONTROL Synchronize]** om alle Campaign Standard-beveiligingsgroepen op te halen. Campaign Standard-groepen buiten de box zijn uitgesloten.

   ![](assets/acs_connect_implementation_4.png)

1. Als uw rechtenbeheer een mappenbasis heeft, gaat u naar **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** en wijst u elke benodigde map toe aan een beveiligingsgroep.

   ![](assets/acs_connect_implementation_5.png)

1. De replicatiewerkstromen zullen dan deze informatie gebruiken en de overeenkomstige organisatorische/geografische eenheden toevoegen aan elk voorwerp om te herhalen.

### Geavanceerde implementatie {#advanced-implementation}

In dit gedeelte worden enkele mogelijkheden beschreven voor een geavanceerde implementatie.

>[!IMPORTANT]
>
>Deze informatie kan alleen als algemene richtsnoeren worden gebruikt. Neem contact op met uw Adobe Campaign-consultant voor de implementatie.

De geavanceerde implementatie voegt aangepaste replicatieworkflows toe, afhankelijk van de behoeften van de klant. Hier volgen enkele voorbeelden:

* Leveringsreplicatie
* Campagnereplicatie
* Programmareplicatie
* Replicatie van zaadleden
* Transactionele replicatie
* enz.

**het Repliceren van uitgebreide gebieden op ontvangers**

Met de basisimplementatie, worden de uit-van-de-doos ontvankelijke gebieden herhaald. Als u douanegebieden wilt herhalen die u aan het ontvankelijke schema toevoegde, moet u hen identificeren.

1. Maak onder **[!UICONTROL Administration > ACS Connector > Data mapping]** een doelafbeelding voor de **[!UICONTROL nms:recipient]** -tabel.

   ![](assets/acs_connect_implementation_6.png)

1. Selecteer de aanvullende velden die u wilt repliceren en andere benodigde gegevens (index, koppelingen, identificatietoetsen).

   ![](assets/acs_connect_implementation_7.png)

1. Open de toepassingsworkflow voor het toegewezen profiel (niet de sjabloon, maar de werkstroominstantie zelf). Wijzig de **[!UICONTROL Query]** - en **[!UICONTROL Update data]** -activiteiten om deze velden op te nemen. Zie [ Technische en replicatieworkflows ](#technical-and-replication-workflows).

   ![](assets/acs_connect_implementation_8.png)

   ![](assets/acs_connect_implementation_9.png)

**het Repliceren van de lijsten van het douaneprofiel**

Met de basisimplementatie, wordt de uit-van-de-doos ontvankelijke lijst herhaald. Als u aangepaste ontvankelijke lijsten hebt toegevoegd, is hier hoe u hen identificeert.

1. Maak onder **[!UICONTROL Administration > ACS Connector > Data mapping]** een doeltoewijzing in de tabel met aangepaste profielen.

   ![](assets/acs_connect_implementation_10.png)

1. Definieer de identificatiegegevens, de index, koppelingen en velden die u wilt repliceren.

   ![](assets/acs_connect_implementation_10.png)

1. Als uw rechtenbeheer is gebaseerd op mappen, gaat u naar **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** en definieert u een beveiligingsgroep voor de mappen die zijn gekoppeld aan uw aangepaste tabellen. Zie [ de omzetting van Rechten ](#rights-conversion).
1. Gebruik de **[!UICONTROL New replication]** -workflow (niet de sjabloon, maar de werkstroominstantie zelf) om de aangepaste tabel en de te repliceren velden op te nemen. Zie [ Technische en replicatieworkflows ](#technical-and-replication-workflows).
