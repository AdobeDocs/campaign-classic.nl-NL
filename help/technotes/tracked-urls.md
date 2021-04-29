---
solution: Campaign Classic
product: campaign
title: TechNote
description: TechNote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: e1b09767a8eed3a7dc90e4db0429238d86d39570
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 5%

---

# Probleem {#tracked-urls} met handtekening van bijgehouden URL&#39;s

Na recente wijzigingen kunnen bijgehouden URL&#39;s mislukken wanneer een URL-handtekening actief is in de campagne. Sommige mailboxes kunnen meer effect hebben dan andere, aangezien sommige bedrijven specifieke veiligheidshulpmiddelen hebben die verbindingen kunnen beïnvloeden en het URL handtekeningsmechanisme veranderen.

Daarom raadt Adobe u aan het handtekeningmechanisme voor het bijhouden van koppelingen uit te schakelen. Deze procedure verhelpt oude het volgen verbindingen behalve degenen die met een dubbele ontsnaping worden ontvangen.

Koppelingen zonder abonnement kunnen mislukken, net als andere koppelingen. De frequentie is variabel van host tot host, maar is minder dan 1%.

**Heb je invloed op?**

Om de beveiliging te verbeteren, is het handtekeningmechanisme voor het bijhouden van koppelingen in e-mailberichten geïntroduceerd in [Campagne Gold Standard 8](../rn/using/gold-standard.md#gs8) - april 2020 - en is standaard ingeschakeld voor alle klanten die beginnen met Build 19.1.4 (9032@3a9dc9c) en Campagne 20.2.

Als uw omgeving wordt uitgevoerd op een van de hieronder vermelde versies, kunt u dit beïnvloeden:

* Gold Standard 8 tot 11. [Meer informatie](../rn/using/gold-standard.md#gs-8)
* Campagne 21.1.1 (build 9277) tot en met 21.1.2 (build 9282). [Meer informatie](../rn/using/latest-release.md)
* Campagne 20.3.1 (build 9228) tot 20.3.3 (build 9234)-releases. [Meer informatie](../rn/using/release--20-3.md)
* Campagne 20.2.1 (build 9178) tot 20.2.3 (build 9182)-releases. [Meer informatie](../rn/using/release--20-2.md)
* Campagne 20.1.1 (build 9122) tot en met 21.1.3 (build 9124). [Meer informatie](../rn/using/release--20-1.md)
* Campagne 19.2.2 (build 9080) tot en met 19.2.3 (build 9081). [Meer informatie](../rn/using/release--19-2.md)
* Campagne 19.1.5 (build 9033) tot en met 19.1.7 (build 9036). [Meer informatie](../rn/using/release--19-1.md)

Leer hoe u uw versie [in deze sectie ](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) controleert.

**Hoe kan ik bijwerken?**

Als **gehoste klant**, zal Adobe met u samenwerken om uw configuratie binnenkort bij te werken.

Als **on-premise/hybride klant**, moet u uw configuratie bijwerken.

Volg de onderstaande stap:

1. Wijzig **signEmailLinks** in **false** in het configuratiebestand [server](../installation/using/the-server-configuration-file.md) (serverConf.xml).
1. Start de **nlserver**-service opnieuw.
1. Start de webserver op de trackingserver opnieuw (apache2 op Debian, httpd op CentOS/RedHat, IIS op Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>Het **config-`<instance>`.xml** dossier treedt **serverConf.xml** montages met voeten. Als **signEmailLinks** aanwezig is in **config-`<instance>`.xml** (waarbij **instance** de naam van uw instantie is), moet het ook aan **false** worden gedraaid.


**Wat is de impact?**

Het onderhoud vereist maximaal 25 minuten downtime en tijdens deze periode werken alle leveringen, koppelingen en API-aanroepen niet.

Wanneer de update is uitgevoerd, werken alle koppelingen naar behoren.

>[!NOTE]
>
>Voor vragen over deze wijzigingen neemt u contact op met [Adobe Customer Care](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
