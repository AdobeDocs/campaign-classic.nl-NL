---
product: campaign
title: Lijsten beheren en aanpassen
description: Leer om lijsten te doorbladeren en te vormen
feature: Audiences, Data Management
exl-id: 21656cc2-15a1-4156-8897-ea4fe3e9b97f
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 1%

---

# Lijsten beheren en aanpassen{#manage-and-customize-lists}



U kunt tot de lijsten van verslagen in het gegevensbestand van de Campagne toegang hebben gebruikend de Ontdekkingsreiziger. U kunt deze lijsten filteren, zoekopdrachten uitvoeren, informatie toevoegen, filteren en sorteren.

## Records tellen {#counting-records}

Standaard laadt Adobe Campaign de eerste 200 records van een lijst. Dit betekent dat niet noodzakelijkerwijs alle records van de tabel worden weergegeven die u bekijkt. U kunt een telling van het aantal verslagen in de lijst in werking stellen en meer verslagen laden.

In het onderste rechtergedeelte van het lijstscherm toont een **[!UICONTROL counter]** hoeveel records zijn geladen en het totale aantal records in de database (na het toepassen van filters):

![](assets/s_ncs_user_nb_200_0.png)

Als een &quot;**?**&quot; wordt weergegeven in plaats van het nummer aan de rechterkant, klikt u op de teller om de berekening te starten.

### Meer records laden {#loading-more-records}

Als u aanvullende records wilt laden (en dus wilt weergeven) (standaard 200 regels), klikt u op **[!UICONTROL Continue loading]** .

![](assets/s_ncs_user_load_list.png)

Als u alle records wilt laden, klikt u met de rechtermuisknop op de lijst en selecteert u **[!UICONTROL Load all]** .

>[!CAUTION]
>
>Afhankelijk van het aantal records kan de tijd voor het laden van de volledige lijst lang zijn.

### Standaardaantal records wijzigen {#change-default-number-of-records}

Als u het standaardaantal geladen records wilt wijzigen, klikt u op **[!UICONTROL Configure list]** rechtsonder in de lijst.

![](assets/s_ncs_user_configure_list.png)

Klik in het lijstconfiguratievenster op **[!UICONTROL Advanced parameters]** (linksonder) en wijzig het aantal regels dat moet worden opgehaald.

![](assets/s_ncs_user_configurelist_advancedparam.png)

## Lijsten configureren {#configuring-lists}

### Kolommen toevoegen {#add-columns}

Er zijn twee manieren om een kolom in een lijst toe te voegen.

U kunt snel een kolom aan een lijst van het detail van een verslag toevoegen. Dit doet u als volgt:

1. Klik in een detailscherm met de rechtermuisknop op het veld dat u in een kolom wilt weergeven.
1. Selecteer **[!UICONTROL Add in the list]**.

   De kolom wordt rechts van de bestaande kolommen toegevoegd.

![](assets/s_ncs_user_add_in_list.png)

Een andere manier om kolommen toe te voegen, bijvoorbeeld als u gegevens wilt tonen die niet op het detailscherm worden getoond, is het venster van de lijstconfiguratie te gebruiken. Dit doet u als volgt:

1. Klik op **[!UICONTROL Configure list]** onder en rechts van de lijst.

   ![](assets/s_ncs_user_configure_list.png)

