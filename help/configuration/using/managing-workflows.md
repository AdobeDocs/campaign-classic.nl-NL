---
product: campaign
title: Workflows beheren
description: Workflows beheren
feature: Workflows, Configuration
role: Data Engineer, Developer
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 4%

---

# Workflows beheren{#managing-workflows}



Door gebrek, zijn uw nieuwe werkschema&#39;s gebaseerd op een werkschemamalplaatje dat pre-gevormd en gebaseerd op een ontvankelijke lijst (nms:ontvanger) is. Om ervoor te zorgen dat ze automatisch worden gebaseerd op de aangepaste lijst met ontvangers waarnaar wordt verwezen in het dialoogvenster **Nms_DefaultRcpSchema** (zie [De interface configureren](../../configuration/using/configuring-the-interface.md) ), moet u een nieuw werkstroomsjabloon maken.

Een nieuwe sjabloon maken via het dialoogvenster **[!UICONTROL Resources > Templates > Workflow templates]** knooppunt. In de eigenschappen van de sjabloon komen de afmetingen overeen met de tabel met externe ontvangers.

Door uw nieuwe werkschema&#39;s op een onlangs gecreeerd malplaatje te baseren, zal uw gepersonaliseerde lijst door gebrek voor het globale richten en filtreren van de werkschema&#39;s worden geselecteerd.

Alle activiteiten die in uw werkschema worden gebruikt zullen zo uw douanetabel zonder enige extra handconfiguratie gebruiken.

Voor meer informatie over workflows raadpleegt u [deze sectie](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
