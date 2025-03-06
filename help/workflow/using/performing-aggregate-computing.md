---
product: campaign
title: Complexe computerverwerking uitvoeren
description: Leer hoe u geaggregeerde computertaken kunt uitvoeren in query's
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Complexe computerverwerking uitvoeren {#performing-aggregate-computing}



In dit voorbeeld willen we het aantal ontvangers dat in Londen woont, op basis van geslacht tellen.

* Welke tabel moet worden geselecteerd?

  De ontvankelijke lijst (**nms:ontvanger**)

* Welke gebieden in de outputkolom zouden moeten worden geselecteerd?

  Primaire sleutel (met telling) en Geslacht

* Op welke voorwaarden is de informatie gefilterd?

  Gebaseerd op de ontvangers die in Londen wonen

U kunt dit voorbeeld maken door de volgende stappen toe te passen:

1. Definieer in **[!UICONTROL Data to extract]** een telling voor de primaire sleutel (zoals in het vorige voorbeeld). Voeg het veld **[!UICONTROL Gender]** toe aan de uitvoerkolom. Controleer de optie **[!UICONTROL Group]** in de kolom **[!UICONTROL Gender]** . Op deze manier worden de ontvangers gegroepeerd op geslacht.

   ![](assets/query_editor_nveau_27.png)

1. Klik in het **[!UICONTROL Sorting]** -venster op **[!UICONTROL Next]** : hier hoeft niet te worden gesorteerd.
1. Gegevensfiltering configureren. Hier wilt u de selectie beperken tot contacten die in Londen wonen.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >Waarden zijn hoofdlettergevoelig. Als de waarde &#39;Londen&#39; in de voorwaarde wordt ingevoerd zonder een hoofdletter en de lijst met ontvangers het woord &#39;Londen&#39; met een hoofdletter bevat, zal de zoekopdracht mislukken.

1. Klik in het **[!UICONTROL Data formatting]** -venster op **[!UICONTROL Next]** : voor dit voorbeeld is geen opmaak vereist.
1. Klik in het voorvertoningsvenster op **[!UICONTROL Launch data preview]** .

   Er zijn drie afzonderlijke waarden voor elke soort door geslacht: **2** voor vrouwelijk, **1** voor mannetje en **0** wanneer het geslacht onbekend is. In dit voorbeeld bevat de lijst 10 vrouwen, 16 mannen en 2 mensen wier geslacht onbekend is.

   ![](assets/query_editor_agregat_04.png)
