---
product: campaign
title: Doelgroep van marketingcampagne
description: Leer hoe u het publiek van uw marketingcampagnes definieert
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
exl-id: 04daa67c-4057-42a7-b993-a6eddf2b883d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 3%

---

# De doelgroep van uw campagnes selecteren {#marketing-campaign-deliveries}

In een marketingcampagne kunt u voor elke levering het volgende definiëren:

* Het publiek - leer meer in [Het publiek in een werkschema bouwen](#building-the-main-target-in-a-workflow) en [Het selecteren van de doelpopulatie](#selecting-the-target-population).
* A control group - Learn more in [this section](#defining-a-control-group).
* Zaadadressen - leer meer in [deze sectie](../../delivery/using/about-seed-addresses.md).

Sommige van deze informatie kan van [campagnemalplaatje](../../campaign/using/marketing-campaign-templates.md#campaign-templates) worden geërft.

Om het leveringsdoel te bouwen, kunt u het filtreren criteria voor de ontvangers in het gegevensbestand bepalen. Deze ontvankelijke selectiemodus wordt voorgesteld in [deze sectie](../../delivery/using/steps-defining-the-target-population.md).

## Naar een groep verzenden

U kunt een populatie in een lijst importeren en deze lijst vervolgens als doel instellen in leveringen. Volg de onderstaande stappen om dit te doen:

1. Bewerk de desbetreffende levering en klik op de koppeling **[!UICONTROL To]** om de doelpopulatie te wijzigen.

1. Selecteer op het tabblad **[!UICONTROL Main target]** de optie **[!UICONTROL Defined via the database]** en klik **[!UICONTROL Add]** om ontvangers te selecteren.

![](assets/s_user_target_group_add.png)

1. Kies **[!UICONTROL A list of recipients]** en klik **[!UICONTROL Next]** om het te selecteren.

![](assets/s_user_target_group_next.png)

## Het publiek opbouwen in een campagneworkflow {#building-the-main-target-in-a-workflow}

Het hoofddoel van een levering kan ook in de campagnewerkstroom worden bepaald: in deze grafische omgeving kunt u een doel maken met behulp van query&#39;s, tests en operatoren: verenigen, dedupliceren, delen, enz.

>[!IMPORTANT]
>
>U mag niet meer dan 28 workflows toevoegen aan een campagne. Buiten deze limiet zijn extra workflows niet zichtbaar in de interface en kunnen fouten genereren.

### De workflow {#creating-a-targeting-workflow} maken

Het richten kan door een combinatie filtervoorwaarden in een grafische opeenvolging in een werkschema worden tot stand gebracht. U kunt populaties en subpopulaties maken die op basis van uw vereisten worden aangepast. Als u de werkstroomeditor wilt weergeven, klikt u op het tabblad **[!UICONTROL Targeting and workflows]** in het campagnedashboard.

![](assets/s_ncs_user_edit_op_wf_link.png)

De doelpopulatie wordt geëxtraheerd uit de Adobe Campaign-database via een of meer query&#39;s die in een workflow zijn geplaatst. Leren hoe te om een vraag te bouwen, verwijs naar [deze sectie](../../workflow/using/query.md).

U kunt query&#39;s starten en populaties delen via vakken zoals Union, Intersection, Sharing, Exclusion enzovoort.

Selecteer de objecten in de lijsten links van de werkruimte en koppel ze om het doel samen te stellen.

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

In het diagram, verbind omhoog het richten en het plannen van vragen die voor doelbouw in het diagram worden vereist. U kunt het richten uitvoeren terwijl de bouw bezig is om de bevolking te controleren die uit het gegevensbestand wordt gehaald.

>[!NOTE]
>
>De voorbeelden en de procedure voor het bepalen van vragen worden voorgesteld in [deze sectie](../../workflow/using/query.md).

Het linkergedeelte van de editor bevat een bibliotheek met grafische objecten die activiteiten vertegenwoordigen. Het eerste lusje bevat de het richten activiteiten, en het tweede lusje bevat de stroom-controle activiteiten, die af en toe worden gebruikt om het richten activiteiten te coördineren.

De functies voor het uitvoeren en opmaken van werkstromen voor het opgeven van doelen zijn toegankelijk via de werkbalk van de diagrameditor.

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>De activiteiten beschikbaar om het diagram evenals alle vertoning en lay-outeigenschappen te bouwen zijn gedetailleerd in [Automatiseren met werkschema&#39;s](../../workflow/using/architecture.md) gids.

U kunt verschillende doelworkflows voor één campagne maken. Een workflow toevoegen:

1. Ga naar de hogere linkersectie van de streek van de werkschemaverwezenlijking, klik met de rechtermuisknop aan, en selecteer **[!UICONTROL Add]**. U kunt de **[!UICONTROL New]** knoop ook gebruiken die boven deze streek wordt gevestigd.

   ![](assets/s_ncs_user_add_a_wf.png)

1. Selecteer de sjabloon **[!UICONTROL New workflow]** en geef deze workflow een naam.
1. Klik **[!UICONTROL OK]** om verwezenlijking van het werkschema te bevestigen, en dan het diagram voor deze werkschema tot stand te brengen.

### De workflow uitvoeren {#executing-a-workflow}

Doelworkflows kunnen handmatig worden gestart via de knop **[!UICONTROL Start]** op de werkbalk, op voorwaarde dat u de juiste rechten hebt.

Het richten kan voor automatische uitvoering volgens een programma (planner) of een gebeurtenis (extern signaal, dossierinvoer, enz.) worden geprogrammeerd.

De acties met betrekking tot het uitvoeren van de doelworkflow (starten, stoppen, pauzeren, enz.) zijn **asynchrone** processen: de opdracht wordt opgeslagen en wordt van kracht zodra de server beschikbaar is om deze toe te passen.

Met de werkbalkpictogrammen kunt u actie ondernemen met betrekking tot de uitvoering van de doelworkflow.

* Starten of opnieuw starten

   * Met het pictogram **[!UICONTROL Start]** kunt u de doelworkflow starten. Wanneer u op dit pictogram klikt, worden alle activiteiten zonder een invoerovergang geactiveerd (behalve sprongen met eindpunten).

      ![](assets/s_user_segmentation_start.png)

      De server houdt rekening met het verzoek, zoals aangetoond door zijn status:

      ![](assets/s_user_segmentation_start_status.png)

      De processtatus verandert in **[!UICONTROL Started]**.

   * U kunt de doelworkflow opnieuw starten via het juiste werkbalkpictogram. Deze opdracht kan handig zijn als het pictogram **[!UICONTROL Start]** niet beschikbaar is, bijvoorbeeld wanneer het stopzetten van de doelworkflow wordt uitgevoerd. Klik in dit geval op het pictogram **[!UICONTROL Restart]** om te anticiperen op het opnieuw opstarten. De server houdt rekening met het verzoek, aangezien zijn status toont:

      ![](assets/s_user_segmentation_restart_status.png)

      Het proces gaat dan **[!UICONTROL Started]** status in.

* Stoppen of pauzeren

   * Met de werkbalkpictogrammen kunt u een actieve doelworkflow stoppen of pauzeren.

      Wanneer u op **[!UICONTROL Pause]** klikt, worden actieve bewerkingen **[!UICONTROL are not]** gepauzeerd, maar wordt geen andere activiteit gestart tot de volgende keer dat u de computer opnieuw opstart.

      ![](assets/s_user_segmentation_pause.png)

      De server houdt rekening met het bevel, aangezien zijn status toont:

      ![](assets/s_user_segmentation_pause_status.png)

      U kunt een doelworkflow ook automatisch pauzeren wanneer de uitvoering een bepaalde activiteit bereikt. Om dit te doen, klik de activiteit met de rechtermuisknop aan waarvan het richten werkschema moet worden gepauzeerd, en selecteer **[!UICONTROL Enable but do not execute]**.

      ![](assets/s_user_segmentation_donotexecute.png)

      Deze configuratie wordt getoond door een speciaal pictogram.

      ![](assets/s_user_segmentation_pause_activity.png)

      >[!NOTE]
      >
      >Deze optie is handig tijdens het ontwerpen en testen van campagnes die u op geavanceerde wijze wilt richten.

      Klik **[!UICONTROL Start]** om uitvoering te hervatten.

   * Klik op het pictogram **[!UICONTROL Stop]** om de actieve uitvoering te stoppen.

      ![](assets/s_user_segmentation_stop.png)

      De server houdt rekening met het bevel, aangezien zijn status toont:

      ![](assets/s_user_segmentation_stop_status.png)
   U kunt een doelworkflow ook automatisch stoppen wanneer de uitvoering een activiteit bereikt. Om dit te doen, klik de activiteit met de rechtermuisknop aan waarvan het richten werkschema zal worden tegengehouden, en selecteer **[!UICONTROL Do not activate]**.

   ![](assets/s_user_segmentation_donotactivate.png)

   ![](assets/s_user_segmentation_unactivation.png)

   Deze configuratie wordt getoond door een speciaal pictogram.

   >[!NOTE]
   >
   >Deze optie is handig tijdens het ontwerpen en testen van campagnes die u op geavanceerde wijze wilt richten.

* Onvoorwaardelijke stop

   In de Ontdekkingsreiziger, selecteer **[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]** om tot elke campagnewerkschema&#39;s toegang te hebben en op te treden.

   U kunt de workflow onvoorwaardelijk stoppen door op het pictogram **[!UICONTROL Actions]** te klikken en **[!UICONTROL Unconditional]** stop te selecteren. Deze actie beëindigt uw campagnewerkschema.

   ![](assets/s_user_segmentation_stop_unconditional.png)

## Een besturingsgroep {#defining-a-control-group} toevoegen

Een controlegroep is een populatie die de levering niet zal ontvangen; het wordt gebruikt om het gedrag en de impact van de campagne na de levering te volgen door een vergelijking te maken met het gedrag van de doelpopulatie, die de levering heeft ontvangen.

De controlegroep kan uit het belangrijkste doel worden gehaald en/of uit een specifieke groep of een vraag komen.

### De besturingsgroep voor een campagne activeren {#activating-the-control-group-for-a-campaign}

U kunt een controlegroep op campagneniveau bepalen, waarbij de controlegroep op elke levering van de betrokken campagne zal worden toegepast.

1. Bewerk de desbetreffende campagne en klik op het tabblad **[!UICONTROL Edit]**.
1. Klik op **[!UICONTROL Advanced campaign settings]**.

   ![](assets/s_ncs_user_edit_op_target.png)

1. Selecteer de optie **[!UICONTROL Enable and edit control group configuration]**.
1. Klik **[!UICONTROL Edit...]** om de controlegroep te vormen.

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

De configuratieprocedure wordt voorgesteld in [Het halen van de controlegroep van het belangrijkste doel](#extracting-the-control-group-from-the-main-target) en [het toevoegen van een controlegroep](#adding-a-population).

### Activeer de controlegroep voor een levering {#activating-the-control-group-for-a-delivery}

U kunt een controlegroep op leveringsniveau bepalen, in welk geval de controlegroep op elke levering van de betrokken campagne zal worden toegepast.

Door gebrek, is de configuratie van de controlegroep die op het campagneniveau wordt bepaald op elke levering van die campagne van toepassing. U kunt, echter, de controlegroep voor een individuele levering aanpassen.

>[!NOTE]
>
>Als u een controlegroep voor een campagne hebt bepaald, en u het voor een levering ook vormt verbonden aan deze campagne, slechts zal de controlegroep die voor de levering wordt bepaald worden toegepast.

1. Bewerk de desbetreffende levering en klik vervolgens op de koppeling **[!UICONTROL To]** in de sectie **[!UICONTROL Email parameters]**.

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. Klik op de tab **[!UICONTROL Control group]** en selecteer **[!UICONTROL Enable and edit control group configuration]**.
1. Klik **[!UICONTROL Edit...]** om de controlegroep te vormen.

De configuratieprocedure wordt voorgesteld in [Het halen van de controlegroep van het belangrijkste doel](#extracting-the-control-group-from-the-main-target) en [het toevoegen van een controlegroep](#adding-a-population).

### Extraheer de controlegroep van het belangrijkste doel {#extracting-the-control-group-from-the-main-target}

U kunt ontvangers extraheren uit het hoofddoel van de levering. In dit geval, zullen de ontvangers van het doel van leveringsacties worden genomen die door deze configuratie worden beïnvloed. Deze extractie kan willekeurig zijn of het resultaat zijn van het sorteren van de ontvangers.

![](assets/s_ncs_user_extract_from_target_population.png)

Als u een controlegroep wilt extraheren, schakelt u de controlegroep voor de campagne of levering in en selecteert u een van de volgende opties: **[!UICONTROL Activate random sampling]** of **[!UICONTROL Keep only the first records after sorting]**.

* **[!UICONTROL Activate random sampling]** : bij deze optie wordt steekproefsgewijze bemonstering toegepast op de ontvangers in de doelpopulatie. Als u vervolgens de drempel instelt op 100, bestaat de controlegroep uit 100 ontvangers die willekeurig uit de doelpopulatie zijn geselecteerd. De willekeurige bemonstering is afhankelijk van de database-engine.
* **[!UICONTROL Keep only the first records after sorting]** : met deze optie kunt u een limiet definiëren op basis van een of meer sorteervolgorden. Als u het **[!UICONTROL Age]** gebied als sorterend criterium selecteert en dan 100 als drempel bepaalt, zal de controlegroep uit de 100 jongste ontvangers worden samengesteld. Het zou bijvoorbeeld interessant kunnen zijn om een controlegroep te definiëren die ontvangers bevat die weinig aankopen doen, of ontvangers die vaak aankopen doen, en om hun gedrag te vergelijken met dat van de gecontacteerde ontvangers.

Klik **[!UICONTROL Next]** om de sorteervolgorde (indien nodig) te bepalen en de ontvankelijke beperkingsmodus te selecteren.

![](assets/s_ncs_user_edit_op_target_param.png)

Deze configuratie is gelijk aan een deelactiviteit in de workflow, waarmee u het doel kunt onderverdelen in subsets. De controlegroep is één van deze subsets. Raadpleeg [deze sectie](../../workflow/using/architecture.md) voor meer informatie.

### Een nieuwe populatie gebruiken als een controlegroep {#adding-a-population}

U kunt een nieuwe bevolking bepalen die als controlegroep moet worden gebruikt. Deze populatie kan uit een groep ontvangers komen of u kunt het tot stand brengen via een specifieke vraag.

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>Adobe Campaign query editor wordt weergegeven in [deze sectie](../../workflow/using/query.md).


#### Video over zelfstudie {#create-email-video}

In deze video wordt uitgelegd hoe u een campagne en een e-mail maakt in Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

Er zijn [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl) extra instructievideo&#39;s voor campagnes beschikbaar.
