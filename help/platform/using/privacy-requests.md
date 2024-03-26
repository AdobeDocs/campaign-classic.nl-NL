---
product: campaign
title: Privacyverzoeken beheren
description: Meer informatie over privacyverzoeken
feature: Privacy, Privacy Tools
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 100%

---

# Privacyverzoeken {#privacy-requests}



Raadpleeg [deze sectie](privacy-management.md) voor een algemene uitleg van privacybeheer.

Deze informatie geldt voor AVG, CCPA, PDPA en LGPD. Zie [deze sectie](privacy-management.md#privacy-management-regulations) voor meer informatie over deze regelgeving.

>[!NOTE]
>
>De opt-out voor de verkoop van persoonsgegevens, die specifiek is voor de CCPA, wordt in [deze sectie](#sale-of-personal-information-ccpa) toegelicht.

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

Doordat u in Adobe Campaign verzoeken voor toegang en verwijdering kunt afhandelen, kunt u zich gemakkelijker houden aan de privacyregels. Het **toegangsrecht** en het **recht om te worden vergeten** (verwijderingsverzoek) worden in [deze sectie](privacy-management.md#right-access-forgotten) beschreven.

Adobe Campaign biedt gegevenscontrollers twee manieren om verzoeken voor toegang tot persoonsgegevens en verwijderingsverzoeken uit te voeren:

* Via de **Adobe Campaign-interface**: voor elk verzoek om toegang tot persoonsgegevens maakt de gegevenscontroller een nieuw dergelijk verzoek in Adobe Campaign. Zie [deze sectie](privacy-requests-ui.md).
* Via de **API**: Adobe Campaign beschikt over een SOAP-API die verzoeken om toegang tot persoonsgegevens automatiseert. Zie [deze sectie](privacy-requests-api.md).

>[!NOTE]
>
>Voor meer informatie over persoonsgegevens en over de verschillende entiteiten die gegevens beheren (gegevenscontroller, gegevensprocessor en betrokkene) raadpleegt u [Persoonsgegevens en persona&#39;s](privacy-and-recommendations.md#personal-data).

## Vereisten {#prerequesites}

Adobe Campaign biedt tools voor gegevenscontrollers waarmee u verzoeken om toegang tot opgeslagen persoonsgegevens in Adobe Campaign kunt maken en verwerken. Het is echter de verantwoordelijkheid van de gegevenscontroller om de relatie met de betrokkene (e-mail, klantenservice of een webportal) af te handelen.

Daarom is het uw verantwoordelijkheid als gegevenscontroller om de identiteit te bevestigen van de betrokkene die het verzoek indient, en om te bevestigen dat de gegevens die naar de aanvrager worden teruggestuurd, over de betrokkene gaan.

## Het privacypakket installeren {#install-privacy-package}

Als u deze functie wilt gebruiken, moet u het **[!UICONTROL Privacy Data Protection Regulation]**-pakket installeren via het menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]**. Raadpleeg de [gedetailleerde documentatie](../../installation/using/installing-campaign-standard-packages.md) voor meer informatie over het installeren van pakketten.

Onder **[!UICONTROL Administration]** > **[!UICONTROL Platform]** worden twee nieuwe mappen gemaakt die specifiek zijn voor privacy:

* **[!UICONTROL Privacy Requests]**: hier kunt u uw verzoeken om toegang tot persoonsgegevens maken en de ontwikkeling ervan volgen.
* **[!UICONTROL Namespaces]**: dit is het veld dat wordt gebruikt om de betrokkene in de Adobe Campaign-database te identificeren.

![](assets/privacy-folders.png)

In **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** worden elke dag drie technische workflows uitgevoerd om verzoeken om toegang tot persoonsgegevens te verwerken.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**: deze workflow genereert de gegevens van de ontvanger die in Adobe Campaign zijn opgeslagen en maakt deze beschikbaar voor downloaden op het scherm van het verzoek om toegang tot persoonsgegevens.
* **[!UICONTROL Delete privacy requests data]**: met deze workflow verwijdert u de gegevens van de ontvanger die in Adobe Campaign zijn opgeslagen.
* **[!UICONTROL Privacy request cleanup]**: met deze workflow wist u de bestanden met toegangsverzoeken die ouder zijn dan 90 dagen.

In **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]** is het opgegeven recht **[!UICONTROL Privacy Data Right]** toegevoegd. Dit opgegeven recht is vereist voor gegevenscontrollers om privacytools te kunnen gebruiken. Hiermee kunnen ze nieuwe verzoeken maken, de ontwikkeling ervan volgen, de API gebruiken, enzovoort.

![](assets/privacy-right.png)

## Naamruimten {#namesspaces}

Voordat u privacyverzoeken maakt, moet u de naamruimte definiëren die u wilt gebruiken. Dit is de sleutel die wordt gebruikt om de betrokkene in de Adobe Campaign-database te identificeren.

Drie naamruimten zijn standaard beschikbaar: e-mail, telefoon en mobiele telefoon. Als u een andere naamruimte nodig hebt (bijvoorbeeld een aangepast veld voor ontvangers), kunt u een nieuwe naamruimte maken via **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

>[!NOTE]
>
>Voor optimale prestaties is het raadzaam om unieke naamruimten te gebruiken.
