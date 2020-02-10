---
title: Toegang tot leveringsgegevens
seo-title: Toegang tot leveringsgegevens
description: Toegang tot leveringsgegevens
seo-description: null
page-status-flag: never-activated
uuid: dc8f0267-1884-4a39-9a7d-d5ef21932928
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: d2631c67-7781-4baa-b24e-e7921353d131
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# Toegang tot leveringsgegevens{#accessing-deliveries-information}

## Toegang tot de lijst met leveringen {#accessing-the-list-of-deliveries}

Ga naar het **[!UICONTROL Campaigns]** universum en klik op de **[!UICONTROL Deliveries]** koppeling om de lijst met leveringen te openen.

Als u [de weergave](../../platform/using/adobe-campaign-workspace.md#about-adobe-campaign-explorer)Explorer gebruikt, hebt u toegang tot alle leveringen via het **[!UICONTROL Campaign management > Deliveries]** knooppunt in de boomstructuur.

>[!NOTE]
>
>De werkruimte van de Campagne van Adobe wordt voorgesteld in [deze sectie](../../platform/using/adobe-campaign-workspace.md).

Op deze pagina hebt u toegang tot een algemene weergave van uw leveringen: alle leveringen in uw database worden weergegeven. U kunt hun status, succespercentage en wijzigingsdatums weergeven.

![](assets/d_ncs_user_filter_interface_delivery01.png)

>[!NOTE]
>
>Het filteren van informatie wordt voorgesteld in [deze sectie](../../platform/using/filtering-options.md).

Met de wizard voor levering kunt u uw leveringen configureren, het goedkeuringsproces starten en verzenden. De inhoud van de wizard is afhankelijk van het communicatiekanaal (e-mail, mobiel, push, direct mail) en de exploitantrechten.

Als u de leveringen in de lijst wilt manipuleren, klikt u op een levering. Het wordt geopend in een nieuw venster en u kunt bijvoorbeeld de levering bevestigen of pauzeren.

![](assets/s_ncs_user_interface_delivery02.png)

Afhankelijk van het stadium van de leveringscyclus zijn de belangrijkste mogelijke statussen:

* Geannuleerd
* Mislukt
* In behandeling
* Voltooid
* Gepauzeerd
* Opnieuw proberen in behandeling
* In uitvoering
* Klaar voor levering
* Bezig met voorbereiding
* Doelberekening
* Wordt bewerkt

Elke status heeft een eigen kleur en label.

![](assets/s_ncs_user_status_campaigns_120.png)

In de vervolgkeuzelijst naast de **[!UICONTROL Create]** knop kunt u leveringen filteren op basis van hun status.

![](assets/delivery_filter_status.png)

## De leveringskalender openen {#accessing-the-delivery-calendar}

Ga naar het **[!UICONTROL Campaign]** universum en klik op de **[!UICONTROL Campaign calendar]** koppeling om de leveringskalender te openen. In deze kalender wordt de uitsplitsing van campagnes in de tijd weergegeven. U kunt de weergave aanpassen op maand, week of dag.

![](assets/s_ncs_user_interface_delivery04.png)

Klik op de naam van een levering om de belangrijkste informatie over de levering weer te geven. U kunt de campagne indien nodig ook openen door op **[!UICONTROL Open]** te klikken.

![](assets/s_ncs_user_interface_delivery05.png)

## Toegang tot de gegevens van de leveringproductie {#accessing-deliveries-throughput-information}

De informatie op de **[!UICONTROL Delivery throughput]** pagina heeft betrekking op alle leveringen van het platform. Om de snelheid te meten waarbij de berichten worden geleverd, zijn de criteria het aantal berichten die per uur worden verzonden en de grootte van de berichten (in beetjes per seconde). In het onderstaande voorbeeld ziet u in de eerste grafiek de geslaagde leveringen in blauw en het aantal onjuiste leveringen in oranje.

U kunt de tijdgroef kiezen waarvoor de productie wordt berekend. Selecteer hiertoe de waarde in de vervolgkeuzelijst en klik op **[!UICONTROL Refresh]**.

![](assets/s_ncs_user_interface_delivery06.png)

>[!NOTE]
>
>Voor gehoste of hybride installaties, als u aan Verbeterde MTA hebt bevorderd, zal de **[!UICONTROL Delivery throughput]** pagina niet meer de productie aan uw e-mailontvangers tonen. Het zal de productiesnelheid voor het relais van uw berichten van Campagne over aan Verbeterde MTA tonen.
>
>Raadpleeg dit [document](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)voor meer informatie over de verbeterde MTA voor Adobe-campagne.