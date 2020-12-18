---
solution: Campaign Classic
product: campaign
title: Netwerkconfiguratie
description: Richtlijnen voor systeemcommunicatie
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 2%

---


# Netwerkconfiguratie{#network-configuration}

## Communicatie tussen processen {#communication-between-processes}

Bepaalde processen van de toepassing moeten met anderen communiceren of toegang krijgen tot LAN en internet. Dit betekent dat sommige havens van TCP voor deze processen open moeten zijn.

Gebruik de ingesloten Apache Tomcat-poort als prioriteit (standaard is dit 8080) voor interne communicatie tussen de verschillende toepassingsservers van een Adobe Campaign-platform.

### Leveringsserver {#delivery-server}

Voor de leveringsserver (**nlserver mta**), moeten de volgende havens open zijn:

<table> 
 <tbody> 
  <tr> 
   <td> Poorten<br /> </td> 
   <td> Doel<br /> </td> 
   <td> Opmerkingen<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> SMTP-verkeer voor e-mailuitzending.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (domein)<br /> </td> 
   <td> DNS-servers<br /> </td> 
   <td> DNS-query's.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (standaardpoort)<br /> </td> 
   <td> SMS-gateway<br /> </td> 
   <td> Wordt gebruikt om SMS-verkeer naar de NetSize-sms-router [option] te verzenden.<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> Statistische server<br /> </td> 
   <td> Toegang tot de statistische server.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Binnenkomende mail {#inbound-mail}

Voor het binnenkomende proces van de postterugwinning (**nlserver inMail**), moeten de volgende havens open zijn:

<table> 
 <tbody> 
  <tr> 
   <td> Poorten<br /> </td> 
   <td> Doel<br /> </td> 
   <td> Opmerkingen<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp (pop3)<br /> </td> 
   <td> Interne mailserver<br /> </td> 
   <td> POP3-verkeer voor het ophalen van stuiterberichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Interne mailserver<br /> </td> 
   <td> SMTP verkeer om resterende stuitberichten te verzenden die niet automatisch door de vooraf bepaalde regels worden verwerkt.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Applicatieserver {#application-server}

Voor de toepassingsserver (**nlserver web**), moeten de volgende havens open zijn:

<table> 
 <tbody> 
  <tr> 
   <td> Poorten<br /> </td> 
   <td> Doel<br /> </td> 
   <td> Opmerkingen<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp (http)<br /> 443/tcp (https)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> HTTP- of HTTPS-verkeer (inclusief voor de aanbieding).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Wanneer meerdere toepassingsservers van een Adobe Campaign-platform met elkaar moeten communiceren, raden we u aan de poort van de Apache Tomcat-server te gebruiken (standaard: 8080) eerder dan dat van de haven van HTTP van de server van het Web die de redirection moduleintegratie werd uitgevoerd met. Dit betekent dat de poort open moet zijn tussen deze servers.

### Status van SMS-verzending {#sms-delivery-status}

Om de leveringen van SMS (**nlserver sms**) te volgen, moet de volgende haven open zijn:

<table> 
 <tbody> 
  <tr> 
   <td> Poorten<br /> </td> 
   <td> Doel<br /> </td> 
   <td> Opmerkingen<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (standaardpoort)<br /> </td> 
   <td> SMS-gateway<br /> </td> 
   <td> Zoekt de status van de leveringsrij die door de gateway van SMS NetSize [optie] wordt beheerd.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Rijke client {#rich-client}

Voor de rijke cliënt van Adobe Campaign (**nlclient**), moeten de volgende havens open zijn:

<table> 
 <tbody> 
  <tr> 
   <td> Poorten<br /> </td> 
   <td> Doel<br /> </td> 
   <td> Opmerkingen<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p>443/tcp (https)</p><br /> </td> 
   <td> Applicatieserver<br /> </td> 
   <td> ZEEP-verkeer (HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Databasetoegang {#database-access}

Alle componenten die de database gebruiken, moeten er verbinding mee kunnen maken. Dit is het geval voor de meeste componenten, met uitzondering van de redirection server, die alleen kan werken, en de dunne cliënt van Win32, die HTTP (of HTTPS) slechts gebruikt om met de toepassingsserver te communiceren.

De standaardhavens zijn het volgende:

<table> 
 <tbody> 
  <tr> 
   <td> Databasetype<br /> </td> 
   <td> Poort (standaard)<br /> </td> 
   <td> Doel<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/tcp<br /> </td> 
   <td> Databaseserver<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> 5432/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Microsoft SQL Server</strong><br /> </td> 
   <td> 1433/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> 50000/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Externe toegang {#external-access}

Bovendien moeten bepaalde componenten toegankelijk zijn via het openbare internet, zodat direct vanuit Adobe Campaign uitgevoerde e-mailcampagnes kunnen worden bekeken. Dit betekent dat sommige havens voor componenten open moeten zijn.

### Omleidingsserver {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> Luisterpoort<br /> </td> 
   <td> Locatie<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Overal. Elke klik op een bijgehouden koppeling genereert een HTTP-aanvraag op de server.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Externe webserver {#external-web-server}

Deze servergastherenWeb vormen, spiegelpagina&#39;s, enz. De volgende poorten moeten geopend zijn:

<table> 
 <tbody> 
  <tr> 
   <td> Luisterpoort<br /> </td> 
   <td> Locatie<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Overal. Dit is nodig wanneer webformulieren rechtstreeks vanaf het Adobe Campaign-platform worden beheerd of wanneer spiegel-pagina's worden gebruikt.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Interne toepassingsserver (Web) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> Luisterpoort<br /> </td> 
   <td> Locatie<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Alle computers die de thin client of rich client uitvoeren.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integratie met Adobe Experience Manager {#integration-with-adobe-experience-manager}

De integratie tussen Adobe Campaign en Adobe Experience Manager vereist het openen van verscheidene havens als de installatie &quot;op-gebouw&quot;is. Raadpleeg de [gedetailleerde documentatie](../../integrations/using/about-adobe-experience-manager.md) voor meer informatie over het configureren van deze integratie.

<table> 
 <tbody> 
  <tr> 
   <td> Luisterpoort<br /> </td> 
   <td> Beschrijving<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> Verbinding AEM met Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Adobe Campaign-verbinding met AEM 'authoring'- en 'publishing'-instanties. De te openen havens kunnen van de standaardhavens, afhankelijk van uw AEM configuratie verschillend zijn.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Bandbreedte {#bandwidth}

Een andere zeer belangrijke parameter van de netwerkconfiguratie om rekening mee te houden. Het is bijna altijd uitgaand en veel in vraag tijdens e-mailuitzendingen. Hieronder volgen enkele voorbeelden van configuraties op basis van onze ervaring:

* 1 MB/s voor 10.000 e-mails per uur (gemiddelde grootte van 30 Kb)
* 8 tot 10 Mb/s voor 100.000 e-mails per uur (gemiddelde grootte van 30 Kb)

Als u beperkingen in termen van bandbreedte hebt, is het mogelijk om campagnes te plannen om tijdens de nacht te lopen wanneer de vraag lager is.
