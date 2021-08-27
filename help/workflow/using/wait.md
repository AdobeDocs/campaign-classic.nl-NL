---
product: campaign
title: Wachten
description: Meer informatie over de workflowactiviteit Wachten
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# Wachten{#wait}

![](../../assets/common.svg)

Een **Wacht** activiteit activeert zijn overgang na een tijdvertraging van overal tussen een paar seconden en verscheidene maanden. Een wachttaak blokkeert de uitvoering van andere taken niet; de werkstroom kan taken parallel uitvoeren terwijl deze taak in behandeling is.

U kunt het label invoeren en tijd wachten met de editor, zoals in het onderstaande voorbeeld:

![](assets/edit_wait.png)

In het veld **[!UICONTROL Duration]** kan de waarde worden uitgedrukt in de eenheid van uw keuze: (volgens de regionale instellingen van de exploitant):

* Als er geen regionale instellingen zijn opgegeven: **s** voor seconden, **m** voor minuten, **h** voor uren, **d** voor dagen, **y** voor jaren. Op het moment van goedkeuring wordt de waarde automatisch omgezet in de best leesbare eenheid.

   De standaardeenheid is de dag (**d**).

* Als bijvoorbeeld de regionale instellingen worden ingesteld op &quot;Français&quot;: **s** voor seconden, **mn** voor minuten, **h** voor uren, **j** voor dagen, **m** voor maanden, **a** voor jaren. Op het moment van goedkeuring wordt de waarde automatisch omgezet in de meest leesbare eenheid, zoals in het voorbeeld hierboven **90s** werd omgezet in **1mn 30s**.

   De standaardeenheid is de dag (**d**).
