---
product: campaign
title: De databasestructuur bijwerken
description: De databasestructuur bijwerken
feature: Configuration
role: Data Engineer, Developer
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---

# De databasestructuur bijwerken{#updating-the-database-structure}



Om de wijzigingen toe te passen die aan de schema&#39;s worden aangebracht, lanceer de medewerker van de gegevensbestandupdate. Deze assistent is toegankelijk via **[!UICONTROL Tools > Advanced > Update database structure]** . Het controleert of de fysieke structuur van het gegevensbestand zijn logische beschrijving aanpast en de SQL updatescripts uitvoert.

![](assets/d_ncs_integration_schema_update.png)

De modules in het gegevensbestand worden automatisch bevolkt en geactiveerd.

![](assets/d_ncs_integration_schema_update_select.png)

De opties **[!UICONTROL Add stored procedures]** en **[!UICONTROL Import initialization data]** worden gebruikt om de eerste SQL-scripts en gegevenspakketten te starten die worden uitgevoerd wanneer de database wordt gemaakt.

U kunt een set gegevens importeren uit een extern gegevenspakket. Selecteer hiervoor **[!UICONTROL Import a package]** en voer het XML-bestand van het pakket in.

Voer de stappen uit en bekijk het SQL-script voor de update van de database:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Dit bevindt zich in een bewerkingsveld en kan worden gewijzigd om SQL-code te verwijderen of toe te voegen.

Start vervolgens de database-update:

![](assets/d_ncs_integration_schema_update3.png)
