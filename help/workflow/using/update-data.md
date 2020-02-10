---
title: Gegevens bijwerken
seo-title: Gegevens bijwerken
description: Gegevens bijwerken
seo-description: null
page-status-flag: never-activated
uuid: 5f3ab7c8-175a-4b06-a50c-edc97b226e3c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: c94ce5b7-aa8a-4ea2-845d-68c9c7dc2a7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Gegevens bijwerken{#update-data}

Een **update van het gegevenstype** voert een massa-update van de gebieden in het gegevensbestand uit.

## Type bewerking {#operation-type}

In het **[!UICONTROL Operation type]** veld kunt u kiezen welk proces wordt uitgevoerd op de gegevens in de database:

* **[!UICONTROL Insert or update]**: gegevens toevoegen of bijwerken als deze al zijn toegevoegd.
* **[!UICONTROL Insert]**: alleen gegevens toevoegen.
* **[!UICONTROL Update]**: alleen gegevens bijwerken.
* **[!UICONTROL Update and merge collections]**: gegevens bijwerken en een &quot;hoofdrecord&quot; kiezen, en vervolgens elementen koppelen die zijn gekoppeld aan de duplicaten in deze hoofdrecord. Duplicaten kunnen vervolgens worden verwijderd zonder weeselementen in bijlage te maken.
* **[!UICONTROL Delete]**: gegevens verwijderen.

![](assets/s_advuser_update_data_1.png)

In het **[!UICONTROL Batch size]** veld kunt u het aantal inkomende overgangselementen selecteren dat moet worden bijgewerkt. Als u bijvoorbeeld 500 opgeeft, worden de eerste 500 records die worden afgehandeld, bijgewerkt.

## Registeridentificatie {#record-identification}

Geef op hoe de records in de database moeten worden geïdentificeerd:

* Als gegevensinvoer betrekking heeft op een bestaande doeldimensie, selecteert u de **[!UICONTROL By directly using the targeting dimension]** optie en selecteert u deze in het **[!UICONTROL Updated dimension]** veld.

   U kunt de velden voor de geselecteerde afmeting weergeven met de knop **[!UICONTROL Edit this link]** Vergrootglas.

* Geef anders een of meer koppelingen op die het mogelijk maken de gegevens in de database te identificeren of de afstemmingssleutels rechtstreeks te gebruiken.

![](assets/s_advuser_update_data_2.png)

## De velden selecteren die moeten worden bijgewerkt {#selecting-the-fields-to-be-updated}

Met deze **[!UICONTROL Automatically associate fields with the same name]** optie herkent Adobe Campaign automatisch de velden die moeten worden bijgewerkt.

![](assets/s_advuser_update_data_3b.png)

U kunt het **[!UICONTROL Insert]** pictogram ook gebruiken om handmatig de databasevelden te selecteren die u wilt bijwerken.

![](assets/s_advuser_update_data_3.png)

Selecteer alle velden die u wilt bijwerken en voeg, indien nodig, voorwaarden toe afhankelijk van de update. Hiervoor gebruikt u de **[!UICONTROL Taken into account if]** kolom. De voorwaarden worden na elkaar toegepast en in overeenstemming met de volgorde in de lijst. Gebruik de pijlen aan de rechterkant om de volgorde van updates te wijzigen.

U kunt hetzelfde doelveld meerdere keren gebruiken.

Binnen een **[!UICONTROL Insert or update]** bewerking kunt u de campagne selecteren die u wilt toepassen, afzonderlijk of voor elk veld. Selecteer hiertoe de gewenste waarde in de **[!UICONTROL Operation]** kolom.

![](assets/s_advuser_update_data_5.png)

De **[!UICONTROL modifiedDate]**, **[!UICONTROL modifiedBy]**, **[!UICONTROL createdDate]** en **[!UICONTROL createdBy]** gebieden worden automatisch bijgewerkt tijdens gegevensupdates, tenzij hun beheerswijze specifiek in de lijst van de gebiedsupdate wordt gevormd.

Record bijwerken wordt alleen uitgevoerd voor records die ten minste één verschil bevatten. Als de waarden gelijk zijn, wordt geen update uitgevoerd.

Met de **[!UICONTROL Advanced parameters]** koppeling kunt u aanvullende opties opgeven voor het bijwerken van gegevens en het beheren van duplicaten. U kunt ook:

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**. Deze optie is standaard automatisch ingeschakeld.
* **[!UICONTROL Update all columns with matching names]**.
* Geef voorwaarden op die bronelementen in aanmerking nemen met behulp van een expressie in het **[!UICONTROL Enabled if]** veld.
* Geef voorwaarden op die duplicaten in overweging nemen met behulp van een expressie. Als u de **[!UICONTROL Ignore records which concern the same target]** optie inschakelt, wordt alleen de eerste optie in de lijst met expressies in overweging genomen.

**[!UICONTROL Generate an outbound transition]**

Creeert een uitgaande overgang die aan het eind van uitvoering zal worden geactiveerd. Bij het bijwerken wordt doorgaans het einde van een doelworkflow aangegeven en wordt de optie daarom niet standaard geactiveerd.

**[!UICONTROL Generate an outbound transition for the rejects]**

Hiermee maakt u een uitgaande overgang met records die na de update niet correct zijn verwerkt (bijvoorbeeld als er een duplicaat is). De update markeert doorgaans het einde van een doelworkflow en daarom wordt de optie niet standaard geactiveerd.

## Verzamelingen bijwerken en samenvoegen {#updating-and-merging-collections}

Door gegevens bij te werken en verzamelingen samen te voegen, kunt u de gegevens in een record bijwerken met behulp van gegevens uit een of meer secundaire records, zodat u desgewenst slechts één record kunt bijhouden. Deze updates worden beheerd door een set regels.

>[!NOTE]
>
>Met deze optie kunt u ook verwijzingen naar secundaire records uit werkstroomwerktabellen (targetWorkflow), leveringen (targetDelivery) en lijsten (targetList) verwerken. Indien nodig worden deze koppelingen weergegeven in de lijst waarin u velden en verzamelingen selecteert.

1. Selecteer de **[!UICONTROL Update and merge collections]** bewerking.

   ![](assets/update_and_merge_collections1.png)

1. Selecteer de prioriteitsvolgorde voor de koppelingen. Zo kunt u het hoofdrecord identificeren. Welke koppelingen beschikbaar zijn, is afhankelijk van de binnenkomende overgang.

   ![](assets/update_and_merge_collections2.png)

1. Selecteer de verzamelingen die u wilt verplaatsen naar de primaire record en de velden die u wilt bijwerken.

   Ga de regels in die op deze van toepassing zijn zodra één of veelvoudige secundaire verslagen worden geïdentificeerd. Hiervoor kunt u de Expression Builder gebruiken. Zie deze [sectie](../../platform/using/defining-filter-conditions.md#building-expressions)voor meer informatie. Bijvoorbeeld door op te geven dat dit de meest recente bijgewerkte waarde is van alle verschillende records die moeten worden bewaard.

   Dan ga de voorwaarden in om met de regel rekening te houden.

   Geef ten slotte het type update op dat moet worden uitgevoerd. U kunt er bijvoorbeeld voor kiezen om de secundaire records te verwijderen nadat u de gegevens hebt bijgewerkt.

   U kunt bijvoorbeeld de samenvoeging configureren van verzamelingen met heterogene gegevens, zoals de abonnementenlijst voor een ontvanger. Gebruikend regels, kunt u nieuwe abonnementsgeschiedenissen van secundaire verslagabonnementen ook tot stand brengen, of zelfs de lijst van abonnementen van een secundair verslag verplaatsen naar een primair verslag.

1. Geef de volgorde op waarin u de secundaire records wilt verwerken door **[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]** te selecteren.

   ![](assets/update_and_merge_collections3.png)

Gegevens voor secundaire records worden gekoppeld aan het hoofdrecord als de gedefinieerde regels van toepassing zijn. Afhankelijk van het geselecteerde type update kunnen de secundaire records worden verwijderd.

## Voorbeeld: Gegevens bijwerken na verrijking {#example--update-data-following-an-enrichment}

De [tweede stap: Het schrijven van verrijkte gegevens naar de de lijstsectie van &quot;Aankopen&quot;](../../workflow/using/creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table) van het gebruiksgeval dat de details die tot een recaplijst leiden een voorbeeld van een gegevensupdate na een verrijkingsactiviteit aanbieden.

## Invoerparameters {#input-parameters}

* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.
