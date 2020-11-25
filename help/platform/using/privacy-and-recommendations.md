---
solution: Campaign Classic
product: campaign
title: Privacy en toestemming
description: Meer informatie over privacy en toestemming
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 97e039e48068e3862bc6640711efe54f21fc0f15
workflow-type: tm+mt
source-wordcount: '2043'
ht-degree: 5%

---


# Privacy and Consent{#privacy-and-recommendations}

## Algemene aanbevelingen {#general-recommendations}

Adobe Campaign is een krachtig instrument voor het verzamelen en verwerken van zeer grote hoeveelheden gegevens, waaronder persoonlijke informatie en gevoelige gegevens. Daarom moet de privacy zorgvuldig worden beheerd.

* Altijd verantwoordelijk en ethisch gebruik maken van persoonlijke informatie.

* Stuur geen ongewenste e-mail, pushberichten en SMS-berichten (&quot;spam&quot;). Adobe gelooft sterk in de beginselen van toestemmings marketing in het bevorderen van de waarde en loyaliteit van het klantenleven, en verbiedt daarom strikt het gebruik van Adobe Campaign in het verzenden van ongevraagde berichten.

Neem de tijd om de [Controlelijst voor beveiliging en privacy](https://helpx.adobe.com/nl/campaign/kb/acc-security.html) door te nemen om de belangrijkste elementen betreffende de controle van beveiliging en privacy te leren.

### Privacyregels {#privacy-regulations}

Werken binnen de wetgeving die van toepassing is op de regio(s) waar u actief bent, om de privacy correct te behandelen en persoonsgegevens te beheren. Deze verordeningen omvatten:
* [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en) (Europese algemene gegevensbeschermingsverordening)
* [DPA](https://www.gov.uk/data-protection) (tenuitvoerlegging door het Verenigd Koninkrijk van de GDPR)
* [Europese richtlijn betreffende privacy en elektronische communicatie](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) (Amerikaanse wet tot vaststelling van de regels en vereisten voor commerciële e-mail)
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;titel=1.81.5.&amp;part=4.&amp;hoofdstuk=&amp;artikel=) (California Consumer Privacy Act)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) (Thailand Personal Data Protection Act)
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) (Braziliaanse algemene wet inzake gegevensbescherming) - zal van kracht worden vanaf 16 augustus 2020

