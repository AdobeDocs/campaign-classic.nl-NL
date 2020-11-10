---
title: Privacybeheer
description: Meer informatie over privacybeheer
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
translation-type: tm+mt
source-git-commit: c2c7398c27f1bc7edf9adb0fc07409d2e525b168
workflow-type: tm+mt
source-wordcount: '899'
ht-degree: 1%

---


# Privacybeheer {#privacy-management}

Adobe Campaign biedt een reeks hulpmiddelen aan om u te helpen aan de verordeningen van de Privacy (met inbegrip van GDPR, CCPA, PDPA, LGPD) voldoen.

* In dit gedeelte wordt algemene informatie gegeven over wat het privacybeheer is en over de functies die Adobe Campaign biedt om het [recht op toegang en het recht om te worden vergeten](#right-access-forgotten)te beheren.

* Het bevat ook informatie over belangrijke functies voor het beheer van privacy ([toestemming, gegevensbewaring en gebruikersrollen](#consent-retention-roles)), en tips en trucs om u te helpen bij het naleven van uw privacyregels wanneer u Adobe Campaign gebruikt.

## Regels inzake privacybeheer {#privacy-management-regulations}

Met Adobe Campaign-mogelijkheden kunt u voldoen aan de volgende regels:

* **GDPR** ([algemene gegevensbeschermingsverordening](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en)) is de privacywet van de Europese Unie die de gegevensbeschermingsvereisten voor de landen van de EU harmoniseert en moderniseert.
* **CCPA** ([California Consumer Privacy Act](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;titel=1.81.5.&amp;part=4.&amp;hoofdstuk=&amp;artikel=)) biedt inwoners van Californië nieuwe rechten met betrekking tot hun persoonlijke gegevens en legt verantwoordelijkheden op het gebied van gegevensbescherming op aan bepaalde entiteiten die zaken in Californië doen.
* **PDPA** ([Personal Data Protection Act](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/)) is de nieuwe privacywet die de vereisten inzake gegevensbescherming voor Thailand harmoniseert en moderniseert.
* **De LGPD** ([Lei Geral de Proteção de Dados](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf)) zal begin 2021 van kracht worden voor alle bedrijven die in Brazilië persoonsgegevens verzamelen of verwerken.

Al deze voorschriften zijn van toepassing op Adobe Campaign-klanten die beschikken over gegevens voor gegevenssubjecten die in de bovengenoemde regio&#39;s of landen (EU, Californië, Thailand, Brazilië) verblijven.

<!--Several Privacy capabilities are available in Adobe Campaign, including consent management, data retention settings, and rights management. See [Consent, Retention and Roles](#consent-retention-roles). In addition to this, Adobe Campaign helps facilitate your readiness as Data Controller for certain Privacy requests. See [Right to Access and Right to be Forgotten](#right-access-forgotten).-->

>[!NOTE]
>
>Voor meer informatie over persoonsgegevens en over de verschillende entiteiten die gegevens beheren (Data Controller, Data Processor en Data Subject), zie [Persoonsgegevens en Persoonlijke personen](../../platform/using/privacy-and-recommendations.md#personal-data).

## Recht op toegang en recht om te worden vergeten {#right-access-forgotten}

Om u te helpen uw privacy-gereedheid te vergemakkelijken, kunt u met Adobe Campaign aanvragen voor **toegang** en **verwijdering** afhandelen.

* Het **recht op toegang** is het recht van de betrokkene om van de verantwoordelijke voor de verwerking bevestiging te krijgen of er al dan niet persoonsgegevens worden verwerkt, waar en voor welk doel. De gegevensverwerkingsverantwoordelijke verstrekt kosteloos een kopie van de persoonsgegevens in elektronische vorm.

* Ook bekend als Data Erasure, geeft het **recht om te worden vergeten** (schrappingsverzoek) de betrokkene het recht om de verantwoordelijke voor de verwerking van de gegevens zijn/haar persoonsgegevens te laten wissen, de verdere verspreiding van de gegevens te beëindigen en mogelijk derden te laten stoppen met de verwerking van de gegevens.

Raadpleeg de **implementatiestappen** voor meer informatie over het maken van **aanvragen voor toegang** en [verwijderen](../../platform/using/privacy-requests.md)en hoe Adobe Campaign deze verwerkt.

<!--Tutorials on Privacy management in Campaign Standard are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).
https://experienceleague.corp.adobe.com/docs/campaign-standard-learn/tutorials/privacy/privacy-overview.html?lang=en-->

## Toestemming, bewaring en rollen {#consent-retention-roles}

Naast het meest recente **recht op toegang** en **recht op vergeten** mogelijkheden, biedt Adobe Campaign andere belangrijke functies die essentieel zijn voor privacy:

* [Toegangsbeheer](#consent-management): abonnementsfunctionaliteit voor voorkeursbeheer
* [Bewaren](#data-retention)van gegevens: de periodes van het gegevensbehoud op alle standaardlogboeklijsten, extra bewaartermijnen kunnen opstelling met werkschema&#39;s
* [Rechtenbeheer](#rights-management): gegevenstoegang die door genoemde recht wordt beheerd

### Toegangsbeheer {#consent-management}

Toestemming betekent instemming van de betrokkene met de verwerking van persoonsgegevens betreffende een betrokkene. De gegevensverwerkingsverantwoordelijke is verantwoordelijk voor het verkrijgen van de nodige toestemming voor die verwerking. Hoewel Adobe Campaign bepaalde functies kan bieden om een klant te helpen bij het beheren van de toestemming voor de service, is Adobe niet verantwoordelijk voor de toestemming. Klanten dienen met hun eigen juridische afdelingen samen te werken om hun eigen processen en praktijken vast te stellen voor de benodigde toestemming.

Adobe Campaign kent sinds het begin van zijn goedkeuring de kenmerken die het mogelijk maken bepaalde aspecten ervan te beheren. Via het abonnementsbeheerproces kunnen klanten bijhouden welke ontvangers hebben gekozen voor welk type abonnement ze kiezen, of het nu nieuwsbrieven, dagelijkse of wekelijkse promoties of een ander type marketingprogramma zijn.

![](assets/privacy-consent-management.png)

Raadpleeg de [gedetailleerde documentatie](../../delivery/using/managing-subscriptions.md)voor meer informatie over contentbeheer.

Naast de hulpprogramma&#39;s voor het beheer van toestemming die Adobe Campaign biedt, kunt u nagaan of een consument heeft gekozen voor de verkoop van persoonlijke gegevens. Zie [deze sectie](../../platform/using/privacy-requests.md#sale-of-personal-information).

### Dataretentie {#data-retention}

Wat het behoud betreft, hebben de ingebouwde logboeklijsten in Campaign vooraf vastgestelde bewaartermijnen op hen, over het algemeen beperkt hun gegevensopslag tot zes maanden of minder.

Hieronder volgen de standaardwaarden voor behoud van ingebouwde tabellen. Houd er rekening mee dat de bewaarconfiguratie tijdens de implementatie door technische beheerders van Adobe is ingesteld en dat de waarden voor elke implementatie kunnen variëren op basis van de vereisten van de klant.

* **Geconsolideerde reeksspatiëring**: 1 jaar
* **Leveringslogboeken**: 6 maanden
* **Logboeken** bijhouden: 1 jaar
* **Verwijderde leveringen**: 1 week
* **Import weigert**: 6 maanden
* **Bezoekersprofielen**: 1 maand
* **Voorstellen** voorstel: 1 jaar
* **Gebeurtenissen**: 1 maand
* **Statistieken van gebeurtenisverwerking**: 1 jaar
* **Gearchiveerde gebeurtenissen**: 1 jaar
* **Gebeurtenissen van Pipeline genegeerd**: 1 maand

En net als bij het verwijderen met de standaardworkflowfunctionaliteit is het mogelijk om retentieperioden in te stellen voor elke aangepaste tabel.

Neem contact op met de consultants of technische Adobe-beheerders voor meer informatie over retentie of als u retentie wilt instellen voor aangepaste tabellen.

### Rechtenbeheer {#rights-management}

Adobe Campaign biedt u de mogelijkheid om de rechten te beheren die aan de verschillende campagneoperatoren zijn toegewezen via verschillende vooraf gebouwde of aangepaste rollen.

Eén voordeel is dat u zo kunt bepalen wie binnen uw bedrijf toegang heeft tot verschillende typen gegevens. U hebt bijvoorbeeld verschillende marketers voor verschillende geo&#39;s en elke markator heeft alleen toegang tot gegevens van zijn geo.

Op dezelfde manier staat deze functionaliteit u ook toe om verschillende mogelijkheden voor elke gebruiker te vormen, zoals het beperken van wie leveringen kan verzenden, of meer relevant voor het beheer van de Privacy, die gegevens kan wijzigen of uitvoeren.

![](assets/privacy-user-management.png)

Raadpleeg de [gedetailleerde documentatie](../../platform/using/access-management.md)voor meer informatie over toegangsbeheer.