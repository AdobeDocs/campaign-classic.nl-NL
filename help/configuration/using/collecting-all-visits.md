---
product: campaign
title: Alle bezoeken verzamelen
description: Alle bezoeken verzamelen
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# Alle bezoeken verzamelen{#collecting-all-visits}

Met de webvolgmodule die door Adobe Campaign wordt geleverd, kunt u de bezoeken aan bepaalde pagina&#39;s van de site verzamelen die door een ontvanger worden uitgevoerd in de context van het bijhouden van sites nadat u een klik in een bericht hebt geplaatst.

U kunt uw platform echter zodanig configureren dat alle bezoeken aan pagina&#39;s met een webtrackingtag worden verzameld door een gebruiker die bekend is bij het platform.

Een gebruiker die aan het platform wordt bekend is een ontvanger die reeds door een levering is gericht en die in een ontvangen bericht minstens eens heeft geklikt. Er wordt een permanent cookie gebruikt om deze ontvanger te identificeren.

>[!IMPORTANT]
>
>Het Adobe Campaign-platform is niet bedoeld als hulpmiddel voor het bijhouden van websites buiten de context van het bezoeken van de site na een klik in een bericht. Wanneer deze optie is ingeschakeld, kan dit leiden tot een zeer hoog gebruik van bronnen op de computers die uw servers hosten (omleiding, toepassing en database). U wordt aangeraden ervoor te zorgen dat uw hardwarearchitectuur dit laden ondersteunt en te voorkomen dat webtrackingtags worden geplaatst op de meest bezochte pagina&#39;s, zoals de homepage.

## Serverconfiguratie {#server-configuration}

De servers worden gevormd door bepaalde elementen van te laden **serverConf.xml** bestand. Deze bestanden worden opgeslagen in de **conf** subdirectory van de installatiemap van Adobe Campaign.

### Redirection-server {#redirection-server}

Voor de omleidingsserver stelt u de **trackWebVisitors** kenmerk van de **omleiding** element naar **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Een standaard overeenkomende campagne configureren {#configuring-a-default-matching-campaign}

Als u de trackinggegevens via uw clientconsole wilt weergeven, moet u:

* Een **dummylevering** (de leveringstoewijzing moet identiek zijn aan de toewijzing van het doelschema),
* Voer de **interne naam** van deze levering in de **NmsTracking_WebTrackingDelivery** optie.

Alle informatie over het bijhouden van de site die niet direct na een klik in een e-mailbericht wordt weergegeven, kunt u bekijken in de gemaakte dummylevering.
