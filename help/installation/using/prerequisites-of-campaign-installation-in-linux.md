---
product: campaign
title: Vereisten voor installatie van campagne in Linux
description: Vereisten voor installatie van campagne in Linux
feature: Installation, Instance Settings
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---

# Vereisten om Campagne op Linux te installeren{#prerequisites-of-campaign-installation-in-linux}



## Softwarevereisten {#software-prerequisites}

In dit gedeelte worden de voorbereidende stappen beschreven die zijn vereist voor de installatie van Adobe Campaign.

De technische en softwareconfiguratie die nodig is voor de installatie van Adobe Campaign wordt beschreven in de [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

Ter herinnering, moeten de volgende componenten worden geïnstalleerd en correct worden gevormd:

* Apache, raadpleeg de [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md),
* Java JDK en OpenJDK, raadpleeg [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotheken, raadpleeg [Bibliotheken](#libraries),
* De de toegangslagen van het gegevensbestand, verwijzen naar [Databasetoegangslagen](#database-access-layers),
* LibreOffice, zie [LibreOffice voor Debian installeren](#installing-libreoffice-for-debian) en [LibreOffice voor CentOS installeren](#installing-libreoffice-for-centos),
* Lettertypen, zie [Lettertypen voor MTA-statistieken](#fonts-for-mta-statistics) en [Lettertypen voor Japanse instanties](#fonts-for-japanese-instances).

>[!NOTE]
>
>Als u een build lager of gelijk aan 8709 wilt installeren op de platforms CentOS 7 en Debian 8, moet de module apache access_compat zijn ingeschakeld.

### Bibliotheken {#libraries}

Zorg ervoor dat u de vereiste bibliotheken hebt om Adobe Campaign in Linux te installeren.

* Bibliotheek C moet ondersteuning bieden voor de tls-modus (Thread Local Storage). Deze modus is in de meeste gevallen actief, behalve bij sommige kernels waarvoor Xen-ondersteuning is uitgeschakeld.

  U kunt dit controleren door bijvoorbeeld de **opdracht uname -a | grep xen te** gebruiken.

  Als het bevel om het even wat (lege lijn) niet terugkeert, betekent het configuratie correct is.

* U moet OpenSSL-versie hebben **1.0.2.** of hoger.

  Voor RHEL 7/8-distributies is versie 1.0 van OpenSSL vereist.

* Als je Adobe Campaign wilt gebruiken, moet je beschikken over de **libicu** geïnstalleerde bibliotheek.

  De volgende versies van **libicu** worden ondersteund (32-bits of 64-bits):

   * RHEL 7/8, CentOS 7: libicu50
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

### Selinux {#selinux}

Indien gebruikt, moet de SELinux module correct geconfigureerd zijn.

Om dit te doen, login als wortel en ga het volgende bevel in:

```
echo 0 >/selinux/enforce
```

Daarnaast wordt in de **/etc/sysconfig/httpd** bestand, is de volgende regel toegevoegd om naar het Adobe Campaign-omgevingsconfiguratiescript te verwijzen:

```
. ~neolane/nl6/env.sh
```

In RHEL en CentOS werden compatibiliteitsproblemen met de clientlagen van databases opgemerkt wanneer SELinux wordt ingeschakeld. We raden u aan SELinux uit te schakelen om er zeker van te zijn dat Adobe Campaign correct kan werken.

**Pas het volgende proces toe:**

* Het bestand bewerken **/etc/selinux/config**

* Wijzig de SELINUX-lijn als volgt:

```
SELINUX=disabled
```

### Lettertypen voor MTA-statistieken {#fonts-for-mta-statistics}

Voeg lettertypen toe om te zorgen dat rapporten over MTA-statistieken (nms/fra/jsp/stat.jsp) correct worden weergegeven.

In Debian voegt u de opdracht toe:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Gebruik in Redhat de volgende opdracht:

* Voor CentOS/RHEL 7:

  ```
  yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
  ```

* Voor RHEL 8:

  ```
  dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
  ```

### Lettertypen voor Japanse instanties {#fonts-for-japanese-instances}

Voor Japanse exemplaren zijn lettertypen van specifieke tekens nodig om de rapporten naar de indeling PDF te kunnen exporteren.

Voeg in Debian de opdracht toe:

```
aptitude install fonts-ipafont
```

Voeg in Rode hoed de opdracht toe:

* Voor RHEL 7:

  ```
  yum install ipa-gothic-fonts ipa-mincho-fonts
  ```

* Voor RHEL 8:

  ```
  dnf install vlgothic-fonts
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

De volgende configuraties zijn nodig voor CentOS:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Lagen voor databasetoegang {#database-access-layers}

De toegangslagen voor de database-engine die u gebruikt, moeten op de server zijn geïnstalleerd en toegankelijk zijn via de Adobe Campaign-account. Versies en installatiemodi kunnen variëren, afhankelijk van de gebruikte database-engine.

De ondersteunde proefversie wordt beschreven in het gedeelte [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

Controleer ook het algemene [Database](../../installation/using/database.md) sectie.

### PostgreSQL {#postgresql}

Adobe Campaign biedt ondersteuning voor alle versies van de PostgreSQL-clientbibliotheken uit versie 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** en **libpq.so.3.1**).

Als u PostSQL met Adobe Campaign gebruikt, moet u ook de bijbehorende **pgcrypto** bibliotheken.

### Oracle {#oracle}

Haal de bibliotheekversie op voor 64-bits Debian, dat wil zeggen: **libclntsh.so**, **libclntsh.so.11.1** en **libclntsh.so.10.1**.

U kunt een Linux RPM pakket van het Netwerk van de Technologie van het Oracle verkrijgen.

>[!NOTE]
>
>Als u de client voor het Oracle al hebt geïnstalleerd, maar de algemene omgeving (bijvoorbeeld: /etc/profile) niet correct is geconfigureerd, kunt u ontbrekende informatie toevoegen aan de **nl6/customer.sh** script Raadpleeg voor meer informatie hierover [Omgevingsvariabelen](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Problemen oplossen en best practices**

Problemen kunnen optreden na een Oracle-client of een serverupdate, een wijziging van versie of bij de eerste installatie van de instantie.

Als u in de clientconsole merkt dat er onverwachte vertragingen (één of meer uren) zijn in de logbestanden, laatste verwerking van de workflow, de volgende verwerking enzovoort, is er mogelijk een probleem tussen de bibliotheek van de Oracle-client en de Oracle Server. Dergelijke problemen voorkomen

1. Zorg ervoor dat u de **volledige client**.

   Er zijn verschillende problemen geïdentificeerd bij het gebruik van de Oracle Instant Client-versie. Bovendien is het onmogelijk om het dossier van de Tijdzone op onmiddellijke cliënt te veranderen.

1. Zorg ervoor dat de **clientversie** en de **databaseserverversie** zijn **zelfde**.

   Het is bekend dat het mengen van versies ondanks de compatibiliteitsmatrix van Oracle en het advies om client- en serverversies uit te lijnen problemen kan veroorzaken.

   Controleer ook ORACLE_HOME waarde om te controleren of deze naar de verwachte clientversie wijst (als er meerdere versies op de computer zijn geïnstalleerd).

1. Zorg ervoor dat de client en de server hetzelfde **tijdzonebestand** gebruiken.

### DB2 {#db2}

De ondersteunde bibliotheekversie is **libdb2.so**.

## Implementatiestappen {#implementation-steps}

Adobe Campaign-installaties voor Linux moeten in de volgende volgorde worden uitgevoerd: serverinstallatie gevolgd door instantieconfiguratie.

Het installatieproces wordt in dit hoofdstuk beschreven. De installatiestappen zijn als volgt:

* Stap 1: De toepassingsserver installeren, verwijs naar [Pakketten installeren met Linux](../../installation/using/installing-packages-with-linux.md).
* Stap 2: Het integreren met een server van het Web (facultatief, afhankelijk van de opgestelde componenten).

Zodra de installatiestappen volledig zijn, moet u de instanties, het gegevensbestand en de server vormen. Raadpleeg voor meer informatie hierover [Informatie over initiële configuratie](../../installation/using/about-initial-configuration.md).
