---
title: Tijdelijke bestanden
seo-title: Tijdelijke bestanden
description: Tijdelijke bestanden
seo-description: null
page-status-flag: never-activated
uuid: ae7ec619-e93f-41fb-ba7c-fcbcf4cba84f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f18237b0-ef54-46a6-9c14-34b038f9de18
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# Tijdelijke bestanden{#temporary-files}

Als de foutenmeldingen zoals het volgende (vooral in leveringslogboeken) verschijnen wanneer het systeem in productie wordt gezet:

**Kan de naam van het bestand &#39;/tmp/tmp0000.tmp&#39; niet wijzigen in /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)**

De oorzaak is als volgt:

Adobe Campaign genereert tijdelijke bestanden onder **/tmp** en wijzigt vervolgens de naam van de bestanden om deze naar **/usr/local/neolane/nl6/var** te verplaatsen. Deze fout treedt op wanneer beide mappen (**/tmp** en **/usr/local/neolane/nl6/var**, in feite een symbolische koppeling naar **/var/nl6**) overeenkomen met verschillende apparaten. De **opdracht df** wordt gebruikt voor verificatie.

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

