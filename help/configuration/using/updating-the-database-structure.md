---
solution: Campaign Classic
product: campaign
title: De databasestructuur bijwerken
description: De databasestructuur bijwerken
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---


# De databasestructuur bijwerken{#updating-the-database-structure}

Als u de wijzigingen die zijn aangebracht in de schema&#39;s wilt toepassen, start u de wizard voor databaseupdates. Deze wizard is toegankelijk via **[!UICONTROL Tools > Advanced > Update database structure]**. Het controleert of de fysieke structuur van het gegevensbestand zijn logische beschrijving aanpast en de SQL updatescripts uitvoert.

![](assets/d_ncs_integration_schema_update.png)

De modules in het gegevensbestand worden automatisch bevolkt en geactiveerd.

![](assets/d_ncs_integration_schema_update_select.png)

De opties **[!UICONTROL Add stored procedures]** en **[!UICONTROL Import initialization data]** worden gebruikt om de eerste SQL-scripts en gegevenspakketten te starten die worden uitgevoerd wanneer de database wordt gemaakt.

U kunt een set gegevens importeren uit een extern gegevenspakket. Selecteer **[!UICONTROL Import a package]** om dit te doen en voer het XML-bestand van het pakket in.

Voer de stappen uit en bekijk het SQL-script voor de update van de database:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Dit bevindt zich in een bewerkingsveld en kan worden gewijzigd om SQL-code te verwijderen of toe te voegen.

Start vervolgens de database-update:

![](assets/d_ncs_integration_schema_update3.png)

