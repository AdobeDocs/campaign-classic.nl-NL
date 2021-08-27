---
product: campaign
title: Lijsten maken en beheren
description: Leer lijsten maken en beheren
feature: Profiles
role: User
level: Beginner
exl-id: 711b84cd-bac8-4f1a-9999-0124fbfc3a01
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 9%

---

# Lijsten maken en beheren{#creating-and-managing-lists}

![](../../assets/common.svg)

## Wat is een lijst? {#about-lists-in-adobe-campaign}

Een lijst is een statische set profielen die kan worden gebruikt voor leveringsacties of die kan worden bijgewerkt tijdens importbewerkingen of tijdens workflowuitvoering. Een populatie die via een query uit de database is geëxtraheerd, kan bijvoorbeeld een lijst leveren.

Lijsten worden gemaakt en beheerd via de koppeling **[!UICONTROL Lists]** op het tabblad **[!UICONTROL Profiles and targets]**.

![](assets/s_ncs_user_interface_group_link.png)

Er zijn twee typen lijsten beschikbaar in Adobe Campaign:

* **[!UICONTROL Group]** type: De  **[!UICONTROL Group]** typelijsten behoren tot een  **** statistische lijst met personen die op basis van specifieke criteria zijn geselecteerd. De lijst is als een momentopname van een reeks profielen. Houd er rekening mee dat dit niet automatisch wordt bijgewerkt als profielen aan de database worden toegevoegd.

   Voor meer informatie over hoe te om een **[!UICONTROL Group]** typelijst tot stand te brengen, verwijs naar deze [pagina](#creating-a-profile-list-from-a-group).

* **[!UICONTROL List]** type: Met  **[!UICONTROL List]** typelijsten kunt u workflows gebruiken om lijsten te maken en te beheren. Dit zijn specifieke lijsten die het resultaat zijn van gegevensimport en die kunnen worden bijgewerkt via de specifieke **[!UICONTROL List update]**-workflowactiviteit.

   In tegenstelling tot de **[!UICONTROL Group]** typelijst, kan deze typelijst automatisch met een **[!UICONTROL Scheduler]** activiteit worden bijgewerkt. Merk op dat voor een voorbeeld op hoe te om **[!UICONTROL List]** typelijsten tot stand te brengen, naar [deze pagina](../../workflow/using/list-update.md) verwijzen.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#create-list-video)

## Een profiellijst maken van een groep {#creating-a-profile-list-from-a-group}

**[!UICONTROL Group]** typelijsten die via de  **[!UICONTROL Profiles and targets]** koppeling worden gemaakt, moeten zijn gebaseerd op de standaard Adobe Campaign-profieltabel (nms:ontvanger).

>[!NOTE]
>
>Als u lijsten wilt maken die andere soorten gegevens bevatten, moet u een workflow uitvoeren. Als u bijvoorbeeld een query op de bezoekerslijst gebruikt en de lijst vervolgens bijwerkt, kunt u een bezoekerslijst maken. Raadpleeg [deze sectie](../../workflow/using/about-workflows.md) voor meer informatie over workflows.

Voer de volgende stappen uit om een nieuwe **[!UICONTROL Group]**-typelijst te maken:

1. Klik op de knop **[!UICONTROL Create]** en selecteer **[!UICONTROL New list]**.

   ![](assets/s_ncs_user_new_group.png)

1. Voer de informatie in op het tabblad **[!UICONTROL Edit]** van het venster voor het maken van de lijst.

   * Typ de lijstnaam in het veld **[!UICONTROL Label]** en wijzig, indien nodig, de interne naam.
   * Voeg een beschrijving voor deze lijst toe.
   * U kunt een vervaldatum opgeven: wanneer deze datum is bereikt, wordt de lijst gewist en automatisch verwijderd.

      ![](assets/list_expiration_date.png)

1. Klik op **[!UICONTROL Content]** op **[!UICONTROL Add]** om de profielen te selecteren die tot de lijst behoren.

   ![](assets/s_ncs_user_add_group.png)

1. Klik **[!UICONTROL Save]** om de lijst op te slaan. Het wordt dan toegevoegd aan het overzicht van lijsten.

U kunt nieuwe profielen rechtstreeks maken vanuit het venster Profielen toevoegen door op **[!UICONTROL Create]** te klikken. Het profiel wordt toegevoegd aan de database.

![](assets/s_ncs_user_new_recipient_from_group.png)

De profiellijst kan net als andere lijsten worden gevormd. Zie [deze sectie](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Gegevens koppelen aan een lijst {#linking-data-to-a-list}

>[!NOTE]
>
>Het koppelen van gegevens aan een lijst kan slechts met een **[!UICONTROL Group]** typelijst worden gedaan.

De profielen van een set profielen kunnen worden gefilterd en gekoppeld aan een lijst. De leveringsacties kunnen dan naar deze lijst, naar doelprofielen worden verzonden. Profielen groeperen:

1. Selecteer profielen en klik met de rechtermuisknop.
1. Selecteer **[!UICONTROL Actions > Associate selection with a list...]**.

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. Selecteer de gewenste lijst of maak een nieuwe lijst met de knop **[!UICONTROL Create]** en klik op **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. Klik op de knop **[!UICONTROL Start]**.

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

Met de optie **[!UICONTROL Recreate the list]** verwijdert u de eerdere inhoud uit de lijst. Deze modus is geoptimaliseerd omdat er geen query nodig is om te controleren of de profielen al aan de lijst zijn gekoppeld.

Als u de optie **[!UICONTROL No trace of this job is saved in the database]** uitschakelt, kunt u de uitvoeringsmap selecteren (of maken) waarin de informatie wordt opgeslagen die aan dit proces is gekoppeld.

In de bovenste sectie van het venster kunt u de uitvoering controleren. Met de knop **[!UICONTROL Stop]** kunt u het proces stoppen. De reeds verwerkte contacten zullen met de lijst worden verbonden.

U kunt het proces controleren via het tabblad **[!UICONTROL Lists]** op de profielen waarop deze bewerking betrekking heeft:

![](assets/s_ncs_user_add_selection_to_group_4.png)

U kunt de lijst ook bewerken via de homepage van Adobe Campaign: Klik op het menu **[!UICONTROL Profiles and Targets > Lists]** en selecteer de desbetreffende lijst. Op het tabblad **[!UICONTROL Content]** worden de profielen weergegeven die aan deze lijst zijn gekoppeld.

![](assets/s_ncs_user_add_selection_to_group_5.png)

## Een profiel uit een lijst verwijderen {#removing-a-profile-from-a-list}

Als u een profiel uit een lijst wilt verwijderen, kunt u:

* Bewerk de lijst, selecteer het profiel op het tabblad **[!UICONTROL Content]** en klik op het pictogram **[!UICONTROL Delete]**.

   ![](assets/list_remove_a_recipient.png)

* Bewerk het profiel, klik op de tab **[!UICONTROL List]** en klik op het pictogram **[!UICONTROL Delete]**.

   ![](assets/recipient_remove_a_list.png)

## Een lijst met profielen verwijderen {#deleting-a-list-of-profiles}

U kunt een of meer lijsten verwijderen uit de lijst met groepen in de Adobe Campaign-structuur. Om dit te doen, geef de boom via de **[!UICONTROL Advanced > Explorer]** verbinding in de homepage van Adobe Campaign uit. Selecteer de desbetreffende groep(en) en klik met de rechtermuisknop. Selecteer **[!UICONTROL Delete]**. U wordt in een waarschuwingsbericht gevraagd de verwijdering te bevestigen.

>[!NOTE]
>
>Wanneer u een lijst verwijdert, worden de profielen in de lijst niet gewijzigd, maar worden de gegevens in het bijbehorende profiel bijgewerkt.

## Video over zelfstudie {#create-list-video}

### Hoe te om een lijst van ontvangers tot stand te brengen

Een lijst is een statische reeks ontvangers die doelgericht kan worden benaderd in leveringsacties of die tijdens importbewerkingen of de uitvoering van een workflow kan worden bijgewerkt. Een lijst met ontvangers wordt ook wel een doelgroep genoemd.

Leer hoe te om een publiek tot stand te brengen door een lijst van ontvangers van de Ontdekkingsreiziger te vormen.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

### Een workflow gebruiken om een lijst met ontvangers te maken {#create-list-in-a-wf-video}

Leer hoe u een workflow maakt om ontvangers als doel in te stellen en hoe u deze terugkeert voordat u de lijst in een e-maildoel gebruikt.

>[!VIDEO](https://video.tv.adobe.com/v/25603?quality=12)

Er zijn [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl) extra Campaign Classic hoe kan ik-video&#39;s beschikbaar.
