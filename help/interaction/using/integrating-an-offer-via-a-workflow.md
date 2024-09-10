---
product: campaign
title: Een aanbieding integreren via een workflow
description: Een aanbieding integreren via een workflow
feature: Interaction, Offers, Workflows
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
exl-id: 33d318f3-1eb4-4c74-8c20-8b9f0442c7c3
source-git-commit: de9ff0b50d819038c97e8515ddb7d6cfeb4547a1
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 1%

---

# Een aanbieding integreren via een workflow{#integrating-an-offer-via-a-workflow}



Buiten de leveringsactiviteit zelf, staan verscheidene werkschemaactiviteiten u toe om de manier te bepalen de aanbiedingen worden voorgesteld:

* Overzicht van levering
* Verrijking
* Aanbiedingsengine
* Aanbiedingen per cel

## Overzicht van levering {#delivery-outline}

Met de overzichtsactiviteit van de levering, die beschikbaar is in de workflows van de campagne, kunt u aanbiedingen presenteren waarnaar wordt verwezen in een leveringsoverzicht van de lopende campagne.

1. Voeg in een workflow een overzichtsactiviteit toe voordat u een leveringsactiviteit toevoegt.
1. Geef in de overzichtsactiviteit van de levering de omtrek op die u wilt gebruiken.

   Voor meer informatie bij het specificeren van leveringsoverzichten, verwijs naar de [ Campagne - MRM ](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline) gids.

1. Vul de beschikbare velden in op basis van uw levering.
1. Er zijn twee mogelijke gevallen:

   * Schakel het selectievakje **[!UICONTROL Restrict the number of propositions selected]** in als u de aanbiedingsengine wilt aanroepen. Geef de aanbiedingsruimte en het aantal voorstellen op dat in de levering wordt weergegeven.

     De aanbiedingsmotor zal rekening houden met het gewicht van de aanbieding en de subsidiabiliteitsregels.

   * Als u niet de doos controleert, zullen alle aanbiedingen in het leveringsoverzicht worden voorgesteld zonder een vraag aan de aanbiedingsmotor te maken.

   >[!NOTE]
   >
   >In de voorvertoning wordt rekening gehouden met het aantal aanbiedingen dat in de levering is opgegeven. Bij het uitvoeren van een workflow wordt rekening gehouden met het nummer dat is opgegeven in het leveringsoverzicht.

   ![](assets/int_compo_offre_wf1.png)

## Verrijking {#enrichment}

Met de verrijkingsactiviteit kunt u aanbiedingen of koppelingen naar aanbiedingen voor ontvangers van de levering toevoegen.

