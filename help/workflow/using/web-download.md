---
title: Webdownload
seo-title: Webdownload
description: Webdownload
seo-description: null
page-status-flag: never-activated
uuid: 44039e9c-0cd8-4d3f-b73f-e01c5343835a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 8590cc75-11c8-450d-90e8-56744e12ac70
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---


# Webdownload{#web-download}

Met de **webdownloadactiviteit** wordt het downloaden van een bestand gestart via een expliciete URL, een externe account of een Adobe Campagne-instantie. Het HTTP-protocol wordt gebruikt. Dit kan een GET- of POST-download zijn.

## Eigenschappen {#properties}

1. **Het webbestand selecteren**

   Als u het te downloaden bestand wilt opgeven, voert u de URL van het bestand in, gebruikt u de externe HTTP-account waar het bestand is opgeslagen of laadt u het bestand via een Adobe Campagne-instantie. De beschikbare parameters worden hieronder beschreven:

   * Als u de URL rechtstreeks wilt invoeren van het bestand dat u wilt downloaden, selecteert u de **[!UICONTROL Explicit URL]** optie en geeft u de URL op in het desbetreffende veld. Deze URL kan worden samengesteld met variabele gegevens.

      ![](assets/download_web_edit.png)

   * Als u een account wilt gebruiken, selecteert u de account in de vervolgkeuzelijst en geeft u het bestand op dat u wilt downloaden. **[!UICONTROL External account]**

      Externe accounts worden geconfigureerd via het **[!UICONTROL Administration > Platform > External accounts]** knooppunt van de Adobe Campaign-structuur. U kunt de accountparameters bewerken via het **[!UICONTROL Edit link]** pictogram.

      ![](assets/download_web_edit_external.png)

   * Selecteer de **[!UICONTROL Adobe Campaign Instance]** optie om het bestand te downloaden van de Adobe Campagne-instantie.

      ![](assets/download_web_edit_instance.png)

1. **Bestandshistorie**

   Met de **[!UICONTROL File historization settings...]** koppeling kunt u de opslagmap van het bestand en de zuiveringsfrequentie van deze map opgeven.

   ![](assets/download_web_edit_hist.png)

   De volgende opties zijn beschikbaar:

   * **[!UICONTROL Use a default storage directory]**: het bestand wordt altijd verplaatst voordat het wordt verwerkt. Als deze optie is ingeschakeld, wordt het bestand naar de standaardopslagmap verplaatst (de map **vars** van de installatiemap van Adobe Campagne). Als u een opslagmap wilt opgeven, schakelt u het selectievakje uit en voert u het pad in het **[!UICONTROL Storage directory]** veld in
   * **[!UICONTROL Number of files]**: Voer het maximumaantal bestanden in dat in de opslagmap moet worden bewaard.
   * **[!UICONTROL Maximum size (in Mb)]**: Voer de maximale capaciteit van de opslagdirectory in (in megabytes).
   Elk bestand wordt 24 uur bewaard voordat het aan de vastgestelde zuiveringsregels wordt onderworpen. Het leegmaken vindt plaats vlak voor het begin van de activiteit en houdt daarom geen rekening met het werkstroombestand dat wordt uitgevoerd.

   Bestanden worden verwijderd op basis van hun leeftijd (oudste naar nieuwste). De oudste bestanden worden gewist totdat beide regels voor leegmaken zijn geverifieerd. Daarom als een 100 dossiergrens wordt bepaald, betekent dit dat de opslagfolder altijd de 100 nieuwste dossiers vóór de aanvang van het werkschema zal bevatten, evenals die die die in het werkschema worden verwerkt dat lopend is.

   Als u niet langer een limiet voor de opties **[!UICONTROL Number of files]** **[!UICONTROL Maximum size (in Mb)]** en opties wilt instellen, voert u 0 in als een waarde.

1. **Geavanceerde parameters**

   Met de **[!UICONTROL Advanced parameters...]** koppeling kunt u de hieronder weergegeven aanvullende opties opgeven:

   ![](assets/download_web_edit_advanced.png)

   De **[!UICONTROL Process errors]** optie wordt gedetailleerd weergegeven in [verwerkingsfouten](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Uitvoerparameters {#output-parameters}

* bestandsnaam: Volledige naam van het gedownloade bestand.
