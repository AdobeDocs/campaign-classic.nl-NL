---
solution: Campaign Classic
product: campaign
title: Benoemde rechten gebruiken om machtigingen in te stellen
description: Leer hoe u benoemde rechten kunt gebruiken om machtigingen in te stellen
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 4%

---


# Benoemde rechten gebruiken om machtigingen in te stellen{#named-rights}

Adobe Campaign stelt standaard een reeks benoemde rechten voor waarmee u de machtigingen kunt definiëren die aan operatoren en groepen operatoren zijn toegewezen. Deze rechten kunnen worden bewerkt vanaf het knooppunt **[!UICONTROL Administration > Access management > Named rights]** van de boomstructuur.

![](assets/s_ncs_admin_named_rights.png)

Deze rechten zijn als volgt:

* **[!UICONTROL ADMINISTRATION]**: Operatoren met  **[!UICONTROL ADMINISTRATION]** recht hebben volledige toegang tot het exemplaar. Beheerders kunnen elk object, zoals workflow, levering, scripts, enzovoort, uitvoeren, maken, bewerken of verwijderen.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: U kunt meerdere goedkeuringsstappen instellen in workflows en leveringen om ervoor te zorgen dat de huidige status is goedgekeurd door een toegewezen operator of groep. Gebruikers met het recht **[!UICONTROL APPROVAL ADMINISTRATION]** kunnen goedkeuringsstappen instellen en ook een operator of groep van operatoren toewijzen die deze stappen moeten goedkeuren.

* **[!UICONTROL CENTRAL]**: Recht op centraal beheer (Distributed Marketing).

* **[!UICONTROL DELETE FOLDER]**: Rechts om mappen te verwijderen. Met dit recht kunnen gebruikers mappen verwijderen uit de verkennerweergave.

* **[!UICONTROL EDIT FOLDERS]**: Recht om omslageigenschappen zoals interne naam, etiket, bijbehorende beeld, subomslagorde te veranderen, etc.

* **[!UICONTROL EXPORT]**: Gebruikers kunnen gegevens uit hun Adobe Campaign-instanties naar een bestand op een server of lokale computer exporteren met behulp van de  **[!UICONTROL EXPORT]** workflowactiviteit.

* **[!UICONTROL FILES ACCESS]**: Recht om toegang voor dossiers te lezen en te schrijven via een manuscript dat in de  **[!UICONTROL JavaScript]** werkschemaactiviteit kan worden geschreven om dossiers op een server te lezen/te schrijven.

* **[!UICONTROL IMPORT]**: Recht op het importeren van generieke gegevens. **[!UICONTROL IMPORT]** kunt u gegevens in een andere tabel importeren, terwijl u  **[!UICONTROL RECIPIENT IMPORT]** rechts alleen in de tabel voor ontvangers kunt importeren.

* **[!UICONTROL INSERT FOLDERS]**: Recht om omslagen op te nemen. Gebruikers met de rechtermuisknop **[!UICONTROL INSERT FOLDERS]** kunnen nieuwe mappen maken in de mappenstructuur in de weergave Verkenner.

* **[!UICONTROL LOCAL]**: Recht op lokaal beheer (Distributed Marketing).

* **[!UICONTROL MERGE]**: Rechts om de geselecteerde records samen te voegen tot één record. Als ontvangers bestaan als duplicaten, staat het **[!UICONTROL MERGE]** recht gebruiker toe om de duplicaten te selecteren en hen samen te voegen in een primaire ontvanger.

* **[!UICONTROL PREPARE DELIVERIES]**: Recht om een levering te maken, te bewerken en op te slaan. Gebruikers met de juiste **[!UICONTROL PREPARE DELIVERIES]** kunnen ook het analyseproces voor de levering starten.

* **[!UICONTROL PRIVACY DATA RIGHT]**: Recht om privacygegevens te verzamelen en te schrappen. Raadpleeg [deze pagina](https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html) voor meer informatie.

* **[!UICONTROL PROGRAM EXECUTION]**: Recht om bevelen in diverse programmeertalen uit te voeren.

* **[!UICONTROL RECIPIENT IMPORT]**: Recht om ontvangers in te voeren. Gebruikers met het recht **[!UICONTROL RECIPIENT IMPORT]** kunnen een lokaal bestand importeren in de ontvangende tabel.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Recht om het even welk SQL bevel direct op het gegevensbestand uit te voeren.

* **[!UICONTROL START DELIVERIES]**: Recht om eerder geanalyseerde leveringen goed te keuren. Na de afleveringsanalyse wordt de levering onderbroken in verschillende goedkeuringsstappen en moet deze worden goedgekeurd om te worden hervat. Gebruikers met de rechteroptie **[!UICONTROL START DELIVERIES]** mogen leveringen goedkeuren.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: Recht om uw eigen SQL manuscripten te schrijven gebruikend de SQL activiteit van het Beheer van Gegevens, om het werklijsten tot stand te brengen en te bevolken (zie  [deze sectie](../../workflow/using/sql-data-management.md)).

* **[!UICONTROL WORKFLOW]**: Recht om werkstromen uit te voeren. Zonder dit recht kunnen gebruikers geen workflows starten, stoppen of opnieuw starten.

* **[!UICONTROL WEBAPP]**: Recht om Webtoepassingen te gebruiken.

>[!NOTE]
>
>Deze lijst kan verschillen, afhankelijk van de invoegtoepassingen die op het platform zijn geïnstalleerd.

## Matrix met toegangsrechten {#access-rights-matrix}

Met standaardgroepen en benoemde rechten hebben operatoren toegang tot bepaalde mappen in de navigatiehiërarchie en kunnen ze lees-, schrijf- en verwijdermachtigingen verlenen.

De Adobe Campaign toegangsrechtenmatrix is [hier](/help/platform/using/assets/access-rights-matrix.pdf) beschikbaar.

[![image](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
