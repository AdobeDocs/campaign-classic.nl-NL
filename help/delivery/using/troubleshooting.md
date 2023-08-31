---
product: campaign
title: Push Troubleshooting
description: Push Troubleshooting
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Push, Troubleshooting
role: User
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 8%

---

# Problemen oplossen{#troubleshooting}

Als uw mobiele apparaat is verbonden met Wi-Fi en u ontvangt geen meldingen, controleert u of de FCM-/APN-poorten niet worden geblokkeerd door uw firewall.

**Android**: Het mobiele apparaat maakt verbinding met de FCM-servers op poorten 5228 tot en met 5230. Daarom moet u de firewall zo configureren dat verbinding met FCM wordt toegestaan. De open poorten zijn: 5228 (de meest gebruikte), 5229 en 5230.

**iOS**:

HTTP/2-connector: u moet communicatie toestaan van en naar de volgende servers:

* api.push.apple.com: poort 443
* api.development.push.apple.com: poort 443

>[!NOTE]
>
>Voor meer informatie over de twee schakelaars, verwijs naar [De mobiele toepassing configureren in Adobe Campaign](configuring-the-mobile-application.md).
