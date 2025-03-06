---
product: campaign
title: Leveringscontent laden
description: Inhoud van levering laden
feature: Workflows
hide: true
hidefromtoc: true
exl-id: a52baffd-402b-4b33-ab72-ac954e4dee85
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 2%

---

# Leveringscontent laden{#loading-delivery-content}



Als uw leveringsinhoud beschikbaar is in een HTML-bestand dat zich op Amazon S3-, FTP- of SFTP-servers bevindt, kunt u deze inhoud gemakkelijk laden in Adobe Campaign-leveringen.

Dit doet u als volgt:

1. Als u nog geen verbinding hebt gedefinieerd tussen Adobe Campaign en de (S)FTP-server die als host fungeert voor de inhoudsbestanden, maakt u een nieuwe externe account van het type S3, FTP of SFTP in **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** . Geef in deze externe account het adres en de referenties op waarmee de verbinding met de S3- of (S)FTP-server tot stand wordt gebracht.

   Hier is een voorbeeld van een externe S3-account:

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. Maak een nieuwe workflow, bijvoorbeeld via **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]** .
1. Voeg een **[!UICONTROL File transfer]** activiteit in uw werkschema toe, en vorm het door te specificeren

   * De externe account die moet worden gebruikt om verbinding te maken met de S3- of (S)FTP-server.
   * Het pad van het bestand op de S3- of (S)FTP-server.

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. Voeg een **[!UICONTROL Delivery]** activiteit toe en verbind het met de uitgaande overgang van de **[!UICONTROL File transfer]** activiteit. Configureer dit als volgt:

   * Levering: Afhankelijk van uw behoeften, kan het een specifieke levering zijn die reeds in het systeem, of een nieuwe levering wordt gecreeerd die op een bestaand malplaatje wordt gebaseerd.
   * Ontvangers: In dit voorbeeld wordt ervan uitgegaan dat het doel is opgegeven in de levering zelf.
   * Inhoud: zelfs als de inhoud in de vorige activiteit wordt geïmporteerd, selecteert u **[!UICONTROL Specified in the delivery]** . Aangezien de inhoud rechtstreeks wordt geïmporteerd uit een bestand op een externe server, heeft de inhoud geen id wanneer deze wordt verwerkt door de workflow en kan niet worden geïdentificeerd als afkomstig van de binnenkomende gebeurtenis.
   * Uit te voeren handeling: selecteer **[!UICONTROL Save]** om de levering op te slaan en deze weer te geven vanuit **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** nadat de workflow is uitgevoerd.

   ![](assets/delivery_loadcontent_activityexample.png)

1. Voeg op het tabblad **[!UICONTROL Script]** van de **[!UICONTROL Delivery]** -activiteit de volgende opdracht toe om de inhoud van het geïmporteerde bestand in de levering te laden:

   ```
   delivery.content.html.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. Sla de workflow op en voer deze uit. Er wordt een nieuwe levering met de geladen inhoud gemaakt onder **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** .

>[!NOTE]
>
>De beste praktijken en het oplossen van problemen op het servergebruik van SFTP zijn gedetailleerd [ in deze pagina ](../../platform/using/sftp-server-usage.md).
