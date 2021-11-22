---
product: campaign
title: Levenscyclus van gegevens
description: Meer informatie over de levenscyclus van gegevens in workflows
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 366acc1e-d769-4053-9fa1-f47182627c07
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 4%

---

# Levenscyclus van gegevens {#data-life-cycle}

![](../../assets/common.svg)

## Werktabel {#work-table}

In werkstromen, worden de gegevens die van één activiteit aan een andere worden vervoerd opgeslagen in een tijdelijke het werklijst.

Deze gegevens kunnen worden weergegeven en geanalyseerd door met de rechtermuisknop op de juiste overgang te klikken.

![](assets/wf-right-click-analyze.png)

Selecteer hiertoe het relevante menu:

* Het doel weergeven

   Dit menu toont de beschikbare gegevens over de doelpopulatie evenals de structuur van de het werklijst (**[!UICONTROL Schema]** ).

   ![](assets/wf-right-click-display.png)

   Raadpleeg voor meer informatie hierover [Worktables and workflow schema](monitoring-workflow-execution.md#worktables-and-workflow-schema).

* Het doel analyseren

   In dit menu hebt u toegang tot de wizard voor beschrijvende analyse, waarmee u statistieken en rapporten over de overgangsgegevens kunt produceren.

   Raadpleeg deze [sectie](../../reporting/using/using-the-descriptive-analysis-wizard.md) voor meer informatie.

De doelgegevens worden gewist terwijl de workflow wordt uitgevoerd. Alleen de laatste werktabel is toegankelijk. U kunt het werkschema vormen zodat alle het werklijsten toegankelijk blijven: controleren **[!UICONTROL Keep the result of interim populations between two executions]** in de workfloweigenschappen.

Wij raden u echter aan deze optie niet te activeren als er grote hoeveelheden gegevens zijn.

![](assets/wf-purge-data-option.png)

## Targetgegevens {#target-data}

De gegevens die in de werktabel van de workflow zijn opgeslagen, zijn toegankelijk in de velden voor personalisatie.

Hiermee kunt u gegevens gebruiken die via een lijst zijn verzameld of die zijn gebaseerd op antwoorden op een enquête in een levering. Hiervoor gebruikt u de volgende syntaxis:

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** (targetData) type verpersoonlijkingselementen zijn niet beschikbaar voor het richten van werkschema&#39;s. Het leveringsdoel moet in het werkschema worden gebouwd en in de binnenkomende overgang van de levering worden gespecificeerd.

Als u proefdrukken voor levering wilt maken, moet het proefdrukdoel worden gebaseerd op de **[!UICONTROL Address substitution]** zodat de verpersoonlijkingsgegevens kunnen worden ingevoerd. Raadpleeg deze [sectie](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof) voor meer informatie.

In het volgende voorbeeld, gaan wij een lijst van informatie over klanten verzamelen, die in een gepersonaliseerd e-mail moet worden gebruikt.

Voer de volgende stappen uit:

1. Maak een workflow voor het verzamelen van informatie, pas deze aan met de gegevens die al in de database staan en start vervolgens een levering.

   ![](assets/wf-targetdata-sample-1.png)

   In ons voorbeeld ziet de bestandsinhoud er als volgt uit:

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   Voer de volgende stappen uit om het bestand te laden:

   ![](assets/wf-targetdata-sample-2.png)

1. Configureer de **[!UICONTROL Enrichment]** Typ activiteit om de verzamelde gegevens te combineren met de gegevens die al in de Adobe Campaign-database staan.

   Hier is de afstemmingssleutel het rekeningnummer:

   ![](assets/wf-targetdata-sample-3.png)

1. Dan vorm **[!UICONTROL Delivery]**: het wordt gecreeerd gebaseerd op een malplaatje, en de ontvangers worden gespecificeerd door de binnenkomende overgang.

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >Alleen gegevens in de overgang mogen worden gebruikt om de levering aan te passen. **targetData** de gebieden van de typeverpersoonlijking zijn slechts beschikbaar voor de binnenkomende bevolking van **[!UICONTROL Delivery]** activiteit.

1. In het leveringsmalplaatje, gebruik de gebieden die in het werkschema worden verzameld.

   Om dit te doen, voeg **[!UICONTROL Target extension]** type verpersoonlijkingsgebieden.

   ![](assets/wf-targetdata-sample-5.png)

   Hier willen we het favoriete muziekgenre en mediatype (CD of DVD) van de klant invoegen, zoals vermeld in het bestand dat tijdens de workflow wordt verzameld.

   Als plus gaan we een coupon toevoegen voor houders van een loyaliteitskaart, dat wil zeggen ontvangers voor wie de waarde van de &#39;Kaart&#39; gelijk is aan 1.

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** (targetData) typegegevens worden opgenomen in leveringen gebruikend de zelfde kenmerken zoals alle verpersoonlijkingsgebieden. Ze kunnen ook worden gebruikt in het onderwerp, koppelingslabels of de koppelingen zelf.

   Berichten die aan verzamelde ontvangers worden gericht zullen de volgende gegevens bevatten:

   ![](assets/wf-targetdata-sample-7.png)
