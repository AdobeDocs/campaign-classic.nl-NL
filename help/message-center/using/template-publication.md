---
title: Sjabloonpublicatie
seo-title: Sjabloonpublicatie
description: Sjabloonpublicatie
seo-description: null
page-status-flag: never-activated
uuid: f83dbe5f-762c-4c58-aeed-6ec289eb522f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 43908738-a71a-49be-ac00-175f57a0555c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1486e897a125520c51661db3030c62ab380fb173
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Sjabloonpublicatie{#template-publication}

Zodra het berichtmalplaatje op de controleinstantie wordt gecreeerd volledig is, kunt u het op alle uitvoeringsinstanties publiceren. Met Publicatie kunt u automatisch twee berichtsjablonen op de uitvoeringsinstantie maken waarmee u berichten kunt verzenden die zijn gekoppeld aan realtime- en batchgebeurtenissen.

>[!IMPORTANT]
>
>Vergeet niet de sjabloon te publiceren wanneer u er wijzigingen in aanbrengt, zodat deze wijzigingen tijdens de levering van transactiemeldingen van kracht worden.

>[!NOTE]
>
>Wanneer het publiceren van transactiemalplaatjes van het berichtbericht, worden de typologische regels automatisch gepubliceerd op de uitvoeringsinstanties.

1. Ga in de besturingsinstantie naar de **[!UICONTROL Message Center > Transactional message templates]** map van de boomstructuur.
1. Selecteer de sjabloon die u op de uitvoeringsinstanties wilt publiceren.
1. Klik op **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

Wanneer de publicatie is voltooid, worden zowel berichtsjablonen die moeten worden toegepast op batchgebeurtenissen als realtime-typegebeurtenissen gemaakt in de structuur van de productieinstantie in de **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** map.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Als u een bestaand veld van de transactiemplate voor berichten, zoals het adres van de afzender, vervangt door een lege waarde, wordt het corresponderende veld op de uitvoeringsinstantie(s) niet bijgewerkt wanneer het transactiemelding opnieuw wordt gepubliceerd. De vorige waarde blijft in de selectie staan. Als u echter een niet-lege waarde toevoegt, wordt het desbetreffende veld op de gebruikelijke wijze na de volgende publicatie bijgewerkt.
