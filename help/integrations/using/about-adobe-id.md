---
product: campaign
title: Maak verbinding met Adobe Campaign via Adobe ID
description: Meer informatie over de implementatie van Adobe IMS in Adobe Campaign
feature: Configuration
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
source-git-commit: ffab91fc9fa7e60973fdda930239f5836671a341
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 13%

---

# Informatie over Adobe ID {#about-adobe-id}

Met Adobe Identity Management System (IMS) kunnen beheerders de toegang van gebruikers tot toepassingen en services maken en beheren. Raadpleeg voor meer informatie over de verschillende typen Adobe-id&#39;s [deze pagina](https://helpx.adobe.com/enterprise/using/identity.html).

Campagnegebruikers kunnen verbinding maken met de Adobe Campaign-console met hun Adobe ID in plaats van met de [native verificatie van gebruikers/wachtwoorden](../../platform/using/access-management-operators.md). Deze implementatie biedt de volgende voordelen:

* Dezelfde id kan voor alle Experience Cloud-oplossingen worden gebruikt.
* De verbinding wordt bewaard wanneer het gebruiken van Adobe Campaign met verschillende integraties.
* Beveiligd beleid voor wachtwoordbeheer dan native aanmelding/wachtwoord.
* Gebruik van Federated ID-accounts (externe id-provider).

>[!IMPORTANT]
>
> In Campagne v8 is het niet toegestaan om verbinding te maken met gebruiker/wachtwoord (ook wel native verificatie genoemd). **Adobe raadt aan om deze migratie uit te voeren vanaf Campagne v7.3.5, zodat u probleemloos kunt migreren naar Campagne v8.**
>
>Leer hoe u naar Adobe IMS kunt migreren in [deze sectie](../../technotes/using/ac-ims.md).
>


<!--
>[!IMPORTANT]
>
>If you are connecting to Campaign through Adobe Identity Service (IMS), you need to upgrade to the latest build to be able to connect to Campaign after **June 30, 2021**. This upgrade is mandatory for both Campaign server and client console. 
>
>Depending on your current version, you must upgrade to one of the following releases: 
>
> * [Campaign [!DNL Gold Standard] 11](../../rn/using/gold-standard.md)
> * [Campaign 21.1.4](../../rn/using/latest-release.md)
>
>[Learn more about IMS updates](../../technotes/using/ims-updates.md)
-->

## Meer bronnen

| Nuttige pagina’s | Aanvullende bronnen |
|---|---|
| [IMS configureren](../../integrations/using/configuring-ims.md) | [Veelgestelde vragen over Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html) |
| [IMS implementeren](../../integrations/using/implementing-ims.md) | [Toegangscontrole](../../platform/using/access-management.md) |
| [IMS-probleemoplossing](../../integrations/using/ims-troubleshooting.md) | [Campagnepakketten installeren](../../installation/using/installing-campaign-standard-packages.md) |
