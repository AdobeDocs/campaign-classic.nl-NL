---
solution: Campaign Classic
product: campaign
title: ACS-verbindingsbeginselen en gegevenscyclus
description: ACS-verbindingsbeginselen en gegevenscyclus
audience: integrations
content-type: reference
topic-tags: acs-connector
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1990'
ht-degree: 0%

---


# ACS Connector principles and data cycle{#acs-connector-principles-and-data-cycle}

## Inleiding {#introduction}

ACS Connector bridges Adobe Campaign v7 en Adobe Campaign Standard. Het is een geïntegreerde eigenschap in Campagne v7 die automatisch gegevens aan Campaign Standard herhaalt, die het beste van beide toepassingen verenigt. Campagne v7 heeft geavanceerde hulpmiddelen om het primaire marketing gegevensbestand te beheren. De gegevensreplicatie van Campagne v7 staat Campaign Standard toe om de rijke gegevens in een gebruikersvriendelijk milieu te gebruiken.

![](assets/acs_connect_puzzle_link_01.png)

Met de Schakelaar ACS, blijft Campaign Standard door digitale marketers worden gebruikt om, campagnes te ontwerpen te richten en uit te voeren terwijl Campaign v7 voor gegeven-georiënteerde gebruikers zoals gegevensbestandmarketers wordt gemaakt.

>[!IMPORTANT]
>
>ACS Connector is alleen beschikbaar als onderdeel van de Adobe Campaign Premier-aanbieding. Neem contact op met uw accountmanager voor meer informatie over het in licentie geven van Adobe Campaign Premier.
>
>ACS Connector is slechts beschikbaar voor ontvangen en hybride architecturen. Het is niet beschikbaar voor volledige installaties op locatie.
>
>Als u deze functie wilt gebruiken, moet u verbinding maken met een campagne met een Adobe ID (IMS). See [Connecting via an Adobe ID](../../integrations/using/about-adobe-id.md).

Dit document stelt de mogelijkheden ACS-Connector voor. In de volgende secties vindt u informatie over de manier waarop de functie gegevens en instructies over het werken met gerepliceerde profielen retourneert.

