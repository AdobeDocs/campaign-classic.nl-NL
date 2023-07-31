---
product: campaign
title: Transactieberichtsjablonen testen
description: Leer hoe u zaadadressen in transactieberichten beheert om deze in Adobe Campaign Classic voor te vertonen en te testen
feature: Transactional Messaging, Message Center, Templates
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 2%

---

# Transactieberichtsjablonen testen {#testing-message-templates}



Eenmaal uw [berichtsjabloon](../../message-center/using/creating-the-message-template.md) is gereed, volgt u de onderstaande stappen om deze voor te vertonen en te testen.

## Seedadressen in transactionele berichten beheren {#managing-seed-addresses-in-transactional-messages}

Met een zaadadres kunt u een voorbeeld van uw bericht weergeven, een proefdruk verzenden en de personalisatie van testberichten vóór verzending via e-mail of SMS uitvoeren. De zaadadressen zijn verbonden met de levering en kunnen niet voor andere leveringen worden gebruikt.

Voer de onderstaande stappen uit om zaadadressen te maken in een transactiemelding:

1. Klik in de sjabloon Transactiebericht op de knop **[!UICONTROL Seed addresses]** tab.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Wijs er een label aan toe zodat u het later gemakkelijk kunt selecteren.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Voer het zaadadres in (e-mail of mobiele telefoon, afhankelijk van het communicatiekanaal).

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Voer de externe id in: in dit optionele veld kunt u een zakelijke sleutel invoeren (unieke id, naam + e-mail, enz.) Deze instelling geldt voor alle toepassingen op uw website die worden gebruikt om uw profielen te identificeren. Als dit veld ook aanwezig is in de Adobe Campaign-marketingdatabase, kunt u een gebeurtenis vervolgens afstemmen op een profiel in de database.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. Testgegevens invoegen (zie [Persoonlijke gegevens](#personalization-data)).

   ![](assets/messagecenter_create_custo_001.png)

   <!--## Creating several seed addresses {#creating-several-seed-addresses}-->
1. Klik op de knop **[!UICONTROL Add other seed addresses]** klikt u op de koppeling **[!UICONTROL Add]** knop.

   ![](assets/messagecenter_create_seedaddr_004.png)

   <!--1. Follow the configuration steps for a seed address detailed in the [Creating a seed address](#creating-a-seed-address) section.-->
1. Herhaal dit proces om zoveel adressen te maken als u nodig hebt.

   ![](assets/messagecenter_create_seedaddr_008.png)

Zodra de adressen worden gecreeerd, kunt u hun voorproef en verpersoonlijking tonen. Zie [Voorvertoning van Transactiebericht](#transactional-message-preview).

## Personalisatiegegevens {#personalization-data}

Het is mogelijk om gegevens in het berichtmalplaatje te gebruiken om transactionele berichtverpersoonlijking te testen. Deze functie wordt gebruikt om een voorvertoning te genereren of een proefdruk te verzenden. U kunt de weergave van het bericht ook weergeven voor verschillende providers van internettoegang. Zie voor meer informatie [Inbox-rendering](../../delivery/using/inbox-rendering.md).

Het doel van deze gegevens is om uw berichten vóór hun definitieve levering te testen. Deze berichten komen niet overeen met de werkelijk te verwerken gegevens. De XML-structuur moet echter gelijk zijn aan die van de gebeurtenis die in de uitvoeringsinstantie is opgeslagen, zoals hieronder wordt getoond:

![](assets/messagecenter_create_custo_006.png)

Met deze informatie kunt u de inhoud van berichten personaliseren met personalisatie-tags (zie voor meer informatie [Berichtinhoud maken](../../message-center/using/creating-the-message-template.md#creating-message-content)).

1. Selecteer het transactiemalplaatje van het bericht.

1. Klik in de sjabloon op de knop **[!UICONTROL Seed addresses]** tab.

1. Voer in de inhoud van de gebeurtenis de testinformatie in XML-indeling in.

   ![](assets/messagecenter_create_custo_001.png)

1. Klik op **[!UICONTROL Save]**.

## Voorvertoning van transactionele berichten  {#transactional-message-preview}

Zodra u één of meerdere zaadadressen en het berichtlichaam hebt gecreeerd, kunt u voorproef het bericht en zijn verpersoonlijking controleren.

1. Klik in de berichtsjabloon op de knop **[!UICONTROL Preview]** tab.

   ![](assets/messagecenter_preview_001.png)

1. Selecteren **[!UICONTROL A seed address]** in de vervolgkeuzelijst.

   ![](assets/messagecenter_preview_002.png)

1. Selecteer het zaadadres eerder wordt gecreeerd om het gepersonaliseerde bericht te tonen dat.

   ![](assets/messagecenter_create_seedaddr_009.png)

Met zaadadressen kunt u ook de weergave van het bericht voor verschillende internettoegangsproviders weergeven. Zie voor meer informatie [Inbox-rendering](../../delivery/using/inbox-rendering.md).

## Een proef verzenden {#sending-a-proof}

U kunt berichtlevering testen door een bewijs naar een eerder gecreeerd zaadadres te verzenden.

Bij het verzenden van een proefdruk wordt hetzelfde proces uitgevoerd als bij een proefdruk [regelmatige levering](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof). Met transactiemeldingen moet u echter de volgende bewerkingen vooraf uitvoeren:

* Een of meer maken [zaadadressen](#managing-seed-addresses-in-transactional-messages) with [personalisatiegegevens](#personalization-data).
* [Berichtinhoud maken](../../message-center/using/creating-the-message-template.md#creating-message-content).

Het bewijs verzenden:

1. Klik op de knop **[!UICONTROL Send a proof]** in het leveringsvenster.
1. Analyseer de levering.
1. Corrigeer eventuele fouten en bevestig de levering.

   ![](assets/messagecenter_send_proof_001.png)

1. Controleer of het bericht aan het zaadadres is bezorgd en of de inhoud ervan aan uw configuratie voldoet.

   ![](assets/messagecenter_send_proof_002.png)

In elke sjabloon zijn proefdrukken toegankelijk via de **[!UICONTROL Audit]** tab. Zie voor meer informatie hierover [Een proefdruk verzenden](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

![](assets/messagecenter_send_proof_003.png)

Uw berichtsjabloon is nu gereed om te worden [gepubliceerd](../../message-center/using/publishing-message-templates.md).