---
product: campaign
title: Seedadressen toevoegen
description: Seedadressen toevoegen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Seed Address
role: User
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 5%

---

# Seedadressen toevoegen{#adding-seed-addresses}

## Zaadadressen in een levering {#seed-addresses-in-a-delivery}

Om specifieke zaadadressen voor een levering toe te voegen, klik **[!UICONTROL To]** Selecteer vervolgens de koppeling **[!UICONTROL Seed addresses]** tab.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Er zijn drie mogelijke invoegmodi:

1. Het ingaan van enige zaadadressen.

   Om dit te doen, klik **[!UICONTROL Add]** en definieert u de inhoud van de adresvelden. Herhaal dit voor elk adres.

1. Importeer adressjablonen en pas deze aan uw wensen aan.

   Om dit te doen, klik **[!UICONTROL Import seed templates...]** en selecteer de map die de adressjablonen bevat. Raadpleeg [deze sectie](creating-seed-addresses.md#creating-seed-address-templates) voor meer informatie.

   Indien nodig kunt u dubbelklikken op de knoppen nadat u ze hebt toegevoegd of op de knop **[!UICONTROL Detail...]** om de inhoud van elk adres aan te passen.

1. Creërend een voorwaarde om dynamisch de controleadressen te selecteren die moeten worden opgenomen.

   Om dit te doen, klik **[!UICONTROL Edit the dynamic condition...]** en voer vervolgens de selectieparameters voor het zaadadres in. Bijvoorbeeld, kon u alle zaadadressen omvatten in een specifieke omslag, of zaadadressen die tot een specifieke afdeling van uw organisatie behoren.

   Een voorbeeld hiervan wordt in deze sectie gegeven: [Hoofdlettergebruik: zaadadressen op criteria selecteren](use-case-selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Deze optie wordt gebruikt wanneer de gebruikte ontvankelijke lijst niet het gebrek is **nms:ontvanger** tabel en u gebruikt de bij Adobe Campaign geleverde functionaliteit voor Inbox Rendering **[!UICONTROL Deliverability]** -module.
>
>Raadpleeg voor meer informatie hierover [Een externe tabel voor ontvangers gebruiken](using-an-external-recipient-table.md) en de documentatie over [Inbox-rendering](inbox-rendering.md).

Voor leveringen kunt u ook de manier aanpassen waarop adressen worden ingevoegd in het extractiebestand. Deze worden standaard ingevoegd in de sorteervolgorde van het uitvoerbestand, maar u kunt ervoor kiezen ze aan het einde of het begin van het bestand in te voegen, of willekeurig onder de ontvangers van het hoofddoel.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Adressen in een campagne {#seed-addresses-in-a-campaign}

Als u zaadadressen wilt toevoegen aan een doel voor een campagne, selecteert u de bewerking en klikt u op de knop **[!UICONTROL Edit]** tab.

Klik op de knop **[!UICONTROL Advanced campaign settings...]** en vervolgens de **[!UICONTROL Seed addresses]** tab, zoals hieronder wordt getoond:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

De zaadadressen die van de campagne worden opgenomen zullen aan het doel van elke levering in de campagne worden toegevoegd.
