---
product: campaign
title: Opgegeven rechten gebruiken om machtigingen in te stellen
description: Leer hoe u benoemde rechten kunt gebruiken om machtigingen in te stellen
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 02ecc0e6bb3bd361f512baeefc9e0f2271063387
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 3%

---

# Opgegeven rechten gebruiken om machtigingen in te stellen{#named-rights}

Adobe Campaign stelt standaard een reeks benoemde rechten voor waarmee u de machtigingen kunt definiëren die aan operatoren en groepen operatoren zijn toegewezen. Deze rechten kunnen worden bewerkt vanaf het knooppunt **[!UICONTROL Administration > Access management > Named rights]** van de boomstructuur.

![](assets/s_ncs_admin_named_rights.png)

Deze rechten zijn als volgt:

* **[!UICONTROL ADMINISTRATION]**: operatoren met het **[!UICONTROL ADMINISTRATION]** -recht hebben volledige toegang tot de instantie. Beheerders kunnen elk object, zoals workflow, levering, scripts, enzovoort, uitvoeren, maken, bewerken of verwijderen.

  >[!IMPORTANT]
  >
  >**na het migreren aan IMS:** Zodra u aan het Systeem van Adobe Identity Management (IMS) migreert, zal om het even welk Profiel van het Product of Benoemd Rechts die het woord &quot;admin&quot;in zijn naam (zoals &quot;Beheerders&quot;, &quot;admin&quot;, &quot;admins&quot;, enz.) bevatten automatisch toegang tot het Controlebord van de Campagne verlenen. We raden u aan het gebruik van &quot;admin&quot; in namen van benoemde rechten of Rol te vermijden, tenzij u van plan bent dat deze gebruikers toegang tot het Configuratiescherm hebben. Leer meer over [&#x200B; migratie IMS &#x200B;](../../technotes/using/migrate-users-to-ims.md) en [&#x200B; het leiden toegang van het Controlebord &#x200B;](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html){target="_blank"}.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: U kunt meerdere goedkeuringsstappen instellen in workflows en leveringen om ervoor te zorgen dat het huidige frame is goedgekeurd door een toegewezen operator of groep. Gebruikers met de optie **[!UICONTROL APPROVAL ADMINISTRATION]** kunnen goedkeuringsstappen instellen en ook een operator of groep van operatoren toewijzen die deze stappen moeten goedkeuren.

  >[!IMPORTANT]
  >
  >**na het migreren aan IMS:** Profielen van het Product of de Genoemde Rechten die het woord &quot;admin&quot;bevatten (zoals &quot;Beheerder van de Goedkeuring&quot;) zullen toegang tot het Controlebord van de Campagne verlenen. Leer meer over [&#x200B; migratie IMS &#x200B;](../../technotes/using/migrate-users-to-ims.md) en [&#x200B; het leiden toegang van het Controlebord &#x200B;](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html){target="_blank"}.

* **[!UICONTROL CENTRAL]**: Recht op centraal beheer (Distributed Marketing).

* **[!UICONTROL DELETE FOLDER]**: rechts om mappen te verwijderen. Met dit recht kunnen gebruikers mappen verwijderen uit de verkennerweergave.

* **[!UICONTROL EDIT FOLDERS]**: rechts om mapeigenschappen zoals interne naam, label, gekoppelde afbeelding, volgorde van submappen, enz. te wijzigen.

* **[!UICONTROL EXPORT]**: gebruikers kunnen gegevens uit hun Adobe Campaign-instanties exporteren naar een bestand op een server of lokale computer met behulp van de **[!UICONTROL EXPORT]** -workflowactiviteit.

* **[!UICONTROL FILES ACCESS]**: Recht op lees- en schrijftoegang voor bestanden via een script dat in de **[!UICONTROL JavaScript]** -workflowactiviteit kan worden geschreven om bestanden op een server te lezen/schrijven.

* **[!UICONTROL IMPORT]**: rechts voor het importeren van generieke gegevens. Met **[!UICONTROL IMPORT]** kunt u gegevens importeren in een andere tabel, terwijl met **[!UICONTROL RECIPIENT IMPORT]** right alleen gegevens kunnen worden geïmporteerd in de ontvangende tabel.

* **[!UICONTROL INSERT FOLDERS]**: rechts om mappen in te voegen. Gebruikers met de rechtermuisknop van **[!UICONTROL INSERT FOLDERS]** kunnen nieuwe mappen in de mappenstructuur in de verkennerweergave maken.

* **[!UICONTROL LOCAL]**: Recht op lokaal beheer (Distributed Marketing).

* **[!UICONTROL MERGE]**: rechts om de geselecteerde records samen te voegen tot één record. Als ontvangers bestaan als duplicaten, staat het recht van **[!UICONTROL MERGE]** gebruiker toe om de duplicaten te selecteren en hen samen te voegen in een primaire ontvanger.

* **[!UICONTROL PREPARE DELIVERIES]**: Recht om een levering te maken, bewerken en opslaan. Gebruikers met de optie **[!UICONTROL PREPARE DELIVERIES]** kunnen ook het analyseproces voor de levering starten.

* **[!UICONTROL PRIVACY DATA RIGHT]**: recht om privacygegevens te verzamelen en te verwijderen. Raadpleeg [deze pagina](https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html) voor meer informatie.

* **[!UICONTROL PROGRAM EXECUTION]**: recht om opdrachten uit te voeren in verschillende programmeertalen.

* **[!UICONTROL RECIPIENT IMPORT]**: Recht om ontvangers te importeren. Gebruikers met de optie **[!UICONTROL RECIPIENT IMPORT]** kunnen een lokaal bestand importeren in de tabel met ontvangers.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Recht om een SQL-opdracht rechtstreeks in de database uit te voeren.

* **[!UICONTROL START DELIVERIES]**: Recht om eerder geanalyseerde leveringen goed te keuren. Na de afleveringsanalyse wordt de levering onderbroken in verschillende goedkeuringsstappen en moet deze worden goedgekeurd om te worden hervat. Gebruikers met de optie **[!UICONTROL START DELIVERIES]** rechts mogen leveringen goedkeuren.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: Recht om uw eigen SQL manuscripten te schrijven gebruikend de SQL activiteit van het Beheer van Gegevens, om het werklijsten tot stand te brengen en te bevolken. Verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/sql-data-management.html){target="_blank"}.

* **[!UICONTROL WORKFLOW]**: Recht om werkstromen uit te voeren. Zonder dit recht kunnen gebruikers geen workflows starten, stoppen of opnieuw starten.

* **[!UICONTROL WEBAPP]**: recht om webtoepassingen te gebruiken.

>[!NOTE]
>
>Deze lijst kan verschillen, afhankelijk van de invoegtoepassingen die op het platform zijn geïnstalleerd.

## Matrix toegangsrechten {#access-rights-matrix}

Met standaardgroepen en benoemde rechten hebben operatoren toegang tot bepaalde mappen in de navigatiehiërarchie en kunnen ze lees-, schrijf- en verwijdermachtigingen verlenen.

De de toegangsrechtenmatrijs van Adobe Campaign is beschikbaar [&#x200B; hier &#x200B;](/help/platform/using/assets/access-rights-matrix.pdf).

[![afbeelding](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf)
