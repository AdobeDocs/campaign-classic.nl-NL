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

Pas de volgende procedure toe als u de **[!UICONTROL Do not request console update]** optie hebt geselecteerd en u het updateverzoek opnieuw wilt activeren:

1. Open de redacteur van het registratiegegevensbestand gebruikend het **regedit** bevel in het **[!UICONTROL Start > Execute]** menu van Vensters.

   ![](assets/ncs_console_update_1.png)

1. Geef in de structuur de opties van het **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** knooppunt weer.
1. Verwijder het **[!UICONTROL confAdvisedUpgrade]** item en sluit de Register-editor.

   ![](assets/ncs_console_update_2.png)

