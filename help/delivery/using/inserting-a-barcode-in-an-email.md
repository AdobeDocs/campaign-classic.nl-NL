---
product: campaign
title: Een streepjescode invoegen in een e-mailbericht
description: Een streepjescode invoegen in een e-mailbericht
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Email Design
role: User
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# Een streepjescode invoegen in een e-mailbericht{#insert-a-barcode-in-an-email}

Met de module voor het genereren van streepjescodes kunt u verschillende typen streepjescodes maken die voldoen aan veel gangbare normen, waaronder 2D-streepjescodes.

Het is mogelijk om dynamisch een streepjescode als bitmap te produceren gebruikend een waarde die gebruikend klantencriteria wordt bepaald. U kunt persoonlijke streepjescodes opnemen in e-mailcampagnes. De ontvanger kan het bericht afdrukken en het aan het uitgevende bedrijf tonen voor scannen (bijvoorbeeld bij uitchecken).

Als u een streepjescode in een e-mailbericht wilt invoegen, plaatst u de cursor op de gewenste plaats in de inhoud en klikt u op de knop voor aanpassen. Selecteer **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

Dan vorm de volgende elementen om uw behoeften aan te passen:

1. Selecteer het type streepjescode.

   * Voor 1D-indeling zijn de volgende typen beschikbaar in Adobe Campaign: Codabar, Code 128, GS1-128 (voorheen EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET en Royal Mail (RM4SCC).

     Voorbeeld van een 1D-streepjescode:

     ![](assets/barcode_insert_08.png)

   * De typen DataMatrix en PDF417 hebben betrekking op de 2D-indeling.

     Voorbeeld van een 2D-streepjescode:

     ![](assets/barcode_insert_09.png)

   * Als u een QR-code wilt invoegen, selecteert u dit type en voert u de toe te passen foutcorrectiesnelheid in. Dit percentage bepaalt de hoeveelheid gegevens die wordt herhaald en de tolerantie voor kwaliteitsverlies.

     ![](assets/barcode_insert_06.png)

     Voorbeeld van een QR-code:

     ![](assets/barcode_insert_12.png)

1. Voer de grootte in van de streepjescode die u in de e-mail wilt invoegen: als u de schaal configureert, kunt u de streepjescode groter of kleiner maken, van x1 tot x10.
1. De **[!UICONTROL Value]** kunt u de waarde van de streepjescode definiëren. Een waarde kan een speciale aanbieding aanpassen en kan de functie van criteria zijn, het kan de waarde van een gegevensbestandgebied zijn verbonden met de klanten.

   In dit voorbeeld wordt een streepjescode van het type EAN-8 getoond, waaraan het rekeningnummer van een ontvanger is toegevoegd. Als u dit accountnummer wilt toevoegen, klikt u op de knop voor personalisatie rechts van het dialoogvenster **[!UICONTROL Value]** veld en selecteer **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. De **[!UICONTROL Height]** kunt u de hoogte van de streepjescode configureren zonder de breedte te wijzigen door de hoeveelheid ruimte tussen de streepjes te wijzigen.

   Er is geen restrictief besturingselement voor invoer afhankelijk van het type streepjescode. Als een streepjescodewaarde onjuist is, is deze alleen zichtbaar in **Voorvertoning** in de modus waarin de streepjescode rood wordt doorgehaald.

   >[!NOTE]
   >
   >De waarde die aan een streepjescode wordt toegewezen, is afhankelijk van het type. Een type EAN-8 moet bijvoorbeeld precies 8 cijfers hebben.
   >
   >De verpersoonlijkingsknoop rechts van **[!UICONTROL Value]** in dit veld kunt u naast de waarde zelf ook gegevens toevoegen. Hiermee wordt de streepjescode verrijkt, op voorwaarde dat de streepjescodestandaard dit accepteert.
   >
   >Als u bijvoorbeeld een streepjescode van het type GS1-128 gebruikt en als u naast de waarde het rekeningnummer van een ontvanger wilt invoeren, klikt u op de knop Verpersoonlijken en selecteert u **[!UICONTROL Recipient > Account number]**. Als het accountnummer van de geselecteerde ontvanger correct is ingevoerd, wordt hiermee rekening gehouden in de streepjescode.

Zodra deze elementen zijn gevormd, kunt u uw e-mail voltooien en het verzenden. Als u fouten wilt voorkomen, moet u ervoor zorgen dat de inhoud correct wordt weergegeven voordat u de levering uitvoert door op de knop **[!UICONTROL Preview]** tab.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Wanneer de waarde van een streepjescode onjuist is, wordt de bitmap rood weergegeven.

![](assets/barcode_insert_11.png)
