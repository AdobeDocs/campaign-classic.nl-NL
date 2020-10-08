---
title: Problemen oplossen
seo-title: Problemen oplossen
description: Problemen oplossen
seo-description: null
page-status-flag: never-activated
uuid: fb51ad18-221b-4058-b206-ca2ca045c507
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f3ff8c8e-22b0-4d61-9f26-11f5ca3bc0be
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 4%

---


# Problemen oplossen{#troubleshooting}

In het geval van fout, zorg ervoor dat de volgende elementen correct worden gevormd:

* **Externe accounts**

   Controleer **[!UICONTROL Administration > Platform > External accounts]** in of de volgende externe SFTP-accounts correct zijn geconfigureerd. De vermelde SFTP-servers hadden in Adobe Experience Cloud moeten zijn geconfigureerd door uw consultant.

   * **[!UICONTROL importSharedAudience]** : SFTP-account voor het importeren van soorten publiek.
   * **[!UICONTROL exportSharedAudience]** : SFTP-account voor het exporteren van soorten publiek.

* **AMC-gegevensbron**

   Controleer **[!UICONTROL Administration > Platform > AMC Data sources]** in of de AMC-gegevensbron juist is ingesteld.

Het kan voorkomen dat sommige gegevens ontbreken wanneer het delen van een publiek via de de kerndienst van Mensen of wanneer het invoeren van een publiek. Alleen records waarvan de id (&#39;Bezoeker-id&#39; of &#39;Opgegeven ID&#39;) in overeenstemming kan worden gebracht met de profieldimensie, worden overgedragen. IDs van de de kernde dienstsegmenten van Mensen die niet door Adobe Campaign worden erkend worden niet ingevoerd.
