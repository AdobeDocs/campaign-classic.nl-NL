---
product: campaign
title: Gegevens bijwerken
description: Meer informatie over de activiteiten in de workflow Gegevens bijwerken
feature: Data Management
exl-id: 9f5735d2-73b8-469f-bc10-482c99cdd4a1
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 2%

---

# Gegevens bijwerken{#update-data}

![](../../assets/common.svg)

An **Gegevens bijwerken**-type activiteit voert een massa-update van de gebieden in het gegevensbestand uit.

## Type bewerking {#operation-type}

De **[!UICONTROL Operation type]** kunt u het proces kiezen dat op de gegevens in de database moet worden uitgevoerd:

* **[!UICONTROL Insert or update]**: gegevens toevoegen of bijwerken als deze al zijn toegevoegd.
* **[!UICONTROL Insert]**: alleen gegevens toevoegen.
* **[!UICONTROL Update]**: alleen gegevens bijwerken.
* **[!UICONTROL Update and merge collections]**: gegevens bijwerken en een primaire record kiezen, en vervolgens elementen koppelen die zijn gekoppeld aan de duplicaten in deze primaire record. Duplicaten kunnen vervolgens worden verwijderd zonder weeselementen in bijlage te maken.
* **[!UICONTROL Delete]**: Data verwijderen.

![](assets/s_advuser_update_data_1.png)

De **[!UICONTROL Batch size]** in dit veld kunt u het aantal inkomende overgangselementen selecteren dat moet worden bijgewerkt. Als u bijvoorbeeld 500 opgeeft, worden de eerste 500 records die worden afgehandeld, bijgewerkt.

## Registeridentificatie {#record-identification}

Geef op hoe de records in de database moeten worden geïdentificeerd:

* Als gegevensinvoer betrekking heeft op een bestaande doeldimensie, selecteert u de optie **[!UICONTROL By directly using the targeting dimension]** en selecteert u deze in het dialoogvenster **[!UICONTROL Updated dimension]** veld.

   U kunt de velden voor de geselecteerde dimensie weergeven met de opdracht **[!UICONTROL Edit this link]** vergrootglasknop.

* Geef anders een of meer koppelingen op die het mogelijk maken de gegevens in de database te identificeren of de afstemmingssleutels rechtstreeks te gebruiken.

![](assets/s_advuser_update_data_2.png)

## De velden selecteren die moeten worden bijgewerkt {#selecting-the-fields-to-be-updated}

Gebruik de **[!UICONTROL Automatically associate fields with the same name]** zodat Adobe Campaign automatisch de velden kan identificeren die moeten worden bijgewerkt.

![](assets/s_advuser_update_data_3b.png)

U kunt ook de opdracht **[!UICONTROL Insert]** om handmatig de databasevelden te selecteren die moeten worden bijgewerkt.

![](assets/s_advuser_update_data_3.png)

Selecteer alle velden die u wilt bijwerken en voeg, indien nodig, voorwaarden toe afhankelijk van de update. Hiervoor gebruikt u de kolom **[!UICONTROL Taken into account if]**. De voorwaarden worden na elkaar toegepast en in overeenstemming met de volgorde in de lijst. Gebruik de pijlen aan de rechterkant om de volgorde van updates te wijzigen.

U kunt hetzelfde doelveld meerdere keren gebruiken.

Binnen een **[!UICONTROL Insert or update]** kunt u de campagne selecteren die u wilt toepassen, afzonderlijk of voor elk veld. Selecteer hiertoe de gewenste waarde in het dialoogvenster **[!UICONTROL Operation]** kolom.

![](assets/s_advuser_update_data_5.png)

De **[!UICONTROL modifiedDate]**, **[!UICONTROL modifiedBy]**, **[!UICONTROL createdDate]** en **[!UICONTROL createdBy]** velden worden automatisch bijgewerkt tijdens gegevensupdates, tenzij hun beheermodus specifiek is geconfigureerd in de tabel met veldupdates.

Record bijwerken wordt alleen uitgevoerd voor records die ten minste één verschil bevatten. Als de waarden gelijk zijn, wordt geen update uitgevoerd.

