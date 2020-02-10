---
title: De databasestructuur bijwerken
seo-title: De databasestructuur bijwerken
description: De databasestructuur bijwerken
seo-description: null
page-status-flag: never-activated
uuid: 084dcc7b-f890-4dff-a322-c9a8f1d614b8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b82ae459-30b5-4a1c-91cc-5c7b8f128333
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# De databasestructuur bijwerken{#updating-the-database-structure}

Als u de wijzigingen die zijn aangebracht in de schema&#39;s wilt toepassen, start u de wizard voor databaseupdates. Deze wizard is toegankelijk via **[!UICONTROL Tools > Advanced > Update database structure]** . Het controleert of de fysieke structuur van het gegevensbestand zijn logische beschrijving aanpast en de SQL updatescripts uitvoert.

![](assets/d_ncs_integration_schema_update.png)

De modules in het gegevensbestand worden automatisch bevolkt en geactiveerd.

![](assets/d_ncs_integration_schema_update_select.png)

De **[!UICONTROL Add stored procedures]** en **[!UICONTROL Import initialization data]** opties worden gebruikt om de eerste SQL-scripts en gegevenspakketten te starten die worden uitgevoerd wanneer de database wordt gemaakt.

U kunt een set gegevens importeren uit een extern gegevenspakket. U doet dit door het XML-bestand van het pakket te selecteren **[!UICONTROL Import a package]** en in te voeren.

Voer de stappen uit en bekijk het SQL-script voor de update van de database:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Dit bevindt zich in een bewerkingsveld en kan worden gewijzigd om SQL-code te verwijderen of toe te voegen.

Start vervolgens de database-update:

![](assets/d_ncs_integration_schema_update3.png)

