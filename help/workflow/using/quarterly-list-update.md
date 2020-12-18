---
solution: Campaign Classic
product: campaign
title: Driemaandelijkse lijstupdate met een incrementele query
description: In dit geval wordt een incrementele query gebruikt om een lijst met ontvangers automatisch bij te werken.
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 5%

---


# Driemaandelijkse lijstupdate met een incrementele query {#quarterly-list-update}

In het volgende voorbeeld wordt een [incrementele query](../../workflow/using/incremental-query.md) gebruikt om een lijst met ontvangers automatisch bij te werken. Deze ontvangers zijn gericht op seizoensgebonden marketingcampagnes.

Aangezien deze campagnes aan het begin van elk seizoen worden gestart om relevante sportactiviteiten aan te bieden, worden deze lijsten elk kwartaal bijgewerkt. Een ontvanger mag echter slechts om de negen maanden voor deze campagne worden ingezet. Op deze manier kunt u de subsidiabiliteitsfrequentie van de ontvanger uitsplitsen en activiteiten aanbieden voor verschillende seizoenen in de loop van de jaren.

![](assets/incremental_query_example.png)

1. Voeg een stijgende vraag evenals een activiteit van de lijstupdate in een nieuw werkschema toe.
1. Configureer het tabblad **[!UICONTROL Incremental query]** van de activiteit zoals opgegeven in [Een query](../../workflow/using/query.md#creating-a-query) maken.
1. Selecteer het tabblad **[!UICONTROL Scheduling & History]** en geef vervolgens een 270-daagse historie op. Een ontvanger die reeds als doelwit is aangemerkt, zal niet langer voor een periode van 270 dagen, of ruwweg 9 maanden, worden aangewezen.

   Klik vervolgens op de knop **[!UICONTROL Change...]**.

1. Selecteer **[!UICONTROL Monthly]** om ervoor te zorgen dat de lijst voor het begin van elk seizoen wordt bijgewerkt.
1. Selecteer in het volgende scherm de opties maart, juni, september en december. Kies de 20e van de maand en geef op wanneer u de workflow wilt starten.
1. Selecteer vervolgens de geldigheidsperiode voor de query. Als u bijvoorbeeld wilt dat deze activiteit permanent actief is, selecteert u **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. Na het goedkeuren van de stijgende vraag, vorm de activiteit van de lijstupdate zoals die in [Update ](../../workflow/using/list-update.md) wordt verklaard.

De workflow wordt daarom automatisch gestart vlak voor het begin van elk seizoen. De lijst wordt bijgewerkt met nieuwe, in aanmerking komende ontvangers die de aanbiedingen ontvangen.
