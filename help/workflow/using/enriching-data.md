---
title: Gegevens worden verrijkt
seo-title: Gegevens worden verrijkt
description: Gegevens worden verrijkt
seo-description: null
page-status-flag: never-activated
uuid: 3f65a8a2-b3e1-4c4c-9653-b8a7c4d7557a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: f87da08f-68b9-4e2b-821f-b3ff20e390f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1aca6758bc787f91ae28d7d5add875edf04541e8
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 0%

---


# Gegevens worden verrijkt{#enriching-data}

## Informatie over het verrijken van gegevens {#about-enriching-data}

In dit geval worden mogelijke toepassingen van de **[!UICONTROL Enrichment]** activiteit in een doelworkflow beschreven. Raadpleeg voor meer informatie over het gebruik van de **[!UICONTROL Enrichment]** activiteit: [Verrijking](../../workflow/using/enrichment.md).

Een gebruiksscenario voor het verrijken van een e-maillevering met aangepaste datums is ook beschikbaar in [deze sectie](../../workflow/using/email-enrichment-with-custom-date-fields.md).

De contactpersonen in de marketingdatabase worden via een webtoepassing uitgenodigd deel te nemen aan een wedstrijd. De resultaten van de mededinging worden in de **[!UICONTROL Competition results]** tabel teruggevorderd. Deze tabel is gekoppeld aan de tabel met contactpersonen (**[!UICONTROL Recipients]**). De **[!UICONTROL Competition results]** tabel bevat de volgende velden:

* Mededingingsnaam (@game)
* Testnummer (@proefversie)
* Score (@score)

![](assets/uc1_enrich_1.png)

Een contactpersoon die in de **[!UICONTROL Recipients]** tabel wordt gevonden, kan aan meerdere regels in de **[!UICONTROL Competition results]** tabel worden gekoppeld. Het verband tussen deze twee lijsten is van 1-n type. Hier volgt een voorbeeld van de resultatenlogs voor een ontvanger:

![](assets/uc1_enrich_2.png)

Het doel van dit gebruik is om persoonlijke leveringen te sturen naar mensen die, afhankelijk van hun hoogste scores, aan de meest recente wedstrijd hebben deelgenomen. De ontvanger met de hoogste score krijgt de eerste prijs, de ontvanger met de op één na hoogste score krijgt een troostprijs en alle anderen krijgen een boodschap die hen de volgende keer meer geluk wil wensen.

Voor het instellen van dit gebruiksgeval hebben we de volgende workflow voor doelversie gemaakt:

![](assets/uc1_enrich_3.png)

Voer de volgende stappen uit om de workflow te maken:

1. Twee **[!UICONTROL Query]** activiteiten en één **[!UICONTROL Intersection]** activiteit worden toegevoegd aan de nieuwe abonnees die het laatste examen hebben afgelegd.
1. Met de **[!UICONTROL Enrichment]** activiteit kunnen we gegevens toevoegen die in de **[!UICONTROL Competition results]** tabel zijn opgeslagen. Het **[!UICONTROL Score]** veld waarop de personalisatie van de levering plaatsvindt, wordt toegevoegd aan de werktabel van de workflow.
1. Met de **[!UICONTROL Split]** tekstactiviteit kunnen subsets voor ontvangers worden gemaakt op basis van scores.
1. Voor elke subset wordt een **[!UICONTROL Delivery]** tekstactiviteit toegevoegd.

## Stap 1: Doelstelling {#step-1--targeting}

De eerste vraag laat ons toe om ontvangers te richten die aan het gegevensbestand binnen de laatste zes maanden werden toegevoegd.

![](assets/uc1_enrich_4.png)

De tweede vraag laat ons toe om de ontvangers te richten die aan de laatste concurrentie hebben deelgenomen.

![](assets/uc1_enrich_5.png)

Een **[!UICONTROL Intersection]** typeactiviteit wordt dan toegevoegd om de ontvangers te richten die aan het gegevensbestand binnen de laatste zes maanden worden toegevoegd en die de laatste concurrentie zijn ingegaan.

## Stap 2: Verrijking {#step-2--enrichment}

