---
product: campaign
title: Operatorgroepen maken en beheren
description: Leer hoe u toegang verleent aan groepen operatoren
feature: Access Management
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Operatorgroepen maken en beheren {#operator-groups}

![](../../assets/common.svg)

Operatorgroepen worden gemaakt via het knooppunt **[!UICONTROL Administration > Access management > Operator groups]** in de structuur.

## Nieuwe operatorgroep maken {#creating-a-new-operator-group}

Voer de volgende stappen uit om een nieuwe operatorgroep te maken:

1. Klik op de knop **[!UICONTROL New]** rechts van de lijst met groepen of klik met de rechtermuisknop op de lijst en kies **[!UICONTROL New]**.
1. Voer in het onderste venster van de sectie op het tabblad **[!UICONTROL General]** de naam en een beschrijving voor deze groep in de desbetreffende velden in.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. Klik op het tabblad **[!UICONTROL Content]** om machtigingen voor deze groep te definiëren.
1. Klik op de knop **[!UICONTROL Add]** om een toegewezen recht of een operator te selecteren die aan de groep moet worden gekoppeld.
1. Klik op de vervolgkeuzelijst of op de map rechts van het veld **[!UICONTROL Folder]** om de toegewezen rechten of operatoren te zoeken die aan deze groep moeten worden gekoppeld.
1. Selecteer de rechten of operatoren die u wilt toevoegen en klik op **[!UICONTROL OK]** om te valideren.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   Herhaal deze bewerking om andere rechten of operatoren toe te voegen.

1. Klik op de knop **[!UICONTROL Save]** om de groep aan de lijst toe te voegen.

## Standaardgroepen {#default-groups}

De standaardgroepen met operatoren zijn:

1. **[!UICONTROL Administrator]**

   De operatoren in deze groep hebben volledige toegang tot het exemplaar. Beheerders zijn gebruikers die toegang hebben tot de meest technische onderdelen van de interface. Zij houden de **[!UICONTROL Administration]** rol en zorgen ervoor dat het platform allen opstelling is.

   Deze groep bevat het volgende benoemde recht:

   * **[!UICONTROL ADMINISTRATION]**: het recht om objecten zoals workflow, levering, scripts, enz. uit te voeren, te maken, te bewerken/te verwijderen.

1. **[!UICONTROL Delivery operators]**

   De exploitanten in deze groep zijn verantwoordelijk voor het beheer van de leveringen: zij verlenen toegang tot de belangrijkste middelen die voor het creëren van en het voorbereiden van levering worden vereist (campagneretypologieën, leveringsafbeeldingen, standaardmalplaatjes, verpersoonlijkingsblokken, enz.).

   Deze groep bevat de volgende benoemde rechten:

   * **[!UICONTROL PREPARE DELIVERIES]**: het recht om de leveringsanalyse te maken, te bewerken en te starten;
   * **[!UICONTROL START DELIVERIES]**: het recht om eerder geanalyseerde leveringen goed te keuren.

1. **[!UICONTROL Campaign managers]**

   De exploitanten in deze groep kunnen marketingcampagnes beheren: hiermee hebt u toegang tot de objecten die aan campagnes zijn gekoppeld (plannen, programma&#39;s, workflows, budgetten, enz.) binnen het kader van **[!UICONTROL Campaign]** (optionele Adobe Campaign-module).

   Deze groep bevat de volgende benoemde rechten:

   * **[!UICONTROL INSERT FOLDERS]**: het recht om mappen in te voegen in de Adobe Campaign-structuur (op voorwaarde dat u bewerkingsrechten hebt voor de betrokken vertakkingen);
   * **[!UICONTROL WORKFLOW]**: recht om werkstromen te gebruiken.
   >[!NOTE]
   >
   >Met deze groep kunnen operatoren geen leveringen starten.

1. **[!UICONTROL Content contributors]**

   De operatoren in deze groep hebben toegang tot de mappen Inhoud binnen het kader van **[!UICONTROL Content management]** (optionele Adobe Campaign-module). Deze groep verleent geen aanvullende rechten.

1. **[!UICONTROL Access to reports]**

   Deze groep is gereserveerd voor externe operatoren, voor toegang tot de leveringsrapporten via een webtoegang.

1. **[!UICONTROL Workflow execution]**

   Met deze groep kunt u operatoren het recht geven om workflows te beheren die geen verband houden met campagnes.

1. **[!UICONTROL Workflow supervisors]**

   De operatoren in deze groep ontvangen een e-mailkennisgeving in geval van waarschuwingen over workflows voor campagnes.

1. Lokaal/centraal beheer

   Met deze groepen kunt u **[!UICONTROL Distributed marketing]** (optionele Adobe Campaign-module) gebruiken.

1. **[!UICONTROL Offer managers]**

   De operatoren in deze groep kunnen aanbiedingen maken en onderhouden. Raadpleeg deze [pagina](../../interaction/using/operator-profiles.md) voor meer informatie hierover.
Deze groep bevat de volgende benoemde rechten:

   * **[!UICONTROL INSERT FOLDERS]**: Recht om mappen in te voegen in de Adobe Campaign-structuur (op voorwaarde dat u bewerkrechten hebt voor de betrokken vertakkingen).
   * **[!UICONTROL EDIT FOLDERS]**: Recht om omslageigenschappen zoals interne naam, etiket, bijbehorende beeld, subomslagorde te veranderen, etc.
