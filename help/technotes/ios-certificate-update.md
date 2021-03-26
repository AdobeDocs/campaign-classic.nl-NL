---
solution: Campaign Classic
product: campaign
title: TechNote
description: TechNote
hide: false
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 08c6e84e07da2811c91aa58ddf40c5781de2b163
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Update voor servercertificaat van Apple Push Notification-service {#apns-certificate-update}

Op 29 maart 2021 is een APN-infrastructuurupdate (Apple Push Notification service) van invloed op het Adobe Campaign Classic iOS-kanaal. Een wijziging in de configuratie van het besturingssysteem is **verplicht** om uitval van het iOS-pushkanaal te voorkomen.

Meer informatie over APNs verandert [op deze pagina](https://developer.apple.com/news/?id=7gx0a2lp).

Als gehoste klant is geen actie nodig: Adobe heeft het nieuwe basiscertificaat al in uw omgeving opgenomen.

Als klant op locatie/hybride dient u uw configuratie bij te werken voor een naadloze overgang **vóór 29 maart 2021**.

Voer de volgende stappen uit om het nieuwe certificaat op te nemen:

1. Download **AACCertificateServices 5/12/2020** basiscertificaat [van deze pagina](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Controleer of het AAA-certificaat aanwezig is in zowel uw OS- als JAVA-betrouwbaarheid. Zo niet, voegt u deze toe.

1. Start Adobe Campaign Web Service opnieuw:

   ```
   nlserver restart web
   ```

