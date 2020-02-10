---
title: Lijsten maken en beheren
seo-title: Lijsten maken en beheren
description: Lijsten maken en beheren
seo-description: null
page-status-flag: never-activated
uuid: 17d1a7d0-a728-490e-a820-19f469fddbcd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 9fc243b2-7b7b-4083-83f6-04c12336492d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Lijsten maken en beheren{#creating-and-managing-lists}

## Informatie over lijsten in Adobe-campagne {#about-lists-in-adobe-campaign}

Een lijst is een statische set profielen die kan worden gebruikt voor leveringsacties of die kan worden bijgewerkt tijdens importbewerkingen of tijdens workflowuitvoering. Bijvoorbeeld, kan een populatie die uit het gegevensbestand via een vraag wordt gehaald een lijst leveren.

Leveringen (via e-mail, sms of andere kanalen) die op deze lijsten gericht zijn, kunnen dan worden opgezet in overeenstemming met de beroepsethiek van het op de markt brengen van vergunningen.

Lijsten worden gemaakt en beheerd via de **[!UICONTROL Lists]** koppeling op het **[!UICONTROL Profiles and targets]** tabblad.

![](assets/s_ncs_user_interface_group_link.png)

Er zijn twee soorten lijsten beschikbaar in Adobe Campaign:

* **[!UICONTROL Group]** type: De **[!UICONTROL Group]** typelijsten behoren tot een **statische** lijst met personen die op basis van specifieke criteria zijn geselecteerd. De lijst is als een momentopname van een reeks profielen. Houd er rekening mee dat dit niet automatisch wordt bijgewerkt als profielen aan de database worden toegevoegd.

   Raadpleeg deze **[!UICONTROL Group]** pagina [voor meer informatie over het maken van een](#creating-a-profile-list-from-a-group)typelijst.

* **[!UICONTROL List]** type: Met **[!UICONTROL List]** typelijsten kunt u workflows gebruiken om lijsten te maken en te beheren. Dit zijn specifieke lijsten die het resultaat zijn van gegevensimporten en die kunnen worden bijgewerkt via de specifieke **[!UICONTROL List update]** workflowactiviteit.

   In tegenstelling tot de **[!UICONTROL Group]** typelijst, kan deze typelijst automatisch met een **[!UICONTROL Scheduler]** activiteit worden bijgewerkt. Raadpleeg de pagina **[!UICONTROL List]** voor een voorbeeld van het maken van [](../../workflow/using/list-update.md)typelijsten.

## Een profiellijst maken op basis van een groep {#creating-a-profile-list-from-a-group}

**[!UICONTROL Group]** typelijsten die via de **[!UICONTROL Profiles and targets]** koppeling worden gemaakt, moeten zijn gebaseerd op de standaardtabel met Adobe-cameraprofielen (nms:ontvanger).

>[!NOTE]
>
>Als u lijsten wilt maken die andere soorten gegevens bevatten, moet u een workflow uitvoeren. Als u bijvoorbeeld een query op de bezoekerslijst gebruikt en de lijst vervolgens bijwerkt, kunt u een bezoekerslijst maken. Raadpleeg [deze sectie](../../workflow/using/about-workflows.md)voor meer informatie over workflows.

Voer de volgende stappen uit om een nieuwe **[!UICONTROL Group]** typelijst te maken:

1. Klik op de **[!UICONTROL Create]** knop en selecteer **[!UICONTROL New list]**.

   ![](assets/s_ncs_user_new_group.png)

1. Voer de informatie in op het **[!UICONTROL Edit]** tabblad van het venster voor het maken van de lijst.

   * Voer de naam van de lijst in het **[!UICONTROL Label]** veld in en wijzig indien nodig de interne naam.
   * Voeg een beschrijving voor deze lijst toe.
   * U kunt een vervaldatum opgeven: wanneer deze datum is bereikt, wordt de lijst gewist en automatisch verwijderd.

      ![](assets/list_expiration_date.png)

1. Klik op het **[!UICONTROL Content]** tabblad **[!UICONTROL Add]** om de profielen te selecteren die bij de lijst horen.

   ![](assets/s_ncs_user_add_group.png)

1. Klik **[!UICONTROL Save]** om de lijst op te slaan. Het wordt dan toegevoegd aan het overzicht van lijsten.

U kunt nieuwe profielen rechtstreeks maken vanuit het venster Profielen toevoegen door op **[!UICONTROL Create]** te klikken. Het profiel wordt toegevoegd aan de database.

![](assets/s_ncs_user_new_recipient_from_group.png)

De profiellijst kan net als andere lijsten worden gevormd. Zie Lijsten [configureren](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Gegevens koppelen aan een lijst {#linking-data-to-a-list}

>[!NOTE]
>
>Gegevens kunnen alleen met een **[!UICONTROL Group]** typelijst worden gekoppeld aan een lijst.

De profielen van een set profielen kunnen worden gefilterd en gekoppeld aan een lijst. De leveringsacties kunnen dan naar deze lijst, naar doelprofielen worden verzonden. Profielen groeperen:

1. Selecteer profielen en klik met de rechtermuisknop.
1. Selecteer **[!UICONTROL Actions > Associate selection with a list...]**.

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. Selecteer de gewenste lijst of maak een nieuwe lijst met de **[!UICONTROL Create]** knop en klik op **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. Klik op de **[!UICONTROL Start]** knop.

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

Met de **[!UICONTROL Recreate the list]** optie verwijdert u de eerdere inhoud uit de lijst. Deze modus is geoptimaliseerd omdat er geen query nodig is om te controleren of de profielen al aan de lijst zijn gekoppeld.

Als u de **[!UICONTROL No trace of this job is saved in the database]** optie uitschakelt, kunt u de uitvoeringsmap selecteren (of maken) waarin de informatie wordt opgeslagen die aan dit proces is gekoppeld.

In de bovenste sectie van het venster kunt u de uitvoering controleren. Met de **[!UICONTROL Stop]** knop kunt u het proces stoppen. De reeds verwerkte contacten zullen met de lijst worden verbonden.

U kunt het proces controleren via het **[!UICONTROL Lists]** tabblad op de profielen waarop deze bewerking betrekking heeft:

![](assets/s_ncs_user_add_selection_to_group_4.png)

U kunt de lijst ook bewerken via de startpagina van Adobe Campagne: Klik op het **[!UICONTROL Profiles and Targets > Lists]** menu en selecteer de desbetreffende lijst. Op het **[!UICONTROL Content]** tabblad ziet u de profielen die aan deze lijst zijn gekoppeld.

![](assets/s_ncs_user_add_selection_to_group_5.png)

## Een profiel uit een lijst verwijderen {#removing-a-profile-from-a-list}

Als u een profiel uit een lijst wilt verwijderen, kunt u:

* Bewerk de lijst, selecteer het profiel op het **[!UICONTROL Content]** tabblad en klik op het **[!UICONTROL Delete]** pictogram.

   ![](assets/list_remove_a_recipient.png)

* Bewerk het profiel, klik op het **[!UICONTROL List]** tabblad en klik vervolgens op het **[!UICONTROL Delete]** pictogram.

   ![](assets/recipient_remove_a_list.png)

## Een lijst met profielen verwijderen {#deleting-a-list-of-profiles}

U kunt een of meer lijsten verwijderen uit de lijst met groepen in de Adobe Campagne-structuur. Hiervoor bewerkt u de structuur via de **[!UICONTROL Advanced > Explorer]** koppeling op de startpagina van Adobe Campagne. Selecteer de desbetreffende groep(en) en klik met de rechtermuisknop. Selecteer **[!UICONTROL Delete]**. U wordt in een waarschuwingsbericht gevraagd de verwijdering te bevestigen.

>[!NOTE]
>
>Wanneer u een lijst verwijdert, worden de profielen in de lijst niet gewijzigd, maar worden de gegevens in het bijbehorende profiel bijgewerkt.

