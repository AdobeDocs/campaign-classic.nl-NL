---
solution: Campaign Classic
product: campaign
title: Problemen oplossen
description: Problemen oplossen
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 3%

---


# Problemen oplossen{#troubleshooting}

Als uw mobiele apparaat is verbonden met Wi-Fi en u ontvangt geen meldingen, controleert u of de FCM-/APN-poorten niet worden geblokkeerd door uw firewall.

**Android**: Het mobiele apparaat maakt verbinding met de FCM-servers op poorten 5228 tot en met 5230. Daarom moet u de firewall zo configureren dat verbinding met FCM wordt toegestaan. De open havens zijn: 5228 (de meest gebruikte), 5229 en 5230.

**iOS**:

Binaire aansluiting: om berichten te verzenden, moet u binnenkomend en uitgaand verkeer van TCP op haven 2195 machtigen. De apparaten die met de duwdienst worden verbonden moeten het binnenkomende en uitgaande verkeer van TCP op haven 5223 machtigen.

HTTP/2-connector: u moet communicatie aan en van de volgende servers toestaan:

* api.push.apple.com: poort 443
* api.development.push.apple.com: poort 443

>[!NOTE]
>
>Voor meer informatie over de twee schakelaars, verwijs naar het [Vormen van de mobiele toepassing in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).
