---
product: campaign
title: Levenscyclus van gegevens
description: Meer informatie over de levenscyclus van gegevens in workflows
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: 366acc1e-d769-4053-9fa1-f47182627c07
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 4%

---

# Levenscyclus van gegevens {#data-life-cycle}



## Werktabel {#work-table}

In werkstromen, worden de gegevens die van één activiteit aan een andere worden vervoerd opgeslagen in een tijdelijke het werklijst.

Deze gegevens kunnen worden weergegeven en geanalyseerd door met de rechtermuisknop op de juiste overgang te klikken.

![](assets/wf-right-click-analyze.png)

Selecteer hiertoe het relevante menu:

* Het doel weergeven

  Dit menu toont de beschikbare gegevens over de doelbevolking evenals de structuur van de het werklijst (**[!UICONTROL Schema]** tabel).

  ![](assets/wf-right-click-display.png)

  Voor meer op dit, verwijs naar [ Worktables en werkschemaschema ](monitoring-workflow-execution.md#worktables-and-workflow-schema).

* Het doel analyseren

  Dit menu laat u tot de beschrijvende analysemedewerker toegang hebben die u statistieken en rapporten over de overgangsgegevens laat produceren.

  Raadpleeg deze [sectie](../../reporting/using/using-the-descriptive-analysis-wizard.md) voor meer informatie.

De doelgegevens worden gewist terwijl de workflow wordt uitgevoerd. Alleen de laatste werktabel is toegankelijk. U kunt de workflow zodanig configureren dat alle werktabellen toegankelijk blijven: controleer de optie **[!UICONTROL Keep the result of interim populations between two executions]** in de workfloweigenschappen.

Wij raden u echter aan deze optie niet te activeren als er grote hoeveelheden gegevens zijn.

![](assets/wf-purge-data-option.png)

## Targetgegevens {#target-data}

De gegevens die in de werktabel van de workflow zijn opgeslagen, zijn toegankelijk in de velden voor personalisatie.

Hiermee kunt u gegevens gebruiken die via een lijst zijn verzameld of die zijn gebaseerd op antwoorden op een enquête in een levering. Hiervoor gebruikt u de volgende syntaxis:

```
%= targetData.FIELD %
```

Aanmaakelementen van het type **[!UICONTROL Target extension]** (targetData) zijn niet beschikbaar voor workflows als doel. Het leveringsdoel moet in het werkschema worden gebouwd en in de binnenkomende overgang van de levering worden gespecificeerd.

Als u leveringsproeven wilt tot stand brengen, moet het proefdrukdoel op de **[!UICONTROL Address substitution]** wijze worden gebouwd zodat de verpersoonlijkingsgegevens kunnen worden ingegaan. Raadpleeg deze [sectie](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof) voor meer informatie.

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

1. Configureer het type van **[!UICONTROL Enrichment]** om de verzamelde gegevens te combineren met de gegevens die al in de Adobe Campaign-database staan.

   Hier is de afstemmingssleutel het rekeningnummer:

   ![](assets/wf-targetdata-sample-3.png)

1. Configureer vervolgens de **[!UICONTROL Delivery]** : deze wordt gemaakt op basis van een sjabloon en de ontvangers worden opgegeven door de binnenkomende overgang.

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >Alleen gegevens in de overgang mogen worden gebruikt om de levering aan te passen. **targetData** typeverpersoonlijkingsgebieden zijn slechts beschikbaar voor de binnenkomende bevolking van de **[!UICONTROL Delivery]** activiteit.

1. In het leveringsmalplaatje, gebruik de gebieden die in het werkschema worden verzameld.

   Voeg daartoe **[!UICONTROL Target extension]** -typefilms in.

   ![](assets/wf-targetdata-sample-5.png)

   Hier willen we het favoriete muziekgenre en mediatype (CD of DVD) van de klant invoegen, zoals vermeld in het bestand dat tijdens de workflow wordt verzameld.

   Als plus gaan we een coupon toevoegen voor houders van een getrouwde kaart, dat wil zeggen ontvangers voor wie de waarde van de &#39;Kaart&#39; gelijk is aan 1.

   ![](assets/wf-targetdata-sample-6.png)

   Gegevens van het type **[!UICONTROL Target extension]** (targetData) worden in leveringen ingevoegd met dezelfde kenmerken als alle verpersoonlijkingsvelden. Ze kunnen ook worden gebruikt in het onderwerp, koppelingslabels of de koppelingen zelf.

   Berichten die aan verzamelde ontvangers worden gericht zullen de volgende gegevens bevatten:

   ![](assets/wf-targetdata-sample-7.png)
