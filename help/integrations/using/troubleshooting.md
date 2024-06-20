---
product: campaign
title: Problemen oplossen
description: Problemen oplossen
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
hide: true
hidefromtoc: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 3%

---

# Problemen oplossen{#troubleshooting}



In het geval van fout, zorg ervoor dat de volgende elementen correct worden gevormd:

* **Externe accounts**

  In **[!UICONTROL Administration > Platform > External accounts]**, zorgt u ervoor dat de volgende externe SFTP-accounts correct zijn geconfigureerd. De vermelde SFTP-servers hadden in Adobe Experience Cloud moeten zijn geconfigureerd door uw consultant.

   * **[!UICONTROL importSharedAudience]** : SFTP-account speciaal bestemd voor het importeren van soorten publiek.
   * **[!UICONTROL exportSharedAudience]** : SFTP-account gewijd aan het exporteren van soorten publiek.

* **AMC-gegevensbron**

  In **[!UICONTROL Administration > Platform > AMC Data sources]**, controleert u of de AMC-gegevensbron juist is ingesteld.

Het kan voorkomen dat sommige gegevens ontbreken wanneer het delen van een publiek via het Publiek van het Experience Cloud of wanneer het invoeren van een publiek. Alleen records waarvan de id (&#39;Bezoeker-id&#39; of &#39;Opgegeven ID&#39;) in overeenstemming kan worden gebracht met de profieldimensie, worden overgedragen. Id&#39;s uit de segmenten die niet door Adobe Campaign worden herkend, worden niet geïmporteerd.
