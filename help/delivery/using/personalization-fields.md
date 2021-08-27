---
product: campaign
title: Personalisatievelden
description: Personalisatievelden
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 67fd9a67-cb05-46cd-acd5-e42fde6f4d4f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 11%

---

# Personalisatievelden{#personalization-fields}

![](../../assets/common.svg)

Personalisatievelden worden gebruikt voor personalisatie op het eerste niveau van de content van geleverde berichten. De velden die u in hoofdcontent invoegt, geven de positie aan waar de gegevens uit de geselecteerde gegevensbron moeten worden ingevoegd.

Bijvoorbeeld, vertelt het verpersoonlijkingsgebied met **&lt;%= receiving.LastName %>** syntaxis Adobe Campaign om de naam van de ontvanger in het gegevensbestand (ontvankelijke lijst) op te nemen.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#personalization-fields-video)

>[!CAUTION]
>
>Inhoud van aanpassingsvelden mag niet langer zijn dan 1024 tekens.

## Gegevensbronnen {#data-sources}

De gebieden van de verpersoonlijking kunnen uit twee types van gegevensbron, volgens de geselecteerde leveringswijze komen:

* De Adobe Campaign-database is de gegevensbron. Dit is het meest gangbare geval, bijvoorbeeld met &#39;personalisatievelden voor ontvangers&#39;. Dit zijn alle velden die zijn gedefinieerd in de tabel met ontvangers, of het nu standaardvelden zijn (doorgaans: achternaam, voornaam, adres, plaats, geboortedatum, enz.) of door de gebruiker gedefinieerde velden.
* Een extern bestand is de gegevensbron. Dit zijn alle velden die zijn gedefinieerd in de kolommen van het bestand dat wordt weergegeven als invoer tijdens een levering met behulp van de gegevens in een extern bestand.

>[!NOTE]
>
>Een Adobe Campaign-personalisatietag heeft altijd de volgende vorm **&lt;%=table.field%>**.

## Een personalisatieveld invoegen {#inserting-a-personalization-field}

Als u verpersoonlijkingsvelden wilt invoegen, klikt u op het vervolgkeuzepictogram dat toegankelijk is vanuit een bewerkveld voor koptekst, onderwerp of berichttekst.

![](assets/s_ncs_user_add_custom_field.png)

Na de selectie van een gegevensbron (ontvangende velden of bestandsveld) neemt deze invoeging de vorm aan van een opdracht die wordt geïnterpreteerd door Adobe Campaign en wordt vervangen door de waarde van het veld voor een bepaalde ontvanger. De fysieke vervanging kan dan op **[!UICONTROL Preview]** tabel worden bekeken.

## Voorbeeld van personalisatievelden {#personalization-fields-example}

We maken een e-mail waarin we eerst de naam van de ontvanger invoegen en vervolgens de aanmaakdatum van het profiel in de hoofdtekst van het bericht toevoegen. Dit doet u als volgt:

1. Maak een nieuwe levering of open een bestaande e-maillevering.
1. Klik in de wizard voor aflevering op **[!UICONTROL Subject]** om het onderwerp van het bericht te bewerken en een onderwerp in te voeren.
1. Voer &quot; **[!UICONTROL Special offer for]** &quot; in en gebruik de knop op de werkbalk om een aanpassingsveld in te voegen. Selecteer **[!UICONTROL Recipients>Title]**.

   ![](assets/s_ncs_user_insert_custom_field.png)

