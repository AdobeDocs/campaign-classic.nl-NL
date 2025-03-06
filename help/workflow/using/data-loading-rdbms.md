---
product: campaign
title: Gegevens laden (RDBMS)
description: Meer informatie over de activiteiten van de RDBMS-workflow (Data Load)
feature: Workflows, Data Management Activity
hide: true
hidefromtoc: true
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---

# Gegevens laden (RDBMS){#data-loading-rdbms}



Met de **[!UICONTROL Data loading (RDBMS)]** -activiteit hebt u rechtstreeks toegang tot deze externe database en kunt u alleen de gegevens verzamelen die vereist zijn voor het opgeven van doelen.

Om prestaties te verbeteren, adviseren wij gebruikend de vraagactiviteit (waar de gegevens van een extern gegevensbestand kunnen worden gebruikt). Voor meer op dit, verwijs naar [ Toegang hebbend tot een extern gegevensbestand (FDA) ](accessing-an-external-database-fda.md).

De bewerking is als volgt:

1. Selecteer de gegevensbron in de lijst en voer de naam in van de tabel die de gegevens bevat die u wilt extraheren.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   De naam van de tabel die in het desbetreffende veld wordt ingevoerd, wordt gebruikt als sjabloon voor het verzamelen van gegevens in de externe database. De naam van de tabel die door de workflow wordt verwerkt, kan worden berekend of overgebracht door de binnenkomende overgang van de activiteit voor het laden van gegevens. Klik op **[!UICONTROL Advanced..]** om de tabel te selecteren die u wilt gebruiken. en selecteert u de optie **[!UICONTROL Specified in the transition]** of **[!UICONTROL Explicit]** .

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Klik op de koppeling **[!UICONTROL Select the columns to extract...]** om de gegevens te kiezen die in de database moeten worden verzameld.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. U kunt een filter voor deze gegevens definiëren. Klik hiertoe op de koppeling **[!UICONTROL Edit query....]** .

   De op deze manier verzamelde gegevens kunnen gedurende de gehele levenscyclus van de workflow worden gebruikt.
