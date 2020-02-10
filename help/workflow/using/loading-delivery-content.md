---
title: Inhoud van levering laden
seo-title: Inhoud van levering laden
description: Inhoud van levering laden
seo-description: null
page-status-flag: never-activated
uuid: f2004fb0-9beb-463f-9903-10f291b3663e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 3667da3d-4940-4128-8878-f1ee67216f56
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Inhoud van levering laden{#loading-delivery-content}

Als uw leveringsinhoud beschikbaar is in een HTML-bestand dat zich op Amazon S3-, FTP- of SFTP-servers bevindt, kunt u deze inhoud eenvoudig laden in Adobe Campagne-leveringen.

Dit doet u als volgt:

1. Als u nog geen verbinding hebt gedefinieerd tussen de Adobe-campagne en de (S)FTP-server die als host fungeert voor de inhoudsbestanden, maakt u een nieuwe externe account van het type S3, FTP of SFTP in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. Geef in deze externe account het adres en de referenties op waarmee de verbinding met de S3- of (S)FTP-server tot stand wordt gebracht.

   Hier is een voorbeeld van een externe S3-account:

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. Maak een nieuwe workflow, bijvoorbeeld via **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Voeg een **[!UICONTROL File transfer]** activiteit in uw werkschema toe en vorm het door te specificeren

   * De externe account die moet worden gebruikt om verbinding te maken met de S3- of (S)FTP-server.
   * Het pad van het bestand op de S3- of (S)FTP-server.
   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. Voeg een **[!UICONTROL Delivery]** activiteit toe en verbind het met de uitgaande overgang van de **[!UICONTROL File transfer]** activiteit. Configureer dit als volgt:

   * Aflevering: Afhankelijk van uw behoeften, kan het een specifieke levering zijn die reeds in het systeem, of een nieuwe levering wordt gecreeerd die op een bestaand malplaatje wordt gebaseerd.
   * Ontvangers: In dit voorbeeld wordt ervan uitgegaan dat het doel is opgegeven in de levering zelf.
   * Inhoud: Zelfs als de inhoud wordt geïmporteerd in de vorige activiteit, selecteert u **[!UICONTROL Specified in the delivery]**. Aangezien de inhoud rechtstreeks wordt geïmporteerd uit een bestand op een externe server, heeft de inhoud geen id wanneer deze wordt verwerkt door de workflow en kan niet worden geïdentificeerd als afkomstig van de binnenkomende gebeurtenis.
   * Uit te voeren handeling: Selecteer deze optie **[!UICONTROL Save]** om de levering op te slaan en deze via **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** te openen zodra de workflow wordt uitgevoerd.
   ![](assets/delivery_loadcontent_activityexample.png)

1. Voeg op het **[!UICONTROL Script]** tabblad van de **[!UICONTROL Delivery]** activiteit de volgende opdracht toe om de inhoud van het geïmporteerde bestand in de levering te laden:

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. Sla de workflow op en voer deze uit. Een nieuwe levering met de geladen inhoud wordt gecreeerd onder **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

>[!NOTE]
>
>De beste praktijken en het oplossen van problemen op het servergebruik van SFTP worden gedetailleerd [in deze pagina](../../platform/using/sftp-server-usage.md).

