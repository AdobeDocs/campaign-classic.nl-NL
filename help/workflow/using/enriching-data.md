---
product: campaign
title: Gegevens vergroten
description: Meer informatie over de activiteit van de verrijkingsworkflow
feature: Workflows, Enrichment Activity
hide: true
hidefromtoc: true
exl-id: ab786cf1-74a4-4185-a63d-84e776a2f776
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# Gegevens vergroten{#enriching-data}



## Informatie over het verrijken van gegevens {#about-enriching-data}

In dit geval kunt u details gebruiken over het mogelijke gebruik van de **[!UICONTROL Enrichment]** -activiteit in een doelworkflow. Voor meer bij het gebruiken van de **[!UICONTROL Enrichment]** activiteit, verwijs naar: [ Verrijking ](enrichment.md).

Een gebruiksgeval op hoe te om een e-maillevering met douanedatums te verrijken is ook beschikbaar in [ deze sectie ](email-enrichment-with-custom-date-fields.md).

De contactpersonen in de marketingdatabase worden via een webtoepassing uitgenodigd deel te nemen aan een wedstrijd. De resultaten van de wedstrijd worden hersteld in de tabel **[!UICONTROL Competition results]** . Deze lijst is verbonden met de contactlijst (**[!UICONTROL Recipients]**). De tabel **[!UICONTROL Competition results]** bevat de volgende velden:

* Mededingingsnaam (@game)
* Testnummer (@proefversie)
* Score (@score)

![](assets/uc1_enrich_1.png)

Een contactpersoon in de tabel **[!UICONTROL Recipients]** kan aan meerdere regels in de tabel **[!UICONTROL Competition results]** worden gekoppeld. Het verband tussen deze twee lijsten is van 1-n type. Hier volgt een voorbeeld van de resultatenlogs voor een ontvanger:

![](assets/uc1_enrich_2.png)

Het doel van dit gebruik is om persoonlijke leveringen te sturen naar mensen die, afhankelijk van hun hoogste scores, aan de meest recente wedstrijd hebben deelgenomen. De ontvanger met de hoogste score krijgt de eerste prijs, de ontvanger met de op één na hoogste score krijgt een troostprijs en alle anderen krijgen een boodschap die hen de volgende keer meer geluk wil wensen.

Voor het instellen van dit gebruiksgeval hebben we de volgende workflow voor doelversie gemaakt:

![](assets/uc1_enrich_3.png)

Voer de volgende stappen uit om de workflow te maken:

1. Twee **[!UICONTROL Query]** -activiteiten en één **[!UICONTROL Intersection]** -activiteit worden toegevoegd aan de doelgroep van nieuwe abonnees die het laatst aan de wedstrijd deelnamen.
1. Met de **[!UICONTROL Enrichment]** -activiteit kunnen we gegevens toevoegen die in de **[!UICONTROL Competition results]** -tabel zijn opgeslagen. Het veld **[!UICONTROL Score]** waarin de personalisatie van de levering plaatsvindt, wordt toegevoegd aan de tabel met werkzaamheden van de workflow.
1. Met de **[!UICONTROL Split]** -tekstactiviteit kunnen we subsets voor ontvangers maken op basis van scores.
1. Voor elke subset wordt een **[!UICONTROL Delivery]** type-activiteit toegevoegd.

## Stap 1: Doel {#step-1--targeting}

De eerste vraag laat ons toe om ontvangers te richten die aan het gegevensbestand binnen de laatste zes maanden werden toegevoegd.

![](assets/uc1_enrich_4.png)

De tweede vraag laat ons toe om de ontvangers te richten die aan de laatste concurrentie hebben deelgenomen.

![](assets/uc1_enrich_5.png)

Een **[!UICONTROL Intersection]** type activiteit wordt dan toegevoegd om de ontvangers te richten die aan het gegevensbestand binnen de laatste zes maanden worden toegevoegd en die de laatste concurrentie zijn ingegaan.

## Stap 2: Verrijking {#step-2--enrichment}

In dit voorbeeld willen we leveringen personaliseren volgens het veld **[!UICONTROL Score]** dat is opgeslagen in de tabel **[!UICONTROL Competition results]** . Deze lijst heeft een 1-n typeverhouding met de lijst van ontvangers. Met de activiteit **[!UICONTROL Enrichment]** kunnen we gegevens uit een tabel toevoegen die zijn gekoppeld aan de filterdimensie aan de werktabel van de workflow.

