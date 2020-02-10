---
title: Hostmodellen
seo-title: Hostmodellen
description: Hostmodellen
seo-description: null
page-status-flag: never-activated
uuid: a9e035d9-326b-4e14-8f05-a22fe38d172b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 3175b9ab-e305-4f19-8267-d6172fa07a2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Hostmodellen{#hosting-models}

Adobe Campagne biedt een keuze uit drie hostingmodellen, die flexibiliteit en vrijheid bieden om het beste model of modellen te kiezen die aan uw bedrijfsbehoeften voldoen.

>[!NOTE]
>
>De belangrijkste installatie- en configuratiestappen kunnen alleen door Adobe worden uitgevoerd voor implementaties die worden gehost door Adobe. Bijvoorbeeld, om de server en de dossiers van de instantieconfiguratie te vormen. Meer over de belangrijkste verschillen tussen plaatsingswijzen leren, verwijs naar [dit artikel](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html). Als u een gehost of hybride model hebt, raadpleegt u deze [sectie](../../installation/using/about-hybrid-and-hosted-models.md).

* **Beheerde services (gehost)**

   De Campagne van Adobe kan als Beheerde Dienst worden opgesteld: Alle componenten van Adobe Campaign, inclusief de gebruikersinterface, de uitvoeringsbeheerengine en de Campagne-database van de klant, worden volledig door Adobe gehost, inclusief het uitvoeren van e-mail, het spiegelen van pagina&#39;s, de trackingserver en extern opvallende webcomponenten, zoals het afmelden van pagina&#39;s/voorkeurscentrum en bestemmingspagina&#39;s. Adobe wijst maximaal drie instanties toe in de cloud: ontwikkeling, test/werkgebied en productie. De installatie- en configuratiestappen voor dit hostmodel worden in deze [sectie](../../installation/using/hosted-model.md)weergegeven.

   ![](assets/deployment_hosted.png)

* **Op locatie**

   Adobe-campagne kan op locatie worden geïmplementeerd: alle componenten van Adobe Campaign, inclusief de gebruikersinterface, de uitvoeringsbeheerengine en de database, bevinden zich ter plaatse in het datacenter van de klant. In dit implementatiemodel beheert de klant alle software- en hardwareupdates en -upgrades en moet een specifieke databasebeheerder onderhouds- en optimalisatietaken uitvoeren om te zorgen voor het beheer van de campagneinstantie.

   ![](assets/deployment_onpremise.png)

* **Hybride**

   Wanneer de Adobe Campaign-software wordt geïmplementeerd als een hybride model, bevindt deze zich op locatie op de locatie van de klant en wordt het uitvoeringsbeheer door Adobe als cloudservice geleverd. De marketinginstantie van Adobe Campagne is geïnstalleerd in de firewall van een klant. Persoonlijke identificeerbare informatie (PII) blijft dus intern en alleen de gegevens die nodig zijn om e-mails aan uw persoonlijke wensen aan te passen worden naar de cloud verzonden voor e-mailuitvoering. De uitvoeringsinstantie, gehost in de cloud, ontvangt de verzoeken van de instantie Op locatie om e-mails te verzenden. Dit exemplaar personaliseert alle e-mails en levert hen. Geen enkel gegeven wordt permanent opgeslagen in de cloud. De installatie- en configuratiestappen voor dit hostmodel worden in deze [sectie](../../installation/using/hybrid-model.md)weergegeven.

   ![](assets/deployment_hybrid.png)

