---
product: campaign
title: De lokale goedkeuringsactiviteit gebruiken
description: Leer hoe u de lokale goedkeuringsactiviteit gebruikt
feature: Workflows
hide: true
hidefromtoc: true
exl-id: cc29eec9-9c97-4d1b-9567-2581154d7b3f
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1283'
ht-degree: 2%

---

# De lokale goedkeuringsactiviteit gebruiken{#using-the-local-approval-activity}



Met de **[!UICONTROL Local approval]** -activiteit die in een doelworkflow is geïntegreerd, kunt u een goedkeuringsproces voor ontvangers instellen voordat de levering wordt verzonden.

>[!CAUTION]
>
>Als u deze functie wilt gebruiken, moet u de module Distributed Marketing aanschaffen. Dit is een optie Campagne. Controleer hiervoor uw licentieovereenkomst.

Voor het instellen van dit gebruiksgeval hebben we de volgende workflow voor doelversie gemaakt:

![](assets/local_validation_workflow.png)

De belangrijkste stappen in het lokale goedkeuringsproces zijn:

1. De populatie die het resultaat is van het opgeven van doelen, kan worden beperkt dankzij een **[!UICONTROL Split]** -activiteit die gebruikmaakt van een gegevensdistributiemodel.

   ![](assets/local_validation_intro_1.png)

1. De **[!UICONTROL Local approval]** activiteit neemt dan over en verzendt een bericht e-mail naar elke lokale supervisor. De activiteit wordt opgeschort tot elke lokale supervisor de ontvangers goedkeurt die aan hen worden toegewezen.

   ![](assets/local_validation_intro_4.png)

1. Wanneer de deadline voor goedkeuring is bereikt, wordt de workflow opnieuw gestart. In dit voorbeeld wordt de **[!UICONTROL Delivery]** -activiteit gestart en wordt de levering verzonden naar de goedgekeurde doelen.

   >[!NOTE]
   >
   >Zodra de deadline is bereikt, worden ontvangers die niet zijn goedgekeurd, uitgesloten van doelbinding.

   ![](assets/local_validation_intro_6.png)

1. Een paar dagen later verzendt de tweede **[!UICONTROL Local approval]** type activiteit een bericht e-mail naar elke lokale supervisor met een samenvatting van de acties die door hun contacten worden uitgevoerd (kliks, opent, etc.).

   ![](assets/local_validation_intro_5.png)

## Stap 1: Het creëren van het malplaatje van de gegevensdistributie {#step-1--creating-the-data-distribution-template-}

Met de sjabloon voor gegevensdistributie kunt u de populatie beperken die het resultaat is van het richten op basis van gegevensgroepering, terwijl u elke waarde kunt toewijzen aan een lokale toezichthouder. In dit voorbeeld hebben we het veld **[!UICONTROL Email address domain]** gedefinieerd als een distributieveld en een domein toegewezen aan elke lokale toezichthouder

Voor meer bij het creëren van een malplaatje van de gegevensdistributie, verwijs naar [ Beperkend het aantal subsetverslagen per gegevensdistributie ](split.md#limiting-the-number-of-subset-records-per-data-distribution).

1. Ga naar het knooppunt **[!UICONTROL Resources > Campaign management > Data distribution]** en klik op **[!UICONTROL New]** om de sjabloon voor gegevensdistributie te maken.

   ![](assets/local_validation_data_distribution_1.png)

1. Selecteer het tabblad **[!UICONTROL General]**. 

   ![](assets/local_validation_data_distribution_2.png)

1. Voer de **[!UICONTROL Label]** en de **[!UICONTROL Distribution context]** in. In dit voorbeeld hebben we het **[!UICONTROL Recipient]** richtingsschema en het **[!UICONTROL Email domain]** -veld geselecteerd als een distributieveld. De lijst met ontvangers wordt uitgesplitst naar domein.
1. Selecteer in het veld **[!UICONTROL Distribution type]** hoe de waarde van de doelbeperking wordt uitgedrukt op het tabblad **[!UICONTROL Distribution]** . Hier hebben we gekozen voor **[!UICONTROL Percentage]** .
1. Voer in het veld **[!UICONTROL Approval storage]** het opslagschema in van de goedkeuringen die overeenkomen met het gebruikte doelschema. Hier gebruiken we het standaardopslagschema: **[!UICONTROL Local approval of recipients]** .
1. Klik vervolgens op de koppeling **[!UICONTROL Advanced parameters]** .

   ![](assets/local_validation_data_distribution_3.png)

1. Laat de optie **[!UICONTROL Approve the targeted messages]** ingeschakeld zodat alle ontvangers vooraf zijn geselecteerd in de lijst met goed te keuren ontvangers.
1. In het veld **[!UICONTROL Delivery label]** hebben we de standaardexpressie (tekenreeks van de levering berekenen) verlaten. Het standaardlabel van de levering wordt gebruikt in de feedbackmelding.
1. In de sectie **[!UICONTROL Grouping field]** hebben we het veld **[!UICONTROL Gender]** geselecteerd als een groeperingsveld voor het weergeven van ontvangers in goedkeurings- en feedbackberichten.
1. In de sectie **[!UICONTROL Edit targeted messages]** hebben we de parameter **[!UICONTROL Edit recipients]** web application en **[!UICONTROL recipientId]** geselecteerd. In de goedkeurings- en feedbackberichten kunnen ontvangers klikken en verwijzen ze naar de URL van de webtoepassing. De extra URL-parameter is **[!UICONTROL recipientId]** .
1. Klik vervolgens op de tab **[!UICONTROL Distribution]** . Voer voor elk domein de volgende velden in:

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]** : voer de waarde van de domeinnaam in.
   * **[!UICONTROL Percentage / Fixed]**: voer voor elk domein de maximale waarde in. aantal ontvangers waarnaar u de levering wilt verzenden. In dit voorbeeld willen we de levering beperken tot 10% per domein.
   * **[!UICONTROL Label]**: voer het label in van het domein dat moet worden weergegeven in de goedkeurings- en feedbackberichten.
   * **[!UICONTROL Group or operator]** : selecteer de operator of groep operatoren die aan het domein zijn toegewezen.

     >[!CAUTION]
     >
     >Controleer of de juiste rechten aan de exploitanten zijn toegekend.