>[!NOTE]
>
>Voor meer informatie over de verrijkingsactiviteit, verwijs naar de specifieke documentatie in de [ gids van de Werkschema&#39;s ](../../workflow/using/enrichment.md).

Bijvoorbeeld, kunt u de gegevens voor een ontvankelijke vraag vóór een levering verrijken.

![](assets/int_enrichment_offer1.png)

Er zijn twee methoden om voorstellen voor aanbiedingen op te geven.

* Een aanbieding of een vraag van de aanbiedingsmotor specificeren.
* Verwijzen naar een koppeling naar een aanbieding.

### Het specificeren van een aanbieding of een vraag aan de aanbiedingsmotor {#specifying-an-offer-or-a-call-to-the-offer-engine}

Na het vormen van uw vraag (verwijs naar de [ gids van Werkschema&#39;s ](../../workflow/using/query.md)):

1. Voeg een verrijkingsactiviteit toe en open deze.
1. Selecteer op het tabblad **[!UICONTROL Enrichment]** de optie **[!UICONTROL Add data]** .
1. Selecteer **[!UICONTROL An offer proposition]** in de typen gegevens die u wilt toevoegen.

   ![](assets/int_enrichment_offer2.png)

1. Geef een id en een label op voor het voorstel dat wordt toegevoegd.
1. Geef de selectie van de aanbieding op. Hiervoor zijn twee opties mogelijk:

   * **[!UICONTROL Search for the best offer in a category]** : controleer deze optie en geef de parameters op voor de aanroep van de aanbiedingsengine (ruimte, categorie of thema(&#39;s), contactdatum, aantal aanbiedingen dat u wilt behouden). De motor berekent automatisch de aanbieding(en) die volgens deze parameters moet worden toegevoegd. U wordt aangeraden het veld **[!UICONTROL Category]** of **[!UICONTROL Theme]** in te vullen en niet beide tegelijk.

     ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** : controleer deze optie en specificeer een aanbiedingsruimte, een specifieke aanbieding, en een contactdatum om de aanbieding direct te vormen die u, zonder de aanbiedingsmotor te roepen wilt toevoegen.

     ![](assets/int_enrichment_offer4.png)

1. Dan vorm een leveringsactiviteit die aan uw gekozen kanaal beantwoordt. Voor meer op dit, verwijs naar [ het Invoegen van een aanbiedingsvoorstel in een levering ](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) sectie.

   >[!NOTE]
   >
   >Het aantal voorstellen dat beschikbaar is voor de voorvertoning is afhankelijk van de configuratie die wordt uitgevoerd in de verrijkingsactiviteit in plaats van een mogelijke configuratie die rechtstreeks in de levering wordt uitgevoerd.

### Verwijzen naar een koppeling naar een aanbieding {#referencing-a-link-to-an-offer}

U kunt ook verwijzen naar een koppeling naar een aanbieding in een verrijkingsactiviteit.

Hiervoor gebruikt u het volgende proces:

1. Selecteer **[!UICONTROL Add data]** op het tabblad **[!UICONTROL Enrichment]** van de activiteit.
1. Selecteer **[!UICONTROL A link]** in het venster waarin u het type gegevens kiest dat u wilt toevoegen.
1. Selecteer het type koppeling dat u wilt maken en het doel ervan. In dit geval is het doel het aanbiedingsschema.

   ![](assets/int_enrichment_link1.png)

1. Specificeer zich tussen de binnenkomende lijstgegevens in de verrijkingsactiviteit (hier de ontvankelijke lijst) en de aanbiedingstabel aan. U kunt bijvoorbeeld een aanbiedingscode koppelen aan een ontvanger.

   ![](assets/int_enrichment_link2.png)

1. Dan vorm een leveringsactiviteit die aan uw gekozen kanaal beantwoordt. Voor meer op dit, verwijs naar [ het Invoegen van een aanbiedingsvoorstel in een levering ](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) sectie.

   >[!NOTE]
   >
   >Het aantal voorvertoningen dat beschikbaar is voor de voorvertoning, is afhankelijk van de configuratie die in de levering wordt uitgevoerd.

### Opslaan van rankings- en gewichten voor aanbiedingen {#storing-offer-rankings-and-weights}

Door gebrek, wanneer een **verrijking** activiteit wordt gebruikt om aanbiedingen te leveren, worden hun classificaties en hun gewichten niet opgeslagen in de propositielijst.

>[!NOTE]
>
>Onthoud: deze informatie wordt standaard opgeslagen in de activiteit **[!UICONTROL Offer engine]** .

U kunt deze gegevens echter als volgt opslaan:

1. Creeer een vraag aan de aanbiedingsmotor in een verrijkingsactiviteit die na een vraag en vóór een leveringsactiviteit wordt geplaatst. Verwijs naar [ specificerend een aanbieding of een vraag aan de sectie van de aanbiedingsmotor ](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine).
1. Selecteer **[!UICONTROL Edit additional data...]** in het hoofdvenster van de activiteit.

   ![](assets/ita_enrichment_rankweight_1.png)

1. Voeg de kolommen **[!UICONTROL @rank]** toe voor de positie en **[!UICONTROL @weight]** voor het gewicht van de aanbieding.

   ![](assets/ita_enrichment_rankweight_2.png)

1. Bevestig uw toevoeging en sla uw workflow op.

De levering slaat automatisch de rangschikking en het gewicht van de aanbiedingen op. Deze informatie is zichtbaar op het tabblad **[!UICONTROL Offers]** van de levering.

## Aanbiedingsengine {#offer-engine}

Met de activiteit **[!UICONTROL Offer engine]** kunt u ook een aanroep naar de aanbiedingsengine opgeven voordat de levering plaatsvindt.

Deze activiteit werkt volgens hetzelfde principe als de verrijkingsactiviteit met een motoraanroep, door de binnenkomende bevolkingsgegevens te verrijken met een aanbod dat door de motor wordt berekend, vóór de levering.

![](assets/int_offerengine_activity2.png)

Na het vormen van uw vraag (verwijs naar de [ gids van Werkschema&#39;s ](../../workflow/using/query.md)):

1. Voeg een **[!UICONTROL Offer engine]** -activiteit toe en open deze.
1. Vul de verschillende beschikbare velden in om de oproep tot het aanbieden van motorparameters op te geven (beschikbare ruimte, categorie of thema(&#39;s), contactdatum, aantal aanbiedingen dat moet worden bewaard). De motor berekent automatisch de aanbieding(en) die volgens deze parameters moet worden toegevoegd.

   >[!NOTE]
   >
   >Waarschuwing: als u deze activiteit gebruikt, worden alleen de aanbiedingsvoorstellen opgeslagen die in de levering worden gebruikt.

   ![](assets/int_offerengine_activity1.png)

1. Dan vorm een leveringsactiviteit die aan uw gekozen kanaal beantwoordt. Voor meer op dit, verwijs naar [ het Invoegen van een aanbiedingsvoorstel in een levering ](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) sectie.

## Aanbiedingen per cel {#offers-by-cell}

Met de activiteit **[!UICONTROL Offers by cell]** kunt u de binnenkomende populatie (bijvoorbeeld van een query) in verschillende segmenten verdelen en een aanbieding opgeven om voor elk van deze segmenten voor te stellen.

Hiervoor gebruikt u het volgende proces:

1. Voeg de **[!UICONTROL Offers by cell]** activiteit toe zodra u de doelpopulatie hebt gespecificeerd, dan open het.
1. Selecteer op het tabblad **[!UICONTROL General]** de aanbiedingsruimte waarop u de aanbiedingen wilt weergeven.
1. Geef op het tabblad **[!UICONTROL Cells]** de verschillende subsets op met de knop **[!UICONTROL Add]** :

   * Geef de subsetpopulatie op met behulp van de beschikbare regels voor filteren en beperken.
   * Selecteer vervolgens het voorstel dat u aan de subset wilt presenteren. De beschikbare aanbiedingen zijn die welke in aanmerking komen op het aanbiedingsmilieu dat in de vorige stap werd geselecteerd.

     ![](assets/int_offer_per_cell1.png)

1. Dan vorm een leveringsactiviteit die aan uw gekozen kanaal beantwoordt. Voor meer op dit, verwijs naar [ het Invoegen van een aanbiedingsvoorstel in een levering ](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) sectie.
