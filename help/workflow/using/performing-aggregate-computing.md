---
product: campaign
title: Complexe computerverwerking uitvoeren
description: Leer hoe u geaggregeerde computertaken kunt uitvoeren in query's
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Workflows
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 2%

---

# Complexe computerverwerking uitvoeren {#performing-aggregate-computing}



In dit voorbeeld willen we het aantal ontvangers dat in Londen woont, op basis van geslacht tellen.

* Welke tabel moet worden geselecteerd?

  De tabel met ontvangers (**nms:ontvanger**)

* Welke gebieden in de outputkolom zouden moeten worden geselecteerd?

  Primaire sleutel (met telling) en Geslacht

* Op welke voorwaarden is de informatie gefilterd?

  Gebaseerd op de ontvangers die in Londen wonen

U kunt dit voorbeeld maken door de volgende stappen toe te passen:

1. In **[!UICONTROL Data to extract]** definieert u een telling voor de primaire sleutel (zoals in het vorige voorbeeld). Voeg de **[!UICONTROL Gender]** in de uitvoerkolom. Controleer de **[!UICONTROL Group]** in de **[!UICONTROL Gender]** kolom. Op deze manier worden de ontvangers gegroepeerd op geslacht.

   ![](assets/query_editor_nveau_27.png)

1. In de **[!UICONTROL Sorting]** venster, klikt u op **[!UICONTROL Next]**: hier hoeft niet gesorteerd te worden.
1. Gegevensfiltering configureren. Hier wilt u de selectie beperken tot contacten die in Londen wonen.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >Waarden zijn hoofdlettergevoelig. Als de waarde &#39;Londen&#39; in de voorwaarde wordt ingevoerd zonder een hoofdletter en de lijst met ontvangers het woord &#39;Londen&#39; met een hoofdletter bevat, zal de zoekopdracht mislukken.

1. In de **[!UICONTROL Data formatting]** venster, klikt u op **[!UICONTROL Next]**: voor dit voorbeeld is geen opmaak vereist.
1. Klik in het voorvertoningsvenster op **[!UICONTROL Launch data preview]**.

   Er zijn drie verschillende waarden voor elke soort naar geslacht: **2** voor vrouwen, **1** voor mannen en **0** wanneer het geslacht onbekend is. In dit voorbeeld bevat de lijst 10 vrouwen, 16 mannen en 2 mensen wier geslacht onbekend is.

   ![](assets/query_editor_agregat_04.png)
