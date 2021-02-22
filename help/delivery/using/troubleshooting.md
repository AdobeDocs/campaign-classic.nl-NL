---
solution: Campaign Classic
product: campaign
title: Problemen oplossen
description: Problemen oplossen
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 22f44f5723ab35e95caa438583fe06314c763ba1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 4%

---


# Problemen oplossen{#troubleshooting}

Als uw mobiele apparaat is verbonden met Wi-Fi en u ontvangt geen meldingen, controleert u of de FCM-/APN-poorten niet worden geblokkeerd door uw firewall.

**Android**: Het mobiele apparaat maakt verbinding met de FCM-servers op poorten 5228 tot en met 5230. Daarom moet u de firewall zo configureren dat verbinding met FCM wordt toegestaan. De open havens zijn: 5228 (de meest gebruikte), 5229 en 5230.

**iOS**:

HTTP/2-connector: u moet communicatie aan en van de volgende servers toestaan:

* api.push.apple.com: poort 443
* api.development.push.apple.com: poort 443

>[!NOTE]
>
>Raadpleeg [De mobiele toepassing configureren in Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md) voor meer informatie over de twee connectors.
