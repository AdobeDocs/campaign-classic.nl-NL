---
product: campaign
title: Opmerkingen bij de release Campagne 18.6
description: Opmerkingen bij de release voor campagne 18.6
audience: rn
content-type: reference
topic-tags: latest-release-notes
feature: Overview
role: User
level: Beginner
exl-id: a849ce10-0972-4c42-b10e-67a81c79bc65
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 7%

---

# Release 18.6{#release-18-6}

![](../../assets/v7-only.svg)

## Release 18.6.2 - Build 8949{#release-18-6-3-build-8949}

22 augustus 2018

>[!CAUTION]
>
>Er is al op gewezen dat dit een bouwwerk is. [upgrade naar de nieuwste build](../../production/using/build-upgrade.md) of neem contact op met [Adobe Customer Care](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Nieuwe functies**

<table> 
 <thead> 
  <tr> 
   <th> Functionaliteit<br /> </th> 
   <th> Beschrijving<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Query-streepvorming<br /> </td> 
   <td> <p>Wanneer de veelvoudige gebruikers van de Campagne met de zelfde FDA Teradata externe rekening verbinden, kunt u een vraagband (sleutel/waardeparen) nu overgaan specifiek voor elke gebruiker. Elke keer dat een campagnegebruiker een query uitvoert op de Teradata-database, kan Adobe Campaign nu metagegevens verzenden die aan de gebruiker zijn gekoppeld. Deze gegevens, die uit een lijst van sleutels en waarden bestaan kunnen dan door de beheerders van Teradata voor controledoeleinden of om toegangsrechten, bijvoorbeeld te beheren worden gebruikt.</p><p>Raadpleeg de <a href="../../installation/using/external-accounts.md">gedetailleerde documentatie</a> voor meer informatie.</p> </td>
  </tr> 
 </tbody> 
</table>

**Verbeteringen**

* Logbestanden voor e-mailarchivering zijn verbeterd, waardoor het eenvoudiger en duidelijker wordt om te controleren welke e-mails met succes zijn geleverd of niet zijn gearchiveerd via BCC-archivering. (NEO-10675)
* Probleem verholpen dat leidde tot de weergave van IP&#39;s van het taakverdelingsmechanisme in plaats van IP&#39;s van de klant in de weblogs voor het bijhouden van berichten. (NEO-11295)
* Probleem verholpen waarbij een willekeurig probleem werd opgelost waardoor de eigenschappen van een levering onjuist werden overschreven. (NEO-11015)
* Oplossing voor een syntaxisfout bij het sorteren van de resultaten van verrijkingsactiviteiten. (NEO-11394)
* Probleem verholpen bij het gebruik van berekende velden in een **[!UICONTROL Survey answers]**-workflowactiviteit. (NEO-11382)
* Tomcat is bijgewerkt om misbruik van kwetsbaarheden te voorkomen. (NEO-11503)
* Oplossing voor een fout met LATIN1-codering bij gebruik van een FDA-verbinding met een PostSQL-database. (NEO-11299)
* Probleem verholpen die optrad bij gebruik van de leveringsoptie **[!UICONTROL Prepare the personalization data with a workflow]**. (NEO-11047)
* Probleem verholpen waarbij het verzenden van SMS tijdens het gebruik van een uitgebreide connector werd verhinderd.
* Verbeterde import/export van pakketten (logboek en regio zijn toegevoegd aan de interface).
* Probleem verholpen waarbij nutteloze fouten in het postupgradelogboek werden weergegeven wanneer een **[!UICONTROL Survey answers]**-workflowactiviteit niet volledig was geconfigureerd.

**Technische ontwikkelingen**

Query-streepjescodes

Een specifieke sleutel (PROXYUSER of PROXYROLE) wordt gebruikt om een gebruiker of een rol van de Teradata aan een gebruiker van de Campagne te associëren. Er is een nieuwe machtiging toegevoegd om deze proxygebruiker/rol te gebruiken. U moet de GRANT CONNECT door toegangsrecht tot de gegevensbestandrekening (die in de Teradata externe rekening wordt bepaald) toevoegen.

Er is een nieuw tabblad toegevoegd aan de externe accounts van Teradata. Het tabblad **[!UICONTROL Query banding]** bevat de volgende opties:

* **[!UICONTROL Active]**: Schakel dit selectievakje in om de functie te activeren.
* **[!UICONTROL Default]**: Voer een standaardquerybinding in die wordt gebruikt als een gebruiker geen querybinding heeft. Als er geen standaard bepaalde vraagband is, zullen de gebruikers die geen bijbehorende vraagband hebben geen Teradata kunnen gebruiken.
* **[!UICONTROL Users]**: voor elke gebruiker, specificeer een vraagband. U kunt zoveel sleutel-/waardeparen toevoegen als u nodig hebt. Bijvoorbeeld: &quot;priority=1;workload=high;&quot;

Raadpleeg de volgende artikelen voor meer informatie over querybinding:

* [https://docs.teradata.com/reader/cY5~BoeEUFWjgN2kBnH3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## Release 18.6 - Build 8947{#release-18-6-build-8947}

25 juni 2018

>[!CAUTION]
>
>Er is al op gewezen dat dit een bouwwerk is. [upgrade naar de nieuwste build](../../production/using/build-upgrade.md) of neem contact op met [technische ondersteuning](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Nieuwe functies**

<table> 
 <thead> 
  <tr> 
   <th> Functionaliteit<br /> </th> 
   <th> Beschrijving<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Beveiligingsverbeteringen<br /> </td> 
   <td> Aan Campaign Classic is een aantal verbeteringen op het gebied van beveiliging toegevoegd. De verbeteringen en de moeilijke situaties worden hieronder vermeld.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ondersteuning voor Windows Server 2016<br /> </td> 
   <td> Adobe Campaign is nu compatibel met Windows Server 2016. Zie <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic Compatibility matrix</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

decryptString

De functie **decryptString** is afgekeurd. Verwijs naar [Vervangen en Verwijderde Eigenschappen](deprecated-features.md) artikel.

Voor nieuwe klanten, wordt deze functie nu slechts gebruikt om crypt identiteitskaart van de ontvanger in het landen pagina&#39;s te decoderen. Om wachtwoorden te decrypteren die in een externe rekening worden opgeslagen, gebruik de nieuwe **decryptPassword** functie.

Voor bestaande klanten, wordt het gedrag van deze functie niet veranderd maar wij adviseren dat u **decryptPassword** in plaats van **decryptString** gebruikt. De compatibiliteitsoptie **XtkSecurity_Unsafe_DecryptString** wordt toegevoegd door de postupgrade en standaard geactiveerd, zodat u de functie kunt blijven gebruiken. Als u **decryptString** wilt deactiveren, deactiveer de optie.

decryptPassword

De functie **decryptPassword** is toegevoegd. Hiermee kunt u een wachtwoord decoderen dat is opgeslagen in een externe account. Raadpleeg de [JSAPI](https://helpx.adobe.com/nl/campaign/kb/compatibility-matrix.html) documentatie voor meer informatie.

Bestand-API&#39;s

Voor nieuwe installaties, is de omslagtoegang via dossier APIs beperkt tot **var**, **sftp** en tijdelijke omslagen van Adobe Campaign.

Voor bestaande klanten hebben bestands-API&#39;s geen toegang meer tot de map **conf** van Adobe Campaign. De compatibiliteitsoptie **XtkSecurity_Disable_JSFileSandboxing** wordt toegevoegd door de postupgrade en standaard geactiveerd, zodat u de andere mappen kunt blijven gebruiken. Als u de toegang tot **var**, **sftp** en tijdelijke omslagen van Adobe Campaign wilt beperken, deactiveer de optie.

**Reparatie**

* Probleem verholpen dat gevolgen kon hebben voor de prestaties van SMS-berichten. (NEO-9812)
