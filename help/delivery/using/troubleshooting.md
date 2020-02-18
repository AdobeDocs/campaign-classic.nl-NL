---
title: Problemen oplossen
seo-title: Problemen oplossen
description: Problemen oplossen
seo-description: null
page-status-flag: never-activated
uuid: 02bd48cf-3928-4817-97b0-1e64cc8ad8ef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: b64c9729-cfe2-4d02-8c59-9e53efd34a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fa2b6890d3c9eaf7b4b6521b2edfb494faa4798c

---


# Problemen oplossen{#troubleshooting}

Als uw mobiele apparaat is verbonden met Wi-Fi en u ontvangt geen meldingen, controleert u of de FCM-/APNS-poorten niet worden geblokkeerd door uw firewall.

**Android**: Het mobiele apparaat maakt verbinding met de FCM-servers op poorten 5228 tot en met 5230. Daarom moet u de firewall zo configureren dat verbinding met FCM wordt toegestaan. De open havens zijn: 5228 (de meest gebruikte), 5229 en 5230.

**iOS**:

Binaire aansluiting: om berichten te verzenden, moet u binnenkomend en uitgaand verkeer van TCP op haven 2195 machtigen. De apparaten die met de duwdienst worden verbonden moeten het binnenkomende en uitgaande verkeer van TCP op haven 5223 machtigen.

HTTP/2-connector: u moet communicatie aan en van de volgende servers toestaan:

* api.push.apple.com: poort 443
* api.development.push.apple.com: poort 443

>[!NOTE]
>
>Voor meer informatie over de twee schakelaars, verwijs naar het [Vormen van de mobiele toepassing in de Campagne](../../delivery/using/configuring-the-mobile-application.md)van Adobe.
