---
title: Personalisatievelden
seo-title: Personalisatievelden
description: Personalisatievelden
seo-description: null
page-status-flag: never-activated
uuid: 3a94a50e-259e-40c3-ae67-8a2c42e9fad7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 27c8e443-ee6b-4d58-bc2d-81cf8391c5de
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 8%

---


# Personalisatievelden{#personalization-fields}

Personalisatievelden worden gebruikt voor personalisatie op het eerste niveau van de content van geleverde berichten. De velden die u in hoofdcontent invoegt, geven de positie aan waar de gegevens uit de geselecteerde gegevensbron moeten worden ingevoegd.

In het verpersoonlijkingsveld met de syntaxis **&lt;%= receiving.LastName %>** geeft Adobe Campaign bijvoorbeeld de opdracht de naam van de ontvanger in te voegen in de database (tabel met ontvangers).

![](assets/do-not-localize/how-to-video.png) [Deze functie in video detecteren](#personalization-fields-video)

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

Na de selectie van een gegevensbron (ontvangende velden of bestandsveld) neemt deze invoeging de vorm aan van een opdracht die wordt geïnterpreteerd door Adobe Campaign en wordt vervangen door de waarde van het veld voor een bepaalde ontvanger. De fysieke vervanging kan dan op het **[!UICONTROL Preview]** lusje worden bekeken.

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
   >Wanneer een levering deel uitmaakt van een workflow, kunt u de gegevens uit de tabel met tijdelijke werkstromen gebruiken. Deze gegevens worden gegroepeerd in het **[!UICONTROL Target extension]** menu. Raadpleeg [deze sectie](../../workflow/using/data-life-cycle.md#target-data) voor meer informatie.

## Aanpassing optimaliseren {#optimizing-personalization}

U kunt personalisatie optimaliseren met behulp van een speciale optie: **[!UICONTROL Prepare the personalization data with a workflow]**, beschikbaar op het **[!UICONTROL Analysis]** tabblad van de leveringseigenschappen. Zie [deze sectie](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)voor meer informatie over het analyseren van de aflevering.

Tijdens de leveringsanalyse, leidt deze optie automatisch tot en voert een werkschema uit dat alle gegevens met betrekking tot het doel in een tijdelijke lijst, met inbegrip van gegevens van lijsten verbonden in FDA opslaat.

Als u deze optie inschakelt, kunnen de prestaties van de leveringsanalyse aanzienlijk worden verbeterd wanneer een groot aantal gegevens wordt verwerkt, vooral als de personalisatiegegevens afkomstig zijn van een externe tabel via FDA. Zie [Toegang tot een externe database (FDA)](../../platform/using/additional-options.md#optimizing-email-personalization-with-external-data)voor meer informatie.

Bijvoorbeeld, als u prestatieskwesties wanneer het leveren aan een hoog aantal ontvangers terwijl het gebruiken van veel verpersoonlijkingsgebieden en/of verpersoonlijkingsblokken in de inhoud van uw berichten ervaart, kan deze optie de behandeling van verpersoonlijking en daarom het leveren van uw berichten versnellen.

Volg onderstaande stappen om deze optie te gebruiken:

1. Een campagne maken. Raadpleeg [deze sectie](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign) voor meer informatie.
1. Voeg op het **[!UICONTROL Targeting and workflows]** tabblad van uw campagne een **query** -activiteit toe aan uw workflow. For more on using this activity, refer to [this section](../../workflow/using/query.md).
1. Voeg een **[!UICONTROL Email delivery]** activiteit aan het werkschema toe en open het. For more on using this activity, refer to [this section](../../workflow/using/delivery.md).
1. Ga naar het **[!UICONTROL Analysis]** tabblad van de optie **[!UICONTROL Delivery properties]** en selecteer de **[!UICONTROL Prepare the personalization data with a workflow]** optie.

   ![](assets/perso_optimization.png)

1. Configureer de levering en start de workflow om de analyse te starten.

Zodra de analyse wordt gedaan, worden de verpersoonlijkingsgegevens opgeslagen in een tijdelijke lijst door een tijdelijke technische werkschema dat op de vlucht tijdens de analyse wordt gecreeerd.

Deze workflow is niet zichtbaar in de Adobe Campaign-interface. Het is alleen bedoeld als een technisch middel om personalisatiegegevens snel op te slaan en af te handelen.

Wanneer de analyse is voltooid, gaat u naar de workflow **[!UICONTROL Properties]** en selecteert u het **[!UICONTROL Variables]** tabblad. Daar kunt u de naam van de tijdelijke lijst zien die u kunt gebruiken om een SQL vraag te maken om identiteitskaarts te tonen die het bevat.

![](assets/perso_optimization_temp_table.png)

## Timing uit verpersoonlijkingsfase {#timing-out-personalization}

Om leveringsbescherming te verbeteren, kunt u een onderbreking voor de verpersoonlijkingsfase plaatsen.

Selecteer op het **[!UICONTROL Delivery]** tabblad van de optie **[!UICONTROL Delivery properties]** een maximumwaarde in seconden voor de **[!UICONTROL Maximum personalization run time]** optie.

Als tijdens de voorvertoning of het verzenden de maximale tijd die u in dit veld instelt, wordt overschreden, wordt het proces afgebroken met een foutbericht en mislukt de levering.

![](assets/perso_time-out.png)

De standaardwaarde is 5 seconden.

Als u deze optie instelt op 0, is er geen tijdslimiet voor de verpersoonlijkingsfase.

## E-mails personaliseren met personalisatievelden {#personalization-fields-video}

Leer hoe u een verpersoonlijkingsveld toevoegt aan de onderwerpregel en de inhoud van een e-maillevering.

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)
