---
title: Release 18.6
seo-title: Release 18.6
description: Release 18.6
seo-description: null
page-status-flag: never-activated
uuid: 72941f8f-0b84-4868-a768-8aa972459ef2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 79a6d3cf-2425-49b9-9b92-b56be26438bf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d046304657f04312d78176c49a650690b05e4c94

---


# Release 18.6{#release-18-6}

## Release 18.6.2 - build 8949{#release-18-6-3-build-8949}

22 augustus 2018

>[!CAUTION]
>
>Er is al op gewezen dat dit een bouwwerk is. Voer een [upgrade uit naar de nieuwste build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) of neem contact op met de [technische ondersteuning](https://support.neolane.net/).

**Wat is nieuw?**

<table> 
 <thead> 
  <tr> 
   <th> Functionaliteit<br /> </th> 
   <th> Beschrijving<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Query-streepjescodes<br /> </td> 
   <td> <p>Wanneer meerdere Campagnegebruikers verbinding maken met dezelfde externe FDA Teradata-account, kunt u nu een queryband (sleutel/waarde-paren) doorgeven die specifiek is voor elke gebruiker. Telkens wanneer een campagnegebruiker een query uitvoert in de Teradata-database, kan Adobe Campaign nu metagegevens verzenden die aan de gebruiker zijn gekoppeld. Deze gegevens, die bestaan uit een lijst met sleutels en waarden, kunnen vervolgens door Teradata-beheerders worden gebruikt voor auditdoeleinden of voor het beheren van toegangsrechten, bijvoorbeeld.</p><p>Raadpleeg de <a href="https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#Teradata_external_account">gedetailleerde documentatie</a>voor meer informatie.</p> </td>
  </tr> 
 </tbody> 
</table>

**Verbeteringen**

* Logbestanden voor e-mailarchivering zijn verbeterd, waardoor het eenvoudiger en duidelijker wordt om te controleren welke e-mails met succes zijn geleverd of niet zijn gearchiveerd via BCC-archivering. (NEO-10675)
* Probleem verholpen dat leidde tot de weergave van IP&#39;s van het taakverdelingsmechanisme in plaats van IP&#39;s van de klant in de weblogs voor het bijhouden van berichten. (NEO-11295)
* Probleem verholpen waarbij een willekeurig probleem werd opgelost waardoor de eigenschappen van een levering onjuist werden overschreven. (NEO-11015)
* Oplossing voor een syntaxisfout bij het sorteren van de resultaten van verrijkingsactiviteiten. (NEO-11394)
* Probleem verholpen bij het gebruik van berekende velden in een **[!UICONTROL Survey answers]** workflowactiviteit. (NEO-11382)
* Tomcat is bijgewerkt om misbruik van kwetsbaarheden te voorkomen. (NEO-11503)
* Oplossing voor een fout met LATIN1-codering bij gebruik van een FDA-verbinding met een PostSQL-database. (NEO-11299)
* Probleem verholpen dat optrad bij gebruik van de **[!UICONTROL Prepare the personalization data with a workflow]** leveringsoptie. (NEO-11047)
* Probleem verholpen waarbij het verzenden van SMS tijdens het gebruik van een uitgebreide connector werd verhinderd.
* Verbeterde import/export van pakketten (logboek en regio zijn toegevoegd aan de interface).
* Probleem verholpen waarbij nutteloze fouten in het postupgradelogboek werden weergegeven wanneer een **[!UICONTROL Survey answers]** workflowactiviteit niet volledig was geconfigureerd.

**Technische ontwikkelingen**

Query-streepjescodes

Een specifieke sleutel (PROXYUSER of PROXYROLE) wordt gebruikt om een gebruiker of rol van Tera-gegevens aan een gebruiker van de Campagne te associëren. Er is een nieuwe machtiging toegevoegd om deze proxygebruiker/rol te gebruiken. U moet de GRANT CONNECT via het toegangsrecht toevoegen aan de databaseaccount (de account die is gedefinieerd in de externe account van Teradata).

Er is een nieuw tabblad toegevoegd aan de externe accounts van Teradata. Het **[!UICONTROL Query banding]** tabblad bevat de volgende opties:

* **[!UICONTROL Active]**: Schakel dit selectievakje in om de functie te activeren.
* **[!UICONTROL Default]**: Voer een standaardquerybinding in die wordt gebruikt als een gebruiker geen querybinding heeft. Als er geen standaardvraagband wordt bepaald, zullen de gebruikers die geen bijbehorende vraagband hebben geen Tera-gegevens kunnen gebruiken.
* **[!UICONTROL Users]**: voor elke gebruiker, specificeer een vraagband. U kunt zoveel sleutel-/waardeparen toevoegen als u nodig hebt. Bijvoorbeeld: &quot;priority=1;workload=high;&quot;

Raadpleeg de volgende artikelen voor meer informatie over querybinding:

* [https://docs.teradata.com/reader/cY5~BoeEUFWjgN2kBnH3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## Release 18.6 - build 8947{#release-18-6-build-8947}

25 juni 2018

>[!CAUTION]
>
>Er is al op gewezen dat dit een bouwwerk is. Voer een [upgrade uit naar de nieuwste build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) of neem contact op met de [technische ondersteuning](https://support.neolane.net/).

**Wat is nieuw?**

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
   <td> Er is een aantal verbeteringen toegevoegd aan Campaign Classic. Hieronder vindt u verbeteringen en correcties.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ondersteuning voor Windows Server 2016<br /> </td> 
   <td> Adobe Campagne is nu compatibel met Windows Server 2016. Zie <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campagne Classic Compatibility Matrix</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

decryptString

De functie **decryptString** is afgekeurd. Raadpleeg het artikel [Vervangen en verwijderde functies](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html) .

Voor nieuwe klanten, wordt deze functie nu slechts gebruikt om crypt identiteitskaart van de ontvanger in het landen pagina&#39;s te decoderen. Om wachtwoorden te decrypteren die in een externe rekening worden opgeslagen, gebruik de nieuwe **decryptPassword** functie.

Voor bestaande klanten, wordt het gedrag van deze functie niet veranderd maar wij adviseren dat u **decryptPassword** in plaats van **decryptString** gebruikt. De **compatibiliteitsoptie XtkSecurity_Unsafe_DecryptString** wordt toegevoegd door de postupgrade en standaard geactiveerd, zodat u de functie kunt blijven gebruiken. Als u **decryptString** wilt deactiveren, deactiveer de optie.

decryptPassword

De functie **decryptPassword** is toegevoegd. Hiermee kunt u een wachtwoord decoderen dat is opgeslagen in een externe account. Raadpleeg de [JSAPI](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) -documentatie voor meer informatie.

Bestand-API&#39;s

Voor nieuwe installaties is maptoegang via bestand-API&#39;s beperkt tot de **var**-, **sftp** - en tijdelijke mappen van Adobe Campaign.

Voor bestaande klanten hebben bestand-API&#39;s geen toegang meer tot de map **conf** van Adobe Campaign. De compatibiliteitsoptie **XtkSecurity_Disable_JSFileSandboxing** wordt toegevoegd door de postupgrade en standaard geactiveerd, zodat u de andere mappen kunt blijven gebruiken. Als u de toegang tot de **var**-, **sftp** - en tijdelijke mappen van Adobe Campaign wilt beperken, deactiveert u de optie.

**Reparatie**

* Probleem verholpen dat gevolgen kon hebben voor de prestaties van SMS-berichten. (NEO-9812)