* [Proces](#process): Overzicht van de Schakelaar ACS en hoe de gegevensreplicatie wordt beheerd.
* [Implementatie](#implementation): Overzicht van hoe te beginnen met de Schakelaar ACS evenals instructies op hoe te om basis en geavanceerde gegevens te herhalen.
* [Profielen](../../integrations/using/synchronizing-profiles.md)synchroniseren: Instructies voor het repliceren van profielen en het maken van leveringen met deze profielen.
* [Synchroniserend publiek](../../integrations/using/synchronizing-audiences.md): Instructies over hoe te om een lijst van ontvangers in Campagne v7 te richten en dan de lijst aan Campaign Standard als publiek te herhalen.
* [Webtoepassingen](../../integrations/using/synchronizing-web-applications.md)synchroniseren: Instructies voor het koppelen van Campagne v7-webtoepassingen aan Campaign Standard.
* [Het oplossen van problemen de Schakelaar](../../integrations/using/troubleshooting-the-acs-connector.md)ACS: Herzie antwoorden op gemeenschappelijke problemen.

>[!NOTE]
>
>De Schakelaar ACS is inbegrepen met Campaign v7 onder vergunningsovereenkomst. Om de Schakelaar ACS te gebruiken, zorg ervoor dat u tussen Campagne v7 en Campaign Standard kunt schakelen. Neem contact op met de beheerder als u niet zeker weet van uw versie en de opgenomen functies.

## Proces {#process}

### Gegevensreplicatie {#data-replication}

![](assets/acs_connect_flows_01.png)

De Schakelaar ACS herhaalt periodiek de volgende punten van Campagne v7 aan Campaign Standard:

* **Ontvangers**
* **Abonnementen**
* **Services**
* **Landingspagina’s**

Door gebrek, is de periodieke replicatie voor Schakelaar ACS eens om de 15 minuten. De periode van de periodieke replicatie kan aan uw behoeften worden aangepast. Neem contact op met uw consultant als er wijzigingen nodig zijn.

Gegevensreplicatie voor ontvangers, abonnementen, services en bestemmingspagina&#39;s is incrementeel, wat betekent dat alleen nieuwe ontvangers en wijzigingen aan bestaande ontvangers worden gerepliceerd van Campagne v7 naar Campaign Standard. Nochtans, komt de replicatie voor een publiek in één enkele instantie voor. U kunt een publiek in Campagne v7 creëren en dan het één keer aan Campaign Standard herhalen. De replicatie is direct en kan niet voor regelmatige updates worden gevormd. Zie [Soorten publiek](../../integrations/using/synchronizing-audiences.md)synchroniseren voor instructies.

>[!NOTE]
>
>Wees geduldig met de eerste replicatie van een grote database, omdat dit enkele uren kan duren. De volgende replicaties zijn echter incrementeel en veel sneller.

De Schakelaar ACS herhaalt periodiek de volgende punten van Campaign Standard aan Campagne v7:

* **[!UICONTROL Delivery IDs]**
* **[!UICONTROL Email broad logs]**
* **[!UICONTROL Email tracking logs]**

Dankzij replicatie van bezorgings-id&#39;s en e-maillogboeken hebt u toegang tot de geschiedenis van leveringen en traceringsgegevens voor uw v7-ontvangers vanuit Campagne v7.

>[!IMPORTANT]
>
>Alleen e-mailuitzendingen en trackinglogboeken worden vanuit Campaign Standard naar Campaign v7 gerepliceerd.

### Gegevenssynchronisatie {#data-synchronization}

![](assets/acs_connect_flows_02.png)

De Schakelaar ACS synchroniseert quarantines tussen Campagne v7 en Campaign Standard.

Een profiel dat is gerepliceerd van Campagne v7 naar Campaign Standard, bevat bijvoorbeeld een e-mailadres. Als het e-mailadres door Campaign Standard in quarantined is, worden de gegevens overgegaan tot Campagne v7 tijdens de volgende synchronisatie. Voor meer informatie over quarantines, zie het beheer [van de](../../delivery/using/understanding-quarantine-management.md) Quarantaine en [Campaign Standard Quarantines](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html).

### Gepliceerde profielen gebruiken {#using-replicated-profiles}

Campaign Standard en Campagne v7 kunnen herhaalde profielen gebruiken voor het maken van doelgerichte workflows in marketingcampagnes.

Zie [Profielen](../../integrations/using/synchronizing-profiles.md)synchroniseren voor instructies over het verzenden van leveringen in Campaign Standard met behulp van gerepliceerde profielen. Er zijn aanvullende instructies beschikbaar voor het delen van de gegevens voor niet-abonnementen tussen Campagne v7 en Campaign Standard.

### Beperkingen {#limitations}

Gedetailleerde profielen zijn gemakkelijk beschikbaar voor leveringen, maar hebben bepaalde beperkingen in Campaign Standard. Bekijk de onderstaande objecten voor meer informatie over hoe u ze het beste kunt beheren.

* **Alleen-lezen profielen voor Campaign Standard**: Gepliceerde profielen zijn alleen-lezen in Campaign Standard. Nochtans, kunt u ontvangers in Campagne v7 uitgeven en de wijzigingen worden automatisch bijgewerkt in Campaign Standard door Schakelaar ACS.
* **Profielen gemaakt in Campaign Standard**: De Schakelaar ACS herhaalt ontvankelijke gegevens in één richting, van Campagne v7 aan Campaign Standard. Daarom worden profielen die afkomstig zijn uit Campaign Standard niet gerepliceerd naar Campagne v7.
* **Basisgegevens voor ontvangers voor Campaign Standard**: De Schakelaar ACS herhaalt ontvankelijke gegevens die voor Campaign Standard geschikt zijn. Hieronder vallen namen, adressen, e-mailadressen, mobiele telefoonnummers, thuistelefoonnummers en andere relevante contactgegevens van ontvangers. Neem contact op met uw consultant als extra ontvangende velden en aangepaste doeltabellen in Campagne v7 van essentieel belang zijn voor uw workflow.
* **In quarantaine geplaatste profielen** importeren: Lijsten met profielen waarmee u geen contact wilt opnemen, kunnen worden geïmporteerd in Campagne v7 of Campaign Standard als quarantaineprofielen. De status voor de profielen wordt opgenomen in de quarantainesynchronisatie tussen de toepassingen en wordt niet gebruikt in leveringen.
* **Abonnement op een service in Campaign Standard** opzeggen: De keuze om het abonnement op een levering op te zeggen, wordt niet gesynchroniseerd van Campaign Standard naar Campagne v7. Nochtans, kunt u een levering van de Campaign Standard vormen om zijn unsubscription verbinding aan Campaign v7 te richten. Het profiel voor een ontvanger die op de koppeling voor het opzeggen van abonnementen klikt, wordt bijgewerkt in Campagne v7 en de gegevens worden gerepliceerd naar Campaign Standard. Zie [De koppeling](../../integrations/using/synchronizing-profiles.md#changing-the-unsubscription-link)voor abonnementen wijzigen.
* Alleen e-mailuitzendingen en trackinglogboeken worden vanuit Campaign Standard naar Campaign v7 gerepliceerd.

### Facturering {#billing}

Het factureren wordt niet beïnvloed door uw keuze van toepassing voor het verzenden van leveringen, Campagne v7 of Campaign Standard. Factureringsgegevens worden afgestemd tussen Campagne v7 en Campaign Standard. Daarom als u leveringen naar de zelfde ontvanger verzendt gebruikend beide toepassingen, wordt het nog geteld als één actief profiel.

## Implementatie {#implementation}

Er bestaan twee soorten implementatie voor ACS-connector. Beide worden altijd uitgevoerd door het Adobe Campaign Consulting-team.

>[!IMPORTANT]
>
>Deze sectie is alleen bedoeld voor professionele gebruikers, zodat zij een algemeen overzicht krijgen van het implementatieproces en de belangrijkste stappen ervan.
>
>Probeer op geen enkele manier zelf een van deze implementaties uit te voeren. Het is uitsluitend voorbehouden aan de consultants van Adobe Campaign.

De **basisimplementatie** staat u toe om ontvangers (uit-van-de-doos gebieden), de diensten en abonnementen, Webtoepassingen en publiek te herhalen. Dit is een eenrichtingsreplicatie van Campagne v7 naar Campaign Standard.

De **geavanceerde implementatie** zal u toestaan om complexere gebruiksgevallen uit te voeren, bijvoorbeeld als u extra ontvankelijke gebieden of douane ontvankelijke lijsten (transactietabel bijvoorbeeld) hebt. Zie [Geavanceerde implementatie](#advanced-implementation).

### Het pakket installeren {#installing-the-package}

Als u deze functie wilt gebruiken, moet het **[!UICONTROL ACS Connector]** pakket zijn geïnstalleerd. Dit wordt altijd uitgevoerd door de technische beheerder of consultant van Adobe.

Alle technische elementen met betrekking tot de Schakelaar ACS zijn beschikbaar in de **[!UICONTROL Administration > ACS Connector]** knoop van de ontdekkingsreiziger.

### Technische en replicatieworkflows {#technical-and-replication-workflows}

Na de installatie van het pakket zijn onder **[!UICONTROL Administration > ACS Connector > Process]**.

>[!IMPORTANT]
>
>Probeer nooit deze workflows te wijzigen. Ze mogen nooit fout zijn of gepauzeerd zijn. Neem contact op met uw Adobe Campaign-consultant als dit gebeurt.

![](assets/acs_connect_implementation_3.png)

* **[!UICONTROL `[ACS] Quarantine synchronization`]** (quarantaineSync): in deze workflow worden alle quarantainegegevens gesynchroniseerd. Alle nieuwe quarantines in Campagne v7 worden herhaald in Campaign Standard. Alle nieuwe quarantines van Campaign Standard worden herhaald in Campaign v7. Dit waarborgt dat alle uitsluitingsregels tussen Campagne v7 en Campaign Standard worden gesynchroniseerd.
* **[!UICONTROL `[ACS] Security group synchronization`]** (securityGroupSync): deze workflow wordt gebruikt voor het converteren van rechten. Zie [Rechtenomzetting](#rights-conversion).

De volgende replicatiewerkschema&#39;s zijn beschikbaar als &quot;klaar om&quot;malplaatjes worden gebruikt. Ze moeten worden geïmplementeerd door uw Adobe Campaign-consultant.

![](assets/acs_connect_implementation_2.png)

* **[!UICONTROL `[ACS] Profile replication`]** (newProfileReplication): in deze incrementele workflow worden ontvangers naar Campaign Standard gerepliceerd. Standaard worden alle ontvangende velden buiten het vak gerepliceerd. Zie [Standaardontvangende velden](#default-recipient-fields).
* **[!UICONTROL `[ACS] Service replication`]** (newServiceReplication): deze incrementele werkstroom repliceert de gekozen services naar Campaign Standard. Zie het gebruik van hoofdletters en kleine letters [synchroniseren van webtoepassingen](../../integrations/using/synchronizing-web-applications.md).
* **[!UICONTROL `[ACS] Landing pages replication`]** (newLandingPageReplication): deze incrementele workflow repliceert de gekozen webtoepassingen naar Campaign Standard. De Campagne v7-webtoepassingen worden weergegeven als bestemmingspagina&#39;s in Campaign Standard. Zie het gebruik van hoofdletters en kleine letters [synchroniseren van webtoepassingen](../../integrations/using/synchronizing-web-applications.md).
* **[!UICONTROL `[ACS] New replication`]** (newReplication): deze incrementele workflow is een voorbeeld dat kan worden gebruikt om een aangepaste tabel te repliceren. Zie [Geavanceerde implementatie](#advanced-implementation).
* **[!UICONTROL `[ACS] Delivery-mesage replication`]** (newDlvMsgQualification): deze incrementele workflow repliceert leveringsberichten van Campaign Standard naar Campaign v7.
* **[!UICONTROL `[ACS] Profile delivery log replication`]** (newRcpDeliveryLogReplication): deze incrementele workflow bevat een kopie van bezorgings-id&#39;s, e-mailbrede logboeken en e-mailtrackinglogboeken van Campaign Standard naar Campaign v7. Er wordt alleen rekening gehouden met leveringen die door Campaign Standard zijn verzonden naar profielen die onderdeel zijn van de tabel nms:ontvangers in Campagne v7.
* **[!UICONTROL `[ACS] New delivery log replication`]** (newRcpDeliveryLogReplication): deze incrementele workflow bevat een kopie van bezorgings-id&#39;s, e-mailbrede logboeken en e-mailtrackinglogboeken van Campaign Standard naar Campaign v7. Er wordt alleen rekening gehouden met leveringen die van Campaign Standard naar profielen worden verzonden die deel uitmaken van een specifieke tabel (om te definiëren, anders dan nms:ontvangers) van Campagne v7.

### Standaardvelden voor ontvangers {#default-recipient-fields}

Als u extra velden of aangepaste tabellen hebt (bijvoorbeeld een tabel met transacties), worden deze niet standaard gerepliceerd. Geavanceerde configuratie moet worden uitgevoerd. Zie [Geavanceerde implementatie](#advanced-implementation).

U vindt onder de lijst met ontvangende velden die worden gerepliceerd met de basisimplementatie. Dit zijn de velden buiten het vak:

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Bron-id<br /> </td> 
   <td> @sourceId<br /> </td> 
  </tr> 
  <tr> 
   <td> Aanmaakdatum<br /> </td> 
   <td> @created<br /> </td> 
  </tr> 
  <tr> 
   <td> Wijzigingsdatum<br /> </td> 
   <td> @lastModified<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mail<br /> </td> 
   <td> @email<br /> </td> 
  </tr> 
  <tr> 
   <td> Achternaam<br /> </td> 
   <td> @lastName<br /> </td> 
  </tr> 
  <tr> 
   <td> Voornaam<br /> </td> 
   <td> @firstName<br /> </td> 
  </tr> 
  <tr> 
   <td> Tweede voornaam<br /> </td> 
   <td> @middleName<br /> </td> 
  </tr> 
  <tr> 
   <td> Mobiel<br /> </td> 
   <td> @mobilePhone<br /> </td> 
  </tr> 
  <tr> 
   <td> Geboortedatum<br /> </td> 
   <td> @bornDate<br /> </td> 
  </tr> 
  <tr> 
   <td> Geslacht<br /> </td> 
   <td> @gender<br /> </td> 
  </tr> 
  <tr> 
   <td> Aanhef<br /> </td> 
   <td> @salutation<br /> </td> 
  </tr> 
  <tr> 
   <td> Geen contact meer (via een kanaal)<br /> </td> 
   <td> @blackList<br /> </td> 
  </tr> 
  <tr> 
   <td> Geen contact meer per e-mail<br /> </td> 
   <td> @blackListEmail<br /> </td> 
  </tr> 
  <tr> 
   <td> Geen contact meer met SMS<br /> </td> 
   <td> @blackListMobile<br /> </td> 
  </tr> 
  <tr> 
   <td> Telefoon<br /> </td> 
   <td> @phone<br /> </td> 
  </tr> 
  <tr> 
   <td> Fax<br /> </td> 
   <td> @fax<br /> </td> 
  </tr> 
  <tr> 
   <td> Adres 1 (appartement)<br /> </td> 
   <td> [locatie/@adres1]<br /> </td> 
  </tr> 
  <tr> 
   <td> Adres 2<br /> </td> 
   <td> [locatie/@adres2]<br /> </td> 
  </tr> 
  <tr> 
   <td> Adres 3 (nummer en straat)<br /> </td> 
   <td> [locatie/@adres3]<br /> </td> 
  </tr> 
  <tr> 
   <td> Adres 4 (provincie)<br /> </td> 
   <td> [locatie/@adres4]<br /> </td> 
  </tr> 
  <tr> 
   <td> Postcode<br /> </td> 
   <td> [locatie/@zipCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> Plaats<br /> </td> 
   <td> [locatie/@stad]<br /> </td> 
  </tr> 
  <tr> 
   <td> Provincie<br /> </td> 
   <td> [location/@stateCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> Landcode<br /> </td> 
   <td> [locatie/@landcode]<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Omzetting van rechten {#rights-conversion}

De rechten worden verschillend behandeld in Campagne v7 en Campaign Standard. In Campaign v7 is het rechtenbeheer gebaseerd op mappen, terwijl in Campaign Standard het gebaseerd is op eenheidstoegang (organisatorische/geografische eenheden). Een gebruiker van de Campaign Standard behoort tot veiligheidsgroep die de beperkingscontext bevat. Daarom moet het systeem van de rechten van de Campagne v7 worden omgezet om Campaign Standard aan te passen. Er zijn verschillende manieren om de rechtenconversie uit te voeren. Hieronder ziet u een voorbeeld van implementatie.

1. Onder **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**, gebruik de **[!UICONTROL Synchronize]** knoop om alle de veiligheidsgroepen van de Campaign Standard terug te winnen. Campaign Standard-groepen buiten de doos zijn uitgesloten.

   ![](assets/acs_connect_implementation_4.png)

1. Als uw rechtenbeheer een mappenbasis heeft, gaat u naar elke benodigde map **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** en wijst u deze toe aan een beveiligingsgroep.

   ![](assets/acs_connect_implementation_5.png)

1. De replicatiewerkstromen zullen dan deze informatie gebruiken en de overeenkomstige organisatorische/geografische eenheden toevoegen aan elk voorwerp om te herhalen.

### Geavanceerde implementatie {#advanced-implementation}

In dit gedeelte worden enkele mogelijkheden beschreven voor een geavanceerde implementatie.

>[!IMPORTANT]
>
>Deze informatie kan alleen als algemene richtsnoeren worden gebruikt. Vraag uw Adobe Campaign-consultant om informatie over de implementatie.

De geavanceerde implementatie voegt aangepaste replicatieworkflows toe, afhankelijk van de behoeften van de klant. Hier volgen enkele voorbeelden:

* Leveringsreplicatie
* Campagnereplicatie
* Programmareplicatie
* Replicatie zaadleden
* Transactionele replicatie
* enz.

**Uitgebreide velden repliceren op ontvangers**

Met de basisimplementatie, worden de uit-van-de-doos ontvankelijke gebieden herhaald. Als u douanegebieden wilt herhalen die u aan het ontvankelijke schema toevoegde, moet u hen identificeren.

1. Maak onder **[!UICONTROL Administration > ACS Connector > Data mapping]** een doelafbeelding voor de **[!UICONTROL nms:recipient]** tabel.

   ![](assets/acs_connect_implementation_6.png)

1. Selecteer de aanvullende velden die u wilt repliceren en andere benodigde gegevens (index, koppelingen, identificatietoetsen).

   ![](assets/acs_connect_implementation_7.png)

1. Open de toepassingsworkflow voor de toegewezen profielreplicatie (niet de sjabloon, maar de werkstroominstantie zelf). Wijzig de **[!UICONTROL Query]** en de **[!UICONTROL Update data]** activiteiten om deze gebieden op te nemen. Zie [Technische workflows en replicatieworkflows](#technical-and-replication-workflows).

   ![](assets/acs_connect_implementation_8.png)

   ![](assets/acs_connect_implementation_9.png)

**Repliceren van aangepaste profieltabellen**

Met de basisimplementatie, wordt de uit-van-de-doos ontvankelijke lijst herhaald. Als u aangepaste ontvankelijke lijsten hebt toegevoegd, is hier hoe u hen identificeert.

1. Maak onder **[!UICONTROL Administration > ACS Connector > Data mapping]** een doelafbeelding in de tabel met aangepaste profielen.

   ![](assets/acs_connect_implementation_10.png)

1. Definieer de identificatiegegevens, -index, -koppelingen en -velden die u wilt repliceren.

   ![](assets/acs_connect_implementation_10.png)

1. Als uw rechtenbeheer is gebaseerd op mappen, gaat u naar **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** en definieert u een beveiligingsgroep voor de mappen die zijn gekoppeld aan uw aangepaste tabellen. Zie [Rechtenomzetting](#rights-conversion).
1. Gebruik de **[!UICONTROL New replication]** workflow (niet de sjabloon, maar de werkstroominstantie zelf) om de aangepaste tabel en de velden op te nemen die u wilt repliceren. Zie [Technische workflows en replicatieworkflows](#technical-and-replication-workflows).

