---
product: campaign
title: Push Troubleshooting
description: Push Troubleshooting
feature: Push, Troubleshooting
role: User
hide: true
hidefromtoc: true
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 89e350c727fb9379d28916f79d9749f22fd4974f
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Problemen oplossen{#troubleshooting}

Als uw mobiele apparaat is verbonden met Wi-Fi en u ontvangt geen meldingen, controleert u of de FCM-/APN-poorten niet worden geblokkeerd door uw firewall.

**Android**: Het mobiele apparaat verbindt met de servers FCM op havens 5228 tot 5230. Daarom moet u de firewall zo configureren dat verbinding met FCM wordt toegestaan. De open poorten zijn: 5228 (de meest gebruikte), 5229 en 5230.

**iOS**:

HTTP/2-connector: u moet communicatie toestaan van en naar de volgende servers:

* api.push.apple.com: poort 443
* api.development.push.apple.com: poort 443

>[!NOTE]
>
>Voor meer informatie over de twee schakelaars, verwijs naar [ Vormend de mobiele toepassing in Adobe Campaign ](configuring-the-mobile-application.md).
