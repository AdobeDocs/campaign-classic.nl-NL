---
product: campaign
title: Applicatieserver
description: Applicatieserver
feature: Installation
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 1%

---

# Applicatieserver{#application-server}



De vereiste databasetoegangslagen moeten op de server zijn geïnstalleerd en toegankelijk zijn vanaf de Adobe Campaign-account.

## Java Development Kit - JDK {#java-development-kit---jdk}

De dynamische generator van de Web-pagina gebruikt JSP 1.2 technologie. Hiervoor wordt een Tomcat-engine (van Apache) in de toepassing opgenomen. Hiervoor is een JDK (Java Development Kit) vereist die is geïnstalleerd op alle servers waarop de Adobe Campaign-toepassing is geïnstalleerd.

U moet eerst een JDK installeren op de computers waarop u de Adobe Campaign-toepassingsserver wilt uitvoeren (**nlserver-web** proces) omdat het een servletcontainer, Apache Tomcat, opneemt die wordt gebruikt om dynamische Web-pagina&#39;s (rapporten, de vormen van het Web, enz.) te produceren.

De aanvraag is goedgekeurd voor de Java Development Kit (JDK) die door Oracle is ontwikkeld en voor **OpenJDK**.

De ondersteunde versies worden gedetailleerd weergegeven in de campagne [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>De toepassing kan worden geïnstalleerd met de JDK-versie die al door andere toepassingen op de computer wordt gebruikt.
>  
>Wanneer het installeren, wordt u niet vereist om de integratie met browsers van het Web uit te voeren.
>
>Op een machine die alleen leveringsagenten uitvoert (**nlserver-mta** proces) of de workflowserver (**nlserver wfserver** -proces), is het installeren van een JDK niet nodig.

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

In Linux moet OpenSSL zijn geïnstalleerd. Adobe Campaign ondersteunt OpenSSL versie 1.0.2 of hoger.

## Rapporten exporteren {#exporting-reports}

Met Adobe Campaign kunt u platformrapporten exporteren in Microsoft Excel- en Adobe PDF-indeling. Voor de Microsoft Excel-indeling gebruikt Adobe Campaign **LibreOffice**. Voor de Adobe PDF-indeling gebruikt Adobe Campaign de **PhantomJS** converter. PhantomJs is opgenomen in het fabriekspakket en LibreOffice moet zijn geïnstalleerd op de computer(s) waarop de Adobe Campaign-toepassingsserver wordt uitgevoerd (**nlserver-web** proces).

>[!NOTE]
>
>Voor Linux moet u lettertypen toevoegen. Raadpleeg voor meer informatie hierover [Lettertypen voor MTA-statistieken](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

Met SpamAssassin kunt u een score toewijzen aan e-mails om te bepalen of een bericht als ongewenst kan worden beschouwd door anti-spamgereedschappen die worden gebruikt bij de ontvangst. Installatie is optioneel.

De kwalificatie van e-mails als ongewenst door SpamAssassin is volledig gebaseerd op filtreer- en scoreregels. Deze regels moeten daarom ten minste eenmaal per dag worden bijgewerkt om ervoor te zorgen dat uw SpamAssassin-installatie en de integratie ervan in Adobe Campaign volledig functioneel zijn en dat de relevantie van de scores die aan uw leveringen zijn toegekend, wordt gegarandeerd voordat deze worden verzonden. Deze update valt onder de verantwoordelijkheid van de serverbeheerder die als host fungeert voor SpamAssassin.

De minimaal ondersteunde versie is: **3,4**

Voor SpamAssassin is HTTP-internettoegang (tcp/80) vereist.

De installatie en configuratiestadia voor SpamAssassin worden voorgesteld in [SpamAssassin configureren](../../installation/using/configuring-spamassassin.md).
