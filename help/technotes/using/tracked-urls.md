---
product: campaign
title: Probleem met handtekening van bijgehouden URL's
description: Probleem met handtekening van bijgehouden URL's
feature: Technote
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 31%

---

# Probleem met handtekening van bijgehouden URL&#39;s {#tracked-urls}



Na recente wijzigingen kunnen bijgehouden URL&#39;s mislukken wanneer een URL-handtekening actief is in de campagne. De impact van het probleem verschilt per e-mailaccount. Sommige bedrijven hebben namelijk specifieke beveiligingstools die verbindingen kunnen beïnvloeden en het URL-handtekeningmechanisme kunnen veranderen.

Daarom wordt u door de Adobe aangeraden het handtekeningmechanisme voor het bijhouden van koppelingen uit te schakelen. Deze procedure verhelpt oude het volgen verbindingen behalve degenen die met een dubbele ontsnaping worden ontvangen.

Afmeldkoppelingen kunnen net als andere koppelingen mislukken. De frequentie verschilt van host tot host, maar is minder dan 1%.

**Heeft dit gevolgen voor u?**

Om de beveiliging te verbeteren, is het handtekeningmechanisme voor het bijhouden van koppelingen in e-mails geïntroduceerd in [Campagne Gold Standard 8](../../rn/using/gold-standard.md#gs8) - April 2020 - en wordt toegelaten door gebrek voor alle klanten die Bouwstijl 19.1.4 (9032@3a9dc9c) en Campagne 20.2 beginnen.

Als uw omgeving wordt uitgevoerd op een van de hieronder vermelde versies, kunt u dit beïnvloeden:

* Gold Standard 8 tot 11. [Meer informatie](../../rn/using/gold-standard.md#gs-8)
* Campagne 21.1.1 (build 9277) tot en met 21.1.2 (build 9282). [Meer informatie](../../rn/using/latest-release.md)
* Campagne 20.3.1 (build 9228) tot 20.3.3 (build 9234)-releases.
* Campagne 20.2.1 (build 9178) tot 20.2.4 (build 9187)-releases.
* Campagne 20.1.1 (build 9122) tot en met 21.1.3 (build 9124).
* Campagne 19.2.2 (build 9080) tot en met 19.2.3 (build 9081).
* Campagne 19.1.5 (build 9033) tot en met 19.1.7 (build 9036).


Leer hoe u uw versie kunt controleren [in deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hoe kan ik bijwerken?**

Als **gehoste klant**, werkt Adobe samen met u om uw configuratie binnenkort bij te werken.

Als **on-premise/hybride klant**, moet u uw configuratie bijwerken.

Volg de onderstaande stap:

1. In de [serverconfiguratiebestand](../../installation/using/the-server-configuration-file.md) (serverConf.xml), wijzigen **signEmailLinks** tot **false**.
1. De opdracht opnieuw starten **nlserver** service.
1. Start de webserver op de trackingserver opnieuw (apache2 op Debian, httpd op CentOS/RedHat, IIS op Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>De **config-`<instance>`.xml** bestand overschrijft het **serverConf.xml** instellingen. Als de **signEmailLinks** aanwezig is in het dialoogvenster  **config-`<instance>`.xml** waarbij **instance** is de naam van uw instantie), moet het ook worden aangezet **false**.
>

**Wat is de impact?**

De uitvaltijd voor onderhoud bedraagt maximaal 25 minuten en tijdens deze periode werken alle verzendingen, trackingkoppelingen en API-aanroepen niet.

Zodra de update is uitgevoerd, werken alle koppelingen weer naar behoren.

>[!NOTE]
>
>Voor vragen over deze wijzigingen neemt u contact op met de [Adobe-klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>
