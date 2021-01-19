---
solution: Campaign Classic
product: campaign
title: Content bewerken
description: Content bewerken
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 43037b2b6b4e3b42f4b666d85a664b9fb117a015
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 1%

---


# Content bewerken{#editing-content}

## Een zichtbaarheidsvoorwaarde {#defining-a-visibility-condition} definiëren

U kunt een zichtbaarheidsvoorwaarde opgeven voor een webpagina-element: dit element is alleen zichtbaar als aan de voorwaarde wordt voldaan .

Als u een zichtbaarheidsvoorwaarde wilt toevoegen, selecteert u een blok en voert u de voorwaarde in het veld **[!UICONTROL Visibility condition]** in met de expressie-editor.

![](assets/dce_add_condition.png)

>[!NOTE]
>
>Geavanceerde bewerkingen van expressies worden weergegeven op [deze pagina](../../platform/using/defining-filter-conditions.md#list-of-functions).

![](assets/dce_popup_visibilitycondition.png)

Deze voorwaarden passen de syntaxis van de XTK-expressie toe (bijvoorbeeld **ctx.receiver.@email!= &quot;&quot;** of **ctx.ontvanger.@status=&quot;0&quot;**). Standaard zijn alle velden zichtbaar.

>[!NOTE]
>
>Niet-zichtbare dynamische blokken, zoals vervolgkeuzemenu&#39;s, kunnen niet worden bewerkt.

## Rand en achtergrond {#adding-a-border-and-background} toevoegen

U kunt een **border** aan een geselecteerd blok toevoegen. De randen worden gedefinieerd met behulp van drie opties: stijl, grootte en kleur.

![](assets/dce_popup_border.png)

U kunt ook een **achtergrondkleur** bepalen door een kleur van de kleurengrafiek te selecteren.

![](assets/dce_popup_background.png)

## Formulieren bewerken {#editing-forms}

### De gegevenseigenschappen van een formulier wijzigen {#changing-the-data-properties-for-a-form}

U kunt databasevelden koppelen aan invoerzone, keuzerondje of keuzelijstblokken.

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>De standaardgebieden zijn die in het schema van de de toepassingsopslag van het Web.

Met de invoerzone **field** kunt u een databaseveld selecteren dat u wilt koppelen aan het formulierveld.

Standaard worden velden aangeboden in de tabel **nms:ontvanger**.

![](assets/dce_field_selection.png)

Met de optie **Vereist veld** kunt u de goedkeuring van de pagina alleen autoriseren als de gebruiker het veld heeft ingevuld. Als een vereist veld niet is ingevuld, wordt een foutbericht weergegeven.

Voor keuzerondjes en selectievakjes is **aanvullende configuratie vereist**.

Als de gebruikte sjabloon standaard geen waarde bevat, moet u deze in de editor voltooien.

Dit doet u als volgt:

* Klik op het pictogram **[!UICONTROL Edit]**.

   ![](assets/dce_sidebar_options.png)

* Voer de opgegeven lijstwaarde (gedefinieerd door het geselecteerde veld) in het veld **[!UICONTROL Value]** in.

   ![](assets/dce_sidebar_completeoptionradio.png)

### Formuliervelden {#modifying-form-fields} wijzigen

Formuliervelden zoals keuzerondjes, invoerzones, vervolgkeuzelijsten, enz. kan worden gewijzigd op basis van de werkbalken.

Dit betekent dat u:

* Verwijder het blok met de formuliervelden met het pictogram **[!UICONTROL Delete]**.
* Dupliceer het geselecteerde veld door een nieuw blok te maken met het pictogram **[!UICONTROL Duplicate]**.
* Bewerk het venster **[!UICONTROL Form data]** om een databaseveld aan de formulierzone te koppelen met het pictogram **[!UICONTROL Edit]**.

   ![](assets/dce_toolbar_formblock_edition.png)

## Een handeling toevoegen aan een knop {#adding-an-action-to-a-button}

Wanneer de gebruiker op een knop klikt, kunt u een bijbehorende actie definiëren. Selecteer hiertoe de uit te voeren actie in de vervolgkeuzelijst.

![](assets/dce_sidebar_button.png)

De beschikbare acties zijn als volgt:

* **[!UICONTROL Refresh]** : Hiermee vernieuwt u de huidige pagina.
* **[!UICONTROL Next page]** : leidt tot een verbinding aan de volgende pagina in de toepassing van het Web.
* **[!UICONTROL Previous page]** : maakt een koppeling naar de vorige pagina in de webtoepassing.

>[!NOTE]
>
>Met de waarde **[!UICONTROL None]** kunt u de knop niet activeren.

U kunt het label dat aan de knop is gekoppeld, wijzigen in het desbetreffende veld.

## Een koppeling {#adding-a-link} toevoegen

U kunt een koppeling invoegen in elk pagina-element: afbeelding, woord, groep woorden, tekstblok, enz.

Selecteer hiertoe het element en gebruik vervolgens het eerste pictogram in het pop-upmenu.

![](assets/dce_insertlink_icon.png)

Met dit pictogram hebt u toegang tot alle beschikbare typen koppelingen.

![](assets/dce_insertlink_menu.png)

U kunt alleen aanpassingsblokken en velden invoegen in tekstblokken.

>[!NOTE]
>
>Voor elk type verbinding, kunt u de openingswijze vormen: Selecteer het doelvenster in de vervolgkeuzelijst **Doel**. Deze waarde komt overeen met de HTML-tag **`<target>`**.
>
>De lijst van beschikbare **target** is als volgt:
>
>* Overige (IFrame)
>* Bovenste venster (_boven)
>* Bovenliggend venster (_bovenliggend)
>* Nieuw venster (_leeg)
>* Huidig venster (_zelf)
>* Standaardbrowsergedrag

>



### Koppeling maken naar een URL {#link-to-a-url}

Met de optie **Koppeling naar een externe URL** kunt u elke URL vanuit de broninhoud openen.

![](assets/dce_toolbar_imgblock_externallink.png)

Voer het koppelingsadres in kwestie in het veld **URL** in. Het veld URL moet worden ingevoerd als: **https://www.myURL.com**.

### Koppeling maken naar een webtoepassing {#link-to-a-web-application}

Met de optie **Koppeling naar een webtoepassing** hebt u toegang tot een Adobe Campaign-webtoepassing.

![](assets/dce_toolbar_imgblock_appweb.png)

Selecteer de toepassing van het Web van het overeenkomstige gebied.

De lijst van voorgestelde toepassingen van het Web beantwoordt aan de beschikbare toepassingen in **[!UICONTROL Resources > Online > Web Applications]** knoop.

### Koppeling maken naar een handeling {#link-to-an-action}

De **Verbinding die een actie** optie bepaalt laat u een actie vormen wanneer het klikken van een bronelement.

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
>
>Beschikbare acties worden beschreven in de sectie [Een handeling toevoegen aan een knop](#adding-an-action-to-a-button).

### Een koppeling {#delete-a-link} verwijderen

Wanneer een koppeling is ingevoegd, bevat de werkbalk twee nieuwe pictogrammen: **Koppeling bewerken** en **De koppeling** verbreken, zodat u kunt communiceren met de gemaakte koppeling.

* **[!UICONTROL Edit link]** Hiermee kunt u een venster weergeven met alle parameters van de koppeling.
* **[!UICONTROL Break the link]** Hiermee kunt u na bevestiging de koppeling en alle bijbehorende parameters verwijderen.

>[!NOTE]
>
>Als de koppeling wordt verwijderd, blijft de inhoud behouden.

## Lettertypekenmerken wijzigen {#changing-font-attributes}

Wanneer u een tekstelement selecteert, kunt u lettertypekenmerken (stijl, opmaak) wijzigen.

![](assets/dce_toolbar_txt.png)

De beschikbare opties zijn als volgt:

* **Lettertype vergroten** : Hiermee vergroot u de grootte van de geselecteerde tekst (toevoegen  `<span style="font size:">`)
* **Verminder** lettertype: Hiermee verkleint u de grootte van de geselecteerde tekst (toevoegen  `<span style="font size:">`)
* **** Boldicon: Hiermee maakt u geselecteerde tekst vet (tekstomloop met  `<strong> </strong>` label)
* **Cursief** pictogram: maakt geselecteerde tekst cursief (tekstomloop met   `<em> </em>` label)
* **** Onderstrepingspictogram: maakt geselecteerde tekst onderstreept (laat tekst omlopen met de  `<span style="text-decoration: underline;">` tag)
* **Links** uitlijnen: Hiermee lijnt u tekst links van het geselecteerde blok uit (add style=&quot;text-align: left;&quot;)
* **** Middenpictogram: centreert de tekst voor het geselecteerde blok (voeg style=&quot;text-align toe: middelpunt;&quot;)
* **Rechts uitlijnen** : Hiermee lijnt u tekst rechts van het geselecteerde blok uit (add style=&quot;text-align: right;&quot;)
* **Wijzig het achtergrondkleurpictogram** : Hiermee kunt u de achtergrondkleur van het geselecteerde blok wijzigen (stijl=&quot;background-color: rgba(170, 86, 255, 0,87)
* **Kleurpictogram** tekst wijzigen: Hiermee kunt u de tekstkleur van het geselecteerde blok of alleen de geselecteerde tekst wijzigen (`<span style="color: #CODE">`)

>[!NOTE]
>
>* **Pictogram** Verwijderen: Hiermee verwijdert u het blok en alle inhoud ervan.
   >
   >
* **Pictogram** Dupliceren: dupliceert het blok evenals alle stijlen met betrekking tot het blok.


## Afbeeldingen en animaties beheren {#managing-images-and-animations}

Met de Digital Content Editor kunt u aan **elk type afbeelding** werken dat compatibel is met browsers.

>[!CAUTION]
>
>U mag externe bestanden niet oproepen in een **script**-tag van de HTML-pagina. Deze bestanden worden niet geïmporteerd op de Adobe Campaign-server.

### Een afbeelding {#adding---deleting---duplicating-an-image} toevoegen/verwijderen/dupliceren

Als u een afbeelding wilt invoegen, selecteert u een blok Afbeeldingstype en klikt u op het pictogram **Afbeelding**.

![](assets/dce_insert_image.png)

Selecteer een afbeeldingsbestand dat lokaal is opgeslagen.

![](assets/dce_popup_imgupload.png)

Met het pictogram **Delete** verwijdert u de tag ![]() die de afbeelding bevat.

Met het pictogram **Dupliceren** worden de tag ![]() en de inhoud ervan gedupliceerd.

>[!CAUTION]
>
>Wanneer u een afbeelding dupliceert, worden de id&#39;s voor de nieuwe afbeelding verwijderd.

### Afbeeldingseigenschappen {#editing-image-properties} bewerken

Wanneer u een blok selecteert dat een afbeelding bevat, hebt u toegang tot de volgende eigenschappen:

* **Met** Bijschrift kunt u het bijschrift definiëren dat is gekoppeld aan de afbeelding (komt overeen met het  **** kenmerk altHTML).
* **Met** Dimensionslets kunt u de afbeeldingsgrootte opgeven, in pixels.

   ![](assets/dce_popup_imgsize.png)

## Aanpassingsinhoud toevoegen {#adding-personalization-content}

### Een personalisatieveld invoegen {#inserting-a-personalization-field}

Met de optie **Personalisatieveld** voor het invoegpictogram kunt u een databaseveld toevoegen aan de inhoud, zoals de naam van de ontvanger. Deze optie is alleen beschikbaar voor tekstblokken.

![](assets/dce_toolbar_textblock_persofield.png)

Standaard zijn de velden die worden aangeboden afkomstig uit de tabel **[!UICONTROL Recipient]**. Indien nodig, geef de de toepassingseigenschappen van het Web uit om een andere lijst te selecteren.

De veldnaam wordt in de editor weergegeven en geel gemarkeerd. Deze wordt vervangen door het profiel van de beoogde ontvanger wanneer de personalisatie wordt gegenereerd (bijvoorbeeld wanneer een voorvertoning van een landingspagina wordt weergegeven).

Een voorbeeld wordt voorgesteld in [Het opnemen van een verpersoonlijkingsgebied](../../web/using/creating-a-landing-page.md#inserting-a-personalization-field) sectie.

### Een aanpassingsblok {#inserting-a-personalization-block} invoegen

Met de optie **Personaliseringsblok** kunt u dynamische en gepersonaliseerde blokken in de inhoud invoegen. U kunt bijvoorbeeld een logo of een begroetingsbericht toevoegen. Deze optie is niet beschikbaar voor tekstblokken.

![](assets/dce_toolbar_textblock_persoblock.png)

Zodra opgenomen, verschijnt de naam van het verpersoonlijkingsblok in de redacteur, die in geel wordt benadrukt. Het wordt automatisch aangepast aan het ontvankelijke profiel wanneer de verpersoonlijking wordt geproduceerd.

Voor meer op ingebouwde verpersoonlijkingsblokken en hoe te om de blokken van de douaneverpersoonlijking te bepalen, verwijs naar [deze pagina](../../delivery/using/personalization-blocks.md).
