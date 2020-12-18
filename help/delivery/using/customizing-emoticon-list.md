---
solution: Campaign Classic
product: campaign
title: De lijst met emoticons aanpassen
description: Leer hoe u de emoticonlijst aanpast wanneer u Adobe Campaign Classic gebruikt.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 3%

---


# De lijst met emoticons aanpassen {#customize-emoticons}

De emoticonlijst die in pop-up wordt getoond wordt bepaald door een opsomming die u toestaat om waarden in een lijst te tonen om de keuzen te beperken die de gebruiker voor een bepaald gebied heeft.
U kunt de volgorde van de emoticonlijst aanpassen en u kunt ook andere emoticons aan uw lijst toevoegen.
De moticons zijn beschikbaar voor e-mail en duw voor meer op dit verwijs naar [pagina](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

## Een nieuw emoticon toevoegen {#add-new-emoticon}

>[!CAUTION]
>
>De emoticonlijst kan niet meer dan 81 items weergeven.

1. Kies het nieuwe emoticon dat u uit deze [pagina](https://unicode.org/emoji/charts/full-emoji-list.html) wilt toevoegen. Let op: deze moet compatibel zijn met de verschillende platforms, zoals de browser en het besturingssysteem.

1. Selecteer **[!UICONTROL Explorer]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** en klik op de **[!UICONTROL Emoticon list]** opsomming in de doos.**[!UICONTROL Administration]**

   >[!NOTE]
   >
   >De opsommingen buiten de doos kunnen slechts door een beheerder van uw console van Adobe Campaign Classic worden beheerd.

   ![](assets/emoticon_1.png)

1. Klik op **[!UICONTROL Add]**.

1. Vul de velden in:

   * **[!UICONTROL U+]**: Code van je nieuwe emoticon. U kunt de lijst met emoticons&#39; codes vinden in deze [pagina](https://unicode.org/emoji/charts/full-emoji-list.html).
Om compatibiliteitsproblemen te voorkomen, raden we u aan emoticons te kiezen die worden ondersteund door browsers en op elk besturingssysteem.

   * **[!UICONTROL Label]**: Label van uw nieuwe emoticon.

   ![](assets/emoticon_5.png)

1. Klik **[!UICONTROL Ok]** dan **[!UICONTROL Save]** wanneer uw configuratie wordt gebeëindigd.
Uw nieuwe emoticon wordt automatisch in de winkel geplaatst.

1. Als u het element in het venster **[!UICONTROL Insert emoticon]** van uw leveringen wilt weergeven, selecteert u het nieuwe emoticon door erop te dubbelklikken.

1. Kies in **[!UICONTROL Display order]** drop-down waarin orde uw nieuw emoticon zal worden getoond. Door een reeds toegewezen weergavevolgorde te selecteren, wordt het bestaande emoticon automatisch naar de winkel verplaatst.

   <br>In dit voorbeeld hebben we de weergavevolgorde 61 gekozen. Dit houdt in dat als een item al deze volgorde had, dit item automatisch naar de winkel wordt verplaatst en dat onze nieuwe vermelding in de opsommingslijst wordt geplaatst.

   ![](assets/emoticon_2.png)

1. Uw nieuwe emoticon is nu toegevoegd aan **[!UICONTROL Insert emoticon list]** uit-van-de-doosopsomming. U kunt zijn **[!UICONTROL Display order]** op elk ogenblik veranderen of het verplaatsen naar de opslag als u het niet meer nodig hebt.

1. Als u rekening wilt houden met uw wijzigingen, verbreekt u de verbinding en maakt u opnieuw verbinding met Adobe Campaign Classic. Als uw nieuwe emoticon nog steeds niet in **[!UICONTROL Insert emoticon]** pop-up venster verschijnt, zou u uw geheime voorgeheugen kunnen moeten ontruimen. Raadpleeg deze [sectie](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear) voor meer informatie.

1. Uw nieuwe emoticon kan nu in uw leveringen in **[!UICONTROL Insert emoticon]** pop-up venster in de 61ste positie zoals gevormd in de vorige stappen worden gevonden. Voor meer informatie over hoe te om emoticons in uw leveringen te gebruiken, verwijs naar dit [pagina](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. Als de volgende emoticons in uw **[!UICONTROL Insert emoticon]** pop-up venster verschijnen, betekent dit dat zij niet correct werden gevormd. Controleer of uw **[!UICONTROL U+]**-code of **[!UICONTROL Display order]** correct is in **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
