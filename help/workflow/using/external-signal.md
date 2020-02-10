---
title: Extern signaal
seo-title: Extern signaal
description: Extern signaal
seo-description: null
page-status-flag: never-activated
uuid: dbe6624a-70cf-4ac4-adfd-bc72db9bb3f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 3739593f-056c-4165-87ef-63c812bd3c43
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Extern signaal{#external-signal}

De **Externe signaalactiviteit** laat u uitvoering van een reeks taken in een werkschema aan een programma teweegbrengen.

Wanneer een &quot;Externe signaaltaak&quot;wordt geactiveerd, wordt het voor onbepaalde tijd gepauzeerd of tot het eind van de gespecificeerde tijdspanne. De overgang ervan wordt geactiveerd door de SOAP-aanroep **PostEvent(sessionToken, workflowId, activiteit, overgang, parameters, voltooid).** De **[!UICONTROL complete]** parameter staat de taak toe om worden gebeëindigd, zodat zal het niet op verdere vraag reageren.

Raadpleeg de online documentatie over SOAP-oproepen voor meer informatie over de PostEvent-functie.

U kunt deze activiteit vormen om gebeurtenissen te bepalen als geen signaal wordt ontvangen. Hiervoor bewerkt u de activiteit en klikt u op het **[!UICONTROL Expiration]** tabblad. Klik op de **[!UICONTROL Insert]** knop om een gebeurtenis te maken en te configureren.

![](assets/edit_signal.png)

De configuratie van verlopen wordt gedetailleerd beschreven in [Verlopen](../../workflow/using/executing-a-workflow.md#expirations).

In het veld **Vertraging** kunt u een vertraging bij verlopen opgeven in de gewenste eenheden. Zie [Wacht](../../workflow/using/wait.md).

Elke regel vertegenwoordigt een type vervaldatum en valt samen met een overgang.

![](assets/external_sign_diag.png)

