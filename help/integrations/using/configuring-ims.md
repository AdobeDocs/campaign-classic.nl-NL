---
title: IMS configureren
seo-title: IMS configureren
description: IMS configureren
seo-description: null
page-status-flag: never-activated
uuid: b659d29f-2a27-4a7b-b5ca-f44c3271dd4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: 279d0548-c876-4d5f-a195-48618bd5e9d1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0a4272ae13b469c7c17b8c3afa9748cbfbcf07ff

---


# IMS configureren{#configuring-ims}

## Vereisten {#prerequisites}

De integratie met de IMS gebruiken:

* U moet beschikken over een Adobe Experience Cloud-organisatie en IMS-id&#39;s (die worden geleverd wanneer u voor het eerst verbinding maakt met de Adobe Experience Cloud).
* U moet gebruikers toevoegen in de Experience Cloud. For more on this, refer to [this page](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!NOTE]
>
>Zorg ervoor dat uw gebruikers zijn gekoppeld aan de Adobe Experience Cloud-groepen die worden gesynchroniseerd met Adobe Campaign. Zie De externe account [](#configuring-the-external-account)configureren.

## De console bijwerken {#updating-the-console}

Om deze functionaliteit te gebruiken, is het noodzakelijk dat u de recentste versie van de console installeert.

## Het pakket installeren {#installing-the-package}

U moet het **[!UICONTROL Integration with the Adobe Experience Cloud]** pakket installeren. Het installeren van een integratiepakket is hetzelfde als het installeren van een standaardpakket, dat in [deze pagina](../../installation/using/installing-campaign-standard-packages.md)wordt beschreven.

![](assets/ims_6.png)

## De externe account configureren {#configuring-the-external-account}

Configureer de externe account voor de **Adobe Experience Cloud** in **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Deze configuratie is gereserveerd voor de technische beheerder.

![](assets/ims_5.png)

Voer de volgende gegevens in:

* Verbindingsgegevens voor de gebruikte IMS-server (id en geheim). Deze informatie wordt geleverd door ondersteuning van Adobe. Raadpleeg de [veelgestelde vragen voor Adobe Experience Cloud-beheerders](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html)voor meer informatie.

   Het **[!UICONTROL Callback server]** adres moet in **https** worden gespecificeerd. Dit veld komt overeen met de toegangs-URL van uw Adobe Campagne-instantie.

* IMS-organisatie-id: Deze informatie is beschikbaar in de Experience Cloud (in **[!UICONTROL Administration > Experience Cloud Details]** ) en wordt weergegeven wanneer u voor het eerst verbinding maakt met de Adobe Experience Cloud.
* Associatiemasker: In dit veld kunt u de syntaxis definiëren waarmee configuratienamen in het Enterprise-dashboard kunnen worden gesynchroniseerd met de groepen in Adobe Campaign. Als u de syntaxis &quot;Campagne - huurder_id - ( gebruikt.*)&quot;, wordt de beveiligingsgroep die in Adobe Campaign is gemaakt, gekoppeld aan de configuratienaam ‘Campaign - huurder_id - internal_name’ in het Enterprise-dashboard.

   >[!CAUTION]
   >
   >Het associatiemasker is essentieel voor de verbinding via Adobe-id om correct te werken.

* Adobe Experience Cloud-verbindingsgegevens, met name de naam van de Adobe Experience Cloud Tenant.

