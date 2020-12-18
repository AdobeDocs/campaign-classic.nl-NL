---
solution: Campaign Classic
product: campaign
title: Categorieën voor aanbiedingen maken
description: Categorieën voor aanbiedingen maken
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---


# Categorieën voor aanbiedingen maken{#creating-offer-categories}

Het creëren van aanbiedingscategorieën kan slechts in het **[!UICONTROL Design]** milieu plaatsvinden. Ze worden automatisch geïmplementeerd in de **[!UICONTROL Live]**-omgeving (d.w.z. beschikbaar gesteld) wanneer de gemaakte/gewijzigde aanbieding(en) die ze bevatten, worden goedgekeurd. Standaard bevat de **[!UICONTROL Design]**-omgeving een categorie voor het ontvangen van alle aanbiedingen. U kunt subcategorieën maken om een hiërarchie toe te voegen aan de catalogusaanbiedingen.

Voor elke categorie kunt u de toelatingsdata bepalen, d.w.z. een periode waarna de aanbiedingen in de categorie niet langer aan hun doel mogen worden gepresenteerd. Als u wilt dat de aanbiedingen van een bepaalde categorie als prioriteit door de aanbiedingsmotor worden geselecteerd, om een product bijvoorbeeld beter toegankelijk te maken, kunt u hun gewicht gedurende een bepaalde periode verhogen door een vermenigvuldigingsgewicht aan de categorie toe te voegen.

Voer de volgende stappen uit om een extra categorie te maken:

1. Ga naar de **[!UICONTROL Offer catalog]** omslag.

   ![](assets/offer_cat_create_001.png)

1. Klik met de rechtermuisknop en selecteer **[!UICONTROL Create a new "Offer category" folder]** in de vervolgkeuzelijst.

   ![](assets/offer_cat_create_002.png)

1. Geef de categorie een nieuwe naam. U kunt het label later bewerken met het tabblad **[!UICONTROL General]**.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Herhaal deze stappen om zoveel categorieën te maken als nodig is.

   Daarna kunt u zo nodig:

   * Wijs toelatingsdata van **[!UICONTROL Eligibility]** tabel toe.

      ![](assets/offer_cat_create_004.png)

   * Voer sleutelwoorden in die u kunt gebruiken om aanbiedingen te selecteren vanuit deze categorie. Gebruik hiervoor het veld **[!UICONTROL Themes]**.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >Wanneer u de aanbiedingsengine aanroept, wordt alleen het gedeelte van de catalogus geselecteerd waarin de thema&#39;s of categorieën overeenkomen met de parameters.

   * Het aanbiedingsgewicht van een categorie gedurende een bepaalde periode tijdelijk verhogen via het veld **[!UICONTROL Multiplier weight]**.

      ![](assets/offer_cat_create_006.png)

Op het dashboard van de aanbiedingen in de categorie staat een overzicht van de subsidiabiliteitsregels. Klik op de koppeling **[!UICONTROL Schedule and eligibility rules of the offer]** om deze weer te geven.

![](assets/offer_create_006.png)

