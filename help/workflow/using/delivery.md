---
product: campaign
title: Levering
description: Meer informatie over de workflowactiviteit van het leveringstype
feature: Workflows, Channels Activity
exl-id: 72fbdd1d-a105-4e9f-9e17-2e9d62d2bb80
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 1%

---

# Levering{#delivery}

![](../../assets/common.svg)

A **Aflevering**-type activiteit laat u een leveringsactie tot stand brengen. Deze kan worden samengesteld uit invoerelementen.

Om het te vormen, geef de activiteit uit en ga de leveringsopties in.

![](assets/edit_diffusion.png)

1. **Levering**

   U kunt:

   * Akte op de levering in de binnenkomende overgang wordt gespecificeerd die. Selecteer hiertoe de eerste optie van de optie **[!UICONTROL Delivery]** van het venster.

      Deze optie kan worden gebruikt wanneer een vorige werkstroomactiviteit reeds heeft gecreeerd of de levering gespecificeerd. Dit kan, zoals in het onderstaande voorbeeld, door een activiteit van het zelfde type worden gedaan die een uitgaande overgang heeft geproduceerd.

      In het volgende voorbeeld wordt de levering voor het eerst gemaakt. De populatie en de inhoud worden later gedefinieerd. Daarna, wordt de informatie voor deze drie elementen opnieuw ingegaan in een nieuwe leveringsactiviteit gebruikend de binnenkomende overgang zodat dit kan worden verzonden.

      ![](assets/specified_transition_option_exemple.png)

   * Selecteer de betrokken levering rechtstreeks. Selecteer hiervoor de optie **[!UICONTROL Explicit]** en selecteert u de levering in de vervolgkeuzelijst van het dialoogvenster **[!UICONTROL Delivery]** veld.

      In de lijst staan de onvoltooide leveringen in het dialoogvenster **Leveringen** map standaard. Als u andere campagnes wilt openen, klikt u op de knop **[!UICONTROL Select link]** pictogram.

      ![](assets/diffusion_edit_1.png)

      Selecteer de campagne in de vervolgkeuzelijst van het dialoogvenster **[!UICONTROL Folder]** veld of klik op **[!UICONTROL Display sub-levels]** om alle leveringen in submappen weer te geven:

      ![](assets/diffusion_edit_2.png)

      Nadat u de leveringsactie hebt geselecteerd, kunt u de inhoud weergeven door op de knop **[!UICONTROL Edit link]** pictogram.

   * Maak een script om de levering te berekenen. Selecteer hiervoor de optie **[!UICONTROL Computed by a script]** en voert u het script in. U kunt een invoervenster openen door te klikken op de knop **[!UICONTROL Edit...]** optie. In het volgende voorbeeld wordt de id van de levering hersteld:

      ![](assets/diffusion_edit_3.png)

   * Maak een nieuwe levering. Selecteer hiervoor de optie **[!UICONTROL New, created from a template]** en selecteer de leveringstemplate waarop de levering wordt gebaseerd.

      ![](assets/diffusion_edit_4.png)

      Klik op de knop **[!UICONTROL Select link]** om door de mappen te bladeren en op de knop **[!UICONTROL Edit link]** als u de inhoud van de geselecteerde sjabloon wilt weergeven.

1. **Ontvangers**

   Ontvangers kunnen door de binnenkomende gebeurtenissen worden opgegeven, bijvoorbeeld na het importeren van een bestand, of in de leveringsactie worden opgegeven. Ze kunnen ook in een of meer bestanden worden opgeslagen.

   ![](assets/diffusion_edit_5.png)

1. **Inhoud**

   De inhoud van het bericht kan in de levering of de binnenkomende gebeurtenis worden bepaald.

   ![](assets/diffusion_edit_6.png)

