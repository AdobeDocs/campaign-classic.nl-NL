---
title: Een externe database openen
seo-title: Een externe database openen
description: Een externe database openen
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---


# Het dataschema maken {#creating-the-data-schema}

Een schema maken voor een externe database:

1. Klik op de **[!UICONTROL New]** knop boven de lijst met gegevensschema&#39;s en kies **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Voer een naam en beschrijving in voor het schema en selecteer de externe account waarmee verbinding met de database kan worden gemaakt. Hierdoor hebt u toegang tot de lijst met tabellen die beschikbaar zijn in de externe basis. Kies de tabel met de gegevens die moeten worden verzameld.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Klik **[!UICONTROL OK]** om te bevestigen. Adobe Campaign detecteert automatisch de structuur van de geselecteerde tabel en genereert het logische schema. Adobe Campaign genereert geen koppelingen.

1. Klik **[!UICONTROL Save]** om het maken te bevestigen.

   >[!CAUTION]
   >
   >Met Snowflake is een primaire sleutel verplicht.

   ![](assets/wf_new_schema_generate_fda.png)

De indexen worden automatisch gemaakt wanneer een tabel (standaard- of FDA-toewijzing) wordt toegewezen.
