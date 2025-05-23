---
product: campaign
title: Privacybeheer
description: Meer informatie over privacybeheer
feature: Privacy, Privacy Tools
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 23c873fd-9016-4d32-842c-772cfff0e23e
source-git-commit: 122d69d3d7474480f7799248413ac89338469ebc
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 79%

---

# Privacybeheer {#privacy-management}

Adobe Campaign biedt een reeks tools om u te helpen voldoen aan de [privacyverordeningen](#privacy-management-regulations) (zoals AVG, CCPA, PDPA, LGPD).

Hier volgen de vijf belangrijkste mogelijkheden die Adobe Campaign biedt om de gereedheid voor privacyregels te garanderen:

* **Recht op toegang**
* **Recht op verwijdering**
* **Toestemmingsbeheer**
* **Dataretentie**
* **Rights Management**

![](assets/privacy-gdpr-use-cases.png)

Zie [Toegangsrecht en recht om te worden vergeten](#right-access-forgotten) en [Toestemming, retentie en rollen](#consent-retention-roles) voor meer informatie.

<!--This section presents general information on what Privacy management is and the features provided by Adobe Campaign to manage the [Right to Access and Right to be Forgotten](#right-access-forgotten).

It also contains information on important features to manage Privacy ([Consent, Retention and Roles](#consent-retention-roles)), as well as best practices to help you with your Privacy compliance when using Adobe Campaign.-->

## Regels voor privacybeheer {#privacy-management-regulations}

Met de opties van Adobe Campaign kunt u voldoen aan de volgende regels:

* **GDPR** (de Algemene Verordening van de Bescherming van Gegevens) is de (EU) privacywet van de Europese Unie die de vereisten van de gegevensbescherming voor de landen van de EU harmoniseert en moderniseert.
* **CCPA** (de Wet van de Privacy van de Consumentenbescherming van Californië) verstrekt de ingezetenen van Californië nieuwe rechten met betrekking tot hun persoonlijke informatie en legt verantwoordelijkheden voor gegevensbescherming aan bepaalde entiteiten op die zaken in Californië leiden.
* **PDPA** (de Wet van de Bescherming van Persoonlijke Gegevens) is de privacywet die de vereisten van de gegevensbescherming voor Thailand harmoniseert en moderniseert.
* **LGPD** (Lei Geral de Proteção de Dados) is van toepassing op alle bedrijven die persoonsgegevens in Brazilië verzamelen of verwerken.
* **CASL** (Canadese anti-Spam Wet) behandelt alle berichten die naar of uit Canada worden verzonden maar omvat geen berichten die door Canada worden verpletterd;
* **VCDPA** (de Wet van de Bescherming van de Consumentengegevens van Virginia) en **CPA** (de Wet van de Privacy van Colorado) is van toepassing op alle bedrijven die zaken of doelingezetenen binnen die staten leiden.

Al deze voorschriften zijn van toepassing op Adobe Campaign-klanten die beschikken over gegevens voor gegevenssubjecten die in de bovengenoemde regio&#39;s of landen verblijven.

<!--Several Privacy capabilities are available in Adobe Campaign, including consent management, data retention settings, and rights management. See [Consent, Retention and Roles](#consent-retention-roles). In addition to this, Adobe Campaign helps facilitate your readiness as Data Controller for certain Privacy requests. See [Right to Access and Right to be Forgotten](#right-access-forgotten).-->

>[!NOTE]
>
>Voor meer informatie over persoonsgegevens en over de verschillende entiteiten die gegevens beheren (gegevenscontroller, gegevensprocessor en betrokkene) raadpleegt u [Persoonsgegevens en persona&#39;s](../../platform/using/privacy-and-recommendations.md#personal-data).

## Toegangsrecht en recht om te worden vergeten {#right-access-forgotten}

U kunt in Adobe Campaign verzoeken voor **Toegang** en **Verwijderen** afhandelen, zodat u zich gemakkelijker kunt voorbereiden op de privacyregels.

* Het **toegangsrecht** is het recht van de betrokkene om van de gegevenscontroller bevestiging te krijgen of er persoonsgegevens van de betrokkene worden verwerkt, waar en voor welk doel. De gegevenscontroller verstrekt kosteloos een kopie van de persoonsgegevens in elektronische vorm.

* Het **recht om te worden vergeten** (verwijderingsverzoek) geeft de betrokkene het recht om de gegevensbeheerder zijn of haar persoonsgegevens te laten wissen, de verdere verspreiding van de gegevens stop te zetten en eventueel de verwerking van de gegevens door derden te laten stopzetten.

Raadpleeg de [implementatiestappen](../../platform/using/privacy-requests.md) om te leren hoe u **toegangs**- en **verwijderings** verzoeken kunt maken en hoe Adobe Campaign ze verwerkt.

<!--Tutorials on Privacy management in Campaign Standard are also available [here](https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/privacy/privacy-overview.html?lang=nl-NL).
https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/privacy/privacy-overview.html-->

## Toestemming, retentie en rollen {#consent-retention-roles}

Naast de meest recente mogelijkheden voor **toegangsrecht** en **recht om te worden vergeten** biedt Adobe Campaign andere belangrijke functies die essentieel zijn voor privacy:

* [Toestemmingsbeheer](#consent-management): abonnementsfuncties voor voorkeurenbeheer
* [Dataretentie](#data-retention): dataretentieperioden in alle standaard logtabellen, er kunnen extra retentieperioden worden ingesteld met workflows
* [Rights Management](#rights-management): gegevenstoegang beheerd volgens opgegeven recht

### Toestemmingsbeheer {#consent-management}

Toestemming betekent instemming van een betrokkene om de persoonsgegevens betreffende de betrokkene te verwerken. De gegevenscontroller is verantwoordelijk voor het verkrijgen van de vereiste toestemming voor deze verwerking. Hoewel Adobe Campaign bepaalde functies kan bieden om een klant te helpen bij het beheren van de toestemming voor de service, is Adobe niet verantwoordelijk voor de toestemming. Klanten dienen samen met hun eigen juridische afdelingen hun eigen processen en praktijken vast te stellen voor de benodigde toestemming.

Vanaf het begin hebben in Adobe Campaign functies voor het helpen beheren van bepaalde aspecten van toestemming centraal gestaan. Via het abonnementsbeheerproces kunnen klanten bijhouden welke ontvangers hebben gekozen voor welk type abonnement, zoals nieuwsbrieven, dagelijkse of wekelijkse aanbiedingen of een ander type marketingprogramma.

![](assets/privacy-consent-management.png)

Raadpleeg de [gedetailleerde documentatie](../../delivery/using/managing-subscriptions.md) voor meer informatie over toestemmingsbeheer.

Naast de tools voor toestemmingsbeheer van Adobe Campaign kunt u ook nagaan of een consument ervoor heeft gekozen om zich af te melden voor de verkoop van persoonsgegevens. Zie [deze sectie](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

### Gegevensretentie {#data-retention}

Voor retentie bevatten de ingebouwde logtabellen in Campaign vooraf ingestelde retentieperioden, waarbij de gegevensopslag over het algemeen is beperkt tot zes maanden of korter.

Hieronder volgen de standaardwaarden voor retentie in de ingebouwde tabellen. Houd er rekening mee dat de retentieconfiguratie tijdens de implementatie door technische beheerders van Adobe wordt ingesteld, en dat de waarden per implementatie kunnen verschillen op basis van de vereisten van de klant.

* **Geconsolideerde tracking**: 1 jaar
* **Verzendingslogs**: 6 maanden
* **Trackinglogs**: 1 jaar
* **Verwijderde verzendingen**: 1 week
* **Geweigerde importacties**: 6 maanden
* **Bezoekersprofielen**: 1 maand
* **Aanbiedingsvoorstellen**: 1 jaar
* **Gebeurtenissen**: 1 maand
* **Statistieken van gebeurtenisverwerking**: 1 jaar
* **Gearchiveerde gebeurtenissen**: 1 jaar
* **Genegeerde pijplijngebeurtenissen**: 1 maand
* **Dynamische rapportering**: 13 maanden

Net als bij verwijderen is het met de functionaliteit van de standaardworkflow mogelijk om retentieperioden in te stellen voor elke aangepaste tabel.

Neem contact op met de consultants of technische beheerders van Adobe voor meer informatie over retentie, of als u retentie wilt instellen voor aangepaste tabellen.

### Rights Management {#rights-management}

Adobe Campaign biedt u de mogelijkheid om via verschillende standaard of aangepaste rollen de rechten te beheren die aan de verschillende Campaign-operators zijn toegewezen.

Eén voordeel is dat u zo kunt bepalen wie binnen uw bedrijf toegang heeft tot verschillende typen gegevens. Als u bijvoorbeeld verschillende marketeers voor verschillende regio’s hebt, kunt u ervoor zorgen dat elke marketeer alleen toegang heeft tot de gegevens van zijn of haar regio.

Zo kunt u met deze functionaliteit ook verschillende mogelijkheden voor elke gebruiker configureren, zoals beperken wie leveringen kan verzenden, of relevanter voor privacy: wie gegevens kan wijzigen of exporteren.

![](assets/privacy-user-management.png)

Zie de [gedetailleerde documentatie](../../platform/using/access-management.md) voor meer informatie over toegangscontrole.
