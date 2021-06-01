---
product: campaign
title: Workflows beheren
description: Workflows beheren
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 4%

---

# Workflows beheren{#managing-workflows}

Door gebrek, zijn uw nieuwe werkschema&#39;s gebaseerd op een werkschemamalplaatje dat pre-gevormd en gebaseerd op een ontvankelijke lijst (nms:ontvanger) is. Opdat zij automatisch op de douanetabel van ontvangers worden gebaseerd die in **Nms_DefaultRcpSchema** optie van verwijzingen worden voorzien (zie [Het vormen van de interface](../../configuration/using/configuring-the-interface.md) sectie), moet u een nieuw werkschemamalplaatje creëren.

Maak een nieuwe sjabloon via het knooppunt **[!UICONTROL Resources > Templates > Workflow templates]**. In de eigenschappen van de sjabloon komen de afmetingen overeen met de tabel met externe ontvangers.

Door uw nieuwe werkschema&#39;s op een onlangs gecreeerd malplaatje te baseren, zal uw gepersonaliseerde lijst door gebrek voor het globale richten en filtreren van de werkschema&#39;s worden geselecteerd.

Alle activiteiten die in uw werkschema worden gebruikt zullen zo uw douanetabel zonder enige extra handconfiguratie gebruiken.

Raadpleeg [deze sectie](../../workflow/using/about-workflows.md) voor meer informatie over workflows.

![](assets/cfg_external_table_workflow.png)
