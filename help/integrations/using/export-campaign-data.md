---
product: campaign
title: Gegevens exporteren van Campaign naar Adobe Experience Platform
description: Leer hoe u gegevens exporteert van Campaign Classic naar Adobe Experience Platform.
audience: integrations
content-type: reference
exl-id: 8d1404c5-030b-47fe-a4c3-e72f15f09bbb
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 3%

---

# Gegevens exporteren van Campaign naar Adobe Experience Platform {#sources}

![](../../assets/common.svg)

Als u Campaign Classic-gegevens wilt exporteren naar het RTCDP-Platform (Adobe Real-Time Customer Data ), moet u eerst een workflow in Campaign Classic maken om de gegevens die u wilt delen naar de opslaglocatie van uw S3- of Azure-blok te exporteren.

Nadat de workflow is geconfigureerd en de gegevens naar de opslaglocatie zijn verzonden, moet u de opslaglocatie van uw S3- of Azure-blok aansluiten als een **Source** in het Platform Adobe Experience.

>[!NOTE]
>
>Houd er rekening mee dat we alleen het exporteren van door campagne gegenereerde gegevens aanbevelen (bijvoorbeeld verzenden, openen, klikken enz.) naar Adobe Experience Platform. Gegevens die van een bron van derden (zoals uw CRM) worden ontvangen, moeten rechtstreeks in Adobe Experience Platform worden geïmporteerd.

## Een exportworkflow maken in Campaign Classic

Als u gegevens van Campaign Classic naar uw opslaglocatie van S3 of Azure Blob wilt exporteren, moet u een workflow maken om de gegevens die u wilt exporteren als doel in te stellen en deze naar uw opslaglocatie te verzenden.

Hiervoor kunt u toevoegen en configureren:

* Een **[!UICONTROL Data extraction (file)]** activiteit om de gerichte gegevens in een Csv- dossier te halen. Raadpleeg [deze sectie](../../workflow/using/extraction--file-.md) voor meer informatie over het configureren van deze activiteit.

   ![](assets/rtcdp-extract-file.png)

* Een **[!UICONTROL File transfer]** activiteit om het CSV dossier naar uw opslagplaats over te brengen. Raadpleeg [deze sectie](../../workflow/using/file-transfer.md) voor meer informatie over het configureren van deze activiteit.

   ![](assets/rtcdp-file-transfer.png)

In de onderstaande workflow worden logbestanden regelmatig uitgepakt in een CSV-bestand en wordt het bestand vervolgens overgebracht naar een opslaglocatie.

![](assets/aep-export.png)

## De opslaglocatie aansluiten als bron

De belangrijkste stappen om uw opslagplaats van S3 of van de Azure blob als **Bron** in het Platform van de Ervaring van Adobe aan te sluiten zijn hieronder vermeld. Gedetailleerde informatie over elk van deze stappen is beschikbaar in de [documentatie van de bronschakelaars](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html).

1. Maak in het menu van het Adobe Experience-platform een verbinding met uw opslaglocatie:**[!UICONTROL Sources]**

   * [Een Amazon S3-bronverbinding maken](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/s3.html)
   * [Azure Blob-connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/cloud-storage/blob.html)

   >[!NOTE]
   >
   >De opslaglocatie kan Amazon S3, SFTP met wachtwoord, SFTP met SSH-sleutel of Azure Blob-verbindingen zijn. De voorkeursmethode voor het verzenden van gegevens naar Adobe Campaign is Amazon S3 of Azure Blob:

   ![](assets/rtcdp-connector.png)

1. Configureer een gegevensstroom voor een batchverbinding voor cloudopslag. Een dataflow is een geplande taak die gegevens van de opslagplaats aan een dataset van Adobe Experience Platform terugwint en opneemt. Met deze stappen kunt u de gegevensinvoer vanaf uw opslaglocatie configureren, inclusief gegevensselectie en de toewijzing van de CSV-velden aan een XDM-schema.

   Gedetailleerde informatie is beschikbaar in [deze pagina](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html).

   ![](assets/rtcdp-map-xdm.png)

1. Nadat de Bron is gevormd, zal Adobe Experience Platform het dossier van de opslagplaats invoeren die u verstrekte.

   Deze bewerking kan volgens uw behoeften worden gepland. We raden u aan de exportbewerking tot zes keer per dag uit te voeren, afhankelijk van de belasting die al op het exemplaar aanwezig is.
