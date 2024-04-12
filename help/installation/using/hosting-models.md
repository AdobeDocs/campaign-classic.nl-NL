---
product: campaign
title: Hostmodellen
description: Campagne-hostmodellen ontdekken
feature: Installation, Architecture, Deployment
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Hostmodellen{#hosting-models}



Adobe Campaign biedt een keuze uit drie hostingmodellen, die flexibiliteit en vrijheid bieden om het beste model te kiezen of modellen die aan de zakelijke behoeften voldoen.

>[!NOTE]
>
>Voor Adobe ontvangen milieu&#39;s, kunnen de belangrijkste installatie en configuratiestappen slechts door Adobe worden uitgevoerd, zoals het vormen van de server en het aanpassen van de dossiers van de instantieconfiguratie. Meer over de belangrijkste verschillen tussen plaatsingswijzen leren, verwijs naar [deze pagina](../../installation/using/capability-matrix.md).

## Managed Services / Gehost

Adobe Campaign kan as a Managed Service worden geïmplementeerd: alle componenten van Adobe Campaign, inclusief de gebruikersinterface, de uitvoeringsbeheerengine en de Campagne-database van de klant, worden volledig gehost door Adobe, waaronder het uitvoeren van e-mail, het spiegelen van pagina&#39;s, het bijhouden van de server en naar buiten wijzende webcomponenten, zoals het afmelden van pagina-/voorkeurscentrum en het landen van pagina&#39;s.

![](assets/deployment_hosted.png)

Als ontvangen klant, worden de meeste installatie en configuratiestappen uitgevoerd door Adobe. U kunt de volgende secties openen om uw implementatie aan te passen:

* Configureer URL&#39;s voor bijhouden en spiegelen per merk. Zie voor transactieberichten [aan deze sectie](../../message-center/using/additional-configurations.md#configuring-multibranding).
* De clientconsole installeren: raadpleeg [aan deze sectie](../../installation/using/installing-the-client-console.md).
* Lees voor meer informatie over de gereedschappen en de beste werkwijzen van de leverancier [gedetailleerde documentatie](../../delivery/using/about-deliverability.md).
* Campagneopties configureren: zie [aan deze sectie](../../installation/using/configuring-campaign-options.md).
* CRM-connectors configureren: zie [aan deze sectie](../../platform/using/crm-connectors.md).

## Op locatie

Adobe Campaign kan op locatie worden geïmplementeerd: alle onderdelen van Adobe Campaign, inclusief de gebruikersinterface, de uitvoeringsbeheerengine en de database, bevinden zich op locatie in het datacenter van de klant. In dit implementatiemodel beheert de klant alle software- en hardwareupdates en -upgrades en moet een specifieke databasebeheerder onderhouds- en optimalisatietaken uitvoeren om te zorgen voor het beheer van de campagneinstantie.

![](assets/deployment_onpremise.png)

Als klant op locatie, alvorens met het opstellen van Campaign Classic te beginnen, zorg voor de volgende eerste vereisten en aanbevelingen:

* Lees de [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md) die alle versies bevat van de systemen en componenten die worden ondersteund voor Adobe Campaign.
* Lees de [voorwaarden voor Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) en [voorwaarden voor Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* Meer informatie over databasemotoren [in deze sectie](../../installation/using/database.md).
* Controleer of de vereiste databasetoegangslagen op de server zijn geïnstalleerd en toegankelijk zijn vanaf de Adobe Campaign-account. [Meer informatie](../../installation/using/application-server.md).
* Vorm uw netwerken aangezien sommige processen met anderen moeten communiceren of tot LAN en Internet toegang hebben. Dit betekent dat sommige havens van TCP voor deze processen open moeten zijn. [Meer informatie](../../installation/using/network-configuration.md) over de configuratievereisten van het Netwerk.
* Uitlezen [Checklist Campagne Security and Privacy](https://helpx.adobe.com/nl/campaign/kb/acc-security.html).
* Algemene richtlijnen controleren voor het schatten van hardwarevereisten voor implementatie op locatie [in dit artikel](https://helpx.adobe.com/nl/campaign/kb/hardware-sizing-guide.html).

## Hybride

Wanneer de Adobe Campaign-oplossingssoftware als hybride model wordt geïmplementeerd, bevindt deze zich op locatie op de locatie van de klant en wordt het uitvoeringsbeheer door Adobe als cloudservice geleverd. Het Adobe Campaign-marketingexemplaar wordt geïnstalleerd in de firewall van een klant. Persoonlijke identificeerbare informatie (PII) blijft dus intern en alleen gegevens die nodig zijn om e-mails aan uw persoonlijke wensen aan te passen worden naar de cloud verzonden voor e-mailuitvoering. De uitvoeringsinstantie, gehost in de cloud, ontvangt de verzoeken van de instantie Op locatie om e-mails te verzenden. Dit exemplaar personaliseert alle e-mails en levert hen. Geen enkel gegeven wordt permanent opgeslagen in de cloud.

![](assets/deployment_hybrid.png)

Als hybride klant, worden de meeste installatie en configuratiestappen uitgevoerd door Adobe. U kunt de volgende secties openen om uw implementatie aan te passen:

* Transactieberichten configureren: zie [aan deze sectie](../../message-center/using/transactional-messaging-architecture.md).
* Configureer URL&#39;s voor bijhouden en spiegelen per merk. Zie voor transactieberichten [aan deze sectie](../../message-center/using/additional-configurations.md#configuring-multibranding).
* De clientconsole installeren: raadpleeg [aan deze sectie](../../installation/using/installing-the-client-console.md).
* Ingebouwde pakketten installeren: zie [aan deze sectie](../../installation/using/installing-campaign-standard-packages.md).
* Leverbaarheid: configureren [MX-regels](../../installation/using/email-deliverability.md#mx-configuration) en [e-mailindelingen](../../installation/using/email-deliverability.md#managing-email-formats). Lees voor meer informatie over de gereedschappen en de beste werkwijzen van de leverancier [gedetailleerde documentatie](../../delivery/using/about-deliverability.md).
* Campagneopties configureren: zie [aan deze sectie](../../installation/using/configuring-campaign-options.md).
* Een externe database configureren (Federated Data Access): zie [aan deze sectie](../../installation/using/about-fda.md).
* Bezig met configureren van CRM-connectors: raadpleeg [aan deze sectie](../../platform/using/crm-connectors.md).
* Raadpleeg voor meer informatie over implementatiebeginselen voor midsourcing de [aan deze sectie](../../installation/using/mid-sourcing-deployment.md).
