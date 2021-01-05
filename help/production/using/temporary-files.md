---
solution: Campaign Classic
product: campaign
title: Tijdelijke bestanden
description: Tijdelijke bestanden
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---


# Tijdelijke bestanden{#temporary-files}

Foutberichten zoals de volgende kunnen worden weergegeven (met name in leveringslogboeken) wanneer het systeem in productie wordt genomen:

*Kan de naam van het bestand &#39;/tmp/tmp0000.tmp&#39; niet wijzigen in /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)*

De oorzaak is als volgt:

Adobe Campaign genereert tijdelijke bestanden onder **/tmp** en wijzigt vervolgens de naam van de bestanden om deze naar **/usr/local/neolane/nl6/var** te verplaatsen. Deze fout treedt op wanneer beide mappen (**/tmp** en **/usr/local/neolane/nl6/var**, wat in feite een symbolische koppeling is naar **/var/nl6**) overeenkomen met verschillende apparaten. De opdracht **df** wordt gebruikt voor verificatie.

U verhelpt dit probleem door de tijdelijke bestanden te genereren op hetzelfde apparaat als het doelapparaat. Bijvoorbeeld door uit te voeren:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

en voegt vervolgens:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```

