---
product: campaign
title: Een dynamische afbeelding invoegen
description: Een dynamische afbeelding invoegen
feature: Target Integration
badge-v7: label="v7" type="Informative" tooltip="Van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 6177f57b-534c-4d86-8f73-d96980c48a77
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 2%

---

# Dynamische inhoud van doel invoegen {#inserting-a-dynamic-image}



In deze pagina leert u hoe u een dynamisch aanbod van Adobe Target kunt integreren in een e-mailbericht in Adobe Campaign.

Het doel is een levering te maken met een afbeeldingsblok dat dynamisch verandert naar gelang het land van de ontvanger: de gegevens worden samen met elk verzoek van de box verzonden en zijn afhankelijk van het IP-adres van de ontvanger.

In dit bericht kunnen afbeeldingen dynamisch variëren, afhankelijk van de volgende gebruikerservaring:

* Het e-mailbericht wordt geopend in Frankrijk.
* Het e-mailbericht wordt geopend in de Verenigde Staten.
* Als geen van deze voorwaarden van toepassing is, wordt een standaardafbeelding weergegeven.

![](assets/target_4.png)

Voer de volgende stappen uit om dit te doen:

1. [De dynamische aanbieding in een e-mail invoegen](../../integrations/using/inserting-a-dynamic-image.md#inserting-dynamic-offer)
1. [Omleidingsvoorstellen maken](../../integrations/using/inserting-a-dynamic-image.md#create-redirect-offers)
1. [Soorten publiek maken](../../integrations/using/inserting-a-dynamic-image.md#audiences-target)
1. [Een ervaring maken die gericht is op activiteiten](../../integrations/using/inserting-a-dynamic-image.md#creating-targeting-activity)
1. [E-mail voorvertonen en verzenden](../../integrations/using/inserting-a-dynamic-image.md#preview-send-email)

## De dynamische aanbieding in een e-mail invoegen {#inserting-dynamic-offer}

Als u in Adobe Campaign klaar bent met het definiëren van het doel en de inhoud van uw e-mail, kunt u een dynamische afbeelding invoegen vanuit Target.

Hiervoor geeft u de URL van de standaardafbeelding, de locatienaam en de velden op die u naar Doel wilt overbrengen.

In Adobe Campaign kunt u op twee manieren een dynamische afbeelding van Target invoegen in een e-mailbericht:

* Als u de editor voor digitale inhoud gebruikt, kiest u een bestaande afbeelding en selecteert u **[!UICONTROL Insert]** > **[!UICONTROL Dynamic image served by Adobe Target]** op de werkbalk.

  ![](assets/target_5.png)

* Als u de standaardeditor gebruikt, plaatst u de cursor op de plaats waar u de afbeelding wilt invoegen en selecteert u **[!UICONTROL Include]** > **[!UICONTROL Dynamic image served by Adobe Target...]** in het vervolgkeuzemenu voor aanpassen.

  ![](assets/target_12.png)

### De afbeeldingsparameters definiëren {#defining-image-parameters}

* De **[!UICONTROL Default image]** De URL van de gebruiker: De afbeelding die wordt weergegeven wanneer aan geen van de voorwaarden wordt voldaan. U kunt ook een afbeelding selecteren in de middelenbibliotheek.
* De **[!UICONTROL Target location]**: Voer een naam in voor de locatie van uw dynamische aanbieding. U moet deze locatie selecteren in uw doelactiviteit.
* De **[!UICONTROL Landing Page]**: Als u de standaardafbeelding wilt omleiden naar een standaardbestemmingspagina. Deze URL is alleen bedoeld voor gevallen waarin de standaardafbeelding in de uiteindelijke e-mail wordt weergegeven en optioneel is.
* De **[!UICONTROL Additional decision parameters]**: Geef de toewijzing op tussen de velden die zijn gedefinieerd in de Adobe Target-segmenten en de Adobe Campaign-velden. De Adobe Campaign-velden die worden gebruikt, moeten zijn opgegeven in de keuzelijst. In ons voorbeeld hebben we het veld Land toegevoegd.

Als u Enterprise-machtigingen gebruikt in uw instellingen in Adobe Target, voegt u de bijbehorende eigenschap toe in dit veld. Meer informatie over Target Enterprise-machtigingen vindt u in [deze pagina](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html).

![](assets/target_13.png)

## Omleidingsvoorstellen maken {#create-redirect-offers}

In Target kunt u verschillende versies van uw aanbieding maken. Afhankelijk van elke gebruikerservaring kan een omleidingsaanbod worden gemaakt en kunt u opgeven welke afbeelding wordt weergegeven.

In ons geval hebben we twee doorgifteaanbiedingen nodig, de derde (de standaard) moet in Adobe Campaign worden gedefinieerd.

1. Als u een nieuwe omleidingsaanbieding wilt maken in de Target Standard, gaat u naar de **[!UICONTROL Content]** tabblad, klikt u op **[!UICONTROL Code offers]**.

1. Klik op **[!UICONTROL Create]** en vervolgens op **[!UICONTROL Redirect Offer]**.

   ![](assets/target_9.png)

1. Voer een naam in voor het voorstel en de URL van de afbeelding.

   ![](assets/target_6.png)

1. Volg dezelfde procedure voor het resterende doorleidingsaanbod. Raadpleeg [deze pagina](https://experienceleague.adobe.com/docs/target/using/experiences/offers/offer-redirect.html) voor meer informatie.

## Soorten publiek maken {#audiences-target}

In Target moet u de twee soorten publiek maken waarin de personen die uw aanbieding bezoeken, worden ingedeeld voor de verschillende inhoud die moet worden geleverd. Voor elk publiek, voeg een regel toe om te bepalen wie de aanbieding zal kunnen zien.

1. Als u een nieuw publiek wilt maken in Doel, gaat u als volgt te werk **[!UICONTROL Audiences]** tabblad, klikt u op **[!UICONTROL Create Audience]**.

   ![](assets/audiences_1.png)

1. Voeg een naam toe aan uw publiek.

   ![](assets/audiences_2.png)

1. Klikken **[!UICONTROL Add a rule]** en selecteer een categorie. De regel gebruikt specifieke criteria om de bezoekers te richten. U kunt de regels verfijnen door voorwaarden toe te voegen of door nieuwe regels te maken in andere categorieën.

1. Volg dezelfde procedure voor het resterende publiek.

## Een ervaring maken die gericht is op activiteiten {#creating-targeting-activity}

In Doel, moeten wij een Ervaring creëren richtend activiteit, de verschillende ervaringen bepalen, en hen associëren met de overeenkomstige aanbiedingen.

### De doelgroep definiëren {#defining-the-audience}

1. Om een Ervaring te creëren richtend activiteit, van **[!UICONTROL Activities]** tabblad, klikt u op **[!UICONTROL Create Activity]** dan **[!UICONTROL Experience Targeting]**.

   ![](assets/target_10.png)

1. Selecteren **[!UICONTROL Form]** als **[!UICONTROL Experience Composer]**.

1. Kies een publiek door op de knop **[!UICONTROL Change audience]** knop.

   ![](assets/target_10_2.png)

1. Selecteer het publiek dat in de vorige stappen is gemaakt.

   ![](assets/target_10_3.png)

1. Een andere ervaring maken door op **[!UICONTROL Add Experience Targeting]**.

### De locatie en inhoud definiëren {#defining-location-content}

Voeg inhoud toe voor elk publiek:

1. Selecteer de locatienaam die u hebt gekozen bij het invoegen van het dynamische aanbod in Adobe Campaign.

   ![](assets/target_15.png)

1. Klik op de vervolgkeuzelijst en selecteer **[!UICONTROL Change Redirect Offer]**.

   ![](assets/target_content.png)

1. Selecteer het omleidingsvoorstel dat u eerder hebt gemaakt.

   ![](assets/target_content_2.png)

1. Voer dezelfde stappen uit voor de tweede ervaring.

### De activiteit definiëren {#defining-activity}

De **[!UICONTROL Target]** geeft een overzicht van uw activiteiten. Indien nodig kunt u andere ervaringen toevoegen.

![](assets/target_experience.png)

De **[!UICONTROL Goal & Settings]** kunt u uw activiteit aanpassen door een prioriteit, een doelstelling of een duur in te stellen.

De **[!UICONTROL Reporting Settings]** kunt u een actie selecteren en de parameters bewerken die bepalen wanneer uw doel wordt bereikt.

![](assets/target_experience_2.png)

## E-mail voorvertonen en verzenden {#preview-send-email}

In Adobe Campaign kunt u nu een voorbeeld van uw e-mail bekijken en de weergave ervan testen op verschillende ontvangers. U zult merken dat de afbeelding verandert op basis van de verschillende ervaringen die u hebt opgedaan. Raadpleeg de volgende secties voor meer informatie over het maken van e-mail [page](../../delivery/using/defining-the-email-content.md).

U kunt nu uw e-mail verzenden, inclusief een dynamisch voorstel van Target.

![](assets/target_20.png)
