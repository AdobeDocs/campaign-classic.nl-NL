---
product: campaign
title: Voorwaardelijke content definiëren
description: Voorwaardelijke content definiëren
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 8%

---

# Voorwaardelijke content definiëren{#defining-a-conditional-content}

![](../../assets/common.svg)

U kunt de weergave van specifieke rapportitems of pagina&#39;s voorschrijven.

Pas de zichtbaarheidsinstellingen van bepaalde items aan om deze voorwaardelijk te maken. Voor meer op dit, verwijs naar [Conditioning puntvertoning](#conditioning-item-display).

Als u de weergave van een of meer pagina&#39;s voorwaardelijk wilt maken, gebruikt u een **[!UICONTROL Test]**-tekstactiviteit. Raadpleeg [Paginaweergave conditioneren](#conditioning-page-display) voor meer informatie.

## Weergave van items conditioneren {#conditioning-item-display}

Om de vertoning van een deel van een rapport voorwaardelijk te maken, moet u zijn zichtbaarheidsvoorwaarden bepalen: als deze niet worden ontmoet, zullen de punten niet worden getoond.

De zichtbaarheidsvoorwaarden kunnen afhankelijk zijn van de status van de operator, van de items die zijn geselecteerd of ingevoerd op de rapportpagina.

De voorbeelden die de voorwaardelijke vertoning van punten op een pagina tonen worden verstrekt in [deze sectie](../../web/using/form-rendering.md#defining-fields-conditional-display).

In het volgende voorbeeld hangt de weergavevoorwaarde af van de taal:

![](assets/reporting_display_condition.png)

## Paginaweergave van conditionering {#conditioning-page-display}

In de grafiek van een rapport, laat de **[!UICONTROL Test]** activiteit u de opeenvolging van pagina&#39;s afhankelijk van één of meerdere voorwaarden veranderen.

Deze activiteit is gebaseerd op het volgende operationele beginsel:

1. Plaats een **[!UICONTROL Test]** in een grafiek en bewerk het.
1. Klik op de knop **[!UICONTROL Add]** om de verschillende mogelijke gevallen te maken.

   ![](assets/reporting_test_sample.png)

   Voor elk geval, wordt een outputovergang toegevoegd aan **[!UICONTROL Test]** activiteit.

   ![](assets/reporting_test_transitions.png)

1. Selecteer **[!UICONTROL Enable default transition]** om een overgang toe te voegen, voor het geval één van de gevormde voorwaarden niet wordt voldaan.

   Raadpleeg [deze sectie](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display) voor meer informatie.

Een **[!UICONTROL Test]** activiteit kan aan het begin van de grafiek worden geplaatst om de vertoning afhankelijk van context of exploitantprofiel bijvoorbeeld te voorwaarde.
