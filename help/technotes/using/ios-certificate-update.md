---
product: campaign
title: TechNote - Apple Push Notification service server certificate update
description: Apple Push Notification service server certificate update
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Apple Push Notification service server certificate update {#apns-certificate-update}



Op 29 maart 2021 heeft een infrastructuurupdate van de Apple Push Notification Service (APNs) gevolgen voor het Adobe Campaign Classic iOS-kanaal. Een wijziging in de configuratie van het besturingssysteem is **verplicht** om uitval van het iOS-pushkanaal te voorkomen.

Meer informatie over APNs-wijzigingen [op deze pagina](https://developer.apple.com/news/?id=7gx0a2lp).

Als gehoste klant is geen actie nodig: Adobe heeft het nieuwe basiscertificaat al in uw omgeving opgenomen.

Als klant op locatie/hybride klant moet u uw configuratie bijwerken om een naadloze overgang te garanderen **vóór 29 maart 2021**.

Voer de volgende stappen uit om het nieuwe certificaat op te nemen:

1. Download de **AAACCertificateServices 5/12/2020** basiscertificaat [van deze pagina](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Controleer of het AAA-certificaat aanwezig is in zowel uw OS- als JAVA-betrouwbaarheid. Zo niet, voegt u deze toe.

1. Start Adobe Campaign Web Service opnieuw:

   ```
   nlserver restart web
   ```
