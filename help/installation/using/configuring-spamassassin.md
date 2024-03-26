---
product: campaign
title: SpamAssassin configureren
description: SpamAssassin configureren
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 1%

---

# SpamAssassin configureren{#configuring-spamassassin}



>[!NOTE]
>
>Sommige configuraties kunnen slechts door Adobe voor plaatsingen worden uitgevoerd die door Adobe worden ontvangen. Bijvoorbeeld, om tot de server en de dossiers van de instantieconfiguratie toegang te hebben. Voor meer informatie over de verschillende implementaties raadpleegt u de [Hostmodellen](../../installation/using/hosting-models.md) van [deze pagina](../../installation/using/capability-matrix.md).

## Overzicht {#overview}

SpamAssassin is software die is ontworpen om ongewenste e-mails te filteren. In combinatie met deze software kan Adobe Campaign een score toewijzen aan e-mailberichten en bepalen of een bericht waarschijnlijk ongewenst wordt geacht voordat de levering wordt gestart. Hiertoe moet SpamAssassin op de toepassingsserver(s) van Adobe Campaign zijn geïnstalleerd en geconfigureerd en is een bepaald aantal aanvullende Perl-modules vereist om te kunnen werken.

De plaatsing en de integratie van SpamAssassin zoals die in dit hoofdstuk wordt beschreven zijn gebaseerd op standaardsoftwareinstallatie, zoals filtreren en het scoren regels, die die door SpamAssassin zonder enige veranderingen of optimalisaties worden verstrekt. De attributie van de score en de berichtkwalificatie zijn uitsluitend gebaseerd op de configuratie van opties SpamAssassin en op het filtreren regels. De beheerders van het netwerk zijn verantwoordelijk voor het aanpassen van hen aan de behoeften van hun bedrijf.

>[!IMPORTANT]
>
>De kwalificatie van e-mails als ongewenst door SpamAssassin is volledig gebaseerd op filtreer- en scoreregels.
>
>Deze regels moeten daarom ten minste eenmaal per dag worden bijgewerkt om ervoor te zorgen dat uw SpamAssassin-installatie en de integratie ervan in Adobe Campaign volledig functioneel zijn en dat de relevantie van de scores die aan uw leveringen zijn toegekend, wordt gegarandeerd voordat deze worden verzonden.
>
>Deze update valt onder de verantwoordelijkheid van de serverbeheerder die als host fungeert voor SpamAssassin.

Het gebruik van SpamAssassin in Adobe Campaign geeft een indicatie van het mogelijke gedrag van mailservers die SpamAssassin gebruiken wanneer ze e-mail ontvangen die door Adobe Campaign is verzonden. Het is echter mogelijk dat de mailservers van internetproviders of online-mailservers de berichten die door Adobe Campaign worden verzonden, als ongewenst beschouwen.

Voor het implementeren van SpamAssassin en de bijbehorende modules in Perl zijn Adobe Campaign-toepassingsservers vereist die zijn uitgerust met internettoegang via een HTTP-verbinding (TCP/80-flow).

## Installeren op een Windows-computer {#installing-on-a-windows-machine}

Voer de volgende stappen uit om SpamAssassin in Windows te installeren en te configureren om integratie met Adobe Campaign mogelijk te maken:

1. SpamAssassin installeren
1. SpamAssassin integreren in Adobe Campaign

### SpamAssassin installeren {#installing-spamassassin}

1. Verbinding maken met de [Software-distributieportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) met uw gebruikersgegevens. Meer informatie over softwaredistributie in [deze pagina](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html).
1. Download de **Neolane Spam Assassin (Windows-installatie) (2.0)** bestand (neolane_spammurin.2.0.zip).
1. Kopieer dit bestand naar de Adobe Campaign-server en decomprimeer het vervolgens.

   >[!NOTE]
   >
   >U kunt desgewenst het bestand uitpakken, mits het pad bestaat uit een van de volgende reguliere-expressietekens: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. Het installatiepad mag geen spatietekens bevatten.

1. Ga naar het bestand waarin u het bestand hebt uitgepakt en dubbelklik op het pictogram **run_me.bat** bestand om het installatiescript te starten.

   Als een Vensters Shell verschijnt en blijft voor een paar seconden worden getoond, wacht tot de installatie en de update zijn gebeëindigd, dan klik **Enter**.

   Als de Vensters Shell niet verschijnen of niet alvorens onmiddellijk verdwijnt getoond, deze stappen volgen, dubbelklik **portableShell.bat** dossier om een Vensters Shell te tonen en te controleren dat de weg van Shell aan de omslag beantwoordt waarin **spammoordenaar.zip** bestand is uitgepakt. Als dit niet het geval is, toegang tot het gebruikend **cd** gebruiken.

   Enter **run_me.bat** klik vervolgens op **Enter** om het installatie- en updateproces te starten. De bewerking retourneert een van de volgende waarden om het resultaat van de update aan te geven.

   * **0**: er is een update uitgevoerd.
   * **1**: Geen nieuwe update beschikbaar.
   * **2**: geen nieuwe update beschikbaar.
   * **3**: update is mislukt tijdens voorafgaande verificatie.
   * **4** of meer: er is een fout opgetreden.

