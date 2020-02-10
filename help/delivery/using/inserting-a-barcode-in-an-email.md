---
title: Een streepjescode invoegen in een e-mail
seo-title: Een streepjescode invoegen in een e-mail
description: Een streepjescode invoegen in een e-mail
seo-description: null
page-status-flag: never-activated
uuid: 61f9d8ea-38b0-46a5-8085-b6f34f8559f7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 679b9ae2-362c-483d-acb8-47bc01928541
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Een streepjescode invoegen in een e-mail{#inserting-a-barcode-in-an-email}

Met de module voor het genereren van streepjescodes kunt u verschillende typen streepjescodes maken die voldoen aan veel gangbare normen, waaronder 2D-streepjescodes.

Het is mogelijk om dynamisch een streepjescode als bitmap te produceren gebruikend een waarde die gebruikend klantencriteria wordt bepaald. U kunt persoonlijke streepjescodes opnemen in e-mailcampagnes. De ontvanger kan het bericht afdrukken en het aan het uitgevende bedrijf tonen voor scannen (bijvoorbeeld bij uitchecken).

Als u een streepjescode in een e-mailbericht wilt invoegen, plaatst u de cursor op de gewenste plaats in de inhoud en klikt u op de knop voor aanpassen. Selecteer **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

Dan vorm de volgende elementen om uw behoeften aan te passen:

1. Selecteer het type streepjescode.

   * Voor de 1D-indeling zijn de volgende typen beschikbaar in Adobe Campagne: Codabar, Code 128, GS1-128 (voorheen EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET and Royal Mail (RM4SCC).

      Voorbeeld van een 1D-streepjescode:

      ![](assets/barcode_insert_08.png)

   * De typen DataMatrix en PDF417 hebben betrekking op de 2D-indeling.

      Voorbeeld van een 2D-streepjescode:

      ![](assets/barcode_insert_09.png)

   * Als u een QR-code wilt invoegen, selecteert u dit type en voert u de toe te passen foutcorrectiesnelheid in. Dit percentage bepaalt de hoeveelheid gegevens die wordt herhaald en de tolerantie voor kwaliteitsverlies.

      ![](assets/barcode_insert_06.png)

      Voorbeeld van een QR-code:

      ![](assets/barcode_insert_12.png)

1. Voer de grootte in van de streepjescode die u in de e-mail wilt invoegen: Door de schaal te configureren kunt u de grootte van de streepjescode verhogen of verlagen, van x1 tot x10.
1. In het **[!UICONTROL Value]** veld kunt u de waarde van de streepjescode definiëren. Een waarde kan een speciale aanbieding aanpassen en kan de functie van criteria zijn, het kan de waarde van een gegevensbestandgebied zijn verbonden met de klanten.

   In dit voorbeeld wordt een streepjescode van het type EAN-8 getoond, waaraan het rekeningnummer van een ontvanger is toegevoegd. Als u dit accountnummer wilt toevoegen, klikt u op de aanpassingsknop rechts van het **[!UICONTROL Value]** veld en selecteert u **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. In het **[!UICONTROL Height]** veld kunt u de hoogte van de streepjescode configureren zonder de breedte te wijzigen door de hoeveelheid ruimte tussen de streepjes te wijzigen.

   Er is geen restrictief besturingselement voor invoer afhankelijk van het type streepjescode. Als een streepjescodewaarde onjuist is, is deze alleen zichtbaar in de modus **Voorbeeld** , waarin de streepjescode in het rood wordt doorgestreept.

   >[!NOTE]
   >
   >De waarde die aan een streepjescode wordt toegewezen, is afhankelijk van het type. Een type EAN-8 moet bijvoorbeeld precies 8 cijfers hebben.
   >
   >Met de aanpassingsknop rechts van het **[!UICONTROL Value]** veld kunt u naast de waarde zelf ook gegevens toevoegen. Hiermee wordt de streepjescode verrijkt, op voorwaarde dat de streepjescodestandaard dit accepteert.
   >
   >Als u bijvoorbeeld een streepjescode van het type GS1-128 gebruikt en als u naast de waarde het rekeningnummer van een ontvanger wilt invoeren, klikt u op de knop Verpersoonlijken en selecteert u **[!UICONTROL Recipient > Account number]**. Als het accountnummer van de geselecteerde ontvanger correct is ingevoerd, wordt hiermee rekening gehouden in de streepjescode.

Zodra deze elementen zijn gevormd, kunt u uw e-mail voltooien en het verzenden. U voorkomt fouten door op het **[!UICONTROL Preview]** tabblad te klikken om ervoor te zorgen dat de inhoud correct wordt weergegeven voordat u de levering uitvoert.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Wanneer de waarde van een streepjescode onjuist is, wordt de bitmap rood weergegeven.

![](assets/barcode_insert_11.png)
