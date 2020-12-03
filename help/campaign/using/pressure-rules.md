---
solution: Campaign Classic
product: campaign
title: Drukregels
description: Drukregels
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '3253'
ht-degree: 4%

---


# Drukregels{#pressure-rules}

## Informatie over moeheid bij het op de markt brengen {#about-marketing-fatigue}

Door het beheer van de verkoopdruk te implementeren, kunt u voorkomen dat de populatie in de database te veel wordt gevraagd, ook wel &#39;marketingmoeheid&#39; genoemd. Om dit te doen, kunt u een maximumaantal berichten per ontvanger bepalen. Ook kunt u arbitrageregels tussen campagnes toepassen, zodat de beste boodschap naar het doelpubliek wordt gestuurd.

**** Voorschriften, om de verhandeling te beheren, bijvoorbeeld om het aantal te verzenden brieven aan een populatie te beperken tot twee, om de communicatie te selecteren die het best aansluit bij de belangen van een groep abonnees, om te voorkomen dat een sms naar een ontevreden klant wordt gestuurd, enz.

De campagnes worden geselecteerd gebaseerd op bepaalde drempels en berichtgewicht.

* Een drempel is het hoogste aantal leveringen dat binnen een bepaalde periode voor een bepaalde afnemer is toegestaan. De variabele kan ingesteld of variabel zijn. Deze wordt ingesteld of berekend in de instellingen voor de typologieregel. Zie [Maximum aantal berichten](#maximum-number-of-messages).
* Met leveringsgewichten kunt u topprioriteit-leveringen identificeren in het kader van drukbeheer. Berichten met het hoogste gewicht hebben prioriteit. Zie [Berichtgewicht](#message-weight).

Arbitrage bestaat erin ervoor te zorgen dat geplande campagnes met een groter gewicht dan de lopende campagne niet leiden tot excessieve profielopvraging: in dat geval wordt het profiel van de levering uitgesloten .

Arbitragecriteria (gewicht en/of drempel) kunnen variëren op basis van twee soorten informatie:

* voorkeur van de ontvanger, die verklarende informatie is: abonnementen op nieuwsbrieven, status van de ontvanger (klant of vooruitzicht);
* gedrag ontvanger: aankopen, bezochte koppelingen enz.

De arbitrageregel voor het definiëren van in aanmerking komende berichten wordt toegepast tijdens de analysefase. Voor elke ontvanger en voor de betrokken periode wordt het bericht verzonden als de volgende formule waar is: **(aantal verzonden berichten) + (aantal berichten met een groter gewicht) &lt; threshold**.

Anders is de ontvanger **[!UICONTROL Excluded by arbitration]**. Raadpleeg [Uitsluiting na arbitrage](#exclusion-after-arbitration) voor meer informatie hierover.

## Een drukregel {#creating-a-pressure-rule} maken

Als u arbitrage wilt instellen tussen campagnes die gebruikmaken van Adobe Campaign, begint u met het maken van typologieën voor campagnes en het definiëren van gekoppelde typologische regels (**Regels voor druk**).

Voer de volgende stappen uit om een typologieregel **[!UICONTROL Pressure]** te maken en te configureren:

1. Klik in de lijst met typologische regels voor de campagne op het pictogram **[!UICONTROL New]** boven de lijst.

   ![](assets/campaign_opt_create_a_rule_01.png)

1. Op **[!UICONTROL General]** lusje van de nieuwe regel, selecteer **Druk** typeregel en ga een naam en een beschrijving voor het in.

   ![](assets/campaign_opt_create_a_rule_02.png)

1. Wijzig zo nodig de uitvoeringsvolgorde. Wanneer de veelvoudige typologieregels als **[!UICONTROL Typology]** reeks worden toegepast, worden de lagere geordende regels eerst toegepast. Raadpleeg [Uitvoeringsvolgorde](../../campaign/using/applying-rules.md#execution-order) voor meer informatie hierover.
1. Definieer in de sectie **[!UICONTROL Calculation parameters]** een frequentie als u het opgeven van doelen na de volgende dagelijkse herarbitrageuitvoering wilt opslaan. Raadpleeg [Rekenfrequentie aanpassen](../../campaign/using/applying-rules.md#adjusting-calculation-frequency) voor meer informatie hierover.
1. Klik op het tabblad **[!UICONTROL Pressure]** en kies de kalenderperiode waarin de typologieregel van toepassing is.

   ![](assets/campaign_opt_create_a_rule_03.png)

   De regel wordt toegepast op leveringen waarvan de contactdatum in de betrokken periode is opgenomen.

   >[!NOTE]
   >
   >Met geplande leveringen wordt alleen rekening gehouden als de optie **[!UICONTROL Take the deliveries into account in the provisional calendar]** is geselecteerd. Raadpleeg [De punt instellen](#setting-the-period) voor meer informatie.

1. Definieer de methode voor het berekenen van het hoogste aantal berichten.

   De drempel vertegenwoordigt het hoogste aantal berichten dat tijdens de betrokken periode naar een ontvanger kan worden verzonden.

   Standaard is de drempelwaarde een constante en u moet een maximumaantal berichten aangeven dat door de regel wordt toegestaan.

   ![](assets/campaign_opt_create_a_rule_03b.png)

   Als u een drempelwaarde voor een variabele wilt definiëren, selecteert u de waarde **[!UICONTROL Depends on the recipient]** in het veld **[!UICONTROL Type of threshold]** en gebruikt u het pictogram aan de rechterkant om de editor voor de expressie te openen.

   ![](assets/campaign_opt_create_a_rule_04.png)

   Voor meer op dit, verwijs naar [Maximum aantal berichten](#maximum-number-of-messages).

1. Geef de methode op voor de berekening van het leveringsgewicht.

   Elke levering heeft een gewicht, d.w.z. een waarde die het prioriteitsniveau vertegenwoordigt: dit maakt arbitrage tussen campagnes mogelijk . Het gewicht wordt berekend aan de hand van de formule die is gedefinieerd in de typologieregel en/of in de eigenschappen ervan. Raadpleeg [Berichtgewicht](#message-weight) voor meer informatie hierover.

1. Standaard worden alle berichten in aanmerking genomen voor de berekening van de drempelwaarde. Op het tabblad **[!UICONTROL Restriction]** kunt u de berichten filteren die door de typologieregel worden beïnvloed:

   * In de bovenste sectie van dit tabblad kunt u de betreffende ontvangers beperken.
   * In de onderste sectie van dit tabblad kunt u de berichten filteren die moeten worden geteld.

      In het volgende voorbeeld wordt alleen rekening gehouden met ontvangers die zijn opgeslagen in de map **NewContacts** en met leveringen die beginnen met **Newsletter**.
   ![](assets/campaign_opt_create_a_rule_05.png)

1. Het **[!UICONTROL Typologies]** lusje laat u de campagnetypologieën bekijken die deze regel toepassen of de regel verbinden aan één of meerdere bestaande typologieën. Voor meer op dit, verwijs naar [Toepassend typologies](../../campaign/using/about-campaign-typologies.md#applying-typologies).

## Drempelwaarden en gewichten {#defining-thresholds-and-weights} definiëren

### Maximum aantal berichten {#maximum-number-of-messages}

Elke drukregel definieert een drempel, d.w.z. het maximumaantal berichten dat gedurende een bepaalde tijdsperiode naar een ontvanger kan worden verzonden. Zodra deze drempelwaarde is bereikt, kunnen tot het einde van de in aanmerking genomen periode geen leveringen meer plaatsvinden. Met dit proces kunt u automatisch een ontvanger uitsluiten van een levering als een bericht de ingestelde drempelwaarde overschrijdt. Op deze manier voorkomt u te veel vragen.

Drempelwaarden kunnen constant zijn of door een formule met variabelen worden berekend. Dit betekent dat de drempels voor een bepaalde periode van de ene ontvanger tot de andere kunnen variëren, of zelfs voor dezelfde ontvanger.

![](assets/campaign_opt_create_a_rule_threshold.png)

>[!CAUTION]
>
>Door **0** als drempelwaarde in te voeren, wordt voorkomen dat alle leveringen aan de doelpopulatie tijdens de beoordelingsperiode plaatsvinden.

**Voorbeeld:**

U kunt het aantal geoorloofde berichten volgens het segment indexeren waartot de ontvanger behoort. Dit betekent dat een ontvanger die tot het websegment behoort meer berichten kan ontvangen dan andere ontvangers. Met een **[!UICONTROL Iif (@origin='Web', 5, 3)]**-typeformule wordt de levering van 5 berichten aan ontvangers en 3 voor andere segmenten toegestaan. De configuratie is als volgt:

![](assets/campaign_opt_pressure_sample.png)

Als u de drempel wilt definiëren, kunt u een dimensie gebruiken die is gekoppeld aan de doeldimensie: Als u bijvoorbeeld berichten wilt opnemen die worden geleverd aan de ontvangende profielen die zijn opgeslagen in de bezoekerstabel (voor meer informatie over de bezoekerslijst, raadpleegt u [deze sectie](../../web/using/use-case--creating-a-refer-a-friend-form.md)) of om te voorkomen dat meer dan één bericht per week naar hetzelfde huishouden wordt verzonden (dat kan verwijzen naar meerdere e-mailadressen) die zijn geïdentificeerd in een dimensie die gekoppeld is aan die van de ontvangers.

Selecteer hiertoe de optie **[!UICONTROL Count messages on a linked dimension]** en selecteer vervolgens de bezoeker of de tabel met contactpersonen.

### Berichtgewicht {#message-weight}

Elke levering heeft een gewicht dat overeenkomt met het prioriteitsniveau. Standaard is het gewicht van een levering ingesteld op 5. Aan de hand van drukregels kunt u het gewicht bepalen van de leveringen waarop deze worden toegepast.

U kunt het gewicht instellen of berekenen met behulp van een formule die geschikt is voor de ontvanger. U kunt bijvoorbeeld het gewicht van een levering bepalen op basis van de belangen van de ontvanger.

>[!CAUTION]
>
>Het gewicht dat in een typologieregel wordt bepaald kan individueel voor elke levering, op **[!UICONTROL Properties]** tabel worden overbelast. Klik op het tabblad **[!UICONTROL Typology]** om de typologie van de campagne te selecteren en geef, indien nodig, het gewicht op dat moet worden toegepast.\
>Het gewicht dat in een A-typologieregel wordt gedeclareerd, wordt echter niet gebruikt voor het berekenen van een B-typologieregel: dit gewicht heeft alleen betrekking op leveringen die gebruikmaken van de A-regel.

**Voorbeeld:**

In het volgende voorbeeld willen we het gewicht van nieuwsbrieven op muziek koppelen aan de nevenscore van hun ontvangers. Dit doet u als volgt:

1. Maak een nieuw veld waarin u de geschiktheidsscores voor ontvangers kunt opslaan. In dit geval wordt het veld **@Music** verrijkt met antwoorden op enquêtes en online opiniepeilingen, verzamelde trackinggegevens, enz.
1. Maak een typologieregel om het gewicht van het bericht te berekenen op basis van dit veld.

   ![](assets/campaign_opt_pressure_weight_sample.png)

1. Pas deze regel op berichten met het volgende onderwerp toe: nieuwsbrieven, speciale aanbiedingen, enz. Het gewicht van deze leveringen, en dus het prioriteitsniveau ervan, zal afhangen van de geschiktheidsscore van elke ontvanger.

## Periode {#setting-the-period} instellen

De drukregels worden bepaald in **n**-dag rolperiodes.

De periode wordt gevormd in **[!UICONTROL Pressure]** lusje van de regel. U kunt het aantal dagen opgeven en, indien nodig, het type groepering selecteren dat u wilt toepassen (dag, week, maand, kwartaal, enz.).

Met het groeperingstype kunt u het veld **[!UICONTROL Period considered]** uitbreiden naar de hele dag, kalenderweek, kalendermaand of kalenderjaar voor datums voor de periode.

Bijvoorbeeld, zal een drukregel die een drempel van 2 berichten per week bepaalt, met een groepering aan elke kalendermaand, de levering van meer dan 2 berichten binnen de zelfde week EN binnen de zelfde kalendermaand verhinderen. Waarschuwing: als de periode twee maanden overlapt, wordt bij de berekening rekening gehouden met de leveringen van deze twee kalendermaanden en kunnen derhalve alle nieuwe leveringen in de tweede maand worden voorkomen.

>[!NOTE]
>
>Standaard wordt bij de berekening van de drempel alleen rekening gehouden met reeds verzonden leveringen. Controleer de optie **[!UICONTROL Take the deliveries into account in the provisional calendar]** als u ook de leveringen wilt overwegen die voor de betrokken periode zijn gepland. In dit geval wordt de beoordelingsperiode verdubbeld om toekomstige leveringen en eerdere leveringen te kunnen integreren.\
>Als u de geleverde producten wilt beperken tot een periode van twee weken, kunt u:
>
>* Typ **15d** in het veld **[!UICONTROL Concerned period]**: leveringen die tot twee weken vóór de datum van levering waarop de regel wordt toegepast, zijn verzonden, worden bij de berekening in aanmerking genomen;
>
>  
of
>
>* Typ **7d** in het veld **[!UICONTROL Period considered]** EN controleer **[!UICONTROL Take the deliveries into account in the provisional calendar]**\
   >optie: bij de berekening wordt rekening gehouden met leveringen die tot 7 dagen vóór de leveringsdatum zijn verzonden en die tot 7 dagen na de leveringsdatum waarop de regel wordt toegepast, zijn gepland.
>
>
De begindatum van de periode is afhankelijk van de configuratie van de database.

Als u bijvoorbeeld een drukregel van 15 dagen toepast zonder te groeperen in een levering van 12/11, wordt rekening gehouden met leveringen tussen 11/27 en 12/12. Indien bij de drukregel rekening wordt gehouden met de leveringen in het voorlopige tijdschema, worden alle tussen 11.27 en 12.27 geplande leveringen in aanmerking genomen. Tot slot als u een groepering per kalendermaand in de regel vormt, zullen alle leveringen in November en December in aanmerking worden genomen voor het berekenen van de drempel (van 11/1 tot 12/31).

>[!CAUTION]
>
>**Frequente gevallen**
>Om ervoor te zorgen dat geen rekening wordt gehouden met leveringen voor de lopende kalenderweek en om geen risico te lopen, rekening houdend met die van de vorige week voor de berekeningsdrempel, geeft u **[!UICONTROL Period considered]** op &#39;0&#39; en selecteert u &#39;Groepering per kalenderweek&#39; als **[!UICONTROL Period type]**.
> 
>Wanneer een periode groter is dan 0 (bijvoorbeeld 1), kan bij de berekening de waarde van de leveringen van de voorgaande dag in aanmerking worden genomen. Indien de vorige dag overeenkomt met de vorige kalenderweek en de gekozen periode &quot;Groepering per kalenderweek&quot; is, wordt derhalve met alle voorafgaande weken rekening gehouden voor de berekeningsdrempel.

**Voorbeeld:**

We willen een drukregel maken die het aanvragen beperkt tot 3 berichten per periode van twee weken, met een groepering tot de kalendermaand.

![](assets/campaign_opt_pressure_period_sample_1a.png)

Laten we zes nieuwsbrieven nemen met hetzelfde gewicht, gepland voor 05/30, 06/3, 06/8, 06/12, 06/22 en 06/30.

![](assets/campaign_opt_pressure_period_sample_0.png)

De voor 12 en 30 juni geplande leveringen worden niet verzonden: de levering 06/12 zou de drempel van 3 berichten per periode van twee weken overschrijden en de dertigste levering zou de drempel van toegestane communicatie per kalendermaand overschrijden.

![](assets/campaign_opt_pressure_period_sample_1.png)

Alle ontvangers voor deze leveringen worden tijdens de analysefase door arbitrage uitgesloten:

![](assets/campaign_opt_pressure_period_sample_2.png)

Voor dezelfde regel geldt dat als u leveringen per kwartaal groepeert, de ontvangers van **nieuwsbrief nr.5** ook worden uitgesloten en niet worden verzonden.

Ten slotte, als geen groepering wordt geselecteerd, slechts **nieuwsbrief nr.4** zal niet worden verzonden, aangezien het voor de zelfde periode van twee weken zoals de eerste drie nieuwsbrieven gepland was.

>[!NOTE]
>
>Wanneer u de definitie van een typologieregel verandert, kunt u **Simulatie** tot stand brengen om zijn effect op de leveringen te controleren het wordt toegepast op en het effect te controleren dat de leveringen op elkaar hebben. Raadpleeg [Campagnesimulaties](../../campaign/using/campaign-simulations.md) voor meer informatie hierover.

## Uitsluiting na arbitrage {#exclusion-after-arbitration}

Arbitrage wordt elke avond opnieuw toegepast via de technische workflow **[!UICONTROL Forecasting]** en de **[!UICONTROL Campaign jobs]**-workflow.

In de **[!UICONTROL Forecasting]**-workflow worden de gegevens vooraf berekend voor de lopende periode (van de begindatum tot de huidige datum), zodat tijdens de analyse typologische regels kunnen worden toegepast. Ook wordt elke avond opnieuw een berekening gemaakt van de uitsluitingstellers voor arbitrage.

Adobe Campaign controleert dus voor elke ontvanger of het aantal te verzenden berichten de drempel niet overschrijdt, rekening houdend met het aantal reeds verzonden berichten voor de betrokken periode. Deze informatie is een **indicator**, aangezien alle berekeningen op het tijdstip van levering worden bijgewerkt.

Als dit aantal de drempel overschrijdt, worden de arbitrageregels toegepast die in de campagnetypologie zijn gedefinieerd en worden de ontvangers uitgesloten van campagnes met een lager gewicht.

![](assets/campaign_opt_pressure_exclusion.png)

>[!NOTE]
>
>Als meerdere leveringen dezelfde scores hebben, wordt de campagne die voor de vroegste datum is gepland, verzonden.

## Gebruik gevallen van drukregels {#use-cases-on-pressure-rules}

### Aanpassing van de drempel op basis van criterium {#adapting-the-threshold-based-on-criterion}

Wij willen een typologieregel tot stand brengen om de levering van meer dan 4 berichten per week aan klanten en 2 berichten per week aan vooruitzichten te verhinderen.

Om klanten en vooruitzichten te identificeren, gebruik het **[!UICONTROL Status]** gebied, dat 0 voor vooruitzichten en 1 voor klanten bevat.

Pas de volgende stappen toe om de regel te maken:

1. Maak een nieuwe **Teksttypologieregel**.
1. Bewerk het tabblad **[!UICONTROL Pressure]**: in **[!UICONTROL Maximum number of messages]** sectie, willen wij een formule tot stand brengen om de drempel afhankelijk van elke ontvanger te berekenen. Selecteer de waarde **[!UICONTROL Depends on the recipient]** in het veld **[!UICONTROL Threshold type]** en klik vervolgens op **[!UICONTROL Edit expression]** rechts van het veld **[!UICONTROL Formula]**.

   Klik op de knop **[!UICONTROL Advanced parameters]** om de berekeningsformule te definiëren.

   ![](assets/campaign_opt_pressure_sample_1_1.png)

1. Selecteer de optie **[!UICONTROL Edit the formula using an expression]** en klik **[!UICONTROL Next]**.

   ![](assets/campaign_opt_pressure_sample_1_2.png)

1. Dubbelklik in de lijst met functies op de functie **Iif** in het knooppunt **[!UICONTROL Others]**.

   Selecteer vervolgens de **Status** van de ontvangers in de sectie **[!UICONTROL Available fields]**.

   ![](assets/campaign_opt_pressure_sample_1_3.png)

   Voer de volgende formule in: **Iif(@status=0,2,4)**

   ![](assets/campaign_opt_pressure_sample_1_4.png)

   Met deze formule kunt u de waarde 2 toewijzen als de status gelijk is aan 0 en de waarde 4 voor alle andere statussen.

   Klik op **[!UICONTROL Finish]** om de formule goed te keuren.

1. Vermeld de periode gedurende welke de regel van toepassing zal zijn: 7 dagen in dit geval om het aantal berichten per week te tellen.

   ![](assets/campaign_opt_pressure_sample_1_5.png)

1. Sla de regel op om het maken van de regel goed te keuren.

Koppel nu de regel die u zojuist hebt gemaakt aan een typologie om deze toe te passen op leveringen. Dit doet u als volgt:

1. Maak een campagnetypologie.
1. Ga naar het **[!UICONTROL Rules]** lusje, klik **[!UICONTROL Add]** knoop en selecteer de regel u enkel hebt gecreeerd.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Sla de typologie op: wordt toegevoegd aan de lijst van bestaande typologieën.

Als u deze typologie in uw leveringen wilt gebruiken, selecteert u deze in de leveringseigenschappen op het tabblad **[!UICONTROL Typology]**, zoals hieronder wordt weergegeven:

![](assets/campaign_opt_pressure_sample_1_7.png)

>[!NOTE]
>
>De typologie kan in de leveringssjabloon worden gedefinieerd, en wordt dan automatisch toegepast op alle leveringen die met deze sjabloon zijn gemaakt.

Tijdens de leveringsanalyse worden de ontvangers van de levering, indien van toepassing, uitgesloten van de levering, afhankelijk van het aantal reeds aan hen verzonden leveringen. Als u deze gegevens wilt weergeven, kunt u:

* Bekijk het analyseresultaat:

   ![](assets/campaign_opt_pressure_sample_1_8.png)

* Bewerk de levering en klik op de tab **[!UICONTROL Delivery]** en de subtab **[!UICONTROL Exclusions]**:

   ![](assets/campaign_opt_pressure_sample_1_9.png)

* Klik op het tabblad **[!UICONTROL Audit]** en vervolgens op het subtabblad **[!UICONTROL Causes of exclusions]** om het aantal uitsluitingen en de toegepaste typologische regels weer te geven:

   ![](assets/campaign_opt_pressure_sample_1_10.png)

### Het leveringsgewicht berekenen op basis van het gedrag {#calculating-the-delivery-weight-based-on-behavior}

U kunt drukregels bepalen die op ontvankelijk gedrag worden gebaseerd: zo kan het gewicht van een levering worden aangepast aan criteria die van de ene ontvanger tot de andere verschillen . U kunt bijvoorbeeld een bericht verzenden, afhankelijk van de vraag of een ontvanger uw website heeft bezocht, in een bepaald gedeelte van de laatste nieuwsbrief heeft geklikt, zich op een informatieservice heeft geabonneerd of zelfs op basis van antwoorden op een enquête, een online game, enz.

In het volgende voorbeeld willen we een levering maken met een gewicht van 5. Dit gewicht wordt verrijkt met nevenscores op basis van het gedrag van de ontvanger: klanten die al vanaf deze site hebben besteld, hebben een score van 5, terwijl klanten die nog nooit online hebben besteld, een score van 4 hebben.

Om dit type van configuratie uit te voeren, moet u een formule gebruiken om berichtgewicht te bepalen. In het gegevensmodel moet informatie over de populatiescore en enquêteantwoorden beschikbaar zijn. In ons voorbeeld is het veld **Propensiteit** toegevoegd.

Pas de volgende configuratiestappen toe:

1. Maak een nieuwe **Teksttypologieregel**.
1. Bewerk het tabblad **[!UICONTROL Pressure]**. Wij willen een drempelformule creëren die op elke individuele ontvanger wordt gebaseerd: Klik op het pictogram **[!UICONTROL Edit expression]** rechts van het veld **[!UICONTROL Weight formula]**.

   ![](assets/campaign_opt_pressure_sample_2_1.png)

1. Standaard wordt de waarde **5** weergegeven in de bovenste sectie van de expressie-editor. We willen de nevenscore van elke ontvanger toevoegen aan dit gewicht: Plaats uw curseur rechts van 5, ga **+** karakter in en selecteer **Propensiteit** gebied.

   ![](assets/campaign_opt_pressure_sample_2_2.png)

1. Voeg vervolgens een hogere waarde toe aan ontvangers die al een aankoop hebben gedaan. Voor hen moet het gewicht van de levering met 5 worden verhoogd, voor andere met slechts 4.

   ![](assets/campaign_opt_pressure_sample_2_3.png)

1. Klik **[!UICONTROL Finish]** om deze regel op te slaan.
1. Koppel de regel aan een campagnetypologie en verwijs deze typologie in een levering om het goed te keuren.

### Alleen de hoogst gewogen berichten {#sending-only-the-highest-weighted-messages} verzenden

U wilt niet meer dan 2 berichten binnen de zelfde week, met een grens van 2 berichten per dag, naar elk van uw ontvangers verzenden, en u wilt slechts de berichten met hogere gewichten om worden geleverd.

Hiervoor moet u verschillende leveringen met verschillende gewichten voor dezelfde ontvanger plannen en een drukregel toepassen om de leveringen met een lager gewicht uit te sluiten.

Eerst, vorm de drukregel.

1. Maak een drukregel. Raadpleeg [Een drukregel maken](#creating-a-pressure-rule) voor meer informatie.
1. Selecteer op het tabblad **[!UICONTROL General]** de optie **[!UICONTROL Re-apply the rule at the start of personalization]**.

   ![](assets/campaign_opt_pressure_example_5.png)

   Met deze optie wordt de waarde die in het veld **[!UICONTROL Frequency]** is gedefinieerd, overschreven en wordt de regel tijdens de verpersoonlijkingsfase automatisch toegepast. Raadpleeg [Rekenfrequentie aanpassen](../../campaign/using/applying-rules.md#adjusting-calculation-frequency) voor meer informatie hierover.

1. Selecteer **[!UICONTROL Pressure]** op het tabblad &lt;a0/> als **[!UICONTROL Period considered]** en **[!UICONTROL Grouping per day]** als **[!UICONTROL Period type]**.**[!UICONTROL 7d]**
1. Selecteer de optie **[!UICONTROL Take the deliveries into account in the provisional calendar]** om de geplande leveringen op te nemen.

   ![](assets/campaign_opt_pressure_example_1.png)

   Bij de berekening wordt rekening gehouden met leveringen die tot 7 dagen vóór de leveringsdatum zijn verzonden en die tot 7 dagen na de leveringsdatum zijn gepland. Raadpleeg [De punt instellen](#setting-the-period) voor meer informatie.

1. Koppel op het tabblad **[!UICONTROL Typologies]** de regel aan een campagnetypologie.
1. Sla uw wijzigingen op.

Maak en configureer nu een workflow voor elke levering waarop u de drukregel wilt toepassen.

1. Een campagne maken. Raadpleeg [deze sectie](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign) voor meer informatie.
1. Voeg op het tabblad **[!UICONTROL Targeting and workflows]** van uw campagne een **Query**-activiteit toe aan uw workflow. Raadpleeg [deze sectie](../../workflow/using/query.md) voor meer informatie over het gebruik van deze activiteit.
1. Voeg een **[!UICONTROL Email delivery]** activiteit aan het werkschema toe en open het. Raadpleeg [deze sectie](../../workflow/using/delivery.md) voor meer informatie over het gebruik van deze activiteit.
1. Ga naar het **[!UICONTROL Approvals]** lusje van **[!UICONTROL Delivery properties]** en maak alle goedkeuringen onbruikbaar.

   ![](assets/campaign_opt_pressure_example_2.png)

1. Verwijs op **[!UICONTROL Typology]** lusje van **[!UICONTROL Delivery properties]**, de campagnetypologie om de regel op toe te passen. Definieer een gewicht voor de levering.

   ![](assets/campaign_opt_pressure_example_3.png)

1. Klik in de levering op **[!UICONTROL Scheduling]** en selecteer **[!UICONTROL Schedule delivery (automatic execution when the scheduled date is reached)]**. Selecteer in dit voorbeeld de optie **[!UICONTROL Use a calculation formula]**.
1. Stel de extractiedatum in op 10 minuten (huidige datum + 10 minuten).
1. Stel de contactdatum in op de volgende dag (huidige datum + 1 dag).

   ![](assets/campaign_opt_pressure_example_4.png)

   Voor de drukregeluitsluitingen die met succes moeten worden geïmplementeerd, moet u de extractiedatum en -tijd vóór de contactdatum en -tijd instellen, evenals voordat de nachtelijke arbitrage opnieuw wordt toegepast. Raadpleeg [Uitsluiting na arbitrage](#exclusion-after-arbitration) voor meer informatie hierover.

1. Schakel de optie **[!UICONTROL Confirm the delivery before sending]** uit en sla uw wijzigingen op.
1. Ga op dezelfde manier te werk voor elke levering die u wilt verzenden. Zorg ervoor dat u het gewenste gewicht voor elke levering instelt.
1. Voer de relevante workflows uit om de leveringen voor te bereiden en te verzenden.

Wanneer de nachtelijke arbitrage wordt toegepast, worden de leveringen met de laagste gewichten voor dezelfde afnemer uitgesloten. Alleen leveringen met het hoogste gewicht worden in aanmerking genomen voor verzending. Raadpleeg [Berichtgewicht](#message-weight) voor meer informatie hierover.

Aangezien er al eerder in de week een e-mailbericht naar de betrokken ontvangers is verzonden, wordt in de onderstaande tabel een voorbeeld weergegeven van de configuraties die kunnen worden toegepast voor nog twee leveringen.

<table> 
 <thead> 
  <tr> 
   <th> Levering<br /> </th> 
   <th> Goedkeuringen<br /> </th> 
   <th> Gewicht<br /> </th> 
   <th> Extractiedatum/-tijd<br /> </th> 
   <th> Contactdatum<br /> </th> 
   <th> Begindatum/-tijd van levering<br /> </th> 
   <th> Uitvoeringsdatum/tijd van de bitmapworkflow<br /> </th> 
   <th> Leveringsstatus<br /> </th> 
   <th> Verzonden levering (datum/tijd)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Levering 1<br /> </td> 
   <td> Uitgeschakeld<br /> </td> 
   <td> 5<br /> </td> 
   <td> 3pm<br /> </td> 
   <td> 8am (volgende dag)<br /> </td> 
   <td> 2pm<br /> </td> 
   <td> Night<br /> </td> 
   <td> Uitgesloten<br /> </td> 
   <td> Uitgesloten<br /> </td> 
  </tr> 
  <tr> 
   <td> Levering 2<br /> </td> 
   <td> Uitgeschakeld<br /> </td> 
   <td> 10<br /> </td> 
   <td> 4pm<br /> </td> 
   <td> 9am (volgende dag)<br /> </td> 
   <td> 2pm<br /> </td> 
   <td> Night<br /> </td> 
   <td> Verzonden<br /> </td> 
   <td> 9am (volgende dag)<br /> </td> 
  </tr> 
 </tbody> 
</table>

Nadat de extractiedatum voor de twee leveringen is verstreken, wordt de nachtelijke arbitrage opnieuw toegepast vóór de contactdata van beide leveringen. Op deze manier kunnen alle reeds verzonden leveringen (ontvangers voor wie een levering wordt verwerkt, geregistreerd via de grote logboeken) of geplande leveringen (ontvangers die in aanmerking komen voor een levering, geregistreerd via de voorspelde logboeken) worden gevonden.

Zodra alle verzonden en potentiële leveringen zijn vermeld voor de periode die in de drukregel is bepaald, sorteert Adobe Campaign ze op basis van gewicht, met de hoogste gewogen eerst. Wanneer de in de drukregel vastgestelde drempelwaarde wordt bereikt (hier niet meer dan twee e-mails in dezelfde week), worden de ontvangers uitgesloten van de levering.
