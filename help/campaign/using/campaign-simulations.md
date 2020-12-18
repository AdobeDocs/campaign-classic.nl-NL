---
solution: Campaign Classic
product: campaign
title: Campagnesimulaties
description: Campagnesimulaties
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 1%

---


# Campagnesimulaties{#campaign-simulations}

## Informatie over simulaties {#about-simulations}

Met Campagneoptimalisatie kunt u de efficiëntie van een campagneplan testen met behulp van simulaties. Zo kunt u het potentiële succes van een campagne meten: gegenereerde inkomsten, doelvolume op basis van de toegepaste typologische regels, enz.

Met simulatie kunt u het effect van leveringen controleren en vergelijken.

>[!NOTE]
>
>Leveringen die in de testmodus worden voorbereid, hebben geen invloed op elkaar, bijvoorbeeld wanneer een campagne wordt beoordeeld in gedistribueerde marketing, of zolang de leveringen niet in de voorlopige kalender zijn gepland.\
>Dit betekent dat druk- en capaciteitsregels alleen worden toegepast op leveringen in **[!UICONTROL Target estimation and message personalization]**-modus. Leveringen in **[!UICONTROL Estimation and approval of the provisional target]** en in **[!UICONTROL Target evaluation]** modus worden niet in aanmerking genomen.\
>De leveringswijze wordt gekozen op **[!UICONTROL Typology]** sublusje van de leveringseigenschappen.

![](assets/simu_campaign_select_delivery_mode.png)

## Een simulatie instellen {#setting-up-a-simulation}

### Een simulatie {#creating-a-simulation} maken

Voer de volgende stappen uit om een simulatie te maken:

1. Ga naar het **[!UICONTROL Campaigns]** universum, klik **[!UICONTROL More]** verbinding binnen **[!UICONTROL Create]** sectie en selecteer **[!UICONTROL Simulation]** optie.

   ![](assets/simu_campaign_opti_01.png)

1. Voer de sjabloon en de naam van de simulatie in. Klik **[!UICONTROL Save]** om de simulatie tot stand te brengen.

   ![](assets/simu_campaign_opti_02.png)

1. Klik op het tabblad **[!UICONTROL Edit]** om het te configureren.

   ![](assets/simu_campaign_opti_edit.png)

1. Geef op het tabblad **[!UICONTROL Scope]** de leveringen op die u voor deze simulatie wilt overwegen. Om dit te doen, klik **[!UICONTROL Add]** knoop en specificeer de wijze van de leveringsselectie om rekening mee te houden.

   ![](assets/simu_campaign_opti_edit_scope.png)

   U kunt elke levering één voor één selecteren of ze sorteren op campagne, programma of plan.

   >[!NOTE]
   >
   >Als u leveringen selecteert via een plan, programma of campagne, kan Adobe Campaign de lijst met leveringen automatisch vernieuwen om hiermee rekening te houden wanneer een simulatie wordt gestart. Om dit te doen, controleer de **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** optie.
   >  
   >Als u dit niet doet, zullen om het even welke leveringen die niet beschikbaar in het plan, het programma, of de campagne zijn wanneer de simulatie wordt gecreeerd niet in aanmerking worden genomen: leveringen die later worden toegevoegd, worden genegeerd.

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. Selecteer de elementen die u in het simulatiebereik wilt opnemen. Selecteer indien nodig meerdere elementen met de toetsen SHIFT en CTRL.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Klik **[!UICONTROL Finish]** om de selectie goed te keuren.

   U kunt geselecteerde leveringen en leveringen die bij plannen, programma&#39;s of campagnes horen, handmatig combineren.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   Indien nodig, kunt u een dynamische voorwaarde via de **[!UICONTROL Edit the dynamic condition...]** verbinding gebruiken.

   Klik **[!UICONTROL Save]** om deze configuratie goed te keuren.

   >[!NOTE]
   >
   >Alleen leveringen waarvan het doel is berekend, worden in aanmerking genomen bij de berekening van de simulaties (statussen: **Doel gereed** of **Klaar om te leveren**).

1. Selecteer op het tabblad **[!UICONTROL Calculations]** bijvoorbeeld een analysedimensie, zoals het ontvangende schema.

   ![](assets/simu_campaign_opti_dimension.png)

1. Vervolgens kunt u expressies toevoegen.

   ![](assets/simu_campaign_opti_dimension_02.png)

### Instellingen voor uitvoering {#execution-settings}

Op het tabblad **[!UICONTROL General]** van de simulatie kunt u uitvoeringsinstellingen invoeren:

