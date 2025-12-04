---
product: campaign
title: Geavanceerd - Leveringslogboeken aanpassen
description: Leer hoe u schema's voor leveringslogbestanden kunt uitbreiden om aangepaste velden toe te voegen in Campaign Classic v7
feature: Monitoring
role: User, Developer
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Geavanceerd: leveringslogboeken aanpassen {#customize-delivery-logs}

>[!NOTE]
>
>De uitvoerige begeleiding bij de toegang tot van de leveringslijst en het gebruiken van het leveringsdashboard wordt gedocumenteerd in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard). Deze inhoud is van toepassing op gebruikers van Campaign Classic v7 en Campagne v8.
>
>Deze pagina documenteert **Campaign Classic v7-specifieke geavanceerde aanpassingen** voor hybride en op-gebouw plaatsingen.

Voor controleleveringen in de Campagne UI, verwijs naar de [&#x200B; Bezorgingen van de Monitor v8 van de Campagne in de documentatie van UI van de Campagne &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}.

## Leveringslogboeken aanpassen {#use-case}

Voor **Campaign Classic v7 hybride/op-gebouw plaatsingen**, kunt u leveringslogboeken aanpassen door schema&#39;s uit te breiden. Deze sectie toont hoe te om IP van afzenders adressen aan de leveringslogboeken toe te voegen.

>[!NOTE]
>
>Deze aanpassing vereist de mogelijkheden van de schemauitbreiding beschikbaar in plaatsingen op-gebouw. Gebruikers van Managed Cloud Services voor campagne v8 dienen contact op te nemen met de klantenservice van Adobe voor aangepaste leveringslogvelden.
>
>Deze wijziging is anders als u één instantie of mid-sourcing instantie gebruikt. Voordat u de wijziging doorvoert, moet u controleren of u verbinding hebt met het verzendende exemplaar van de e-mail.

### Stap 1: Het schema uitbreiden

Om **publicID** in uw leveringslogboeken toe te voegen moet u het schema eerst uitbreiden. U kunt doorgaan zoals volgt.

1. Maak een schema-extensie onder **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]** .

   Voor meer informatie over schemauitbreidingen, verwijs naar [&#x200B; deze pagina &#x200B;](../../configuration/using/extending-a-schema.md).

1. Selecteer **[!UICONTROL broadLogRcp]** om de Ontvanger leverlogboeken (nms) uit te breiden en een aangepaste Namespace te bepalen. In dit geval is het &quot;cus&quot;:

   ![](assets/schema-parameters.png)

   >[!NOTE]
   >
   >Als uw instantie in Midden-sourcing is, moet u met schema werken wideLogMid.

1. Voeg het nieuwe veld toe aan de extensie. In dit voorbeeld moet u het volgende vervangen:

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp"/>
   ```

   door:

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp">
   <attribute desc="Outbound IP identifier" label="IP identifier"
   name="publicId" type="long"/>
   </element>
   ```

   ![](assets/edit-schema.png)

### Stap 2: De databasestructuur bijwerken

Zodra de wijzigingen worden gedaan, moet u gegevensbestandstructuur bijwerken zodat het met zijn logische beschrijving gericht is.

Hiervoor voert u de volgende stappen uit:

1. Klik op het menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** .**[!UICONTROL Update database structure...]**

   ![](assets/update-database-structure.png)

1. In het venster **[!UICONTROL Edit tables]** wordt de **[!UICONTROL NmsBroadLogRcp]** -tabel gecontroleerd (of de **[!UICONTROL broadLogMid]** -tabel als de tabel zich in een omgeving voor midsourcing bevindt), zoals hieronder:

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >Zorg altijd dat er geen andere wijzigingen zijn, behalve de tabel **[!UICONTROL NmsBroadLoGRcp]** (of de tabel **[!UICONTROL broadLogMid]** als de tabel zich in een omgeving voor midsourcing bevindt). Als dat het geval is, schakelt u andere tabellen uit.

1. Klik op **[!UICONTROL Next]** om te valideren. Het volgende scherm wordt weergegeven:

   ![](assets/update-script.png)

1. Klik op **[!UICONTROL Next]** en vervolgens op **[!UICONTROL Start]** om de databasestructuur bij te werken. Het samenstellen van indexen begint. Deze stap kan lang zijn, afhankelijk van het aantal rijen in de tabel **[!UICONTROL NmsBroadLogRcp]** .

   ![](assets/start-database-update.png)

>[!NOTE]
>
>Nadat de update van de fysieke structuur van de database is voltooid, moet u de verbinding verbreken en opnieuw tot stand brengen, zodat er rekening wordt gehouden met uw wijzigingen.

### Stap 3: De wijziging valideren

Om alles te bevestigen werkte correct, moet u het scherm van leveringslogboeken bijwerken.

Om dit te doen, heb toegang tot de leveringslogboeken en voeg de &quot;IP herkenningsteken&quot;kolom toe.

![](assets/list-config.png)

>[!NOTE]
>
>Leren hoe te om lijsten in de interface van Campaign Classic te vormen, verwijs naar [&#x200B; deze pagina &#x200B;](../../platform/using/adobe-campaign-workspace.md).

Hieronder ziet u wat u na wijzigingen op het tabblad **[!UICONTROL Delivery]** moet zien:

![](assets/logs-with-ip.png)

## Verwante onderwerpen

* [&#x200B; leveringen van de Monitor in Campagne UI &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; leveringsstatussen &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; Begrijpend leveringsmislukkingen &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; het beheer van de quarantaine &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; Uitbreidend een schema &#x200B;](../../configuration/using/extending-a-schema.md) (v7 hybride/op-gebouw)

