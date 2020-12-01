---
solution: Campaign Classic
product: campaign
title: Lijstupdate
description: Lijstupdate
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 49f3c123cb8e91b3a2a2a1eb6bd593a242b8bbfe
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 1%

---


# Lijstupdate{#list-update}

In een **List-updateactiviteit** wordt de populatie die in de overgang is opgegeven, opgeslagen in een lijst met ontvangers.

![](assets/s_user_segmentation_update_group.png)

U kunt de lijst selecteren in de lijst met bestaande groepen.

Deze kan ook worden gemaakt met behulp van de opties **[!UICONTROL Create the list if necessary (Computed name)]** en **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** . Met deze opties kunt u het label van uw keuze selecteren om een lijst te maken en later de map waarin deze wordt opgeslagen. Het label kan ook automatisch worden gegenereerd door dynamische velden of een script in te voegen. De verschillende dynamische velden zijn beschikbaar in het pop-upmenu rechts van het label.

![](assets/s_user_segmentation_update_list_calc.png)

Als de lijst al bestaat, worden ontvangers toegevoegd aan de bestaande inhoud, tenzij u de **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** optie inschakelt. In dit geval wordt de inhoud van de lijst vóór de update verwijderd.

Als u wilt dat de gemaakte of bijgewerkte lijst een andere tabel gebruikt dan de tabel voor ontvangers, controleert u de **[!UICONTROL Create or use a list with its own table]** optie.

Als u deze optie wilt gebruiken, moeten de desbetreffende tabellen zijn geconfigureerd in uw Adobe Campaign-exemplaar.

Over het algemeen betekent het opslaan van een doel in een lijst het einde van een workflow. Door gebrek, heeft de **[!UICONTROL List update]** activiteit daarom geen uitgaande overgang. Schakel de **[!UICONTROL Generate an outbound transition]** optie in om er een toe te voegen.

![](assets/do-not-localize/how-to-video.png) [Ontdek hoe u in video een lijst met ontvangers van de Verkenner kunt maken](#video)

## Voorbeeld: Lijstupdate {#example--list-update}

In het volgende voorbeeld volgt de activiteit van de lijstupdate een vraag die mannen meer dan 30 richt die in Frankrijk wonen. De lijst wordt eerst gemaakt op basis van de resultaten van de query. Het zal dan worden bijgewerkt telkens als het van het werkschema wordt gelanceerd. Het kan bijvoorbeeld regelmatig worden gebruikt voor gerichte promotieaanbiedingen voor campagnes.

1. Voeg **[!UICONTROL list update activity]** direct na een vraag toe dan open het omhoog om het uit te geven.

   Raadpleeg [Query](../../workflow/using/query.md)voor meer informatie over het maken van een query in een workflow.

1. U kunt een label voor de activiteit selecteren.
1. Selecteer de **[!UICONTROL Create the list if necessary (Calculated name)]** optie om te tonen dat de lijst zal worden gecreeerd zodra het eerste werkschema is uitgevoerd, dan bijgewerkt met de volgende uitvoeringen.
1. Selecteer de map waarin u de lijst wilt opslaan.
1. Voer een label in voor de lijst. U kunt dynamische velden invoegen om automatisch de naam te genereren uit de lijst. In dit voorbeeld heeft de lijst dezelfde naam als de query om de inhoud ervan gemakkelijk te kunnen identificeren.
1. Laat de **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** optie ingeschakeld om ontvangers te verwijderen die niet voldoen aan de doelcriteria en om de nieuwe criteria in de lijst in te voegen.
1. Also leave the **[!UICONTROL Create or use a list with its own table]** option checked.
1. Leave the **[!UICONTROL Generate an outbound transition]** option unchecked.
1. Click **[!UICONTROL Ok]** then start the workflow.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   De lijst met overeenkomende ontvangers wordt vervolgens gemaakt of bijgewerkt.

## Invoerparameters {#input-parameters}

* tableName
* schema

Hiermee wordt de populatie aangegeven die in de groep moet worden opgeslagen.

## Uitvoerparameters {#output-parameters}

* groupId: Groep-id.

## Video over zelfstudie {#video}

Deze video laat zien hoe u een lijst met ontvangers in de Verkenner kunt maken.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

Er zijn [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html)aanvullende Campaign Classic-instructievideo&#39;s beschikbaar.
