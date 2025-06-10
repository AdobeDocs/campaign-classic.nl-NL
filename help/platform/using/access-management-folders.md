---
product: campaign
title: Toegang tot campagnemappen beheren
description: Leer hoe u toegang tot campagnemappen verleent en weergaven maakt
badge: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Application Settings, Permissions
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
source-git-commit: 6e83067cef2b08b5bee37610bfef515714756ada
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 2%

---

# Toegang tot mappen beheren{#folder-access-management}



Elke omslag van de boomstructuur van de Ontdekkingsreiziger heeft gelezen, schrijft, en schrapt toegangsrechten verbonden aan het. Om toegang te krijgen tot een bestand, moet een operator of groep operatoren ten minste lees-toegang tot het bestand hebben.

>[!NOTE]
>
>Meer over toestemmingen op omslagen leren, gelieve te verwijzen naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}.


## Mappen en weergaven {#folders-and-views}

### Wat is een map {#about-folders}

Mappen zijn knooppunten in Adobe Campaign-structuur. Deze knooppunten worden gemaakt door met de rechtermuisknop op de structuur te klikken via het menu **[!UICONTROL Add new folder]** . Standaard kunt u in het eerste menu de map toevoegen die overeenkomt met de huidige context.

![](assets/s_ncs_user_add_folder_in_tree.png)

U kunt de boomstructuur van de Explorer aanpassen. Leer configuratiestappen en beste praktijken [ in deze sectie ](adobe-campaign-workspace.md).

### Wat is een weergave {#about-views}

Daarnaast kunt u weergaven maken om de toegang tot gegevens te beperken en de inhoud van de structuur aan uw wensen aan te passen. U kunt vervolgens rechten toewijzen aan de weergaven.

Een weergave is een map waarin records worden weergegeven die fysiek zijn opgeslagen in een of meer andere mappen van hetzelfde type. Als u bijvoorbeeld een map Campagne maakt die een weergave is, worden standaard alle campagnes in de database weergegeven, ongeacht de oorsprong ervan. Deze gegevens kunnen vervolgens worden gefilterd.

Wanneer u een map naar een weergave converteert, worden alle gegevens die overeenkomen met het maptype dat in de database aanwezig is, weergegeven in de weergave, ongeacht de map waarin deze is opgeslagen. Vervolgens kunt u het filter filteren om de lijst met weergegeven gegevens te beperken.

>[!IMPORTANT]
>
>De weergaven bevatten gegevens en bieden toegang tot deze gegevens, maar de gegevens worden niet fysiek opgeslagen in de weergavemap. De exploitant moet de aangewezen rechten voor de gewenste actie in de omslagen van de gegevensbron (lees minstens toegang) hebben.
>
>Als u toegang tot een weergave wilt geven zonder toegang tot de bronmap, geeft u geen leestoegang op het bovenliggende knooppunt van de bronmap.

Om weergaven van mappen te onderscheiden, wordt de naam van elke weergave weergegeven in een andere kleur (donkercyaan).

![](assets/s_ncs_user_view_name_color.png)

### Mappen toevoegen en weergaven maken {#adding-folders-and-creating-views}

>[!IMPORTANT]
>
>Buiten de vakmappen mogen niet als weergave worden gemarkeerd.


In het onderstaande voorbeeld maken we nieuwe mappen waarin specifieke gegevens worden weergegeven:

1. Creeer een nieuwe **[!UICONTROL Deliveries]** typeomslag, en noem het **levert Frankrijk**.
1. Klik met de rechtermuisknop op deze map en selecteer **[!UICONTROL Properties...]** .

   ![ Schermafbeelding die een juiste klik tonen in de eigenschappen ](assets/s_ncs_user_add_folder_exple.png)

1. Selecteer op het tabblad **[!UICONTROL Restriction]** de optie **[!UICONTROL This folder is a view]** . Alle leveringen in het gegevensbestand zullen dan worden getoond.

   ![ Scherm die het meningsvakje tonen dat wordt gecontroleerd ](assets/s_ncs_user_add_folder_exple01.png)

1. Bepaal de criteria van de leveringsfilter van de vraagredacteur in het midden sectie van het venster: de campagnes die aan de bepaalde filter beantwoorden zullen dan worden getoond.

   >[!NOTE]
   >
   >De vraagredacteur wordt voorgesteld in [ deze sectie ](../../platform/using/about-queries-in-campaign.md).

   Met de volgende filtervoorwaarden:

![ Schermafbeelding die de verschillende filtervoorwaarden tonen ](assets/s_ncs_user_add_folder_exple00.png)

De volgende leveringen worden weergegeven in de weergave:

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>Wanneer het beheren van [ transactieoverseinen ](../../message-center/using/about-transactional-messaging.md) gebeurtenissen, moeten de **[!UICONTROL Real time events]** of **[!UICONTROL Batch events]** omslagen niet als meningen op de uitvoeringsinstanties worden geplaatst, aangezien dit tot de kwesties van het toegangsrecht zou kunnen leiden. Voor meer op gebeurtenisinzameling, zie [ deze sectie ](../../message-center/using/about-event-processing.md#event-collection).

<!--
## Permissions on a folder

### Edit permissions on a folder {#edit-permissions-on-a-folder}

To edit permissions on a specific folder of the tree, follow the steps below:

1. Right-click on the folder and select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Click the **[!UICONTROL Security]** tab to view authorizations on this folder.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Modify permissions {#modify-permissions}

To modify permissions, you can:

* **Replace a group or an operator**. To do this, click one of the groups (or operators) with rights to the folder, and select a new group (or a new operator) from the drop-down list:

  ![](assets/s_ncs_user_folder_properties_security02.png)

* **Authorize a group or an operator**. To do this, click the **[!UICONTROL Add]** button and select the group or operator to which you want to assign authorizations for this folder.
* **Forbid a group or an operator**. To do this, click **[!UICONTROL Delete]** and select the group or operator from which you want to remove authorization for this folder.
* **Select the rights assigned to a group or an operator**. To do this, click the group or operator concerned, then select the access rights you want to grant and deselect the others.

  ![](assets/s_ncs_user_folder_properties_security03.png)

### Propagate permissions {#propagate-permissions}

You can propagate authorizations and access rights. To do this, select the **[!UICONTROL Propagate]** option in the folder properties.

The authorizations defined in this window will then be applied to all the sub-folders of the current node. You can then overload these authorizations for each of the sub-folders.

>[!NOTE]
>
>Clearing this option for a folder does not automatically clear it for the sub-folders. You must clear it explicitly for each of the sub-folders.

### Grant access to all operators {#grant-access-to-all-operators}

In the **[!UICONTROL Security]** tab, if the **[!UICONTROL System folder]** option is selected, all operators will have access to this data, regardless of their rights. If this option is cleared, you must explicitly add the operator (or their group) to the list of authorizations in order for them to have access.

![](assets/s_ncs_user_folder_properties_security03b.png)
-->