1. Om te controleren dat de installatie SpamAssassin succesvol was, gebruik de test GTUBE (Generische Test voor Ongevraagde Bulk E-mail) gebruikend de volgende procedure:

   1. Een tekstbestand maken en opslaan onder **C:\TestSpamMail.txt**.
   1. Voeg de volgende inhoud in het bestand in:

      ```
      Subject: Test Spam Mail (GTUBE)
      Message-ID: <1010101@example.net>
      Date: MM-DD-YY
      From: Sender <sender@example.net>
      To: Recipient <recipient@example.net>
      Precedence: junk
      MIME-Version: 1.0
      Content-Type: text/plain; charset=us-ascii
      Content-Transfer-Encoding: 7bit
      
      XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
      ```

   1. Dubbelklik op de knop **portableShell.bat** dossier om een Vensters Shell te tonen dan het volgende bevel (of &quot;`<root>`&quot; wijst de gemaakte map aan wanneer het uitpakken van de  **spammoordenaar.zip** bestand):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      De inhoud van deze test-e-mail activeert een score van 1.000 punten door SpamAssassin. Dit betekent dat het als ongewenst is ontdekt en dat de installatie succesvol was en volledig functioneel is.

### SpamAssassin integreren in Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Bewerk de **`[INSTALL]/conf/serverConf.xml`** bestand. Alle parameters die beschikbaar zijn in het dialoogvenster **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).
1. De waarde van de optie **spamCheck** elementen&#39; **command** in het dialoogvenster **Web** knooppunt. Voer hiertoe de volgende opdracht uit:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Alle paden moeten absoluut zijn.

   Stop en start de **[!UICONTROL Adobe Campaign]** service.

1. Als u de integratie van SpamAssassin in Adobe Campaign wilt controleren, gebruikt u een GTBUE-test (Generic Test for Unrequested Bulk Email):

   Dubbelklik op de knop **portableshell.bat** bestand. Dit brengt de vertoning van Vensters Shell teweeg. Voer vervolgens de volgende opdracht uit:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   De inhoud van deze test-e-mail activeert 1.000 punten die door SpamAssassin zijn toegewezen. Dit betekent dat het als ongewenst is ontdekt en dat de integratie in Adobe Campaign succesvol was en volledig functioneert.

1. Het filtreren en het scoring regels van SpamAssassin bijwerken

   Voor een eerste update van filteren en het scoren van regels, begin **portableShell.bat** en voer de volgende opdracht uit:

   ```
   sa-update --no-gpg
   ```

   Om een automatische update van het filtreren en het schrapen regels in werking te stellen, gebruik dit zelfde bevel in een geplande systeemtaak:

   ```
   sa-update --no-gpg
   ```

## Installeren op een Linux-computer {#installing-on-a-linux-machine}

### Installatiestappen in Debian {#installation-steps-in-debian}

* Indien nodig, installeer Perl en SpamAssassin gebruikend het volgende bevel:

  ```
  apt-get install spamassassin libxml-writer-perl
  ```

* In de **serverConf.xml** bestand (beschikbaar in `/usr/local/[INSTALL]/nl6/conf/`), wijzigt u **spamCheck** lijn als volgt:

  ```
  <spamCheck command="perl
  /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
  ```

### Installatiestappen in RHEL/CentOS {#installation-steps-in-rhel-centos}

Indien nodig, installeer Perl en herhaal de pakketten gebruikend CPAN:

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### Filterregels bijwerken {#updating-filter-rules}

Filterregels kunnen automatisch worden bijgewerkt met de opdracht **sa-update** gebruiken. Raadpleeg de officiële website van SpamAssassin [https://spamassassin.apache.org/](https://spamassassin.apache.org/) voor meer informatie .

In Debian vinden updates elke dag automatisch plaats.

Als dit niet het geval is (bijvoorbeeld wanneer Debian manueel wordt geïnstalleerd), creeer een manuscript om regelupdates te automatiseren.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Dit script invoegen in **crontab** met de volgende opdracht:

```
crontab-e
```

### Optimalisatie van prestaties {#performance-optimization}

Als u de prestaties in Linux wilt verbeteren, bewerkt u de **/etc/spamassassin/local.cf** en voeg de volgende regel toe aan het einde van het bestand:

```
dns_available no
```
