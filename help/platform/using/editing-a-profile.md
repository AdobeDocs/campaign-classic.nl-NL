---
product: campaign
title: Een profiel bewerken
description: Een profiel bewerken
feature: Profiles
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: 0f3a5582-5c90-4393-bee8-d9e2f07e5982
source-git-commit: ec774cc10a69a694b3c2bf5a6f662afd12a1435a
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 4%

---

# Een profiel bewerken{#editing-a-profile}



Klik op de naam van een profiel in de lijst met profielen om informatie over een profiel weer te geven.

De profieldetails komen omhoog in een nieuw lusje.

![](assets/s_user_recipient_edit.png)

De gegevens over profielen worden gegroepeerd in tabbladen.

De tabbladen en hun inhoud zijn afhankelijk van uw configuratie en geïnstalleerde pakketten.

>[!CAUTION]
>
>Het XML-schema en het formulier dat betrekking heeft op de velden in de tabel met profielen, zijn toegankelijk via het knooppunt **[!UICONTROL Administration > Configuration > Data schemas]** van de Adobe Campaign-structuur. Alleen deskundige gebruikers kunnen wijzigingen aanbrengen in deze schema&#39;s.
>
>Voor verdere informatie, verwijs naar [ deze pagina ](../../configuration/using/about-schema-edition.md).

## Tabblad Algemeen {#general-tab}

Dit scherm bevat alle algemene gegevens over het geselecteerde profiel. Het bevat met name de achternaam, voornaam, e-mailadres, e-mailontvangstnotatie, enz. Het ziet er zo uit:

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>Wanneer de optie **[!UICONTROL No longer contact (by any channel)]** is geselecteerd, betekent dit dat het profiel op lijst van gewezen personen staat, d.w.z. dat het profiel de wens heeft uitgedrukt om niet te worden benaderd (bijvoorbeeld door op een koppeling voor niet-abonnementen in een nieuwsbrief te klikken). Deze zullen niet meer het doelwit zijn van leveringen op een kanaal (e-mail, direct mail, enz.). Raadpleeg [deze pagina](../../delivery/using/understanding-quarantine-management.md) voor meer informatie.

## Tabblad Contactgegevens {#contact-information-tab}

Dit scherm bevat het directe-mailadres van het geselecteerde profiel. Het ziet er zo uit:

![](assets/s_ncs_user_profile_details_tab.png)

Dit scherm toont de kwaliteitsindex van het adres, evenals hoeveel fouten het adres bevat. Deze informatie wordt gebruikt direct door de postdrager die op het aantal fouten wordt gebaseerd die tijdens vorige leveringen worden gevonden, en is niet manueel wijzigbaar.

## Ander tabblad {#other-tab}

Dit scherm bevat door de gebruiker gedefinieerde velden die op basis van vereisten kunnen worden aangepast. U kunt ook de namen van de velden wijzigen en de indeling ervan definiëren via **[!UICONTROL Field properties...]**, zoals hieronder wordt weergegeven:

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>Voor meer op gebiedseigenschappen en bij het toevoegen van gebieden, verwijs naar [ deze pagina ](../../configuration/using/new-field-wizard.md).

## Tabblad Lijsten {#lists-tab}

In dit scherm worden de groep(en) weergegeven waartoe het geselecteerde profiel behoort. Klik op **[!UICONTROL Add]** om het profiel in te schrijven op een lijst. Klik op **[!UICONTROL Detail]** om de beschrijving en de lijst met profielen in de geselecteerde lijst weer te geven.

![](assets/s_ncs_user_profile_groups_tab_details.png)

Voor meer op dit, verwijs naar [ creeer en beheer lijsten ](../../platform/using/creating-and-managing-lists.md).

## Tabblad Abonnementen {#subscriptions-tab}

Dit scherm bevat de informatiediensten waarop het profiel heeft geabonneerd.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

De knop **[!UICONTROL Detail]** geeft de eigenschappen van het geselecteerde abonnement weer. Met de knop **[!UICONTROL Add]** kunt u handmatig een nieuw abonnement toevoegen.

Raadpleeg [deze pagina](../../delivery/using/managing-subscriptions.md) voor meer informatie.

## Tabblad Aflevering {#deliveries-tab}

In dit scherm worden de leveringslogboeken voor het geselecteerde profiel weergegeven. U kunt de labels, datums en status van de aan het profiel geadresseerde leveringsacties ook via alle kanalen weergeven.

![](assets/s_ncs_user_profile_delivery_tab.png)

## Tabblad Tekstspatiëring {#tracking-tab}

In dit scherm kunt u de trackinglogboeken voor het geselecteerde profiel weergeven. Deze informatie wordt gebruikt om profielgedrag na leveringen te volgen.

![](assets/s_ncs_user_profile_tracking_tab.png)

Dit tabblad geeft het cumulatieve totaal weer van alle URL&#39;s die in leveringen worden bijgehouden.

De lijst is configureerbaar en bevat meestal: de URL waarop is geklikt, de datum en tijd waarop is geklikt en het document dat de URL bevat.

>[!NOTE]
>
>Voor meer bij het volgen van functionaliteit, gelieve te verwijzen naar [ deze pagina ](../../delivery/using/delivery-dashboard.md).
