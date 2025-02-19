---
product: campaign
title: Een campagne bijhouden
description: Leer hoe u een campagne kunt bijhouden met campagne Distributed Marketing
feature: Distributed Marketing
hide: true
hidefromtoc: true
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
source-git-commit: 36fe54cf6d4d762d96205bd637311a426c741427
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 1%

---

# Een campagne bijhouden{#tracking-a-campaign}



De centrale entiteitexploitanten kunnen campagneorden in de lijst van campagnepakketten volgen.

Hierdoor kunnen ze:

* [ de pakketten van de Filter ](#filter-packages),
* [ geef pakketten ](#edit-packages) uit,
* [ annuleert een pakket ](#cancel-a-package),
* [ herinitialiseer een pakket ](#reinitializing-a-package).

## Filterpakketten {#filter-packages}

Vanuit het tabblad **[!UICONTROL Campaigns]** kunt u de lijst weergeven van **[!UICONTROL Campaign packages]** die alle bestaande campagnes voor gedistribueerde marketing groepeert. U kunt deze lijst zo filteren dat alleen campagnes worden weergegeven die worden gepubliceerd, laat, in afwachting van goedkeuring, enzovoort. Klik hiertoe op de koppelingen in de bovenste sectie van deze weergave of gebruik de koppeling **[!UICONTROL Filter list]** en selecteer de status van het campagnepakket die u wilt weergeven.

![](assets/mkg_dist_catalog_filter.png)

## Pakketten bewerken {#edit-packages}

Op de pagina **[!UICONTROL Campaign packages]** kunt u de samenvatting van elk pakket weergeven.

Deze samenvatting bevat de volgende informatie: label, type campagne en de naam van de campagne waaruit deze is gemaakt, en de map.

Klik op de pakketnaam om deze te bewerken. U kunt ook bestellingen bekijken door de lokale entiteiten en door hun status.

Deze informatie wordt ook aangeboden in de **[!UICONTROL Campaign orders]** -weergave waarin alle bestellingen worden vermeld.

![](assets/mkg_dist_catalog_op_command_details.png)

De centrale operator kan de volgorde bewerken. Er zijn twee manieren om dit te doen:

1. De exploitant kan de ordenaam klikken om het uit te geven: dit toont de orddetails.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   Op het tabblad **[!UICONTROL Edit > General]** kunt u informatie weergeven die door de lokale entiteit is ingevoerd toen deze de campagne heeft besteld.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. De exploitant kan het campagnepakketetiket klikken om het uit te geven en bepaalde montages te veranderen.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Een pakket annuleren {#cancel-a-package}

De centrale entiteit kan een campagnepakket op elk ogenblik annuleren.

Klik op **[!UICONTROL Cancel]** in het campagnepakket **[!UICONTROL Dashboard]** .

![](assets/mkg_dist_cancel_op_from_dashboard.png)

In het veld **[!UICONTROL Comment]** kunt u de annulering uitvullen.

Voor **lokale campagnes**, verwijdert het annuleren van een pakket het uit de lijst van beschikbare marketing campagnes.

Voor **samenwerkings campagnes**, die een pakket annuleert brengt talrijke acties teweeg:

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
1. Klik op de koppeling **[!UICONTROL Reinitialize the package to reuse it]** en klik op **[!UICONTROL OK]** .

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Klik op de knop **[!UICONTROL Save]** om pakketherinitialisatie goed te keuren.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. De pakketstatus verandert in **[!UICONTROL Being edited]** . Wijzig, keur en publiceer het opnieuw om het in de lijst van campagnepakket te herstellen goed te keuren.

>[!NOTE]
>
>U kunt geannuleerde campagnepakketten ook opnieuw initialiseren.
