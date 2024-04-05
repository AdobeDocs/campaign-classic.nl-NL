---
product: campaign
title: Operatorgroepen maken en beheren
description: Leer hoe u toegang verleent aan groepen operatoren
badge: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: 4e99ec73f99264e91ca427542e29bd42da88a3f9
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 1%

---

# Operatorgroepen maken en beheren {#operator-groups}



Operatorgroepen worden gecreëerd via de **[!UICONTROL Administration > Access management > Operator groups]** knooppunt in de boomstructuur.

## Nieuwe operatorgroep maken {#creating-a-new-operator-group}

Voer de volgende stappen uit om een nieuwe operatorgroep te maken:

1. Klik op de knop **[!UICONTROL New]** rechts van de lijst met groepen klikken of met de rechtermuisknop op de lijst klikken en **[!UICONTROL New]**.
1. In het gedeelte onder het venster, vanuit het **[!UICONTROL General]** voert u de naam en een beschrijving van deze groep in de desbetreffende velden in.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. Klik op de knop **[!UICONTROL Content]** om machtigingen voor deze groep te definiëren.
1. Klik op de knop **[!UICONTROL Add]** om een aangesteld recht of een exploitant te selecteren om aan de groep te associëren.
1. Klik op de vervolgkeuzelijst of op de map rechts van de **[!UICONTROL Folder]** veld om de aangestelde rechten of exploitanten te vinden die aan deze groep moeten worden gekoppeld.
1. Selecteer de rechten of operatoren die u wilt toevoegen en klik op **[!UICONTROL OK]** om te valideren.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   Herhaal deze bewerking om andere rechten of operatoren toe te voegen.

1. Klik op de knop **[!UICONTROL Save]** om de groep aan de lijst toe te voegen.

## Standaardgroepen {#default-groups}

De standaardgroepen met operatoren zijn:

1. **[!UICONTROL Administrator]**

   De operatoren in deze groep hebben volledige toegang tot het exemplaar. Beheerders zijn gebruikers die toegang hebben tot de meest technische onderdelen van de interface. Ze houden de **[!UICONTROL Administration]** en ervoor zorgen dat het platform volledig is opgezet.

   Deze groep bevat het volgende benoemde recht:

   * **[!UICONTROL ADMINISTRATION]**: recht om objecten zoals workflow, levering, scripts, enz. uit te voeren, te maken, te bewerken/te verwijderen.

1. **[!UICONTROL Delivery operators]**

   De operatoren in deze groep zijn verantwoordelijk voor het beheer van de leveringen: zij bieden toegang tot de belangrijkste bronnen die nodig zijn voor het maken en voorbereiden van de leveringen (campagneretypologieën, leveringstoewijzingen, standaardsjablonen, aanpassingsblokken, enz.).

   Deze groep bevat de volgende benoemde rechten:

   * **[!UICONTROL PREPARE DELIVERIES]**: recht om de leveringsanalyse te maken, te bewerken en te starten,
   * **[!UICONTROL START DELIVERIES]**: recht om eerder geanalyseerde leveringen goed te keuren.

1. **[!UICONTROL Campaign managers]**

   De exploitanten in deze groep kunnen marketing campagnes beheren: het laat u tot de voorwerpen toegang hebben verbonden aan campagnes (plannen, programma&#39;s, werkschema&#39;s, begrotingen, etc.) in het kader van **[!UICONTROL Campaign]** (optionele Adobe Campaign-module).

   Deze groep bevat de volgende benoemde rechten:

   * **[!UICONTROL INSERT FOLDERS]**: recht om mappen in te voegen in de Adobe Campaign-structuur (op voorwaarde dat u bewerkingsrechten hebt voor de betrokken vertakkingen),
   * **[!UICONTROL WORKFLOW]**: recht om workflows te gebruiken.

   >[!NOTE]
   >
   >Met deze groep kunnen operatoren geen leveringen starten.

1. **[!UICONTROL Content contributors]**

   De operatoren in deze groep hebben binnen het kader van **[!UICONTROL Content management]** (optionele Adobe Campaign-module). Deze groep verleent geen aanvullende rechten.

1. **[!UICONTROL Access to reports]**

   Deze groep is gereserveerd voor externe operatoren, zodat de pictogrammen Rapport, Planning en Forum in het campagneredashboard beschikbaar zijn voor een specifieke operator.

1. **[!UICONTROL Workflow execution]**

   Met deze groep kunt u operatoren het recht geven om workflows te beheren die geen verband houden met campagnes.

1. **[!UICONTROL Workflow supervisors]**

   De operatoren in deze groep ontvangen een e-mailkennisgeving in geval van waarschuwingen over workflows voor campagnes.

1. Lokaal/centraal beheer

   U kunt deze groepen gebruiken **[!UICONTROL Distributed marketing]** (optionele Adobe Campaign-module).

1. **[!UICONTROL Offer managers]**

   De operatoren in deze groep kunnen aanbiedingen maken en onderhouden. Raadpleeg voor meer informatie hierover [page](../../interaction/using/operator-profiles.md).
Deze groep bevat de volgende benoemde rechten:

   * **[!UICONTROL INSERT FOLDERS]**: Recht om mappen in te voegen in de Adobe Campaign-structuur (op voorwaarde dat u bewerkrechten hebt voor de betrokken vertakkingen),
   * **[!UICONTROL EDIT FOLDERS]**: Recht om mapeigenschappen zoals interne naam, label, gekoppelde afbeelding, volgorde van submappen, enz. te wijzigen.
