---
product: campaign
title: Adobe Experience Platform-segmenten in campagne plaatsen
description: Leer hoe u een Adobe Experience Platform-publiek in Campaign Classic kunt opnemen
feature: Experience Platform Integration
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
source-git-commit: d15592aaccf036fc956049e611139ea5a46e9fc0
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---

# Adobe Experience Platform-segmenten in campagne plaatsen {#destinations}



Als u een Adobe Experience Platform-publiek wilt opnemen in de campagne en deze wilt gebruiken in uw workflows, moet u eerst Adobe Campaign als een Adobe Experience Platform verbinden **Doel** en configureer deze met het segment dat u wilt exporteren.

Zodra de Bestemming is gevormd, zullen de gegevens naar uw opslagplaats worden uitgevoerd, en u zult een specifieke werkschema in Campaign Classic moeten bouwen om het in te voeren.

## Adobe Campaign verbinden als doel

In het platform van de Ervaring van de Adobe, vorm een verbinding met Adobe Campaign door een opslagplaats voor de uitgevoerde segmenten te selecteren. Met deze stappen kunt u ook de segmenten selecteren die u wilt exporteren en aanvullende XDM-velden opgeven die u wilt opnemen.

Raadpleeg voor meer informatie de [Doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

Nadat de Bestemming is gevormd, leidt Adobe Experience Platform tot een lusje-afgebakend .txt of .csv- dossier in de opslagplaats die u verstrekte. Deze bewerking is gepland en wordt één keer per 24 uur uitgevoerd.

U kunt een werkschema van het Campaign Classic nu vormen om het segment in Campagne in te nemen.

## Een importworkflow maken in Campaign Classic

Zodra het Campaign Classic als Bestemming is gevormd, moet u een specifieke werkschema bouwen om het dossier in te voeren dat door Adobe Experience Platform is uitgevoerd.

Om dit te doen, moet u toevoegen en vormen **[!UICONTROL File transfer]** activiteit. Raadpleeg voor meer informatie over het configureren van deze activiteit [deze sectie](../../workflow/using/file-transfer.md).

![](assets/rtcdp-file-transfer.png)

Vervolgens kunt u uw workflow naar wens samenstellen (werk de database bij met behulp van de segmentgegevens, verzend een levering tussen kanalen naar het segment, enz.)

In de onderstaande workflow wordt het bestand bijvoorbeeld dagelijks vanaf de opslaglocatie gedownload en vervolgens wordt de Campagne-database bijgewerkt met de segmentgegevens.

![](assets/rtcdp-workflow.png)
