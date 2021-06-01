---
solution: Campaign Classic
product: campaign
title: Hostmodellen
description: Campagne-hostmodellen ontdekken
feature: Overzicht
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: 54d503e97a4374927c4ebe3ba4e0ec05e51d47db
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 2%

---

# Hostmodellen{#hosting-models}

Adobe Campaign biedt een keuze uit drie hostingmodellen, die flexibiliteit en vrijheid bieden om het beste model te kiezen of modellen die aan de zakelijke behoeften voldoen.

>[!NOTE]
>
>Voor op Adobe gehoste omgevingen kunnen de hoofdinstallatie- en configuratiestappen alleen worden uitgevoerd door Adobe, zoals het configureren van de server en het aanpassen van configuratiebestanden voor instanties. Raadpleeg [deze pagina](../../installation/using/capability-matrix.md) voor meer informatie over de belangrijkste verschillen tussen de implementatiemodi.

## Managed Services / Gehost

Adobe Campaign kan worden geïmplementeerd als een beheerde service: alle componenten van Adobe Campaign, inclusief de gebruikersinterface, de uitvoeringsbeheerengine en de Campagne-database van de klant, worden volledig gehost door Adobe, zoals het uitvoeren van e-mail, het spiegelen van pagina&#39;s, de trackingserver en extern opvallende webcomponenten, zoals het afmelden van pagina&#39;s/voorkeurscentrum en bestemmingspagina&#39;s.

![](assets/deployment_hosted.png)

Als ontvangen klant, worden de meeste installatie en configuratiestappen uitgevoerd door Adobe. U kunt de volgende secties openen om uw implementatie aan te passen:

* Configureer URL&#39;s voor bijhouden en spiegelen per merk. Raadpleeg [voor transactieberichten deze sectie](../../message-center/using/additional-configurations.md#configuring-multibranding).
* De clientconsole installeren: zie [deze sectie](../../installation/using/installing-the-client-console.md).
* Lees voor meer informatie over de gereedschappen en de aanbevolen procedures voor de levering de [gedetailleerde documentatie](../../delivery/using/about-deliverability.md).
* Campagneopties configureren: zie [deze sectie](../../installation/using/configuring-campaign-options.md).
* CRM-connectors configureren: zie [deze sectie](../../platform/using/crm-connectors.md).

## Op locatie

Adobe Campaign kan op locatie worden geïmplementeerd: alle onderdelen van Adobe Campaign, inclusief de gebruikersinterface, de uitvoeringsbeheerengine en de database, bevinden zich ter plaatse in het datacenter van de klant. In dit implementatiemodel beheert de klant alle software- en hardwareupdates en -upgrades en moet een specifieke databasebeheerder onderhouds- en optimalisatietaken uitvoeren om te zorgen voor het beheer van de campagneinstantie.

![](assets/deployment_onpremise.png)

Als klant op locatie, alvorens te beginnen met het implementeren van Campaign Classic, zorg dan voor de volgende voorwaarden en aanbevelingen:

* Lees de [Compatibility matrix](../../rn/using/compatibility-matrix.md) die alle versies van de systemen en componenten bevat die voor Adobe Campaign worden ondersteund.
* Afhankelijk van uw milieu, lees uit [eerste vereisten voor Vensters ](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) en [eerste vereisten voor Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* Leer aanbevelingen met betrekking tot gegevensbestandmotoren [in deze sectie](../../installation/using/database.md).
* Controleer of de vereiste databasetoegangslagen op de server zijn geïnstalleerd en toegankelijk zijn vanaf de Adobe Campaign-account. [Meer informatie](../../installation/using/application-server.md).
* Vorm uw netwerken aangezien sommige processen met anderen moeten communiceren of tot LAN en Internet toegang hebben. Dit betekent dat sommige havens van TCP voor deze processen open moeten zijn. [Leer ](../../installation/using/network-configuration.md) meer over de configuratievereisten van het Netwerk.
* Lees [Controlelijst voor beveiliging en privacy van campagne](https://helpx.adobe.com/nl/campaign/kb/acc-security.html).
* Raadpleeg de algemene richtlijnen voor het schatten van de hardwarevereisten voor on-premise implementatie [in dit artikel](https://helpx.adobe.com/nl/campaign/kb/hardware-sizing-guide.html).

## Hybride

Wanneer de Adobe Campaign-oplossingssoftware als hybride model wordt geïmplementeerd, bevindt deze zich op locatie op de locatie van de klant en wordt het uitvoeringsbeheer als cloudservice geleverd door Adobe. Het Adobe Campaign-marketingexemplaar wordt geïnstalleerd in de firewall van een klant. Persoonlijke identificeerbare informatie (PII) blijft dus intern en alleen gegevens die nodig zijn om e-mails aan uw persoonlijke wensen aan te passen worden naar de cloud verzonden voor e-mailuitvoering. De uitvoeringsinstantie, gehost in de cloud, ontvangt de verzoeken van de instantie Op locatie om e-mails te verzenden. Dit exemplaar personaliseert alle e-mails en levert hen. Geen enkel gegeven wordt permanent opgeslagen in de cloud.

![](assets/deployment_hybrid.png)

Als hybride klant, worden de meeste installatie en configuratiestappen uitgevoerd door Adobe. U kunt de volgende secties openen om uw implementatie aan te passen:

* Transactieberichten configureren: zie [deze sectie](../../message-center/using/transactional-messaging-architecture.md).
* Configureer URL&#39;s voor bijhouden en spiegelen per merk. Raadpleeg [voor transactieberichten deze sectie](../../message-center/using/additional-configurations.md#configuring-multibranding).
* De clientconsole installeren: zie [deze sectie](../../installation/using/installing-the-client-console.md).
* Ingebouwde pakketten installeren: zie [deze sectie](../../installation/using/installing-campaign-standard-packages.md).
* Leverbaarheid: configureren [MX-regels](../../installation/using/email-deliverability.md#mx-configuration) en [e-mailindelingen](../../installation/using/email-deliverability.md#managing-email-formats). Lees voor meer informatie over de gereedschappen en de aanbevolen procedures voor de levering de [gedetailleerde documentatie](../../delivery/using/about-deliverability.md).
* Campagneopties configureren: zie [deze sectie](../../installation/using/configuring-campaign-options.md).
* Een externe database configureren (Federated Data Access): zie [deze sectie](../../installation/using/about-fda.md).
* CRM-connectors configureren: zie [deze sectie](../../platform/using/crm-connectors.md).
* Raadpleeg [deze sectie](../../installation/using/mid-sourcing-deployment.md) voor meer informatie over implementatiebeginselen voor midsourcing.
