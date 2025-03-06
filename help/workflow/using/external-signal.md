---
product: campaign
title: Extern signaal
description: Meer informatie over de activiteit van de externe signaalworkflow
feature: Workflows
hide: true
hidefromtoc: true
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# Extern signaal{#external-signal}



De **Externe signaal** activiteit laat u uitvoering van een reeks taken in een werkschema aan een programma teweegbrengen.

Wanneer een &quot;Externe signaaltaak&quot;wordt geactiveerd, wordt het voor onbepaalde tijd gepauzeerd of tot het eind van de gespecificeerde tijdspanne. Zijn overgang wordt geactiveerd door SOAP vraag **PostEvent (sessionToken, workflowId, activiteit, overgang, parameters, volledig).** Met de parameter **[!UICONTROL complete]** kan de taak worden voltooid, zodat deze niet reageert op volgende aanroepen.

Raadpleeg de online documentatie over SOAP voor meer informatie over de PostEvent-functie.

U kunt deze activiteit vormen om gebeurtenissen te bepalen als geen signaal wordt ontvangen. Hiervoor bewerkt u de activiteit en klikt u op het tabblad **[!UICONTROL Expiration]** . Klik op de knop **[!UICONTROL Insert]** om een gebeurtenis te maken en te configureren.

![](assets/edit_signal.png)

De configuratie van verlopen is gedetailleerd in [ Verlopen ](defining-approvals.md).

Het **gebied van de Vertraging** laat u een vervalvertraging in de eenheden van uw keus specificeren. Zie [ wachten ](wait.md).

Elke regel vertegenwoordigt een type vervaldatum en valt samen met een overgang.

![](assets/external_sign_diag.png)
