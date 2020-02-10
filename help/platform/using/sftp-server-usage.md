---
title: SFTP-servergebruik
seo-title: SFTP-servergebruik
description: SFTP-servergebruik
seo-description: null
page-status-flag: never-activated
uuid: 5281058d-91bd-4f98-835d-1d46dc7b8b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: f449ccd5-3965-4ab8-b5a9-993f3260aba9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1e8492d8e91d679ac13da875974e27d0f7791dc3

---


# SFTP-servergebruik{#sftp-server-usage}

## Aanbevolen werkwijzen SFTP-server {#sftp-server-best-practices}

Als u bestanden en gegevens beheert voor ETL-doeleinden, worden deze bestanden opgeslagen op een gehoste SFTP-server die door Adobe wordt geleverd. Deze SFTP is ontworpen als een tijdelijke opslagruimte waarop u het bewaren en het schrappen van dossiers kunt controleren.

Als deze ruimte niet correct wordt gebruikt of gecontroleerd, kan deze snel de fysieke ruimte vullen die op de server beschikbaar is en leiden tot het afbreken van bestanden bij volgende uploads. Zodra de ruimte verzadigd is, kunnen bestanden die het oudst zijn in de SFTP-opslag worden geactiveerd en verwijderd door automatische verwijdering.

Adobe raadt u aan de onderstaande aanbevolen procedures te volgen om dergelijke problemen te voorkomen.

>[!NOTE]
>
>Als uw instantie op AWS wordt gehost, kunt u de opslagruimte van uw SFTP-server controleren met het Classic [Configuratiescherm](https://docs.adobe.com/content/help/en/control-panel/using/sftp-management/sftp-storage-management.html).
>
>Volg de stappen in [deze sectie](https://docs.adobe.com/content/help/en/control-panel/using/faq.html#ims-org-id) om te controleren of uw exemplaar wordt gehost op AWS.

* De mogelijkheden voor servergrootte variëren afhankelijk van uw licentie. In elk geval moet u de minimale gegevens mogelijk houden en de gegevens slechts zo lang bewaren als nodig is (15 dagen is de maximale termijn).
* Gebruik op sleutels gebaseerde authentificatie eerder dan wachtwoordauthentificatie, om wachtwoordvervalsing te vermijden (de wachtwoorden hebben een geldigheidsperiode van 90 dagen). Bovendien kunt u met op sleutels gebaseerde verificatie meerdere sleutels genereren, bijvoorbeeld wanneer u meerdere entiteiten beheert. Integendeel, voor wachtwoordverificatie moet u het wachtwoord delen met alle entiteiten die u beheert.

   De gesteunde zeer belangrijke indeling is SSH-2 RSA 2048. Toetsen kunnen worden gegenereerd met programma&#39;s zoals PyTTY (Windows) of ssh-keygen (Unix). U moet de openbare sleutel aan het ondersteuningsteam van Adobe verstrekken via een [ondersteuningsticket](https://support.neolane.net) om deze te uploaden naar de campagneserver.

* Gebruik workflows om de gegevens correct te verwijderen (de bewaring van werkstromen die gegevens verbruiken, beheren).
* Gebruik batchverwerking in SFTP-uploads en in workflows.
* Fouten/uitzonderingen afhandelen.
* Soms, login aan SFTP om direct te controleren wat daar ligt.
* Houd er rekening mee dat SFTP-schijfbeheer primair uw verantwoordelijkheid is.
* Standaard staan alle mappen die u maakt alleen in de modus Lezen/Schrijven voor uw id. Wanneer het creëren van omslagen die door Campagne moeten worden betreden, zorg ervoor om hen te vormen met lees/schrijf rechten voor de volledige groep. Anders kunnen workflows mogelijk geen bestanden maken of verwijderen omdat deze om beveiligingsredenen onder een andere id binnen dezelfde groep worden uitgevoerd.
* Openbare IPs waarvan u probeert om de verbinding in werking te stellen SFTP moet op de instantie van de Campagne worden gewhitelisteerd. Whitelisting van IP adressen kan via een [steunkaartje](https://support.neolane.net)worden gevraagd.

>[!CAUTION]
>
>Als u uw eigen SFTP-server gebruikt, moet u de bovenstaande aanbevelingen zoveel mogelijk opvolgen.

## Problemen met SFTP-server {#sftp-server-troubleshooting}

In de onderstaande sectie vindt u de informatie die u wilt controleren en die u via een [ondersteuningsticket](https://support.neolane.net) aan het ondersteuningsteam van Adobe wilt doorgeven bij het zoeken naar verbindingsproblemen met door Adobe gehoste SFTP-servers.

1. Controleer of de instantie actief is. Om dit te doen, open uw browser, dan doe een **[!UICONTROL GET]** vraag op het instantie **[!UICONTROL /r/test]** eindpunt:

   ```
   https://instanceUrl/r/test
   ```

   Als de instantie actief is, krijgt u dit type reactie:

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instanceName'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instanceName'/>
   ```

   In elk geval, verstrek de bevelreactie in het steunkaartje.

1. Controleer of uitgaande poort 22 is geopend op de site van waaruit u de SFTP-verbinding probeert te maken. Hiervoor gebruikt u de volgende opdracht:

   ```
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   >[!NOTE]
   >
   >Met het gereedschap Netcat kunt u eenvoudig netwerkverbindingen beheren op verschillende besturingssystemen (zie [https://eternallybored.org/misc/netcat/](https://eternallybored.org/misc/netcat/)).

   Als de poort niet is geopend, moet u uitgaande verbindingen aan uw zijde openen en het opnieuw proberen. Als u nog steeds verbindingsproblemen ondervindt, deelt u de uitvoer van de opdracht met het ondersteuningsteam van Adobe.

1. Controleer of de openbare IP van waaruit u de verbinding van SFTP probeert in werking te stellen die u aan de Steun van Adobe voor het whitelisting verstrekte.
1. Als u een op een wachtwoord gebaseerde verificatie gebruikt, is uw wachtwoord mogelijk verlopen (wachtwoorden hebben een geldigheidsduur van 90 dagen). Daarom adviseren wij sterk gebruikend een zeer belangrijke gebaseerde authentificatie (zie de beste praktijken [van de server](#sftp-server-best-practices)SFTP).
1. Als u een op sleutels gebaseerde authentificatie gebruikt, controleer dat de sleutel u gebruikt het zelfde is dat u aan het team van de Steun van Adobe voor de instantieconfiguratie verstrekte.
1. Als u FileZilla of een gelijkwaardig hulpmiddel van FTP gebruikt, verstrek de details van verbindingslogboeken in het steunkaartje.

