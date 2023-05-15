---
product: campaign
title: Een campagne bijhouden
description: Leer hoe u een campagne kunt bijhouden met campagne Distributed Marketing
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Distributed Marketing
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 1%

---

# Een campagne bijhouden{#tracking-a-campaign}



De centrale entiteitexploitanten kunnen campagneorden in de lijst van campagnepakketten volgen.

Hierdoor kunnen ze:

* [Filterpakketten](#filter-packages),
* [Pakketten bewerken](#edit-packages),
* [Een pakket annuleren](#cancel-a-package),
* [Een pakket opnieuw initialiseren](#reinitializing-a-package).

## Filterpakketten {#filter-packages}

Van de **[!UICONTROL Campaigns]** kunt u de lijst weergeven met **[!UICONTROL Campaign packages]** die alle bestaande Distributed Marketing campagnes groepeert. U kunt deze lijst zo filteren dat alleen campagnes worden weergegeven die worden gepubliceerd, laat, in afwachting van goedkeuring, enzovoort. Om dit te doen, klik de verbindingen in de hogere sectie van deze mening, of gebruik **[!UICONTROL Filter list]** en selecteer de status van het campagnepakket die u wilt weergeven.

![](assets/mkg_dist_catalog_filter.png)

## Pakketten bewerken {#edit-packages}

De **[!UICONTROL Campaign packages]** kunt u de samenvatting van elk pakket weergeven.

Deze samenvatting bevat de volgende informatie: label, type campagne, alsmede de naam van de campagne waaruit deze is gemaakt en de map.

Klik op de pakketnaam om deze te bewerken. U kunt ook bestellingen bekijken door de lokale entiteiten en door hun status.

Deze informatie wordt ook aangeboden in het **[!UICONTROL Campaign orders]** bekijken welke van alle orden een lijst maakt.

![](assets/mkg_dist_catalog_op_command_details.png)

De centrale operator kan de volgorde bewerken. Er zijn twee manieren om dit te doen:

1. De exploitant kan de ordenaam klikken om het uit te geven: hier worden de gegevens van de bestelling weergegeven .

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   De **[!UICONTROL Edit > General]** kunt u informatie bekijken die door de lokale entiteit is ingevoerd toen deze de campagne bestelde.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. De exploitant kan het campagnepakketetiket klikken om het uit te geven en bepaalde montages te veranderen.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Een pakket annuleren {#cancel-a-package}

De centrale entiteit kan een campagnepakket op elk ogenblik annuleren.

Klikken **[!UICONTROL Cancel]** in het campagnepakket **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

De **[!UICONTROL Comment]** kunt u de annulering uitvullen.

Voor **lokale campagnes** Als u een pakket annuleert, wordt dit verwijderd uit de lijst met beschikbare marketingcampagnes.

Voor **samenwerkingscampagnes** Wanneer u een pakket annuleert, worden talloze acties geactiveerd:

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
1. Klik op de knop **[!UICONTROL Reinitialize the package to reuse it]** koppeling en klik op **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Klik op de knop **[!UICONTROL Save]** om pakketherinitialisatie goed te keuren.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. De pakketstatus verandert in **[!UICONTROL Being edited]**. Wijzig, keur en publiceer het opnieuw om het in de lijst van campagnepakket te herstellen goed te keuren.

>[!NOTE]
>
>U kunt geannuleerde campagnepakketten ook opnieuw initialiseren.
