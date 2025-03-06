---
product: campaign
title: Wachten
description: Meer informatie over de workflowactiviteit Wachten
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# Wachten{#wait}



A **wacht** activiteit activeert zijn overgang na een tijdvertraging van overal tussen een paar seconden en verscheidene maanden. Een wachttaak blokkeert niet de uitvoering van andere taken; de workflow kan taken parallel uitvoeren terwijl deze taak in behandeling is.

U kunt het label invoeren en tijd wachten met de editor, zoals in het onderstaande voorbeeld:

![](assets/edit_wait.png)

In het veld **[!UICONTROL Duration]** kan de waarde worden uitgedrukt in de eenheid van uw keuze: (volgens de regionale instellingen van de operator):

* Als de regionale montages niet worden gespecificeerd: **s** voor seconden, **m** voor notulen, **h** voor uren, **d** voor dagen, **y** voor jaren. Op het moment van goedkeuring wordt de waarde automatisch omgezet in de best leesbare eenheid.

  De standaardeenheid is de dag (**d**).

* Terwijl als, bijvoorbeeld, de regionale montages aan &quot;Français&quot;worden geplaatst: **s** voor seconden, **mn** voor notulen, **h** voor uren, **j** voor dagen, **m** voor maanden, **a** voor jaren. Op het tijdstip van goedkeuring, wordt de waarde automatisch omgezet in de leesbaarste eenheid, zoals in het voorbeeld hierboven **90s** werd omgezet in **1mn 30s**.

  De standaardeenheid is de dag (**d**).
