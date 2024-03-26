---
product: campaign
title: Problemen oplossen
description: Problemen oplossen
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 4%

---

# Problemen oplossen{#troubleshooting}



In het geval van fout, zorg ervoor dat de volgende elementen correct worden gevormd:

* **Externe accounts**

  In **[!UICONTROL Administration > Platform > External accounts]**, zorgt u ervoor dat de volgende externe SFTP-accounts correct zijn geconfigureerd. De vermelde SFTP-servers hadden in Adobe Experience Cloud moeten zijn geconfigureerd door uw consultant.

   * **[!UICONTROL importSharedAudience]** : SFTP-account speciaal bestemd voor het importeren van soorten publiek.
   * **[!UICONTROL exportSharedAudience]** : SFTP-account gewijd aan het exporteren van soorten publiek.

* **AMC-gegevensbron**

  In **[!UICONTROL Administration > Platform > AMC Data sources]**, controleert u of de AMC-gegevensbron juist is ingesteld.

Het kan voorkomen dat sommige gegevens ontbreken wanneer het delen van een publiek via de de kerndienst van Mensen of wanneer het invoeren van een publiek. Alleen records waarvan de id (&#39;Bezoeker-id&#39; of &#39;Opgegeven ID&#39;) in overeenstemming kan worden gebracht met de profieldimensie, worden overgedragen. IDs van de de kernde dienstsegmenten van Mensen die niet door Adobe Campaign worden erkend worden niet ingevoerd.
