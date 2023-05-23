---
product: campaign
title: Vereisten voor installatie van Campaign in Linux
description: Vereisten voor installatie van Campaign in Linux
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 1%

---

# Vereisten om Campagne op Linux te installeren{#prerequisites-of-campaign-installation-in-linux}



## Softwarevereisten {#software-prerequisites}

In dit gedeelte worden de voorbereidende stappen beschreven die zijn vereist voor de installatie van Adobe Campaign.

De technische en softwareconfiguratie die nodig is voor de installatie van Adobe Campaign wordt beschreven in de [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

Ter herinnering, moeten de volgende componenten worden geïnstalleerd en correct worden gevormd:

* Apache, zie [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md),
* Java JDK en OpenJDK, zie [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotheken, zie [Bibliotheken](#libraries),
* De de toegangslagen van het gegevensbestand, verwijs naar [Databasetoegangslagen](#database-access-layers),
* LibreOffice, zie [LibreOffice voor Debian installeren](#installing-libreoffice-for-debian) en [LibreOffice voor CentOS installeren](#installing-libreoffice-for-centos),
* Lettertypen, zie [Lettertypen voor MTA-statistieken](#fonts-for-mta-statistics) en [Lettertypen voor Japanse instanties](#fonts-for-japanese-instances).

>[!NOTE]
>
>Als u een build lager of gelijk aan 8709 wilt installeren op de platforms CentOS 7 en Debian 8, moet de module apache access_compat zijn ingeschakeld.

### Bibliotheken {#libraries}

Als u Adobe Campaign in Linux wilt installeren, moet u de vereiste bibliotheken hebben.

* Bibliotheek C moet de TLS-modus (Thread Local Storage) kunnen ondersteunen. Deze modus is in de meeste gevallen actief, behalve bij sommige kernels waarvoor Xen-ondersteuning is uitgeschakeld.

   Om dit te controleren, kunt u gebruiken **uname -a | groene xen** bijvoorbeeld.

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

### SELinux {#selinux}

Indien gebruikt, moet de module SELinux behoorlijk worden gevormd.

Om dit te doen, login als wortel en ga het volgende bevel in:

```
echo 0 >/selinux/enforce
```

Daarnaast wordt in de **/etc/sysconfig/httpd** bestand is de volgende regel toegevoegd om te verwijzen naar het Adobe Campaign-omgevingsconfiguratiescript:

```
. ~neolane/nl6/env.sh
```

In RHEL en CentOS werden compatibiliteitsproblemen met de clientlagen van databases opgemerkt wanneer SELinux wordt ingeschakeld. We raden u aan SELinux uit te schakelen om er zeker van te zijn dat Adobe Campaign correct kan werken.

**Pas het volgende proces toe:**

* Het bestand bewerken **/etc/selinux/config**

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

Voeg de opdracht in Rode hoed toe:

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

De volgende configuraties zijn nodig met CentOS:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Databasetoegangslagen {#database-access-layers}

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
>Als u al de client van het Oracle maar de algemene omgeving hebt geïnstalleerd (bijvoorbeeld: /etc/profile) niet correct wordt gevormd, kunt u ontbrekende informatie aan toevoegen **nl6/customer.sh** script Raadpleeg voor meer informatie hierover [Omgevingsvariabelen](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Problemen oplossen en best practices**

Problemen kunnen optreden na een Oracle-client of een serverupdate, een versiewijziging of bij de eerste installatie van de instantie.

Als u op de cliëntconsole opmerkt dat er onverwachte tijdvertraging (één of meerdere uren) in logboeken, werkschemalaatste verwerking, volgende verwerking, etc. zijn, zou er een probleem tussen de bibliotheek van de cliënt van het Oracle en de Server van het Oracle kunnen zijn. Dergelijke problemen voorkomen

1. Zorg ervoor dat u de **volledige client**.

   Er zijn verschillende problemen geïdentificeerd bij het gebruik van de Oracle Instant Client-versie. Bovendien is het onmogelijk om het dossier van de Tijdzone op onmiddellijke cliënt te veranderen.

1. Zorg ervoor dat de **clientversie** en de **databaseserverversie** zijn **zelfde**.

   Het mengen van versies ondanks de verenigbaarheidsmatrijs en aanbeveling van het Oracle om cliënt en serverversies te richten is gekend om problemen te veroorzaken.

   Controleer ook ORACLE_HOME-waarde om te controleren of deze naar de verwachte clientversie verwijst (als er meerdere versies op de computer zijn geïnstalleerd).

1. Zorg ervoor dat de client en de server hetzelfde gebruiken **tijdzonebestand**.

### DB2 {#db2}

De ondersteunde bibliotheekversie is **libdb2.so**.

## Implementatiestappen {#implementation-steps}

Adobe Campaign-installaties voor Linux moeten in de volgende volgorde worden uitgevoerd: serverinstallatie gevolgd door instantieconfiguratie.

Het installatieproces wordt in dit hoofdstuk beschreven. De installatiestappen zijn als volgt:

* Stap 1: De toepassingsserver installeren, raadpleegt u [Pakketten installeren met Linux](../../installation/using/installing-packages-with-linux.md).
* Stap 2: Integratie met een webserver (optioneel, afhankelijk van de gebruikte componenten).

Zodra de installatiestappen volledig zijn, moet u de instanties, het gegevensbestand en de server vormen. Raadpleeg voor meer informatie hierover [Informatie over initiële configuratie](../../installation/using/about-initial-configuration.md).
