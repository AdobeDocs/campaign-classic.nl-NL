---
product: campaign
title: Een profiel bewerken
description: Een profiel bewerken
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: 0f3a5582-5c90-4393-bee8-d9e2f07e5982
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 5%

---

# Een profiel bewerken{#editing-a-profile}

![](../../assets/common.svg)

Klik op de naam van een profiel in de lijst met profielen om informatie over een profiel weer te geven.

De profieldetails komen omhoog in een nieuw lusje.

![](assets/s_user_recipient_edit.png)

De gegevens over profielen worden gegroepeerd in tabbladen.

De tabbladen en hun inhoud zijn afhankelijk van uw configuratie en geïnstalleerde pakketten.

>[!CAUTION]
>
>Het XML-schema en het formulier dat betrekking heeft op de velden in de tabel met profielen, zijn toegankelijk via het **[!UICONTROL Administration > Configuration > Data schemas]** knooppunt van de boomstructuur Adobe Campaign. Alleen deskundige gebruikers kunnen wijzigingen aanbrengen in deze schema&#39;s.
>
>Zie voor meer informatie [deze pagina](../../configuration/using/about-schema-edition.md).

## Tabblad Algemeen {#general-tab}

Dit scherm bevat alle algemene gegevens over het geselecteerde profiel. Het bevat met name de achternaam, voornaam, e-mailadres, e-mailontvangstnotatie, enz. Het ziet er zo uit:

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>Wanneer de **[!UICONTROL No longer contact (by any channel)]** is geselecteerd, betekent dit dat het profiel op lijst van gewezen personen is, d.w.z. dat het profiel de wens heeft geuit om niet te worden gecontacteerd (bijvoorbeeld door op een koppeling voor niet-abonnementen in een nieuwsbrief te klikken). Deze zullen niet meer het doelwit zijn van leveringen op welke kanalen dan ook (e-mail, direct mail, enz.). Raadpleeg [deze pagina](../../delivery/using/understanding-quarantine-management.md) voor meer informatie.

## Tabblad Contactgegevens {#contact-information-tab}

Dit scherm bevat het directe-mailadres van het geselecteerde profiel. Het ziet er zo uit:

![](assets/s_ncs_user_profile_details_tab.png)

Dit scherm toont de kwaliteitsindex van het adres, evenals hoeveel fouten het adres bevat. Deze informatie wordt gebruikt direct door de postdrager die op het aantal fouten wordt gebaseerd die tijdens vorige leveringen worden gevonden, en is niet manueel wijzigbaar.

## Ander tabblad {#other-tab}

Dit scherm bevat door de gebruiker gedefinieerde velden die op basis van vereisten kunnen worden aangepast. U kunt ook de namen van de velden wijzigen en de indeling ervan definiëren via **[!UICONTROL Field properties...]**, zoals hieronder weergegeven:

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>Voor meer informatie over veldeigenschappen en bij het toevoegen van gebieden, verwijs naar [deze pagina](../../configuration/using/new-field-wizard.md).

## Tabblad Lijsten {#lists-tab}

In dit scherm worden de groep(en) weergegeven waartoe het geselecteerde profiel behoort. Klikken **[!UICONTROL Add]** om het profiel in te schrijven op een lijst. Klikken **[!UICONTROL Detail]** om de beschrijving en de lijst met profielen in de geselecteerde lijst weer te geven.

![](assets/s_ncs_user_profile_groups_tab_details.png)

Raadpleeg voor meer informatie hierover [Lijsten maken en beheren](../../platform/using/creating-and-managing-lists.md).

## Tabblad Abonnementen {#subscriptions-tab}

Dit scherm bevat de informatiediensten waarop het profiel heeft geabonneerd.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

De **[!UICONTROL Detail]** geeft de eigenschappen van het geselecteerde abonnement weer. De **[!UICONTROL Add]** wordt gebruikt om handmatig een nieuw abonnement toe te voegen.

Raadpleeg [deze pagina](../../delivery/using/managing-subscriptions.md) voor meer informatie.

## Tabblad Aflevering {#deliveries-tab}

In dit scherm worden de leveringslogboeken voor het geselecteerde profiel weergegeven. U kunt de labels, datums en status van de aan het profiel geadresseerde leveringsacties ook via alle kanalen weergeven.

![](assets/s_ncs_user_profile_delivery_tab.png)

## Tabblad Tekstspatiëring {#tracking-tab}

In dit scherm kunt u de trackinglogboeken voor het geselecteerde profiel weergeven. Deze informatie wordt gebruikt om profielgedrag na leveringen te volgen.

![](assets/s_ncs_user_profile_tracking_tab.png)

Dit tabblad geeft het cumulatieve totaal weer van alle URL&#39;s die in leveringen worden bijgehouden.

De lijst is configureerbaar, en bevat gewoonlijk: klikte URL, datum en tijd van klik, en het document dat URL bevatte.

>[!NOTE]
>
>Raadpleeg voor meer informatie over trackingfuncties [deze pagina](../../delivery/using/delivery-dashboard.md).
