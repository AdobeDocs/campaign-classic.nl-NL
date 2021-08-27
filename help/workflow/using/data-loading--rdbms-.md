---
product: campaign
title: Gegevens laden (RDBMS)
description: Meer informatie over de activiteit van de workflow voor het laden van gegevens (RDBMS)
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---

# Gegevens laden (RDBMS){#data-loading-rdbms}

![](../../assets/common.svg)

Met de **[!UICONTROL Data loading (RDBMS)]**-activiteit hebt u rechtstreeks toegang tot deze externe database en kunt u alleen de gegevens verzamelen die vereist zijn voor de doelindeling.

Om prestaties te verbeteren, adviseren wij gebruikend de vraagactiviteit (waar de gegevens van een extern gegevensbestand kunnen worden gebruikt). Raadpleeg [Toegang tot een externe database (FDA)](accessing-an-external-database--fda-.md) voor meer informatie hierover.

De bewerking is als volgt:

1. Selecteer de gegevensbron in de lijst en voer de naam in van de tabel die de gegevens bevat die u wilt extraheren.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   De naam van de tabel die in het desbetreffende veld wordt ingevoerd, wordt gebruikt als sjabloon voor het verzamelen van gegevens in de externe database. De naam van de tabel die door de workflow wordt verwerkt, kan worden berekend of overgebracht door de binnenkomende overgang van de activiteit voor het laden van gegevens. Klik op **[!UICONTROL Advanced..]** om de tabel te selecteren die u wilt gebruiken. en selecteer de optie **[!UICONTROL Specified in the transition]** of **[!UICONTROL Explicit]**.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Klik op de koppeling **[!UICONTROL Select the columns to extract...]** om de gegevens te kiezen die in de database moeten worden verzameld.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. U kunt een filter voor deze gegevens definiëren. Klik op de koppeling **[!UICONTROL Edit query....]** om dit te doen.

   De op deze manier verzamelde gegevens kunnen gedurende de gehele levenscyclus van de workflow worden gebruikt.
