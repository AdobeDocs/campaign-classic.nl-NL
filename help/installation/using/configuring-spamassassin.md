---
title: SpamAssassin configureren
seo-title: SpamAssassin configureren
description: SpamAssassin configureren
seo-description: null
page-status-flag: never-activated
uuid: 327548c0-d621-4417-9fc9-b0bf30251dc0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: aa37bdc6-0f85-4eca-859f-e8b15083cfb5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1a9d4c9eadf996d37481f33636eae98e482ac115
workflow-type: tm+mt
source-wordcount: '984'
ht-degree: 0%

---


# SpamAssassin configureren{#configuring-spamassassin}

>[!NOTE]
>
>Sommige configuraties kunnen alleen door Adobe worden uitgevoerd voor implementaties die worden gehost door Adobe. Bijvoorbeeld, om tot de server en de dossiers van de instantieconfiguratie toegang te hebben. Meer over de verschillende plaatsingen leren, verwijs naar de [Hosting modelsectie](../../installation/using/hosting-models.md) of naar [dit artikel](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Overzicht {#overview}

SpamAssassin is software die is ontworpen om ongewenste e-mails te filteren. In combinatie met deze software kan Adobe Campaign een score toewijzen aan e-mailberichten en bepalen of een bericht waarschijnlijk ongewenst wordt geacht voordat de levering wordt gestart. Hiervoor moet SpamAssassin op de toepassingsserver(s) van Adobe Campaign zijn geïnstalleerd en geconfigureerd en is een aantal aanvullende Perl-modules vereist om te werken.

De plaatsing en de integratie van SpamAssassin zoals die in dit hoofdstuk wordt beschreven zijn gebaseerd op standaardsoftwareinstallatie, zoals filtreren en het scoren regels, die die door SpamAssassin zonder enige veranderingen of optimalisaties worden verstrekt. De attributie van de score en de berichtkwalificatie zijn uitsluitend gebaseerd op de configuratie van opties SpamAssassin en op het filtreren regels. De beheerders van het netwerk zijn verantwoordelijk voor het aanpassen van hen aan de behoeften van hun bedrijf.

>[!IMPORTANT]
>
>De kwalificatie van e-mails als ongewenst door SpamAssassin is volledig gebaseerd op filtreer- en scoreregels.
>
>Deze regels moeten daarom ten minste eenmaal per dag worden bijgewerkt, zodat uw SpamAssassin-installatie en de integratie ervan in Adobe Campaign volledig functioneel zijn en de relevantie van de scores die aan uw leveringen zijn toegewezen, wordt gegarandeerd voordat deze worden verzonden.
>
>Deze update valt onder de verantwoordelijkheid van de serverbeheerder die als host fungeert voor SpamAssassin.

Het gebruik van SpamAssassin in de Campagne van Adobe verstrekt een aanwijzing op het mogelijke gedrag van postservers die SpamAssassin gebruiken wanneer zij e-mail ontvangen die door de Campagne van Adobe wordt verzonden. Het is echter mogelijk dat de mailservers van internetproviders of online-mailservers de berichten die door Adobe Campaign worden verzonden, als ongewenst beschouwen.

Voor het implementeren van SpamAssassin en de bijbehorende modules in Perl zijn Adobe Campagne-toepassingsservers vereist die via een HTTP-verbinding (TCP/80-flow) zijn uitgerust met internettoegang.

## Installeren op een Windows-computer {#installing-on-a-windows-machine}

Voer de volgende stappen uit als u SpamAssassin in Windows wilt installeren en configureren om integratie met Adobe Campaign mogelijk te maken:

1. SpamAssassin installeren
1. SpamAssassin integreren in Adobe-campagne

### SpamAssassin installeren {#installing-spamassassin}

1. Maak verbinding met het [Extranetportaal](http://support.neolane.net) met uw gebruikersgegevens.
1. Ga naar het **Downloadcentrum** en blader op de pagina naar de sectie **Tools** .
1. Download het bestand **Neolane Spam Assassin (Windows-installatie) (2.0)** (neolane_spammurin.2.0.zip).
1. Kopieer dit bestand naar de Adobe Campaign-server en decomprimeer het vervolgens.

   >[!NOTE]
   >
   >U kunt desgewenst het bestand uitpakken, mits het pad bestaat uit een van de volgende reguliere-expressietekens: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. Het installatiepad mag geen spatietekens bevatten.

1. Ga naar het bestand waarin u het bestand hebt uitgepakt en dubbelklik op het bestand **run_me.bat** om het installatiescript te starten.

   Als een Vensters Shell verschijnt en blijft voor een paar seconden worden getoond, wacht tot de installatie en de update zijn gebeëindigd, dan klik **binnengaan**.

   Als de Vensters Shell niet verschijnt of niet alvorens onmiddellijk verdwijnt getoond, deze stappen volgen, tweemaal klikken het **portableShell.bat** dossier om een Vensters Shell te tonen en te controleren dat de weg van Shell aan de omslag beantwoordt waarin het **spammurin.zip** dossier is unzipped. Als dit niet het geval is, toegang het gebruikend het **cd** bevel.

   Voer **run_me.bat** in en klik vervolgens op **Enter** om het installatie- en updateproces te starten. De bewerking retourneert een van de volgende waarden om het resultaat van de update aan te geven.

   * **0**: er is een bijwerking uitgevoerd.
   * **1**: Geen nieuwe update beschikbaar.
   * **2**: geen nieuwe update beschikbaar.
   * **3**: update is mislukt tijdens voorafgaande verificatie.
   * **4** of meer: er heeft zich een fout voorgedaan.

1. Om te controleren dat de installatie SpamAssassin succesvol was, gebruik de test GTUBE (Generische Test voor Ongevraagde Bulk E-mail) gebruikend de volgende procedure:

   1. Maak een tekstbestand en sla dit op onder **C:\TestSpamMail.txt**.
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

   1. Dubbelklik op het bestand **portableShell.bat** om een Windows Shell weer te geven en start vervolgens de volgende opdracht (of &quot;`<root>`&quot; geeft de gemaakte map aan wanneer het bestand **spammurin.zip** wordt uitgepakt):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      De inhoud van deze test-e-mail activeert een score van 1.000 punten door SpamAssassin. Dit betekent dat het als ongewenst is ontdekt en dat de installatie succesvol was en volledig functioneel is.

### SpamAssassin integreren in Adobe-campagne {#integrating-spamassassin-into-adobe-campaign}

1. Bewerk het **`[INSTALL]/conf/serverConf.xml`** bestand. Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).
1. Verander de waarde van het **spamCheck** de **bevelattribuut** van elementen in de knoop van het **Web** . Voer hiertoe de volgende opdracht uit:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Alle paden moeten absoluut zijn.

   Stop en start de **[!UICONTROL Adobe Campaign]** service.

1. Als u de integratie van SpamAssassin in Adobe Campaign wilt controleren, gebruikt u een GTBUE-test (Algemene test voor ongevraagde e-mail met opsommingstekens):

   Dubbelklik op het bestand **portableshell.bat** . Dit brengt de vertoning van Vensters Shell teweeg. Voer vervolgens de volgende opdracht uit:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   De inhoud van deze test-e-mail activeert 1.000 punten die door SpamAssassin zijn toegewezen. Dit betekent dat het als ongewenst is gedetecteerd en dat de integratie in Adobe Campaign is gelukt en volledig functioneel is.

1. Het filtreren en het scoring regels van SpamAssassin bijwerken

   Voor een eerste update van het filtreren en het schrapen van regels, begin **portableShell.bat** en stel het volgende bevel in werking:

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

* Wijzig in het bestand **serverConf.xml** (beschikbaar in `/usr/local/[INSTALL]/nl6/conf/`) de regel **spamCheck** als volgt:

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

Filterregels kunnen automatisch worden bijgewerkt met het gereedschap **sa-update** . Raadpleeg de officiële website van SpamAssassin [http://spamassassin.apache.org/](http://spamassassin.apache.org/) voor meer informatie.

In Debian vinden updates elke dag automatisch plaats.

Als dit niet het geval is (bijvoorbeeld wanneer Debian manueel wordt geïnstalleerd), creeer een manuscript om regelupdates te automatiseren.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Voeg dit script met de volgende opdracht in **contab** :

```
crontab-e
```

### Optimalisatie van prestaties {#performance-optimization}

Als u de prestaties in Linux wilt verbeteren, bewerkt u het bestand **/etc/spamassassin/local.cf** en voegt u de volgende regel aan het einde van het bestand toe:

```
dns_available no
```

