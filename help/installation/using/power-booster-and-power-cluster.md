---
product: campaign
title: Power Booster en Power Cluster
description: Power Booster en Power Cluster
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 6%

---

# Power Booster en Power Cluster{#power-booster-and-power-cluster}



## Overzicht {#overview}

Adobe Campaign biedt u twee sets vooraf verpakte architecturale opties voor het dimensioneren van uw implementatie:

* **Extra voeding**

  Deze optie biedt ondersteuning voor één extra uitvoeringsinstantie die is losgekoppeld van de primaire Adobe Campaign-toepassingsinstantie. Speciale uitvoeringsinstanties kunnen op afstand of door een derde worden gehost. Wanneer geïmplementeerd, worden e-mailuitvoering, bijhouden, spiegel- en stuiterberichten onafhankelijk van de centrale toepassingsfuncties afgehandeld.

* **Power Cluster**

  Deze optie biedt ondersteuning voor 2 tot N geclusterde uitvoeringsinstanties die zijn losgekoppeld van de primaire Adobe Campaign-toepassingsinstantie met betrekking tot een bepaalde toepassing. Clusters kunnen op afstand, in gedistribueerde implementaties en door derden worden gehost. Naast de voordelen van procesisolatie, maakt de Adobe Campaign Power Cluster-optie redundantie mogelijk en schaalt deze strategieën uit met behulp van gewone hardware voor een vereenvoudigde ontwikkeling van SLA of prestaties.

![](assets/architectural_options_diagram.png)

## Subsidiabele aanvragen {#eligible-applications}

De opties voor Power Booster en Power Cluster kunnen door de volgende toepassingen worden gebruikt:

* Campaign
* Levering
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
   <td> Transactionele berichten<br /> </td> 
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
   <td> Marketing op locatie met uitvoering in de cloud; uitvoering in verschillende geopos mogelijk<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Aanbevelingen {#recommendations}

* Een uitvoeringsinstantie moet aan de dienst worden gewijd. U kunt geen pakket installeren voor een service waarop u zich niet hebt geabonneerd. Als u zich bijvoorbeeld abonneert op de **Extra voeding** voor de **Berichtencentrum** -service, kunt u alleen de **[!UICONTROL Execution of transactional messages]** pakket op de toegewezen uitvoeringsinstantie. Controleer hiervoor uw licentieovereenkomst.
* Aangezien specifieke instanties (of clusters) Adobe Campaign-instanties zijn, zijn de aanbevelingen hetzelfde als voor een hoofdinstantie. Raadpleeg voor meer informatie hierover [dit document](../../production/using/foreword.md).
* Neem contact op met Adobe Campaign Professional Services om de instantie correct te configureren vanuit het gezichtspunt van database-/hardwarecomponenten.
