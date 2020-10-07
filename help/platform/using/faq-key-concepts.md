---
title: Belangrijkste concepten
seo-title: Veelgestelde vragen over Campaign-functies
description: Veelgestelde vragen over Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 100%

---


# Belangrijkste concepten {#key-concepts}

Ontdek de belangrijkste stappen om met Adobe Campaign te beginnen.

## Kan ik verbinding maken met Campaign Classic met een Adobe ID? {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

Dankzij de integratie met het IMS (Adobe Identity Management System) kunnen gebruikers verbinding maken met de Adobe Campaign-console via hun Adobe ID. Deze integratie biedt de volgende voordelen:

* Dezelfde id kan voor alle Experience Cloud-oplossingen worden gebruikt.
* De verbinding wordt onthouden bij het gebruik van Adobe Campaign met verschillende integraties.
* Veiliger beleid voor wachtwoordbeheer.
* Gebruik van Federated ID-accounts (externe id-provider).

[Klik hier voor meer informatie](../../integrations/using/about-adobe-id.md) over toegang tot Campaign Classic met een Adobe ID.

## Wat is mijn versie van Campaign? {#what-is-my-version-of-campaign-}

Controleer uw [versie en buildnummer](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) in het menu **Help > Info...** van de Campaign-clientconsole.

## Wat zijn de verschillen bij het werken in een on-premise omgeving versus in een gehoste omgeving? {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Adobe Campaign Classic wordt geleverd met een reeks modules en opties. De beschikbaarheid van deze modules en hun configuratie kunnen afhankelijk zijn van het [type implementatie](../../installation/using/hosting-models.md) van uw installatie: gehost (Managed Services) of on-premise.

