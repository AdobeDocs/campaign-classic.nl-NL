---
product: campaign
title: SFTP-servergebruik
description: Meer informatie over best practices en probleemoplossing voor SFTP-servers
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 14%

---

# Best practices en probleemoplossing voor SFTP-servers {#sftp-server-usage}



## Algemene aanbevelingen voor SFTP-server {#global-recommendations}

Als u bestanden en data beheert voor ETL-doeleinden, worden deze bestanden opgeslagen op een gehoste SFTP-server die door Adobe wordt geleverd. Volg de onderstaande aanbevelingen bij het gebruik van SFTP-servers.

* Gebruik op sleutels gebaseerde authentificatie eerder dan wachtwoordauthentificatie, om wachtwoordvervalsing te vermijden (de wachtwoorden hebben een geldigheidsperiode van 90 dagen). Bovendien kunt u met op sleutels gebaseerde verificatie meerdere sleutels genereren, bijvoorbeeld wanneer u meerdere entiteiten beheert. Integendeel, voor wachtwoordverificatie moet u het wachtwoord delen met alle entiteiten die u beheert.

   De gesteunde zeer belangrijke indeling is SSH-2 RSA 2048. De sleutels kunnen met hulpmiddelen zoals PyTTY (Vensters), of ssh-keygen (Unix) worden geproduceerd.U zult de openbare sleutel aan het team van de Steun van Adobe via moeten verstrekken [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om het op de server van de Campagne te uploaden.

* Gebruik batchverwerking in SFTP-uploads en in workflows.

* Verwerk fouten/uitzonderingen.

* Standaard staan alle mappen die u maakt alleen in de modus Lezen/Schrijven voor uw id. Wanneer het creëren van omslagen die door Campagne moeten worden betreden, zorg ervoor om hen te vormen met lees/schrijf rechten voor de volledige groep. Anders kunnen workflows mogelijk geen bestanden maken of verwijderen omdat deze om beveiligingsredenen onder een andere id binnen dezelfde groep worden uitgevoerd.

* Openbare IPs waarvan u probeert om de verbinding in werking te stellen SFTP moet aan de lijst van gewenste personen op de instantie van de Campagne worden toegevoegd. Het toevoegen van IP adressen aan de lijst van gewenste personen kan worden gevraagd via [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Best practices voor databasegebruik {#sftp-server-best-practices}

SFTP-servers zijn ontworpen als tijdelijke opslagruimten waarop u het bewaren en verwijderen van bestanden kunt beheren.

Als deze spaties niet correct worden gebruikt of gecontroleerd, kunnen ze snel de fysieke ruimte op de server vullen en leiden tot het afbreken van bestanden bij volgende uploads. Zodra de ruimte verzadigd is, kunnen bestanden die het oudst zijn in de SFTP-opslag worden geactiveerd en verwijderd door automatische verwijdering.

Om dergelijke problemen te voorkomen, raadt Adobe aan de onderstaande beste praktijken te volgen.

>[!NOTE]
>
>Als uw instantie wordt gehost op AWS, kunt u de opslagruimte van uw SFTP-server controleren met de Campaign Classic [Deelvenster Beheer](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html). Controleer of uw versie wordt gehost op AWS door de volgende stappen te volgen op [deze pagina](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).
>
>Het configuratiescherm is toegankelijk voor alle gebruikers met beheerdersrechten. De stappen om toegang met beheerdersrechten aan een gebruiker te verlenen worden gedetailleerd beschreven op [deze pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=nl#discover-control-panel).
>
>Merk op dat uw instantie met moet worden bevorderd [nieuwste GA-build](../../rn/using/rn-overview.md). Leer hoe u uw versie kunt controleren in [dit gedeelte](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

* De mogelijkheden voor servergrootte variëren afhankelijk van uw licentie. In elk geval moet u de minimale gegevens mogelijk houden en de gegevens slechts zo lang bewaren als nodig is (15 dagen is de maximale termijn).

* Gebruik workflows om de data op de juiste manier te verwijderen (beheer de retentie van workflows die de data verbruiken).

* Meld u af en toe aan bij de SFTP om de content rechtstreeks te controleren.

* Vergeet niet dat SFTP-schijfbeheer in de eerste plaats uw verantwoordelijkheid is.

## Extern SFTP-servergebruik {#external-SFTP-server}

Als u uw eigen SFTP-server gebruikt, moet u de bovenstaande aanbevelingen zoveel mogelijk opvolgen.

Wanneer u bovendien in Campaign Classic een pad naar een externe SFTP-server opgeeft, verschilt de padsyntaxis per besturingssysteem van de SFTP-server:

* Als uw SFTP-server is ingeschakeld **Windows** altijd een relatief pad gebruiken.
* Als uw STP-server is ingeschakeld **Linux** Gebruik altijd een pad dat relatief is ten opzichte van de startpagina (te beginnen met &#39;~/&#39;) of een absoluut pad (te beginnen met &#39;/&#39;).

## Verbindingsproblemen met door Adobe gehoste SFTP-server {#sftp-server-troubleshooting}

In de onderstaande sectie wordt de informatie weergegeven die u via [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) wanneer het ontmoeten van verbindingskwesties met Adobe ontvangen servers SFTP.

1. Controleer of de instantie actief is. Om dit te doen, open uw browser, dan maak **[!UICONTROL GET]** aanroepen van de instantie **[!UICONTROL /r/test]** eindpunt:

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

   Als de poort niet is geopend, moet u uitgaande verbindingen aan uw zijde openen en het opnieuw proberen. Als u nog steeds verbindingsproblemen ondervindt, deelt u de uitvoer van de opdracht met [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team.

1. Controleer dat openbare IP waarvan u probeert om de verbinding in werking te stellen SFTP is die u aan de Steun van de Adobe voor de lijst van gewenste personen verstrekte.
1. Als u een op een wachtwoord gebaseerde verificatie gebruikt, is uw wachtwoord mogelijk verlopen (wachtwoorden hebben een geldigheidsduur van 90 dagen). Daarom adviseren wij sterk gebruikend een zeer belangrijke gebaseerde authentificatie (zie [Aanbevolen werkwijzen SFTP-server](#sftp-server-best-practices)).
1. Als u een op sleutels gebaseerde authentificatie gebruikt, controleer dat de sleutel u gebruikt het zelfde is dat u verstrekte aan [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team voor de instantieconfiguratie.
1. Als u FileZilla of een gelijkwaardig hulpmiddel van FTP gebruikt, verstrek de details van verbindingslogboeken in het steunkaartje.

## Fout &quot;Kan hostnaam niet oplossen&quot;

Deze sectie bevat informatie over de controles en de handelingen die moeten worden uitgevoerd wanneer de fout &quot;Kan hostnaam niet oplossen&quot; wordt opgehaald nadat verbinding is gemaakt met FTP-server vanuit Campaign Classic.

Het werkschemadagboek toont de volgende logboeken:

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

Deze fout treedt op wanneer u probeert verbinding te maken met de FTP-server vanuit een workflow en de bestanden downloadt van de server, terwijl u nog steeds verbinding kunt maken via FTP met FileZilla of WinSCP.

Deze fout geeft aan dat de domeinnaam van de FTP-server niet correct kan worden omgezet. Ga als volgt te werk om problemen op te lossen:

1. Problemen oplossen **DNS-serverconfiguratie**:

   1. Controleer of de servernaam is toegevoegd aan de lokale DNS-server.
   1. Als ja, stel het volgende bevel op de server van Adobe Campaign in werking om het IP adres te krijgen:

      `nslookup <server domain name>`

      Dit bevestigt dat de FTP-server werkt en bereikbaar is vanaf de Adobe Campaign-toepassingsserver.

1. Problemen oplossen **sessielogbestanden**:

   1. Dubbelklik in de workflow op de knop [Bestandsoverdracht](../../workflow/using/file-transfer.md) activiteit.
   1. Ga naar **[!UICONTROL File Transfer]** tab, en klik vervolgens op **[!UICONTROL Advanced Parameters]**.
   1. Schakel de optie **[!UICONTROL Display the session logs]** in.

      ![](assets/sftp-error-display-logs.png)

   1. Ga naar de workflowcontrole en controleer of in de logboeken de fout &#39;Kan hostnaam niet oplossen&#39; wordt weergegeven.

1. Als de server SFTP door Adobe wordt ontvangen, controleer of IP aan de lijst van gewenste personen wordt toegevoegd door de Zorg van de Klant te contacteren.

   Anders valideren:

   * Het wachtwoord bevat geen &#39;@&#39;. De verbinding is mislukt als het wachtwoord &#39;@&#39; bevat.
   * Er zijn geen firewallproblemen die de communicatie tussen Adobe Campaign-toepassingsserver en SFTP-server kunnen belemmeren.
   * De tracert en Telnet van de looppas bevelen van de campagneserver aan sftp om te zien of zijn er om het even welke verbindingskwesties.
   * Er zijn geen problemen met het communicatieprotocol.
   * Poort is open.
