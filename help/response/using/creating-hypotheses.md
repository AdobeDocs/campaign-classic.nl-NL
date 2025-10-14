---
product: campaign
title: hypothesen maken
description: Leer hoe u hypothesen maakt in Campagne Response Manager
feature: Campaigns
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: e0b3bc9f-5e81-463f-a59e-cd972a47109b
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1025'
ht-degree: 2%

---

# Hypothesen maken{#creating-hypotheses}



Er zijn verschillende mogelijkheden om hypothesen te creëren/te koppelen aan een campagneaanbod of levering:

* Via de map **[!UICONTROL Measurement hypotheses]** maakt u een nieuwe hypothese op basis van een bestaande sjabloon en koppelt u deze aan een bestaande levering.
* Via het tabblad **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** in een campagne.
* Via de optie **[!UICONTROL Measurement]** van een levering die is gemaakt op basis van een campagne.

Hypothesen kunnen pas worden berekend nadat de marketingcampagne is gestart en de ontvangers de levering hebben ontvangen. Indien de hypothese gebaseerd is op een aanbod-voorstel, moet deze ten minste worden gepresenteerd en nog steeds actief zijn. Aanbiedings- en leveringshypothesen worden gemaakt via de map **[!UICONTROL Measurement hypotheses]** en zijn gebaseerd op een hypothesesjabloon. Het is echter mogelijk om voor het begin van de campagne rechtstreeks naar een hypothese te verwijzen in de uitvoering of de campagne. In dit geval worden de hypothesen automatisch berekend wanneer de marketingcampagne wordt gestart, op basis van de instellingen voor de uitvoering. [Meer informatie](hypothesis-templates.md#hypothesis-template-execution-settings)

## Een hypothese maken tijdens een levering {#creating-a-hypothesis-on-the-fly-on-a-delivery}

Als u een hypothese over een bestaande levering wilt maken, past u het volgende proces toe:

>[!NOTE]
>
>Deze bewerking is alleen mogelijk voor in behandeling zijnde leveringen.

1. Ga in de Adobe Campaign-structuur naar **[!UICONTROL Campaign management > Measurement hypotheses]** .
1. Klik op de knop **[!UICONTROL New]** of klik met de rechtermuisknop op de lijst met hypothesen en selecteer **[!UICONTROL New]** in de vervolgkeuzelijst.

   ![](assets/response_hypothesis_instance_creation_002.png)

1. Selecteer een eerder gemaakte sjabloon in het hypothesevenster. [Meer informatie](hypothesis-templates.md)

   ![](assets/response_hypothesis_instance_creation_003.png)

   De hypothesecontext zoals deze in het geselecteerde model is gedefinieerd, wordt weergegeven in het venster.

   >[!NOTE]
   >
   >De instellingen die in de sjabloon zijn gedefinieerd en in deze stap niet zichtbaar zijn, blijven ook in het geheugen staan en worden opnieuw toegewezen aan de hypothese die wordt uitgevoerd.

   ![](assets/response_hypothesis_instance_creation_004.png)

1. Selecteer de levering waarvoor u een hypothese wilt maken.

   ![](assets/response_hypothesis_instance_creation_005.png)

1. U kunt uw hypothese aanpassen door de tabbladen **[!UICONTROL General]** , **[!UICONTROL Transactions]** en **[!UICONTROL Scope]** te bewerken. [Meer informatie](hypothesis-templates.md#creating-a-hypothesis-model)
1. Start de hypothese door op **[!UICONTROL Start]** te klikken.

   Er wordt automatisch een workflow gemaakt om de meting uit te voeren. De naam wordt automatisch bepaald afhankelijk van de hypotheseconfiguratie.

   >[!CAUTION]
   >
   >U kunt dit doen door het selectievakje **[!UICONTROL Keep execution workflow]** in te schakelen.\
   >Deze optie moet alleen worden geactiveerd voor foutopsporingsdoeleinden, in het geval van een fout tijdens het uitvoeren van de hypothese. De automatisch gegenereerde workflows worden opgeslagen in de map **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Objects created automatically]** > **[!UICONTROL Campaign workflows]** in de Adobe Campaign-verkenner.
   > 
   >Bovendien mogen automatisch gegenereerde workflows niet worden gewijzigd. Eventuele wijzigingen zouden elders niet in aanmerking worden genomen voor latere berekeningen.
   >
   >Als u deze optie hebt ingeschakeld, verwijdert u de workflow nadat deze is uitgevoerd.

   ![](assets/response_hypothesis_instance_creation_006.png)

   Zodra de berekening is voltooid, worden de meetindicatoren automatisch bijgewerkt.

   ![](assets/response_hypothesis_instance_creation_007.png)

1. Wijzig zo nodig de instellingen en start de hypothese opnieuw.

## Verwijzing naar een hypothese in een campagnelevering {#referencing-a-hypothesis-in-a-campaign-delivery}

U kunt in een marketingcampagne naar een hypothese verwijzen voordat deze wordt gestart. In dit geval wordt de hypothese automatisch gestart zodra de levering is verzonden, op basis van de uitvoeringsinstellingen die in de hypothesesjabloon zijn gedefinieerd. Als u een hypothese wilt maken in een levering, past u het volgende proces toe:

1. Afhankelijk van uw behoeften, kunt u één of meerdere **[!UICONTROL Delivery]** typemalplaatjes tot stand brengen, zoals die in [&#x200B; worden beschreven deze sectie &#x200B;](hypothesis-templates.md#creating-a-hypothesis-model)
1. Maak een marketingcampagne en maak doelgerichte workflows.
1. Klik in het leveringsvenster op het pictogram **[!UICONTROL Delivery measurement]** .
1. Selecteer het hypothesemalplaatje (de vraag die in het model wordt gevormd wordt getoond in het hypothesevenster).

   De hypothese wordt automatisch berekend zodra de campagne is voltooid, op basis van de data die in het model zijn geconfigureerd. [Meer informatie](hypothesis-templates.md#hypothesis-template-execution-settings)

   ![](assets/response_hypothesis_instance_creation_008.png)

## Een standaardhypothese toevoegen aan leveringen voor een campagne {#adding-a-default-hypothesis-to-deliveries-for-a-campaign}

U kunt rechtstreeks verwijzen naar een hypothese op campagnereniveau. In dit geval zal de hypothese automatisch worden gekoppeld aan alle leveringen die in de campagne worden gemaakt. Dit doet u als volgt:

1. Ga naar het tabblad **[!UICONTROL Edit]** van de campagne.
1. Klik in de sectie Metingen op de tab **[!UICONTROL Default hypotheses]** .

   ![](assets/response_hypothesis_instance_creation_010.png)

1. Klik op **[!UICONTROL Add]** en selecteer een hypothesesjabloon.

   ![](assets/response_hypothesis_instance_creation_011.png)

   In elke nieuwe levering voor de campagne wordt nu standaard verwezen naar een hypothese op basis van deze sjabloon.

   ![](assets/response_hypothesis_instance_creation_012.png)

De resultaten van de hypothese kunnen worden weergegeven op de tabbladen **[!UICONTROL General]** en **[!UICONTROL Reactions]** . [Meer informatie](hypothesis-tracking.md)

Voor meer informatie, kunt u ook naar [&#x200B; verwijzen deze steekproef &#x200B;](#example--creating-a-hypothesis-linked-to-a-delivery).

## Een hypothese op een aanbod maken {#creating-a-hypothesis-on-an-offer}

Het creëren van een hypothese over een aanbiedingsvoorstel is vergelijkbaar met het creëren van een hypothese over de levering tijdens de vlucht. De hypothese kan worden uitgevoerd zolang het aanbod actief is. De berekeningsperiode is gebaseerd op de datum van het voorstel. Wanneer de hypothese u een ontvanger aan een aankoop laat verbinden, kan de status van het aanbiedingsvoorstel waarschijnlijk worden goedgekeurd automatisch worden veranderd. [Meer informatie](hypothesis-templates.md#transactions)

1. Creeer één of meerdere **[!UICONTROL Offer]** typemodellen zoals die in [&#x200B; worden beschreven deze sectie &#x200B;](hypothesis-templates.md#creating-a-hypothesis-model).
1. Ga naar het knooppunt **[!UICONTROL Campaign management > Measurement hypotheses]** .
1. Maak een hypothese van het type **[!UICONTROL Offers]** door het eerder gemaakte model te selecteren.

   ![](assets/response_hypothesis_instance_offer_001.png)

   De query die in het model is gemaakt, wordt in het venster weergegeven.

   ![](assets/response_hypothesis_instance_offer_003.png)

1. Kies het aanbod waarvoor u een hypothese wilt maken.

   ![](assets/response_hypothesis_instance_offer_004.png)

1. Verfijn indien nodig de query.
1. Klik op **[!UICONTROL Start]** om de hypothese uit te voeren.
1. De resultaten van hypotheses kunnen worden weergegeven op de tabbladen **[!UICONTROL General]** en **[!UICONTROL Reactions]** . [Meer informatie](hypothesis-tracking.md)

   Op het tabblad **[!UICONTROL Measurement]** wordt verwezen naar de hypothesen die op een aanbieding zijn aangebracht.

   ![](assets/response_hypothesis_instance_offer_007.png)

   Als de **[!UICONTROL Update offer proposition status]** optie in het hypothesemalplaatje werd toegelaten, wordt het statuut van de aanbiedingsvoorstel automatisch veranderd, daardoor verstrekkend terugkoppelt op het effect van de campagne (voor meer op dit, verwijs naar [&#x200B; Transacties &#x200B;](hypothesis-templates.md#transactions)).

## Voorbeeld: een hypothese maken die gekoppeld is aan een levering {#example--creating-a-hypothesis-linked-to-a-delivery}

In dit voorbeeld willen we een hypothese creëren die gekoppeld is aan een levering. Deze hypothese zal gebaseerd zijn op het eerder gemaakte model. [Meer informatie](hypothesis-templates.md#example--creating-a-hypothesis-template-on-a-delivery)

Vervolgens wordt de query die van het model is overgenomen, verfijnd en wordt een hypothese gemaakt voor een specifiek artikel van de aankooptabel.

1. Maak een campagne en een levering. Verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=nl-NL){target=_blank}.

   In ons voorbeeld, zullen wij een directe posttype levering gebruiken.

1. Vorm een zaadadres: het eerder gecreeerde hypothesemalplaatje werd gevormd om een controlegroep in de reactieresultaten rekening te houden.

   ![](assets/response_hypothesis_delivery_example_007.png)

   >[!NOTE]
   >
   >Raadpleeg de [Campaign v8-documentatie](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=nl-NL#add-a-control-group){target="_blank"} voor meer informatie.

1. Open **[!UICONTROL Direct mail delivery]**, klik op het pictogram **[!UICONTROL Delivery measurement]** en klik vervolgens op **[!UICONTROL Add]** .

   ![](assets/response_hypothesis_delivery_example_002.png)

1. Kies de eerder gemaakte hypothesesjabloon in de vervolgkeuzelijst.

   ![](assets/response_hypothesis_delivery_example_004.png)

   De query die in het model wordt gemaakt, wordt weergegeven.

   ![](assets/response_hypothesis_delivery_example_005.png)

1. Klik op **[!UICONTROL Edit query...]** en verfijn de query door het product in te voeren waarop de hypothese betrekking heeft.

   ![](assets/response_hypothesis_delivery_example_006.png)

   U kunt controleren of de hypothese is gekoppeld aan de levering op het tabblad **[!UICONTROL Edit]** > **[!UICONTROL Measurement]** van de campagne.

   ![](assets/response_hypothesis_delivery_example_008.png)

1. Start de doelworkflow en voer de vereiste controles uit totdat de campagne is voltooid. Verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-deliveries.html?lang=nl-NL#start-a-delivery){target=_blank}.

   ![](assets/response_hypothesis_delivery_example_009.png)

1. Ga in de Adobe Campaign-structuur naar het knooppunt **[!UICONTROL Campaign management > Measurement hypotheses]** om de indicatoren te controleren die door de hypothese worden berekend.

   ![](assets/response_hypothesis_delivery_example_010.png)
