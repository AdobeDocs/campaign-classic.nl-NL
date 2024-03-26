---
product: campaign
title: Splitsen
description: Meer informatie over de activiteit van de gesplitste workflow
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: 4204350a-c2d2-4033-9bdf-87b49d8211b9
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 0%

---

# Splitsen{#split}



A **Splitsen** Met activiteit van het type -kunt u een doel in verscheidene subsets splitsen. Het doel is samengesteld met alle ontvangen resultaten: alle eerdere activiteiten moeten dus zijn voltooid om deze activiteit te kunnen uitvoeren.

Deze activiteit leidt niet tot een unie van binnenkomende populaties. Als meerdere overgangen in één gesplitste activiteit worden geland, raden we u aan een **[!UICONTROL Union]** activiteiten die voor hem liggen.

Voor een voorbeeld van de splitsingsactiviteit die wordt gebruikt, verwijs naar [Subsets maken met de splitsingsactiviteit](targeting-data.md#creating-subsets-using-the-split-activity).

Een voorbeeld dat illustreert hoe te om de Gesplitste activiteit te gebruiken om het doel in verschillende populaties te segmenteren gebruikend het filtreren voorwaarden wordt beschreven in [deze sectie](cross-channel-delivery-workflow.md).

Er is een voorbeeld beschikbaar van het gebruik van een instantievariabele in een gesplitste activiteit in [deze sectie](javascript-scripts-and-templates.md).

Om deze activiteit te vormen, bepaal de inhoud en het etiket van de ondergroep in **[!UICONTROL Subsets]** en kiest u vervolgens de doeldimensie in het dialoogvenster **[!UICONTROL General]** tab.

## Subsets maken {#creating-subsets}

Een subset maken:

1. Klik op het label in het desbetreffende veld en selecteer het filter dat u wilt toepassen.
1. Selecteer de optie **[!UICONTROL Add a filtering condition]** en klik op de knop **[!UICONTROL Edit...]** koppeling.

   Selecteer het type filter dat op de gegevens moet worden toegepast om het in deze set op te nemen.

   Het proces is hetzelfde als voor een **Query**-type activiteit.

   >[!NOTE]
   >
   >U kunt de gegevens filteren in maximaal twee externe databases (FDA).

1. U kunt het maximumaantal records opgeven dat uit het doel moet worden geëxtraheerd om de subset te maken. Controleer de **[!UICONTROL Limit the selected records]** en klik op de knop **[!UICONTROL Edit...]** koppeling.

   Met een wizard kunt u de selectiemodus kiezen voor records van deze subset. De stappen vindt u in [Het aantal subsetrecords beperken](#limiting-the-number-of-subset-records).

   ![](assets/s_user_segmentation_partage4.png)

1. Indien gewenst kunt u **andere subsets toevoegen** met de **[!UICONTROL Add]** knop.

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >Als de **[!UICONTROL Enable overlapping of output populations]** Deze optie is niet ingeschakeld. Subsets worden in de tabvolgorde gemaakt. Gebruik de pijlen in de rechterbovensectie van dit venster om ze te verplaatsen. Als de eerste subset bijvoorbeeld 70% van de oorspronkelijke populatie herstelt, past de volgende subset zijn selectiecriteria alleen toe op de resterende 30%, enzovoort.

   Voor elke gemaakte subset wordt een uitgaande overgang toegevoegd aan de splitsingsactiviteit.

   ![](assets/s_user_segmentation_partage_add2.png)

   U kunt ervoor kiezen één uitgaande overgang te genereren (en sets te identificeren met behulp van bijvoorbeeld de segmentcode): hiervoor selecteert u de optie **[!UICONTROL Generate subsets in the same table]** in de **[!UICONTROL General]** tab.

   Als het wordt voltooid, wordt de segmentcode van elke subset automatisch opgeslagen in een extra kolom. Deze kolom zal in de verpersoonlijkingsgebieden op leveringsniveau toegankelijk zijn.

## Het aantal subsetrecords beperken {#limiting-the-number-of-subset-records}

Als u niet de gehele populatie wilt gebruiken die zich in een subset bevindt, kunt u het aantal records beperken dat deze bevat.

1. Controleer in het bewerkingsvenster van de subset het **[!UICONTROL Limit the selected records]** en klik op de knop **[!UICONTROL Edit...]** koppeling.
1. Selecteer het type limiet voor uw keuze:

   * **[!UICONTROL Activate random sampling]**: voor deze optie wordt een willekeurige steekproef van de records genomen. Het type willekeurige bemonstering is afhankelijk van de database-engine.
   * **[!UICONTROL Keep only the first records after sorting]**: met deze optie kunt u een beperking definiëren op basis van een of meer sorteervolgorden. Als u **[!UICONTROL Age]** veld als sorteercriterium en 100 als grenswaarde worden alleen de jongste 100 ontvangers gehouden .
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**: Met deze optie worden de twee vorige opties gecombineerd. Hiermee kunt u een beperking definiëren op basis van een of meer sorteervolgorden en vervolgens een willekeurige selectie toepassen op de eerste records als sommige records dezelfde waarden hebben als de gedefinieerde criteria.

     Als u bijvoorbeeld de optie **[!UICONTROL Age]** veld als sorteercriteria, en u definieert dan een limiet van 100, maar de 2000 jongste ontvangers in de database zijn allemaal 18, dan worden 100 ontvangers willekeurig geselecteerd uit die 2000.

   ![](assets/s_user_segmentation_partage_wz1.png)

1. Als u sorteercriteria wilt definiëren, kunt u met een extra stap de kolommen en de sorteervolgorde definiëren.

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. Kies vervolgens de methode voor gegevensbeperking.

   ![](assets/s_user_segmentation_partage_wz2.png)

   Er zijn verschillende manieren om dit te doen:

   * **[!UICONTROL Size (in %)]**: een percentage records. De configuratie hieronder extraheert bijvoorbeeld 10% van de totale bevolking.

     Het percentage is van toepassing op de initiële populatie, niet op het resultaat van de activiteit.

   * **[!UICONTROL Size (as a % of the segment)]**: een percentage van de registers dat alleen betrekking heeft op de subgroepen en niet op de initiële populatie.
   * **[!UICONTROL Maximum size]**: een maximum aantal records.
   * **[!UICONTROL By data grouping]**: u kunt een limiet instellen voor het aantal records, afhankelijk van de waarden in een opgegeven veld van de binnenkomende populatie. Raadpleeg voor meer informatie over dit onderwerp [Het aantal subsetrecords beperken door gegevensgroepering](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data grouping (in %)]**: u kunt een percentage gebruiken om een limiet in te stellen voor het aantal records, afhankelijk van de waarden in een opgegeven veld van de binnenkomende populatie. Raadpleeg voor meer informatie over dit onderwerp [Het aantal subsetrecords beperken door gegevensgroepering](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data distribution]**: Als uw groeperingsvelden te veel waarden hebben of als u wilt voorkomen dat de waarden opnieuw worden ingevoerd voor elke nieuwe gesplitste activiteit, kunt u met Adobe Campaign een **[!UICONTROL By data distribution]** beperking (optionele module Distributed Marketing). Raadpleeg voor meer informatie hierover [Het aantal subsetrecords per gegevensdistributie beperken](#limiting-the-number-of-subset-records-per-data-distribution).

1. Klikken **[!UICONTROL Finish]** de criteria voor de recordselectie goed te keuren. De bepaalde configuratie wordt dan getoond in het middelste venster van de redacteur.

## Het aantal subsetrecords beperken door gegevensgroepering {#limiting-the-number-of-subset-records-by-data-grouping}

U kunt het aantal records beperken door gegevensgroepering. Deze grenswaarde kan met een vaste waarde of een percentage worden vastgesteld.

Als u bijvoorbeeld de **[!UICONTROL Language]** veld als een groepsveld, kunt u een lijst met records voor elke taal definiëren.

1. Nadat u de gegevensbeperkingswaarden hebt geselecteerd, selecteert u **[!UICONTROL By data grouping]** of **[!UICONTROL By data grouping (as a %)]** en klik op **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz3.png)

1. Selecteer vervolgens het (de) groeperingsveld(en) (de categorie **[!UICONTROL Language]** veld (bijvoorbeeld) en klik op **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz4.png)

1. Geef ten slotte de drempelwaarden voor gegevensgroepering op (waarbij de vaste waarden of percentages worden gebruikt, afhankelijk van de eerder geselecteerde groeperingsmethode). Als u dezelfde drempel voor elke waarde wilt instellen, bijvoorbeeld als u het aantal records voor elke taal wilt instellen op 10, selecteert u de optie **[!UICONTROL All data groupings are the same size]** -optie. Als u een andere limiet voor elke waarde wilt instellen, selecteert u de optie **[!UICONTROL Limitations by grouping value]** -optie. Op deze manier kunt u een andere beperking kiezen voor Engels, Frans, enzovoort.

   ![](assets/s_user_segmentation_partage_wz5.png)

1. Klikken **[!UICONTROL Finish]** om de beperking goed te keuren en terug te keren naar het bewerken van de splitsingsactiviteit.

## Het aantal subsetrecords per gegevensdistributie beperken {#limiting-the-number-of-subset-records-per-data-distribution}

Als uw groeperingsvelden een te groot aantal waarden bevatten of als u wilt voorkomen dat waarden opnieuw worden ingesteld voor elke nieuwe gesplitste activiteit, kunt u met Adobe Campaign een beperking per gegevensdistributie maken. Als u gegevensbeperkingswaarden selecteert (zie voor meer informatie over dit onderwerp de [Subsets maken](#creating-subsets) ), selecteert u de **[!UICONTROL By data distribution]** en selecteert u een sjabloon in het keuzemenu. Hieronder ziet u hoe u een sjabloon voor gegevensdistributie maakt.

Voor een voorbeeld van het **[!UICONTROL Local approval]** activiteit met een distributiemalplaatje, verwijs naar [De lokale goedkeuringsactiviteit gebruiken](using-the-local-approval-activity.md).

![](assets/s_user_segmentation_partage_wz6.png)

>[!IMPORTANT]
>
>Als u deze functie wilt gebruiken, moet u de module Distributed Marketing aanschaffen. Dit is een optie Campagne. Controleer hiervoor uw licentieovereenkomst.

Met de sjabloon voor gegevensdistributie kunt u het aantal records beperken aan de hand van een lijst met groeperingswaarden. Voer de volgende stappen uit om een sjabloon voor gegevensdistributie te maken:

1. Ga naar de **[!UICONTROL Resources > Campaign management > Data distribution]** knoop en klik **[!UICONTROL New]**.

   ![](assets/local_validation_data_distribution_1.png)

1. De **[!UICONTROL General]** kunt u het label en de uitvoeringscontext van de distributie (doeldimensie, verspreidingsveld) invoeren.

   ![](assets/local_validation_data_distribution_2.png)

   De volgende velden moeten worden ingevuld:

   * **[!UICONTROL Label]**: label voor de distributiesjabloon.
   * **[!UICONTROL Targeting dimension]**: de doeldimensie vermelden waarop de gegevensverspreiding zal worden toegepast; **[!UICONTROL Recipient]** bijvoorbeeld. Dit schema moet altijd compatibel zijn met de gegevens die worden gebruikt in de doelworkflow.
   * **[!UICONTROL Distribution field]**: selecteer een veld via de doeldimensie. Als u bijvoorbeeld de **[!UICONTROL Email domain]** wordt de lijst met ontvangers uitgesplitst naar domein.
   * **[!UICONTROL Distribution type]**: selecteer de manier waarop de beperkingswaarde van het doel wordt opgesplitst in de **[!UICONTROL Distribution]** tab: **[!UICONTROL Percentage]** of **[!UICONTROL Set]**.
   * **[!UICONTROL Assignment type]**: selecteer het gegevenstype voor de toewijzing van de gegevensdistributie. U kunt kiezen tussen toewijzen per groep of operator of toewijzen door lokale entiteit. Toewijzing door lokale entiteit wordt gebruikt in **Distributed Marketing**. Raadpleeg deze voor meer informatie [sectie](../../distributed/using/about-distributed-marketing.md).
   * **[!UICONTROL Approval storage]**: als u een **[!UICONTROL Local approval]** activiteit in uw het richten werkschema (zie [Lokale goedkeuring](local-approval.md)), voert u het schema in waarin de goedkeuringsresultaten worden opgeslagen. U moet één opslagschema per het richten schema specificeren. Als u het **[!UICONTROL Recipients]** het richten schema, ga het gebrek in **[!UICONTROL Local approval of recipients]** opslagschema.

     In het geval van een eenvoudige beperking door gegevensgroepering zonder lokale goedkeuring, te hoeven u niet om in te gaan **[!UICONTROL Approvals storage]** veld.

1. Als u een **[!UICONTROL Local approval]** activiteit (zie [Lokale goedkeuring](local-approval.md)), voert u de **[!UICONTROL Advanced settings]** voor het distributiemalplaatje:

   ![](assets/local_validation_data_distribution_3.png)

   De volgende velden moeten worden ingevuld:

   * **[!UICONTROL Approve targeted messages]**: controleer deze optie als u wilt dat alle ontvangers vooraf zijn geselecteerd in de lijst met ontvangers die moeten worden goedgekeurd. Als deze optie is uitgeschakeld, wordt geen ontvanger vooraf geselecteerd.

     >[!NOTE]
     >
     >Deze optie is standaard ingeschakeld.

     ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**: hiermee kunt u een expressie definiëren om het leveringslabel weer te geven in het retourbericht. De standaarduitdrukking verstrekt informatie over het standaardetiket van de levering (compute koord). U kunt deze expressie wijzigen.

     ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**: in dit veld kunt u de groepering definiëren die wordt gebruikt om ontvangers weer te geven in goedkeurings- en retourberichten.

     ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**: hiermee kunt u een webtoepassing koppelen aan de lijst met ontvangers. In het goedkeurings en terugkeerbericht, zal elke ontvanger klikbaar zijn en zal met de geselecteerde Webtoepassing verbinden. De **[!UICONTROL Parameters]** field (bijvoorbeeld **[!UICONTROL recipientId]**) kunt u de aanvullende parameter configureren die in de URL en de webtoepassing moet worden gebruikt.

     ![](assets/local_validation_notification_5.png)

1. De **[!UICONTROL Breakdown]** kunt u de lijst met distributiewaarden definiëren.

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**: voer de distributiewaarden in.
   * **[!UICONTROL Percentage / Set]**: voer de recordlimiet (vast of percentage) in die aan elke waarde is gekoppeld.

     Deze kolom wordt gedefinieerd door de **[!UICONTROL Distribution type]** in het veld **[!UICONTROL General]** tab.

   * **[!UICONTROL Label]**: voer het label in dat aan elke waarde is gekoppeld.
   * **[!UICONTROL Group or operator]**: als u een **[!UICONTROL Local approval]** activiteit (zie [Lokale goedkeuring](local-approval.md)), selecteert u de operator of groep van operatoren die aan elke distributiewaarde is toegewezen.

     In het geval van een eenvoudige beperking door gegevensgroepering zonder lokale goedkeuring, te hoeven u niet om in te gaan **[!UICONTROL Group or operator]** veld.

     >[!IMPORTANT]
     >
     >Controleer of de juiste rechten aan de exploitanten zijn toegekend.

   * **[!UICONTROL Local entity]**: selecteer de lokale entiteit die aan elke distributiewaarde is toegewezen. Lokale entiteiten worden gebruikt in **Distributed Marketing**. Raadpleeg deze voor meer informatie [sectie](../../distributed/using/about-distributed-marketing.md).

## Parameters filteren {#filtering-parameters}

Klik op de knop **[!UICONTROL General]** om het activiteitlabel in te voeren. Selecteer de doel- en filterafmetingen voor deze splitsing. Indien nodig kunt u deze afmetingen voor een bepaalde subset wijzigen.

![](assets/s_user_segmentation_partage_general.png)

Controleer de **[!UICONTROL Generate complement]** als u de overblijvende bevolking wilt uitbuiten. De complement is het binnenkomende doel min de samenvoeging van de subsets. Een extra uitgaande overgang zal dan aan de activiteit worden toegevoegd, als volgt:

![](assets/s_user_segmentation_partage_compl.png)

Deze optie werkt alleen correct als de binnenkomende gegevens een primaire sleutel hebben.

Als de gegevens bijvoorbeeld rechtstreeks worden gelezen vanuit een externe database, zoals Netezza (die het begrip index niet ondersteunt) via een **[!UICONTROL Data loading (RDBMS)]** de door de **[!UICONTROL Split]** activiteit is onjuist.

U kunt dit voorkomen door een **[!UICONTROL Enrichment]** activiteit vlak voor de **[!UICONTROL Split]** activiteit. In de **[!UICONTROL Enrichment]** activiteit, controleer **[!UICONTROL Keep all additional data from the main set]** en geef in de aanvullende gegevens de kolommen op die u wilt gebruiken voor het configureren van de filters van de **[!UICONTROL Split]** activiteit. De gegevens van de binnenkomende overgang van de **[!UICONTROL Split]** activiteit wordt dan plaatselijk opgeslagen in een tijdelijke lijst op de server van Adobe Campaign en het complement kan correct worden geproduceerd.

De **[!UICONTROL Enable overlapping of output populations]** Met deze optie kunt u populaties beheren die tot verschillende subsets behoren:

* Wanneer het vakje niet wordt gecontroleerd, zorgt de gespleten activiteit ervoor een ontvanger niet in verscheidene outputovergangen kan aanwezig zijn, zelfs als het aan de criteria van verscheidene subsets voldoet. Deze worden als doel ingesteld op het eerste tabblad met overeenkomende criteria.
* Als het selectievakje is ingeschakeld, kunnen de ontvangers in verschillende subsets worden gevonden als ze voldoen aan hun filtercriteria. Adobe Campaign raadt aan exclusieve criteria te hanteren.

## Invoerparameters {#input-parameters}

* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.

## Uitvoerparameters {#output-parameters}

* tableName
* schema
* recCount

Deze reeks van drie waarden identificeert het doel dat uit de uitsluiting voortvloeit. **[!UICONTROL tableName]** is de naam van de lijst die de doelherkenningstekens registreert, **[!UICONTROL schema]** is het schema van de populatie (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de tabel.

De overgang verbonden aan het complement heeft de zelfde parameters.