De **[!UICONTROL Advanced parameters]** Met de koppeling kunt u aanvullende opties opgeven voor het bijwerken van gegevens en het beheren van duplicaten. U kunt ook:

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**. Deze optie is standaard automatisch ingeschakeld.
* **[!UICONTROL Update all columns with matching names]**.
* Geef voorwaarden op die bronelementen in aanmerking nemen met behulp van een expressie in het dialoogvenster **[!UICONTROL Enabled if]** veld.
* Geef voorwaarden op die duplicaten in overweging nemen met behulp van een expressie. Als u de **[!UICONTROL Ignore records which concern the same target]** alleen de eerste in de lijst van expressies wordt in overweging genomen.

**[!UICONTROL Generate an outbound transition]**

Creeert een uitgaande overgang die aan het eind van uitvoering zal worden geactiveerd. Bij het bijwerken wordt doorgaans het einde van een doelworkflow aangegeven en wordt de optie daarom niet standaard geactiveerd.

**[!UICONTROL Generate an outbound transition for the rejects]**

Hiermee maakt u een uitgaande overgang met records die na de update niet correct zijn verwerkt (bijvoorbeeld als er een duplicaat is). De update markeert doorgaans het einde van een doelworkflow en daarom wordt de optie niet standaard geactiveerd.

## Verzamelingen bijwerken en samenvoegen {#updating-and-merging-collections}

Door gegevens bij te werken en verzamelingen samen te voegen, kunt u de gegevens in een record bijwerken met behulp van gegevens uit een of meer secundaire records, zodat u desgewenst slechts één record kunt bijhouden. Deze updates worden beheerd door een set regels.

>[!NOTE]
>
>Met deze optie kunt u ook verwijzingen naar secundaire records uit werkstroomwerktabellen (targetWorkflow), leveringen (targetDelivery) en lijsten (targetList) verwerken. Indien nodig worden deze koppelingen weergegeven in de lijst waarin u velden en verzamelingen selecteert.

1. Selecteer **[!UICONTROL Update and merge collections]** bewerking.

   ![](assets/update_and_merge_collections1.png)

1. Selecteer de prioriteitsvolgorde voor de koppelingen. Zo kunt u het hoofdrecord identificeren. Welke koppelingen beschikbaar zijn, is afhankelijk van de binnenkomende overgang.

   ![](assets/update_and_merge_collections2.png)

1. Selecteer de verzamelingen die u wilt verplaatsen naar de primaire record en de velden die u wilt bijwerken.

   Ga de regels in die op deze van toepassing zijn zodra één of veelvoudige secundaire verslagen worden geïdentificeerd. Hiervoor kunt u de Expression Builder gebruiken. Raadpleeg deze [sectie](../../platform/using/defining-filter-conditions.md#building-expressions) voor meer informatie. Bijvoorbeeld door op te geven dat dit de meest recente bijgewerkte waarde is van alle verschillende records die moeten worden bewaard.

   Dan ga de voorwaarden in om met de regel rekening te houden.

   Geef ten slotte het type update op dat moet worden uitgevoerd. U kunt er bijvoorbeeld voor kiezen om de secundaire records te verwijderen nadat u de gegevens hebt bijgewerkt.

   U kunt bijvoorbeeld de samenvoeging configureren van verzamelingen met heterogene gegevens, zoals de abonnementenlijst voor een ontvanger. Gebruikend regels, kunt u nieuwe abonnementsgeschiedenissen van secundaire verslagabonnementen ook tot stand brengen, of zelfs de lijst van abonnementen van een secundair verslag verplaatsen naar een primair verslag.

1. Geef de volgorde op waarin u de secundaire records wilt verwerken door **[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**.

   ![](assets/update_and_merge_collections3.png)

Gegevens voor secundaire records worden gekoppeld aan het hoofdrecord als de gedefinieerde regels van toepassing zijn. Afhankelijk van het geselecteerde type update kunnen de secundaire records worden verwijderd.

## Voorbeeld: Gegevens bijwerken na verrijking {#example--update-data-following-an-enrichment}

De [Stap 2: Verrijkte gegevens naar de tabel &#39;Aankopen&#39; schrijven](creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table) een gedeelte van het gebruiksgeval waarin details over het maken van een lijst met terugwinningsobjecten een voorbeeld zijn van een gegevensupdate na een verrijkingsactiviteit.

## Invoerparameters {#input-parameters}

* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.
