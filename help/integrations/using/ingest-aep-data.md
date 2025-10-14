---
product: campaign
title: Adobe Experience Platform-segmenten in campagne plaatsen
description: Leer hoe u een Adobe Experience Platform-publiek kunt opnemen in Campaign Classic
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Adobe Experience Platform-segmenten in campagne plaatsen {#destinations}



Om het publiek van Adobe Experience Platform in Campagne op te nemen en hen in uw werkschema&#39;s te gebruiken, moet u eerst Adobe Campaign als Adobe Experience Platform **Bestemming** verbinden en het met het segment vormen om uit te voeren.

Zodra de Bestemming is gevormd, zullen de gegevens naar uw opslagplaats worden uitgevoerd, en u zult een specifieke werkschema in Campaign Classic moeten bouwen om het in te voeren.

## Adobe Campaign verbinden als doel

In het Adobe Experience-platform configureert u een verbinding met Adobe Campaign door een opslaglocatie voor de geëxporteerde segmenten te selecteren. Met deze stappen kunt u ook de segmenten selecteren die u wilt exporteren en aanvullende XDM-velden opgeven die u wilt opnemen.

Voor meer op dit, verwijs naar de [&#x200B; documentatie van Doelen &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=nl-NL).

Nadat de Bestemming is gevormd, leidt Adobe Experience Platform tot een lusje-afgebakend .txt of .csv- dossier in de opslagplaats die u verstrekte. Deze bewerking is gepland en wordt één keer per 24 uur uitgevoerd.

U kunt nu een Campaign Classic-workflow configureren om het segment in te voeren in Campagne.

## Een importworkflow maken in Campaign Classic

Als Campaign Classic eenmaal is geconfigureerd als een doel, moet u een specifieke workflow maken om het bestand te importeren dat door Adobe Experience Platform is geëxporteerd.

Hiervoor moet u een **[!UICONTROL File transfer]** -activiteit toevoegen en configureren. Voor meer op hoe te om deze activiteit te vormen, verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html?lang=nl-NL){target="_blank"}.

![](assets/rtcdp-file-transfer.png)

Vervolgens kunt u uw workflow naar wens samenstellen (werk de database bij met behulp van de segmentgegevens, verzend een levering tussen kanalen naar het segment, enz.)

In de onderstaande workflow wordt het bestand bijvoorbeeld dagelijks vanaf de opslaglocatie gedownload en vervolgens wordt de Campagne-database bijgewerkt met de segmentgegevens.

![](assets/rtcdp-workflow.png)
