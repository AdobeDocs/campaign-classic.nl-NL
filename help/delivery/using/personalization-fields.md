---
title: Velden aanpassen
seo-title: Velden aanpassen
description: Velden aanpassen
seo-description: null
page-status-flag: never-activated
uuid: 3a94a50e-259e-40c3-ae67-8a2c42e9fad7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 27c8e443-ee6b-4d58-bc2d-81cf8391c5de
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f5062117b5cefbdd2570018f6803f114c14a3fae

---


# Velden aanpassen{#personalization-fields}

De gebieden van de aanpassing worden gebruikt voor verpersoonlijking op het eerste niveau van de inhoud van geleverde berichten. De velden die u in een hoofdinhoud invoegt, geven de positie aan waar de gegevens uit de geselecteerde gegevensbron moeten worden ingevoegd.

In het verpersoonlijkingsveld met de syntaxis **&lt;%= receiving.LastName %>** geeft u Adobe Campagne bijvoorbeeld de opdracht de naam van de ontvanger in te voegen in de database (tabel met ontvangers).

>[!NOTE]
>
>Inhoud van aanpassingsvelden mag niet langer zijn dan 1024 tekens.

## Gegevensbronnen {#data-sources}

De gebieden van de verpersoonlijking kunnen uit twee types van gegevensbron, volgens de geselecteerde leveringswijze komen:

* De Adobe Campaign-database is de gegevensbron. Dit is het meest gangbare geval, bijvoorbeeld met &#39;personalisatievelden voor ontvangers&#39;. Dit zijn alle velden die zijn gedefinieerd in de tabel met ontvangers, of het nu standaardvelden zijn (doorgaans: achternaam, voornaam, adres, plaats, geboortedatum, enz.) of door de gebruiker gedefinieerde velden.
* Een extern bestand is de gegevensbron. Dit zijn alle velden die zijn gedefinieerd in de kolommen van het bestand dat wordt weergegeven als invoer tijdens een levering met behulp van de gegevens in een extern bestand.

>[!NOTE]
>
>Een Adobe Campagne-aanpassingstag heeft altijd de volgende vorm **&lt;%=table.field%>**.

## Een aanpassingsveld invoegen {#inserting-a-personalization-field}

Als u verpersoonlijkingsvelden wilt invoegen, klikt u op het vervolgkeuzepictogram dat toegankelijk is vanuit een bewerkveld voor koptekst, onderwerp of berichttekst.

![](assets/s_ncs_user_add_custom_field.png)

Nadat een gegevensbron is geselecteerd (ontvangende velden of bestandsveld), neemt deze invoeging de vorm aan van een opdracht die wordt geïnterpreteerd door Adobe Campagne en wordt vervangen door de waarde van het veld voor een bepaalde ontvanger. De fysieke vervanging kan dan op het **[!UICONTROL Preview]** lusje worden bekeken.

## Voorbeeld van personalisatievelden {#personalization-fields-example}

We maken een e-mail waarin we eerst de naam van de ontvanger invoegen en vervolgens de aanmaakdatum van het profiel in de hoofdtekst van het bericht toevoegen. Dit doet u als volgt:

1. Maak een nieuwe levering of open een bestaande e-maillevering.
1. Klik in de wizard voor aflevering **[!UICONTROL Subject]** om het onderwerp van het bericht te bewerken en voer een onderwerp in.
1. Typ &quot; **[!UICONTROL Special offer for]** &quot; en gebruik de knop op de werkbalk om een verpersoonlijkingsveld in te voegen. Selecteer **[!UICONTROL Recipients>Title]**.

   ![](assets/s_ncs_user_insert_custom_field.png)

