---
title: Voorwaardelijke inhoud definiëren
seo-title: Voorwaardelijke inhoud definiëren
description: Voorwaardelijke inhoud definiëren
seo-description: null
page-status-flag: never-activated
uuid: 2b49958d-6429-445d-a7dc-caaca072f4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0ca5e0f6-cc81-4da9-aecf-a095cc1a19f9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Voorwaardelijke inhoud definiëren{#defining-a-conditional-content}

U kunt de weergave van specifieke rapportitems of pagina&#39;s voorschrijven.

Pas de zichtbaarheidsinstellingen van bepaalde items aan om deze voorwaardelijk te maken. Raadpleeg de weergave [van](#conditioning-item-display)Conditioning-items voor meer informatie.

Gebruik een **[!UICONTROL Test]** tekstactiviteit om de weergave van een of meer pagina&#39;s voorwaardelijk te maken. Raadpleeg de weergave [van de pagina](#conditioning-page-display)Conditioning voor meer informatie.

## Weergave van items conditioneren {#conditioning-item-display}

Om de vertoning van een deel van een rapport voorwaardelijk te maken, moet u zijn zichtbaarheidsvoorwaarden bepalen: als deze niet worden ontmoet, zullen de punten niet worden getoond.

De zichtbaarheidsvoorwaarden kunnen afhankelijk zijn van de status van de operator, van de items die zijn geselecteerd of ingevoerd op de rapportpagina.

In [deze sectie](../../web/using/form-rendering.md#defining-fields-conditional-display)worden voorbeelden gegeven van de voorwaardelijke weergave van items op een pagina.

In het volgende voorbeeld hangt de weergavevoorwaarde af van de taal:

![](assets/reporting_display_condition.png)

## Weergave van pagina&#39;s conditioneren {#conditioning-page-display}

In het diagram van een rapport kunt u met de **[!UICONTROL Test]** activiteit de volgorde van pagina&#39;s wijzigen, afhankelijk van een of meer voorwaarden.

Deze activiteit is gebaseerd op het volgende operationele beginsel:

1. Plaats een grafiek **[!UICONTROL Test]** in een grafiek en bewerk deze.
1. Klik op de **[!UICONTROL Add]** knop om de verschillende mogelijke gevallen te maken.

   ![](assets/reporting_test_sample.png)

   Voor elk geval, wordt een outputovergang toegevoegd aan de **[!UICONTROL Test]** activiteit.

   ![](assets/reporting_test_transitions.png)

1. Selecteer **[!UICONTROL Enable default transition]** om een overgang toe te voegen, voor het geval dat aan één van de gevormde voorwaarden niet wordt voldaan.

   Zie [deze sectie](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)voor meer informatie.

U kunt een **[!UICONTROL Test]** activiteit aan het begin van het diagram plaatsen om de weergave afhankelijk te maken van bijvoorbeeld context- of operatorprofiel.
