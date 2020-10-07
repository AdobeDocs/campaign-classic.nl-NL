---
title: Personalisatiedata
seo-title: Personalisatiedata
description: Personalisatiedata
seo-description: null
page-status-flag: never-activated
uuid: d3d66216-502a-410b-b062-fb413eb9363f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 2cd8a320-37e8-410a-b71b-0c13c8e15482
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 5%

---


# Personalisatiedata{#personalization-data}

Het is mogelijk om gegevens in het berichtmalplaatje te gebruiken om transactionele berichtverpersoonlijking te testen. Deze functie wordt gebruikt om een voorvertoning te genereren of een proefdruk te verzenden. Als u de module **Leverbaarheid** installeert, kunt u met deze gegevens een weergave van de berichten weergeven voor verschillende providers van internettoegang (**Inbox-rendering**: zie voor meer informatie [deze sectie](../../delivery/using/about-deliverability.md)).

Het doel van deze gegevens is om uw berichten vóór hun definitieve levering te testen. Deze berichten vallen niet samen met werkelijke gegevens die door Message Center moeten worden verwerkt. De XML-structuur moet echter gelijk zijn aan die van de gebeurtenis die in de uitvoeringsinstantie is opgeslagen, zoals hieronder wordt weergegeven.

![](assets/messagecenter_create_custo_006.png)

Met deze informatie kunt u de inhoud van berichten personaliseren met personalisatietags (zie [Berichtinhoud](../../message-center/using/creating-message-content.md)maken voor meer informatie).

1. Klik in de berichtsjabloon op de **[!UICONTROL Seed addresses]** tab.
1. Voer in de inhoud van de gebeurtenis de testinformatie in XML-indeling in.

   ![](assets/messagecenter_create_custo_001.png)

