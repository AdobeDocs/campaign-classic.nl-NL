---
product: campaign
title: Incrementele query
description: Meer informatie over de activiteit van de Incrementele queryworkflow
feature: Workflows, Targeting Activity
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 3%

---

# Incrementele query{#incremental-query}



Met een incrementele query kunt u periodiek een doel selecteren op basis van een criterium, terwijl de personen die al voor dit criterium zijn aangewezen, worden uitgesloten.

De reeds gerichte bevolking wordt opgeslagen in het geheugen door werkschemainstantie en door activiteit, d.w.z. twee werkschema&#39;s begonnen van het zelfde malplaatje delen niet het zelfde logboek. Anderzijds, zullen twee taken die op de zelfde stijgende vraag voor de zelfde werkschemainstantie worden gebaseerd het zelfde logboek gebruiken.

De vraag wordt bepaald op de zelfde manier zoals voor standaardvragen, maar zijn uitvoering is gepland.

**Verwante onderwerpen:**

* [Hoofdlettergebruik: driemaandelijkse lijst bijwerken met een incrementele query](quarterly-list-update.md)
* [Een query maken](query.md#creating-a-query)

>[!CAUTION]
>
>Als het resultaat van een stijgende vraag aan **0** tijdens één van zijn uitvoeringen gelijk is, wordt het werkschema gepauzeerd tot de volgende geprogrammeerde uitvoering van de vraag. De overgangen en de activiteiten die volgen op de stijgende vraag worden daarom niet verwerkt vóór de volgende uitvoering.

Dit doet u als volgt:

1. Selecteer op het tabblad **[!UICONTROL Scheduling & History]** de optie **[!UICONTROL Schedule execution]** . De taak blijft actief zodra het is gecreeerd en zal slechts op de tijden worden teweeggebracht die door het programma voor het uitvoeren van de vraag worden gespecificeerd. Nochtans, als de optie gehandicapt is, wordt de vraag uitgevoerd onmiddellijk **en in één gaat**.
1. Klik op de knop **[!UICONTROL Change]**.

   In het venster **[!UICONTROL Schedule editing assistant]** kunt u het type frequentie, terugkerende gebeurtenis en geldigheidsperiode van de gebeurtenis configureren.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Klik op **[!UICONTROL Finish]** om het schema op te slaan.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. In de onderste sectie van het tabblad **[!UICONTROL Scheduling & History]** kunt u het aantal dagen selecteren waarmee u rekening wilt houden in de geschiedenis.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

     Reeds beoogde ontvangers kunnen worden geregistreerd gedurende een maximumaantal dagen vanaf de dag waarop zij als doelgroep zijn aangemeld. Als deze waarde nul is, worden de ontvangers nooit gezuiverd van het logboek.

   * **[!UICONTROL Keep history when starting]**

     Met deze optie kunt u het logbestand niet leegmaken wanneer de activiteit is ingeschakeld.

   * **[!UICONTROL SQL table name]**

     Met deze parameter kunt u de standaard SQL-tabel met de historiegegevens overladen.

## Uitvoerparameters {#output-parameters}

* tableName
* schema
* recCount

Deze reeks van drie waarden identificeert de bevolking die door de vraag wordt gericht. **[!UICONTROL tableName]** is de naam van de tabel waarin de doel-id&#39;s worden vastgelegd. **[!UICONTROL schema]** is het schema van de populatie (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de tabel.
