---
product: campaign
title: Vertakking
description: Meer informatie over de workflowactiviteit van Fork
feature: Workflows
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# Vertakking{#fork}



U kunt de **[!UICONTROL Fork]** activiteit om veelvoudige uitgaande overgangen tot stand te brengen en verscheidene activiteiten onafhankelijk binnen het zelfde werkschema te leiden.

>[!IMPORTANT]
>
>De uitgaande overgangen die u na een **[!UICONTROL Fork]** activiteit wordt niet gelijktijdig uitgevoerd. Dit gedrag kan van invloed zijn op de workflowprestaties. Gebruik de **[!UICONTROL Fork]** activiteit als u verscheidene activiteiten onafhankelijk moet uitvoeren. Naar keuze, kunt u zich bij de uitgaande activiteiten vóór het verdere deel van het werkschema aansluiten.

Om een **[!UICONTROL Fork]** de activiteit en de daarmee verband houdende activiteiten volgen de volgende stappen :

1. Open de **[!UICONTROL Fork]** en definieert u de naam en het label van de uitgaande overgangen.

   ![](assets/s_user_segmentation_fork.png)

1. Open elke uitgaande overgang en vorm het.
1. Naar keuze, om zich bij uitgaande overgangen aan te sluiten, voeg een EN-lid activiteit toe. [Meer informatie](and-join.md).

   Het volgende gedeelte van de workflow wordt alleen uitgevoerd na voltooiing van de gecombineerde uitgaande overgangen.

## Voorbeeld: segmentatie

In dit voorbeeld worden verschillende e-mails verzonden naar verschillende bevolkingsgroepen. A **[!UICONTROL Fork]** activiteit wordt gebruikt na een vraag, om twee acties parallel uit te voeren:

* Het queryresultaat opslaan
* Segmenteer het resultaat om meerdere leveringen te verzenden

  ![De vorkactiviteit volgt de doorsnede van twee vragen en voorafgaat een activiteit van de lijstupdate en een gespleten activiteit.](assets/wkf_fork_example.png)

De workflow omvat de volgende activiteiten:

1. **[!UICONTROL Query]** activiteit

   Er zijn twee bevolkingsgroepen geselecteerd: vrouwen en Parisiërs.

1. **[!UICONTROL Intersection]** activiteit

   De doorsnede van de zoekresultaten, dat wil zeggen, Parisiaanse vrouwen, wordt geselecteerd.

1. **[!UICONTROL Fork]** activiteit

   De berekende populatie wordt bespaard en parallel verdeeld in twee groepen:

   1. Parisiaanse vrouwen tussen de 18 en 40 jaar
   1. Parisiaanse vrouwen ouder dan 40

1. **[!UICONTROL Delivery]** activiteit

   Er wordt een ander e-mailbericht verzonden naar elke bevolkingsgroep.

## Kwestie gebruiken: een e-mail voor een geboortedatum verzenden

Een terugkerende e-mail wordt verzonden naar een lijst met ontvangers op hun verjaardag. A **[!UICONTROL Fork]** Deze activiteit wordt gebruikt om ontvangers op te nemen die op 29 februari op een schrikkeljaar geboren zijn. [Meer informatie](sending-a-birthday-email.md) over dit gebruiksgeval.

![De vorkactiviteit volgt een testactiviteit en voorafgaat twee vraagactiviteiten.](assets/birthday-workflow_usecase_1.png)

## Hoofdlettergebruik: inhoud automatiseren met een workflow

Het maken en leveren van een inhoudsblok wordt geautomatiseerd. A **[!UICONTROL Fork]** wordt gebruikt om het doel te berekenen en tegelijkertijd de inhoud te maken. [Meer informatie](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) over dit gebruiksgeval.

![De vorkactiviteit volgt een leveringsactiviteit en voorafgaat een vraagactiviteit en een activiteit van het inhoudsbeheer, die allebei door een EN-sluit zich aan bij activiteit worden aangesloten.](../../delivery/using/assets/d_ncs_content_workflow10.png)

U kunt elke uitgaande overgangen dan vormen, dan hen samenvoegen gebruikend een [AND-join](and-join.md) activiteit, indien nodig. Op deze manier wordt de rest van de workflow slechts één keer uitgevoerd **[!UICONTROL Fork]** de uitgaande overgangen van de activiteit worden gebeëindigd.

## Verwante onderwerpen

* [AND-join-activiteit](and-join.md)
* [Kwestie gebruiken: verjaardagsbericht](sending-a-birthday-email.md)
* [Hoofdlettergebruik: inhoud maken en leveren](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)