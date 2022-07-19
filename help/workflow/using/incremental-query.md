---
product: campaign
title: Incrementele query
description: Meer informatie over de activiteit van de Incrementele queryworkflow
feature: Workflows, Targeting Activity
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---

# Incrementele query{#incremental-query}

![](../../assets/v7-only.svg)

Met een incrementele query kunt u periodiek een doel selecteren op basis van een criterium, terwijl de personen die al voor dit criterium zijn aangewezen, worden uitgesloten.

De reeds gerichte bevolking wordt opgeslagen in het geheugen door werkschemainstantie en door activiteit, d.w.z. twee werkschema&#39;s begonnen van het zelfde malplaatje delen niet het zelfde logboek. Anderzijds, zullen twee taken die op de zelfde stijgende vraag voor de zelfde werkschemainstantie worden gebaseerd het zelfde logboek gebruiken.

De vraag wordt bepaald op de zelfde manier zoals voor standaardvragen, maar zijn uitvoering is gepland.

**Verwante onderwerpen:**

* [Hoofdlettergebruik: Driemaandelijkse lijstupdate die een stijgende vraag gebruikt](quarterly-list-update.md)
* [Een query maken](query.md#creating-a-query)

>[!CAUTION]
>
>Als het resultaat van een incrementele query gelijk is aan **0** tijdens één van zijn uitvoeringen, wordt het werkschema gepauzeerd tot de volgende geprogrammeerde uitvoering van de vraag. De overgangen en de activiteiten die volgen op de stijgende vraag worden daarom niet verwerkt vóór de volgende uitvoering.

Dit doet u als volgt:

1. In de **[!UICONTROL Scheduling & History]** selecteert u de **[!UICONTROL Schedule execution]** optie. De taak blijft actief zodra het is gecreeerd en zal slechts op de tijden worden teweeggebracht die door het programma voor het uitvoeren van de vraag worden gespecificeerd. Als de optie echter is uitgeschakeld, wordt de query direct uitgevoerd **en in één keer**.
1. Klik op de knop **[!UICONTROL Change]**.

   In de **[!UICONTROL Schedule editing wizard]** kunt u het type frequentie, de terugkerende gebeurtenis en de geldigheidsperiode van de gebeurtenis configureren.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Klikken **[!UICONTROL Finish]** om het programma op te slaan.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. De onderste sectie van de **[!UICONTROL Scheduling & History]** kunt u het aantal dagen selecteren waarmee u rekening wilt houden in de geschiedenis.

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

Deze reeks van drie waarden identificeert de bevolking die door de vraag wordt gericht. **[!UICONTROL tableName]** is de naam van de lijst die de doelherkenningstekens registreert, **[!UICONTROL schema]** is het schema van de populatie (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de tabel.
