---
product: campaign
title: Gedupliceerde ontvangers filteren
description: Leer hoe u gedupliceerde ontvangers filtert
feature: Workflows
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# Gedupliceerde ontvangers filteren {#filtering-duplicated-recipients}



In dit voorbeeld willen we ontvangers filteren die twee of meer in een levering verschijnen om gedupliceerde profielen te herstellen.

U kunt dit voorbeeld maken door de volgende stappen toe te passen:

1. Sleep een **[!UICONTROL Query]** activiteit in een werkstroom en open de activiteit.
1. Klikken **[!UICONTROL Edit query]** en stel de doel- en filterafmetingen in op **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Bepaal de volgende filtervoorwaarde aan doelontvanger die in het leveringslogboek bestaat. Kies **Logbestand voor levering ontvanger (broadlog)** in de **Uitdrukking** kolom, kies **bestaan** in de **Operator** kolom.

   ![](assets/query_recipients_2.png)

1. Bepaal de volgende filtervoorwaarde om uw levering te richten. Kies **[!UICONTROL Internal name]** in de kolom Expressie en **[!UICONTROL equal to]** in de kolom Exploitant.
1. Voeg in de waardekolom de interne naam van de beoogde levering toe.

   ![](assets/query_recipients_3.png)

1. Met een **[!UICONTROL AND]** -operator, herhaal dezelfde bewerkingen om andere leveringen als doel in te stellen.

   ![](assets/query_recipients_4.png)

Uw uitgaande overgang bevat de gedupliceerde ontvangers die in de leveringen als doel zijn ingesteld.
