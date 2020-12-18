---
solution: Campaign Classic
product: campaign
title: Problemen oplossen
description: Problemen oplossen
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---


# Problemen oplossen{#troubleshooting}

In het geval van fout, zorg ervoor dat de volgende elementen correct worden gevormd:

* **Externe accounts**

   Controleer in **[!UICONTROL Administration > Platform > External accounts]** of de volgende externe SFTP-accounts correct zijn geconfigureerd. De vermelde SFTP-servers hadden in Adobe Experience Cloud moeten zijn geconfigureerd door uw consultant.

   * **[!UICONTROL importSharedAudience]** : SFTP-account voor het importeren van soorten publiek.
   * **[!UICONTROL exportSharedAudience]** : SFTP-account voor het exporteren van soorten publiek.

* **AMC-gegevensbron**

   Controleer in **[!UICONTROL Administration > Platform > AMC Data sources]** of de AMC-gegevensbron juist is ingesteld.

Het kan voorkomen dat sommige gegevens ontbreken wanneer het delen van een publiek via de de kerndienst van Mensen of wanneer het invoeren van een publiek. Alleen records waarvan de id (&#39;Bezoeker-id&#39; of &#39;Opgegeven ID&#39;) in overeenstemming kan worden gebracht met de profieldimensie, worden overgedragen. IDs van de de kernde dienstsegmenten van Mensen die niet door Adobe Campaign worden erkend worden niet ingevoerd.
