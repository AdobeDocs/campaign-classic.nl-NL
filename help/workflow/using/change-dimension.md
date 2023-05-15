---
product: campaign
title: Dimensie wijzigen
description: Dimensie wijzigen
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: c3de99f8-089f-4c7c-be11-f375a9463eaa
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---

# Dimensie wijzigen{#change-dimension}



De activiteit van de veranderingsdimensie laat u de het richten dimensie tijdens de cyclus van de doelbouw veranderen. Axisverschuiving is afhankelijk van de gegevenssjabloon en de invoerdimensie. Dit laat u van de &quot;contracten&quot;afmeting aan de &quot;cliënten&quot;afmeting schakelen, bijvoorbeeld.

U kunt deze activiteit ook gebruiken om de extra kolommen van het nieuwe doel te bepalen.

Het is mogelijk criteria voor gegevensdeduplicatie vast te stellen.

## Configuratiemodus {#configuration-mode}

Om de activiteit van de veranderingsdimensie te vormen, pas de volgende stappen toe:

1. Selecteer de nieuwe doeldimensie via de **[!UICONTROL Change dimension]** veld.

   ![](assets/s_user_change_dimension_param1.png)

1. Tijdens het wijzigen van de afmetingen kunt u alle elementen behouden of selecteren die in de uitvoer moeten worden bewaard. In het volgende voorbeeld, max. Aantal duplicaten is ingesteld op 2.

   ![](assets/s_user_change_dimension_limit.png)

   Wanneer u verkiest om slechts één verslag te houden, wordt een inzameling getoond in het het werkschema: Deze verzameling vertegenwoordigt alle records die in het eindresultaat niet als doel zullen worden gebruikt (aangezien er slechts één record wordt bewaard). Net als bij alle andere verzamelingen kunt u met deze verzameling aggregaten berekenen of gegevens in kolommen herstellen.

   Als u bijvoorbeeld de opdracht **[!UICONTROL Customers]** de **[!UICONTROL Recipients]** afmeting, zal het mogelijk zijn om klanten van een specifieke opslag te richten, terwijl het toevoegen van het aantal gemaakte aankopen.

1. Als u verkiest om al deze informatie niet te houden, kunt u de dubbele beheerswijze vormen.

   ![](assets/s_user_change_dimension_param2.png)

   Met de blauwe pijlen kunt u de dubbele verwerkingsprioriteit definiëren.

   In het bovenstaande voorbeeld worden ontvangers eerst gededupliceerd op hun e-mailadres en vervolgens, indien nodig, op hun accountnummer.

1. De **[!UICONTROL Result]** kunt u aanvullende informatie toevoegen.

   U kunt bijvoorbeeld het land herstellen op basis van de postcode met behulp van een **Subtekenreeks** type functie. Dit doet u als volgt:

   * Klik op de knop **[!UICONTROL Add data...]** koppelen en selecteren **[!UICONTROL Data linked to the filtering dimension]**.

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >Voor informatie over het creëren van en het beheren van extra kolommen, verwijs naar [Gegevens toevoegen](query.md#adding-data).

   * Selecteer de vorige gericht afmeting (vóór asschakelaar) en selecteer **[!UICONTROL Zip Code]** in de **[!UICONTROL Location]** substructuur, en klik vervolgens op **[!UICONTROL Edit expression]**.

      ![](assets/wf_change-dimension_sample_02.png)

   * Klikken **[!UICONTROL Advanced selection]** en kiest u **[!UICONTROL Edit the formula using an expression]**.

      ![](assets/wf_change-dimension_sample_03.png)

   * Gebruik de functies in de lijst en geef de uit te voeren berekening op.

      ![](assets/wf_change-dimension_sample_04.png)

   * Tot slot ga het etiket van de kolom in u enkel hebt gecreeerd.

      ![](assets/wf_change-dimension_sample_05.png)

1. Voer het werkschema uit om het resultaat van deze configuratie te bekijken. Vergelijk de gegevens in de tabellen voor en na de activiteit voor de veranderingsdimensie en vergelijk de structuur van de workflowtabellen, zoals in de volgende voorbeelden wordt getoond:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)
