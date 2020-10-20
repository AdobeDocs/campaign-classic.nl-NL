---
title: Hostmodellen
description: Hostmodellen
page-status-flag: never-activated
uuid: a9e035d9-326b-4e14-8f05-a22fe38d172b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 3175b9ab-e305-4f19-8267-d6172fa07a2a
translation-type: tm+mt
source-git-commit: c03e90b2e2f57606749c86cda343ce5756fec122
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 3%

---


# Hostmodellen{#hosting-models}

Adobe Campaign biedt een keuze uit drie hostingmodellen, die flexibiliteit en vrijheid bieden om het beste model te kiezen of modellen die aan de zakelijke behoeften voldoen.

>[!NOTE]
>
>Voor op Adobe gehoste omgevingen kunnen de hoofdinstallatie- en configuratiestappen alleen worden uitgevoerd door Adobe, zoals het configureren van de server en het aanpassen van configuratiebestanden voor instanties. Meer over de belangrijkste verschillen tussen plaatsingswijzen leren, verwijs naar [dit artikel](https://helpx.adobe.com/nl/campaign/kb/acc-on-prem-vs-hosted.html).

* **Managed Services (gehost)**

   Adobe Campaign kan worden geïmplementeerd als een beheerde service: alle componenten van Adobe Campaign, inclusief de gebruikersinterface, de uitvoeringsbeheerengine en de Campagne-database van de klant, worden volledig gehost door Adobe, zoals het uitvoeren van e-mail, het spiegelen van pagina&#39;s, de trackingserver en extern opvallende webcomponenten, zoals het afmelden van pagina&#39;s/voorkeurscentrum en bestemmingspagina&#39;s. Adobe wijst maximaal drie instanties toe in de cloud: ontwikkeling, test/werkgebied en productie. De installatie- en configuratiestappen voor dit hostmodel worden [in deze sectie](../../installation/using/hosted-model.md)weergegeven.

   ![](assets/deployment_hosted.png)

* **Op locatie**

   Adobe Campaign kan op locatie worden geïmplementeerd: alle onderdelen van Adobe Campaign, inclusief de gebruikersinterface, de uitvoeringsbeheerengine en de database, bevinden zich ter plaatse in het datacenter van de klant. In dit implementatiemodel beheert de klant alle software- en hardwareupdates en -upgrades en moet een specifieke databasebeheerder onderhouds- en optimalisatietaken uitvoeren om te zorgen voor het beheer van de campagneinstantie. De richtlijnen van de plaatsing voor on-premise klanten worden voorgesteld [in deze sectie](../../installation/using/before-starting.md).

   ![](assets/deployment_onpremise.png)

* **Hybride**

   Wanneer de Adobe Campaign-oplossingssoftware als hybride model wordt geïmplementeerd, bevindt deze zich op locatie op de locatie van de klant en wordt het uitvoeringsbeheer als cloudservice geleverd door Adobe. Het Adobe Campaign-marketingexemplaar wordt geïnstalleerd in de firewall van een klant. Persoonlijke identificeerbare informatie (PII) blijft dus intern en alleen gegevens die nodig zijn om e-mails aan uw persoonlijke wensen aan te passen worden naar de cloud verzonden voor e-mailuitvoering. De uitvoeringsinstantie, gehost in de cloud, ontvangt de verzoeken van de instantie Op locatie om e-mails te verzenden. Dit exemplaar personaliseert alle e-mails en levert hen. Geen enkel gegeven wordt permanent opgeslagen in de cloud. De installatie- en configuratiestappen voor dit hostmodel worden [in deze sectie](../../installation/using/hybrid-model.md)weergegeven.

   ![](assets/deployment_hybrid.png)

