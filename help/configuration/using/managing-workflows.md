---
solution: Campaign Classic
product: campaign
title: Workflows beheren
description: Workflows beheren
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 4%

---


# Workflows beheren{#managing-workflows}

Door gebrek, zijn uw nieuwe werkschema&#39;s gebaseerd op een werkschemamalplaatje dat pre-gevormd en gebaseerd op een ontvankelijke lijst (nms:ontvanger) is. Opdat zij automatisch op de douanetabel van ontvangers worden gebaseerd die in de optie **Nms_DefaultRcpSchema** van verwijzingen worden voorzien (zie het [Vormen van de interfacesectie](../../configuration/using/configuring-the-interface.md) ), moet u een nieuw werkschemamalplaatje tot stand brengen.

Maak een nieuwe sjabloon via het **[!UICONTROL Resources > Templates > Workflow templates]** knooppunt. In de eigenschappen van de sjabloon komen de afmetingen overeen met de tabel met externe ontvangers.

Door uw nieuwe werkschema&#39;s op een onlangs gecreeerd malplaatje te baseren, zal uw gepersonaliseerde lijst door gebrek voor het globale richten en filtreren van de werkschema&#39;s worden geselecteerd.

Alle activiteiten die in uw werkschema worden gebruikt zullen zo uw douanetabel zonder enige extra handconfiguratie gebruiken.

For more information on workflows, refer to [this section](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)

