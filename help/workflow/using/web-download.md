---
solution: Campaign Classic
product: campaign
title: Webdownload
description: Meer informatie over de activiteiten van de webdownloadworkflow
audience: workflow
content-type: reference
topic-tags: event-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 1%

---


# Webdownload{#web-download}

Met de activiteit **Webdownload** wordt het downloaden van een bestand op een expliciete URL, een externe account of een Adobe Campaign-instantie gestart. Het HTTP-protocol wordt gebruikt. Dit kan een download van de GET of van de POST zijn.

## Properties {#properties}

1. **Het webbestand selecteren**

   Als u het te downloaden bestand wilt opgeven, voert u de URL van het bestand in, gebruikt u de externe HTTP-account waar het bestand is opgeslagen of laadt u het bestand via een Adobe Campaign-instantie. De beschikbare parameters worden hieronder beschreven:

   * Als u de URL van het te downloaden bestand rechtstreeks wilt invoeren, selecteert u de optie **[!UICONTROL Explicit URL]** en geeft u de URL op in het desbetreffende veld. Deze URL kan worden samengesteld met variabele gegevens.

      ![](assets/download_web_edit.png)

   * Als u een **[!UICONTROL External account]** wilt gebruiken, selecteert u de account in de vervolgkeuzelijst en geeft u het bestand op dat u wilt downloaden.

      Externe accounts worden geconfigureerd via het knooppunt **[!UICONTROL Administration > Platform > External accounts]** van de Adobe Campaign-structuur. De accountparameters kunnen worden bewerkt met het pictogram **[!UICONTROL Edit link]**.

      ![](assets/download_web_edit_external.png)

   * Als u het bestand wilt downloaden van de Adobe Campaign-instantie, selecteert u de optie **[!UICONTROL Adobe Campaign Instance]**.

      ![](assets/download_web_edit_instance.png)

1. **Bestandshistorie**

   Met de koppeling **[!UICONTROL File historization settings...]** kunt u de opslagmap van het bestand en de zuiveringsfrequentie van deze map opgeven.

   ![](assets/download_web_edit_hist.png)

   De volgende opties zijn beschikbaar:

   * **[!UICONTROL Use a default storage directory]**: het bestand wordt altijd verplaatst voordat het wordt verwerkt. Als deze optie is ingeschakeld, wordt het bestand naar de standaardopslagmap verplaatst (de map **vars** van de installatiemap van Adobe Campaign). Als u een opslagmap wilt opgeven, schakelt u het selectievakje uit en voert u het pad in het veld **[!UICONTROL Storage directory]** in
   * **[!UICONTROL Number of files]**: Voer het maximumaantal bestanden in dat in de opslagmap moet worden bewaard.
   * **[!UICONTROL Maximum size (in Mb)]**: Voer de maximale capaciteit van de opslagdirectory in (in megabytes).

   Elk bestand wordt 24 uur bewaard voordat het aan de vastgestelde zuiveringsregels wordt onderworpen. Het leegmaken vindt plaats vlak voor het begin van de activiteit en houdt daarom geen rekening met het werkstroombestand dat wordt uitgevoerd.

   Bestanden worden verwijderd op basis van hun leeftijd (oudste naar nieuwste). De oudste bestanden worden gewist totdat beide regels voor leegmaken zijn geverifieerd. Daarom als een 100 dossiergrens wordt bepaald, betekent dit dat de opslagfolder altijd de 100 nieuwste dossiers vóór de aanvang van het werkschema zal bevatten, evenals die die die in het werkschema worden verwerkt dat lopend is.

   Als u niet meer een grens voor **[!UICONTROL Number of files]** en **[!UICONTROL Maximum size (in Mb)]** opties wilt plaatsen, ga 0 als waarde in.

1. **Geavanceerde parameters**

   Met de koppeling **[!UICONTROL Advanced parameters...]** kunt u de hieronder weergegeven aanvullende opties opgeven:

   ![](assets/download_web_edit_advanced.png)

   De optie **[!UICONTROL Process errors]** wordt beschreven in [Fouten verwerken](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Uitvoerparameters {#output-parameters}

* bestandsnaam: Volledige naam van het gedownloade bestand.
