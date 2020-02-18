---
title: zaadadressen toevoegen
seo-title: zaadadressen toevoegen
description: zaadadressen toevoegen
seo-description: null
page-status-flag: never-activated
uuid: e94ddd46-bed6-4505-91b7-7e17abb0e9c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 0b9b53bf-4dd2-416c-894e-393aded489f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# zaadadressen toevoegen{#adding-seed-addresses}

## Zaadadressen in een levering {#seed-addresses-in-a-delivery}

Om specifieke zaadadressen voor een levering toe te voegen, klik de **[!UICONTROL To]** verbinding, dan selecteer het **[!UICONTROL Seed addresses]** tabel.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Er zijn drie mogelijke invoegmodi:

1. Het ingaan van enige zaadadressen.

   Klik hiertoe op de **[!UICONTROL Add]** knop en definieer de inhoud van de adresvelden. Herhaal dit voor elk adres. Zie [deze sectie](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address)voor meer informatie.

1. Adressjablonen importeren en deze aan uw wensen aanpassen.

   Klik hiertoe op de **[!UICONTROL Import seed templates...]** koppeling en selecteer de map met de adressjablonen. Voor meer op dit, verwijs naar het [Creëren van zaadadresmalplaatjes](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates).

   Indien nodig, zodra zij worden toegevoegd, kunt u hen tweemaal klikken of de **[!UICONTROL Detail...]** knoop klikken om de inhoud van elk adres aan te passen.

1. Creërend een voorwaarde om dynamisch de controleadressen te selecteren die moeten worden opgenomen.

   Klik hiertoe op de **[!UICONTROL Edit the dynamic condition...]** koppeling en voer vervolgens de selectieparameters voor het zaadadres in. Bijvoorbeeld, kon u alle zaadadressen omvatten in een specifieke omslag, of zaadadressen die tot een specifieke afdeling van uw organisatie behoren.

   Een voorbeeld hiervan wordt in deze sectie gegeven: Hoofdlettergebruik [: het selecteren van zaadadressen op criteria](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Deze optie wordt gebruikt wanneer de gebruikte ontvankelijke lijst niet het gebrek **nms:ontvankelijke** lijst is en u de Inbox Rendering functionaliteit gebruikt die van de **[!UICONTROL Deliverability]** module van de Campagne van Adobe wordt voorzien.
>
>Raadpleeg voor meer informatie [Een externe tabel](../../delivery/using/using-an-external-recipient-table.md) voor ontvangers gebruiken en de documentatie over [Inbox-rendering](../../delivery/using/inbox-rendering.md).

Voor leveringen kunt u ook de manier aanpassen waarop adressen worden ingevoegd in het extractiebestand. Deze worden standaard ingevoegd in de sorteervolgorde van het uitvoerbestand, maar u kunt ervoor kiezen ze aan het einde of het begin van het bestand in te voegen, of willekeurig onder de ontvangers van het hoofddoel.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Adressen in een campagne {#seed-addresses-in-a-campaign}

Als u zaadadressen wilt toevoegen aan een doel voor een campagne, selecteert u de bewerking en klikt u op het **[!UICONTROL Edit]** tabblad.

Klik op de **[!UICONTROL Advanced campaign settings...]** koppeling en vervolgens op het **[!UICONTROL Seed addresses]** tabblad, zoals hieronder wordt weergegeven:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

De zaadadressen die van de campagne worden opgenomen zullen aan het doel van elke levering in de campagne worden toegevoegd.
