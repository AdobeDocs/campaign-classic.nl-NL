---
title: Campagne op locatie, hybride en gehoste capaciteitstabel
description: Ontdek de belangrijkste verschillen tussen gehoste en on-premise implementaties
page-status-flag: never-activated
uuid: d1c786a1-2691-4966-9108-059004050464
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 582f7ac6-cebe-4b47-8730-bbc16fd6b1bd
translation-type: tm+mt
source-git-commit: c03e90b2e2f57606749c86cda343ce5756fec122
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 18%

---


# Capability matrix {#capability-matrix-per-model}

Adobe Campaign Classic wordt geleverd met een reeks modules en opties. De beschikbaarheid van deze modules en hun gebruik kunnen van het type van plaatsing van uw installatie afhangen. In dit artikel worden enkele details weergegeven over de belangrijkste verschillen tussen volledig gehoste (Managed Services) en on-premise implementaties voor bepaalde functies.

Deze pagina toont de belangrijkste verschillen tussen gehoste (Managed Services) en on-premise implementaties. De specifieke eigenschappen van hybride plaatsingen hangen van de elementen af die door Adobe worden ontvangen en in uw gebouwen worden ontvangen.

De verschillende hostingmodellen worden geïntroduceerd [in deze sectie](../../installation/using/hosting-models.md).

## Beschikbaarheid per implementatiemodel {#capability-matrix}

| Capaciteit | Gehost | Hybride | Op locatie | Details |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Campagneserver configureren | Op aanvraag | Beschikbaar | Beschikbaar | [Meer informatie](../../installation/using/the-server-configuration-file.md) |
| BCC e-mailen | Op aanvraag | Op aanvraag | Beschikbaar | [Meer informatie](../../installation/using/email-archiving.md) |
| Uitvoerinstantie van Message Center beheren | Op aanvraag | Op aanvraag | Beschikbaar | [Meer informatie](../../message-center/using/about-transactional-messaging.md) |
| Middelsourcingsplatform beheren | Op aanvraag | Op aanvraag | Beschikbaar | [Meer informatie](../../installation/using/mid-sourcing-server.md) |
| Inbox rendering via Litmus | Op aanvraag | Op aanvraag | Beschikbaar | [Meer informatie](../../delivery/using/inbox-rendering.md) |
| Integreren met IMS (Adobe ID) | Op aanvraag | Op aanvraag | Op aanvraag | [Meer informatie](../../integrations/using/about-adobe-id.md) |
| Gegevens versleutelen/ontsleutelen voor bestandsoverdracht | Op aanvraag | Beschikbaar | Beschikbaar | [Meer informatie](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Zipping/Unzipping-bestanden | Op aanvraag | Beschikbaar | Beschikbaar | [Meer informatie](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Domeinnaamdelegatie | Op aanvraag | Op aanvraag | Niet beschikbaar | [Meer informatie](https://helpx.adobe.com/nl/campaign/kb/domain-name-delegation.html) |
| SpamAssassin installeren | Op aanvraag | Beschikbaar | Beschikbaar | [Meer informatie](../../delivery/using/spamassassin.md) |
| Toegang tot leverbaarbaarheidsrapporten | Beschikbaar | Op aanvraag | Beschikbaar | [Meer informatie](../../delivery/using/monitoring-deliverability.md) |
| LDAP-verificatie configureren | Niet beschikbaar | Beschikbaar | Beschikbaar | [Meer informatie](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data. [Meer informatie](../../platform/using/about-fda.md)

>[!CAUTION]
>
>Toegang tot een externe database via FDA is alleen mogelijk voor installaties op locatie of hybride installaties, behalve met de [Snowflake-aansluiting](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).


**Zie ook**

* [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md)
* [Release-opmerkingen](../../rn/using/latest-release.md)
* [Campaign Classic upgrades](../../rn/using/rn-overview.md)
* [Verouderde en verwijderde functies](../../rn/using/deprecated-features.md)
* [Gold Standard-releases](../../rn/using/gold-standard.md)
* [Gold Standard-programma](https://helpx.adobe.com/nl/campaign/kb/gold-standard.html)
