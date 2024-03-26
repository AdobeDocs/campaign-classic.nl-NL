---
product: campaign
title: Het gegevensschema voor FDA maken
description: Leer hoe u het gegevensschema voor FDA maakt
feature: Installation, Instance Settings, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 3%

---

# Het gegevensschema maken {#creating-the-data-schema}



Een schema maken voor een externe database:

1. Klik op de knop **[!UICONTROL New]** boven de lijst met gegevensschema&#39;s en kies **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Voer een **[!UICONTROL Namespace]** en  **[!UICONTROL Name]** voor het schema en selecteer **[!UICONTROL External account]** waarmee verbinding kan worden gemaakt met de database. Hierdoor hebt u toegang tot de lijst met tabellen die beschikbaar zijn in de externe basis.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Van de **[!UICONTROL Table name]** kiest u de tabel met de gegevens die moeten worden verzameld.

   Met Snowflake, kunt u hier uw meningen selecteren als de gegevensbestandgebruiker de correcte voorrechten heeft gekregen. Als u weergaven gebruikt, kan Adobe Campaign het XML-schema niet automatisch genereren. U moet het zelf maken. Raadpleeg voor meer informatie over weergaven [Documentatie Snowflake](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Klikken **[!UICONTROL OK]** ter bevestiging. Adobe Campaign detecteert automatisch de structuur van de geselecteerde tabel en genereert het logische schema. Adobe Campaign genereert geen koppelingen.

1. Klikken **[!UICONTROL Save]** om de aanmaak te bevestigen.

   >[!CAUTION]
   >
   >Met Snowflake is een primaire sleutel verplicht.

   ![](assets/wf_new_schema_generate_fda.png)

De indexen worden automatisch gemaakt wanneer een tabel (standaard- of FDA-toewijzing) wordt toegewezen.
