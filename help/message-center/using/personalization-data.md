---
solution: Campaign Classic
product: campaign
title: Personalisatiedata
description: Personalisatiedata
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# Personalisatiedata{#personalization-data}

Het is mogelijk om gegevens in het berichtmalplaatje te gebruiken om transactionele berichtverpersoonlijking te testen. Deze functie wordt gebruikt om een voorvertoning te genereren of een proefdruk te verzenden. Als u de **Deliverability** module installeert, staat dit gegeven u toe om een teruggave van de berichten voor diverse leveranciers van de internettoegang (**Inbox teruggeven**: Zie [deze sectie](../../delivery/using/inbox-rendering.md)) voor meer informatie hierover.

Het doel van deze gegevens is om uw berichten vóór hun definitieve levering te testen. Deze berichten vallen niet samen met werkelijke gegevens die door Message Center moeten worden verwerkt. De XML-structuur moet echter gelijk zijn aan die van de gebeurtenis die in de uitvoeringsinstantie is opgeslagen, zoals hieronder wordt weergegeven.

![](assets/messagecenter_create_custo_006.png)

Deze informatie laat u toe om berichtinhoud te personaliseren gebruikend verpersoonlijkingsmarkeringen (voor meer op dit, verwijs naar [het Creëren van berichtinhoud](../../message-center/using/creating-message-content.md)).

1. Klik in de berichtsjabloon op het tabblad **[!UICONTROL Seed addresses]**.
1. Voer in de inhoud van de gebeurtenis de testinformatie in XML-indeling in.

   ![](assets/messagecenter_create_custo_001.png)
