---
product: campaign
title: Console-update
description: Console-update
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# Console-update{#console-update}

![](../../assets/v7-only.svg)

Als u de optie **[!UICONTROL Do not request console update]** hebt geselecteerd en u wilt het verzoek om de update opnieuw activeren, past u de volgende procedure toe:

1. Open de editor van de registerdatabase met de opdracht **regedit** in het menu **[!UICONTROL Start > Execute]** van Windows.

   ![](assets/ncs_console_update_1.png)

1. Geef in de structuur de opties van het knooppunt **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** weer.
1. Verwijder het **[!UICONTROL confAdvisedUpgrade]**-item en sluit de Register-editor.

   ![](assets/ncs_console_update_2.png)
