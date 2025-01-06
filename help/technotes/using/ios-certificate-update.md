---
product: campaign
title: TechNote - Apple Push Notification service server certificate update
description: Apple Push Notification service server certificate update
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0143e0d6ebcdbd96d183ddd0c7f07beb149a9670
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Apple Push Notification service server certificate update {#apns-certificate-update}



Op 17 oktober 2024 had een infrastructuurupdate van de Apple Push Notification Service (APNs) gevolgen voor Adobe Campaign Classic iOS-kanaal. Een OS configuratieverandering is **verplicht** om de stroomonderbreking van het de duwkanaal van iOS te vermijden.

Leer meer over APNs verandert [ in deze pagina ](https://developer.apple.com/news/?id=09za8wzy).

Als gehoste klant is geen actie nodig: Adobe heeft het nieuwe basiscertificaat al in uw omgeving opgenomen.

Als klant op-gebouw/hybride, moet u uw configuratie bijwerken om een naadloze overgang **vóór 24 februari, 2025** te verzekeren.

Voer de volgende stappen uit om het nieuwe certificaat op te nemen:

1. Download **SHA-2 Woot: Het certificaat van de CertificatieAutoriteit van USERTrust RSA** wortelcertificaat [ van deze pagina ](https://www.sectigo.com/knowledge-base/detail/Sectigo-Intermediate-Certificates/kA01N000000rfBO).

1. Controleer of het AAA-certificaat aanwezig is in zowel uw OS- als JAVA-betrouwbaarheid. Zo niet, voegt u deze toe.

1. Start Adobe Campaign Web Service opnieuw:

   ```
   nlserver restart web
   ```
