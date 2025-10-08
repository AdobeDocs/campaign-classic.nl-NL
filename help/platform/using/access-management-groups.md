---
product: campaign
title: Operatorgroepen maken en beheren
description: Leer hoe u toegang verleent aan groepen operatoren
badge: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: a5bbd2e6c102a8afa4cd5931b77b0c83705a7bfa
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 1%

---

# Operatorgroepen maken en beheren {#operator-groups}

>[!NOTE]
>
>Deze procedures zijn slechts voor exploitanten van toepassing die met Campagne met de **erfenis inheemse authentificatie** verbinden. Beginnend Campaign Classic v7.3.1, zouden alle exploitanten [ Adobe Identity Management Systeem (IMS) ](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} moeten gebruiken om met Campagne te verbinden. [Meer informatie](../../technotes/using/migrate-users-to-ims.md)
>
>Wanneer u verbinding maakt met Campagne met uw Adobe ID, is de volgende sectie niet meer van toepassing. Leer hoe te opstellingstoestemmingen met Adobe IMS in [ Campagne v8 documentatie ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html){target="_blank"}.

Operatorgroepen worden gemaakt via het knooppunt **[!UICONTROL Administration > Access management > Operator groups]** in de structuur.

## Nieuwe operatorgroep maken {#creating-a-new-operator-group}

Voer de volgende stappen uit om een nieuwe operatorgroep te maken:

1. Klik op de knop **[!UICONTROL New]** rechts van de lijst met groepen of klik met de rechtermuisknop op de lijst en kies **[!UICONTROL New]** .
1. Typ in het onderste venster van de sectie de naam en een beschrijving voor deze groep in de desbetreffende velden op het tabblad **[!UICONTROL General]** .

   ![](assets/s_ncs_user_create_operator_gp.png)

1. Klik op het tabblad **[!UICONTROL Content]** om autorisaties voor deze groep te definiëren.
1. Klik op de knop **[!UICONTROL Add]** om een toegewezen recht of operator te selecteren die u aan de groep wilt koppelen.
1. Klik op de vervolgkeuzelijst of op de map rechts van het veld **[!UICONTROL Folder]** om de toegewezen rechten of operatoren te zoeken die u aan deze groep wilt koppelen.
1. Selecteer de rechten of operatoren die u wilt toevoegen en klik op **[!UICONTROL OK]** om te valideren.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   Herhaal deze bewerking om andere rechten of operatoren toe te voegen.

1. Klik op de knop **[!UICONTROL Save]** om de groep aan de lijst toe te voegen.

## Standaardgroepen {#default-groups}

De standaardgroepen met operatoren zijn:

1. **[!UICONTROL Administrator]**

   De operatoren in deze groep hebben volledige toegang tot het exemplaar. Beheerders zijn gebruikers die toegang hebben tot de meest technische onderdelen van de interface. Ze hebben de **[!UICONTROL Administration]** rol en zorgen ervoor dat het platform helemaal is ingesteld.

   Deze groep bevat het volgende benoemde recht:

   * **[!UICONTROL ADMINISTRATION]**: het recht om objecten zoals workflow, levering, scripts, enzovoort uit te voeren, te maken, te bewerken/te verwijderen.

1. **[!UICONTROL Delivery operators]**

   De operatoren in deze groep zijn verantwoordelijk voor het beheer van de leveringen: zij bieden toegang tot de belangrijkste bronnen die nodig zijn voor het maken en voorbereiden van de leveringen (campagneretypologieën, leveringstoewijzingen, standaardsjablonen, aanpassingsblokken, enz.).

   Deze groep bevat de volgende benoemde rechten:

   * **[!UICONTROL PREPARE DELIVERIES]**: recht om de leveringsanalyse te maken, te bewerken en te starten,
   * **[!UICONTROL START DELIVERIES]** : rechts om eerder geanalyseerde leveringen goed te keuren.

1. **[!UICONTROL Campaign managers]**

   De operatoren in deze groep kunnen marketingcampagnes beheren. U hebt toegang tot de objecten die gekoppeld zijn aan campagnes (plannen, programma&#39;s, workflows, budgetten, enzovoort) in het kader van **[!UICONTROL Campaign]** (optionele Adobe Campaign-module).

   Deze groep bevat de volgende benoemde rechten:

   * **[!UICONTROL INSERT FOLDERS]**: het recht om mappen in te voegen in de Adobe Campaign-structuur (op voorwaarde dat u bewerkrechten hebt voor de betrokken vertakkingen),
   * **[!UICONTROL WORKFLOW]** : recht om workflows te gebruiken.

   >[!NOTE]
   >
   >Met deze groep kunnen operatoren geen leveringen starten.

1. **[!UICONTROL Content contributors]**

   De operatoren in deze groep hebben toegang tot de mappen Inhoud binnen het kader van **[!UICONTROL Content management]** (optionele Adobe Campaign-module). Deze groep verleent geen aanvullende rechten.

1. **[!UICONTROL Access to reports]**

   Deze groep is gereserveerd voor externe operatoren, zodat de pictogrammen Rapport, Planning en Forum in het campagneredashboard beschikbaar zijn voor een specifieke operator.

1. **[!UICONTROL Workflow execution]**

   Met deze groep kunt u operatoren het recht geven om workflows te beheren die geen verband houden met campagnes.

1. **[!UICONTROL Workflow supervisors]**

   De operatoren in deze groep ontvangen een e-mailkennisgeving in geval van waarschuwingen over workflows voor campagnes.

1. Lokaal/centraal beheer

   Met deze groepen kunt u **[!UICONTROL Distributed marketing]** gebruiken (optionele Adobe Campaign-module).

1. **[!UICONTROL Offer managers]**

   De operatoren in deze groep kunnen aanbiedingen maken en onderhouden. Voor meer informatie over dit, verwijs naar deze [ pagina ](../../interaction/using/operator-profiles.md).
Deze groep bevat de volgende benoemde rechten:

   * **[!UICONTROL INSERT FOLDERS]**: recht om mappen in te voegen in de Adobe Campaign-structuur (op voorwaarde dat u bewerkrechten hebt voor de betrokken vertakkingen),
   * **[!UICONTROL EDIT FOLDERS]**: rechts om mapeigenschappen zoals interne naam, label, gekoppelde afbeelding, volgorde van submappen, enz. te wijzigen.
