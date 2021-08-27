---
product: campaign
title: Seed-adressen toevoegen
description: Seed-adressen toevoegen
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 5%

---

# Seedadressen toevoegen{#adding-seed-addresses}

![](../../assets/common.svg)

## Zaadadressen in een levering {#seed-addresses-in-a-delivery}

Om specifieke zaadadressen voor een levering toe te voegen, klik **[!UICONTROL To]** verbinding, dan selecteer **[!UICONTROL Seed addresses]** tabel.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Er zijn drie mogelijke invoegmodi:

1. Het ingaan van enige zaadadressen.

   Klik hiertoe op de knop **[!UICONTROL Add]** en definieer de inhoud van de adresvelden. Herhaal dit voor elk adres.

1. Adressjablonen importeren en deze aan uw wensen aanpassen.

   Om dit te doen, klik **[!UICONTROL Import seed templates...]** verbinding en selecteer de omslag die de adresmalplaatjes bevat. Raadpleeg [deze sectie](creating-seed-addresses.md#creating-seed-address-templates) voor meer informatie.

   Indien nodig, zodra zij worden toegevoegd, kunt u hen tweemaal klikken of **[!UICONTROL Detail...]** knoop klikken om de inhoud van elk adres aan te passen.

1. Creërend een voorwaarde om dynamisch de controleadressen te selecteren die moeten worden opgenomen.

   Om dit te doen, klik **[!UICONTROL Edit the dynamic condition...]** verbinding, dan ga de parameters van de zaadselectie in. Bijvoorbeeld, kon u alle zaadadressen omvatten in een specifieke omslag, of zaadadressen die tot een specifieke afdeling van uw organisatie behoren.

   Een voorbeeld hiervan wordt in deze sectie gegeven: [Hoofdlettergebruik: zaadadressen op criteria](use-case--selecting-seed-addresses-on-criteria.md) selecteren.

>[!NOTE]
>
>Deze optie wordt gebruikt wanneer de gebruikte ontvankelijke lijst niet het gebrek **nms:ontvanger** lijst is en u gebruikt de Inbox Rendering functionaliteit die met Adobe Campaign **[!UICONTROL Deliverability]** module wordt verstrekt.
>
>Zie [Een externe tabel voor ontvangers gebruiken](using-an-external-recipient-table.md) en de documentatie over [Inbox-rendering](inbox-rendering.md) voor meer informatie.

Voor leveringen kunt u ook de manier aanpassen waarop adressen worden ingevoegd in het extractiebestand. Deze worden standaard ingevoegd in de sorteervolgorde van het uitvoerbestand, maar u kunt ervoor kiezen ze aan het einde of het begin van het bestand in te voegen, of willekeurig onder de ontvangers van het hoofddoel.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Adressen in een campagne {#seed-addresses-in-a-campaign}

Als u zaadadressen wilt toevoegen aan een doel voor een campagne, selecteert u de bewerking en klikt u op het tabblad **[!UICONTROL Edit]**.

Klik op de koppeling **[!UICONTROL Advanced campaign settings...]** en vervolgens op de tab **[!UICONTROL Seed addresses]**, zoals hieronder wordt weergegeven:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

De zaadadressen die van de campagne worden opgenomen zullen aan het doel van elke levering in de campagne worden toegevoegd.
