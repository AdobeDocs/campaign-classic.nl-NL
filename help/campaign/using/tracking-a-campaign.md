---
solution: Campaign Classic
product: campaign
title: Een campagne opvolgen
description: Een campagne opvolgen
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---


# Een campagne opvolgen{#tracking-a-campaign}

De centrale entiteitexploitanten kunnen campagneorden in de lijst van campagnepakketten volgen.

Hierdoor kunnen ze:

* [Filterpakketten](#filter-packages),
* [Pakketten](#edit-packages) bewerken
* [Een pakket](#cancel-a-package) annuleren,
* [Een pakket](#reinitializing-a-package) opnieuw initialiseren.

## Filterpakketten {#filter-packages}

Van **[!UICONTROL Campaigns universe]**, kunt u de lijst van **[!UICONTROL Campaign packages]** tonen die alle bestaande Verdeelde campagnes van de Marketing hergroepeert. U kunt deze lijst zo filteren dat alleen campagnes worden weergegeven die worden gepubliceerd, laat, in afwachting van goedkeuring, enzovoort. Om dit te doen, klik de verbindingen in de hogere sectie van deze mening, of gebruik **[!UICONTROL Filter list]** verbinding en selecteer de status van het campagnepakket aan vertoning.

![](assets/mkg_dist_catalog_filter.png)

## Pakketten {#edit-packages} bewerken

Op de pagina **[!UICONTROL Campaign packages]** kunt u de samenvatting van elk pakket weergeven.

Deze samenvatting bevat de volgende informatie: label, type campagne, alsmede de naam van de campagne waaruit deze is gemaakt en de map.

Klik op de pakketnaam om deze te bewerken. U kunt ook bestellingen bekijken door de lokale entiteiten en door hun status.

Deze informatie wordt ook aangeboden in de weergave **[!UICONTROL Campaign orders]** waarin alle bestellingen worden vermeld.

![](assets/mkg_dist_catalog_op_command_details.png)

De centrale operator kan de volgorde bewerken. Er zijn twee manieren om dit te doen:

1. De exploitant kan de ordenaam klikken om het uit te geven: hier worden de gegevens van de bestelling weergegeven .

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   Op het tabblad **[!UICONTROL Edit > General]** kunt u informatie weergeven die door de lokale entiteit is ingevoerd toen deze de campagne heeft besteld.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. De exploitant kan het campagnepakketetiket klikken om het uit te geven en bepaalde montages te veranderen.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Een pakket {#cancel-a-package} annuleren

De centrale entiteit kan een campagnepakket op elk ogenblik annuleren.

Klik **[!UICONTROL Cancel]** in het campagnepakket **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

In het veld **[!UICONTROL Comment]** kunt u de annulering uitvullen.

Als u een pakket annuleert voor **lokale campagnes**, wordt dit verwijderd uit de lijst met beschikbare marketingcampagnes.

Voor **samenwerkingscampagnes** leidt het annuleren van een pakket tot talrijke acties:

1. Alle bestellingen met betrekking tot dit pakket worden geannuleerd.

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. De referentiecampagne wordt geannuleerd en alle actieve processen (workflows, leveringen) worden gestopt,

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. Alle betrokken lokale entiteiten ontvangen een kennisgeving.

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

Geannuleerde pakketten kunnen desgewenst nog steeds door de centrale entiteit worden benaderd en opnieuw worden geïnitialiseerd (zie hieronder). Ze zullen pas weer aan lokale entiteiten worden aangeboden nadat ze zijn goedgekeurd en van start zijn gegaan. Het herinitialisatieproces van het pakket wordt hieronder weergegeven.

## Een pakket opnieuw initialiseren {#reinitializing-a-package}

Campagnepakketten die al zijn gepubliceerd, kunnen opnieuw worden geïnitialiseerd, gewijzigd en ter beschikking van lokale entiteiten worden gesteld.

1. Selecteer het betreffende pakket.
1. Klik op de koppeling **[!UICONTROL Reinitialize the package to reuse it]** en klik **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Klik op de knop **[!UICONTROL Save]** om pakketherinitialisatie goed te keuren.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. De pakketstatus verandert in **[!UICONTROL Being edited]**. Wijzig, keur en publiceer het opnieuw om het in de lijst van campagnepakket te herstellen goed te keuren.

>[!NOTE]
>
>U kunt geannuleerde campagnepakketten ook opnieuw initialiseren.

