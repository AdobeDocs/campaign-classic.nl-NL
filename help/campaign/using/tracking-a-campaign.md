---
title: Een campagne volgen
seo-title: Een campagne volgen
description: Een campagne volgen
seo-description: null
page-status-flag: never-activated
uuid: 66919c81-b22c-4138-a654-ea53154ba718
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: e1f8958d-f036-4635-be6e-ebdbea6ac116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Een campagne volgen{#tracking-a-campaign}

De centrale entiteitexploitanten kunnen campagneorden in de lijst van campagnepakketten volgen.

Hierdoor kunnen ze:

* [Filterpakketten](#filter-packages),
* [Pakketten](#edit-packages)bewerken
* [Een pakket](#cancel-a-package)annuleren,
* [Een pakket](#reinitializing-a-package)opnieuw initialiseren.

## Filterpakketten {#filter-packages}

Van **[!UICONTROL Campaigns universe]**, kunt u de lijst tonen waarvan **[!UICONTROL Campaign packages]** alle bestaande Verdeelde campagnes van de Marketing hergroepeert. U kunt deze lijst zo filteren dat alleen campagnes worden weergegeven die worden gepubliceerd, laat, in afwachting van goedkeuring, enzovoort. Klik hiertoe op de koppelingen in de bovenste sectie van deze weergave of gebruik de **[!UICONTROL Filter list]** koppeling en selecteer de status van het campagnepakket die u wilt weergeven.

![](assets/mkg_dist_catalog_filter.png)

## Pakketten bewerken {#edit-packages}

Op de **[!UICONTROL Campaign packages]** pagina kunt u de samenvatting van elk pakket weergeven.

Deze samenvatting bevat de volgende informatie: label, type campagne, alsmede de naam van de campagne waaruit deze is gemaakt en de map.

Klik op de pakketnaam om deze te bewerken. U kunt ook bestellingen bekijken door de lokale entiteiten en door hun status.

Deze informatie wordt ook aangeboden in de **[!UICONTROL Campaign orders]** weergave waarin alle bestellingen worden vermeld.

![](assets/mkg_dist_catalog_op_command_details.png)

De centrale operator kan de volgorde bewerken. Er zijn twee manieren om dit te doen:

1. De exploitant kan de ordenaam klikken om het uit te geven: dit toont het ordendetail.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   Op het **[!UICONTROL Edit > General]** tabblad kunt u informatie weergeven die door de lokale entiteit is ingevoerd toen deze de campagne heeft besteld.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. De exploitant kan het campagnepakketetiket klikken om het uit te geven en bepaalde montages te veranderen.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Een pakket annuleren {#cancel-a-package}

De centrale entiteit kan een campagnepakket op elk ogenblik annuleren.

Klik **[!UICONTROL Cancel]** in het campagnepakket **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

In het **[!UICONTROL Comment]** veld kunt u de annulering uitvullen.

Als u een pakket annuleert voor **lokale campagnes**, wordt dit verwijderd uit de lijst met beschikbare marketingcampagnes.

Bij **samenwerkingscampagnes** leidt het annuleren van een pakket tot een groot aantal acties:

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
1. Klik op de **[!UICONTROL Reinitialize the package to reuse it]** koppeling en klik **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Klik op de **[!UICONTROL Save]** knop om pakketherinitialisatie goed te keuren.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. De pakketstatus verandert in **[!UICONTROL Being edited]**. Wijzig, keur en publiceer het opnieuw om het in de lijst van campagnepakket te herstellen goed te keuren.

>[!NOTE]
>
>U kunt geannuleerde campagnepakketten ook opnieuw initialiseren.

