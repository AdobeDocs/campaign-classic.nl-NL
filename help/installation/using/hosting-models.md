---
product: campaign
title: Hostmodellen
description: Campagne-hostmodellen ontdekken
feature: Installation, Architecture, Deployment
role: Developer
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 1%

---

# Hostmodellen{#hosting-models}



Adobe Campaign biedt een keuze uit drie hostingmodellen, die flexibiliteit en vrijheid bieden om het beste model te kiezen of modellen die aan de zakelijke behoeften voldoen.

>[!NOTE]
>
>Voor door Adobe gehoste omgevingen kunnen de hoofdinstallatie- en configuratiestappen alleen door Adobe worden uitgevoerd, zoals het configureren van de server en het aanpassen van configuratiebestanden voor instanties. Meer over de belangrijkste verschillen tussen plaatsingswijzen leren, verwijs naar [&#x200B; deze pagina &#x200B;](../../installation/using/capability-matrix.md).

## Managed Services / Gehost

Adobe Campaign kan worden geïmplementeerd as a Managed Service: alle componenten van Adobe Campaign, inclusief de gebruikersinterface, de uitvoeringsbeheerengine en de Campagne-database van de klant, worden volledig gehost door Adobe, inclusief e-mailuitvoering, spiegelpagina&#39;s, trackingserver en naar buiten wijzende webcomponenten, zoals het afmelden van pagina&#39;s/voorkeurscentrum en bestemmingspagina&#39;s.

![](assets/deployment_hosted.png)

Als gehoste klant worden de meeste installatie- en configuratiestappen uitgevoerd door Adobe. U kunt de volgende secties openen om uw implementatie aan te passen:

* Configureer URL&#39;s voor bijhouden en spiegelen per merk. Voor transactionele berichten, verwijs [&#x200B; naar deze sectie &#x200B;](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Installeer de cliëntconsole: verwijs [&#x200B; naar deze sectie &#x200B;](../../installation/using/installing-the-client-console.md).
* Leer meer op de de plaatsingshulpmiddelen en beste praktijken door de [&#x200B; gedetailleerde documentatie &#x200B;](../../delivery/using/about-deliverability.md) te lezen.
* Vorm de opties van de Campagne: verwijs [&#x200B; naar deze sectie &#x200B;](../../installation/using/configuring-campaign-options.md).
* Vorm de schakelaars van CRM: verwijs [&#x200B; naar deze sectie &#x200B;](../../platform/using/crm-connectors.md).

## Op locatie

Adobe Campaign kan op locatie worden geïmplementeerd: alle onderdelen van Adobe Campaign, inclusief de gebruikersinterface, de uitvoeringsbeheerengine en de database, bevinden zich op locatie in het datacenter van de klant. In dit implementatiemodel beheert de klant alle software- en hardwareupdates en -upgrades en moet een specifieke databasebeheerder onderhouds- en optimalisatietaken uitvoeren om te zorgen voor het beheer van de campagneinstantie.

![](assets/deployment_onpremise.png)

Als klant op locatie, voordat u begint met het implementeren van Campaign Classic, dient u de volgende voorwaarden en aanbevelingen in acht te nemen:

* Lees uit de [&#x200B; matrijs van de Verenigbaarheid &#x200B;](../../rn/using/compatibility-matrix.md) die van alle versies van de systemen en componenten een lijst maakt die voor Adobe Campaign worden gesteund.
* Afhankelijk van uw milieu, lees de [&#x200B; eerste vereisten voor Vensters &#x200B;](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) en [&#x200B; eerste vereisten voor Linux &#x200B;](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) uit.
* Leer aanbevelingen met betrekking tot gegevensbestandmotoren [&#x200B; in deze sectie &#x200B;](../../installation/using/database.md).
* Controleer of de vereiste databasetoegangslagen op de server zijn geïnstalleerd en toegankelijk zijn vanaf de Adobe Campaign-account. [Meer informatie](../../installation/using/application-server.md).
* Vorm uw netwerken aangezien sommige processen met anderen moeten communiceren of tot LAN en Internet toegang hebben. Dit betekent dat sommige havens van TCP voor deze processen open moeten zijn. [&#x200B; leer meer &#x200B;](../../installation/using/network-configuration.md) over de configuratievereisten van het Netwerk.
* Lees uit [&#x200B; checklist van de Veiligheid van de Campagne en van de Privacy &#x200B;](https://helpx.adobe.com/nl/campaign/kb/acc-security.html).
* Controle algemene richtlijnen voor het schatten van hardwarevereisten voor plaatsing op locatie [&#x200B; in dit artikel &#x200B;](https://helpx.adobe.com/nl/campaign/kb/hardware-sizing-guide.html).

## Hybride

Bij implementatie als hybride model bevindt de Adobe Campaign-oplossingssoftware zich op locatie op de locatie van de klant en wordt het uitvoeringsbeheer door Adobe als cloudservice geleverd. Het Adobe Campaign-marketingexemplaar wordt geïnstalleerd in de firewall van een klant. Persoonlijke identificeerbare informatie (PII) blijft dus intern en alleen gegevens die nodig zijn om e-mails aan uw persoonlijke wensen aan te passen worden naar de cloud verzonden voor e-mailuitvoering. De uitvoeringsinstantie, gehost in de cloud, ontvangt de verzoeken van de On-premise instantie om e-mails te verzenden. Dit exemplaar personaliseert alle e-mails en levert hen. Geen enkel gegeven wordt permanent opgeslagen in de cloud.

![](assets/deployment_hybrid.png)

Als hybride klant worden de meeste installatie- en configuratiestappen uitgevoerd door Adobe. U kunt de volgende secties openen om uw implementatie aan te passen:

* Vorm transactionele berichten: verwijs [&#x200B; naar deze sectie &#x200B;](../../message-center/using/transactional-messaging-architecture.md).
* Configureer URL&#39;s voor bijhouden en spiegelen per merk. Voor transactionele berichten, verwijs [&#x200B; naar deze sectie &#x200B;](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Installeer de cliëntconsole: verwijs [&#x200B; naar deze sectie &#x200B;](../../installation/using/installing-the-client-console.md).
* Installeer ingebouwde pakketten: verwijs [&#x200B; naar deze sectie &#x200B;](../../installation/using/installing-campaign-standard-packages.md).
* Leverbaarheid: vorm [&#x200B; MX regels &#x200B;](../../installation/using/email-deliverability.md#mx-configuration) en [&#x200B; e-mailformaten &#x200B;](../../installation/using/email-deliverability.md#managing-email-formats). Leer meer op de de plaatsingshulpmiddelen en beste praktijken door de [&#x200B; gedetailleerde documentatie &#x200B;](../../delivery/using/about-deliverability.md) te lezen.
* Vorm de opties van de Campagne: verwijs [&#x200B; naar deze sectie &#x200B;](../../installation/using/configuring-campaign-options.md).
* Vorm een extern gegevensbestand (Federated Toegang van Gegevens): verwijs [&#x200B; naar deze sectie &#x200B;](../../installation/using/about-fda.md).
* Het vormen de schakelaars van CRM: verwijs [&#x200B; naar deze sectie &#x200B;](../../platform/using/crm-connectors.md).
* Om meer op midsourcingplaatsingsprincipes te leren, verwijs [&#x200B; naar deze sectie &#x200B;](../../installation/using/mid-sourcing-deployment.md).
