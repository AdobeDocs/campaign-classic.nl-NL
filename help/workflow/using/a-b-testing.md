---
solution: Campaign Classic
product: campaign
title: A/B-tests
description: A/B-tests
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1347'
ht-degree: 1%

---


# A/B-tests{#a-b-testing}

Als u meerdere inhoud voor een e-maillevering hebt en u wilt weten welke versie de grootste invloed heeft op de beoogde populatie, kunt u de verschillende versies naar sommige van uw ontvangers sturen, vervolgens de versie met de hoogste successnelheid selecteren en deze naar de rest van uw ontvangers sturen.

In dit geval gaan we twee inhoud van de e-maillevering vergelijken via een doelworkflow. Het bericht en de tekst zijn identiek in beide leveringen: alleen de layout wordt gewijzigd.

De doelgroep bestaat uit drie groepen: twee testgroepen en de resterende populatie. Een verschillende versie van de levering wordt verzonden naar elke testgroep. Na de levering, wordt een 5 dagen wachttijdperiode gevormd alvorens de resultaten van de beste open tarieven te verzamelen. De inhoud van de levering met de hoogste score wordt dan teruggekregen door een manuscript en verzonden naar de bevolking die niet als testgroep werd gebruikt.

Houd er rekening mee dat de criteria die bepalen welke levering het beste is, kunnen worden aangepast aan uw behoeften. Het kan de open tarief, het klikthrough tarief, het abonnementstarief, reactiviteit, enz. zijn.

Bovendien heeft de test die in dit gebruiksgeval wordt beschreven slechts betrekking op twee leveringen, maar u kunt zo veel versies testen als nodig is. Voeg gewoon activiteiten toe aan de workflow.

Voer de volgende stappen uit om de A/B-test te maken:

* [Stap 1: Een doelworkflow maken](#step-1--creating-a-targeting-workflow)
* [Stap 2: Bezig met configureren van populatiemonsters](#step-2--configuring-population-samples)
* [Stap 3: Twee leveringssjablonen maken](#step-3--creating-two-delivery-templates)
* [Stap 4: De leveringen in de workflow configureren](#step-4--configuring-the-deliveries-in-the-workflow)
* [Stap 5: Script maken](#step-5--creating-the-script)
* [Stap 7: De workflow starten](#step-7--starting-the-workflow)
* [Stap 8: Het resultaat](#step-8--analyzing-the-result) analyseren.

## Stap 1: Een doelworkflow {#step-1--creating-a-targeting-workflow} maken

U moet uw workflow maken op het tabblad **[!UICONTROL Targeting and Workflows]** van een campagne. Het bestaat uit een **[!UICONTROL Query]** activiteit, een **[!UICONTROL Split]** activiteit verbonden met twee **[!UICONTROL Email delivery]** activiteiten, een **[!UICONTROL Wait]** activiteit, een **[!UICONTROL JavaScript code]** activiteit, en een **[!UICONTROL Delivery]** activiteit.

1. Als u dit nog niet hebt gedaan, creeer een campagne (voor meer op dit, verwijs naar [sectie](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Ga naar het tabblad **[!UICONTROL Targeting and Workflows]**. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Wijzig het label van de bestaande workflow of klik op **[!UICONTROL Add]** om een nieuwe te maken (voor meer informatie hierover raadpleegt u deze [sectie](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Gebruik de muis om activiteiten naar het werkstroomdiagram te slepen, inclusief een **[!UICONTROL Query]** (**[!UICONTROL Target]** tab), een **[!UICONTROL Split]** (**[!UICONTROL Target]** tab), twee **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** tab), een **[!UICONTROL Wait]** activiteit (**[!UICONTROL Flow Control]** tab), een **[!UICONTROL JavaScript code]** activiteit (**[!UICONTROL Actions]** tab) en een **[!UICONTROL Delivery]** activiteit (**[!UICONTROL Actions]** tabblad).

![](assets/use_case_abtesting_targetwkfl_004.png)

## Stap 2: Bezig met configureren van populatiemonsters {#step-2--configuring-population-samples}

### Het vormen van de activiteit van de Vraag {#configuring-the-query-activity}

* Dubbelklik op de activiteit **[!UICONTROL Query]**.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Klik op de koppeling **[!UICONTROL Edit query]** en selecteer de ontvangers die u als doel wilt instellen.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Koppel de **[!UICONTROL Query]** activiteit aan **[!UICONTROL Split]** activiteit.

   ![](assets/use_case_abtesting_createrecipients_003.png)

### De splitsingsactiviteit {#configuring-the-split-activity} configureren

Met deze activiteit kunt u verschillende populaties maken: degene die levering A ontvangt, degene die levering B ontvangt, en de resterende populatie. Door willekeurige selectie te gebruiken, kunt u zich richten op slechts een deel van de populatie van elke levering.

1. Bezig met maken van populatie A:

   * Dubbelklik op de activiteit **[!UICONTROL Split]**.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * Wijzig in het bestaande tabblad het label in populatie A.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * Selecteer de optie **[!UICONTROL Limit the selected records]**.

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * Klik op de koppeling **[!UICONTROL Edit]**, selecteer **[!UICONTROL Activate random sampling]** en klik op **[!UICONTROL Next]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * Stel de drempel in op 10% en klik op **[!UICONTROL Finish]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. Bezig met maken van populatie B:

   * Klik **[!UICONTROL Add]** om een nieuw lusje voor populatie B tot stand te brengen.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * Beperk de bevolking tot 10% zoals eerder.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. Creëren van de resterende populatie:

   * Ga naar het tabblad **[!UICONTROL General]**. 

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * Selecteer **[!UICONTROL Generate complement]**.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * Wijzig het label om aan te geven dat deze populatie geen A of B bevat en klik op **[!UICONTROL OK]** om de activiteit te sluiten.

      ![](assets/use_case_abtesting_createrecipients_013.png)

## Stap 3: Twee leveringssjablonen maken {#step-3--creating-two-delivery-templates}

We willen nu twee leveringssjablonen maken. Naar elke sjabloon wordt verwezen in een **[!UICONTROL Email delivery]**-activiteit die is gekoppeld aan de **[!UICONTROL Split]**-activiteit. Raadpleeg deze [sectie](../../delivery/using/about-templates.md) voor meer informatie.

1. Ga naar de **[!UICONTROL Resources > Delivery template]** omslag.
1. Dupliceer **[!UICONTROL Email]** leveringsmalplaatje.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Maak de inhoud die moet worden gebruikt voor levering A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Herhaal dit proces om een sjabloon voor levering B te maken.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

## Stap 4: De leveringen in de workflow configureren {#step-4--configuring-the-deliveries-in-the-workflow}

De volgende stap is de leveringen te vormen. Zij zijn bestemd voor de drie populaties die in de vorige fase zijn ontstaan: [Stap 2: Bezig met configureren van populatiemonsters](#step-2--configuring-population-samples). Met de eerste twee leveringen kunt u verschillende inhoud naar populatie A en B sturen. De derde levering is bestemd voor de bevolking die noch A noch B heeft ontvangen. De inhoud ervan wordt berekend met behulp van een script en is gelijk aan A of B, afhankelijk van welke score de hoogste open snelheid heeft behaald. We moeten een wachtperiode configureren voor de derde levering, om het resultaat van de leveringen A en B te achterhalen. Dit is waarom de derde levering een **[!UICONTROL Wait]** activiteit omvat.

1. Ga naar **[!UICONTROL Split]** activiteit en verbind de overgang die voor populatie A aan één van de e-mailleveringen wordt bestemd reeds in het werkschema.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Dubbelklik op de levering om deze te openen.
1. Selecteer de sjabloon voor levering A in de vervolgkeuzelijst.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Klik **[!UICONTROL Continue]** om de levering te bekijken, dan sparen het.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Koppel de overgang van de **[!UICONTROL Split]** activiteit bestemd voor populatie B aan de tweede e-maillevering.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Open de levering en selecteer het malplaatje in levering B, dan sparen de levering.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Koppel de overgang bestemd voor de resterende populatie aan de **[!UICONTROL Wait]** activiteit.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Open de **[!UICONTROL Wait]** activiteit en vorm een wachttijd van 5 dagen.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Koppel de **[!UICONTROL Wait]** activiteit aan **[!UICONTROL JavaScript code]** activiteit.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

## Stap 5: Het script {#step-5--creating-the-script} maken

De keus van de leveringsinhoud die voor de resterende bevolking wordt bestemd wordt berekend door een manuscript. Met dit script wordt de informatie over de levering met de hoogste snelheid van het openen hersteld en wordt de inhoud naar de uiteindelijke levering gekopieerd.

### Voorbeeld van een script {#example-of-a-script}

Het volgende script kan worden gebruikt zoals in de doelworkflow. Raadpleeg [Implementatie](#implementation) voor meer informatie hierover.

```
 // query the database to find the winner (best open rate)
   var winner = xtk.queryDef.create(
     <queryDef schema="nms:delivery" operation="get">
       <select>
         <node expr="@id"/>
         <node expr="@label"/>
         <node expr="[@operation-id]"/>
         <node expr="[@workflow-id]"/>
       </select>
       <where>
         <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
       </where>
       <orderBy>
         <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
       </orderBy>
     </queryDef>).ExecuteQuery()
   
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)

   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"

   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]

   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
 
   // save the delivery in database
   delivery.save()
 
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
```

Raadpleeg [Details van het script](#details-of-the-script) voor een gedetailleerde uitleg van het script.

### Implementatie {#implementation}

1. Open uw **[!UICONTROL JavaScript code]** activiteit.
1. Kopieer het script dat wordt aangeboden in [Voorbeeld van een script](#example-of-a-script) naar het venster **[!UICONTROL JavaScript code]**.

   ![](assets/use_case_abtesting_configscript_002.png)

1. Voer in het veld **[!UICONTROL Label]** de naam van het script in, dat wil zeggen

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. Sluit de **[!UICONTROL JavaScript code]** activiteit.
1. Sla uw workflow op.

### Details van het script {#details-of-the-script}

In deze sectie worden de verschillende delen van het script en de bijbehorende uitvoermodus beschreven.

* Het eerste deel van het script is een query. Met de opdracht **queryDef** kunt u de leveringen herstellen die zijn gemaakt door de doelworkflow uit te voeren en deze te sorteren op basis van de geschatte snelheid van de openen. De informatie van de levering met de hoogste snelheid van de opening wordt dan hersteld.****

   ```
   // query the database to find the winner (best open rate)
      var winner = xtk.queryDef.create(
        <queryDef schema="nms:delivery" operation="get">
          <select>
            <node expr="@id"/>
            <node expr="@label"/>
            <node expr="[@operation-id]"/>
          </select>
          <where>
            <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
          </where>
          <orderBy>
            <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
          </orderBy>
        </queryDef>).ExecuteQuery()
   ```

* De levering met de hoogste snelheid van opent wordt gedupliceerd.

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* Het label van de gedupliceerde levering wordt gewijzigd en het woord **final** wordt eraan toegevoegd.

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* De levering wordt gekopieerd naar het campagnedashboard.

   ```
   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]
   ```

   ```
   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
   ```

* De levering wordt opgeslagen in de database.

   ```
   // save the delivery in database
   delivery.save()
   ```

* De unieke id van de gedupliceerde levering wordt opgeslagen in de workflowvariabele.

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

### Andere selectiecriteria {#other-selection-criteria}

In het bovenstaande voorbeeld kunt u de inhoud van een levering selecteren op basis van de snelheid waarmee e-mails worden geopend. U kunt het aanpassen om zich op andere levering-specifieke indicatoren te baseren:

* Best geklikt doorvoer: `[indicators/@recipientClickRatio]`,
* Hoogste reactiviteitspercentage (e-mail geopend en klik in het bericht): `[indicators/@reactivity]`,
* Laagste klachtenpercentage: `[indicators/@refusedRatio]` (gebruik de false waarde voor het kenmerk sortDesc),
* Hoogste conversiesnelheid: `[indicators/@transactionRatio]`,
* Aantal bezochte pagina&#39;s na ontvangst van een bericht: `[indicators/@totalWebPage]`,
* Laagste abonnement: `[indicators/@optOutRatio]`,
* Transactiebedrag: `[indicators/@amount]`.

## Stap 6: Definiëren van de uiteindelijke levering {#step-6--defining-the-final-delivery}

Wanneer het script is gemaakt om de testwinnaar A/B te selecteren, kunt u de parameters van de uiteindelijke levering definiëren.

1. Sluit de **[!UICONTROL JavaScript code]** activiteit aan de resterende **[!UICONTROL Delivery]** activiteit aan.
1. Open de **[!UICONTROL Delivery]** activiteit.
1. Schakel de optie **[!UICONTROL Generate an outbound transition]** uit om de workflow met deze activiteit te voltooien.
1. Laat de standaardwaarden van de andere opties ongewijzigd.

   ![](assets/ab_test_final_delivery.png)

Door de levering voor te bereiden die is opgegeven in de overgang (gedefinieerd via de **[!UICONTROL Javascript Code]**-activiteit), kunt u deze goedkeuren en het verzenden starten, zoals beschreven in de volgende stap.

## Stap 7: De werkstroom starten {#step-7--starting-the-workflow}

1. Klik op **[!UICONTROL Start]** de workflow.

   ![](assets/use_case_abtesting_startwkfl_001.png)

1. Doel en inhoud voor de leveringen A en B goedkeuren via het campagnemdashboard.
1. Levering bevestigen.
1. Wacht tot het einde van de periode van 5 dagen om te weten te komen welke inhoud na levering openingsresultaten werd berekend.

   ![](assets/use_case_abtesting_startwkfl_002.png)

   In dit geval is template B gekozen.

1. Wanneer de inhoud van de derde levering is bepaald, keurt u het doel en de inhoud goed.

## Stap 8: Het resultaat {#step-8--analyzing-the-result} analyseren

Nadat de testleveringen zijn verzonden, kunt u controleren naar welke ontvanger(s) zij zijn verzonden en of zij al dan niet zijn geopend.

* Om te weten te komen welke ontvangers zijn gericht, open een levering via het campagnesdashboard en klik **[!UICONTROL Delivery]** tabel.

   ![](assets/use_case_abtesting_analysis_001.png)

* Als u wilt weten of de levering is geopend, gaat u naar het tabblad **[!UICONTROL Tracking]**.

   ![](assets/use_case_abtesting_analysis_002.png)

* Ben met andere levering vergelijkbaar.

   ![](assets/use_case_abtesting_analysis_003.png)

In ons voorbeeld heeft levering B de hoogste open snelheid gehaald. Dit betekent dat inhoud B wordt gebruikt voor de uiteindelijke levering.

![](assets/use_case_abtesting_analysis_004.png)