* Met de optie **[!UICONTROL Schedule execution for down-time]** wordt de simulatie-opstart uitgesteld tot een minder drukke tijdsperiode, op basis van het gekozen prioriteitsniveau. De simulaties gebruiken significante gegevensbestandmiddelen, dat is waarom de niet-urgente simulaties zouden moeten worden gepland om bij nacht, bijvoorbeeld te lopen.
* **[!UICONTROL Priority]** is het niveau dat op de simulatie wordt toegepast om zijn teweegbrengen uit te stellen.
* **[!UICONTROL Save SQL queries in the log]**. Met SQL-logboeken kunt u een simulatie diagnosticeren als deze eindigt met fouten. Ze kunnen u ook helpen te achterhalen waarom een simulatie te langzaam is. Deze berichten worden weergegeven na de simulatie op het subtabblad **[!UICONTROL SQL logs]** van het tabblad **[!UICONTROL Audit]**.

## Een simulatie uitvoeren {#executing-a-simulation}

### Een simulatie {#starting-a-simulation} starten

Zodra het simulatiewerkingsgebied wordt bepaald, kunt u het uitvoeren.

Open hiertoe het dashboard voor de simulatie en klik op **[!UICONTROL Start simulation]**.

![](assets/simu_campaign_opti_start.png)

Zodra de uitvoering volledig is, open de simulatie en klik **[!UICONTROL Results]** lusje om de doelstellingen te bekijken die voor elke levering worden berekend.

![](assets/simu_campaign_opti_results.png)

1. Het subtabblad **[!UICONTROL Deliveries]** bevat een lijst met alle leveringen waarmee rekening is gehouden in de simulatie. Er zijn twee punten:

   * De **[!UICONTROL Initial count]** is het doel zoals het tijdens zijn raming in de levering werd berekend.
   * **[!UICONTROL Final count]** is het aantal ontvangers geteld na simulatie.

      Het verschil tussen aanvankelijke en definitieve tellingen wijst op de toepassing van de diverse regels of de filters die voorafgaand aan de simulatie worden gevormd.

      Als u meer wilt weten over deze berekening, bewerkt u het subtabblad **[!UICONTROL Exclusions]**.

1. Met het subtabblad **[!UICONTROL Exclusions]** kunt u de uitsplitsing naar uitsluiting weergeven.

   ![](assets/simu_campaign_opti_14.png)

