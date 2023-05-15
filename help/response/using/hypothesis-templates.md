---
product: campaign
title: Hypothesesjablonen
description: Leer hoe u hypothesesjablonen maakt in Campagne Response Manager
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 428c7677-454b-4618-bae7-0be7df6dfcaa
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 2%

---

# Hypothesesjablonen{#hypothesis-templates}



## Een hypothesemodel maken {#creating-a-hypothesis-model}

Door het samenstellen van de hypothesesjabloon kunt u de context definiëren voor het meten van reacties, of het nu gaat om een levering of een aanbieding. Hier wordt verwezen naar de verschillende meettabellen, waaronder die voor het definiëren van relaties tussen personen, hypothesen en de transactietabel.

Voer de volgende stappen uit om een hypothesesjabloon te maken:

1. Klik in de Adobe Campaign-verkenner op **[!UICONTROL Resources>Templates>Hypothesis templates]**.

   ![](assets/response_hypothesis_model_creation_001.png)

1. Klikken **[!UICONTROL New]** of klik met de rechtermuisknop in de lijst met sjablonen en kies **[!UICONTROL New]** in de vervolgkeuzelijst.
1. Voer het hypotheselabel in.
1. Geef aan of de template bestemd is voor hypothesen over aanbiedingen of leveringen via de **[!UICONTROL Hypothesis type]**.
1. Voor **[!UICONTROL Delivery]** typesjablonen, geef aan of metingen moeten worden uitgevoerd met of zonder een controlegroep. [Meer informatie](#properties-of-a-hypothesis-template)
1. Voor **[!UICONTROL Delivery]** typesjablonen, kunt u een specifiek kanaal kiezen of de sjabloon toepassen op alle beschikbare kanalen in Adobe Campaign met behulp van de **[!UICONTROL Channel]** vervolgkeuzelijst. [Meer informatie](#properties-of-a-hypothesis-template)
1. Selecteer **[!UICONTROL Execution folder]** waarin u de hypothesen wilt creëren en automatisch uitvoeren die van dit malplaatje zullen worden gecreeerd.
1. Kies de uitvoeringsinstellingen. [Meer informatie](#hypothesis-template-execution-settings)
1. Geef de berekeningsperiode voor de hypothese op. [Meer informatie](#hypothesis-template-execution-settings)

   >[!CAUTION]
   >
   >Deze periode wordt bepaald vanaf de contactdatum.

1. In de **[!UICONTROL Transactions]** , geeft u de tabellen en velden op die nodig zijn voor de berekening van de hypothese. [Meer informatie](#transactions)
1. Als uw sjabloon is geconfigureerd voor **[!UICONTROL Offer]** type hypothesen, kunt u toelaten **[!UICONTROL Update offer proposition status]** optie: in dit geval selecteert u de status van het voorstel dat u wilt wijzigen.
1. Geef de reikwijdte van de hypothesetoepassing op. [Meer informatie](#hypothesis-perimeter)
1. Gebruik indien nodig een script om het filteren te voltooien. [Meer informatie](#hypothesis-perimeter)

### Eigenschappen van een hypothesesjabloon {#properties-of-a-hypothesis-template}

De sjablonen **[!UICONTROL General]** kunt u de algemene sjabloonopties opgeven. De beschikbare velden zijn:

* **[!UICONTROL Hypothesis type]**: Hiermee kunt u bepalen of de sjabloon bestemd moet zijn voor hypothesen over leveringen of aanbiedingen.

   U kunt ook een hypothese maken die zowel op leveringen als op aanbiedingen van toepassing is.

   >[!NOTE]
   >
   >Als de sjabloon van toepassing is op aanbiedingen, **[!UICONTROL Update offer proposition status]** Deze optie is beschikbaar in het dialoogvenster **[!UICONTROL Transactions]** tab.

* **[!UICONTROL Measurement with control group]**: Hiermee kunt u aangeven of een controlegroep is gedefinieerd voor de levering of de campagne en deze opnemen in meetindicatoren. De controlegroep, die geen leveringen ontvangt, laat u het effect van de campagne na de levering meten, door het met de doelpopulatie te vergelijken die de levering ontving.

   >[!NOTE]
   >
   >Als het malplaatje wordt gevormd om een controlegroep in overweging te nemen, maar geen groep wordt bepaald in de levering die de hypothesen betreffen, zullen de resultaten op gerichte slechts ontvangers worden gebaseerd.

   Voor meer bij het bepalen van en het vormen van een controlegroep, verwijs naar [deze sectie](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

* **[!UICONTROL Channel]**: u kunt een specifiek kanaal kiezen of de hypothesesjabloon beschikbaar maken voor alle kanalen in de Adobe Campaign-console door **[!UICONTROL All channels]** in de vervolgkeuzelijst. Als u het malplaatje voor een specifiek kanaal vormt, laat dit u leveringen automatisch filtreren per kanaal wanneer het creëren van de hypothese. [Meer informatie](creating-hypotheses.md)

   ![](assets/response_properties_001.png)

* **[!UICONTROL Execution folder]**: Hiermee kunt u de uitvoeringsmap voor de hypothese opgeven.
* **[!UICONTROL Taken into account in campaign ROI calculation]**: houdt bij de berekening van het rendement van investeringen voor de desbetreffende campagne rekening met het hypotheseresultaat.

### Instellingen voor het uitvoeren van hypothesesjablonen {#hypothesis-template-execution-settings}

De sjablonen **[!UICONTROL General]** kunt u ook de parameters voor het uitvoeren van hypothesen opgeven. De beschikbare opties zijn als volgt:

* **[!UICONTROL Schedule execution for a time of low activity]**: Hiermee kunt u de hypothese plannen om Adobe Campaign-prestaties te optimaliseren. Als deze optie is ingeschakeld, wordt tijdens de downtime in de verwerkingsworkflow van campagnes hypotheseverberekening uitgevoerd.

   ![](assets/response_exec_settings_002.png)

* **[!UICONTROL Priority]**: het niveau dat wordt toegepast op de hypothese om de berekeningsbevelen voor hypothesen uit te splitsen indien er sprake is van gelijktijdige executies.

   ![](assets/response_exec_settings_003.png)

* **[!UICONTROL Automatic execution]**: Indien nodig kunt u een herberekening van de hypothese plannen (bijvoorbeeld als u de indicatoren regelmatig wilt bijwerken tot het einde van de levering).

   ![](assets/response_exec_settings_001.png)

   Pas het volgende proces toe om een schema op te geven:

   1. Klik op de knop **[!UICONTROL Frequency of execution...]** dan de koppeling **[!UICONTROL Change...]** knop.

      ![](assets/response_frequency_execution_001.png)

   1. Configureer de frequentie, de gerelateerde gebeurtenissen en de geldigheidsperiode.

      ![](assets/response_frequency_execution_002.png)

   1. Klikken **[!UICONTROL Finish]** om het programma op te slaan.

      ![](assets/response_frequency_execution_003.png)

* **[!UICONTROL Log SQL queries in journal]**: deze functie is gereserveerd voor deskundige gebruikers. Het laat u een lusje aan de controle van de meethypothese toevoegen om SQL vragen te tonen. Dit laat de opsporing van mogelijke storingen toe als een simulatie met fouten eindigt.
* **[!UICONTROL Keep execution workflow]**: Hiermee kunt u de workflow behouden die automatisch is gegenereerd bij het begin van de hypotheseberekening. In de hypothesen die zijn gemaakt op basis van een sjabloon waarop deze optie is ingeschakeld, is de gegenereerde workflow beschikbaar om het proces te volgen.

   >[!CAUTION]
   >
   >Deze optie moet alleen worden geactiveerd voor foutopsporingsdoeleinden, in het geval van een fout tijdens het uitvoeren van de hypothese.\
   >Bovendien mogen automatisch gegenereerde workflows niet worden gewijzigd. Eventuele wijzigingen zouden elders niet in aanmerking worden genomen voor latere berekeningen.\
   >Als u deze optie hebt ingeschakeld, verwijdert u de workflow nadat deze is uitgevoerd.

### Transacties {#transactions}

Dit tabblad bevat de verschillende velden en tabellen waarmee u de geschiedenis van reacties van ontvangers in termen van transacties kunt opslaan. Zie dit [sectie](../../configuration/using/about-schema-reference.md) voor meer informatie over de tabellen die gewijd zijn aan reactiebeheer.

* **[!UICONTROL Schema (reaction log storage)]**: Selecteer de tabel met reacties van de ontvanger. De out-of-the-box-tabel in Adobe Campaign is **NmsRemaMatchRcp**.
* **[!UICONTROL Transaction schema]**: kiest u de tabel die de hypothesen betreffen, d.w.z. de transactie of de aankooptabel.
* **[!UICONTROL Querying schema]**: de criteria voor het filteren van de hypothese te kiezen.
* **[!UICONTROL Link to individuals]**: Kies de koppeling tussen personen en de tabel die als transactieschema wordt gebruikt.
* **[!UICONTROL Link to the household]**: Selecteer de koppeling naar het huishouden in het transactieschema als u alle leden van een huishouden in een hypothese wilt opnemen. Dit veld is optioneel.
* **[!UICONTROL Transaction date]**: dit veld is optioneel, maar wordt aanbevolen, omdat u hiermee een berekeningsruimte voor hypothesen kunt definiëren.
* **[!UICONTROL Measurement period]**: Hiermee kunt u begin- en einddatums configureren waarin hypothesen worden uitgevoerd en aankooplijnen worden hersteld.

   Wanneer de hypothese verband houdt met een levering, wordt de meting automatisch geactiveerd een paar dagen na de contactdatum voor directe postzendingen of na de leveringsdatum voor e-mail- of sms-leveringen.

   ![](assets/response_measurement_001.png)

   Als de hypothese direct wordt gelanceerd, kan ze worden gedwongen als ze onmiddellijk zou willen worden geactiveerd. Anders, wordt het teweeggebracht automatisch gebaseerd op het gevormde eind van berekeningsdatum, die op de hypotheseaanmaakdatum gebaseerd is. [Meer informatie](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)).

* **[!UICONTROL Transaction/Margin amount]**: deze velden zijn optioneel , zodat u de omzetindicatoren automatisch kunt berekenen . [Meer informatie](hypothesis-tracking.md#indicators)
* **[!UICONTROL Unit amount]**: Hiermee kunt u een bedrag instellen voor het berekenen van inkomsten. [Meer informatie](hypothesis-tracking.md#indicators)

   ![](assets/response_transactions_001.png)

* **[!UICONTROL Additional measures and data]**: Hiermee kunt u aanvullende rapportagemaatregelen of assen opgeven vanuit velden in de verschillende tabellen.
* **[!UICONTROL Update offer proposition status]**: Hiermee kunt u de status van het voorstel wijzigen als een ontvanger van het aanbod door de hypothese wordt geïdentificeerd.

   ![](assets/response_offer_status_001.png)

### Hypothese-omtrek {#hypothesis-perimeter}

Als u de transactietabel en de velden hebt gedefinieerd waarop de hypothese betrekking heeft, kunt u het bereik van de hypothesen verfijnen door de doeltransacties en -leveringen aan de hand van filters op te geven. U kunt ook een JavaScript-script gebruiken om expliciet te verwijzen naar een product waarnaar in de transactietabel wordt verwezen.

* **Filter op transacties**: in de **[!UICONTROL Scope]** kunt u een filter op de hypothese configureren. Dit doet u als volgt:

   1. Klik op de koppeling **[!UICONTROL Edit query]**.

      ![](assets/response_scope_filtering_001.png)

   1. Geef de filtervoorwaarden op.

      ![](assets/response_scope_filtering_002.png)

   1. Selecteer de transactie waarop de hypothese betrekking heeft.

      ![](assets/response_scope_filtering_003.png)

* **Filter op ontvangers**: in de **[!UICONTROL Scope]** kunt u uw hypothese beperken tot alle informatie die aan een bericht is gekoppeld (levering, ontvanger, e-mailadres, service, enzovoort):

   1. Klik op de knop **[!UICONTROL Add a filter]** koppeling, dan **[!UICONTROL Edit query]**.

      ![](assets/response_scope_filtering_004.png)

   1. Geef de filtervoorwaarden op.

      ![](assets/response_scope_filtering_005.png)

   1. Klikken **[!UICONTROL Finish]** om uw query op te slaan.

      ![](assets/response_scope_filtering_006.png)

* **Script**: u kunt een JavaScript-script gebruiken om de hypothesemontages tijdens de uitvoering dynamisch te overladen.

   Om dit te doen, klik **[!UICONTROL Advanced settings]** Voer vervolgens het gewenste script in.

   >[!NOTE]
   >
   >Deze optie is bedoeld voor ervaren gebruikers.

   ![](assets/response_hypothesis_model_creation_011.png)

## Voorbeeld: een hypothesesjabloon voor levering maken {#example--creating-a-hypothesis-template-on-a-delivery}

In dit voorbeeld, gaan wij een hypothesemalplaatje op een direct-mailtype levering tot stand brengen. De transactietabel (**Aankopen** in ons voorbeeld ) waarop de hypothesen gebaseerd zullen zijn , bevat aankooplijnen die gekoppeld zijn aan artikelen of producten . Wij willen ons model vormen om hypotheses op artikelen of producten in de aankooplijst tot stand te brengen.

1. Ga in de Adobe Campaign-verkenner naar de **[!UICONTROL Resources > Templates > Hypothesis templates]** knooppunt.
1. Klikken **[!UICONTROL New]** om een sjabloon te maken.

   ![](assets/response_hypothesis_model_example_001.png)

1. Wijzig het sjabloonlabel.

   ![](assets/response_hypothesis_model_example_002.png)

1. Selecteren **[!UICONTROL Deliveries]** als hypothesetype.
1. Geef aan dat de levering een controlegroep kan bevatten door het desbetreffende vak in te schakelen.
1. Kies de optie **[!UICONTROL Direct mail]** kanaal.

   >[!NOTE]
   >
   >Aangezien de sjabloon specifiek is voor direct-mailleveringen, kunnen hypothesen die met dit model worden gemaakt, niet aan andere leveringstypen worden gekoppeld.

1. In de **[!UICONTROL Transactions]** selecteert u de tabel met reacties bij ontvangers.

   ![](assets/response_hypothesis_model_example_006.png)

1. In de **[!UICONTROL Transactions schema]** , kiest u uw aankooptabel.

   ![](assets/response_hypothesis_model_example_007.png)

1. Selecteer aankooplijnen in het dialoogvenster **[!UICONTROL Querying schema]** veld.

   ![](assets/response_hypothesis_model_example_008.png)

1. Kies de ontvangers die aan de aankooptabel zijn gekoppeld.

   ![](assets/response_hypothesis_model_example_009.png)

1. Selecteer het veld dat is gekoppeld aan de aankoopdatum.

   Hiermee kunt u een tijdkader voor hypothesen definiëren. Dit werkgebied is niet verplicht, maar wordt wel aanbevolen.

   ![](assets/response_hypothesis_model_example_010.png)

1. Configureer de berekeningsperiode 5 tot 25 dagen.

   ![](assets/response_hypothesis_model_example_005.png)

1. In de **[!UICONTROL Scope]** tabblad, klikt u op **[!UICONTROL Edit query]** om een filter op hypothesen te maken.

   ![](assets/response_hypothesis_model_example_011.png)

   Met de gemaakte sjabloon kunt u dus hypothesen uitvoeren op de producten of artikelen in de aankooptabel.

1. Klikken **[!UICONTROL Save]** om de sjabloon op te nemen.
