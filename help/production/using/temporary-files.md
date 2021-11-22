---
product: campaign
title: Tijdelijke bestanden
description: Tijdelijke bestanden
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# Tijdelijke bestanden{#temporary-files}

![](../../assets/v7-only.svg)

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
