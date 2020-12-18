---
solution: Campaign Classic
product: campaign
title: Applicatieserver
description: Applicatieserver
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 1%

---


# Applicatieserver{#application-server}

De vereiste databasetoegangslagen moeten op de server zijn geïnstalleerd en toegankelijk zijn vanaf de Adobe Campaign-account.

## Java Development Kit - JDK {#java-development-kit---jdk}

De dynamische generator van de Web-pagina gebruikt JSP 1.2 technologie. Hiervoor wordt een Tomcat-engine (van Apache) in de toepassing opgenomen. Hiervoor is een JDK (Java Development Kit) vereist die is geïnstalleerd op alle servers waarop de Adobe Campaign-toepassing is geïnstalleerd.

U moet eerst een JDK installeren op de computers waarop u de Adobe Campaign-toepassingsserver wilt uitvoeren (**nlserver web** proces) omdat het een servletcontainer bevat, Apache Tomcat, die wordt gebruikt om dynamische webpagina&#39;s te genereren (rapporten, webformulieren, enz.).

De toepassing is goedgekeurd voor de Java Development Kit (JDK) die is ontwikkeld door Oracle en voor **OpenJDK**.

De ondersteunde versies zijn gedetailleerd in de campagne [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>De toepassing kan worden geïnstalleerd met de JDK-versie die al door andere toepassingen op de computer wordt gebruikt.
>  
>Wanneer het installeren, wordt u niet vereist om de integratie met browsers van het Web uit te voeren.
>
>Op een computer die alleen leveringsagenten (**nlserver mta** proces) of de werkschemaserver (**nlserver wfserver** proces) uitvoert, is het installeren van een JDK niet noodzakelijk.

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

In Linux moet OpenSSL zijn geïnstalleerd. De door Adobe Campaign ondersteunde versies zijn **OpenSSL 1.0.1** en **OpenSSL 0.9.8**. Subversies 0.9.8g tot en met 0.9.8o worden geaccepteerd.

## Rapporten exporteren {#exporting-reports}

Met Adobe Campaign kunt u platformrapporten exporteren in Microsoft Excel- en Adobe PDF-indeling. Voor het formaat van Microsoft Excel, gebruikt Adobe Campaign **LibreOffice**. Voor de Adobe PDF-indeling gebruikt Adobe Campaign de converter **PhantomJS**. PhantomJs is inbegrepen in het fabriekspakket en LibreOffice moet op de machine(s) worden geïnstalleerd die de Adobe Campaign toepassingsserver op (**nlserver web** proces) wordt uitgevoerd.

>[!NOTE]
>
>Voor Linux moet u lettertypen toevoegen. Raadpleeg [Lettertypen voor MTA-statistieken](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics) voor meer informatie.

## SpamAssassin {#spamassassin}

Met SpamAssassin kunt u een score toewijzen aan e-mails om te bepalen of een bericht als ongewenst kan worden beschouwd door anti-spamgereedschappen die worden gebruikt bij de ontvangst. Installatie is optioneel.

De kwalificatie van e-mails als ongewenst door SpamAssassin is volledig gebaseerd op filtreer- en scoreregels. Deze regels moeten daarom ten minste eenmaal per dag worden bijgewerkt om ervoor te zorgen dat uw SpamAssassin-installatie en de integratie ervan in Adobe Campaign volledig functioneel zijn en dat de relevantie van de scores die aan uw leveringen zijn toegekend, wordt gegarandeerd voordat deze worden verzonden. Deze update valt onder de verantwoordelijkheid van de serverbeheerder die als host fungeert voor SpamAssassin.

De minimaal ondersteunde versie is: **3.4**

Voor SpamAssassin is HTTP-internettoegang (tcp/80) vereist.

De installatie en de configuratiestadia voor SpamAssassin worden voorgesteld in [het Vormen SpamAssassin](../../installation/using/configuring-spamassassin.md).
