---
product: campaign
title: Power Booster en Power Cluster
description: Power Booster en Power Cluster
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 5%

---

# Power Booster en Power Cluster{#power-booster-and-power-cluster}



## Overzicht {#overview}

Adobe Campaign biedt u twee sets vooraf verpakte architecturale opties voor het dimensioneren van uw implementatie:

* **de Booster van de Macht**

  Deze optie biedt ondersteuning voor één extra uitvoeringsinstantie die is losgekoppeld van de primaire Adobe Campaign-toepassingsinstantie. Speciale uitvoeringsinstanties kunnen op afstand of door een derde worden gehost. Wanneer geïmplementeerd, worden e-mailuitvoering, bijhouden, spiegel- en stuiterberichten onafhankelijk van de centrale toepassingsfuncties afgehandeld.

* **Cluster van de Macht**

  Deze optie biedt ondersteuning voor 2 tot N geclusterde uitvoeringsinstanties die zijn losgekoppeld van de primaire Adobe Campaign-toepassingsinstantie met betrekking tot een bepaalde toepassing. Clusters kunnen op afstand, in gedistribueerde implementaties en door derden worden gehost. Naast de voordelen van procesisolatie maakt de Adobe Campaign Power Cluster-optie redundantie mogelijk en schaalt deze strategieën uit met behulp van gewone hardware voor een vereenvoudigde ontwikkeling van SLA of prestaties.

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
   <td> <strong> Standaard architectuur </strong><br /> </td> 
   <td> <strong> de Booster van de Macht </strong><br /> </td> 
   <td> <strong> Cluster van de Macht </strong><br /> </td> 
  </tr> 
  <tr> 
   <td> E-mailcampagnes en uitgaande interacties <br /> </td> 
   <td> Tot ongeveer 30 miljoen e-mails per maand <br /> </td> 
   <td> 30 tot 100 miljoen e-mails per maand <br /> </td> 
   <td> Meer dan 100 miljoen e-mails per maand <br /> </td> 
  </tr> 
  <tr> 
   <td> Transactieberichten <br /> </td> 
   <td> 50.000 per uur per uitvoeringsserver <br /> </td> 
   <td> 50.000 per uur per uitvoeringsserver <br /> </td> 
   <td> 50.000 per uur per uitvoeringsserver <br /> </td> 
  </tr> 
  <tr> 
   <td> Beschikbaarheid <br /> </td> 
   <td> Dat van het primaire gegevensbestand <br /> </td> 
   <td> 24/7 behalve onderhoudsvensters en downtimes voor de uitvoeringsinstantie <br /> </td> 
   <td> 24-7-365 service mogelijk <br /> </td> 
  </tr> 
  <tr> 
   <td> Beveiliging <br /> </td> 
   <td> De markt van gegevens is potentieel toegankelijk van openbaar Internet <br /> </td> 
   <td> De markt van gegevens is geïsoleerd van frontale, Internet-Onder ogen ziet componenten <br /> </td> 
   <td> De markt van gegevens is geïsoleerd van frontale, Internet-Onder ogen ziet componenten <br /> </td> 
  </tr> 
  <tr> 
   <td> Implementatiesjabloon <br /> </td> 
   <td> Alles op één plaats (kan op gebouw of in de wolk zijn) <br /> </td> 
   <td> Marketing op gebouw met uitvoering in de wolk mogelijk <br /> </td> 
   <td> Marketing op locatie met uitvoering in de cloud; uitvoering in verschillende geopos mogelijk <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Aanbevelingen {#recommendations}

* Een uitvoeringsinstantie moet aan de dienst worden gewijd. U kunt geen pakket installeren voor een service waarop u zich niet hebt geabonneerd. Bijvoorbeeld, als u aan de **optie van de Booster van de Macht** voor de **dienst van het Centrum van het Bericht** intekent, kunt u het **[!UICONTROL Execution of transactional messages]** pakket op de specifieke uitvoeringsinstantie slechts installeren. Controleer hiervoor uw licentieovereenkomst.
* Aangezien specifieke instanties (of clusters) Adobe Campaign-instanties zijn, zijn de aanbevelingen hetzelfde als voor een hoofdinstantie. Voor meer op dit, verwijs naar [ dit document ](../../production/using/foreword.md).
* Neem contact op met Adobe Campaign Professional Services om de instantie correct te configureren vanuit het gezichtspunt van database-/hardwarecomponenten.
