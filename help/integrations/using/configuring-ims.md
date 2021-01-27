---
solution: Campaign Classic
product: campaign
title: IMS configureren
description: Leer hoe u verbinding maakt via een Adobe ID
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
translation-type: tm+mt
source-git-commit: db595e59f4725ba5d125e688e7bfc6d1c1a03d9f
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 2%

---


# IMS{#configuring-ims} configureren

>[!IMPORTANT]
>
>De Adobe IMS-implementatie is strikt voorbehouden aan de technische Adobe-beheerders. Neem contact op met de Adobe-manager om het implementatieproces te starten.

## Vereisten {#prerequisites}

De integratie met de IMS gebruiken:

* U moet beschikken over een Adobe Experience Cloud-organisatie en IMS-id&#39;s (opgegeven wanneer u voor het eerst verbinding maakt met de Adobe Experience Cloud).
* U moet gebruikers toevoegen in de Experience Cloud. Raadpleeg [deze pagina](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html) voor meer informatie.

>[!NOTE]
>
>Controleer of uw gebruikers zijn gekoppeld aan de Adobe Experience Cloud-groepen die worden gesynchroniseerd met Adobe Campaign. Zie [De externe account configureren](#configuring-the-external-account).

## De console {#updating-the-console} bijwerken

Om deze functionaliteit te gebruiken, is het noodzakelijk dat u de recentste versie van de console installeert.

## Het pakket {#installing-the-package} installeren

U moet het **[!UICONTROL Integration with the Adobe Experience Cloud]** pakket installeren. Het installeren van een integratiepakket is hetzelfde als het installeren van een standaardpakket, dat wordt beschreven in [deze pagina](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## De externe account {#configuring-the-external-account} configureren

Configureer de **Adobe Experience Cloud** externe account in **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Deze configuratie is gereserveerd voor de technische beheerder.

![](assets/ims_5.png)

Voer de volgende gegevens in:

* Verbindingsgegevens voor de gebruikte IMS-server (id en geheim). Deze informatie wordt verstrekt door de steun van Adobe. Raadpleeg de [Veelgestelde vragen voor Adobe Experience Cloud-beheerders](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html) voor meer informatie.

   Het **[!UICONTROL Callback server]** adres moet in **https** worden gespecificeerd. Dit veld komt overeen met de toegangs-URL van uw Adobe Campaign-instantie.

* IMS-organisatie-id: Deze informatie is beschikbaar op de Experience Cloud (in **[!UICONTROL Administration > Experience Cloud Details]**) en wordt verstrekt wanneer u voor het eerst met Adobe Experience Cloud verbindt.
* Associatiemasker: In dit veld kunt u de syntaxis definiëren waarmee configuratienamen in het Enterprise-dashboard kunnen worden gesynchroniseerd met de groepen in Adobe Campaign. Als u de syntaxis &quot;Campagne - huurder_id - ( gebruikt.*)&quot;, wordt de beveiligingsgroep die in Adobe Campaign is gemaakt, gekoppeld aan de configuratienaam &quot;Campaign - huurder_id - internal_name&quot; in het Enterprise-dashboard.

   >[!CAUTION]
   >
   >Het associatiemasker is essentieel voor de verbinding via Adobe ID om correct te werken.

* Adobe Experience Cloud-verbindingsgegevens, met name de naam van de Adobe Experience Cloud Tenant.

