---
product: campaign
title: Transactieberichtsjablonen testen
description: Leer hoe u zaadadressen in transactieberichten beheert om deze in Adobe Campaign Classic voor te vertonen en te testen
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 2%

---

# Transactieberichtsjablonen testen {#testing-message-templates}



Zodra uw [ berichtmalplaatje ](../../message-center/using/creating-the-message-template.md) klaar is, volg de stappen hieronder aan voorproef en test het.

## Seedadressen in transactionele berichten beheren {#managing-seed-addresses-in-transactional-messages}

Met een zaadadres kunt u een voorbeeld van uw bericht weergeven, een proefdruk verzenden en de personalisatie van testberichten vóór verzending via e-mail of SMS uitvoeren. De zaadadressen zijn verbonden met de levering en kunnen niet voor andere leveringen worden gebruikt.

Voer de onderstaande stappen uit om zaadadressen te maken in een transactiemelding:

1. Klik in de transactiemalplaatje op de tab **[!UICONTROL Seed addresses]** .

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Wijs er een label aan toe zodat u het later gemakkelijk kunt selecteren.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Voer het zaadadres in (e-mail of mobiele telefoon, afhankelijk van het communicatiekanaal).

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Voer de externe id in: in dit optionele veld kunt u een bedrijfssleutel invoeren (unieke id, naam + e-mail, enz.) die wordt gebruikt voor alle toepassingen op uw website en waarmee uw profielen worden geïdentificeerd. Als dit veld ook aanwezig is in de Adobe Campaign-marketingdatabase, kunt u een gebeurtenis vervolgens afstemmen op een profiel in de database.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. De testgegevens van het tussenvoegsel (verwijs naar [ gegevens van Personalization ](#personalization-data)).

   ![](assets/messagecenter_create_custo_001.png)

   <!--## Creating several seed addresses {#creating-several-seed-addresses}-->
1. Klik op de koppeling **[!UICONTROL Add other seed addresses]** en klik vervolgens op de knop **[!UICONTROL Add]** .

   ![](assets/messagecenter_create_seedaddr_004.png)

   <!--1. Follow the configuration steps for a seed address detailed in the [Creating a seed address](#creating-a-seed-address) section.-->
1. Herhaal dit proces om zoveel adressen te maken als u nodig hebt.

   ![](assets/messagecenter_create_seedaddr_008.png)

Zodra de adressen worden gecreeerd, kunt u hun voorproef en verpersoonlijking tonen. Verwijs naar [ Transactionele berichtvoorproef ](#transactional-message-preview).

## Personalisatiegegevens {#personalization-data}

Het is mogelijk om gegevens in het berichtmalplaatje te gebruiken om transactionele berichtverpersoonlijking te testen. Deze functie wordt gebruikt om een voorvertoning te genereren of een proefdruk te verzenden. U kunt de weergave van het bericht ook weergeven voor verschillende providers van internettoegang. Voor meer op dit, zie [ Inbox teruggevend ](../../delivery/using/inbox-rendering.md).

Het doel van deze gegevens is om uw berichten vóór hun definitieve levering te testen. Deze berichten komen niet overeen met de werkelijk te verwerken gegevens. De XML-structuur moet echter gelijk zijn aan die van de gebeurtenis die in de uitvoeringsinstantie is opgeslagen, zoals hieronder wordt getoond:

![](assets/messagecenter_create_custo_006.png)

Deze informatie laat u toe om berichtinhoud te personaliseren gebruikend verpersoonlijkingsmarkeringen (voor meer op dit, zie [ de berichtinhoud ](../../message-center/using/creating-the-message-template.md#creating-message-content) creëren).

1. Selecteer het transactiemalplaatje van het bericht.

1. Klik in de sjabloon op de tab **[!UICONTROL Seed addresses]** .

1. Voer in de inhoud van de gebeurtenis de testinformatie in XML-indeling in.

   ![](assets/messagecenter_create_custo_001.png)

1. Klik op **[!UICONTROL Save]**.

## Voorvertoning van transactionele berichten  {#transactional-message-preview}

Zodra u één of meerdere zaadadressen en het berichtlichaam hebt gecreeerd, kunt u voorproef het bericht en zijn verpersoonlijking controleren.

1. Klik in de berichtsjabloon op de tab **[!UICONTROL Preview]** .

   ![](assets/messagecenter_preview_001.png)

1. Selecteer **[!UICONTROL A seed address]** in de vervolgkeuzelijst.

   ![](assets/messagecenter_preview_002.png)

1. Selecteer het zaadadres eerder wordt gecreeerd om het gepersonaliseerde bericht te tonen dat.

   ![](assets/messagecenter_create_seedaddr_009.png)

Met zaadadressen kunt u ook de weergave van het bericht voor verschillende internettoegangsproviders weergeven. Voor meer op dit, zie [ Inbox teruggevend ](../../delivery/using/inbox-rendering.md).

## Een proef verzenden {#sending-a-proof}

U kunt berichtlevering testen door een bewijs naar een eerder gecreeerd zaadadres te verzenden.

Bij het verzenden van een bewijs wordt hetzelfde proces gebruikt als bij een normale levering. Zie de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html){target="_blank"}. Met transactiemeldingen moet u echter de volgende bewerkingen vooraf uitvoeren:

* Creeer één of meerdere [ zaadadressen ](#managing-seed-addresses-in-transactional-messages) met [ verpersoonlijkingsgegevens ](#personalization-data).
* [ creeer de berichtinhoud ](../../message-center/using/creating-the-message-template.md#creating-message-content).

Het bewijs verzenden:

1. Klik op de knop **[!UICONTROL Send a proof]** in het leveringsvenster.
1. Analyseer de levering.
1. Corrigeer eventuele fouten en bevestig de levering.

   ![](assets/messagecenter_send_proof_001.png)

1. Controleer of het bericht aan het zaadadres is bezorgd en of de inhoud ervan aan uw configuratie voldoet.

   ![](assets/messagecenter_send_proof_002.png)

In elke sjabloon kunt u proefdrukken openen via het tabblad **[!UICONTROL Audit]** . Voor meer details op dit, zie de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html){target="_blank"}.

![](assets/messagecenter_send_proof_003.png)

Uw berichtmalplaatje is nu klaar om [ worden gepubliceerd ](../../message-center/using/publishing-message-templates.md).