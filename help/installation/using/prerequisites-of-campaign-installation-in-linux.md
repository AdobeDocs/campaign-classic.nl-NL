---
solution: Campaign Classic
product: campaign
title: Vereisten voor installatie van Campaign in Linux
description: Vereisten voor installatie van Campaign in Linux
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 2%

---


# Vereisten voor installatie van Campaign in Linux{#prerequisites-of-campaign-installation-in-linux}

## Softwarevereisten {#software-prerequisites}

In dit gedeelte worden de voorbereidende stappen beschreven die zijn vereist voor de installatie van Adobe Campaign.

De technische en softwareconfiguratie die vereist is voor de installatie van Adobe Campaign wordt beschreven in de [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

Ter herinnering, moeten de volgende componenten worden geïnstalleerd en correct worden gevormd:

* Apache, zie [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md),
* Java JDK en OpenJDK, verwijs naar [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotheken, zie [Bibliotheken](#libraries),
* De de toegangslagen van het gegevensbestand, verwijs naar [de toegangslagen van het Gegevensbestand](#database-access-layers),
* LibreOffice, verwijs naar [Installing LibreOffice for Debian](#installing-libreoffice-for-debian) en [Installing LibreOffice for CentOS](#installing-libreoffice-for-centos);
* Lettertypen, raadpleeg [Lettertypen voor MTA-statistieken](#fonts-for-mta-statistics) en [Lettertypen voor Japanse instanties](#fonts-for-japanese-instances).

>[!NOTE]
>
>Als u een build lager of gelijk aan 8709 wilt installeren op de platforms CentOS 7 en Debian 8, moet de module apache access_compat zijn ingeschakeld.

### Bibliotheken {#libraries}

Als u Adobe Campaign in Linux wilt installeren, moet u de vereiste bibliotheken hebben.

* Bibliotheek C moet de TLS-modus (Thread Local Storage) kunnen ondersteunen. Deze modus is in de meeste gevallen actief, behalve bij sommige kernels waarvoor Xen-ondersteuning is uitgeschakeld.

   Om dit te controleren, kunt u **uname -a gebruiken | grep xen** opdracht bijvoorbeeld.

   Als het bevel om het even wat (lege lijn) niet terugkeert, betekent het configuratie correct is.

* U moet **versie 0.9.8** of **1.0** van OpenSSL hebben.

   Voor RHEL 7-distributies is versie 1.0 van OpenSSL vereist.

* Als u Adobe Campaign wilt gebruiken, moet de bibliotheek **libicu** zijn geïnstalleerd.

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

Daarnaast is in het bestand **/etc/sysconfig/httpd** de volgende regel toegevoegd om naar het Adobe Campaign-omgevingsconfiguratiescript te verwijzen:

```
. ~neolane/nl6/env.sh
```

In RHEL en CentOS werden compatibiliteitsproblemen met de clientlagen van databases opgemerkt wanneer SELinux wordt ingeschakeld. We raden u aan SELinux uit te schakelen om er zeker van te zijn dat Adobe Campaign correct kan werken.

**Pas het volgende proces toe:**

* Het bestand **/etc/selinux/config** bewerken

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

### LibreOffice voor Debian {#installing-libreoffice-for-debian} installeren

Voor Debian zijn de volgende configuraties vereist:

1. Installeer de volgende standaardpakketten:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installeer de volgende lettertypen (optioneel, maar hoogst aanbevolen voor Japanse instanties):

   ```
   apt-get install fonts-ipafont
   ```

### LibreOffice installeren voor CentOS {#installing-libreoffice-for-centos}

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

De toegangslagen voor de database-engine die u gebruikt, moeten op de server zijn geïnstalleerd en toegankelijk zijn via de Adobe Campaign-account. Versies en installatiemodi kunnen variëren, afhankelijk van de gebruikte database-engine.

De ondersteunde proefversie wordt beschreven in de [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

Controleer ook de algemene [Database](../../installation/using/database.md) sectie.

### PostgreSQL {#postgresql}

Adobe Campaign biedt ondersteuning voor alle versies van de PostgreSQL-clientbibliotheken uit versie 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** en **libpq.so.3.1**).

Als u PostSQL met Adobe Campaign gebruikt, moet u ook de bijbehorende **pgcrypto**-bibliotheken installeren.

### Oracle {#oracle}

Haal de bibliotheekversie op voor 64-bits Debian, dat wil zeggen: **libclntsh.so**, **libclntsh.so.11.1** en **libclntsh.so.10.1**.

U kunt een Linux RPM-pakket verkrijgen van het Oracle Technology Network.

>[!NOTE]
>
>Als u de Oracle-client al hebt geïnstalleerd, maar de algemene omgeving (bijvoorbeeld: /etc/profile) niet behoorlijk wordt gevormd, kunt u ontbrekende informatie aan **nl6/customer.sh** manuscript voor meer op dit toevoegen, verwijs naar [de variabelen van het Milieu](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Problemen oplossen en best practices**

Problemen kunnen optreden na een Oracle-client of een serverupdate, een versiewijziging of bij de eerste installatie van de instantie.

Als u op de cliëntconsole opmerkt dat er onverwachte tijdvertraging (één of meerdere uren) in logboeken, werkschema laatste verwerking, volgende verwerking, etc. zijn, zou er een probleem tussen de bibliotheek van de cliënt van Oracle en de Server van Oracle kunnen zijn. Dergelijke problemen voorkomen

1. Zorg ervoor dat u de **volledige client** gebruikt.

   Er zijn verschillende problemen geïdentificeerd bij het gebruik van de Oracle Instant Client-versie. Bovendien is het onmogelijk om het dossier van de Tijdzone op onmiddellijke cliënt te veranderen.

1. Zorg ervoor dat de **clientversie** en de **databaseserverversie** **same** zijn.

   Het is bekend dat het mengen van versies ondanks de compatibiliteitsmatrix van Oracle en de aanbeveling om client- en serverversies uit te lijnen problemen kan veroorzaken.

   Controleer ook de ORACLE_HOME-waarde om te controleren of deze naar de verwachte clientversie verwijst (als er meerdere versies op de computer zijn geïnstalleerd).

1. Zorg ervoor dat de client en de server hetzelfde **tijdzonebestand** gebruiken.

### DB2 {#db2}

De ondersteunde bibliotheekversie is **libdb2.so**.

## Implementatiestappen {#implementation-steps}

Adobe Campaign-installaties voor Linux moeten in de volgende volgorde worden uitgevoerd: serverinstallatie gevolgd door instantieconfiguratie.

Het installatieproces wordt in dit hoofdstuk beschreven. De installatiestappen zijn als volgt:

* Stap 1: Als u de toepassingsserver wilt installeren, raadpleegt u [Pakketten installeren met Linux](../../installation/using/installing-packages-with-linux.md).
* Stap 2: Integratie met een webserver (optioneel, afhankelijk van de gebruikte componenten).

Zodra de installatiestappen volledig zijn, moet u de instanties, het gegevensbestand en de server vormen. Voor meer op dit, verwijs naar [Ongeveer aanvankelijke configuratie](../../installation/using/about-initial-configuration.md).
