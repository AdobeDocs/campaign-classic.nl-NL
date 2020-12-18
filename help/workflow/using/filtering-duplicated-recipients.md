---
solution: Campaign Classic
product: campaign
title: Gedupliceerde ontvangers filteren
description: Leer hoe u gedupliceerde ontvangers filtert
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---


# Gedupliceerde ontvangers filteren {#filtering-duplicated-recipients}

In dit voorbeeld willen we ontvangers filteren die twee of meer in een levering verschijnen om dubbele profielen te herstellen.

U kunt dit voorbeeld maken door de volgende stappen toe te passen:

1. Sleep een **[!UICONTROL Query]** activiteit in een werkstroom en open de activiteit.
1. Klik op **[!UICONTROL Edit query]** en stel de doel- en filterafmetingen in op **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Bepaal de volgende filtervoorwaarde aan doelontvanger die in het leveringslogboek bestaat. Kies **Ontvangersleveringslogboek (broadlog)** in de **Expressie** kolom, kies **bestaan zoals** in **Operator** kolom.

   ![](assets/query_recipients_2.png)

1. Bepaal de volgende filtervoorwaarde om uw levering te richten. Kies **[!UICONTROL Internal name]** in de kolom van de Uitdrukking en **[!UICONTROL equal to]** in de kolom van de Exploitant.
1. Voeg in de waardekolom de interne naam van de beoogde levering toe.

   ![](assets/query_recipients_3.png)

1. Met een **[!UICONTROL AND]** exploitant, herhaal de zelfde verrichtingen om andere leveringen te richten.

   ![](assets/query_recipients_4.png)

Uw uitgaande overgang bevat de dubbele ontvangers die in de leveringen als doel zijn ingesteld.
