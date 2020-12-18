---
solution: Campaign Classic
product: campaign
title: Hypothesesjablonen
description: Hypothesesjablonen
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 0%

---


# Hypothesesjablonen{#hypothesis-templates}

## Een hypothesemodel maken {#creating-a-hypothesis-model}

Door het samenstellen van de hypothesesjabloon kunt u de context definiëren voor het meten van reacties, of het nu gaat om een levering of een aanbieding. Hier wordt verwezen naar de verschillende meettabellen, waaronder die voor het definiëren van relaties tussen personen, hypothesen en de transactietabel.

Voer de volgende stappen uit om een hypothesesjabloon te maken:

1. Klik in de Adobe Campaign-verkenner op **[!UICONTROL Resources>Templates>Hypothesis templates]**.

   ![](assets/response_hypothesis_model_creation_001.png)

1. Klik **[!UICONTROL New]** of klik in de lijst van malplaatjes met de rechtermuisknop aan en kies **[!UICONTROL New]** in de drop-down lijst.
1. Voer het hypotheselabel in.
1. Geef aan of de sjabloon bestemd is voor hypothesen over aanbiedingen of leveringen via de **[!UICONTROL Hypothesis type]**.
1. Geef voor **[!UICONTROL Delivery]** typesjablonen op of metingen moeten worden uitgevoerd met of zonder een controlegroep (zie [Eigenschappen van een hypothesesjabloon](#properties-of-a-hypothesis-template) voor meer informatie hierover).
1. Voor **[!UICONTROL Delivery]** typesjablonen, kunt u een specifiek kanaal kiezen of besluiten om de sjabloon toe te passen op alle beschikbare kanalen in Adobe Campaign met behulp van de vervolgkeuzelijst **[!UICONTROL Channel]** (voor meer informatie hierover raadpleegt u [Eigenschappen van een hypothesesjabloon](#properties-of-a-hypothesis-template)).
1. Selecteer **[!UICONTROL Execution folder]** waarin u wenst om de hypothesen tot stand te brengen en automatisch uit te voeren die van dit malplaatje zullen worden gecreeerd.
1. Kies de uitvoeringsinstellingen (voor meer informatie hierover gaat u naar [Instellingen voor de uitvoering van een hypothesesjabloon](#hypothesis-template-execution-settings)).
1. Geef de berekeningsperiode voor de hypothese op (zie [Instellingen voor de uitvoering van een hypothesesjabloon](#hypothesis-template-execution-settings) voor meer informatie).

   >[!CAUTION]
   >
   >Deze periode wordt bepaald vanaf de contactdatum.

1. Geef op het tabblad **[!UICONTROL Transactions]** de tabellen en velden op die nodig zijn voor de hypotheseverberekening (zie [Transacties](#transactions) voor meer informatie hierover).
1. Als uw malplaatje voor **[!UICONTROL Offer]** typehypothesen wordt gevormd, kunt u **[!UICONTROL Update offer proposition status]** optie toelaten: in dit geval selecteert u de status van het voorstel dat u wilt wijzigen.
1. Geef het toepassingsgebied van de hypothesetoepassing op (zie [Omtrek van de hypothese](#hypothesis-perimeter) voor meer informatie).
1. Indien nodig, gebruik een manuscript om het filtreren (voor meer op dit, verwijs naar [Hypothese perimeter](#hypothesis-perimeter)) te voltooien.

### Eigenschappen van een hypothesesjabloon {#properties-of-a-hypothesis-template}

Op het tabblad **[!UICONTROL General]** van de sjabloon kunt u de algemene sjabloonopties opgeven. De beschikbare velden zijn:

* **[!UICONTROL Hypothesis type]**: Hiermee kunt u bepalen of de sjabloon bestemd moet zijn voor hypothesen over leveringen of aanbiedingen.

   U kunt ook een hypothese maken die zowel op leveringen als op aanbiedingen van toepassing is.

   >[!NOTE]
   >
   >Als de sjabloon van toepassing is op aanbiedingen, is de optie **[!UICONTROL Update offer proposition status]** beschikbaar op het tabblad **[!UICONTROL Transactions]**.

* **[!UICONTROL Measurement with control group]**: Hiermee kunt u aangeven of een controlegroep is gedefinieerd voor de levering of de campagne en deze opnemen in meetindicatoren. De controlegroep, die geen leveringen ontvangt, laat u het effect van de campagne na de levering meten, door het met de doelpopulatie te vergelijken die de levering ontving.

   >[!NOTE]
   >
   >Als het malplaatje wordt gevormd om een controlegroep in overweging te nemen, maar geen groep wordt bepaald in de levering die de hypothesen betreffen, zullen de resultaten op gerichte slechts ontvangers worden gebaseerd.

   Voor meer bij het bepalen van en het vormen van een controlegroep, verwijs naar [het bepalen van een controlegroep](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

* **[!UICONTROL Channel]**: u kunt een specifiek kanaal kiezen of de hypothesesjabloon beschikbaar maken voor alle kanalen in de Adobe Campaign-console door  **[!UICONTROL All channels]** in de vervolgkeuzelijst te selecteren. Als u het malplaatje voor een specifiek kanaal vormt, laat dit u automatisch leveringen per kanaal filtreren wanneer het creëren van de hypothese (verwijs naar [het Creëren van hypotheses](../../campaign/using/creating-hypotheses.md)).

   ![](assets/response_properties_001.png)

* **[!UICONTROL Execution folder]**: Hiermee kunt u de uitvoeringsmap voor de hypothese opgeven.
* **[!UICONTROL Taken into account in campaign ROI calculation]**: houdt bij de berekening van het rendement van investeringen voor de desbetreffende campagne rekening met het hypotheseresultaat.

### Instellingen {#hypothesis-template-execution-settings} voor de uitvoering van een hypothesesjabloon

Op het tabblad **[!UICONTROL General]** van de sjabloon kunt u ook de parameters voor het uitvoeren van hypothesen opgeven. De beschikbare opties zijn als volgt:

* **[!UICONTROL Schedule execution for a time of low activity]**: Hiermee kunt u de hypothese plannen om Adobe Campaign-prestaties te optimaliseren. Als deze optie is ingeschakeld, wordt tijdens de downtime in de verwerkingsworkflow van campagnes hypotheseverberekening uitgevoerd.

   ![](assets/response_exec_settings_002.png)

* **[!UICONTROL Priority]**: het niveau dat wordt toegepast op de hypothese om de berekeningsbevelen voor hypothesen uit te splitsen indien er sprake is van gelijktijdige executies.

   ![](assets/response_exec_settings_003.png)

* **[!UICONTROL Automatic execution]**: Indien nodig kunt u een herberekening van de hypothese plannen (bijvoorbeeld als u de indicatoren regelmatig wilt bijwerken tot het einde van de levering).

   ![](assets/response_exec_settings_001.png)

   Pas het volgende proces toe om een schema op te geven:

   1. Klik op de koppeling **[!UICONTROL Frequency of execution...]** en vervolgens op de knop **[!UICONTROL Change...]**.

      ![](assets/response_frequency_execution_001.png)

   1. Configureer de frequentie, de gerelateerde gebeurtenissen en de geldigheidsperiode.

      ![](assets/response_frequency_execution_002.png)

   1. Klik **[!UICONTROL Finish]** om het programma te bewaren.

      ![](assets/response_frequency_execution_003.png)

* **[!UICONTROL Log SQL queries in journal]**: deze functie is gereserveerd voor deskundige gebruikers. Het laat u een lusje aan de controle van de meethypothese toevoegen om SQL vragen te tonen. Dit laat de opsporing van mogelijke storingen toe als een simulatie met fouten eindigt.
* **[!UICONTROL Keep execution workflow]**: Hiermee kunt u de workflow behouden die automatisch is gegenereerd bij het begin van de hypotheseberekening. In de hypothesen die zijn gemaakt op basis van een sjabloon waarop deze optie is ingeschakeld, is de gegenereerde workflow beschikbaar om het proces te volgen.

   >[!CAUTION]
   >
   >Deze optie moet alleen worden geactiveerd voor foutopsporingsdoeleinden, in het geval van een fout tijdens het uitvoeren van de hypothese.\
   >Bovendien mogen automatisch gegenereerde workflows niet worden gewijzigd. Eventuele wijzigingen zouden elders niet in aanmerking worden genomen voor latere berekeningen.\
   >Als u deze optie hebt ingeschakeld, verwijdert u de workflow nadat deze is uitgevoerd.

### Transacties {#transactions}

Dit tabblad bevat de verschillende velden en tabellen waarmee u de geschiedenis van reacties van ontvangers in termen van transacties kunt opslaan. Raadpleeg de [Configuration](../../configuration/using/about-schema-reference.md)-handleiding voor meer informatie over de tabellen die zijn gewijd aan reactiebeheer.

* **[!UICONTROL Schema (reaction log storage)]**: Selecteer de tabel met reacties van de ontvanger. De out-of-the-box tabel in Adobe Campaign is **NmsRemaMatchRcp**.
* **[!UICONTROL Transaction schema]**: kiest u de tabel die de hypothesen betreffen, d.w.z. de transactie of de aankooptabel.
* **[!UICONTROL Querying schema]**: de criteria voor het filteren van de hypothese te kiezen.
* **[!UICONTROL Link to individuals]**: Kies de koppeling tussen personen en de tabel die als transactieschema wordt gebruikt.
* **[!UICONTROL Link to the household]**: Selecteer de koppeling naar het huishouden in het transactieschema als u alle leden van een huishouden in een hypothese wilt opnemen. Dit veld is optioneel.
* **[!UICONTROL Transaction date]**: dit veld is optioneel, maar wordt aanbevolen, omdat u hiermee een berekeningsruimte voor hypothesen kunt definiëren.
* **[!UICONTROL Measurement period]**: Hiermee kunt u begin- en einddatums configureren waarin hypothesen worden uitgevoerd en aankooplijnen worden hersteld.

   Wanneer de hypothese verband houdt met een levering, wordt de meting automatisch geactiveerd een paar dagen na de contactdatum voor directe postzendingen of na de leveringsdatum voor e-mail- of sms-leveringen.

   ![](assets/response_measurement_001.png)

   Als de hypothese direct wordt gelanceerd, kan ze worden gedwongen als ze onmiddellijk zou willen worden geactiveerd. Anders, wordt het teweeggebracht automatisch gebaseerd op het gevormde eind van berekeningsdatum, die op de hypotheseaanmaakdatum gebaseerd is (verwijs naar [het Creëren van een hypothese op de vlucht op een levering](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)).

* **[!UICONTROL Transaction/Margin amount]**: Deze velden zijn optioneel en stellen u in staat omzetindicatoren automatisch te berekenen (zie  [Indicatoren](../../campaign/using/hypothesis-tracking.md#indicators)).
* **[!UICONTROL Unit amount]**: Hiermee kunt u een bedrag instellen voor het berekenen van de inkomsten (zie  [Indicatoren](../../campaign/using/hypothesis-tracking.md#indicators)).

   ![](assets/response_transactions_001.png)

* **[!UICONTROL Additional measures and data]**: Hiermee kunt u aanvullende rapportagemaatregelen of assen opgeven vanuit velden in de verschillende tabellen.
* **[!UICONTROL Update offer proposition status]**: Hiermee kunt u de status van het voorstel wijzigen als een ontvanger van het aanbod door de hypothese wordt geïdentificeerd.

   ![](assets/response_offer_status_001.png)

### Hypothische omtrek {#hypothesis-perimeter}

Als u de transactietabel en de velden hebt gedefinieerd waarop de hypothese betrekking heeft, kunt u het bereik van de hypothesen verfijnen door de doeltransacties en -leveringen aan de hand van filters op te geven. U kunt ook een JavaScript-script gebruiken om expliciet te verwijzen naar een product waarnaar in de transactietabel wordt verwezen.

* **Filteren op transacties**: in het  **[!UICONTROL Scope]** lusje, kunt u een filter op de hypothese vormen. Dit doet u als volgt:

   1. Klik op de koppeling **[!UICONTROL Edit query]**.

      ![](assets/response_scope_filtering_001.png)

   1. Geef de filtervoorwaarden op.

      ![](assets/response_scope_filtering_002.png)

   1. Selecteer de transactie waarop de hypothese betrekking heeft.

      ![](assets/response_scope_filtering_003.png)

* **Filter op ontvangers**: op het  **[!UICONTROL Scope]** tabblad kunt u uw hypothese beperken tot alle informatie die aan een bericht is gekoppeld (levering, ontvanger, e-mailadres, service, enz.):

   1. Klik op de koppeling **[!UICONTROL Add a filter]** en **[!UICONTROL Edit query]**.

      ![](assets/response_scope_filtering_004.png)

   1. Geef de filtervoorwaarden op.

      ![](assets/response_scope_filtering_005.png)

   1. Klik **[!UICONTROL Finish]** om uw vraag te bewaren.

      ![](assets/response_scope_filtering_006.png)

* **Script**: u kunt een JavaScript-script gebruiken om de hypothesemontages tijdens de uitvoering dynamisch te overladen.

   Om dit te doen, klik **[!UICONTROL Advanced settings]** verbinding dan ga het gewenste manuscript in.

   >[!NOTE]
   >
   >Deze optie is bedoeld voor ervaren gebruikers.

   ![](assets/response_hypothesis_model_creation_011.png)

## Voorbeeld: het creëren van een hypothesemalplaatje op een levering {#example--creating-a-hypothesis-template-on-a-delivery}

In dit voorbeeld, gaan wij een hypothesemalplaatje op een direct-mailtype levering tot stand brengen. De transactietabel (**Aankopen** in ons voorbeeld) waarop de hypothesen worden gebaseerd, bevat aankooplijnen die zijn gekoppeld aan artikelen of producten. Wij willen ons model vormen om hypotheses op artikelen of producten in de aankooplijst tot stand te brengen.

1. Ga in de Adobe Campaign-verkenner naar het knooppunt **[!UICONTROL Resources > Templates > Hypothesis templates]**.
1. Klik **[!UICONTROL New]** om een malplaatje tot stand te brengen.

   ![](assets/response_hypothesis_model_example_001.png)

1. Wijzig het sjabloonlabel.

   ![](assets/response_hypothesis_model_example_002.png)

1. Selecteer **[!UICONTROL Deliveries]** als type hypothese.
1. Geef aan dat de levering een controlegroep kan bevatten door het desbetreffende vak in te schakelen.
1. Kies het kanaal **[!UICONTROL Direct mail]**.

   >[!NOTE]
   >
   >Aangezien de sjabloon specifiek is voor direct-mailleveringen, kunnen hypothesen die met dit model worden gemaakt, niet aan andere leveringstypen worden gekoppeld.

1. Selecteer op het tabblad **[!UICONTROL Transactions]** de tabel met reacties bij ontvangers.

   ![](assets/response_hypothesis_model_example_006.png)

1. Kies in het veld **[!UICONTROL Transactions schema]** de aankooptabel.

   ![](assets/response_hypothesis_model_example_007.png)

1. Selecteer aankooplijnen in het **[!UICONTROL Querying schema]** gebied.

   ![](assets/response_hypothesis_model_example_008.png)

1. Kies de ontvangers die aan de aankooptabel zijn gekoppeld.

   ![](assets/response_hypothesis_model_example_009.png)

1. Selecteer het veld dat is gekoppeld aan de aankoopdatum.

   Hiermee kunt u een tijdkader voor hypothesen definiëren. Dit werkgebied is niet verplicht, maar wordt wel aanbevolen.

   ![](assets/response_hypothesis_model_example_010.png)

1. Configureer de berekeningsperiode 5 tot 25 dagen.

   ![](assets/response_hypothesis_model_example_005.png)

1. Klik op het tabblad **[!UICONTROL Scope]** om een filter voor hypothesen te maken.**[!UICONTROL Edit query]**

   ![](assets/response_hypothesis_model_example_011.png)

   Met de gemaakte sjabloon kunt u dus hypothesen uitvoeren op de producten of artikelen in de aankooptabel.

1. Klik **[!UICONTROL Save]** om uw malplaatje te registreren.

