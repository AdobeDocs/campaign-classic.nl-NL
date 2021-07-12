---
product: campaign
title: Toegang tot campagnemappen beheren
description: Leer hoe u toegang kunt verlenen tot campagnemappen en weergaven kunt maken
feature: Applicatie-instellingen
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
source-git-commit: 6c28e6cd78ce7a8ee5c0dc7e671de780787b9f57
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 1%

---

# Toegang tot mappen beheren{#folder-access-management}

Elke omslag van de boomstructuur van de Ontdekkingsreiziger heeft gelezen, schrijft, en schrapt toegangsrechten verbonden aan het. Om toegang te krijgen tot een bestand, moet een operator of groep operatoren ten minste lees-toegang hebben.

## Mappen en weergaven {#folders-and-views}

### Wat is een map? {#about-folders}

Mappen zijn knooppunten in Adobe Campaign-structuur. Deze knooppunten worden gemaakt door met de rechtermuisknop op de structuur te klikken via het menu **[!UICONTROL Add new folder]**. Standaard kunt u in het eerste menu de map toevoegen die overeenkomt met de huidige context.

![](assets/s_ncs_user_add_folder_in_tree.png)

U kunt de boomstructuur van de Explorer aanpassen. Leer configuratiestappen en beste praktijken [in deze sectie](adobe-campaign-workspace.md).

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

In het onderstaande voorbeeld maken we nieuwe mappen waarin specifieke gegevens worden weergegeven:

1. Maak een nieuwe **[!UICONTROL Deliveries]**-typemap en noem deze **Deliveries France**.
1. Klik met de rechtermuisknop op deze map en selecteer **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_add_folder_exple.png)

1. Selecteer op het tabblad **[!UICONTROL Restriction]** de optie **[!UICONTROL This folder is a view]**. Alle leveringen in het gegevensbestand zullen dan worden getoond.

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. Bepaal de criteria van de leveringsfilter van de vraagredacteur in het middelste gedeelte van het venster: de campagnes die overeenkomen met het gedefinieerde filter worden dan weergegeven.

   >[!NOTE]
   >
   >De vraagredacteur wordt voorgesteld in [deze sectie](../../platform/using/about-queries-in-campaign.md).

   Met de volgende filtervoorwaarden:

![](assets/s_ncs_user_add_folder_exple00.png)

De volgende leveringen worden weergegeven in de weergave:

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>Bij het beheren van [transactioneel overseinen](../../message-center/using/about-transactional-messaging.md) gebeurtenissen, moeten **[!UICONTROL Real time events]** of **[!UICONTROL Batch events]** omslagen niet als meningen op de uitvoeringsinstanties worden geplaatst, aangezien dit tot toegangsjuiste kwesties zou kunnen leiden. Zie [deze sectie](../../message-center/using/about-event-processing.md#event-collection) voor meer informatie over het verzamelen van gebeurtenissen.

## Machtigingen voor een map

### Machtigingen bewerken in een map {#edit-permissions-on-a-folder}

Voer de volgende stappen uit als u machtigingen voor een specifieke map in de structuur wilt bewerken:

1. Klik met de rechtermuisknop op de map en selecteer **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Klik op het tabblad **[!UICONTROL Security]** om machtigingen voor deze map weer te geven.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Machtigingen wijzigen {#modify-permissions}

Als u machtigingen wilt wijzigen, kunt u:

* **Een groep of operator** vervangen. Klik hiertoe op een van de groepen (of operatoren) met rechten voor de map en selecteer een nieuwe groep (of een nieuwe operator) in de vervolgkeuzelijst:

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **Een groep of operator** autoriseren. Klik hiertoe op de knop **[!UICONTROL Add]** en selecteer de groep of operator waaraan u machtigingen voor deze map wilt toewijzen.
* **Verbod een groep of een operator**. Om dit te doen, klik **[!UICONTROL Delete]** en selecteer de groep of de exploitant waarvan u vergunning voor deze omslag wilt verwijderen.
* **Selecteer de rechten die aan een groep of een operator** zijn toegewezen. Klik hiertoe op de betrokken groep of operator, selecteer vervolgens de toegangsrechten die u wilt verlenen en hef de selectie van de andere rechten op.

   ![](assets/s_ncs_user_folder_properties_security03.png)

### Machtigingen voor doorgeven {#propagate-permissions}

U kunt machtigingen en toegangsrechten doorgeven. Selecteer hiertoe de optie **[!UICONTROL Propagate]** in de mapeigenschappen.

De in dit venster gedefinieerde autorisaties worden vervolgens toegepast op alle submappen van het huidige knooppunt. Vervolgens kunt u deze machtigingen voor elke submap te veel laden.

>[!NOTE]
>
>Als u deze optie voor een map wist, wordt deze niet automatisch gewist voor de submappen. U moet dit expliciet wissen voor elk van de submappen.

### Toegang verlenen aan alle marktdeelnemers {#grant-access-to-all-operators}

Als op het tabblad **[!UICONTROL Security]** de optie **[!UICONTROL System folder]** is geselecteerd, hebben alle operatoren toegang tot deze gegevens, ongeacht hun rechten. Als deze optie wordt ontruimd, moet u de exploitant (of hun groep) aan de lijst van toestemmingen uitdrukkelijk toevoegen om hen toegang te hebben.

![](assets/s_ncs_user_folder_properties_security03b.png)
