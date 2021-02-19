---
solution: Campaign Classic
product: campaign
title: Privacy en toestemming
description: Meer informatie over privacy en toestemming
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '2043'
ht-degree: 73%

---


# Privacy en toestemming{#privacy-and-recommendations}

## Algemene aanbevelingen {#general-recommendations}

Adobe Campaign is een krachtige tool voor het verzamelen en verwerken van zeer grote hoeveelheden gegevens, waaronder persoonlijke informatie en gevoelige gegevens. Daarom moet privacy zorgvuldig worden beheerd.

* Ga altijd op verantwoordelijke en ethische wijze te werk bij het gebruik van persoonsgegevens.

* Stuur geen ongewenste e-mails, pushberichten en sms-berichten (&quot;spam&quot;). Adobe gelooft sterk in de principes van permission marketing, in het bevorderen van customer lifetime value en in de loyaliteit van klanten, en verbiedt daarom strikt het gebruik van Adobe Campaign voor het verzenden van ongevraagde berichten.

Neem de tijd om de [Controlelijst voor beveiliging en privacy](https://helpx.adobe.com/nl/campaign/kb/acc-security.html) door te nemen om de belangrijkste elementen betreffende de controle van beveiliging en privacy te leren.

### Privacywetgeving{#privacy-regulations}

Werk binnen de wetgeving die geldt voor de regio(’s) waar u actief bent om privacy en persoonsgegevens correct te behandelen en te beheren. Het gaat bijvoorbeeld om de volgende wetgevingen:
* [AVG](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en) (Algemene verordening gegevensbescherming)
* [DPA](https://www.gov.uk/data-protection) (Britse implementatie van de AVG)
* [Europese richtlijn betreffende privacy en elektronische communicatie](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) (Amerikaanse wetgeving over regels en vereisten voor commerciële e-mail)
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=) (California Consumer Privacy Act)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) (Thaise wet inzake de bescherming van persoonsgegevens)
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf)  (Braziliaanse algemene wet inzake gegevensbescherming) - wordt van kracht vanaf 16 augustus 2020

