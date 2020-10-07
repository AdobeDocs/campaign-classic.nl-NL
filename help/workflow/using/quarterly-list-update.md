---
title: Driemaandelijkse lijstupdate die een stijgende vraag gebruikt
description: In dit geval wordt een incrementele query gebruikt om een lijst met ontvangers automatisch bij te werken.
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# Driemaandelijkse lijstupdate die een stijgende vraag gebruikt {#quarterly-list-update}

In het volgende voorbeeld wordt een [incrementele query](../../workflow/using/incremental-query.md) gebruikt om een lijst met ontvangers automatisch bij te werken. Deze ontvangers zijn gericht op seizoensgebonden marketingcampagnes.

Aangezien deze campagnes aan het begin van elk seizoen worden gestart om relevante sportactiviteiten aan te bieden, worden deze lijsten elk kwartaal bijgewerkt. Een ontvanger mag echter slechts om de negen maanden voor deze campagne worden ingezet. Op deze manier kunt u de subsidiabiliteitsfrequentie van de ontvanger uitsplitsen en activiteiten aanbieden voor verschillende seizoenen in de loop van de jaren.

![](assets/incremental_query_example.png)

1. Voeg een stijgende vraag evenals een activiteit van de lijstupdate in een nieuw werkschema toe.
1. Vorm het **[!UICONTROL Incremental query]** lusje van de activiteit zoals die in het [Creëren van een vraag](../../workflow/using/query.md#creating-a-query)wordt gespecificeerd.
1. Selecteer het **[!UICONTROL Scheduling & History]** tabblad en geef een historie van 270 dagen op. Een ontvanger die reeds als doelwit is aangemerkt, zal niet langer voor een periode van 270 dagen, of ruwweg 9 maanden, worden aangewezen.

   Then click the **[!UICONTROL Change...]** button.

1. Selecteer **[!UICONTROL Monthly]**.
1. Selecteer in het volgende scherm de opties maart, juni, september en december. Kies de 20e van de maand en geef op wanneer u de workflow wilt starten.
1. Selecteer vervolgens de geldigheidsperiode voor de query. Selecteer bijvoorbeeld deze activiteit als u deze permanent actief wilt maken. **[!UICONTROL Permanent validity]**

   ![](assets/incremental_query_example_2.png)

1. Na het goedkeuren van de stijgende vraag, vorm de activiteit van de lijstupdate zoals die in de update [van de](../../workflow/using/list-update.md)Lijst wordt verklaard.

De workflow wordt daarom automatisch gestart vlak voor het begin van elk seizoen. De lijst wordt bijgewerkt met nieuwe, in aanmerking komende ontvangers die de aanbiedingen ontvangen.
