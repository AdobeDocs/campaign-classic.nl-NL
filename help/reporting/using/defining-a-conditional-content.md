---
product: campaign
title: Voorwaardelijke content definiëren
description: Voorwaardelijke content definiëren
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Reporting, Monitoring
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 8%

---

# Voorwaardelijke content definiëren{#defining-a-conditional-content}



U kunt de weergave van specifieke rapportitems of pagina&#39;s voorschrijven.

Pas de zichtbaarheidsinstellingen van bepaalde items aan om deze voorwaardelijk te maken. Raadpleeg voor meer informatie hierover [Weergave van Condition-item](#conditioning-item-display).

Als u de weergave van een of meer pagina&#39;s voorwaardelijk wilt maken, gebruikt u een **[!UICONTROL Test]** type activiteit. Raadpleeg voor meer informatie hierover [Weergave van voorwaardepagina](#conditioning-page-display).

## Weergave van Condition-item {#conditioning-item-display}

Om de vertoning van een deel van een rapport voorwaardelijk te maken, moet u zijn zichtbaarheidsvoorwaarden bepalen: als deze niet worden voldaan aan, zullen de punten niet worden getoond.

De zichtbaarheidsvoorwaarden kunnen afhankelijk zijn van de status van de operator, van de items die zijn geselecteerd of ingevoerd op de rapportpagina.

Voorbeelden van de voorwaardelijke weergave van items op een pagina zijn te vinden in [deze sectie](../../web/using/form-rendering.md#defining-fields-conditional-display).

In het volgende voorbeeld hangt de weergavevoorwaarde af van de taal:

![](assets/reporting_display_condition.png)

## Weergave van voorwaardepagina {#conditioning-page-display}

In het overzicht van een verslag worden de **[!UICONTROL Test]** Met activiteit kunt u de volgorde van pagina&#39;s wijzigen afhankelijk van een of meer voorwaarden.

Deze activiteit is gebaseerd op het volgende operationele beginsel:

1. Een **[!UICONTROL Test]** in een grafiek en bewerk deze.
1. Klik op de knop **[!UICONTROL Add]** om de verschillende mogelijke gevallen te maken.

   ![](assets/reporting_test_sample.png)

   Voor elk geval, wordt een outputovergang toegevoegd aan **[!UICONTROL Test]** activiteit.

   ![](assets/reporting_test_transitions.png)

1. Selecteer de **[!UICONTROL Enable default transition]** om een overgang toe te voegen, voor het geval dat één van de gevormde voorwaarden niet wordt voldaan.

   Raadpleeg [deze sectie](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display) voor meer informatie.

A **[!UICONTROL Test]** activiteit kan aan het begin van de grafiek worden geplaatst om de vertoning afhankelijk van context of exploitantprofiel bijvoorbeeld te conditioneren.
