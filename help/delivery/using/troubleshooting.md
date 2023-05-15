---
product: campaign
title: Push Troubleshooting
description: Push Troubleshooting
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Push
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 2%

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
>Voor meer informatie over de twee schakelaars, verwijs naar [De mobiele toepassing configureren in Adobe Campaign](configuring-the-mobile-application.md).