1. Herhaal de bewerking om de naam van de ontvanger in te voegen. Voeg spaties in tussen alle verpersoonlijkingsvelden.
1. Klik **[!UICONTROL OK]** om te bevestigen.
1. Voeg de personalisatie in de berichttekst in. Klik hiertoe in de inhoud van het bericht en klik op de knop voor het invoegen van het veld.
1. Selecteer **[!UICONTROL Recipient>Other...]**.

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. Selecteer het veld met de informatie die u wilt weergeven en klik op **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. Klik op het tabblad **[!UICONTROL Preview]** om het verpersoonlijkingsresultaat weer te geven. U moet een ontvanger selecteren om het bericht van die ontvanger te tonen.

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >Wanneer een levering deel uitmaakt van een workflow, kunt u de gegevens uit de tabel met tijdelijke werkstromen gebruiken. Deze gegevens worden gegroepeerd in het menu **[!UICONTROL Target extension]**. Raadpleeg [deze sectie](../../workflow/using/data-life-cycle.md#target-data) voor meer informatie.

## Aanpassing optimaliseren {#optimizing-personalization}

U kunt personalisatie optimaliseren met behulp van een speciale optie: **[!UICONTROL Prepare the personalization data with a workflow]**, beschikbaar op het **[!UICONTROL Analysis]** lusje van de leveringseigenschappen. Zie [deze sectie](steps-validating-the-delivery.md#analyzing-the-delivery) voor meer informatie over het analyseren van de aflevering.

Tijdens de leveringsanalyse, leidt deze optie automatisch tot en voert een werkschema uit dat alle gegevens met betrekking tot het doel in een tijdelijke lijst, met inbegrip van gegevens van lijsten verbonden in FDA opslaat.

Als u deze optie inschakelt, kunnen de prestaties van de leveringsanalyse aanzienlijk worden verbeterd wanneer een groot aantal gegevens wordt verwerkt, vooral als de personalisatiegegevens afkomstig zijn van een externe tabel via FDA. Zie [Toegang tot een externe database (FDA)](../../installation/using/about-fda.md) voor meer informatie.

Bijvoorbeeld, als u prestatieskwesties wanneer het leveren aan een hoog aantal ontvangers terwijl het gebruiken van veel verpersoonlijkingsgebieden en/of verpersoonlijkingsblokken in de inhoud van uw berichten ervaart, kan deze optie de behandeling van verpersoonlijking en daarom het leveren van uw berichten versnellen.

Volg onderstaande stappen om deze optie te gebruiken:

1. Een campagne maken. Raadpleeg [deze sectie](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign) voor meer informatie.
1. Voeg op het tabblad **[!UICONTROL Targeting and workflows]** van uw campagne een **Query**-activiteit toe aan uw workflow. Raadpleeg [deze sectie](../../workflow/using/query.md) voor meer informatie over het gebruik van deze activiteit.
1. Voeg een **[!UICONTROL Email delivery]** activiteit aan het werkschema toe en open het. Raadpleeg [deze sectie](../../workflow/using/delivery.md) voor meer informatie over het gebruik van deze activiteit.
1. Ga naar het **[!UICONTROL Analysis]** lusje van **[!UICONTROL Delivery properties]** en selecteer **[!UICONTROL Prepare the personalization data with a workflow]** optie.

   ![](assets/perso_optimization.png)

1. Configureer de levering en start de workflow om de analyse te starten.

Zodra de analyse wordt gedaan, worden de verpersoonlijkingsgegevens opgeslagen in een tijdelijke lijst door een tijdelijke technische werkschema dat op de vlucht tijdens de analyse wordt gecreeerd.

Deze workflow is niet zichtbaar in de Adobe Campaign-interface. Het is alleen bedoeld als een technisch middel om personalisatiegegevens snel op te slaan en af te handelen.

Wanneer de analyse is voltooid, gaat u naar de workflow **[!UICONTROL Properties]** en selecteert u het tabblad **[!UICONTROL Variables]**. Daar kunt u de naam van de tijdelijke lijst zien die u kunt gebruiken om een SQL vraag te maken om identiteitskaarts te tonen die het bevat.

![](assets/perso_optimization_temp_table.png)

## Timing uit verpersoonlijkingsfase {#timing-out-personalization}

Om leveringsbescherming te verbeteren, kunt u een onderbreking voor de verpersoonlijkingsfase plaatsen.

Selecteer op het tabblad **[!UICONTROL Delivery]** van **[!UICONTROL Delivery properties]** een maximumwaarde in seconden voor de optie **[!UICONTROL Maximum personalization run time]**.

Als tijdens de voorvertoning of het verzenden de maximale tijd die u in dit veld instelt, wordt overschreden, wordt het proces afgebroken met een foutbericht en mislukt de levering.

![](assets/perso_time-out.png)

De standaardwaarde is 5 seconden.

Als u deze optie instelt op 0, is er geen tijdslimiet voor de verpersoonlijkingsfase.

## Video over zelfstudie {#personalization-fields-video}

Leer hoe u een personalisatieveld toevoegt aan de onderwerpregel en de content van een e-maillevering.

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)

Er zijn [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl) extra Campaign Classic hoe kan ik-video&#39;s beschikbaar.