1. Herhaal de bewerking om de naam van de ontvanger in te voegen. Voeg spaties in tussen alle verpersoonlijkingsvelden.
1. Klik **[!UICONTROL OK]** om te valideren.
1. Voeg de personalisatie in de berichttekst in. Klik hiertoe in de inhoud van het bericht en klik op de knop voor het invoegen van het veld.
1. Selecteer **[!UICONTROL Recipient>Other...]**.

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. Selecteer het veld met de informatie die u wilt weergeven en klik op **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. Klik op het **[!UICONTROL Preview]** tabblad om het resultaat van de aanpassing weer te geven. U moet een ontvanger selecteren om het bericht van die ontvanger te tonen.

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >Wanneer een levering deel uitmaakt van een workflow, kunt u de gegevens uit de tabel met tijdelijke werkstromen gebruiken. Deze gegevens worden gegroepeerd in het **[!UICONTROL Target extension]** menu. Zie [deze sectie](../../workflow/using/executing-a-workflow.md#target-data)voor meer informatie.

## Aanpassing optimaliseren {#optimizing-personalization}

U kunt personalisatie optimaliseren met behulp van een speciale optie: **[!UICONTROL Prepare the personalization data with a workflow]**, beschikbaar op het **[!UICONTROL Analysis]** tabblad van de leveringseigenschappen.

Tijdens de leveringsanalyse, leidt deze optie automatisch tot en voert een werkschema uit dat alle gegevens met betrekking tot het doel in een tijdelijke lijst, met inbegrip van gegevens van lijsten verbonden in FDA opslaat.

Door deze optie in te schakelen, kunt u een aanzienlijke prestatieverbetering bereiken voor het uitvoeren van personalisatie.

Bijvoorbeeld, als u prestatieskwesties wanneer het leveren aan een hoog aantal ontvangers terwijl het gebruiken van veel verpersoonlijkingsgebieden en/of verpersoonlijkingsblokken in de inhoud van uw berichten ervaart, kan deze optie de behandeling van verpersoonlijking en daarom het leveren van uw berichten versnellen.

Volg onderstaande stappen om deze optie te gebruiken:

1. Maak een campagne. Zie [deze sectie](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)voor meer informatie.
1. Voeg op het **[!UICONTROL Targeting and workflows]** tabblad van uw campagne een **query** -activiteit toe aan uw workflow. Raadpleeg [deze sectie](../../workflow/using/query.md)voor meer informatie over het gebruik van deze activiteit.
1. Voeg een **[!UICONTROL Email delivery]** activiteit aan het werkschema toe en open het. Raadpleeg [deze sectie](../../workflow/using/delivery.md)voor meer informatie over het gebruik van deze activiteit.
1. Ga naar het **[!UICONTROL Analysis]** tabblad van de optie **[!UICONTROL Delivery properties]** en selecteer de **[!UICONTROL Prepare the personalization data with a workflow]** optie.

   ![](assets/perso_optimization.png)

1. Configureer de levering en start de workflow om de analyse te starten.

Zodra de analyse wordt gedaan, worden de verpersoonlijkingsgegevens opgeslagen in een tijdelijke lijst door een tijdelijke technische werkschema dat op de vlucht tijdens de analyse wordt gecreeerd.

Deze workflow is niet zichtbaar in de Adobe Campagne-interface. Het is alleen bedoeld als een technisch middel om personalisatiegegevens snel op te slaan en af te handelen.

Wanneer de analyse is voltooid, gaat u naar de workflow **[!UICONTROL Properties]** en selecteert u het **[!UICONTROL Variables]** tabblad. Daar kunt u de naam van de tijdelijke lijst zien die u kunt gebruiken om een SQL vraag te maken om identiteitskaarts te tonen die het bevat.

![](assets/perso_optimization_temp_table.png)

## Timing uit verpersoonlijkingsfase {#timing-out-personalization}

Om leveringsbescherming te verbeteren, kunt u een onderbreking voor de verpersoonlijkingsfase plaatsen.

Selecteer op het **[!UICONTROL Delivery]** tabblad van de optie **[!UICONTROL Delivery properties]** een maximumwaarde in seconden voor de **[!UICONTROL Maximum personalization run time]** optie.

Als tijdens de voorvertoning of het verzenden de maximale tijd die u in dit veld instelt, wordt overschreden, wordt het proces afgebroken met een foutbericht en mislukt de levering.

![](assets/perso_time-out.png)

De standaardwaarde is 5 seconden.

Als u deze optie instelt op 0, is er geen tijdslimiet voor de verpersoonlijkingsfase.