1. Selecteer **[!UICONTROL Add data]** in het bewerkingsscherm van de verrijkingsactiviteit en klik vervolgens op **[!UICONTROL Data linked to the filtering dimension]** **[!UICONTROL Next]** .

   ![](assets/uc1_enrich_6.png)

1. Selecteer vervolgens de optie **[!UICONTROL Data linked to the filtering dimension]** , selecteer de **[!UICONTROL Competition results]** tabel en klik op **[!UICONTROL Next]** .

   ![](assets/uc1_enrich_7.png)

1. Voer een id en een label in en selecteer de optie **[!UICONTROL Limit the line count]** in het veld **[!UICONTROL Data collected]** . Selecteer in het veld **[!UICONTROL Lines to retrieve]** &#39;1&#39; als een waarde. Voor elke ontvanger voegt de verrijkingsactiviteit één regel van de tabel **[!UICONTROL Competition results]** toe aan de werktabel van de workflow. Klik op **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. In dit voorbeeld willen we de hoogste score van de ontvanger terugkrijgen, maar alleen voor de laatste competitie. Hiervoor voegt u een filter toe aan het veld **[!UICONTROL Competition name]** om alle regels uit te sluiten die betrekking hebben op vorige wedstrijden. Klik op **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. Ga naar het scherm **[!UICONTROL Sort]** en klik op de knop **[!UICONTROL Add]** , selecteer het veld **[!UICONTROL Score]** en schakel het selectievakje in de kolom **[!UICONTROL descending]** in om items van de velden **[!UICONTROL Score]** in aflopende volgorde te sorteren. Voor elke ontvanger voegt de verrijkingsactiviteit een regel toe die overeenkomt met de hoogste score voor de laatste game. Klik op **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. Dubbelklik in het venster **[!UICONTROL Data to add]** op het veld **[!UICONTROL Score]** . Voor elke ontvanger voegt de verrijkingsactiviteit alleen het veld **[!UICONTROL Score]** toe. Klik op **[!UICONTROL Finish]**.

   ![](assets/uc1_enrich_11.png)

Klik met de rechtermuisknop op de binnenkomende overgang van de verrijkingsactiviteit en selecteer **[!UICONTROL Display the target]** . De werktabel bevat de volgende gegevens:

![](assets/uc1_enrich_13.png)

Het gekoppelde schema is:

![](assets/uc1_enrich_15.png)

Verleng deze bewerking bij de uitgaande overgang van de verrijkingsactiviteit. We kunnen zien dat de gegevens met betrekking tot de scores van de ontvangers zijn toegevoegd. De hoogste score van elke ontvanger is teruggekregen.

![](assets/uc1_enrich_12.png)

Het overeenkomende schema is ook verrijkt.

![](assets/uc1_enrich_14.png)

## Stap 3: Splitsen en leveren {#step-3--split-and-delivery}

Als u de ontvangers wilt sorteren op basis van hun scores, wordt een **[!UICONTROL Split]** -activiteit toegevoegd na de verrijking.

![](assets/uc1_enrich_18.png)

1. Een eerste (**Winner**) ondergroep is bepaald om de ontvanger met de hoogste score te omvatten. Hiervoor definieert u een beperking van het aantal records, past u een aflopende sortering toe op de score en beperkt u het aantal records tot 1.

   ![](assets/uc1_enrich_16.png)

1. De tweede (**Tweede plaats**) ondergroep omvat de ontvanger met de tweede hoogste score. De configuratie is het zelfde als voor de eerste ondergroep.

   ![](assets/uc1_enrich_17.png)

1. De derde (**verliezers**) ondergroep bevat alle andere ontvangers. Ga naar het tabblad **[!UICONTROL General]** en schakel het selectievakje **[!UICONTROL Generate complement]** in om alle ontvangers te selecteren die de twee hoogste scores niet hebben gehaald.

   ![](assets/uc1_enrich_19.png)

1. Voeg een **[!UICONTROL Delivery]** type activiteit voor elke ondergroep toe, gebruikend een verschillend leveringsmalplaatje voor elk.

   ![](assets/uc1_enrich_20.png)
