---
title: Vereisten voor installatie van campagne in Linux
seo-title: Vereisten voor installatie van campagne in Linux
description: Vereisten voor installatie van campagne in Linux
seo-description: null
page-status-flag: never-activated
uuid: 65c7af3f-ca1d-4255-b54a-6a3c83af40ae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 3e2ccb70-6c0c-435f-9c06-f3e5e40367bb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# Vereisten voor installatie van campagne in Linux{#prerequisites-of-campaign-installation-in-linux}

## Softwarevereisten {#software-prerequisites}

In deze sectie worden de voorbereidende stappen beschreven die voor de installatie van Adobe Campagne zijn vereist.

De technische en softwareconfiguratie die vereist is voor de installatie van Adobe Campaign wordt beschreven in de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Ter herinnering, moeten de volgende componenten worden geïnstalleerd en correct worden gevormd:

* Apache, raadpleeg de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).
* Java JDK en OpenJDK, verwijs naar [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotheken, zie [Bibliotheken](#libraries),
* De toegangslagen van het gegevensbestand, verwijs naar de toegangslagen [van het](#database-access-layers)Gegevensbestand,
* LibreOffice, verwijs naar het [Installeren van LibreOffice voor Debian](#installing-libreoffice-for-debian) en het [Installeren van LibreOffice voor CentOS](#installing-libreoffice-for-centos),
* Lettertypen, raadpleeg [Lettertypen voor MTA-statistieken](#fonts-for-mta-statistics) en [Lettertypen voor Japanse instanties](#fonts-for-japanese-instances).

>[!NOTE]
>
>Als u een build lager of gelijk aan 8709 wilt installeren op de platforms CentOS 7 en Debian 8, moet de module apache access_compat zijn ingeschakeld.

### Bibliotheken {#libraries}

Als u Adobe Campaign in Linux wilt installeren, moet u over de vereiste bibliotheken beschikken.

* Bibliotheek C moet de TLS-modus (Thread Local Storage) kunnen ondersteunen. Deze modus is in de meeste gevallen actief, behalve bij sommige kernels waarvoor Xen-ondersteuning is uitgeschakeld.

   Om dit te controleren, kunt u gebruiken **uname - a| bijvoorbeeld de opdracht grep xen** .

   Als het bevel om het even wat (lege lijn) niet terugkeert, betekent het configuratie correct is.

* U moet **versie 0.9.8** of **1.0** van OpenSSL hebben.

   Voor RHEL 7-distributies is versie 1.0 van OpenSSL vereist.

* Als u Adobe Campaign wilt gebruiken, moet de **libicu** -bibliotheek zijn geïnstalleerd.

   De volgende versies van **libicu** worden ondersteund (32-bits of 64-bits):

   * RHEL 7, CentOS 7: libicu50
   * Debian 8: libicu52
   * Debian 9: libicu57
   Als u Adobe Campaign wilt gebruiken, moet de bibliotheek libc-ares zijn geïnstalleerd. Voer bij RHEL/CentOS de volgende opdracht uit:

   ```
   yum install c-ares
   ```

   In Debian:

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

Indien gebruikt, moet de module SELinux behoorlijk worden gevormd.

Om dit te doen, login als wortel en ga het volgende bevel in:

```
echo 0 >/selinux/enforce
```

Daarnaast is in het bestand **/etc/sysconfig/httpd** de volgende regel toegevoegd om te verwijzen naar het configuratiescript voor de omgeving van Adobe Campagne:

```
. ~neolane/nl6/env.sh
```

In RHEL en CentOS werden compatibiliteitsproblemen met de clientlagen van databases opgemerkt wanneer SELinux wordt ingeschakeld. We raden u aan SELinux uit te schakelen om er zeker van te zijn dat de Adobe-campagne correct kan werken.

**Pas het volgende proces toe:**

* Het bestand **/etc/selinux/config bewerken**

* Wijzig de regel SELINUX als volgt:

```
SELINUX=disabled
```

### Lettertypen voor MTA-statistieken {#fonts-for-mta-statistics}

Om rapporten over MTA statistieken (nms/fra/jsp/stat.jsp) correct te tonen, voeg doopvonten toe.

Voeg in Debian de opdracht toe:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Gebruik in Redhat de volgende opdracht:

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### Lettertypen voor Japanse instanties {#fonts-for-japanese-instances}

Voor Japanse exemplaren zijn lettertypen van specifieke tekens nodig om de rapporten naar de PDF-indeling te kunnen exporteren.

Voeg in Debian de opdracht toe:

```
aptitude install fonts-ipafont
```

Voeg de opdracht in Rode hoed toe:

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### LibreOffice voor Debian installeren {#installing-libreoffice-for-debian}

Voor Debian zijn de volgende configuraties vereist:

1. Installeer de volgende standaardpakketten:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installeer de volgende lettertypen (optioneel, maar hoogst aanbevolen voor Japanse instanties):

   ```
   apt-get install fonts-ipafont
   ```

### LibreOffice voor CentOS installeren {#installing-libreoffice-for-centos}

De volgende configuraties zijn nodig met CentOS:

1. Installeer de volgende standaardpakketten:

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. Installeer de volgende lettertypen (optioneel, maar hoogst aanbevolen voor Japanse instanties):

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## Databasetoegangslagen {#database-access-layers}

De toegangslagen voor de database-engine die u gebruikt, moeten op de server zijn geïnstalleerd en toegankelijk zijn via het Adobe Campaign-account. Versies en installatiemodi kunnen variëren, afhankelijk van de gebruikte database-engine.

De ondersteunde proefversie wordt beschreven in de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Controleer ook de algemene sectie [Database](../../installation/using/database.md) .

### PostgreSQL {#postgresql}

Adobe Campaign biedt ondersteuning voor alle versies van de PostgreSQL-clientbibliotheken uit versie 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** en **libpq.so.3.1**).

Als u PostSQL met Adobe Campaign gebruikt, moet u ook de bijbehorende **pgcrypto** -bibliotheken installeren.

### Oracle {#oracle}

Haal de bibliotheekversie op voor 64-bits Debian, dat wil zeggen: **libclntsh.so**, **libclntsh.so.11.1** en **libclntsh.so.10.1**.

U kunt een Linux RPM-pakket verkrijgen van het Oracle Technology Network.

>[!NOTE]
>
>Als u de Oracle-client al hebt geïnstalleerd, maar de algemene omgeving (bijvoorbeeld: /etc/profile) niet correct wordt gevormd, kunt u ontbrekende informatie aan het **nl6/customer.sh** manuscript toevoegen voor meer op dit, verwijs naar de variabelen [van het](../../installation/using/installing-packages-with-linux.md#environment-variables)Milieu.

**Problemen oplossen en best practices**

Problemen kunnen optreden na een Oracle-client of een serverupdate, wijziging van versie of bij de eerste installatie van de instantie.

Als u op de clientconsole opmerkt dat er sprake is van onverwachte tijdsvertraging (een of meer uren) in logboeken, werkstroomlaatste verwerking, volgende verwerking enzovoort, kan er een probleem zijn tussen de bibliotheek van de Oracle-client en de Oracle-server. Dergelijke problemen voorkomen

1. Gebruik de **volledige client**.

   Er zijn verschillende problemen vastgesteld bij het gebruik van de Oracle Instant Client-versie. Bovendien is het onmogelijk om het dossier van de Tijdzone op onmiddellijke cliënt te veranderen.

1. Zorg ervoor dat de **clientversie** en de versie **van de** databaseserver **hetzelfde** zijn.

   Het is bekend dat het mixen van versies ondanks de compatibiliteitsmatrix en de aanbeveling van Oracle om client- en serverversies uit te lijnen problemen kan veroorzaken.

   Controleer ook de waarde ORACLE_HOME om te controleren of deze naar de verwachte clientversie verwijst (voor het geval er meerdere versies op de computer zijn geïnstalleerd).

1. Zorg ervoor dat de client en de server hetzelfde **tijdzonebestand** gebruiken.

### DB2 {#db2}

De ondersteunde bibliotheekversie is **libdb2.so**.

## Uitvoeringsstappen {#implementation-steps}

Adobe Campagne-installaties voor Linux moeten in de volgende volgorde worden uitgevoerd: serverinstallatie gevolgd door instantieconfiguratie.

Het installatieproces wordt in dit hoofdstuk beschreven. De installatiestappen zijn als volgt:

* Stap 1: Als u de toepassingsserver installeert, raadpleegt u [Pakketten met Linux](../../installation/using/installing-packages-with-linux.md)installeren.
* Stap 2: Integratie met een webserver (optioneel, afhankelijk van de gebruikte componenten).

Zodra de installatiestappen volledig zijn, moet u de instanties, het gegevensbestand en de server vormen. Voor meer op dit, verwijs naar [Ongeveer aanvankelijke configuratie](../../installation/using/about-initial-configuration.md).
