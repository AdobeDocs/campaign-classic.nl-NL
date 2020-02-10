---
title: Wachten
seo-title: Wachten
description: Wachten
seo-description: null
page-status-flag: never-activated
uuid: 55e4f15d-8d69-45b1-b842-5ccdfdedf550
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 41bcfe67-b5d6-4ee6-9f8a-6a7a208e2036
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Wachten{#wait}

Een **Wacht** activiteit activeert zijn overgang na een tijdvertraging van overal tussen een paar seconden en verscheidene maanden. Een wachttaak blokkeert de uitvoering van andere taken niet; de werkstroom kan taken parallel uitvoeren terwijl deze taak in behandeling is.

U kunt het label invoeren en tijd wachten met de editor, zoals in het onderstaande voorbeeld:

![](assets/edit_wait.png)

In het **[!UICONTROL Duration]** veld kan de waarde worden uitgedrukt in de eenheid van uw keuze: (volgens de regionale instellingen van de exploitant):

* Als er geen regionale instellingen zijn opgegeven: **s** voor seconden, **m** voor minuten, **h** voor uren, **d** voor dagen, **y** voor jaren. Op het moment van goedkeuring wordt de waarde automatisch omgezet in de best leesbare eenheid.

   De standaardeenheid is de dag (**d**).

* Als bijvoorbeeld de regionale instellingen worden ingesteld op &quot;Français&quot;: **s** voor seconden, **mn** voor minuten, **h** voor uren, **j** voor dagen, **m** **** voor maanden,a voor jaren. Op het moment van goedkeuring wordt de waarde automatisch geconverteerd naar de meest leesbare eenheid, zoals in het voorbeeld boven **de jaren 90** werd omgezet in **1 mn 30s**.

   De standaardeenheid is de dag (**d**).

