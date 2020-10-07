---
title: Workflows beheren
seo-title: Workflows beheren
description: Workflows beheren
seo-description: null
page-status-flag: never-activated
uuid: 8b6320c0-1aae-4acd-a698-03f9bebd916d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ee724240-c337-489d-a21b-5f3aec1f247a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 5%

---


# Workflows beheren{#managing-workflows}

Door gebrek, zijn uw nieuwe werkschema&#39;s gebaseerd op een werkschemamalplaatje dat pre-gevormd en gebaseerd op een ontvankelijke lijst (nms:ontvanger) is. Opdat zij automatisch op de douanetabel van ontvangers worden gebaseerd die in de optie **Nms_DefaultRcpSchema** van verwijzingen worden voorzien (zie het [Vormen van de interfacesectie](../../configuration/using/configuring-the-interface.md) ), moet u een nieuw werkschemamalplaatje tot stand brengen.

Maak een nieuwe sjabloon via het **[!UICONTROL Resources > Templates > Workflow templates]** knooppunt. In de eigenschappen van de sjabloon komen de afmetingen overeen met de tabel met externe ontvangers.

Door uw nieuwe werkschema&#39;s op een onlangs gecreeerd malplaatje te baseren, zal uw gepersonaliseerde lijst door gebrek voor het globale richten en filtreren van de werkschema&#39;s worden geselecteerd.

Alle activiteiten die in uw werkschema worden gebruikt zullen zo uw douanetabel zonder enige extra handconfiguratie gebruiken.

For more information on workflows, refer to [this section](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)