## Stap 2: de doelworkflow maken {#step-2--creating-the-targeting-workflow}

Voor het instellen van dit gebruiksgeval hebben we de volgende workflow voor doelversie gemaakt:

![](assets/local_validation_workflow.png)

De volgende activiteiten zijn toegevoegd:

* Twee **[!UICONTROL Query]** -activiteiten,
* Eén **[!UICONTROL Intersection]** activiteit,
* Eén **[!UICONTROL Split]** activiteit,
* Eén **[!UICONTROL Local approval]** activiteit,
* Eén **[!UICONTROL Delivery]** activiteit,
* Eén **[!UICONTROL Wait]** activiteit,
* Een tweede **[!UICONTROL Local approval]** activiteit
* Eén **[!UICONTROL End]** activiteit.

### Zoekopdrachten, doorsnede en Splitsen {#queries--intersection-and-split}

Het stroomopwaartse richten bestaat uit twee vragen, één doorsnede en één spleet. De populatie die het resultaat is van het opgeven van doelen, kan worden beperkt met een **[!UICONTROL Split]** -activiteit die gebruikmaakt van een sjabloon voor gegevensdistributie.

Voor meer bij het vormen van een gespleten activiteit, verwijs naar [ Gesplitst ](split.md). De verwezenlijking van een malplaatje van de gegevensdistributie wordt gedetailleerd in [ Beperkend het aantal subsetverslagen per gegevensdistributie ](split.md#limiting-the-number-of-subset-records-per-data-distribution).

Als u de populatie van de query niet wilt beperken, hoeft u de activiteiten **[!UICONTROL Query]** , **[!UICONTROL Intersection]** en **[!UICONTROL Split]** niet te gebruiken. Voer in dit geval de sjabloon voor gegevensdistributie in de eerste **[!UICONTROL Local approval]** -activiteit in.

1. Selecteer in de sectie **[!UICONTROL Record count limitation]** de optie **[!UICONTROL Limit the selected records]** en klik op de koppeling **[!UICONTROL Edit]** .

   ![](assets/local_validation_split_1.png)

1. Selecteer de optie **[!UICONTROL Keep only the first records after sorting]** en klik op **[!UICONTROL Next]** .

   ![](assets/local_validation_split_1bis.png)

1. Voeg in de sectie **[!UICONTROL Sort columns]** het veld toe waarop de sortering wordt toegepast. Hier hebben we het veld **[!UICONTROL Email]** gekozen. Klik op **[!UICONTROL Next]**.

   ![](assets/local_validation_split_2.png)

1. Selecteer de **[!UICONTROL By data distribution]** optie, selecteer eerder gecreeerd distributiemalplaatje (verwijs naar [ Stap 1: Creërend het malplaatje van de gegevensdistributie ](#step-1--creating-the-data-distribution-template-)) en klik **[!UICONTROL Finish]**.

   ![](assets/local_validation_split_3.png)

In het distributiemalplaatje, hebben wij ervoor gekozen om de bevolking tot 10% per groeperingswaarde te beperken, die met de waarden samenvalt die in het werkschema worden getoond (340 als input en 34 als output).

![](assets/local_validation_intro_1.png)

### Goedkeuringsmelding {#approval-notification}

Met de **[!UICONTROL Local approval]** -activiteit kunt u een melding naar elke lokale toezichthouder sturen.

Voor meer bij het vormen van de **[!UICONTROL Local approval]** activiteit, verwijs naar [ Lokale goedkeuring ](local-approval.md).

![](assets/local_validation_workflow_2.png)

De volgende velden moeten worden ingevuld:

1. Selecteer in de sectie **[!UICONTROL Action to execute]** de optie **[!UICONTROL Target approval notification]**.
1. Selecteer in de sectie **[!UICONTROL Distribution context]** de optie **[!UICONTROL Specified in the transition]**.

   Als u de doelpopulatie niet wilt beperken, selecteert u hier de optie **[!UICONTROL Explicit]** en voert u de eerder gemaakte distributiesjabloon in het veld **[!UICONTROL Data distribution]** in.

1. Selecteer in de sectie **[!UICONTROL Notification]** de leveringssjabloon en het onderwerp dat voor de e-mailmelding moet worden gebruikt. Hier hebben we de standaardsjabloon gekozen: **[!UICONTROL Local approval notification]** .
1. In de sectie **[!UICONTROL Approval schedule]** hebben we de standaardgoedkeuringsdeadline (3 dagen) behouden en een herinnering toegevoegd. De levering duurt 3 dagen na de aanvang van de goedkeuring. Zodra de goedkeuringsdeadline is bereikt, worden de ontvangers die niet zijn goedgekeurd niet in aanmerking genomen door zich te richten.

Het meldingsbericht dat door de **[!UICONTROL Local approval]** -activiteit aan lokale toezichthouders wordt verzonden, ziet er als volgt uit:

![](assets/local_validation_intro_2.png)

### Wachten {#wait}

Met de wachtactiviteiten kunt u het starten van de tweede lokale goedkeuringsactiviteit uitstellen die de feedbackmelding voor levering verzendt. In het veld **[!UICONTROL Duration]** hebben we de waarde **[!UICONTROL 5d]** (5 dagen) ingevoerd. De acties die de ontvangers gedurende vijf dagen na de verzending van de levering uitvoeren, worden in de feedbackmelding opgenomen.

![](assets/local_validation_workflow_3.png)

### Feedbackmelding {#feedback-notification}

De tweede **[!UICONTROL Local approval]** activiteit laat u een levering verzenden terugkoppelt bericht aan elke lokale supervisor.

![](assets/local_validation_workflow_4.png)

De volgende velden moeten worden ingevoerd.

1. Kies **[!UICONTROL Delivery feedback report]** in de sectie **[!UICONTROL Action to execute]** .
1. Kies **[!UICONTROL Specified in the transition]** in de sectie **[!UICONTROL Delivery]** .
1. Selecteer in de sectie **[!UICONTROL Notification]** de leveringssjabloon en het onderwerp dat voor de e-mailmelding moet worden gebruikt.

Zodra de termijn die in de wachttijdactiviteit wordt gevormd wordt bereikt, verzendt de tweede **[!UICONTROL Local approval]** typeactiviteit het volgende bericht e-mail naar elke lokale supervisor:

![](assets/local_validation_intro_3.png)

### Goedkeuring bijhouden door de beheerder {#approval-tracking-by-the-administrator}

Telkens wanneer de lokale goedkeuringsactiviteit begint, wordt een goedkeuringstaak gecreeerd. De beheerder kan elk van deze goedkeuringstaken controleren.

Ga naar de doelworkflow van uw campagne en klik op het tabblad **[!UICONTROL Local approval tasks]** .

![](assets/local_validation_admin_1.png)

De lijst met lokale goedkeuringstaken kan ook worden geopend via het tabblad **[!UICONTROL Approval tasks]** van de sjabloon voor gegevensdistributie.

![](assets/local_validation_admin_2.png)

Selecteer de taak die u wilt controleren en klik op de knop **[!UICONTROL Detail]** . Op het tabblad **[!UICONTROL General]** van de lokale goedkeuringstaak kunt u informatie over de taak weergeven. Indien nodig kunt u de goedkeuringsdatums en de herinneringsdatums wijzigen.

![](assets/local_validation_admin_3.png)

Dit tabblad bevat de volgende informatie:

* het label en de id van de taak
* het gebruikte distributiemalplaatje
* het aantal gerichte berichten
* de gekoppelde workflow en campagne
* het taakschema

Op het tabblad **[!UICONTROL Distribution]** voor de taak kunt u de goedkeuringslogboeken, de status ervan, het aantal berichten dat u wilt ontvangen, de goedkeuringsdatum en de operator die de levering heeft goedgekeurd, weergeven.

![](assets/local_validation_admin_4.png)

Selecteer een goedkeuringslogboek en klik op de knop **[!UICONTROL Detail]** om meer informatie weer te geven. Op het tabblad **[!UICONTROL General]** van het lokale goedkeuringslogboek kunt u algemene logboekgegevens weergeven. U kunt ook de goedkeuringsstatus wijzigen.

![](assets/local_validation_admin_5.png)

Dit tabblad bevat de volgende informatie:

* de daarmee verband houdende goedkeuringstaak
* de goedkeuringsstatus (**[!UICONTROL Approved]** of **[!UICONTROL Pending]**)
* het gebruikte distributiemalplaatje
* de lokale toezichthouder die de goedkeuring heeft verleend en de goedkeuringsdatum
* het aantal gerichte en goedgekeurde berichten

Op het tabblad **[!UICONTROL Targeted]** van het goedkeuringslogboek worden de lijst met beoogde ontvangers en hun goedkeuringsstatus weergegeven. U kunt deze status desgewenst wijzigen.

![](assets/local_validation_admin_6.png)
