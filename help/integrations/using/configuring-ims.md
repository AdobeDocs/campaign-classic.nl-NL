---
product: campaign
title: IMS configureren
description: Leer hoe u verbinding maakt via een Adobe ID
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 49271e291953483ee14709b26ec053217a336718
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 2%

---

# IMS configureren{#configuring-ims}

>[!IMPORTANT]
>
>Als op Campagne gehoste of beheerde de dienstengebruiker, is uw implementatie van Adobe IMS eigendom van Adobe. De hieronder beschreven stappen zijn alleen van toepassing op klanten op locatie en op hybride klanten.
> Adobe IMS-implementatie mag alleen worden uitgevoerd door technische beheerders van Adoben. Neem contact op met uw Adobe om het implementatieproces te starten.

## Vereisten {#prerequisites}

* U moet een Adobe Experience Cloud-naam en -id hebben. Raadpleeg voor meer informatie over uw organisatie-id [deze pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=nl){_blank}.
* U moet gebruikers toevoegen in het Experience Cloud. Raadpleeg voor meer informatie hierover [deze pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>Controleer of uw gebruikers zijn gekoppeld aan de Adobe Experience Cloud-groepen die worden gesynchroniseerd met Adobe Campaign. [Meer informatie](#configuring-the-external-account).

## De console bijwerken {#updating-the-console}

Om deze functionaliteit te gebruiken, is het noodzakelijk dat u de recentste versie van de console van de Cliënt installeert.

## Het pakket installeren {#installing-the-package}

U moet de ingebouwde **[!UICONTROL Integration with the Adobe Experience Cloud]** pakket. Een integratiepakket installeren is hetzelfde als een standaardpakket installeren, dat in [deze pagina](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## De externe account configureren {#configuring-the-external-account}

Vorm **Adobe Experience Cloud** externe rekening in **[!UICONTROL Administration > Platform > External accounts]**.

![](assets/ims_5.png)

Voer de volgende gegevens in:

* Verbindingsgegevens voor de gebruikte IMS-server (id en geheim). Deze informatie wordt verstrekt door het team van de Zorg van de Adobe. Raadpleeg voor meer informatie de [Veelgestelde vragen voor Adobe Experience Cloud-beheerders](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

  De **[!UICONTROL Callback server]** adres moet worden opgegeven in **https**. Dit veld komt overeen met de toegangs-URL van uw Adobe Campaign-instantie.

* Organisatie-id: raadpleeg voor meer informatie over uw organisatie-id [deze pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=nl){_blank}.

* Associatiemasker: in dit veld kunt u de syntaxis definiëren waarmee configuratienamen in het Enterprise-dashboard kunnen worden gesynchroniseerd met de groepen in Adobe Campaign. Als u de syntaxis &quot;Campagne - huurder_id - ( gebruikt.&#42;)&quot;, wordt de in Adobe Campaign gemaakte beveiligingsgroep gekoppeld aan de configuratienaam &quot;Campaign - huurder_id - internal_name&quot; in het Enterprise-dashboard.

* Adobe Experience Cloud connection information, which is the name of the Adobe Experience Cloud Tenant.