1. **Uit te voeren handeling**

   U kunt de levering maken, voorbereiden, starten, het doel schatten of een proefdruk verzenden.

   ![](assets/diffusion_edit_7.png)

   Selecteer het type actie dat moet worden uitgevoerd:

   * **[!UICONTROL Save]**: met deze optie kunt u de levering maken en opslaan. Het zal het niet analyseren of leveren.
   * **[!UICONTROL Estimate the target]**: met deze optie kunt u het leveringsdoel berekenen om het potentieel ervan te beoordelen ( eerste analysefase ) . Deze handeling is gelijk aan het selecteren van de **[!UICONTROL Estimate the population to be targeted]** en klikken **[!UICONTROL Analyze]** wanneer een levering naar het hoofddoel wordt verzonden via **Aflevering**.
   * **[!UICONTROL Prepare]**: met deze optie kunt u het volledige analyseproces uitvoeren ( doelberekening en inhoudsvoorbereiding ) . De levering wordt niet verzonden. Deze handeling is gelijk aan het selecteren van de **[!UICONTROL Deliver as soon as possible]** en klikken **[!UICONTROL Analyze]** wanneer een levering naar het hoofddoel wordt verzonden met **Aflevering**.
   * **[!UICONTROL Send a proof]**: met deze optie kunt u een bewijs van levering verzenden. Deze handeling is gelijk aan het klikken op de knop **[!UICONTROL Send a proof]** op de werkbalk van een levering met **Aflevering**
   * **[!UICONTROL Prepare and start]**: met deze optie wordt het volledige analyseproces gestart ( doelberekening en inhoudsvoorbereiding ) en wordt de levering verzonden . Deze handeling is gelijk aan klikken **[!UICONTROL Deliver as soon as possible]**, **[!UICONTROL Analyze]**, en **[!UICONTROL Confirm delivery]** optie bij het verzenden van een levering naar het hoofddoel met **Aflevering**.

   De **[!UICONTROL Act on a delivery]** Met de activiteiten die u verder in de workflow gebruikt, kunt u alle resterende stappen starten die vereist zijn voor het starten van de levering (doelberekening, inhoudsvoorbereiding, levering). Raadpleeg voor meer informatie hierover [Afleveringscontrole](delivery-control.md).

   De volgende opties zijn ook beschikbaar:

   * **[!UICONTROL Generate an outbound transition]**

      Creeert een uitgaande overgang die aan het eind van uitvoering zal worden geactiveerd. U kunt kiezen al dan niet om het doel van de uitgaande levering terug te winnen.

   * **[!UICONTROL Do not recover target]**

      Herstelt niet het doel van de uitgaande leveringsactie.

   * **[!UICONTROL Processing errors]**

      Zie [Afleveringscontrole](delivery-control.md).
   De **Script** kunt u de leveringsparameters wijzigen.

   ![](assets/edit_diffusion_fil_script.png)

## Voorbeeld: leveringsworkflow {#example--delivery-workflow}

Maak een nieuwe workflow en voeg activiteiten toe zoals in de onderstaande afbeelding wordt getoond:

![](assets/new-workflow-5.png)

Open de **Aflevering** en definieert de eigenschappen als volgt:

* In de **[!UICONTROL Delivery]** sectie, selecteert u **[!UICONTROL New, created from a template]** en selecteer een leveringssjabloon.
* In de **[!UICONTROL Recipients]** sectie, selecteert u **[!UICONTROL Specified in the delivery]**.
* In de **[!UICONTROL Action to execute]** de **[!UICONTROL Prepare]** optie.

![](assets/new-workflow-param-delivery.png)

Klikken **[!UICONTROL OK]** om het eigenschappenvenster te sluiten. U hebt net een activiteit gevormd die bestaat uit het creëren van en het voorbereiden van een nieuwe levering die op een leveringsmalplaatje wordt gebaseerd het waarvan doel binnen het zal worden gespecificeerd.

Open de **Goedkeuring** en definieert de eigenschappen als volgt:

1. In de **[!UICONTROL Assignment type]** selecteert u een groep waarin u bent geregistreerd. Als u verbinding hebt via de account &#39;admin&#39;, selecteert u de groep Beheer.
1. Voer vervolgens een titel in en voeg de volgende tekst in de berichttekst in:

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   Dit is een bericht dat een expressie bevat die in JavaScript is geschreven: **[!UICONTROL vars.recCount]** geeft het aantal ontvangers aan waarop de levering van de voorafgaande taak betrekking heeft. Raadpleeg voor meer informatie over JavaScript-expressies [JavaScript-scripts en -sjablonen](javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   De goedkeuringstaak wordt in detail beschreven in [Goedkeuring](approval.md).

## Invoerparameters {#input-parameters}

Identificatiecode van de levering, indien de **[!UICONTROL Specified in the transition]** is geselecteerd in het dialoogvenster **[!UICONTROL Delivery]** sectie.

* deliveryId
* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.

>[!NOTE]
>
>Deze parameter wordt alleen weergegeven als **[!UICONTROL Specified by inbound event(s)]** is geselecteerd in het dialoogvenster **[!UICONTROL Recipients]** sectie.

* filename

   Volledige naam van het bestand dat wordt gegenereerd als de **[!UICONTROL File(s) specified by inbound event(s)]** is geselecteerd in het dialoogvenster **[!UICONTROL Recipients]** sectie.

* contentId

   Inhoud-id als de **[!UICONTROL Specified by inbound events]** is geselecteerd in het dialoogvenster **[!UICONTROL Content]** sectie.

## Uitvoerparameters {#output-parameters}

* tableName
* schema
* recCount

Deze reeks van drie waarden identificeert het doel resulterend uit de levering. **[!UICONTROL tableName]** de naam van de tabel die de id&#39;s van het doel in zich bergt, **[!UICONTROL schema]** is het schema van de populatie (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de tabel.

De overgang verbonden aan het complement heeft de zelfde parameters.

>[!NOTE]
>
>Er zijn geen uitvoerparameters wanneer de **[!UICONTROL Do not recover target]** is geselecteerd.
