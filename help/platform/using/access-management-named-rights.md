---
product: campaign
title: Opgegeven rechten gebruiken om machtigingen in te stellen
description: Leer hoe u benoemde rechten kunt gebruiken om machtigingen in te stellen
feature: Access Management
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 6%

---

# Opgegeven rechten gebruiken om machtigingen in te stellen{#named-rights}

![](../../assets/common.svg)

Adobe Campaign stelt standaard een reeks benoemde rechten voor waarmee u de machtigingen kunt definiëren die aan operatoren en groepen operatoren zijn toegewezen. Deze rechten kunnen worden bewerkt via de **[!UICONTROL Administration > Access management > Named rights]** knooppunt van de structuur.

![](assets/s_ncs_admin_named_rights.png)

Deze rechten zijn als volgt:

* **[!UICONTROL ADMINISTRATION]**: Operatoren met de **[!UICONTROL ADMINISTRATION]** het recht heeft volledige toegang tot het gerecht . Beheerders kunnen elk object, zoals workflow, levering, scripts, enzovoort, uitvoeren, maken, bewerken of verwijderen.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: U kunt meerdere goedkeuringsstappen instellen in workflows en leveringen om ervoor te zorgen dat de huidige status is goedgekeurd door een toegewezen operator of groep. Gebruikers met de **[!UICONTROL APPROVAL ADMINISTRATION]** met recht kunnen goedkeuringsstappen worden ingesteld en kan ook een exploitant of een groep van exploitanten worden toegewezen die deze stappen moeten goedkeuren.

* **[!UICONTROL CENTRAL]**: Recht op centraal beheer (Distributed Marketing).

* **[!UICONTROL DELETE FOLDER]**: Rechts om mappen te verwijderen. Met dit recht kunnen gebruikers mappen verwijderen uit de verkennerweergave.

* **[!UICONTROL EDIT FOLDERS]**: Recht om omslageigenschappen zoals interne naam, etiket, bijbehorende beeld, subomslagorde te veranderen, etc.

* **[!UICONTROL EXPORT]**: Gebruikers kunnen gegevens uit hun Adobe Campaign-instanties exporteren naar een bestand op een server of lokale computer met behulp van de **[!UICONTROL EXPORT]** workflowactiviteit.

* **[!UICONTROL FILES ACCESS]**: Recht om toegang voor dossiers te lezen en te schrijven via een manuscript dat in kan schrijven **[!UICONTROL JavaScript]** workflowactiviteit voor het lezen/schrijven van bestanden op een server.

* **[!UICONTROL IMPORT]**: Recht op het importeren van generieke gegevens. **[!UICONTROL IMPORT]** kunt u gegevens in een andere tabel importeren, terwijl de optie **[!UICONTROL RECIPIENT IMPORT]** Met right kunt u alleen importeren in de tabel voor ontvangers.

* **[!UICONTROL INSERT FOLDERS]**: Recht om omslagen op te nemen. Gebruikers met de **[!UICONTROL INSERT FOLDERS]** Met de rechtermuisknop kunt u nieuwe mappen maken in de mappenstructuur in de weergave Verkenner.

* **[!UICONTROL LOCAL]**: Recht op lokaal beheer (Distributed Marketing).

* **[!UICONTROL MERGE]**: Rechts om de geselecteerde records samen te voegen tot één record. Als ontvangers bestaan als duplicaten, worden de **[!UICONTROL MERGE]** Met de rechtermuisknop kan de gebruiker de duplicaten selecteren en deze samenvoegen in een primaire ontvanger.

* **[!UICONTROL PREPARE DELIVERIES]**: Recht om een levering te maken, te bewerken en op te slaan. Gebruikers met de **[!UICONTROL PREPARE DELIVERIES]** het recht kan ook beginnen met het proces van de leveringsanalyse .

* **[!UICONTROL PRIVACY DATA RIGHT]**: Recht om privacygegevens te verzamelen en te schrappen. Raadpleeg [deze pagina](https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html) voor meer informatie.

* **[!UICONTROL PROGRAM EXECUTION]**: Recht om bevelen in diverse programmeertalen uit te voeren.

* **[!UICONTROL RECIPIENT IMPORT]**: Recht om ontvangers in te voeren. Gebruikers met de **[!UICONTROL RECIPIENT IMPORT]** Met de rechtermuisknop kunt u een lokaal bestand importeren in de ontvangende tabel.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Recht om het even welk SQL bevel direct op het gegevensbestand uit te voeren.

* **[!UICONTROL START DELIVERIES]**: Recht om eerder geanalyseerde leveringen goed te keuren. Na de afleveringsanalyse wordt de levering onderbroken in verschillende goedkeuringsstappen en moet deze worden goedgekeurd om te worden hervat. Gebruikers met de **[!UICONTROL START DELIVERIES]** het recht heeft leveringen goed te keuren.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: Recht om uw eigen SQL manuscripten te schrijven gebruikend de SQL activiteit van het Beheer van Gegevens, om het werklijsten tot stand te brengen en te bevolken (zie [deze sectie](../../workflow/using/sql-data-management.md)).

* **[!UICONTROL WORKFLOW]**: Recht om werkstromen uit te voeren. Zonder dit recht kunnen gebruikers geen workflows starten, stoppen of opnieuw starten.

* **[!UICONTROL WEBAPP]**: Recht om Webtoepassingen te gebruiken.

>[!NOTE]
>
>Deze lijst kan verschillen, afhankelijk van de invoegtoepassingen die op het platform zijn geïnstalleerd.

## Matrix toegangsrechten {#access-rights-matrix}

Met standaardgroepen en benoemde rechten hebben operatoren toegang tot bepaalde mappen in de navigatiehiërarchie en kunnen ze lees-, schrijf- en verwijdermachtigingen verlenen.

Adobe Campaign-matrix voor toegangsrechten is beschikbaar [hier](/help/platform/using/assets/access-rights-matrix.pdf).

[![image](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
