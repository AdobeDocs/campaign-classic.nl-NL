---
product: campaign
title: Console-update
description: Console-update
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# Console-update{#console-update}



Als u **[!UICONTROL Do not request console update]** en u wilt het verzoek om een update opnieuw activeren, past u de volgende procedure toe:

1. Open de editor van de registerdatabase met behulp van de **regedit** in Windows **[!UICONTROL Start > Execute]** -menu.

   ![](assets/ncs_console_update_1.png)

1. Geef in de structuur de opties van het dialoogvenster **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** knooppunt.
1. Verwijder de **[!UICONTROL confAdvisedUpgrade]** vermelding en sluit de Register-editor.

   ![](assets/ncs_console_update_2.png)
