---
title: Een profiel bewerken
seo-title: Een profiel bewerken
description: Een profiel bewerken
seo-description: null
page-status-flag: never-activated
uuid: ad3cd54e-b22f-4fae-8d2a-3e0d3e45fffb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 93dd29e8-cf0a-4010-a3cc-f68c52c0d9ef
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Een profiel bewerken{#editing-a-profile}

Klik op de naam van een profiel in de lijst met profielen om informatie over een profiel weer te geven.

De profieldetails komen omhoog in een nieuw lusje.

![](assets/s_user_recipient_edit.png)

De gegevens over profielen worden gegroepeerd in tabbladen.

De tabbladen en hun inhoud zijn afhankelijk van uw configuratie en geïnstalleerde pakketten.

>[!CAUTION]
>
>Het XML-schema en het formulier dat betrekking heeft op de velden in de tabel met profielen, zijn toegankelijk via het **[!UICONTROL Administration > Configuration > Data schemas]** knooppunt van de Adobe Campagne-structuur. Alleen deskundige gebruikers kunnen wijzigingen aanbrengen in deze schema&#39;s.
>
>Raadpleeg [deze pagina](../../configuration/using/about-schema-edition.md)voor meer informatie.

## Tabblad Algemeen {#general-tab}

Dit scherm bevat alle algemene gegevens over het geselecteerde profiel. Het bevat met name de achternaam, voornaam, e-mailadres, e-mailontvangstnotatie, enz. Het ziet er zo uit:

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>Wanneer de **[!UICONTROL No longer contact (by any channel)]** optie is geselecteerd, betekent dit dat het profiel op de zwarte lijst staat, d.w.z. dat in het profiel de wens is geuit dat geen contact wordt opgenomen (bijvoorbeeld door in een nieuwsbrief op een koppeling zonder abonnement te klikken). Deze zullen niet meer het doelwit zijn van leveringen op welke kanalen dan ook (e-mail, direct mail, enz.). Raadpleeg [deze pagina](../../delivery/using/understanding-quarantine-management.md)voor meer informatie.

## Tabblad Contactgegevens {#contact-information-tab}

Dit scherm bevat het directe-mailadres van het geselecteerde profiel. Het ziet er zo uit:

![](assets/s_ncs_user_profile_details_tab.png)

Dit scherm toont de kwaliteitsindex van het adres, evenals hoeveel fouten het adres bevat. Deze informatie wordt gebruikt direct door de postdrager die op het aantal fouten wordt gebaseerd die tijdens vorige leveringen worden gevonden, en is niet manueel wijzigbaar.

## Ander tabblad {#other-tab}

Dit scherm bevat door de gebruiker gedefinieerde velden die op basis van vereisten kunnen worden aangepast. U kunt ook de namen van de velden wijzigen en de indeling van de velden definiëren, zoals hieronder **[!UICONTROL Field properties...]** wordt weergegeven:

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>Raadpleeg [deze pagina](../../configuration/using/new-field-wizard.md)voor meer informatie over veldeigenschappen en over het toevoegen van velden.

## Tabblad Lijsten {#lists-tab}

In dit scherm worden de groep(en) weergegeven waartoe het geselecteerde profiel behoort. Klik **[!UICONTROL Add]** om het profiel in te schrijven op een lijst. Klik **[!UICONTROL Detail]** om de beschrijving en de lijst met profielen in de geselecteerde lijst weer te geven.

![](assets/s_ncs_user_profile_groups_tab_details.png)

Raadpleeg Lijsten [](../../platform/using/creating-and-managing-lists.md)maken en beheren voor meer informatie hierover.

## Tabblad Abonnementen {#subscriptions-tab}

Dit scherm bevat de informatiediensten waarop het profiel heeft geabonneerd.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

De **[!UICONTROL Detail]** knop geeft de eigenschappen van het geselecteerde abonnement weer. Met de **[!UICONTROL Add]** knop kunt u handmatig een nieuw abonnement toevoegen.

Raadpleeg [deze pagina](../../delivery/using/managing-subscriptions.md)voor meer informatie.

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
>Raadpleeg [deze pagina](../../delivery/using/monitoring-a-delivery.md)voor meer informatie over trackingfunctionaliteit.

