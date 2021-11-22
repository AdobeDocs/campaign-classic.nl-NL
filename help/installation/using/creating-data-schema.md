---
product: campaign
title: Toegang tot een externe database
description: Toegang tot een externe database
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: d2d0ff575edbee18febb5ec895fcec1e0ae34de7
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 6%

---

# Het dataschema maken {#creating-the-data-schema}

![](../../assets/v7-only.svg)

Een schema maken voor een externe database:

1. Klik op de knop **[!UICONTROL New]** boven de lijst met gegevensschema&#39;s en kies **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Voer een **[!UICONTROL Namespace]** en  **[!UICONTROL Name]** voor het schema en selecteer **[!UICONTROL External account]** waarmee verbinding kan worden gemaakt met de database. Hierdoor hebt u toegang tot de lijst met tabellen die beschikbaar zijn in de externe basis.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Van de **[!UICONTROL Table name]** kiest u de tabel met de gegevens die moeten worden verzameld.

   Met Snowflake kunt u hier uw weergaven selecteren als aan de databasegebruiker de juiste bevoegdheden zijn toegekend. Als u weergaven gebruikt, kan Adobe Campaign het XML-schema niet automatisch genereren. U moet het zelf maken. Raadpleeg voor meer informatie over weergaven [Snowflake-documentatie](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Klikken **[!UICONTROL OK]** ter bevestiging. Adobe Campaign detecteert automatisch de structuur van de geselecteerde tabel en genereert het logische schema. Adobe Campaign genereert geen koppelingen.

1. Klikken **[!UICONTROL Save]** om de aanmaak te bevestigen.

   >[!CAUTION]
   >
   >Met Snowflake is een primaire sleutel verplicht.

   ![](assets/wf_new_schema_generate_fda.png)

De indexen worden automatisch gemaakt wanneer een tabel (standaard- of FDA-toewijzing) wordt toegewezen.