1. De **[!UICONTROL Alerts]** subtab groepeert alle waarschuwingsberichten die tijdens de simulatie worden gegenereerd. Waarschuwingsberichten kunnen worden verzonden in geval van capaciteitsoverbelasting (als het aantal beoogde ontvangers de ingestelde capaciteit overschrijdt, bijvoorbeeld).
1. Met het subtabblad **[!UICONTROL Exploration of the exclusions]** kunt u een tabel voor resultaatanalyse maken. De gebruiker moet variabelen in de abscis/ordinates-assen aangeven.

   Voor een voorbeeld van de verwezenlijking van de analystabel, verwijs naar het eind van [het Verkennen van resultaten](#exploring-results).

### Resultaten weergeven {#viewing-results}

#### Audit {#audit}

Met het tabblad **[!UICONTROL Audit]** kunt u de uitvoering van de simulatie controleren. Het subtabblad **[!UICONTROL SQL Logs]** is handig voor ervaren gebruikers. Er worden uitvoerlogbestanden in SQL-indeling weergegeven. Deze logboeken worden alleen weergegeven als de optie **[!UICONTROL Save SQL queries in the log]** is geselecteerd op het tabblad **[!UICONTROL General]** voordat de simulatie wordt uitgevoerd.

![](assets/simu_campaign_opti_11.png)

#### Resultaten verkennen {#exploring-results}

Met het subtabblad **[!UICONTROL Exploration of the exclusions]** kunt u de gegevens analyseren die het resultaat zijn van een simulatie.

Beschrijvende analyse wordt beschreven in [deze sectie](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## Resultaten van een simulatie {#results-of-a-simulation}

De indicatoren in **[!UICONTROL Log]** en **[!UICONTROL Results]** lusjes verstrekken een eerste overzicht van simulatieresultaten. Open het tabblad **[!UICONTROL Reports]** voor een gedetailleerdere weergave van de resultaten.

### Rapporten {#reports}

Om het resultaat van een simulatie te analyseren, geef zijn rapporten uit: zij tonen uitsluitingen en oorzaken .

De volgende rapporten worden standaard geleverd:

* **[!UICONTROL Detail of simulation exclusions]** : dit verslag bevat een gedetailleerd overzicht van de oorzaken van uitsluiting voor alle betrokken leveringen .
* **[!UICONTROL Simulation summary]** : in dit verslag wordt aangegeven welke bevolkingsgroepen gedurende de verschillende leveringen van de simulatie zijn uitgesloten .
* **[!UICONTROL Summary of exclusions linked to the simulation]** : dit verslag bevat een overzicht van de uitsluitingen die door de simulatie worden veroorzaakt , samen met de toegepaste typologische regel en een grafiek met de uitsluitingsverhouding per regel .

>[!NOTE]
>
>U kunt nieuwe rapporten creëren en hen toevoegen aan aangeboden degenen. Raadpleeg [deze sectie](../../reporting/using/about-adobe-campaign-reporting-tools.md) voor meer informatie.

Klik op de koppeling **[!UICONTROL Reports]** van de doelsimulatie via het dashboard om rapporten te openen.

![](assets/campaign_opt_reporting_edit_from_board.png)

U kunt rapporten ook uitgeven gebruikend de **[!UICONTROL Reports]** verbinding toegankelijk van het simulatiedashboard.

### Simulaties vergelijken {#comparing-simulations-}

Telkens wanneer een simulatie wordt uitgevoerd, vervangt het resultaat om het even welke vorige resultaten: u kunt de resultaten van de ene uitvoering niet weergeven en vergelijken.

Om resultaten te vergelijken, moet u rapporten gebruiken. In Adobe Campaign kunt u zelfs een rapportgeschiedenis opslaan om deze later opnieuw te bekijken. Deze geschiedenis wordt gedurende de levenscyclus van de simulaties bewaard.

**Voorbeeld:**

1. Creeer een simulatie op een levering welke typologie **A** wordt toegepast op.
1. Bewerk op het tabblad **[!UICONTROL Reports]** een van de beschikbare rapporten, zoals bijvoorbeeld **[!UICONTROL Detail of simulation exclusions]**.
1. Klik in de rechterbovensectie van het rapport op het pictogram om een nieuwe geschiedenis te maken.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. Sluit de simulatie en verander de configuratie van typologie **A**.
1. Voer opnieuw de simulatie uit en vergelijk het resultaat met dat in het rapport wordt getoond waarvoor een geschiedenis werd gecreeerd.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   U kunt zoveel rapporthistorie opslaan als nodig is.

### Assen {#reporting-axes} rapporteren

Met het tabblad **[!UICONTROL Calculations]** kunt u rapportassen op het doel definiëren. Deze assen worden tijdens resultaatanalyse gebruikt (zie [Resultaten verkennen](#exploring-results)).

>[!NOTE]
>
>Wij adviseren bepalende berekeningsassen in de simulatiesjablonen eerder dan individueel voor elke simulatie.\
>Simulatiesjablonen worden opgeslagen in het knooppunt **[!UICONTROL Resources > Templates > Simulation templates]** van de Adobe Campaign-structuur.

**Voorbeeld:**

In het onderstaande voorbeeld willen we een extra rapportas maken op basis van de status van de ontvangers (&quot;Klant&quot;, &quot;Vooruitziend&quot; of geen).

1. Als u een rapportas wilt definiëren, selecteert u de tabel met de gegevens die in het veld **[!UICONTROL Analysis dimension]** moeten worden verwerkt. Deze informatie is verplicht.
1. Hier, willen wij het gebied van het Segment van de ontvankelijke lijst selecteren.

   ![](assets/simu_campaign_opti_09.png)

1. De volgende opties zijn beschikbaar:

   * **[!UICONTROL Generate target overlap statistics]** laat u alle overlappende statistieken in het simulatierapport terugkrijgen. Overlappingen zijn ontvangers die zijn aangewezen in ten minste twee leveringen binnen één simulatie.

      >[!IMPORTANT]
      >
      >Als u deze optie selecteert, neemt de uitvoeringstijd van de simulatie aanzienlijk toe.

   * **[!UICONTROL Keep the simulation work table]** Hiermee kunt u simulatietraces behouden.

      >[!IMPORTANT]
      >
      >Voor het automatisch opslaan van deze tabellen is een aanzienlijke opslagcapaciteit vereist: zorg ervoor dat de database groot genoeg is.

Wanneer de simulatieresultaten worden weergegeven, wordt de informatie over de geselecteerde expressie weergegeven op het subtabblad **[!UICONTROL Overlaps]**.

De doeloverlappingen van de levering geven de beoogde ontvangers aan in ten minste twee leveringen van een simulatie.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>Dit subtabblad wordt alleen weergegeven als de optie **[!UICONTROL Generate target recovery statistics]** is ingeschakeld.

De informatie over rapportageassen kan worden verwerkt in uitsluitingsanalyserapporten die worden gemaakt op het subtabblad **[!UICONTROL Exploring exclusions]**. Raadpleeg [Resultaten verkennen](#exploring-results) voor meer informatie.
