---
product: campaign
title: Tijdelijke bestanden
description: Tijdelijke bestanden
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 9%

---

# Tijdelijke bestanden{#temporary-files}



Foutberichten zoals de volgende kunnen worden weergegeven (met name in leveringslogboeken) wanneer het systeem in productie wordt genomen:

*Kan de naam van het bestand &#39;/tmp/tmp0000.tmp&#39; niet wijzigen in /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)*

De oorzaak is als volgt:

Adobe Campaign genereert tijdelijke bestanden onder **/tmp** en wijzigt vervolgens de naam van de **/usr/local/neolane/nl6/var**. Deze fout treedt op wanneer beide mappen (**/tmp** en **/usr/local/neolane/nl6/var**, die in feite een symbolische koppeling is naar **/var/nl6**) komt overeen met verschillende apparaten. De **df** wordt gebruikt voor verificatie.

U verhelpt dit probleem door de tijdelijke bestanden te genereren op hetzelfde apparaat als het doelapparaat.

Voer bijvoorbeeld het volgende uit:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

Voeg vervolgens toe:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
