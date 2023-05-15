---
product: campaign
title: Een webapplicatie vertalen
description: Een webapplicatie vertalen
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Apps
exl-id: 82c5c610-8161-4686-aa79-1b690e763765
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 5%

---

# Een webapplicatie vertalen{#translating-a-web-application}



U kunt webtoepassingspagina&#39;s die zijn gemaakt met de Adobe Campaign Digital Content Editor (DCE), vertalen.

Als u ten minste één extra taal selecteert via de **[!UICONTROL Localization]** in de **[!UICONTROL Properties]** van een toepassing van het Web, wordt een nieuwe optie beschikbaar wanneer het toevoegen van een HTML inhoudsblok in een pagina die met DCE wordt uitgegeven.

Met deze optie kunt u aangeven of de blokinhoud moet worden vertaald of niet.

Tekenreeksen die moeten worden vertaald, worden op dezelfde manier verzameld als de andere tekenreeksen van de webtoepassing, via de **[!UICONTROL Translations]** van de toepassing. Raadpleeg [deze pagina](translating-a-web-form.md) voor meer informatie.

De tekenreeksen markeren die moeten worden vertaald:

1. Open een inhoudspagina die met DCE in een toepassing van het Web wordt uitgegeven.

   ![](assets/dce_translation_3.png)

1. Selecteer een HTML-blok.
1. In het parameterblok rechts, **[!UICONTROL Localization]** kunt u de inhoud van het geselecteerde blok markeren. Standaard wordt alleen de paginatitel vertaald.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >Tekenreeksen mogen niet langer zijn dan 1023 tekens.

   Er zijn drie specifieke gevallen:

   * Wanneer het geselecteerde blok verschillende tekenreeksen/blokken bevat, wordt het gemarkeerd als één tekenreeks die moet worden vertaald. De tekenreeks bevat vervolgens de HTML-code van de elementen in dit blok.
   * Wanneer u een blok wilt markeren dat meerdere tekenreeksen bevat en wanneer ten minste een van deze tekenreeksen al is gemarkeerd, wordt een waarschuwing weergegeven. Vervolgens kunt u de markering verwijderen uit de geïsoleerde tekenreeks en het volledige blok toevoegen.

      ![](assets/dce_translation_4.png)

   * Wanneer u de markering wilt verwijderen uit een tekenreeks die zich in een blok bevindt dat al is gemarkeerd, kunt u de optie voor het omzetten van de tekenreeks niet rechtstreeks wijzigen. U kunt echter wel toegang krijgen tot het blok met de tekenreeks om deze te wijzigen.

      ![](assets/dce_translation_2.png)

1. Als u de tekenreeksen hebt gemarkeerd, gaat u terug naar de webtoepassing en selecteert u de optie **[!UICONTROL Translations]** tab.
1. Selecteer **[!UICONTROL Collect the strings to translate]**. De tekenreeksen die in DCE worden gemarkeerd, worden toegevoegd aan de tekenreeksen van de webtoepassing.

   >[!NOTE]
   >
   >Nadat de tekenreeksen zijn verzameld, worden deze niet uit de lijst verwijderd als u de vertaalmarkering in DCE verwijdert. Hierdoor blijven ze in het vertaalgeheugen staan.

1. Vertaal en keur de tekenreeksen goed.

   U kunt vervolgens een voorvertoning van de vertalingen bekijken door de gewenste taal te selecteren in het menu **[!UICONTROL Preview]** in de webtoepassing.
