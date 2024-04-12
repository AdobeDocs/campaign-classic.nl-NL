---
product: campaign
title: Doelgroep van marketingcampagne
description: Leer hoe u het publiek van uw marketingcampagnes definieert
role: User
feature: Campaigns, Audiences
exl-id: 04daa67c-4057-42a7-b993-a6eddf2b883d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 0%

---

# De doelgroep van uw campagnes selecteren {#marketing-campaign-deliveries}

In een marketingcampagne kunt u voor elke levering het volgende definiëren:

* Het publiek - Meer informatie in [Het publiek opbouwen in een workflow](#building-the-main-target-in-a-workflow) en [De doelpopulatie selecteren](#selecting-the-target-population).
* Een controlegroep - Meer informatie in [deze sectie](#defining-a-control-group).
* Zaadadressen - Meer informatie in [deze sectie](../../delivery/using/about-seed-addresses.md).

Sommige van deze gegevens kunnen worden overgeërfd van [campagnemalsjabloon](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

Om het leveringsdoel te bouwen, kunt u het filtreren criteria voor de ontvangers in het gegevensbestand bepalen. Deze selectiemodus voor ontvangers wordt weergegeven in [deze sectie](../../delivery/using/steps-defining-the-target-population.md).

## Naar een groep verzenden

U kunt een populatie in een lijst importeren en deze lijst vervolgens als doel instellen in leveringen. Hiervoor voert u de volgende stappen uit:

1. Bewerk de desbetreffende levering en klik op de knop **[!UICONTROL To]** koppeling om de doelgroep te veranderen.

1. In de **[!UICONTROL Main target]** selecteert u de **[!UICONTROL Defined via the database]** en klik op **[!UICONTROL Add]** om ontvangers te selecteren.

![](assets/s_user_target_group_add.png)

1. Kies **[!UICONTROL A list of recipients]** en klik op **[!UICONTROL Next]** om het te selecteren.

![](assets/s_user_target_group_next.png)

## Het publiek samenstellen in een campagneworkflow {#building-the-main-target-in-a-workflow}

Het hoofddoel van een levering kan ook worden gedefinieerd in de campagneworkflow: met deze grafische omgeving kunt u een doel maken aan de hand van query&#39;s, tests en operatoren: union, deduplicatie, sharing, enzovoort.

>[!IMPORTANT]
>
>U mag niet meer dan 28 workflows toevoegen aan een campagne. Buiten deze limiet zijn extra workflows niet zichtbaar in de interface en kunnen fouten genereren.

### De workflow maken {#creating-a-targeting-workflow}

Het richten kan door een combinatie filtervoorwaarden in een grafische opeenvolging in een werkschema worden tot stand gebracht. U kunt populaties en subpopulaties maken die op basis van uw vereisten worden aangepast. Als u de werkstroomeditor wilt weergeven, klikt u op de knop **[!UICONTROL Targeting and workflows]** in het campagnedashboard.

![](assets/s_ncs_user_edit_op_wf_link.png)

De doelpopulatie wordt geëxtraheerd uit de Adobe Campaign-database via een of meer query&#39;s die in een workflow zijn geplaatst. Om te leren hoe te om een vraag te bouwen, verwijs naar [deze sectie](../../workflow/using/query.md).

U kunt query&#39;s starten en populaties delen via vakken zoals Union, Intersection, Sharing, Exclusion enzovoort.

Selecteer de objecten in de lijsten links van de werkruimte en koppel ze om het doel samen te stellen.

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

In het diagram, verbind omhoog het richten en het plannen van vragen die voor doelbouw in het diagram worden vereist. U kunt het richten uitvoeren terwijl de bouw bezig is om de bevolking te controleren die uit het gegevensbestand wordt gehaald.

>[!NOTE]
>
>De voorbeelden en de procedure om vragen te bepalen worden voorgesteld in [deze sectie](../../workflow/using/query.md).

Het linkergedeelte van de editor bevat een bibliotheek met grafische objecten die activiteiten vertegenwoordigen. Het eerste lusje bevat de het richten activiteiten, en het tweede lusje bevat de stroom-controle activiteiten, die af en toe worden gebruikt om het richten activiteiten te coördineren.

De functies voor het uitvoeren en opmaken van werkstromen voor het opgeven van doelen zijn toegankelijk via de werkbalk van de diagrameditor.

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>De activiteiten die beschikbaar zijn om het diagram te bouwen en alle weergave- en lay-outfuncties worden beschreven in de [Automatiseren met workflows](../../workflow/using/architecture.md) hulplijn.

U kunt verschillende doelworkflows voor één campagne maken. Een workflow toevoegen:

1. Ga naar het gedeelte linksboven van de zone waar de workflow wordt gemaakt, klik met de rechtermuisknop en selecteer **[!UICONTROL Add]**. U kunt ook de opdracht **[!UICONTROL New]** boven deze zone.

   ![](assets/s_ncs_user_add_a_wf.png)

1. Selecteer de **[!UICONTROL New workflow]** sjabloon en noem deze workflow.
1. Klikken **[!UICONTROL OK]** om de creatie van het werkschema te bevestigen, en dan het diagram voor deze werkschema tot stand te brengen.

### De workflow uitvoeren {#executing-a-workflow}

Doelworkflows kunnen handmatig worden gestart via de **[!UICONTROL Start]** op de werkbalk, op voorwaarde dat u de juiste rechten hebt.

Het richten kan voor automatische uitvoering volgens een programma (planner) of een gebeurtenis (extern signaal, dossierinvoer, enz.) worden geprogrammeerd.

De acties met betrekking tot het uitvoeren van de doelworkflow (starten, stoppen, pauzeren, enz.) zijn **asynchroon** processen: de opdracht wordt opgeslagen en wordt van kracht zodra de server beschikbaar is om deze toe te passen.

Met de werkbalkpictogrammen kunt u actie ondernemen met betrekking tot de uitvoering van de doelworkflow.

* Starten of opnieuw starten

   * De **[!UICONTROL Start]** kunt u de doelworkflow starten. Wanneer u op dit pictogram klikt, worden alle activiteiten zonder een invoerovergang geactiveerd (behalve sprongen met eindpunten).

     ![](assets/s_user_segmentation_start.png)

     De server houdt rekening met het verzoek, zoals aangetoond door zijn status:

     ![](assets/s_user_segmentation_start_status.png)

     De processtatus verandert in **[!UICONTROL Started]**.

   * U kunt de doelworkflow opnieuw starten via het juiste werkbalkpictogram. Deze opdracht kan handig zijn als de opdracht **[!UICONTROL Start]** pictogram is niet beschikbaar, bijvoorbeeld wanneer het activeren van werkstroom wordt uitgevoerd. Klik in dit geval op de knop **[!UICONTROL Restart]** om te anticiperen op het opnieuw opstarten. De server houdt rekening met het verzoek, aangezien zijn status toont:

     ![](assets/s_user_segmentation_restart_status.png)

     Het proces gaat dan binnen **[!UICONTROL Started]** status.

* Stoppen of pauzeren

   * Met de werkbalkpictogrammen kunt u een actieve doelworkflow stoppen of pauzeren.

     Wanneer u op **[!UICONTROL Pause]**, lopende bewerkingen **[!UICONTROL are not]** gepauzeerd, maar er wordt geen andere activiteit gestart tot de volgende herstart.

     ![](assets/s_user_segmentation_pause.png)

     De server houdt rekening met het bevel, aangezien zijn status toont:

     ![](assets/s_user_segmentation_pause_status.png)

     U kunt een doelworkflow ook automatisch pauzeren wanneer de uitvoering een bepaalde activiteit bereikt. Klik hiertoe met de rechtermuisknop op de activiteit waarvan de doelworkflow moet worden gepauzeerd en selecteer **[!UICONTROL Enable but do not execute]**.

     ![](assets/s_user_segmentation_donotexecute.png)

     Deze configuratie wordt getoond door een speciaal pictogram.

     ![](assets/s_user_segmentation_pause_activity.png)

     >[!NOTE]
     >
     >Deze optie is handig tijdens het ontwerpen en testen van campagnes die u op geavanceerde wijze wilt richten.

     Klikken **[!UICONTROL Start]** om de uitvoering te hervatten.

   * Klik op de knop **[!UICONTROL Stop]** pictogram om de uitvoering in uitvoering te stoppen.

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

  Selecteer in de Verkenner de optie **[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]** om toegang te krijgen tot en op elke campagneworkflows te handelen.

  U kunt de workflow onvoorwaardelijk stoppen door op de knop **[!UICONTROL Actions]** pictogram en selecteren **[!UICONTROL Unconditional]** stoppen. Deze actie beëindigt uw campagnewerkschema.

  ![](assets/s_user_segmentation_stop_unconditional.png)

## Een controlegroep toevoegen {#defining-a-control-group}

Een controlegroep is een populatie die de levering niet zal ontvangen; het wordt gebruikt om het gedrag na de levering en het effect van de campagne te volgen door een vergelijking te maken met het gedrag van de doelpopulatie, die de levering heeft ontvangen.

De controlegroep kan uit het belangrijkste doel worden gehaald en/of uit een specifieke groep of een vraag komen.

### De controlegroep voor een campagne activeren {#activating-the-control-group-for-a-campaign}

U kunt een controlegroep op campagneniveau bepalen, waarbij de controlegroep op elke levering van de betrokken campagne zal worden toegepast.

1. Bewerk de desbetreffende campagne en klik op de knop **[!UICONTROL Edit]** tab.
1. Klik op **[!UICONTROL Advanced campaign settings]**.

   ![](assets/s_ncs_user_edit_op_target.png)

1. Selecteer de **[!UICONTROL Enable and edit control group configuration]** -optie.
1. Klikken **[!UICONTROL Edit...]** om de controlegroep te vormen.

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

De configuratieprocedure wordt weergegeven in [De besturingsgroep extraheren van het hoofddoel](#extracting-the-control-group-from-the-main-target) en [Een besturingsgroep toevoegen](#adding-a-population).

### De controlegroep voor een levering activeren {#activating-the-control-group-for-a-delivery}

U kunt een controlegroep op leveringsniveau bepalen, in welk geval de controlegroep op elke levering van de betrokken campagne zal worden toegepast.

Door gebrek, is de configuratie van de controlegroep die op het campagneniveau wordt bepaald op elke levering van die campagne van toepassing. U kunt, echter, de controlegroep voor een individuele levering aanpassen.

>[!NOTE]
>
>Als u een controlegroep voor een campagne hebt bepaald, en u het voor een levering ook vormt verbonden aan deze campagne, slechts zal de controlegroep die voor de levering wordt bepaald worden toegepast.

1. Bewerk de desbetreffende levering en klik op de knop **[!UICONTROL To]** in de **[!UICONTROL Email parameters]** sectie.

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. Klik op de knop **[!UICONTROL Control group]** en selecteert u **[!UICONTROL Enable and edit control group configuration]**.
1. Klikken **[!UICONTROL Edit...]** om de controlegroep te vormen.

De configuratieprocedure wordt weergegeven in [De besturingsgroep extraheren van het hoofddoel](#extracting-the-control-group-from-the-main-target) en [Een besturingsgroep toevoegen](#adding-a-population).

### Extraheer de controlegroep uit het hoofddoel {#extracting-the-control-group-from-the-main-target}

U kunt ontvangers extraheren uit het hoofddoel van de levering. In dit geval, zullen de ontvangers van het doel van leveringsacties worden genomen die door deze configuratie worden beïnvloed. Deze extractie kan willekeurig zijn of het resultaat zijn van het sorteren van de ontvangers.

![](assets/s_ncs_user_extract_from_target_population.png)

Als u een controlegroep wilt extraheren, schakelt u de controlegroep voor de campagne of levering in en selecteert u een van de volgende opties: **[!UICONTROL Activate random sampling]** of **[!UICONTROL Keep only the first records after sorting]**.

* **[!UICONTROL Activate random sampling]** : deze optie past willekeurige bemonstering toe op de ontvangers in de doelpopulatie. Als u vervolgens de drempel instelt op 100, bestaat de controlegroep uit 100 ontvangers die willekeurig uit de doelpopulatie zijn geselecteerd. De willekeurige bemonstering is afhankelijk van de database-engine.
* **[!UICONTROL Keep only the first records after sorting]** : met deze optie kunt u een beperking definiëren op basis van een of meer sorteervolgorden. Als u **[!UICONTROL Age]** de controlegroep zal bestaan uit de 100 jongste ontvangers . Het zou bijvoorbeeld interessant kunnen zijn om een controlegroep te definiëren die ontvangers bevat die weinig aankopen doen, of ontvangers die vaak aankopen doen, en om hun gedrag te vergelijken met dat van de gecontacteerde ontvangers.

Klikken **[!UICONTROL Next]** om de sorteervolgorde te definiëren (indien nodig) en de beperkingsmodus voor de ontvanger te selecteren.

![](assets/s_ncs_user_edit_op_target_param.png)

Deze configuratie is gelijk aan een deelactiviteit in de workflow, waarmee u het doel kunt onderverdelen in subsets. De controlegroep is één van deze subsets. Zie de [deze sectie](../../workflow/using/architecture.md) voor meer informatie .

### Een nieuwe populatie gebruiken als een controlegroep {#adding-a-population}

U kunt een nieuwe populatie definiëren die als een controlegroep moet worden gebruikt. Deze populatie kan uit een groep ontvangers komen of u kunt het tot stand brengen via een specifieke vraag.

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>Adobe Campaign-query-editor wordt weergegeven in [deze sectie](../../workflow/using/query.md).


#### Video over zelfstudie {#create-email-video}

In deze video wordt uitgelegd hoe u een campagne en een e-mail kunt maken in Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

Er zijn aanvullende instructievideo&#39;s beschikbaar voor campagnes [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