[Klik hier voor meer informatie](https://helpx.adobe.com/nl/campaign/kb/acc-on-prem-vs-hosted.html).

## Hoe kan ik gebruikersmachtigingen instellen? {#how-can-i-set-up-user-permissions-}

Als Campaign-beheerder kunt u machtigingen instellen voor gebruikers van uw organisatie.

Dit zijn een reeks rechten en beperkingen waarbij wordt toegestaan of geweigerd om:

* Toegang te krijgen tot bepaalde functies
* Toegang te krijgen tot bepaalde data
* Data te maken, te wijzigen en/of te verwijderen

[Klik hier voor meer informatie ](../../platform/using/access-management.md) over gebruikersmachtigingen.

## Hoe kan ik naleving van de privacyvereisten garanderen met Campaign? {#how-to-be-gdpr-compliant-with-campaign-}

Adobe Campaign biedt een reeks tools om u te helpen de privacyvereisten voor AVG en CCPA na te leven.

Raadpleeg [dit document](https://helpx.adobe.com/nl/campaign/kb/campaign-privacy-overview.html) voor meer informatie over de tools en functies die Adobe Campaign biedt en over best practices om u te helpen met de naleving van de AVG wanneer u onze service gebruikt. Implementatiestappen voor Campaign Classic worden beschreven in [dit artikel](https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html).

## Wat zijn de concepten van de Campaign-gebruikersinterface die ik zou moeten weten? {#what-are-campaign-user-interface-concepts-i-should-know-}

Lees [deze sectie](../../platform/using/adobe-campaign-workspace.md) voor meer informatie over de basisbeginselen van de Adobe Campaign-werkruimte. U kunt ook [deze video](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/interface-overview.html) bekijken.

## Hoe kan ik de doelgroep van mijn berichten selecteren? {#how-can-i-select-the-target-population-of-my-messages-}

Met Adobe Campaign kunt u verschillende strategieën gebruiken om doelgroepen te maken en doelontvangers te selecteren.

[Klik hier voor meer informatie](../../delivery/using/steps-defining-the-target-population.md).

## Wat is een workflow? {#what-is-a-workflow-}

Adobe Campaign bevat workflows om het volledige scala aan processen en taken in de verschillende modules van de applicatieserver te orkestreren. Met deze uitgebreide grafische omgeving kunt u processen ontwerpen, zoals segmentatie, uitvoering van campagnes, bestandsverwerking, menselijke participatie, enzovoort. Deze processen worden uitgevoerd en bijgehouden door de workflowengine.

U kunt bijvoorbeeld een workflow gebruiken om een bestand van een server te downloaden, het te decomprimeren en vervolgens records in de Adobe Campaign-database te importeren.

Een workflow kan ook een of meer operatoren omvatten die op de hoogte moeten worden gebracht of die keuzes kunnen maken en processen kunnen goedkeuren. Op deze manier is het mogelijk om een leveringsactie te maken, een taak toe te wijzen aan een of meer operatoren om aan content te werken, doelen op te geven en proeven goed te keuren voordat de levering wordt gestart.

[Klik hier voor meer informatie](../../workflow/using/about-workflows.md) over workflows. U kunt ook [de best practices voor workflows](../../workflow/using/building-a-workflow.md) lezen.

## Hoe maak en verzend ik een eerste e-mail? {#how-to-create-and-send-a-first-email-}

[Klik hier voor meer informatie](../../delivery/using/about-email-channel.md) of [bekijk deze video](https://docs.adobe.com/content/help/nl-NL/campaign-classic-learn/tutorials/getting-started/creating-a-campaign-and-an-email.html) om een e-mail te maken in een campagne.

## Hoe kan ik sms-berichten verzenden? {#how-to-send-sms-messages-}

Ontdek [in deze sectie](../../delivery/using/sms-channel.md) hoe u uw platform configureert en sms-berichten verzendt.

## Hoe kan ik pushmeldingen verzenden? {#how-to-send-push-notifications-}

Leer hoe u met Adobe Campaign [een persoonlijke pushmelding](../../delivery/using/creating-notifications.md) naar iOS en Android-apparaten kunt verzenden via apps.

## Hoe kan ik een online enquête ontwerpen en delen? {#how-to-design-and-share-an-online-survey-}

Ontdek hoe u [een online enquête kunt maken](../../web/using/getting-started-with-surveys.md) met de belangrijkste stappen voor het ontwerpen en publiceren van deze enquête met Campaign Classic.

## Hoe kan ik een landingspagina maken? {#how-to-create-landing-page-}

U kunt de digitale content-editor van Adobe Campaign gebruiken om een landingspagina te ontwerpen en toewijzingen te definiëren met databasevelden.

[Klik hier voor meer informatie](../../web/using/creating-a-landing-page.md).

## Hoe kan ik leveringen volgen? {#how-can-i-track-deliveries-}

U kunt leveringen die met Campaign Classic zijn verzonden, volgen aan de hand van speciale [leveringsrapporten](../../reporting/using/delivery-reports.md) en vervolgens uw leveringen controleren.

Meer informatie over trackingbeheer in Campaign vindt u op [deze pagina](https://helpx.adobe.com/nl/campaign/kb/acc-tracking.html).

## Wat zijn best practices voor beveiliging (on-premise)? {#what-are-security-best-practices--on-premise--}

Lees de [controlelijst voor beveiligingsconfiguratie](https://helpx.adobe.com/nl/campaign/kb/acc-security.html) voor de belangrijkste elementen die u moet controleren inzake beveiligingsconfiguratie en hardening voor on-premise implementaties.

## Hoe kan ik een foutbericht vertalen? {#how-to-translate-an-error-message-}

Een foutbericht wordt weergegeven in een vreemde taal? Alle foutberichten en de vertaling ervan worden weergegeven op [deze pagina](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/error_messages/error_codes.html).

## Kan ik een webformulier maken en antwoorden verzamelen in Campaign? {#can-i-create-a-webform-and-collect-answers-in-campaign-}

Ontdek hoe u [een webformulier maakt](../../web/using/about-web-forms.md): een webformulier ontwerpen, testen, publiceren en antwoorden verzamelen.

## Is er een lijst met afgeschafte functies en versies? {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe evalueert voortdurend de mogelijkheden in het product en is van plan om in de loop der tijd de mogelijkheden te vervangen door krachtigere versies, of besluit om bepaalde onderdelen opnieuw te implementeren om beter voorbereid te zijn op toekomstige verwachtingen of uitbreidingen. Aangezien Campaign met tools van derden werkt, wordt de compatibiliteit regelmatig bijgewerkt om alleen ondersteunde versies te implementeren.

[Klik hier voor meer informatie](https://helpx.adobe.com/nl/campaign/kb/deprecated-and-removed-features.html).

## Zijn er nieuwe documentatie-updates en Help-materialen vrijgegeven? {#are-there-new-documentation-updates-and-help-materials-released-}

De meest recente Campaign Classic-documentatie-updates worden weergegeven [op deze pagina](https://docs.adobe.com/content/help/nl-NL/campaign-classic/using/documentation-updates.html).

U kunt ook de meest recente technische opmerkingen [op deze pagina](https://helpx.adobe.com/nl/campaign/kb/article-list.html) raadplegen.
