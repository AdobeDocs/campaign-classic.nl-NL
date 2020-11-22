---
solution: Campaign Classic
product: campaign
title: Extern signaal
description: Meer informatie over de activiteit van de externe signaalworkflow
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---


# Extern signaal{#external-signal}

De **Externe signaalactiviteit** laat u uitvoering van een reeks taken in een werkschema aan een programma teweegbrengen.

Wanneer een &quot;Externe signaaltaak&quot;wordt geactiveerd, wordt het voor onbepaalde tijd gepauzeerd of tot het eind van de gespecificeerde tijdspanne. De overgang ervan wordt geactiveerd door de SOAP-aanroep **PostEvent(sessionToken, workflowId, activiteit, overgang, parameters, voltooid).** De **[!UICONTROL complete]** parameter staat de taak toe om worden gebeëindigd, zodat zal het niet op verdere vraag reageren.

Raadpleeg de online documentatie over SOAP-oproepen voor meer informatie over de PostEvent-functie.

U kunt deze activiteit vormen om gebeurtenissen te bepalen als geen signaal wordt ontvangen. Hiervoor bewerkt u de activiteit en klikt u op het **[!UICONTROL Expiration]** tabblad. Klik op de **[!UICONTROL Insert]** knop om een gebeurtenis te maken en te configureren.

![](assets/edit_signal.png)

De configuratie van verlopen wordt gedetailleerd beschreven in [Verlopen](../../workflow/using/defining-approvals.md).

In het veld **Vertraging** kunt u een vertraging bij verlopen opgeven in de gewenste eenheden. Zie [Wacht](../../workflow/using/wait.md).

Elke regel vertegenwoordigt een type vervaldatum en valt samen met een overgang.

![](assets/external_sign_diag.png)

