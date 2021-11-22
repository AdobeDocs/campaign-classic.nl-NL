---
product: campaign
title: Campagne op locatie, hybride en gehoste capaciteitstabel
description: Ontdek de belangrijkste verschillen tussen gehoste en on-premise implementaties
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 19%

---

# Capaciteitsmatrix per model{#capability-matrix-per-model}

![](../../assets/v7-only.svg)

Adobe Campaign Classic wordt geleverd met een reeks modules en opties. De beschikbaarheid van deze modules en hun gebruik kunnen van het type van plaatsing van uw installatie afhangen. In dit artikel worden enkele details weergegeven over de belangrijkste verschillen tussen volledig gehoste (Managed Services) en on-premise implementaties voor bepaalde functies.

Deze pagina toont de belangrijkste verschillen tussen gehoste (Managed Services) en on-premise implementaties. De specifieke eigenschappen van hybride plaatsingen hangen van de elementen af die door Adobe worden ontvangen en in uw gebouwen worden ontvangen.

De verschillende hostingmodellen zijn geïntroduceerd [in deze sectie](../../installation/using/hosting-models.md).

## Beschikbaarheid per implementatiemodel {#capability-matrix}

| Capaciteit | Gehost | Hybride | Op locatie | Details |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Campaign-server configureren | Op aanvraag | Beschikbaar | Beschikbaar | [Meer informatie](../../installation/using/the-server-configuration-file.md) |
| BCC e-mailen | Op aanvraag | Op aanvraag | Beschikbaar | [Meer informatie](../../installation/using/email-archiving.md) |
| Uitvoerinstantie van Message Center beheren | Op aanvraag | Op aanvraag | Beschikbaar | [Meer informatie](../../message-center/using/about-transactional-messaging.md) |
| Middelsourcingsplatform beheren | Op aanvraag | Op aanvraag | Beschikbaar | [Meer informatie](../../installation/using/mid-sourcing-server.md) |
| Inbox rendering via Litmus | Op aanvraag | Op aanvraag | Beschikbaar | [Meer informatie](../../delivery/using/inbox-rendering.md) |
| Integreren met IMS (Adobe ID) | Op aanvraag | Op aanvraag | Op aanvraag | [Meer informatie](../../integrations/using/about-adobe-id.md) |
| Gegevens versleutelen/ontsleutelen voor bestandsoverdracht | Op aanvraag | Beschikbaar | Beschikbaar | [Meer informatie](../../platform/using/unzip-decrypt.md) |
| Zipping/Unzipping-bestanden | Op aanvraag | Beschikbaar | Beschikbaar | [Meer informatie](../../platform/using/unzip-decrypt.md) |
| Domeinnaamdelegatie | Op aanvraag | Op aanvraag | Niet beschikbaar | [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=nl) |
| SpamAssassin installeren | Op aanvraag | Beschikbaar | Beschikbaar | [Meer informatie](../../delivery/using/spamassassin.md) |
| Toegang tot leverbaarbaarheidsrapporten | Beschikbaar | Op aanvraag | Beschikbaar | [Meer informatie](../../delivery/using/monitoring-deliverability.md) |
| LDAP-verificatie configureren | Niet beschikbaar | Beschikbaar | Beschikbaar | [Meer informatie](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign biedt de **Federale gegevenstoegang** (FDA) optie om informatie te verwerken die is opgeslagen in een of meer externe databases: u hebt toegang tot externe gegevens zonder de structuur van Adobe Campaign-gegevens te wijzigen. [Meer informatie](../../installation/using/about-fda.md)

>[!CAUTION]
>
>Toegang tot een externe database via FDA is alleen mogelijk voor installaties op locatie of hybride installaties, behalve voor [Snowflake-aansluiting](../../installation/using/configure-fda-snowflake.md).


**Zie ook**

* [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md)
* [Release-opmerkingen](../../rn/using/latest-release.md)
* [Campaign Classic upgrades](../../rn/using/rn-overview.md)
* [Afgeschafte en verwijderde functies](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard]-releases ](../../rn/using/gold-standard.md)
* [[!DNL Gold Standard] programma](../../rn/using/gs-overview.md)