1. Dubbelklik in het configuratievenster van de lijst op het veld dat u wilt toevoegen aan de lijst **[!UICONTROL Available fields]** om deze toe te voegen aan de lijst **[!UICONTROL Output columns]** .

   ![](assets/s_ncs_user_configurelist.png)

   >[!NOTE]
   >
   >Geavanceerde velden worden standaard niet weergegeven. Om hen te tonen, klik **Geavanceerde gebieden van de Vertoning** hieronder en rechts van de lijst van beschikbare gebieden.
   >
   >De labels worden weergegeven als een tabel en vervolgens in alfabetische volgorde.
   >
   >Gebruik het **gebied van het Onderzoek** om een onderzoek op de beschikbare gebieden in werking te stellen. Voor verdere informatie, verwijs naar [ deze sectie ](#sorting-a-list).
   >
   >Velden worden aangegeven met specifieke pictogrammen: SQL-velden, gekoppelde tabellen, berekende velden enzovoort. Voor elk geselecteerd veld wordt de beschrijving weergegeven onder de lijst met beschikbare velden. [Meer informatie](#configuring-lists).
   >
   >U kunt gegevens ook sorteren en filteren. Zie [deze sectie](../../platform/using/filtering-options.md).

1. Herhaal deze bewerking voor elke kolom die u wilt weergeven.
1. Gebruik de pijlen om de **vertoningsorde** te wijzigen. De hoogste kolom zal op de linkerzijde in de lijst van verslagen zijn.

   ![](assets/s_ncs_user_columns_order_down.png)

1. Indien nodig, kunt u op **[!UICONTROL Distribution of values]** klikken om de verdeling van waarden voor het geselecteerde veld in de huidige map weer te geven.

   ![](assets/s_ncs_user_configurelist_values.png)

1. Klik **[!UICONTROL OK]** om de configuratie te bevestigen en het resultaat te tonen.

### Een nieuwe kolom maken {#create-a-new-column}

U kunt nieuwe kolommen maken om extra velden in de lijst weer te geven. Dit doet u als volgt:

1. Klik op **[!UICONTROL Configure the list]** onder en rechts van de lijst.
1. Klik op **[!UICONTROL Add]** om een nieuw veld in de lijst weer te geven.

### Een kolom verwijderen {#remove-a-column}

U kunt een of meer kolommen in een lijst met records maskeren met behulp van **[!UICONTROL Configure list]** die zich onder en rechts van de lijst bevindt.

![](assets/s_ncs_user_configure_list.png)

Selecteer in het lijstconfiguratievenster de kolom die u wilt maskeren in de **[!UICONTROL Output columns]** -zone en klik op de knop Verwijderen.

![](assets/s_ncs_user_removecolumn_icon.png)

Herhaal deze bewerking voor elke kolom die u wilt maskeren. Klik **[!UICONTROL OK]** om de configuratie te bevestigen en het resultaat te tonen.

### Kolombreedte aanpassen {#adjust-column-width}

Wanneer een lijst actief is, d.w.z. minstens één lijn wordt geselecteerd, kunt u F9 gebruiken om de breedte van de kolommen aan te passen zodat alle kolommen op het scherm kunnen worden getoond.

### Gegevens weergeven in submappen {#display-sub-folders-records}

Lijsten kunnen worden weergegeven:

* Alleen de records in de geselecteerde map,
* Of de records in de geselecteerde map EN de bijbehorende submappen.

Als u van de ene weergavemodus naar de andere wilt schakelen, klikt u op **[!UICONTROL Display sub-levels]** op de werkbalk.

![](assets/s_ncs_user_display_children_icon.png)

## Een lijstconfiguratie opslaan {#saving-a-list-configuration}

De lijstconfiguraties worden bepaald plaatselijk op het werkstationniveau. Wanneer de lokale cache wordt gewist, worden lokale configuraties uitgeschakeld.

Standaard zijn de gedefinieerde weergaveparameters van toepassing op alle lijsten met het overeenkomende maptype. Wanneer u dus wijzigt hoe de lijst met ontvangers wordt weergegeven vanuit een map, wordt deze configuratie toegepast op alle andere mappen voor ontvangers.

Het is echter mogelijk meerdere configuraties op te slaan die op verschillende mappen van hetzelfde type moeten worden toegepast. De configuratie wordt opgeslagen met de eigenschappen van de map die de gegevens bevat en kan opnieuw worden toegepast.

Bijvoorbeeld, voor een leveringsomslag, is het mogelijk om de volgende vertoning te vormen:

![](assets/s_ncs_user_folder_save_config_1.png)

Volg onderstaande stappen om deze lijstconfiguratie op te slaan zodat deze opnieuw kan worden gebruikt:

1. Klik met de rechtermuisknop op de map met de weergegeven gegevens.
1. Selecteer **[!UICONTROL Properties]**.
1. Klik op **[!UICONTROL Advanced settings]** en geef een naam op in het veld **[!UICONTROL Configuration]** .

   ![](assets/s_ncs_user_folder_save_config_2.png)

1. Klik op **[!UICONTROL OK]** en vervolgens op **[!UICONTROL Save]** .

U kunt deze configuratie op een andere **omslag van de Levering {dan toepassen 1}:**

![](assets/s_ncs_user_folder_save_config_3.png)

Klik op **[!UICONTROL Save]** in het venster met mapeigenschappen. De lijstweergave wordt aangepast aan de opgegeven configuratie:

![](assets/s_ncs_user_folder_save_config_5.png)

## Een lijst exporteren {#exporting-a-list}

Als u gegevens uit een lijst wilt exporteren, moet u een exportassistent gebruiken. Als u deze wilt openen, selecteert u de elementen die u wilt exporteren in de lijst, klikt u met de rechtermuisknop en selecteert u **[!UICONTROL Export...]** .

Het gebruik van de invoer en de uitvoerfuncties wordt verklaard in [ Algemene invoer en uitvoer ](../../platform/using/about-generic-imports-exports.md).

>[!CAUTION]
>
>Elementen uit een lijst mogen niet worden geëxporteerd met de functie Kopiëren/Plakken.

## Een lijst sorteren {#sorting-a-list}

Lijsten kunnen veel gegevens bevatten. U kunt deze gegevens sorteren of eenvoudige of geavanceerde filters toepassen. Door te sorteren kunt u gegevens in oplopende of aflopende volgorde weergeven. Met filters kunt u alleen geselecteerde gegevens definiëren en combineren.

Klik op de kolomkop om oplopende of aflopende sortering toe te passen of om gegevenssortering te annuleren. De actieve sorteerstatus en sorteervolgorde worden aangegeven met een blauwe pijl vóór het kolomlabel. Een rood streepje vóór het kolomlabel betekent dat de sortering wordt toegepast op gegevens die uit de database zijn geïndexeerd. Deze sorteermethode wordt gebruikt om sorteertaken te optimaliseren.

U kunt ook sorteren configureren of sorteercriteria combineren. Hiervoor voert u de volgende stappen uit:

1. **[!UICONTROL Configure list]** onder en rechts van de lijst.

   ![](assets/s_ncs_user_configure_list.png)

1. Klik in het lijstconfiguratievenster op de tab **[!UICONTROL Sorting]** .
1. Selecteer de velden die u wilt sorteren en de sorteerrichting (oplopend of aflopend).

   ![](assets/s_ncs_user_configurelist_sort.png)

1. De sorteerprioriteit wordt gedefinieerd door de volgorde van de sorteerkolommen. Als u de prioriteit wilt wijzigen, gebruikt u de juiste pictogrammen om de volgorde van de kolommen te wijzigen.

   ![](assets/s_ncs_user_configurelist_move.png)

   De sorteerprioriteit heeft geen invloed op de weergave van de kolommen in de lijst.

1. Klik op **[!UICONTROL Ok]** om deze configuratie te bevestigen en het resultaat in de lijst weer te geven.

### Elementen zoeken {#running-a-search}

U kunt de beschikbare velden in een editor doorzoeken met het veld **[!UICONTROL Search]** boven de lijst met velden. De pers **gaat** op het toetsenbord binnen of doorbladert de lijst. De velden die overeenkomen met uw zoekopdracht, hebben vette labels.

>[!NOTE]
>
>U kunt filters maken om slechts enkele gegevens in een lijst weer te geven. [Meer informatie](../../platform/using/creating-filters.md).
