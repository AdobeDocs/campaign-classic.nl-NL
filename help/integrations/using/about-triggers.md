---
product: campaign
title: Informatie over Adobe Experience Cloud-triggers
description: Aan de slag met Adobe Experience Cloud Triggers-implementatie
feature: Triggers
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 7%

---

# Werken met Triggers voor campagnes en Experiencen Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] is een integratie tussen Adobe Campaign en Adobe Analytics door middel van de pijpleiding. De pijplijn haalt gebruikersacties of trekkers van uw website terug. Een achterlating van een winkelwagen is een voorbeeld van een trigger. Triggers worden in Adobe Campaign verwerkt om e-mails in bijna real-time te verzenden.

>[!CAUTION]
>
>Deze mogelijkheid is niet rechtstreeks beschikbaar als onderdeel van het product. Voor deze implementatie werkt u samen met uw Adobe/klantenservice. U kunt dan de in dit [page](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] Voer marketingacties uit binnen een korte tijdspanne na de actie van een gebruiker. De gemiddelde responstijd is minder dan een uur.

Het staat voor meer flexibele integratie toe aangezien de configuratie minimaal is en een derde niet betrokken is.
Ook wordt steun verleend aan grote verkeersvolumes zonder dat dit van invloed is op de prestaties van marketingactiviteiten. De integratie kan bijvoorbeeld een miljoen triggers per uur verwerken.

![](assets/do-not-localize/book.png) Ontdek hoe u [een trigger voor een Experience Cloud maken](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html) en kritieke consumentengedragingen identificeren, definiëren en bewaken.

## [!DNL Triggers] architectuur {#triggers-architecture}

De [!DNL pipelined] -proces wordt altijd uitgevoerd op de Adobe Campaign-marketingserver. Het verbindt met de pijpleiding, wint de gebeurtenissen terug, en verwerkt hen onmiddellijk.

![](assets/triggers_2.png)

De [!DNL pipelined] proces het programma opent aan het Experience Cloud gebruikend de authentificatiedienst en verzendt een privé sleutel. De verificatieservice retourneert een token. Het token wordt gebruikt voor verificatie bij het ophalen van de gebeurtenissen.

## Vereisten {#adobe-io-prerequisites}

Controleer voordat u met deze implementatie begint of:

* een geldige **Organisatie-id**: de organisatie-id is de unieke id in de Adobe Experience Cloud, die bijvoorbeeld wordt gebruikt voor de service VisitorID en de IMS Single-Sign On (SSO). [Meer informatie](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=nl)
* a **Toegang voor ontwikkelaars** aan uw organisatie. De systeembeheerder van de organisatie moet de **Ontwikkelaars toevoegen aan één productprofiel** procedure [op deze pagina](https://helpx.adobe.com/enterprise/using/manage-developers.html) om ontwikkelaarstoegang voor `Analytics - {tenantID}` Productprofiel van het Adobe Analytics-product dat is gekoppeld aan Triggers.

## Implementatiestappen {#implement}

Voer de volgende stappen uit om campagne- en Experience Cloud-triggers te implementeren:

1. Maak een OAuth-project. [Meer informatie](oauth-technical-account.md#oauth-service)

1. Voeg uw OAuth projectgeloofsbrieven in Adobe Campaign toe. [Meer informatie](oauth-technical-account.md#add-credentials)

1. Werk het authentificatietype aan het de consoleproject van de Ontwikkelaar in het configuratiedossier bij **config-&lt; instance-name >.xml** als volgt:

   ```
   <pipelined ... authType="imsJwtToken"  ... />
   ```

   Voer vervolgens een `config -reload` en het opnieuw opstarten van de [!DNL pipelined] voor de in aanmerking te nemen wijzigingen.

