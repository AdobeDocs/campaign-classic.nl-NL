---
product: campaign
title: Campagne op locatie, hybride en gehoste capaciteitstabel
description: Ontdek de belangrijkste verschillen tussen gehoste en on-premise implementaties
feature: Installation, Architecture
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 17%

---

# Capaciteitsmatrix per model{#capability-matrix-per-model}



Adobe Campaign Classic wordt geleverd met een reeks modules en opties. De beschikbaarheid van deze modules en hun gebruik kunnen van het type van plaatsing van uw installatie afhangen. In dit artikel worden enkele details weergegeven over de belangrijkste verschillen tussen volledig gehoste (Managed Services) en on-premise implementaties voor bepaalde functies.

Deze pagina toont de belangrijkste verschillen tussen gehoste (Managed Services) en on-premise implementaties. De specifieke eigenschappen van hybride plaatsingen hangen van de elementen af die door Adobe worden ontvangen en in uw gebouwen worden ontvangen.

De verschillende ontvangende modellen worden geïntroduceerd [ in deze sectie ](../../installation/using/hosting-models.md).

## Beschikbaarheid per implementatiemodel {#capability-matrix}

| Capaciteit | Gehost | Hybride | Op locatie | Details |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Campagneserver configureren | Op aanvraag | Beschikbaar | Beschikbaar | [Meer informatie](../../installation/using/the-server-configuration-file.md) |
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

Adobe Campaign verstrekt de **Federated optie van de Toegang van Gegevens** (FDA) om informatie te verwerken die in één of meerdere externe gegevensbestanden wordt opgeslagen: u kunt tot externe gegevens toegang hebben zonder de structuur van de gegevens van Adobe Campaign te veranderen. [Meer informatie](../../installation/using/about-fda.md)

>[!CAUTION]
>
>Compatibele externe databasesystemen zijn afhankelijk van uw hostingmodel. Leer meer in [ de Matrijs van de Verenigbaarheid van de Campagne ](../../rn/using/compatibility-matrix.md).
>

**zie ook**

* [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md)
* [Aanvullende informatie ](../../rn/using/latest-release.md)
* [Campaign Classic upgrades](../../rn/using/rn-overview.md)
* [Afgeschafte en verwijderde functies](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard]-releases ](../../rn/using/gold-standard.md)