>[!NOTE]
>
>Zie [deze pagina](../../platform/using/privacy-management.md#privacy-management-regulations) voor meer informatie over hoe GDPR, CCPA, PDPA en LGPD van toepassing zijn op Adobe Campaign.

### Adobe Experience Cloud-privacy {#experience-cloud-privacy}

Adobe Campaign maakt deel uit van de Adobe Experience Cloud-oplossingen. De manier waarop in Campaign met privacy wordt omgegaan, volgt de algemene Experience Cloud-beginselen:

* **Welke informatie wanneer wordt verzameld bij het gebruik van Adobe Experience Cloud**

   Als bedrijf dat Adobe Experience Cloud-oplossingen gebruikt, bepaalt u welke gegevens u verzamelt en naar uw Adobe Experience Cloud-account verzendt. Voorbeelden van soorten informatie die mogelijk worden verzameld, zijn webbrowseractiviteiten, IP-adressen, locatiegegevens van mobiele apparaten, succespercentages van campagnes, items die zijn aangeschaft of in een winkelwagentje zijn geplaatst, enz.

   >[!NOTE]
   >
   >Net als alle andere Adobe-producten verzamelt Campaign informatie over gebruikers van apps en websites. Zie het [Adobe-privacybeleid](https://www.adobe.com/privacy/policy.html) voor meer informatie.

* **Hoe Adobe Experience Cloud wordt gebruikt om informatie te verzamelen**

   * Adobe Experience Cloud-oplossingen gebruiken cookies en vergelijkbare technologieën zoals webbakens (ook wel tags of pixels genoemd), waarmee u informatie kunt verzamelen. Zie [deze sectie](#tracking-capabilities) voor meer informatie over cookies en trackingmogelijkheden met Adobe Campaign.
   * U kunt in uw mobiele apps ook Adobe Experience Cloud-technologieën gebruiken. Zie [SMS-kanaal](../../delivery/using/sms-channel.md) en [Mobiel app-kanaal](../../delivery/using/about-mobile-app-channel.md) voor meer informatie over het verzenden van mobiele leveringen met campagne.

* **De privacyopties van uw gebruikers voor uw gebruik van Adobe Experience Cloud**

   Adobe vraagt u om uw klanten een privacybeleid te verstrekken waarin het volgende wordt beschreven:

   * Uw privacymethoden in verband met Adobe Experience Cloud
   * Hoe gebruikers hun voorkeuren kunnen instellen voor het verzamelen of gebruiken van hun gegevens in verband met Adobe Experience Cloud

   >[!NOTE]
   >
   >Net als bij alle Adobe-producten kunnen Campaign-gebruikers weigeren om verzamelde informatie over hen te delen via apps en websites. Raadpleeg de [Veelgestelde vragen over Adobe Experience Cloud-gebruiksgegevens](https://www.adobe.com/privacy/experience-cloud-usage-info-faq.html) voor meer informatie daarover.

Zie [deze pagina](https://www.adobe.com/privacy/marketing-cloud.html) voor meer informatie over de Adobe Experience Cloud-privacy.

## Persoonsgegevens en persona&#39;s {#personal-data}

Bij privacybeheer is het belangrijk om te bepalen welke gegevens met zorg moeten worden behandeld en door wie.
* **Persoonsgegevens** omvatten informatie aan de hand waarvan een levende persoon direct of indirect kan worden geïdentificeerd.
* **Gevoelige persoonsgegevens** zijn gegevens over etnische afkomst, politieke opvattingen, godsdienstige overtuiging, criminele achtergrond, genetische informatie, gezondheidsgegevens, seksuele voorkeur, biometrische informatie en lidmaatschap van een vakbond.

Wanneer u Campagne integreert met andere Experience Cloud-oplossingen waarbij het publiek van het ene systeem naar het andere kan worden overgebracht, zoals [Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md), [Audience Manager- of People core service](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md), [Campaign Standard](../../integrations/using/synchronizing-audiences.md) of met andere oplossingen via [CRM-connectors](../../platform/using/crm-connectors.md), moet u extra aandacht besteden aan de bescherming van persoonsgegevens.

De [belangrijkste verordeningen](#privacy-regulations) betreffen de verschillende entiteiten die gegevens als volgt beheren:
* Een **gegevenscontroller** is de instantie die de middelen en het doel van het verzamelen, gebruiken en delen van persoonsgegevens bepaalt.
* Een **gegevensprocessor** is een persoon of partij die persoonsgegevens verzamelt, gebruikt of deelt op de manier die door de gegevenscontroller wordt aangegeven.
* Een **betrokkene** is een levende persoon wiens persoonsgegevens worden verzameld, gebruikt of gedeeld en die aan de hand van deze persoonsgegevens direct of indirect kan worden geïdentificeerd.

Als bedrijf dat persoonsgegevens verzamelt en deelt, bent u dus de gegevenscontroller, zijn uw klanten de betrokkenen en fungeert Adobe Campaign als gegevensprocessor bij het verwerken van deze persoonsgegevens op uw aanwijzingen. Als gegevenscontroller bent u verantwoordelijk voor de relatie met de betrokkenen, bijvoorbeeld bij het beheren van [verzoeken om toegang tot persoonsgegevens](#privacy-requests).

### Gebruiksscenario {#use-case-scenario}

Hier is een voorbeeld van een AVG-gebruiksscenario van hoog niveau om te laten zien hoe verschillende persona’s interactie met elkaar hebben.

In dit voorbeeld is de klant van Adobe Campaign een luchtvaartmaatschappij. Dit bedrijf is de **Gegevenscontroller** en alle klanten van de luchtvaartmaatschappij zijn **Betrokkenen**. Laura is in dit specifieke geval een klant van de luchtvaartmaatschappij.

Dit zijn de verschillende persona’s die in dit voorbeeld worden gebruikt:

* **Laura** is de **Betrokkene**. Zij is de ontvanger die berichten van de luchtvaartmaatschappij krijgt. Laura vliegt misschien wel vaak (Frequent Flyer), maar ze zou op een gegeven moment kunnen besluiten dat ze geen gepersonaliseerde reclame- of marketingberichten van de luchtvaartmaatschappij meer wil. Ze zal de luchtvaartmaatschappij (volgens hun procedure) vragen haar Frequent-Flyernummer te verwijderen.

* **Anne** is **Gegevenscontroller** bij de luchtvaartmaatschappij. Ze ontvangt het verzoek van Laura, haalt handige ID’s op die zijn aangevraagd om de betrokkene te identificeren en verzendt het verzoek in Adobe Campaign.

* **Adobe Campaign** is de **Gegevensprocessor**.

![](assets/privacy-gdpr-flow.png)

Hier volgt de algemene workflow voor dit gebruiksscenario:

1. De **Betrokkene** (Laura) stuurt een AVG-verzoek naar de **Gegevenscontroller** via e-mail, de Klantenservice of een webportal.

1. De **Gegevenscontroller** (Anne) stuurt het AVG-verzoek naar Campaign via de interface of met een API.

1. Zodra de **Gegevensprocessor** (Adobe Campaign) de informatie heeft ontvangen, onderneemt deze actie voor het AVG-verzoek en stuurt een reactie of een bevestiging naar de **Gegevenscontroller** (Anne).

1. De **Gegevenscontroller** (Anne) bekijkt vervolgens de informatie en stuurt deze terug naar de **Betrokkene** (Laura).

## Gegevensacquisitie {#data-acquisition}

Met Adobe Campaign kunt u gegevens verzamelen, waaronder persoonlijke en gevoelige informatie. Het is daarom van essentieel belang dat u de toestemming van uw ontvangers ontvangt en controleert.

* Zorg ervoor dat ontvangers altijd toestemming geven voor het ontvangen van communicatie. Daarvoor moet u opt-outverzoeken altijd zo snel mogelijk verwerken en moet u toestemming controleren via een dubbele opt-inprocedure. Zie [Een abonnementsformulier maken met dubbele opt-in](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in) voor meer informatie.
* Importeer geen frauduleuze lijsten en gebruik geen zaadadressen om te controleren of uw clientbestand niet frauduleus wordt gebruikt. Voor meer op dit, zie [Ongeveer zaadadressen](../../delivery/using/about-seed-addresses.md).
* Via toestemmings- en rechtenbeheer kunt u de voorkeuren van uw ontvangers bijhouden en beheren wie binnen uw organisatie toegang heeft tot welke gegevens. Zie [deze sectie](#consent)voor meer informatie.
* Faciliteer en beheer de verzoeken om toegang tot persoonsgegevens van uw ontvangers. Zie [deze sectie](#privacy-requests)voor meer informatie.

## Privacybeheer {#privacy-management}

Privacybeheer verwijst naar alle processen en tools die u kunnen helpen te voldoen aan de privacywetgeving (AVG, CCPA, enz.). Bekijk een overzicht van privacybeheer op [deze pagina](https://helpx.adobe.com/nl/campaign/kb/campaign-privacy-overview.html).

Adobe Campaign biedt u verschillende functiesets voor privacybeheer:
* toestemmingsbeheer, dataretentie en gebruikersrollen. Zie [deze sectie](#consent).
* Verzoeken om toegang tot persoonsgegevens (toegangsrecht en recht om te worden vergeten). Zie [deze sectie](#privacy-requests).
* Opt-out voor de verkoop van persoonsgegevens (CCPA-specifiek). Zie [deze sectie](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

De belangrijkste privacymogelijkheden in Campaign en een voorbeeld van de betrokken persona’s worden weergegeven in [deze sectie](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-faq.html?lang=nl#getting-started).

### Toestemming, retentie en rollen {#consent}

Oorspronkelijk biedt Adobe Campaign belangrijke functies die essentieel zijn voor privacy:

* **Toestemmingsbeheer**: via de procedure van abonnementsbeheer kunt u de voorkeuren van uw ontvangers beheren en bijhouden welke ontvangers zich hebben aangemeld voor welke soorten abonnementen. Zie [Informatie over abonnementen](../../delivery/using/about-services-and-subscriptions.md) voor meer informatie.
* **Dataretentie**: alle ingebouwde standaard logtabellen bevatten vooraf ingestelde retentieperioden, waarbij de gegevensopslag over het algemeen is beperkt tot 6 maanden of korter. Er kunnen extra retentieperioden worden ingesteld met workflows. Neem hiervoor contact op met de adviseurs van Adobe of met technische beheerders.
* **Rights Management**: Adobe Campaign biedt u de mogelijkheid om via verschillende standaard of aangepaste rollen de rechten te beheren die aan de verschillende Campaign-operators zijn toegewezen. Hierdoor kunt u bepalen wie binnen uw bedrijf toegang heeft tot verschillende typen gegevens en deze kan wijzigen of exporteren. Zie [Toegangscontrole](../../platform/using/access-management.md) voor meer informatie.

Zie [deze sectie](../../platform/using/privacy-management.md#consent-retention-roles) voor meer informatie over deze functies en hoe u ze kunt beheren in Adobe Campaign.

### Verzoeken om toegang tot persoonsgegevens {#privacy-requests}

Adobe Campaign biedt extra mogelijkheden om uw taak als gegevenscontroller voor bepaalde verzoeken om toegang tot persoonsgegevens te vergemakkelijken:

* Het **toegangsrecht** is het recht van de betrokkene om van de gegevenscontroller bevestiging te krijgen of er persoonsgegevens van de betrokkene worden verwerkt, waar en voor welk doel.

* Het **recht om te worden vergeten** (verwijderingsverzoek) geeft de betrokkene het recht om zijn/haar persoonsgegevens door de gegevenscontroller te laten wissen.

Verzoeken om **toegang** en **verwijdering** worden weergegeven in [deze sectie](../../platform/using/privacy-management.md#right-access-forgotten).

De implementatiestappen voor het maken van deze verzoeken worden uiteengezet in [deze sectie](../../platform/using/privacy-requests.md).

## Trackingmogelijkheden {#tracking-capabilities}

### Cookies {#cookies}

Dankzij de trackingfuncties van Adobe Campaign kunt u het bladeren door de ontvangers van de cookies bijhouden aan de hand van drie typen cookies: een sessiecookie en twee permanente cookies.

* Een **session** cookie: het **nlid**-cookie bevat de id van de e-mail die naar de contactpersoon is verzonden (**broadlogId**) en de id van de berichtsjabloon (**deliveryId**). Deze wordt toegevoegd wanneer de contactpersoon op een URL klikt die is opgenomen in een e-mail die door Adobe Campaign wordt verzonden. Hiermee kunt u het gedrag van de contactpersoon op het web volgen. Deze sessiecookie wordt automatisch gewist wanneer de browser wordt gesloten. De contactpersoon kan zijn browser configureren om cookies te weigeren.

* Twee **permanente** cookies:
   * Het **UUID** (Universal Unique IDentifier)-cookie wordt gedeeld tussen Adobe Experience Cloud-oplossingen. Deze wordt één keer ingesteld totdat deze verdwijnt uit de clientbrowser wanneer een nieuwe waarde wordt gegenereerd. Met dit cookie kunt u de gebruikers identificeren die met de Experience Cloud-oplossingen werken wanneer ze een website bezoeken. Het kan door een landingspagina (om onbekende klantenactiviteiten aan een ontvanger te associëren) of door een levering worden gedeponeerd. De beschrijving van dit cookie is beschikbaar op [deze pagina](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html?lang=en#ec-cookies).
   * Het **nllastdelid**-cookie (geïntroduceerd in Campaign Classic 20.3) is een permanente cookie die **deliveryId** bevat van de laatste levering waarvan de gebruiker op de koppeling heeft geklikt. Dit cookie wordt gebruikt - wanneer het sessiecookie ontbreekt - om de volgende tabel te identificeren die wordt gebruikt.

In verordeningen zoals de Algemene verordening gegevensbescherming (AVG) wordt bepaald dat bedrijven de toestemming van webgebruikers nodig hebben voordat ze cookies mogen installeren.

* U moet gebruikers laten weten dat uw sites zijn uitgerust met webtraceringsprogramma&#39;s via een verzoek om toestemming (bijvoorbeeld via de pagina) met een selectievakje voor het gebruik van cookies, of u moet een banner toevoegen boven aan de eerste pagina waarop ze landen, enzovoort.
* Pop-upvensters moeten worden vermeden omdat ze vaak worden geblokkeerd door browsers.

### Berichten bijhouden {#message-tracking}

Met Adobe Campaign kunt u de verzonden e-mails en het gedrag van de ontvangers van de levering volgen: openen, klikken op koppelingen, abonnementen enz. Zie [Informatie over bericht bijhouden](../../delivery/using/about-message-tracking.md) voor meer informatie.

Om dit te doen, voeg [gevolgde verbindingen](../../delivery/using/how-to-configure-tracked-links.md) aan uw berichten toe om het effect van uw levering en ontvankelijk gedrag op [het Volgen](../../delivery/using/delivery-dashboard.md#tracking-logs) lusje van het leveringsdashboard te meten. Trackinggegevens worden geïnterpreteerd in het [Trackingindicatoren](../../reporting/using/delivery-reports.md#tracking-indicators)-rapport.

### Webspatiëring {#web-tracking}

Met Adobe Campaign kunt u ook controleren hoe ontvangers door uw website bladeren: tags voor bijhouden invoegen om informatie te verzamelen en bezoeken aan webtoepassingspagina&#39;s te meten. Zie [Een webtoepassing bijhouden](../../web/using/tracking-a-web-application.md) voor meer informatie.

De configuratie van web tracking wordt weergegeven in [deze sectie](../../configuration/using/about-web-tracking.md).

Om het bijhouden van wijzigingen verder te beheren, kunt u in Adobe Campaign een uitschakelbanner weergeven om het webgedrag van eindgebruikers die zich afmelden voor het volgen van gedragingen, niet meer te volgen. Voor meer op dit, zie [De toepassing van het Web volgzich opt-out](../../web/using/web-application-tracking-opt-out.md).
