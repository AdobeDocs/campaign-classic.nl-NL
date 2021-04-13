---
solution: Campaign Classic
product: campaign
title: Adobe Experience Platform-segmenten in campagne plaatsen
description: Leer hoe u Adobe Experience Platform-publiek inneemt in Campaign Classic.
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: 9b3254c16eed784846db87d27f9f5de009dafdc3
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Adobe Experience Platform-segmenten opnemen in campagne {#destinations}

Als u Adobe Experience Platform wilt opnemen in Campagne en deze wilt gebruiken in uw workflows, moet u eerst Adobe Campaign verbinden als een Adobe Experience Platform **Doel** en deze configureren met het te exporteren segment.

Zodra de Bestemming is gevormd, zullen de gegevens naar uw opslagplaats worden uitgevoerd, en u zult een specifieke werkschema in Campaign Classic moeten bouwen om het in te voeren.

## Adobe Campaign verbinden als doel

In het Adobe Experience-platform configureert u een verbinding met Adobe Campaign door een opslaglocatie voor de geëxporteerde segmenten te selecteren. Met deze stappen kunt u ook de segmenten selecteren die u wilt exporteren en aanvullende XDM-velden opgeven die u wilt opnemen.

Raadpleeg de [documentatie bij Doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html) voor meer informatie.

Nadat de Bestemming is gevormd, leidt Adobe Experience Platform tot een lusje-afgebakend .txt of .csv- dossier in de opslagplaats die u verstrekte. Deze bewerking is gepland en wordt één keer per 24 uur uitgevoerd.

U kunt nu een Campaign Classic-workflow configureren om het segment in te voeren in Campagne.

## Een importworkflow maken in Campaign Classic

Zodra Campaign Classic is gevormd als Bestemming, moet u een specifieke werkschema bouwen om het dossier in te voeren dat door Adobe Experience Platform is uitgevoerd.

Om dit te doen, moet u een **[!UICONTROL File transfer]** activiteit toevoegen en vormen. Raadpleeg [deze sectie](../../workflow/using/file-transfer.md) voor meer informatie over het configureren van deze activiteit.

![](assets/rtcdp-file-transfer.png)

Vervolgens kunt u uw workflow naar wens samenstellen (werk de database bij met behulp van de segmentgegevens, verzend een levering tussen kanalen naar het segment, enz.)

In de onderstaande workflow wordt het bestand bijvoorbeeld dagelijks vanaf de opslaglocatie gedownload en vervolgens wordt de Campagne-database bijgewerkt met de segmentgegevens.

![](assets/rtcdp-workflow.png)