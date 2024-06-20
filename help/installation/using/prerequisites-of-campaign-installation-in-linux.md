---
product: campaign
title: Vereisten voor installatie van campagne in Linux
description: Voorwaarden voor de Campaign-installatie in Linux
feature: Installation, Instance Settings
badge-v7-prem: label="Alleen on-premise/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premises en hybride implementaties"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# Vereisten om Campagne op Linux te installeren{#prerequisites-of-campaign-installation-in-linux}

## Softwarevereisten {#software-prerequisites}

In dit gedeelte worden de voorbereidende stappen beschreven die zijn vereist voor de installatie van Adobe Campaign.

De technische en softwareconfiguratie die nodig is voor de installatie van Adobe Campaign wordt beschreven in de [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

Ter herinnering, moeten de volgende componenten worden geïnstalleerd en correct worden gevormd:

* Apache, zie [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md),
* Java JDK en OpenJDK, zie [Java Development Kit - JDK](../../installation/using/application-server.md#jdk),
* Bibliotheken, zie [Bibliotheken](#libraries),
* De de toegangslagen van het gegevensbestand, verwijzen naar [Databasetoegangslagen](#database-access-layers),
* LibreOffice, zie [LibreOffice voor Debian installeren](#installing-libreoffice-for-debian) en [LibreOffice voor CentOS installeren](#installing-libreoffice-for-centos),
* Lettertypen, zie [Lettertypen voor MTA-statistieken](#fonts-for-mta-statistics) en [Lettertypen voor Japanse instanties](#fonts-for-japanese-instances).


### Bibliotheken {#libraries}

Zorg ervoor dat u de vereiste bibliotheken hebt om Adobe Campaign in Linux te installeren.

* Bibliotheek C moet ondersteuning bieden voor de tls-modus (Thread Local Storage). Deze modus is in de meeste gevallen actief, behalve bij sommige kernels waarvoor Xen-ondersteuning is uitgeschakeld.

  U kunt dit controleren door bijvoorbeeld de **opdracht uname -a | grep xen te** gebruiken.

  Als het bevel geen lege lijn terugkeert, betekent het configuratie correct is.

* U moet OpenSSL-versie hebben **1.0.2.** of hoger.

  Voor RHEL-distributies is versie 1.0 van OpenSSL vereist.

* Als je Adobe Campaign wilt gebruiken, moet je beschikken over de **libicu** geïnstalleerde bibliotheek.

### SELinux {#selinux}

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

* Wijzig de regel SELINUX als volgt:

```
SELINUX=disabled
```

### Lettertypen voor MTA-statistieken {#fonts-for-mta-statistics}

Om rapporten over MTA statistieken (nms/fra/jsp/stat.jsp) correct te tonen, voeg doopvonten toe.

Voeg in Debian de opdracht toe:

```
apt install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Gebruik de volgende opdracht voor RHEL:

```
dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
```

### Lettertypen voor Japanse instanties {#fonts-for-japanese-instances}

Lettertypen met specifieke tekens zijn nodig voor de Japanse instanties om de rapporten naar de PDF-indeling te exporteren.

In Debian voegt u de opdracht toe:

```
apt install fonts-ipafont
```

Voeg voor RHEL de volgende opdracht toe:

```
dnf install epel-release # if required
dnf install vlgothic-fonts
```

### LibreOffice voor Debian installeren {#installing-libreoffice-for-debian}

Voor Debian zijn de volgende configuraties vereist:

1. Installeer de volgende standaardpakketten:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installeer de volgende lettertypen (optioneel, maar wordt sterk aanbevolen voor Japanse instanties):

   ```
   apt-get install fonts-ipafont
   ```

### LibreOffice voor CentOS installeren {#installing-libreoffice-for-centos}

De volgende configuraties zijn nodig voor CentOS:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Lagen voor databasetoegang {#database-access-layers}

De toegangslagen voor de database-engine die u gebruikt, moeten op uw server zijn geïnstalleerd en toegankelijk zijn via het Adobe Campaign-account. Versies en installatiemodi kunnen variëren, afhankelijk van de gebruikte database-engine.

De ondersteunde proefversie wordt beschreven in het gedeelte [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

Controleer ook het algemene [Database](../../installation/using/database.md) sectie.

### PostgreSQL {#postgresql}

Adobe Campaign biedt ondersteuning voor alle versies van de PostgreSQL-clientbibliotheken uit versie 9.6: **libpq.so.5**.

Als u PostSQL met Adobe Campaign gebruikt, moet u ook de bijbehorende **pgcrypto** bibliotheken.

### Oracle {#oracle}

Haal de bibliotheekversie op voor 64-bits Debian, dat wil doen: libclntsh.so, libclntsh.so.19.1 **,** libclntsh.so.18.1 **,** libclntsh.so.12.1 **,** libclntsh.so.11.1 of **** libclntsh.so.10.1.********

U kunt een Linux RPM-pakket verkrijgen van Oracle Technology Network.

>[!NOTE]
>
>Als u de Oracle client al hebt geïnstalleerd, maar de algemene omgeving (bijvoorbeeld: /etc/profile) niet goed is geconfigureerd, kunt u ontbrekende informatie toevoegen aan het **nl6/customer.sh** script Raadpleeg omgevingsvariabelen](../../installation/using/installing-packages-with-linux.md#environment-variables) voor meer informatie [hierover.

**Probleemoplossing en aanbevolen procedures**

Problemen kunnen optreden na een Oracle-client of een serverupdate, een versiewijziging of bij de eerste installatie van de instantie.

Als u op de cliëntconsole opmerkt dat er onverwachte tijdvertraging (één of meerdere uren) in logboeken, werkschemalaatste verwerking, volgende verwerking, etc. zijn, zou er een probleem tussen de bibliotheek van de cliënt van het Oracle en de Server van het Oracle kunnen zijn. Dergelijke problemen voorkomen

1. Zorg ervoor dat u de **volledige client**.

   Er zijn verschillende problemen geïdentificeerd bij het gebruik van de Oracle Instant Client-versie. Bovendien is het onmogelijk om het tijdzone-bestand op de Instant-client te wijzigen.

1. Controleer of de **clientversie** en de versie **van de** databaseserver gelijk **zijn**.

   Het mengen van versies ondanks de verenigbaarheidsmatrijs en aanbeveling van het Oracle om cliënt en serverversies te richten is gekend om problemen te veroorzaken.

   Controleer ook ORACLE_HOME-waarde om te controleren of deze naar de verwachte clientversie verwijst (als er meerdere versies op de computer zijn geïnstalleerd).

1. Zorg ervoor dat de client en de server hetzelfde gebruiken **tijdzonebestand**.

## Implementatiestappen {#implementation-steps}

Adobe Campaign-installaties voor Linux moeten in de volgende volgorde worden uitgevoerd: serverinstallatie gevolgd door instantieconfiguratie.

Het installatieproces wordt in dit hoofdstuk beschreven. De installatiestappen zijn als volgt:

* Stap 1: De toepassingsserver installeren, verwijs naar [Pakketten installeren met Linux](../../installation/using/installing-packages-with-linux.md).
* Stap 2: Het integreren met een server van het Web (facultatief, afhankelijk van de opgestelde componenten).

Zodra de installatiestappen volledig zijn, moet u de instanties, het gegevensbestand en de server vormen. Raadpleeg voor meer informatie hierover [Informatie over initiële configuratie](../../installation/using/about-initial-configuration.md).
