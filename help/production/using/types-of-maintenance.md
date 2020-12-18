---
solution: Campaign Classic
product: campaign
title: Typen onderhoud
description: Typen onderhoud
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---


# Typen onderhoud{#types-of-maintenance}

## Onderhoud van toepassingen {#application-maintenance}

Adobe Campaign biedt een ingebouwde workflow waarmee u bepaalde onderhoudstaken voor databases kunt plannen: de **workflow voor het opschonen van databases**. Deze workflow voert de volgende taken uit:

* verwijdering van verlopen records;
* verwijdering van zwevende records en herinitialisatie van status voor verlopen objecten;
* het bijwerken van de databasestatistieken.

>[!IMPORTANT]
>
>Houd er rekening mee dat de opschoningstaak vooral betrekking heeft op onderhoud op toepassingsniveau, niet op onderhoud op RDBMS-niveau (met uitzondering van de update van statistische gegevens). Onderhoudsbewerkingen zijn echter vereist voor de database. Zelfs als de workflow voor het opschonen van de database met succes wordt uitgevoerd, betekent dit niet dat de database optimaal is ingesteld.

## Technisch onderhoud {#technical-maintenance}

De workflow voor het opschonen van databases bevat geen enkele tool voor databaseonderhoud: het is aan u om onderhoud te organiseren. Hiervoor kunt u:

* met uw beheerder van het Gegevensbestand aan opstellings gegevensbestandonderhoud met derdehulpmiddelen,
* gebruik de Adobe Campaign-workflowengine om deze onderhoudsactiviteiten te plannen en te volgen.

Deze onderhoudsprocedures moeten regelmatig worden uitgevoerd en moeten het volgende omvatten:

* regelmatig bijgewerkte tabellen opnieuw indexeren;
* de tabellen compact/opnieuw samenstellen om fragmentatie te voorkomen.

### Onderhoudsschema {#maintenance-schedule}

U moet de juiste sleuven vinden voor het uitvoeren van deze onderhoudsactiviteiten. Ze kunnen grote invloed hebben op de databaseprestaties terwijl de toepassing wordt uitgevoerd of zelfs geblokkeerd (door vergrendeling).

Deze taken worden doorgaans één keer per week uitgevoerd tijdens een periode van lage activiteit die niet botst met back-ups, het opnieuw laden van gegevens of de berekening van aggregaten. Sommige systemen die zeer gevraagd zijn, vereisen frequenter onderhoud.

Meer diepgaand onderhoud, zoals volledige tabelrebuilds, kan één keer per maand worden uitgevoerd, bij voorkeur met toepassingen die volledig zijn gestopt omdat het systeem sowieso onbruikbaar is.

### Een tabel opnieuw samenstellen {#rebuilding-a-table}

Er zijn verschillende strategieën beschikbaar:

<table> 
 <thead> 
  <tr> 
   <th> Bewerkingen </th> 
   <th> Beschrijving </th> 
   <th> Voordelen </th> 
   <th> Nadelen </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Online defragmentation<br /> </td> 
   <td> De meeste gegevensbestandmotoren verstrekken defragmentatiemethodes.<br /> </td> 
   <td> Gebruik eenvoudig de database defragmentation methode. Deze methodes behandelen typisch integriteitskwesties door de gegevens tijdens defragmentation te sluiten.<br /> </td> 
   <td> Afhankelijk van het gegevensbestand, kunnen deze defragmentation methodes als optie RDBMS (Oracle) worden verstrekt en zijn niet altijd de meest efficiënte manier om grotere lijsten te behandelen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Reliëf en herstel<br /> </td> 
   <td> Zet de lijst aan een dossier neer, schrap de lijst in het gegevensbestand en herstel van de stortplaats.<br /> </td> 
   <td> Dit is de eenvoudigste manier om een tabel te defragmenteren. Ook de enige oplossing wanneer het gegevensbestand bijna volledig is.<br /> </td> 
   <td> Aangezien de tabel wordt verwijderd en opnieuw gemaakt, kan de toepassing niet online worden gelaten, zelfs niet in de modus Alleen-lezen (de tabel is niet beschikbaar tijdens de terugzetfase).<br /> </td> 
  </tr> 
  <tr> 
   <td> Dupliceren, naam wijzigen en neerzetten<br /> </td> 
   <td> Dit leidt tot een exemplaar van een lijst en zijn indexen, dan laat vallen bestaande en noemt het exemplaar anders om zijn plaats te nemen.<br /> </td> 
   <td> Deze methode is sneller dan de eerste benadering aangezien het minder IOs (geen exemplaar als dossier en gelezen van dit dossier) produceert.<br /> </td> 
   <td> Vereist tweemaal de hoeveelheid ruimte.<br /> Alle actieve processen die tijdens het proces naar de tabel worden geschreven, moeten worden gestopt. Dit heeft echter geen invloed op het leesproces, aangezien de tabel op het laatste moment na de heropbouw wordt omgewisseld. <br /> </td> 
  </tr> 
 </tbody> 
</table>

