---
title: Toepassingsserver
seo-title: Toepassingsserver
description: Toepassingsserver
seo-description: null
page-status-flag: never-activated
uuid: 837c6a5c-53a4-4d1b-a084-9cf77e7a0eee
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 7a9e028c-255d-4aad-9827-d19f9a7897b2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# Toepassingsserver{#application-server}

De vereiste databasetoegangslagen moeten op de server zijn geïnstalleerd en toegankelijk zijn vanaf de Adobe Campagne-account.

## Java Development Kit - JDK {#java-development-kit---jdk}

De dynamische generator van de Web-pagina gebruikt JSP 1.2 technologie. Hiervoor wordt een Tomcat-engine (van Apache) in de toepassing opgenomen. Hiervoor is een JDK (Java Development Kit) vereist, die is geïnstalleerd op alle servers waarop de Adobe Campagne-toepassing is geïnstalleerd.

U moet eerst een JDK installeren op de computers waarop u de toepassingsserver van de Campagne van Adobe (**het Webproces** van de Server) wilt in werking stellen omdat het een servletcontainer, Apache Tomcat, opneemt die wordt gebruikt om dynamische Web-pagina&#39;s (rapporten, Web-formulieren, enz.) te produceren.

De toepassing is goedgekeurd voor de Java Development Kit (JDK) die door Oracle is ontwikkeld en voor **OpenJDK**.

De ondersteunde versies worden gedetailleerd beschreven in de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

>[!NOTE]
>
>De toepassing kan worden geïnstalleerd met de JDK-versie die al door andere toepassingen op de computer wordt gebruikt.
>  
>Wanneer het installeren, wordt u niet vereist om de integratie met browsers van het Web uit te voeren.
>
>Op een computer die alleen leveringsagents (**nlserver mta** -proces) of de workflowserver (**nlserver wfserver** -proces) uitvoert, is het installeren van een JDK niet nodig.

Als u Java JDK wilt downloaden, maakt u verbinding met: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Waarschuwing: u moet een JDK downloaden, niet een JRE.**

>[!CAUTION]
>
>Als u de prestaties van het platform wilt behouden en compatibiliteit met de geïnstalleerde versie wilt garanderen, moet u de automatische JDK-updatefuncties in Windows en Linux uitschakelen.

Als u de JDSL in een Linux-omgeving wilt installeren, kunt u het beste een pakketbeheer gebruiken.

Gebruik in Debian 8 en 9 de volgende opdracht:

```
aptitude install openjdk-8-jdk
```

Gebruik voor RHEL 7 de volgende opdracht:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

In Linux moet OpenSSL zijn geïnstalleerd. De versies die worden ondersteund door Adobe Campaign zijn **OpenSSL 1.0.1** en **OpenSSL 0.9.8**. Subversies 0.9.8g tot en met 0.9.8o worden geaccepteerd.

## Rapporten exporteren {#exporting-reports}

Met Adobe Campaign kunt u platformrapporten exporteren in Microsoft Excel- en Adobe PDF-indeling. Voor de indeling Microsoft Excel gebruikt Adobe Campaign **LibreOffice**. Voor de Adobe PDF-indeling gebruikt Adobe Campaign de **PhantomJS** -converter. PhantomJs is opgenomen in het fabriekspakket en LibreOffice moet zijn geïnstalleerd op de computer(s) waarop de Adobe Campagne-toepassingsserver wordt uitgevoerd (**nlserver webproces** ).

>[!NOTE]
>
>Voor Linux moet u lettertypen toevoegen. Raadpleeg [Lettertypen voor MTA-statistieken](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)voor meer informatie hierover.

## SpamAssassin {#spamassassin}

Met SpamAssassin kunt u een score toewijzen aan e-mails om te bepalen of een bericht als ongewenst kan worden beschouwd door anti-spamgereedschappen die worden gebruikt bij de ontvangst. Installatie is optioneel.

De kwalificatie van e-mails als ongewenst door SpamAssassin is volledig gebaseerd op filtreer- en scoreregels. Deze regels moeten daarom ten minste eenmaal per dag worden bijgewerkt, zodat uw SpamAssassin-installatie en de integratie ervan in Adobe Campaign volledig functioneel zijn en de relevantie van de scores die aan uw leveringen zijn toegewezen, wordt gegarandeerd voordat deze worden verzonden. Deze update valt onder de verantwoordelijkheid van de serverbeheerder die als host fungeert voor SpamAssassin.

De minimaal ondersteunde versie is: **3,4**

Voor SpamAssassin is HTTP-internettoegang (tcp/80) vereist.

De installatie en de configuratiestadia voor SpamAssassin worden voorgesteld in het [Vormen SpamAssassin](../../installation/using/configuring-spamassassin.md).
