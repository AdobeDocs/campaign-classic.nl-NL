---
title: Incrementele query
seo-title: Incrementele query
description: Incrementele query
seo-description: null
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: aa192d975a08246ba684940fff3d33853d7d9345
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---


# Incrementele query{#incremental-query}

Met een incrementele query kunt u periodiek een doel selecteren op basis van een criterium, terwijl de personen die al voor dit criterium zijn aangewezen, worden uitgesloten.

De reeds gerichte bevolking wordt opgeslagen in het geheugen door werkschemainstantie en door activiteit, d.w.z. twee werkschema&#39;s begonnen van het zelfde malplaatje delen niet het zelfde logboek. Anderzijds, zullen twee taken die op de zelfde stijgende vraag voor de zelfde werkschemainstantie worden gebaseerd het zelfde logboek gebruiken.

De vraag wordt bepaald op de zelfde manier zoals voor standaardvragen, maar zijn uitvoering is gepland.

**Verwante onderwerpen:**

* [Hoofdlettergebruik: Driemaandelijkse lijstupdate die een stijgende vraag gebruikt](../../workflow/using/quarterly-list-update.md)
* [Een query maken](../../workflow/using/query.md#creating-a-query)

>[!CAUTION]
>
>Als het resultaat van een stijgende vraag aan **0** tijdens één van zijn uitvoeringen gelijk is, wordt het werkschema gepauzeerd tot de volgende geprogrammeerde uitvoering van de vraag. De overgangen en de activiteiten die volgen op de stijgende vraag worden daarom niet verwerkt vóór de volgende uitvoering.

Dit doet u als volgt:

1. Selecteer op het **[!UICONTROL Scheduling & History]** tabblad de **[!UICONTROL Schedule execution]** optie. De taak blijft actief zodra het is gecreeerd en zal slechts op de tijden worden teweeggebracht die door het programma voor het uitvoeren van de vraag worden gespecificeerd. Als de optie echter is uitgeschakeld, wordt de query onmiddellijk **en in één keer** uitgevoerd.
1. Klik op de knop **[!UICONTROL Change]**. 

   In het **[!UICONTROL Schedule editing wizard]** venster kunt u het type frequentie, de terugkerende gebeurtenis en de geldigheidsperiode van de gebeurtenis configureren.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Klik **[!UICONTROL Finish]** om het schema op te slaan.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. In de onderste sectie van het **[!UICONTROL Scheduling & History]** tabblad kunt u het aantal dagen selecteren waarmee u rekening wilt houden in de geschiedenis.

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

Deze reeks van drie waarden identificeert de bevolking die door de vraag wordt gericht. **[!UICONTROL tableName]** is de naam van de lijst die de doelherkenningstekens registreert, **[!UICONTROL schema]** is het schema van de bevolking (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de lijst.
