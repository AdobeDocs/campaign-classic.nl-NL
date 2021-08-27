---
product: campaign
title: Berekening van samenvoegingen uitvoeren
description: Leer hoe u geaggregeerde computertaken kunt uitvoeren in query's
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---

# Berekening van samenvoegingen uitvoeren {#performing-aggregate-computing}

![](../../assets/common.svg)

In dit voorbeeld willen we het aantal ontvangers dat in Londen woont, op basis van geslacht tellen.

* Welke tabel moet worden geselecteerd?

   De ontvankelijke lijst (**nms:ontvanger**)

* Welke gebieden in de outputkolom zouden moeten worden geselecteerd?

   Primaire sleutel (met telling) en Geslacht

* Op welke voorwaarden is de informatie gefilterd?

   Gebaseerd op de ontvangers die in Londen wonen

U kunt dit voorbeeld maken door de volgende stappen toe te passen:

1. Definieer in **[!UICONTROL Data to extract]** een telling voor de primaire sleutel (zoals in het vorige voorbeeld). Voeg het veld **[!UICONTROL Gender]** in de uitvoerkolom toe. Schakel de optie **[!UICONTROL Group]** in de kolom **[!UICONTROL Gender]** in. Op deze manier worden de ontvangers gegroepeerd op geslacht.

   ![](assets/query_editor_nveau_27.png)

1. Klik in het venster **[!UICONTROL Sorting]** op **[!UICONTROL Next]**: hier is geen sortering nodig .
1. Gegevensfiltering configureren. Hier wilt u de selectie beperken tot contacten die in Londen wonen.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >Waarden zijn hoofdlettergevoelig. Als de waarde &#39;Londen&#39; in de voorwaarde wordt ingevoerd zonder een hoofdletter en de lijst met ontvangers het woord &#39;Londen&#39; met een hoofdletter bevat, zal de zoekopdracht mislukken.

1. Klik in het venster **[!UICONTROL Data formatting]** op **[!UICONTROL Next]**: voor dit voorbeeld is geen opmaak vereist.
1. Klik in het voorvertoningsvenster op **[!UICONTROL Launch data preview]**.

   Er zijn drie verschillende waarden voor elke soort naar geslacht: **2** voor vrouwen, **1** voor mannen en **0** als het geslacht onbekend is. In dit voorbeeld bevat de lijst 10 vrouwen, 16 mannen en 2 mensen wier geslacht onbekend is.

   ![](assets/query_editor_agregat_04.png)
