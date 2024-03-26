---
product: campaign
title: Midsourcingimplementatie
description: Midsourcingimplementatie
feature: Installation, Architecture, Deployment
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 3%

---

# Midsourcingimplementatie{#mid-sourcing-deployment}



Deze configuratie is een optimale middenoplossing tussen een ontvangen (ASP) configuratie en internalisering. De naar buiten gerichte uitvoeringscomponenten worden uitgevoerd op een &quot;mid-sourcing&quot;-server die wordt gehost op Adobe Campaign.

>[!NOTE]
>
>Als u dit type implementatie wilt instellen, moet u de juiste optie aanschaffen. Controleer uw licentieovereenkomst.

De algemene communicatie tussen servers en processen wordt uitgevoerd volgens het volgende schema:

![](assets/s_ncs_install_midsourcing.png)

* De uitvoerings en stuitbeheersmodules zijn onbruikbaar gemaakt op de instantie.
* De toepassing wordt gevormd om berichtuitvoering op een verre &quot;midsourced&quot;server uit te voeren die gebruikend de vraag van de ZEEP (over HTTP of HTTPS) wordt gedreven.

## Functies {#features}

### Voordelen {#advantages}

* Vereenvoudigde serverconfiguratie: de klant hoeft geen naar buiten gerichte modules (mta en inMail) te configureren.
* Beperkt gebruik van bandbreedte: aangezien de uitvoering wordt uitgevoerd door de server voor midsourcing, is alleen voldoende bandbreedte vereist om aanpassingsgegevens naar de server voor midsourcing te verzenden.
* Hoge beschikbaarheid is niet langer een intern probleem: het probleem wordt verschoven naar de server voor midsourcing (omleiding, spiegel, uitvoeringsservers, enz.).
* De database verlaat het bedrijf niet: hiervoor kunnen alleen gegevens worden gebruikt die nodig zijn voor het samenstellen van de berichten naar de server voor midsourcing (HTTPS).
* Dit type van plaatsing kan een oplossing voor hoge volumearchitectuur (vele ontvangers in het gegevensbestand), met een significante leveringsproductie zijn.

### Nadelen {#disadvantages}

* Enige vertraging bij het bekijken van de informatie van de bericht-uitvoering en voor het melden van functionaliteit wegens de tijd het vergt om informatie terug van de midsourcingserver terug te krijgen.
* Enquêtes en webformulieren blijven aanwezig op het clientplatform.

### Aanbevolen apparatuur {#recommended-equipment}

* Toepassingsserver: 2 GHz quad-core CPU, 4 GB RAM, software RAID 1 80 GB SATA harde schijf.
* Databaseserver: 3 GHz bi-quad core CPU&#39;s, minimaal 4 GB RAM, hardware RAID 10 1.5000 RPM SAS harde schijf, het aantal afhankelijk van de grootte en de verwachte prestaties van de database.

>[!NOTE]
>
>Omleiding en midsourcing zijn afzonderlijke elementen, maar de trackingserver wordt over het algemeen gedeeld met de mid-sourcingservers.

## Installatie- en configuratiestappen {#installation-and-configuration-steps-}

### Vereisten {#prerequisites}

* JDK op de toepassingsserver.
* Toegang tot een databaseserver op de toepassingsserver.
* Firewall geconfigureerd voor het openen van HTTP- (80) of HTTPS-poorten (443) naar de server voor midsourcing.

### Installeren en configureren (implementatie van midsourcing) {#installing-and-configuring--mid-sourcing-deployment-}

Zie [Midden-sourcingserver](../../installation/using/mid-sourcing-server.md).
