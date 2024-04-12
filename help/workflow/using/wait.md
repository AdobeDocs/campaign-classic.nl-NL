---
product: campaign
title: Wachten
description: Meer informatie over de workflowactiviteit Wachten
feature: Workflows
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# Wachten{#wait}



A **Wachten** de activiteit activeert zijn overgang na een tijdvertraging van overal tussen een paar seconden en verscheidene maanden. Een wachttaak blokkeert niet de uitvoering van andere taken; de workflow kan taken parallel uitvoeren terwijl deze taak in behandeling is.

U kunt het label invoeren en tijd wachten met de editor, zoals in het onderstaande voorbeeld:

![](assets/edit_wait.png)

In de **[!UICONTROL Duration]** veld, kan de waarde worden uitgedrukt in de eenheid van uw keuze: (volgens de regionale instellingen van de operator):

* Als er geen regionale instellingen zijn opgegeven: **s** gedurende seconden, **m** gedurende minuten, **h** gedurende uren, **d** dagen, **y** jarenlang. Op het moment van goedkeuring wordt de waarde automatisch omgezet in de best leesbare eenheid.

  De standaardeenheid is de dag (**d**).

* Als bijvoorbeeld de regionale instellingen worden ingesteld op &quot;Français&quot;: **s** gedurende seconden, **mn** gedurende minuten, **h** gedurende uren, **j** dagen, **m** gedurende maanden, **a** jarenlang. Op het ogenblik van de goedkeuring wordt de waarde automatisch omgezet in de best leesbare eenheid, zoals in het bovenstaande voorbeeld **jaren 90** is omgezet in **1mn 30s**.

  De standaardeenheid is de dag (**d**).
