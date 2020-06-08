---
title: De lijst met emoticonen aanpassen
description: Leer hoe u de emoticonlijst aanpast wanneer u Adobe Campagne Classic gebruikt.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3beb62d0264cfcb03486c291ce79cc7ff582e9c7
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---


# De lijst met emoticonen aanpassen {#customize-emoticons}

De emoticonlijst die in pop-up wordt getoond wordt bepaald door een opsomming die u toestaat om waarden in een lijst te tonen om de keuzen te beperken die de gebruiker voor een bepaald gebied heeft.
U kunt de volgorde van de emoticonlijst aanpassen en u kunt ook andere emoticons aan uw lijst toevoegen.
Er zijn emoticons beschikbaar voor e-mail en druk op deze [pagina](../../delivery/using/defining-the-email-content.md#inserting-emoticons)op om meer.

## Een nieuw emoticon toevoegen {#add-new-emoticon}

>[!CAUTION]
>
>De emoticonlijst kan niet meer dan 81 items weergeven.

1. Kies het nieuwe emoticon dat u van deze [pagina](https://unicode.org/emoji/charts/full-emoji-list.html)wilt toevoegen. Let op: deze moet compatibel zijn met de verschillende platforms, zoals de browser en het besturingssysteem.

1. Selecteer in het **[!UICONTROL Explorer]** vak **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** en klik op de **[!UICONTROL Emoticon list]** opsomming.

   >[!NOTE]
   >
   >De opsommingen buiten de doos kunnen slechts door een beheerder van uw Klassieke console van de Campagne van Adobe worden beheerd.

   ![](assets/emoticon_1.png)

1. Klik op **[!UICONTROL Add]**.

1. Vul de velden in:

   * **[!UICONTROL U+]**: Code van je nieuwe emoticon. De lijst met emoticons-codes vindt u op deze [pagina](https://unicode.org/emoji/charts/full-emoji-list.html).
Om compatibiliteitsproblemen te voorkomen, raden we u aan emoticons te kiezen die worden ondersteund door browsers en op elk besturingssysteem.

   * **[!UICONTROL Label]**: Label van uw nieuwe emoticon.
   ![](assets/emoticon_5.png)

1. Klik **[!UICONTROL Ok]** dan **[!UICONTROL Save]** wanneer uw configuratie wordt gebeëindigd.
Uw nieuwe emoticon wordt automatisch in de winkel geplaatst.

1. Als u het element wilt weergeven in het **[!UICONTROL Insert emoticon]** venster van uw leveringen, selecteert u het nieuwe emoticon door erop te dubbelklikken.

1. Kies in de **[!UICONTROL Display order]** vervolgkeuzelijst in welke volgorde het nieuwe emoticon wordt weergegeven. Door een reeds toegewezen weergavevolgorde te selecteren, wordt het bestaande emoticon automatisch naar de winkel verplaatst.

   <br>In dit voorbeeld hebben we de weergavevolgorde 61 gekozen. Dit houdt in dat als een item al deze volgorde had, dit item automatisch naar de winkel wordt verplaatst en dat onze nieuwe vermelding in de opsommingslijst wordt geplaatst.

   ![](assets/emoticon_2.png)

1. Uw nieuwe emoticon is nu toegevoegd aan de **[!UICONTROL Insert emoticon list]** opsomming uit de doos. U kunt het **[!UICONTROL Display order]** op elk gewenst moment wijzigen of naar de winkel verplaatsen als u het niet meer nodig hebt.

1. Als u rekening wilt houden met uw wijzigingen, verbreekt u de verbinding en maakt u opnieuw verbinding met Adobe Campagne Classic. Als het nieuwe emoticon nog steeds niet in het pop- **[!UICONTROL Insert emoticon]** upvenster wordt weergegeven, moet u mogelijk de cache wissen. For more on this, refer to this [section](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).

1. Uw nieuwe emoticon kunt u nu vinden in uw leveringen in het pop- **[!UICONTROL Insert emoticon]** upvenster op de 61ste positie zoals die in de vorige stappen wordt gevormd. Raadpleeg deze [pagina](../../delivery/using/defining-the-email-content.md#inserting-emoticons)voor meer informatie over het gebruik van emoticons in uw leveringen.

   ![](assets/emoticon_4.png)

1. Als de volgende emoticons in uw pop- **[!UICONTROL Insert emoticon]** up venster verschijnen, betekent dit dat zij niet correct werden gevormd. Controleer of uw **[!UICONTROL U+]** code of **[!UICONTROL Display order]** de code correct is in de **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