>[!NOTE]
>
>Zie [deze pagina](../../platform/using/privacy-management.md#privacy-management-regulations)voor meer informatie over hoe GDPR, CCPA, PDPA en LGPD van toepassing zijn op Adobe Campaign.

### Adobe Experience Cloud privacy {#experience-cloud-privacy}

Adobe Campaign maakt deel uit van de Adobe Experience Cloud-oplossingen. De manier waarop de privacy in Campaign wordt behandeld volgt de algemene beginselen van de Experience Cloud, zoals het volgende:

* **Welke informatie wordt verzameld bij gebruik van Adobe Experience Cloud**

   Als bedrijf dat Adobe Experience Cloud-oplossingen gebruikt, kiest u welke gegevens u wilt verzamelen en naar uw Adobe Experience Cloud-account verzenden. Voorbeelden van de soorten informatie die kunnen worden verzameld zijn onder andere webbrowseractiviteiten, IP-adressen, locatiegegevens van mobiele apparaten, succespercentages van campagnes, items die zijn aangeschaft of in een winkelwagentje zijn geplaatst, enz.

   >[!NOTE]
   >
   >Net als voor alle Adobe-producten verzamelt Campagne informatie over gebruikers van apps en websites. Zie het [Adobe-privacybeleid](https://www.adobe.com/privacy/policy.html)voor meer informatie.

* **Hoe Adobe Experience Cloud wordt gebruikt om informatie te verzamelen**

   * Adobe Experience Cloud-oplossingen gebruiken cookies en vergelijkbare technologieën, zoals webbakens (ook wel tags of pixels genoemd), om u in staat te stellen informatie te verzamelen. Zie [deze sectie](#tracking-capabilities)voor meer informatie over cookies en trackingmogelijkheden met Adobe Campaign.
   * U kunt ook Adobe Experience Cloud-technologieën gebruiken in uw mobiele apps. Raadpleeg het [SMS-kanaal](../../delivery/using/sms-channel.md) en het [mobiele app-kanaal](../../delivery/using/about-mobile-app-channel.md)voor meer informatie over het verzenden van mobiele leveringen met campagne.

* **De privacyopties van uw gebruikers met betrekking tot uw gebruik van Adobe Experience Cloud**

   Adobe vraagt u om het privacybeleid van uw klanten te beschrijven:

   * Je privacy-praktijken in verband met Adobe Experience Cloud
   * Hoe gebruikers hun voorkeuren kunnen instellen voor het verzamelen of gebruiken van hun gegevens in verband met Adobe Experience Cloud

   >[!NOTE]
   >
   >Net als voor alle Adobe-producten kunnen Campagnegebruikers weigeren om informatie over hen te delen via apps en websites. Raadpleeg de veelgestelde vragen over [Adobe Experience Cloud-gebruiksgegevens voor meer informatie](https://www.adobe.com/privacy/experience-cloud-usage-info-faq.html).

Zie [deze pagina](https://www.adobe.com/privacy/marketing-cloud.html)voor meer informatie over de Adobe Experience Cloud-privacy.

## Persoonlijke gegevens en personen {#personal-data}

Bij het beheren van Privacy, is het belangrijk om te bepalen welke gegevens met zorg en door wie moeten worden behandeld.
* **Persoonsgegevens** zijn informatie die direct of indirect een levende persoon kan identificeren.
* **Gevoelige persoonsgegevens** zijn gegevens over ras, politieke opvattingen, godsdienstige overtuiging, criminele achtergrond, genetische informatie, gezondheidsgegevens, seksuele voorkeur, biometrische informatie en lidmaatschap van een vakvereniging.

Wanneer het integreren van Campagne met andere oplossingen van Experience Cloud waar het publiek van één systeem aan een andere kan worden overgebracht, zoals [Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md), [Audience Manager of de kerndienst](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md)van het Mensen, [Campaign Standard](../../integrations/using/synchronizing-audiences.md), of met andere oplossingen door de Verbindingen van [CRM](../../platform/using/crm-connectors.md), moet u extra zorg aan de bescherming van persoonsgegevens betalen.

De [belangrijkste verordeningen](#privacy-regulations) verwijzen naar de verschillende entiteiten die gegevens beheren als volgt:
* Een **gegevenscontroller** is de instantie die de middelen en het doel van het verzamelen, gebruiken en delen van persoonsgegevens bepaalt.
* Een **gegevensprocessor** is een persoon of partij die persoonlijke gegevens verzamelt, gebruikt of deelt op de wijze die door de gegevenscontroller wordt aangegeven.
* Een **betrokkene** is een levende persoon wiens persoonsgegevens worden verzameld, gebruikt of gedeeld en die direct of indirect kan worden geïdentificeerd aan de hand van die persoonsgegevens.

Als bedrijf dat persoonlijke gegevens verzamelt en deelt, bent u dus de Data Controller, zijn uw klanten de Data Subjects en Adobe Campaign fungeert als een Data Processor bij het verwerken van hun persoonlijke gegevens op de door u aangegeven wijze. Merk op dat het uw verantwoordelijkheid als Controlemechanisme van Gegevens is om de verhouding met de Onderwerpen van Gegevens te behandelen zoals wanneer het beheren van [privacyverzoeken](#privacy-requests).

### Hoofdscenario gebruiken {#use-case-scenario}

Om te illustreren hoe de verschillende personen met elkaar communiceren, is dit een voorbeeld van een GDPR-gebruiksgeval op hoog niveau.

In dit voorbeeld is een luchtvaartmaatschappij de klant van Adobe Campaign. Dit bedrijf is de **Data Controller** en alle klanten van het luchtvaartbedrijf zijn **Data Subjects**. Laura is in dit specifieke geval een klant van de luchtvaartmaatschappij.

Hier volgen de verschillende personen die in dit voorbeeld worden gebruikt:

* **Laura** is het **onderwerp** Data. Zij is de ontvanger die berichten van de luchtvaartmaatschappij ontvangt. Laura kan vaak vliegen, maar kan op een gegeven moment besluiten dat ze geen gepersonaliseerde reclame- of marketingberichten van de luchtvaartmaatschappij wil. Ze zal de luchtvaartmaatschappij (op basis van hun proces) vragen haar frequent flyer nummer te verwijderen.

* **Anne** is de **Data Controller** bij de luchtvaartmaatschappij. Ze ontvangt het verzoek van Laura, haalt nuttige id&#39;s op die zijn gevraagd om het onderwerp te identificeren en verzendt het verzoek in Adobe Campaign.

* **Adobe Campaign** is de **Data Processor**.

![](assets/privacy-gdpr-flow.png)

Hier volgt de algemene stroom voor dit geval van gebruik:

1. Het **Gegevenssubject** (Laura) verzendt een GDPR-verzoek naar de **Data Controller**, via e-mail, klantenservice of een webportaal.

1. De **Datacontrole** (Bijlage) duwt het GDPR- verzoek aan Campagne via de interface of het gebruiken van API.

1. Zodra de **Gegevensverwerker** (Adobe Campaign) de informatie ontvangt, neemt het actie op het GDPR- verzoek en verzendt een antwoord of erkenning naar de **Datacontrole** (Bijlage).

1. Het **Controlemechanisme** van Gegevens (Anne) herziet dan de informatie en verzendt het terug naar het **Onderwerp** van Gegevens (Laura).

## Gegevensverwerving {#data-acquisition}

Met Adobe Campaign kunt u gegevens verzamelen, waaronder persoonlijke en vertrouwelijke informatie. Het is daarom van essentieel belang dat u de toestemming van uw ontvangers ontvangt en controleert.

* Heb altijd ontvangers overeenkomen om mededelingen te ontvangen. Om dit te doen, moet u zo snel mogelijk aan de &quot;opt-out&quot;-verzoeken blijven voldoen en moet u de instemming controleren via een &quot;double opt-in&quot;-proces. Zie [Een abonnementsformulier met dubbele aanmelding](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)maken voor meer informatie.
* Importeer geen frauduleuze lijsten en gebruik geen zaadadressen om te controleren of uw clientbestand niet frauduleus wordt gebruikt. Zie [Informatie over zaadadressen](../../delivery/using/about-seed-addresses.md)voor meer informatie.
* Via toestemmings- en rechtenbeheer kunt u de voorkeuren van uw ontvangers bijhouden en beheren wie binnen uw organisatie toegang heeft tot welke gegevens. Zie [deze sectie](#consent)voor meer informatie.
* De privacyverzoeken van uw ontvangers faciliteren en beheren. Zie [deze sectie](#privacy-requests)voor meer informatie.

## Privacybeheer {#privacy-management}

Het beheer van de privacy verwijst naar alle processen en hulpmiddelen die u kunnen helpen aan de verordeningen van de Privacy (GDPR, CCPA, enz.) voldoen. Bekijk een overzicht van het privacybeheer op [deze pagina](https://helpx.adobe.com/nl/campaign/kb/campaign-privacy-overview.html).

Adobe Campaign biedt u verschillende functies voor privacybeheer:
* Goedkeuringsbeheer, gegevensbewaring en gebruikersrollen. Zie [deze sectie](#consent).
* Privacyverzoeken (recht op toegang en recht om te worden vergeten). Zie [deze sectie](#privacy-requests).
* Opt-out voor de Verkoop van Persoonlijke Informatie (specifiek CCPA). Zie [deze sectie](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

De belangrijkste mogelijkheden van de Privacy in Campagne en een voorbeeld van de betrokken personen worden voorgesteld in [deze sectie](https://helpx.adobe.com/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow).

### Toestemming, bewaring en rollen {#consent}

Oorspronkelijk biedt Adobe Campaign belangrijke functies die essentieel zijn voor privacy:

* **Toegangsbeheer**: Via het abonnementsbeheerproces kunt u de voorkeuren van uw ontvangers beheren en bijhouden welke ontvangers hebben gekozen voor welk type abonnement. Zie [Informatie over abonnementen](../../delivery/using/about-services-and-subscriptions.md)voor meer informatie.
* **Bewaren** van gegevens: Alle ingebouwde standaardlogtabellen hebben vooraf ingestelde retentieperioden, waarbij de gegevensopslag doorgaans tot 6 maanden of minder wordt beperkt. Er kunnen extra retentieperiodes worden ingesteld met workflows. Neem hiervoor contact op met de consultants van de Adobe of met technische beheerders.
* **Rechtenbeheer**: Adobe Campaign biedt u de mogelijkheid om de rechten te beheren die aan de verschillende campagneoperatoren zijn toegewezen via verschillende vooraf gebouwde of aangepaste rollen. Hierdoor kunt u bepalen wie binnen uw bedrijf toegang heeft tot verschillende typen gegevens, deze kan wijzigen of exporteren. Zie [Informatie over toegangsbeheer](../../platform/using/access-management.md)voor meer informatie hierover.

Zie [deze sectie](../../platform/using/privacy-management.md#consent-retention-roles)voor meer informatie over deze functies en hoe u ze in Adobe Campaign kunt beheren.

### Privacyverzoeken {#privacy-requests}

Adobe Campaign biedt extra mogelijkheden om u te helpen uw bereidheid als Data Controller voor bepaalde privacyverzoeken te vergemakkelijken:

* Het **recht op toegang** is het recht van de betrokkene om van de verantwoordelijke voor de verwerking bevestiging te krijgen dat al dan niet persoonsgegevens worden verwerkt, waar en waarom.

* Het **recht om te worden vergeten** (schrappingsverzoek) geeft de betrokkene het recht om zijn/haar persoonlijke gegevens te laten wissen door de verantwoordelijke voor de verwerking.

De verzoeken **om toegang** en **schrapping** worden voorgesteld in [deze sectie](../../platform/using/privacy-management.md#right-access-forgotten).

De implementatiestappen voor het maken van deze aanvragen worden in [deze sectie](../../platform/using/privacy-requests.md)beschreven.

## Traceermogelijkheden {#tracking-capabilities}

### Cookies {#cookies}

Dankzij de trackingfuncties van Adobe Campaign kunt u het bladeren door de ontvangers van de cookies bijhouden aan de hand van drie typen cookies: een sessiecookie en twee permanente cookies.

* A **session** cookie: the **nlid** cookie contains the identifier of the email sent to the contact (**broadlogId**) and the identifier of the message template (**deliveryId**). Deze wordt toegevoegd wanneer de contactpersoon op een URL klikt die is opgenomen in een e-mail die door Adobe Campaign wordt verzonden. Hiermee kunt u het gedrag van de contactpersoon op het web volgen. Deze sessiecookie wordt automatisch gewist wanneer de browser wordt gesloten. De contactpersoon kan zijn browser configureren om cookies te weigeren.

* Twee **permanente** cookies:
   * Het **UUID** -cookie (Universal Unique IDentifier) wordt gedeeld door Adobe Experience Cloud-oplossingen. Deze wordt één keer ingesteld totdat deze verdwijnt uit de clientbrowser wanneer een nieuwe waarde wordt gegenereerd. Met dit cookie kunt u de gebruikers identificeren die met de Experience Cloud-oplossingen werken wanneer ze een website bezoeken. Het kan door een landingspagina (om onbekende klantenactiviteiten aan een ontvanger te associëren) of door een levering worden gedeponeerd. De beschrijving van deze cookie is beschikbaar op [deze pagina](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html?lang=en#ec-cookies).
   * Het **nllastdelid** cookie (geïntroduceerd in Campaign Classic 20.3) is een permanent cookie dat de **deliveryId** bevat van de laatste levering waarvan de gebruiker op de koppeling klikte. Dit cookie wordt gebruikt - wanneer het sessiecookie ontbreekt - om de volgende tabel te identificeren die wordt gebruikt.

In verordeningen zoals de algemene gegevensbeschermingsverordening (GDPR) wordt bepaald dat bedrijven de toestemming van webgebruikers eisen voordat ze cookies installeren.

* U moet gebruikers laten weten dat uw sites zijn uitgerust met webtraceringsprogramma&#39;s via een verzoek om toestemming (bijvoorbeeld via de pagina) met een selectievakje voor het gebruik van cookies, of u moet een banner toevoegen boven aan de eerste pagina waarop ze landen, enzovoort.
* Pop-upvensters moeten worden vermeden omdat ze vaak worden geblokkeerd door browsers.

### Berichten bijhouden {#message-tracking}

Met Adobe Campaign kunt u de verzonden e-mails en het gedrag van de ontvangers van de levering volgen: openen, klikken op koppelingen, abonnementen enz. Zie [Informatie over bericht bijhouden](../../delivery/using/about-message-tracking.md)voor meer informatie.

Om dit te doen, voeg [bijgehouden verbindingen](../../delivery/using/how-to-configure-tracked-links.md) aan uw berichten toe om het effect van uw levering en ontvankelijk gedrag op het [Volgen](../../delivery/using/monitoring-a-delivery.md#tracking-logs) lusje van het leveringsdashboard te meten. Trackinggegevens worden geïnterpreteerd in het rapport [Trackingindicatoren](../../reporting/using/delivery-reports.md#tracking-indicators) .

### Webtracking {#web-tracking}

Met Adobe Campaign kunt u ook controleren hoe ontvangers door uw website bladeren: tags voor bijhouden invoegen om informatie te verzamelen en bezoeken aan webtoepassingspagina&#39;s te meten. Zie Een [webtoepassing](../../web/using/tracking-a-web-application.md)bijhouden voor meer informatie.

De configuratie van webtracering wordt weergegeven in [deze sectie](../../configuration/using/about-web-tracking.md).

Voor verder beheer van tracering kunt u in Adobe Campaign een uitschakelingsbanner weergeven om het webgedrag van eindgebruikers die zich afmelden voor het volgen van gedragingen, niet meer te volgen. Voor meer op dit, zie de toepassing van het [Web het volgen opt-out](../../web/using/web-application-tracking-opt-out.md).
