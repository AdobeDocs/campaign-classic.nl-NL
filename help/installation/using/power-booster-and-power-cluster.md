---
title: Power Booster en Power Cluster
seo-title: Power Booster en Power Cluster
description: Power Booster en Power Cluster
seo-description: null
page-status-flag: never-activated
uuid: 4d23ed42-a368-4bd6-afaf-48452e253d19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 715d2b69-5b47-4890-8b7d-1dc0a0d4ead8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a5072ba55690d4d88c12ac7ff647f163deddbf32

---


# Power Booster en Power Cluster{#power-booster-and-power-cluster}

## Overzicht {#overview}

Adobe Campaign biedt u twee sets vooraf verpakte architectuuropties waarmee u uw implementatie kunt afmeten:

* **Extra voeding**

   Deze optie biedt ondersteuning voor één extra uitvoeringsinstantie die is losgekoppeld van de primaire toepassingsinstantie van Adobe Campagne. Speciale uitvoeringsinstanties kunnen op afstand of door een derde worden gehost. Wanneer geïmplementeerd, worden e-mailuitvoering, bijhouden, spiegel- en stuiterberichten onafhankelijk van de centrale toepassingsfuncties afgehandeld.

* **Power Cluster**

   Deze optie biedt ondersteuning voor 2 tot N geclusterde uitvoeringsinstanties, losgekoppeld van de primaire toepassing van Adobe Campagne voor een bepaalde toepassing. Clusters kunnen op afstand, in gedistribueerde implementaties en door derden worden gehost. Naast de voordelen van procesisolatie, maakt de optie van de Cluster van de Macht van de Campagne van Adobe overtolligheid en schaal uit strategieën gebruikend grondstoffenhardware voor vereenvoudigde evolutie van SLA of prestaties mogelijk.

![](assets/architectural_options_diagram.png)

## Subsidiabele aanvragen {#eligible-applications}

De opties voor Power Booster en Power Cluster kunnen door de volgende toepassingen worden gebruikt:

* Campagne
* Leads
* Aflevering
* Berichtencentrum

## Matrix met architectuuraanbevelingen {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Standaardarchitectuur</strong><br /> </td> 
   <td> <strong>Extra voeding</strong><br /> </td> 
   <td> <strong>Power Cluster</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> E-mailcampagnes en uitgaande interacties<br /> </td> 
   <td> Tot ongeveer 30 miljoen e-mails per maand<br /> </td> 
   <td> 30 tot 100 miljoen e-mails per maand<br /> </td> 
   <td> Meer dan 100 miljoen e-mails per maand<br /> </td> 
  </tr> 
  <tr> 
   <td> Transactieberichten<br /> </td> 
   <td> 50.000 per uur per uitvoeringsserver<br /> </td> 
   <td> 50.000 per uur per uitvoeringsserver<br /> </td> 
   <td> 50.000 per uur per uitvoeringsserver<br /> </td> 
  </tr> 
  <tr> 
   <td> Beschikbaarheid<br /> </td> 
   <td> Dat van de primaire database<br /> </td> 
   <td> 24/7 behalve onderhoudsvensters en downtimes voor de uitvoeringsinstantie<br /> </td> 
   <td> 24-07-365 service mogelijk<br /> </td> 
  </tr> 
  <tr> 
   <td> Beveiliging<br /> </td> 
   <td> Gegevensmarkt is mogelijk toegankelijk via het openbare internet<br /> </td> 
   <td> Gegevensmarkt is geïsoleerd van frontale, internetgerichte componenten<br /> </td> 
   <td> Gegevensmarkt is geïsoleerd van frontale, internetgerichte componenten<br /> </td> 
  </tr> 
  <tr> 
   <td> Implementatiesjabloon<br /> </td> 
   <td> Alles op één site (kan zich op locatie bevinden of in de cloud)<br /> </td> 
   <td> Marketing op locatie met uitvoering in de cloud mogelijk<br /> </td> 
   <td> marketing op locatie met uitvoering in de cloud; uitvoering in verschillende geo ' s mogelijk<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Aanbevelingen {#recommendations}

* Een uitvoeringsinstantie moet aan de dienst worden gewijd. U kunt geen pakket installeren voor een service waarop u zich niet hebt geabonneerd. Als u bijvoorbeeld een abonnement neemt op de optie **Power Booster** voor de service **Message Center** , mag u het **[!UICONTROL Execution of transactional messages]** pakket alleen op de toegewezen uitvoeringsinstantie installeren. Controleer uw licentieovereenkomst.
* Aangezien speciale instanties (of clusters) Adobe Campagne-instanties zijn, zijn de aanbevelingen hetzelfde als voor een hoofdinstantie. Raadpleeg [dit document](../../production/using/foreword.md)voor meer informatie.
* Neem contact op met de Adobe Campagne Professional Services om de instantie correct te configureren vanuit het oogpunt van database-/hardwarecomponenten.

