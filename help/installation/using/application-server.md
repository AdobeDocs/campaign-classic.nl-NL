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
source-git-commit: 7906e9fee164d731659bbb9f96394faca5961240
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 1%

---

# Applicatieserver{#application-server}

De vereiste databasetoegangslagen moeten op de server zijn geïnstalleerd en toegankelijk zijn vanaf de Adobe Campaign-account.

## Java Development Kit - JDK {#jdk}

Java Development Kit (JDK) is een software-ontwikkelingskit. Het is de basiscomponent die de ontwikkeling van Java-toepassingen en Java-applets mogelijk maakt.

De dynamische generator van de Web-pagina gebruikt technologie JSP. Hiervoor wordt een Tomcat-engine (van Apache) in de toepassing opgenomen. Hiervoor is een JDK (Java Development Kit) vereist die is geïnstalleerd op alle servers waarop de Adobe Campaign-toepassing is geïnstalleerd.

U moet eerst een JDK op de computers installeren waarop u wenst om de de toepassingsserver van Adobe Campaign in werking te stellen (**proces van het 0} nlserverWeb {) omdat het een servletcontainer, Apache Tomcat opneemt, die wordt gebruikt om dynamische Web-pagina&#39;s (rapporten, de vormen van het Web, enz.) te produceren.**

De toepassing is goedgekeurd voor de Uitrusting van de Ontwikkeling van Java (JDK) die door Oracle evenals voor **wordt ontwikkeld OpenJDK**.

De gesteunde versies zijn gedetailleerd in de matrijs van de Verenigbaarheid van de Campagne [ ](../../rn/using/compatibility-matrix.md).


>[!AVAILABILITY]
>
>* Vanaf v7.4.1 vereist campagne ten minste Java JDK 11. Als uw Campagneserver in een milieu van Vensters geïnstalleerd is, moet u JRE produceren aangezien het niet meer door gebrek wordt verstrekt. De JRE_HOME-omgevingsvariabele is vereist om de Java-runtime DLL (jvm.dll) te vinden.
>
>* Vanaf v7.4.1 is Tomcat 10.1 de standaardversie.
>

### Aanbevelingen

Pas de volgende aanbevelingen toe wanneer u uw Java Development Kit installeert en bijwerkt:

* Java Development Kit kan worden geïnstalleerd met de JDK-versie die hiervoor geschikt is en die al door andere toepassingen op de computer wordt gebruikt.

* Wanneer het installeren van JDK, wordt de integratie met browsers van het Web niet vereist.

* Op een machine die slechts leveringsagenten (**nlserver mta** proces) of de werkschemaserver (**nlserver wfserver** proces) uitvoert, wordt het installeren van JDK niet vereist.

* Wanneer u uw Java-versie upgradet, moet u eerst de vorige versie verwijderen. Beide versies van Java die op dezelfde computer zijn geïnstalleerd, kunnen conflicten veroorzaken.

  Als klant On-premise, kunt u `LD_LIBRARY_PATH` controleren [ milieu veranderlijke ](installing-packages-with-linux.md#environment-variables) wordt geplaatst aan de recentste versie (bijvoorbeeld. java11). Als deze op een vorige versie is ingesteld (bijvoorbeeld Java8), dan moet het worden bijgewerkt. Voor JDK 11 is het pad naar JDK-bibliotheken `/usr/lib/jvm/java-11-openjdk-amd64/lib` .


### Installatiestappen

Java Development Kit is platformspecifiek: voor elk besturingssysteem zijn afzonderlijke installatieprogramma&#39;s nodig.

Om JDK te downloaden, verbind met [ website van het Oracle ](https://www.oracle.com/technetwork/java/javase/downloads/index.html) {target="_blank"}.

>[!CAUTION]
>
> Zorg ervoor dat u een JDK (Java Development Kit) downloadt, geen JRE (Java Runtime Environment).


Om JDSL in een milieu van Linux te installeren, adviseert de Adobe om een pakketmanager te gebruiken.

Gebruik voor Debian de volgende opdracht:

```sql
apt install openjdk-11-jdk-headless
```

Gebruik voor RHEL de volgende opdracht:

```sql
dnf install java-11-openjdk-headless
```



## Rapporten exporteren {#exporting-reports}

Met Adobe Campaign kunt u rapporten exporteren naar Microsoft Excel en Adobe PDF.

* Voor het formaat van Microsoft Excel, vertrouwt Adobe Campaign op **LibreOffice**.

* Voor het formaat van Adobe PDF, gebruikt Adobe Campaign **PhantomJS** converter. PhantomJs is inbegrepen in het fabriekspakket en LibreOffice moet op de machine(s) worden geïnstalleerd die de de toepassingsserver van Adobe Campaign (**nlserverWeb** proces) wordt uitgevoerd.

>[!NOTE]
>
>Voor Linux moet u lettertypen toevoegen. Voor meer op dit, verwijs naar [ Doopvonten voor MTA statistieken ](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

Met SpamAssassin kunt u een score toewijzen aan e-mails om te bepalen of een bericht als ongewenst kan worden beschouwd door anti-spamgereedschappen die worden gebruikt bij de ontvangst. Installatie is optioneel.

De kwalificatie van e-mails als ongewenst door SpamAssassin is volledig gebaseerd op filtreer- en scoreregels. Deze regels moeten daarom ten minste eenmaal per dag worden bijgewerkt om ervoor te zorgen dat uw SpamAssassin-installatie en de integratie ervan in Adobe Campaign volledig functioneel zijn en dat de relevantie van de scores die aan uw leveringen zijn toegekend, wordt gegarandeerd voordat deze worden verzonden. Deze update valt onder de verantwoordelijkheid van de serverbeheerder die als host fungeert voor SpamAssassin.

De minimum gesteunde versie is: **3.4**

Voor SpamAssassin is HTTP-internettoegang (tcp/80) vereist.

De installatie en de configuratiestadia voor SpamAssassin worden voorgesteld in [ het Vormen SpamAssassin ](../../installation/using/configuring-spamassassin.md).
