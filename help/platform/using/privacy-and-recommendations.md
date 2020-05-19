---
title: Privacy en aanbevelingen
seo-title: Privacy en aanbevelingen
description: Privacy en aanbevelingen
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be148d7cd55097b9014d2f4d3b095c65a5ca8c54
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---


# Privacy en aanbevelingen{#privacy-and-recommendations}

## Over privacy en toestemming {#about-privacy-and-consent}

Adobe Campaign is een krachtig hulpmiddel voor het verzamelen en verwerken van zeer grote hoeveelheden gegevens, waaronder persoonlijke gegevens. We moedigen alle gebruikers van Adobe Campaign aan om binnen de wetgeving te werken (DPA, CAN-SPAM, Europese richtlijn over privacy en elektronische communicatie, Europese GDPR, CCPA, enz.), op verantwoorde en ethische wijze gebruik te maken van persoonlijke informatie en af te zien van het verzenden van ongevraagde e-mail, pushberichten en SMS-berichten (&quot;spam&quot;). Wij zijn sterk van mening dat de beginselen van het op de markt brengen van machtigingen de waarde en loyaliteit van de levensduur van de klant bevorderen en daarom verbieden wij het gebruik van Adobe Campaign om ongewenste berichten te verzenden.

Raadpleeg de privacy [van](https://www.adobe.com/privacy/marketing-cloud.html)Adobe Experience Cloud voor meer informatie.

Neem de tijd om door checklist [van de](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html) Veiligheid en van de Privacy te gaan om de belangrijkste elementen te leren om betreffende veiligheid en privacy te controleren.

## Privacybeheer {#privacy-management}

De Campagne van Adobe biedt een reeks hulpmiddelen om u te helpen aan de verordeningen van de Privacy (GDPR, CCPA, en meer.) voldoen.

GDPR (General Data Protection Regulation) is de privacywet van de Europese Unie (EU) die de vereisten inzake gegevensbescherming harmoniseert en moderniseert. GDPR is van toepassing op klanten van de Campagne van Adobe die gegevens voor de Onderwerpen van Gegevens in de EU houden.

CCPA (California Consumer Privacy Act) biedt inwoners van Californië nieuwe rechten met betrekking tot hun persoonlijke gegevens en legt verantwoordelijkheden op het gebied van gegevensbescherming op aan bepaalde entiteiten die zaken doen in Californië.

Naast toestemmingsbeheer, de montages van het gegevensbehoud, en het rechtenbeheer, verstrekken wij, in onze rol als Bewerker van Gegevens, extra mogelijkheden om uw bereidheid als Controlemechanisme van Gegevens voor bepaalde verzoeken van de Privacy te helpen vergemakkelijken.

In [dit artikel](https://helpx.adobe.com/campaign/kb/acc-privacy.html)leert u hoe u met Adobe Campaign de verschillende functies van de privacysleutel kunt beheren: Recht op toegang, recht om te worden vergeten, toestemming, gegevensbewaring en gebruikersrollen. U zult ook beste praktijken vinden, om u met uw naleving van de Privacy te helpen wanneer het gebruiken van onze oplossing.

## Cookies en trackingmogelijkheden {#cookies-and-tracking-capabilities}

Dankzij de trackingfuncties van Adobe Campaign kunt u het bladeren door de ontvangers van de zending op een website volgen. Hiervoor gebruikt Adobe Campaign sessiecookies en permanente cookies.

In de Europese richtlijn 2009/136/EG over &quot;Privacy en elektronische communicatie&quot; en de Europese verordening inzake algemene gegevensbescherming (GDPR) wordt bepaald dat bedrijven de toestemming van webgebruikers nodig hebben voordat zij cookies installeren. U moet gebruikers laten weten dat uw sites zijn uitgerust met webtraceringsprogramma&#39;s via een verzoek om toestemming (bijvoorbeeld via de pagina) met een selectievakje voor het autoriseren van de installatie van cookies, of u moet een banner toevoegen boven aan de eerste pagina waarop ze landen, enzovoort. Pop-upvensters moeten worden vermeden omdat ze vaak worden geblokkeerd door browsers.

De configuratie van het gebruiker volgende beheer is beschikbaar voor de Toepassingen van het Web en het Landen Pagina&#39;s met een uit opt-banner. Zie [deze pagina](../../web/using/web-application-tracking-opt-out.md).

Adobe Campaign gebruikt twee soorten cookies:

1. Een sessiecookie (ongeldig): het bevat het herkenningsteken van e-mail die naar het contact (broadlogId) wordt verzonden en herkenningsteken van het berichtmalplaatje (deliveryId). Deze wordt toegevoegd wanneer de contactpersoon op een URL klikt die is opgenomen in een e-mailbericht dat is verzonden door Adobe Campaign. Hiermee kunt u het gedrag van de contactpersoon op het web volgen. Deze sessiecookie wordt automatisch gewist wanneer de browser wordt gesloten. De contactpersoon kan zijn browser configureren om cookies te weigeren.
1. Een permanente cookie (uuid230): Hiermee kunt u de gebruikers identificeren die communiceren met Adobe Campaign wanneer ze een website bezoeken. Deze wordt door Adobe Campaign gebruikt om het aantal klikken en de geschatte overdrachtsnelheid tijdens een marketingcampagne te tellen. Deze wordt geplaatst wanneer de contactpersoon in een e-mail klikt, een formulier invult in Adobe Campaign of tijdens het aanroepen van de binnenkomende interactie-engine. De gebruiker kan zijn browser configureren om deze te verwijderen of te weigeren.

## Database-integriteit {#database-integrity}

Adobe Campaign beschikt over veel functies. Daarom wordt een complexe databasestructuur gebruikt. De database bevat veel tabellen, velden, koppelingen en indexen. Bepaalde tussenliggende tabellen worden niet weergegeven in de interface. De software maakt, verwijdert of wijzigt automatisch bepaalde koppelingen, velden en indexen. Alleen Adobe Campagne-interfaces (grafische interface, importprogramma, servermodule, webmodule, leveringsservers, veld toevoegen, databaseextensie, enz.) U kunt de inhoud van de database wijzigen zonder de integriteit van de database uit het oog te verliezen.

**Wijzig nooit de inhoud of structuur van de database met een ander gereedschap dan deze software**. Dergelijke wijzigingen zouden zeer waarschijnlijk het gegevensbestand bederven, resulterend in: onbedoelde wijziging of verlies van koppelingen, het maken van spookrecords of koppelingen, ernstige foutberichten, enzovoort, en het annuleren van het contract voor garantie en technische ondersteuning dat door Adobe Campaign wordt aangeboden.

In het Adobe Campagne-systeem worden alle gegevens opgeslagen in de database. De juiste werking van het gehele Adobe Campagne-systeem is afhankelijk van de beschikbaarheid van deze gegevens voor: webmodules voor abonnement, beheer en abonnement, beheerschermen, leveringswachtrijen, optimalisatiemechanismen voor levering, enz.

## Apache Tomcat {#apache-tomcat}

Adobe Campaign omvat Apache Tomcat, ontwikkeld door de Apache Software Foundation ( [https://www.apache.org/](https://www.apache.org/)).
