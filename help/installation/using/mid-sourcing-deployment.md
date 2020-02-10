---
title: Implementatie van midsourcing
seo-title: Implementatie van midsourcing
description: Implementatie van midsourcing
seo-description: null
page-status-flag: never-activated
uuid: e359c486-7ee6-4295-80fc-4c371a0ef068
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 19220d8e-9494-46b4-9aa0-4c4a729aea96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Implementatie van midsourcing{#mid-sourcing-deployment}

Deze configuratie is een optimale middenoplossing tussen een ontvangen (ASP) configuratie en internalisering. De naar buiten gerichte uitvoeringscomponenten worden uitgevoerd op een &quot;mid-sourcing&quot;-server die wordt gehost in Adobe Campaign.

>[!NOTE]
>
>Als u dit type implementatie wilt instellen, moet u de juiste optie kiezen. Controleer uw licentieovereenkomst.

De algemene communicatie tussen servers en processen wordt uitgevoerd volgens het volgende schema:

![](assets/s_ncs_install_midsourcing.png)

* De uitvoerings en stuitbeheersmodules zijn onbruikbaar gemaakt op de instantie.
* De toepassing wordt gevormd om berichtuitvoering op een verre &quot;midsourced&quot;server uit te voeren die gebruikend de vraag van de ZEEP (over HTTP of HTTPS) wordt gedreven.

## Functies {#features}

### Voordelen {#advantages}

* Vereenvoudigde serverconfiguratie: Het is niet noodzakelijk voor de klant om naar buiten gerichte modules (mta en inMail) te vormen.
* Beperkt gebruik van bandbreedte: Aangezien de uitvoering wordt uitgevoerd door de server voor midsourcing, is alleen voldoende bandbreedte vereist om aanpassingsgegevens naar de server voor midsourcing te verzenden.
* Hoge beschikbaarheid is niet langer een intern probleem: Het probleem wordt verplaatst naar de server voor midsourcing (omleiding, spiegel, uitvoeringsservers, enz.).
* De database verlaat het bedrijf niet: Alleen de gegevens die nodig zijn voor het samenstellen van de berichten worden naar de server voor midsourcing verzonden (hiervoor kan HTTPS worden gebruikt).
* Dit type van plaatsing kan een oplossing voor hoge volumearchitectuur (vele ontvangers in het gegevensbestand), met een significante leveringsproductie zijn.

### Nadelen {#disadvantages}

* Enige vertraging bij het bekijken van de informatie van de bericht-uitvoering en voor het melden van functionaliteit wegens de tijd het vergt om informatie terug van de midsourcingserver terug te krijgen.
* Enquêtes en webformulieren blijven aanwezig op het clientplatform.

### Aanbevolen apparatuur {#recommended-equipment}

* Toepassingsserver: 2 GHz quad-core CPU, 4 GB RAM, software RAID 1 80 GB SATA harde schijf.
* Databaseserver: 3 GHz bi-quad core CPU&#39;s, minimaal 4 GB RAM, hardware RAID 10 1.5.000 RPM SAS harde schijf, het aantal afhankelijk van de grootte en de verwachte prestaties van de database.

>[!NOTE]
>
>Omleiding en midsourcing zijn afzonderlijke elementen, maar de trackingserver wordt over het algemeen gedeeld met de mid-sourcingservers.

## Installatie- en configuratiestappen {#installation-and-configuration-steps-}

### Vereisten {#prerequisites}

* JDK op de toepassingsserver.
* Toegang tot een databaseserver op de toepassingsserver.
* Firewall geconfigureerd voor het openen van HTTP- (80) of HTTPS-poorten (443) naar de server voor midsourcing.

### Installeren en configureren (implementatie van midsourcing) {#installing-and-configuring--mid-sourcing-deployment-}

Raadpleeg de [server](../../installation/using/mid-sourcing-server.md)voor midsourcing.
