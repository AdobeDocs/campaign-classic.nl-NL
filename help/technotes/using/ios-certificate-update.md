---
product: campaign
title: TechNote - Certificaat van de Apple Push Notification-service
description: Update voor servercertificaat van Apple Push Notification-service
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0c97efef21bfd3b8671847c3e1c27bb76cf167e4
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Update voor servercertificaat van Apple Push Notification-service {#apns-certificate-update}

![](../../assets/v7-only.svg)

Op 29 maart 2021 heeft een APN-infrastructuurupdate (Apple Push Notification service) invloed op het Adobe Campaign Classic iOS-kanaal. Een wijziging in de configuratie van het besturingssysteem is **verplicht** om uitval van het iOS-pushkanaal te voorkomen.

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
