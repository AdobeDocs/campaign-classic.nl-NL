---
solution: Campaign Classic
product: campaign
title: Console-update
description: Console-update
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---


# Console-update{#console-update}

Als u de optie **[!UICONTROL Do not request console update]** hebt geselecteerd en u wilt het verzoek om de update opnieuw activeren, past u de volgende procedure toe:

1. Open de editor van de registerdatabase met de opdracht **regedit** in het menu **[!UICONTROL Start > Execute]** van Windows.

   ![](assets/ncs_console_update_1.png)

1. Geef in de structuur de opties van het knooppunt **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** weer.
1. Verwijder het **[!UICONTROL confAdvisedUpgrade]**-item en sluit de Register-editor.

   ![](assets/ncs_console_update_2.png)

