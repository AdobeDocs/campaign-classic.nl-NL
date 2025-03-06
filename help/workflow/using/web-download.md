---
product: campaign
title: Webdownload
description: Meer informatie over de activiteiten van de webdownloadworkflow
feature: Workflows
hide: true
hidefromtoc: true
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 1%

---

# Webdownload{#web-download}



De **download van het Web** activiteit lanceert het downloaden van een dossier op expliciete URL, een externe rekening, of een instantie van Adobe Campaign. Het HTTP-protocol wordt gebruikt. Dit kan een GET- of POST-download zijn.

## Properties {#properties}

1. **Selecterend het dossier van het Web**

   Als u het te downloaden bestand wilt opgeven, voert u de URL van het bestand in, gebruikt u de externe HTTP-account waar het bestand is opgeslagen of laadt u het bestand via een Adobe Campaign-instantie. De beschikbare parameters worden hieronder beschreven:

   * Als u de URL rechtstreeks wilt invoeren van het bestand dat u wilt downloaden, selecteert u de optie **[!UICONTROL Explicit URL]** en geeft u de URL op in het desbetreffende veld. Deze URL kan worden samengesteld met variabele gegevens.

     ![](assets/download_web_edit.png)

   * Als u een **[!UICONTROL External account]** wilt gebruiken, selecteert u de account in de vervolgkeuzelijst en geeft u het bestand op dat u wilt downloaden.

     Externe accounts worden geconfigureerd via het knooppunt **[!UICONTROL Administration > Platform > External accounts]** van de Adobe Campaign-structuur. De accountparameters kunnen worden bewerkt met het pictogram **[!UICONTROL Edit link]** .

     ![](assets/download_web_edit_external.png)

   * Selecteer de optie **[!UICONTROL Adobe Campaign Instance]** als u het bestand wilt downloaden van de Adobe Campaign-instantie.

     ![](assets/download_web_edit_instance.png)

1. **historization van het Dossier**

   Met de koppeling **[!UICONTROL File historization settings...]** kunt u de opslagmap van het bestand en de purgeerfrequentie van deze map opgeven.

   ![](assets/download_web_edit_hist.png)

   De volgende opties zijn beschikbaar:

   * **[!UICONTROL Use a default storage directory]**: het bestand wordt altijd verplaatst voordat het wordt verwerkt. Als deze optie wordt gecontroleerd, wordt het dossier bewogen in de standaardopslagfolder (de **vars** folder van de de installatiemap van Adobe Campaign). Als u een opslagmap wilt opgeven, schakelt u het selectievakje uit en voert u het pad in het veld **[!UICONTROL Storage directory]** in
   * **[!UICONTROL Number of files]** : voer het maximumaantal bestanden in dat in de opslagmap moet worden bewaard.
   * **[!UICONTROL Maximum size (in Mb)]** : voer de maximale capaciteit van de opslagmap in (in megabytes).

   Elk bestand wordt 24 uur bewaard voordat het aan de vastgestelde zuiveringsregels wordt onderworpen. Het leegmaken vindt plaats vlak voor het begin van de activiteit en houdt daarom geen rekening met het werkstroombestand dat wordt uitgevoerd.

   Bestanden worden verwijderd op basis van hun leeftijd (oudste naar nieuwste). De oudste bestanden worden gewist totdat beide regels voor leegmaken zijn geverifieerd. Daarom als een 100 dossiergrens wordt bepaald, betekent dit dat de opslagfolder altijd de 100 nieuwste dossiers vóór de aanvang van het werkschema zal bevatten, evenals die die die in het werkschema worden verwerkt dat lopend is.

   Als u niet langer een limiet voor de opties **[!UICONTROL Number of files]** en **[!UICONTROL Maximum size (in Mb)]** wilt instellen, voert u 0 in als een waarde.

1. **Geavanceerde parameters**

   Met de koppeling **[!UICONTROL Advanced parameters...]** kunt u de hieronder weergegeven aanvullende opties opgeven:

   * **[!UICONTROL Follow redirections]**: met Bestandsomleiding kunt u overschrijvingen gebruiken om de invoer of uitvoer van gegevens naar een ander type apparaat te sturen.
   * **[!UICONTROL Add the HTTP headers to the file]**: In sommige gevallen kunt u extra HTTP-headers aan een bestand toevoegen. Meestal, zullen deze kopballen worden gebruikt om extra informatie voor het oplossen van problemendoeleinden, voor [ het Delen van het Middel van de Cross-Origin (CORS) ](https://developer.mozilla.org/docs/Web/HTTP/CORS) te verstrekken, of specifieke caching richtlijnen te plaatsen.
   * **[!UICONTROL Ignore the HTTP return code]**: HTTP-retourcodes, ook wel HTTP-statuscodes genoemd, geven het resultaat van een HTTP-aanvraag aan.

   ![](assets/download_web_edit_advanced.png)

   De **[!UICONTROL Process errors]** optie is gedetailleerd in [ Verwerkingsfouten ](monitoring-workflow-execution.md#processing-errors).

## Uitvoerparameters {#output-parameters}

* bestandsnaam: volledige naam van het gedownloade bestand.