In dit voorbeeld, willen wij leveringen volgens het **[!UICONTROL Score]** gebied personaliseren dat in de **[!UICONTROL Competition results]** lijst wordt opgeslagen. Deze lijst heeft een 1-n typeverhouding met de lijst van ontvangers. De **[!UICONTROL Enrichment]** activiteit laat ons toe om gegevens van een lijst toe te voegen verbonden aan de het filtreren dimensie aan de het werklijst van het werkschema.

1. Selecteer vervolgens in het bewerkingsscherm van de verrijkingsactiviteit **[!UICONTROL Add data]** en klik **[!UICONTROL Data linked to the filtering dimension]** op **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_6.png)

1. Selecteer vervolgens de **[!UICONTROL Data linked to the filtering dimension]** optie, selecteer de **[!UICONTROL Competition results]** tabel en klik op **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. Voer een id en een label in en selecteer de **[!UICONTROL Limit the line count]** optie in het **[!UICONTROL Data collected]** veld. Selecteer in het **[!UICONTROL Lines to retrieve]** veld &#39;1&#39; als waarde. Voor elke ontvanger, zal de verrijkingsactiviteit één enkele lijn van de **[!UICONTROL Competition results]** lijst aan de het werklijst van het werkschema toevoegen. Klik op **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. In dit voorbeeld willen we de hoogste score van de ontvanger terugkrijgen, maar alleen voor de laatste competitie. Hiervoor voegt u een filter toe aan het **[!UICONTROL Competition name]** veld om alle regels uit te sluiten die betrekking hebben op eerdere vergelijkende onderzoeken. Klik op **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. Ga naar het **[!UICONTROL Sort]** scherm en klik op de **[!UICONTROL Add]** knop, selecteer het **[!UICONTROL Score]** veld en schakel het selectievakje in de **[!UICONTROL descending]** kolom in om items van de **[!UICONTROL Score]** velden in aflopende volgorde te sorteren. Voor elke ontvanger voegt de verrijkingsactiviteit een regel toe die overeenkomt met de hoogste score voor de laatste game. Klik op **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. Dubbelklik in het **[!UICONTROL Data to add]** venster op het **[!UICONTROL Score]** veld. Voor elke ontvanger voegt de verrijkingsactiviteit alleen het **[!UICONTROL Score]** veld toe. Klik op **[!UICONTROL Finish]**.

   ![](assets/uc1_enrich_11.png)

Klik met de rechtermuisknop op de binnenkomende overgang van de verrijkingsactiviteit en selecteer **[!UICONTROL Display the target]**. De werktabel bevat de volgende gegevens:

![](assets/uc1_enrich_13.png)

Het gekoppelde schema is:

![](assets/uc1_enrich_15.png)

Verleng deze bewerking bij de uitgaande overgang van de verrijkingsactiviteit. We kunnen zien dat de gegevens met betrekking tot de scores van de ontvangers zijn toegevoegd. De hoogste score van elke ontvanger is hersteld.

![](assets/uc1_enrich_12.png)

Het overeenkomende schema is ook verrijkt.

![](assets/uc1_enrich_14.png)

## Stap 3: Splitsen en leveren {#step-3--split-and-delivery}

Als u de ontvangers wilt sorteren op basis van hun scores, wordt een **[!UICONTROL Split]** activiteit toegevoegd na de verrijking.

![](assets/uc1_enrich_18.png)

1. Een eerste subset (**Winner**) is gedefinieerd om de ontvanger met de hoogste score te bevatten. Hiervoor definieert u een beperking van het aantal records, past u een aflopende sortering toe op de score en beperkt u het aantal records tot 1.

   ![](assets/uc1_enrich_16.png)

1. De tweede subset (**tweede plaats**) bevat de ontvanger met de op één na hoogste score. De configuratie is het zelfde als voor de eerste ondergroep.

   ![](assets/uc1_enrich_17.png)

1. De derde subset (**losers**) bevat alle andere ontvangers. Ga naar het **[!UICONTROL General]** tabblad en schakel het **[!UICONTROL Generate complement]** selectievakje in om alle ontvangers aan te wijzen die de twee hoogste scores niet hebben gehaald.

   ![](assets/uc1_enrich_19.png)

1. Voeg een **[!UICONTROL Delivery]** typeactiviteit voor elke ondergroep toe, gebruikend een verschillend leveringsmalplaatje voor elk.

   ![](assets/uc1_enrich_20.png)

