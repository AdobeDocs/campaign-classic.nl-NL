---
product: campaign
title: Informatie over Adobe Experience Cloud-triggers
description: Aan de slag met de implementatie van Adobe Experience Cloud Triggers
feature: Triggers
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 7%

---

# Werken met campagne- en Experience Cloud-triggers{#about-adobe-experience-triggers}

[!DNL Triggers] is een integratie tussen Adobe Campaign en Adobe Analytics die de pijpleiding gebruikt. De pijplijn haalt gebruikersacties of trekkers van uw website terug. Een achterlating van een winkelwagen is een voorbeeld van een trigger. Triggers worden in Adobe Campaign verwerkt om e-mails in bijna real-time te verzenden.

>[!CAUTION]
>
>Deze mogelijkheid is niet rechtstreeks beschikbaar als onderdeel van het product. Voor deze implementatie werkt u samen met uw Adobe-vertegenwoordiger/klantenservice. U zult dan de stappen kunnen volgen die in deze [ worden gedetailleerd pagina ](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] voert marketingacties uit binnen een korte tijdsspanne na de actie van een gebruiker. De gemiddelde responstijd is minder dan een uur.

Het staat voor meer flexibele integratie toe aangezien de configuratie minimaal is en een derde niet betrokken is.
Ook wordt steun verleend aan grote verkeersvolumes zonder dat dit van invloed is op de prestaties van marketingactiviteiten. De integratie kan bijvoorbeeld een miljoen triggers per uur verwerken.

![](assets/do-not-localize/book.png) ontdekt hoe te om [ een trekker van Experience Cloud ](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html?lang=nl-NL) tot stand te brengen en, kritiek consumentengedrag te identificeren te bepalen en te controleren.

## [!DNL Triggers] architectuur {#triggers-architecture}

Het [!DNL pipelined] -proces wordt altijd uitgevoerd op de Adobe Campaign-marketingserver. Het verbindt met de pijpleiding, wint de gebeurtenissen terug, en verwerkt hen onmiddellijk.

![](assets/triggers_2.png)

Het [!DNL pipelined] -proces meldt zich aan bij de Experience Cloud met behulp van een verificatieservice en verzendt een persoonlijke sleutel. De verificatieservice retourneert een token. Het token wordt gebruikt voor verificatie bij het ophalen van de gebeurtenissen.

## Vereisten {#adobe-io-prerequisites}

Controleer voordat u met deze implementatie begint of:

* a geldig **herkenningsteken van de Organisatie**: identiteitskaart van de Organisatie is het unieke herkenningsteken binnen Adobe Experience Cloud, dat bijvoorbeeld voor de dienst VisitorID en IMS wordt gebruikt Single-Sign On (SSO). [Meer informatie](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=nl)
* a **toegang van de Ontwikkelaar** tot uw Organisatie. De beheerder van het Systeem van de organisatie moet **volgen ontwikkelaars aan één enkel productprofiel** gedetailleerde procedure [ in deze pagina ](https://helpx.adobe.com/nl/enterprise/using/manage-developers.html) toevoegen om ontwikkelaartoegang voor het `Analytics - {tenantID}` Profiel van het Product van Adobe Analytics verbonden aan Trekkers te verlenen.

## Implementatiestappen {#implement}

Voer de volgende stappen uit om campagne- en Experience Cloud-triggers te implementeren:

1. Maak een OAuth-project. [Meer informatie](oauth-technical-account.md#oauth-service)

1. Voeg uw OAuth projectgeloofsbrieven in Adobe Campaign toe. [Meer informatie](oauth-technical-account.md#add-credentials)

1. Werk het authentificatietype aan het de consoleproject van de Ontwikkelaar in het configuratiedossier **config-&lt; instance-name >.xml** als volgt bij:

   ```
   <pipelined ... authType="imsJwtToken"  ... />
   ```

   Voer vervolgens een `config -reload` en een nieuwe start van de [!DNL pipelined] uit om rekening te houden met de wijzigingen.

