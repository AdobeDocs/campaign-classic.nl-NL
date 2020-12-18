---
solution: Campaign Classic
product: campaign
title: Toegang tot een externe database
description: Toegang tot een externe database
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 9%

---


# Het dataschema maken {#creating-the-data-schema}

Een schema maken voor een externe database:

1. Klik op de knop **[!UICONTROL New]** boven de lijst met gegevensschema&#39;s en kies **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Voer een naam en beschrijving in voor het schema en selecteer de externe account waarmee verbinding met de database kan worden gemaakt. Hierdoor hebt u toegang tot de lijst met tabellen die beschikbaar zijn in de externe basis. Kies de tabel met de gegevens die moeten worden verzameld.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Klik **[!UICONTROL OK]** om te bevestigen. Adobe Campaign detecteert automatisch de structuur van de geselecteerde tabel en genereert het logische schema. Adobe Campaign genereert geen koppelingen.

1. Klik op **[!UICONTROL Save]** om het maken te bevestigen.

   >[!CAUTION]
   >
   >Met Snowflake is een primaire sleutel verplicht.

   ![](assets/wf_new_schema_generate_fda.png)

De indexen worden automatisch gemaakt wanneer een tabel (standaard- of FDA-toewijzing) wordt toegewezen.
