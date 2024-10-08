---
product: campaign
title: Tabellen om te onderhouden
description: Tabellen om te onderhouden
feature: Monitoring
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---

# Tabellen om te onderhouden{#tables-to-maintain}



De lijst met tabellen die moet worden onderhouden, is afhankelijk van uw versie van Adobe Campaign, hoe u deze gebruikt en van de configuratie van het gegevensmodel.

De volgende lijst bevat slechts de lijsten het meest onderworpen aan fragmentatie. De gevolgen zijn als volgt:

* overconsumptie van schijfruimte, waardoor de databasetoegang wordt beïnvloed;
* indexen die niet regelmatig zijn bijgewerkt, waardoor de zoekprestaties afnemen.

## Adobe Campaign-tabellen {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong> Tabelnaam </strong><br /> </th> 
   <th> <strong> Grootte </strong><br /> </th> 
   <th> <strong> Belangrijkste type van activiteit </strong><br /> </th> 
   <th> <strong> Commentaren </strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery <br /> </td> 
   <td> Klein <br /> </td> 
   <td> Updates <br /> </td> 
   <td> Er is één record per leveringsactie. Eén record kan meerdere keren worden bijgewerkt om de voortgang van de levering te weerspiegelen. Daarom worden indexen in deze tabel vaak snel gefragmenteerd. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart <br /> </td> 
   <td> Medium<br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Werkentabel waarin records worden ingevoegd tijdens de voorbereiding van de levering. Deze worden vervolgens tijdens de levering bijgewerkt en worden ten slotte verwijderd zodra de levering is voltooid.<br /> Deze tabel bevat vaak een snel fragment, ook al is de gemiddelde grootte tamelijk beperkt. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, verwijderingen <br /> </td> 
   <td> Deze lijst bevat de informatie nodig om gepersonaliseerde spiegel pagina's te produceren. Het bevat een veld memo (CLOB) en zal als zodanig erg groot zijn. Het volume is direct evenredig met de geschiedenis van de spiegel-pagina's die worden bewaard. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat <br /> </td> 
   <td> Medium<br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Deze tabel bevat statistieken over het leveringsproces. De gegevens worden regelmatig bijgewerkt. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Medium<br /> </td> 
   <td> Updates, invoegingen <br /> </td> 
   <td> Deze tabel bevat informatie over e-mailadressen. Het wordt vaak bijgewerkt als deel van het quarantaineproces (de verslagen worden gecreeerd bij de eerste leveringsfout, bijgewerkt wanneer de tellers veranderen en worden geschrapt zodra de levering succesvol is). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow <br /> </td> 
   <td> Klein <br /> </td> 
   <td> Updates <br /> </td> 
   <td> Er is één record per werkstroominstantie, dus er zijn maar weinig records. Nochtans wordt de lijst regelmatig bijgewerkt om status en vooruitgang te weerspiegelen.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask <br /> </td> 
   <td> Klein <br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Elke uitvoering van een workflowactiviteit leidt tot het maken van een record in deze tabel. Het zuiveringsmechanisme schrapt hen zodra zij zijn verlopen.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent <br /> </td> 
   <td> Klein <br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Elke overgang die wordt geactiveerd tussen taken in een werkstroom, leidt tot het maken van een record in deze tabel. Deze worden verwijderd als ze verlopen zijn. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob <br /> </td> 
   <td> Heel klein <br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Deze tabel is specifiek voor de workflow-engine. Het laat het verzenden van bevelen aan werkschema's (Begin, Einde, Pauze, bijvoorbeeld) toe. Hoewel het klein is, wordt deze lijst in aanmerking genomen tijdens de zuivering van transactietabellen verbonden aan werkschema's.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog <br /> </td> 
   <td> Grootste <br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Dit is de grootste tabel in het systeem. Er is één verslag per verzonden bericht, en deze verslagen worden opgenomen, bijgewerkt om de leveringsstatus te volgen, en geschrapt wanneer de geschiedenis wordt gezuiverd. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, verwijderingen <br /> </td> 
   <td> Logbestanden voor bijhouden worden ingevoegd en verwijderd wanneer de historie wordt gewist, maar worden niet bijgewerkt. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Klein <br /> </td> 
   <td> Updates <br /> </td> 
   <td> Deze lijst bevat informatie die voor het kwalificeren van SMTP fouten wordt gebruikt. Het is vrij klein, maar zal massaal worden bijgewerkt, zodat de indexen op deze lijst neigen snel te fragmenteren. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat <br /> </td> 
   <td> Medium<br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Deze lijst bevat de aggregaten op fouten SMTP die door domein worden gesorteerd. Het bevat aanvankelijk gedetailleerde informatie die door de schoonmaaktaak wordt samengevoegd zodra het verouderd wordt. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (op een mid-sourcing instantie) <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Alleen wanneer de instantie 5.10 (of hoger) wordt gebruikt als een instantie voor midsourcing. Dit is een van de grootste tabellen in de database. Er is één verslag per verzonden bericht, en deze verslagen worden opgenomen, bijgewerkt om de leveringsstatus te volgen, en geschrapt wanneer de geschiedenis wordt gezuiverd. Als u gebruik maakt van mid-sourcing, wordt aanbevolen de geschiedenis te beperken (meestal minder dan twee maanden). Deze tabel blijft dus redelijk qua grootte (minder dan 30 Go voor 60 miljoen rijen, data+index), maar het is van tijd tot tijd belangrijk om de tabel opnieuw op te bouwen. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (wanneer de tabel NmsRecipient wordt gebruikt) <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Dit is de grootste tabel in het systeem. Er is één verslag per verzonden bericht, en deze verslagen worden opgenomen, bijgewerkt om de leveringsstatus te volgen, en geschrapt wanneer de geschiedenis wordt gezuiverd. Merk op dat in 5.10, deze lijst kleiner is dan het equivalent in 4.05 (NmsBroadLog) aangezien de SMTP berichttekst in de tabel NmsBroadLogMsg in versie 5.10 wordt verdisconteerd. Het blijft echter van essentieel belang om deze tabel regelmatig opnieuw te indexeren (om de twee weken om mee te beginnen) en deze van tijd tot tijd volledig opnieuw op te bouwen (eenmaal per maand of wanneer de prestaties worden beïnvloed). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (wanneer een externe ontvankelijke lijst wordt gebruikt) <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Hetzelfde als NmsBroadLogRcp, maar met een externe tabel voor ontvangers. Pas Yyy en Xxx aan met de waarden in de leveringstoewijzing. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (wanneer de tabel NmsRecipient wordt gebruikt) <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, verwijderingen <br /> </td> 
   <td> Logbestanden voor bijhouden worden ingevoegd en verwijderd wanneer de historie wordt gewist, maar worden niet bijgewerkt. Het volume is afhankelijk van de lengte van de gegevensbewaring. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx (wanneer de externe ontvankelijke lijst wordt gebruikt) <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, verwijderingen <br /> </td> 
   <td> Hetzelfde als NmsTrackingLogRcp maar met een externe ontvangertabel. Pas Yyy en Xxx aan met de waarden die worden gebruikt in de leveringstoewijzing. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (de uitvoeringsinstantie van het Centrum van het Bericht) <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Gelijkaardig aan andere uitzendingstabellen, maar met NmsRtEvent in plaats van NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent ( de uitvoeringsinstantie van het Centrum van het Bericht) <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, verwijderingen <br /> </td> 
   <td> Gelijkaardig aan andere trackingLog lijsten, maar met de lijst NmsRtEvent in plaats van NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (de uitvoeringsinstantie van het Centrum van het Bericht) <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Lijst die de de gebeurtenisrij van het Centrum van het Bericht bevat. De status van deze gebeurtenissen wordt bijgewerkt door Message Center terwijl ze worden verwerkt. Tijdens de zuivering worden verwijderingen uitgevoerd. Wij adviseren u regelmatig de index van deze lijst opnieuw te creëren en het te herbouwen.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (de controleinstantie van het Centrum van het Bericht) <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Vergelijkbaar met NmsRtEvent. Deze tabel archiveert elke gebeurtenis van alle uitvoeringsinstanties. Het wordt gebruikt door geen proces in real time, slechts door rapporten.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp <br /> </td> 
   <td> Erg klein <br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Tabellen die mobiele toepassingen en hun configuratie omvatten.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, updates <br /> </td> 
   <td> Lijst die de herkenningstekens van mobiele apparaten (adressen) omvat die worden gebruikt om het bericht (gelijkend op een ontvankelijke lijst) te verzenden.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, updates, verwijderingen <br /> </td> 
   <td> Gelijkaardig aan andere uitzendingstabellen, maar met NmsappSubscriptionRcp in plaats van NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp <br /> </td> 
   <td> Groot <br /> </td> 
   <td> Invoegingen, verwijderingen <br /> </td> 
   <td> Gelijkaardig aan andere trackingLog lijsten, maar met de lijst NmsappSubscriptionRcp in plaats van NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo <br /> </td> 
   <td> Klein <br /> </td> 
   <td> Invoegingen, verwijderingen <br /> </td> 
   <td> Tabel die gebruikerssessies bevat. Het aantal toevoegingen en schrappingen is zeer belangrijk.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Klanttabellen {#customer-tables}

Naast de bovenstaande lijst kunnen tabellen die tijdens de installatie van het platform door klanten zijn gemaakt (en die niet in het Adobe Campaign-gegevensmodel staan), ook worden gefragmenteerd, vooral als deze tabellen vaak worden bijgewerkt tijdens het laden of synchroniseren van gegevens. Deze lijsten kunnen deel van het standaard de gegevensmodel van Adobe Campaign (bijvoorbeeld **NmsRecipient**) uitmaken. In dit geval, is het aan de beheerder van het platform van Adobe Campaign om een controle van zijn specifiek gegevensbestandmodel uit te voeren om deze douanetabellen te vinden. Deze lijsten worden noodzakelijk niet uitdrukkelijk vermeld in onze onderhoudsprocedures.
