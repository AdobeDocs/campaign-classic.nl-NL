---
product: campaign
title: IMS configureren
description: Leer hoe u verbinding maakt via een Adobe ID
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 4%

---

# IMS configureren{#configuring-ims}

![](../../assets/common.svg)

>[!IMPORTANT]
>
>De implementatie van Adobe IMS is uitsluitend voorbehouden aan de technische beheerders van de Adobe. Neem contact op met de Adobe-manager om het implementatieproces te starten.

## Vereisten {#prerequisites}

De integratie met de IMS gebruiken:

* U moet een Adobe Experience Cloud-naam en -id hebben. Raadpleeg voor meer informatie over uw organisatie-id [deze pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=nl){_blank}.
* U moet gebruikers toevoegen in de Experience Cloud. Raadpleeg voor meer informatie hierover [deze pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>Controleer of uw gebruikers zijn gekoppeld aan de Adobe Experience Cloud-groepen die worden gesynchroniseerd met Adobe Campaign. [Meer informatie](#configuring-the-external-account).

## De console bijwerken {#updating-the-console}

Om deze functionaliteit te gebruiken, is het noodzakelijk dat u de recentste versie van de console installeert.

## Het pakket installeren {#installing-the-package}

U moet de ingebouwde **[!UICONTROL Integration with the Adobe Experience Cloud]** pakket. Een integratiepakket installeren is hetzelfde als een standaardpakket installeren, dat in [deze pagina](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## De externe account configureren {#configuring-the-external-account}

Configureer de **Adobe Experience Cloud** externe rekening in **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Deze configuratie is gereserveerd voor de technische beheerder.

![](assets/ims_5.png)

Voer de volgende gegevens in:

* Verbindingsgegevens voor de gebruikte IMS-server (id en geheim). Deze informatie wordt verstrekt door de steun van Adobe. Raadpleeg voor meer informatie de [Veelgestelde vragen voor Adobe Experience Cloud-beheerders](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

   De **[!UICONTROL Callback server]** adres moet worden opgegeven in **https**. Dit veld komt overeen met de toegangs-URL van uw Adobe Campaign-instantie.

* Organisatie-id: om uw organisatie-id te zoeken, raadpleegt u [deze pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=nl){_blank}.
* Associatiemasker: In dit veld kunt u de syntaxis definiëren waarmee configuratienamen in het Enterprise-dashboard kunnen worden gesynchroniseerd met de groepen in Adobe Campaign. Als u de syntaxis &quot;Campagne - huurder_id - ( gebruikt.&#42;)&quot;, wordt de in Adobe Campaign gemaakte beveiligingsgroep gekoppeld aan de configuratienaam &quot;Campaign - huurder_id - internal_name&quot; in het Enterprise-dashboard.

   >[!CAUTION]
   >
   >Het associatiemasker is essentieel voor de verbinding via Adobe ID om correct te werken.

* Adobe Experience Cloud-verbindingsgegevens, met name de naam van de Adobe Experience Cloud Tenant.
