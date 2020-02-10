---
title: Lokale goedkeuring
seo-title: Lokale goedkeuring
description: Lokale goedkeuring
seo-description: null
page-status-flag: never-activated
uuid: 4de59c8a-e229-4c8d-acab-2b116cafb70b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a223641e-93e1-42ef-bb6b-8e1a0f8f6a65
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Lokale goedkeuring{#local-approval}

Wanneer geïntegreerd in een het richten werkschema, laat de **[!UICONTROL Local approval]** activiteit u opstelling een ontvankelijk goedkeuringsproces alvorens de levering wordt verzonden.

![](assets/local_validation_0.png)

>[!CAUTION]
>
>Om deze activiteit te gebruiken, moet u de Verdeelde module van de Marketing hebben gekocht, die een optie van de Campagne is. Controleer uw licentieovereenkomst.

Voor een voorbeeld van de **[!UICONTROL Local approval]** activiteit met een distributiemalplaatje, verwijs naar het [Gebruiken van de lokale goedkeuringsactiviteit](../../workflow/using/using-the-local-approval-activity.md).

Voer eerst een label in voor de activiteit en het **[!UICONTROL Action to execute]** veld:

![](assets/local_validation_1.png)

* Selecteer de **[!UICONTROL Target approval notification]** optie om een bericht-mail naar lokale supervisors vóór de levering te verzenden, vragend hen om de ontvangers goed te keuren die aan hen worden toegewezen.

   ![](assets/local_validation_intro_2.png)

* **Incrementele query**: laat u een vraag uitvoeren en zijn uitvoering plannen. Raadpleeg de sectie [Incrementele query](../../workflow/using/incremental-query.md) .

   ![](assets/local_validation_intro_3.png)

## Doelgoedkeuring {#target-approval-notification}

In dit geval wordt de **[!UICONTROL Local approval]** activiteit geplaatst tussen upstream gericht en levering:

![](assets/local_validation_2.png)

De velden die moeten worden ingevuld in het geval van een kennisgeving voor goedkeuring als doel zijn:

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**: Selecteer de **[!UICONTROL Specified in the transition]** optie als u een **[!UICONTROL Split]** type activiteit gebruikt om de doelpopulatie te beperken. In dit geval wordt de distributiesjabloon in de splitsingsactiviteit ingevoerd. Als u de beoogde populatie niet beperkt, selecteert u hier de **[!UICONTROL Explicit]** optie en voert u de distributiesjabloon in het **[!UICONTROL Data distribution]** veld in.

   Voor meer informatie over het creëren van een malplaatje van de gegevensdistributie, verwijs naar het [Beperken van het aantal subsetverslagen per gegevensdistributie](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution).

* **[!UICONTROL Approval management]**

   * Selecteer de leveringssjabloon en het onderwerp dat voor het e-mailbericht wordt gebruikt. Er is een standaardsjabloon beschikbaar: **[!UICONTROL Local approval notification]**. U kunt ook een beschrijving toevoegen die boven de lijsten met ontvangers wordt weergegeven in de goedkeurings- en feedbackberichten.
   * Geef aan **[!UICONTROL Approval type]** welke termijn overeenkomt met de goedkeuringstermijn (datum of uiterste datum vanaf het begin van de goedkeuring). Op deze datum wordt de workflow opnieuw gestart en wordt bij het bepalen van de doelen geen rekening gehouden met de ontvangers die niet zijn goedgekeurd. Zodra de berichten zijn verzonden, wordt de activiteit een rij gevormd zodat de lokale supervisors hun contacten kunnen goedkeuren.

      >[!NOTE]
      >
      >Wanneer het goedkeuringsproces wordt gestart, wordt de activiteit standaard drie dagen voortgezet.

      U kunt ook een of meer herinneringen toevoegen om lokale toezichthouders te laten weten dat de deadline nadert. Klik hiertoe op de **[!UICONTROL Add a reminder]** koppeling.

* **[!UICONTROL Complementary set]**: Met de **[!UICONTROL Generate complement]** optie kunt u een tweede set genereren die alle niet-goedgekeurde doelen bevat.

   >[!NOTE]
   >
   >Deze optie is standaard uitgeschakeld.

## Feedbackrapport leveren {#delivery-feedback-report}

In dit geval wordt de **[!UICONTROL Local approval]** activiteit na de levering geplaatst:

![](assets/local_validation_4.png)

In het geval van een feedbackrapport voor levering moeten de volgende velden worden ingevuld:

![](assets/local_validation_workflow_4.png)

* Selecteer de **[!UICONTROL Specified in the transition]** optie als de levering is ingevoerd tijdens een vorige activiteit. Selecteer deze optie **[!UICONTROL Explicit]** om de levering op te geven in de lokale goedkeuringsactiviteit.
* Selecteer de leveringssjabloon en het object van het e-mailbericht. Er is een standaardsjabloon: **[!UICONTROL Local approval notification]**.

## Voorbeeld: Workflowlevering goedkeuren {#example--approving-a-workflow-delivery}

In dit voorbeeld wordt getoond hoe u een goedkeuringsproces voor workflowlevering instelt. Raadpleeg het [voorbeeld voor meer informatie over het maken van workflows voor levering: sectie over de leveringsworkflow](../../workflow/using/delivery.md#example--delivery-workflow) .

Een exploitant kan een levering op één van twee manieren goedkeuren: het gebruiken van de Web-pagina verbonden in het e-mailbericht, of via de console.

* Webgoedkeuring

   Met het e-mailbericht dat naar beheerders van de groep Beheerders wordt verzonden, kunt u het leveringsdoel goedkeuren. Het bericht gebruikt de gedefinieerde tekst en de JavaScript-expressie wordt vervangen door de berekende waarde (in dit geval &#39;574&#39;)

   Als u de levering wilt goedkeuren, klikt u op de desbetreffende koppeling en meldt u zich aan bij de Adobe Campaign-console.

   ![](assets/new-workflow-valid-webaccess.png)

   Maak een keuze en klik op de **[!UICONTROL Submit]** knop.

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* Goedkeuring via de console

   In de boomstructuur, bevat de **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** knoop de lijst van taken die door de exploitant moeten worden goedgekeurd die momenteel wordt verbonden. In de lijst moet één regel worden weergegeven. Dubbelklik op deze regel om te reageren. Het volgende venster wordt weergegeven:

![](assets/new-workflow-7.png)

Selecteer **Ja** en klik op **[!UICONTROL Approve]**. U ontvangt een bericht met de mededeling dat de reactie is opgenomen.

Ga terug naar het workflowscherm: Na tien seconden of zo, wordt het diagram getoond als volgt:

![](assets/new-workflow-8.png)

De workflow heeft de **[!UICONTROL Delivery control]** taak uitgevoerd, wat in dit geval betekent dat de eerder gemaakte levering wordt gestart. De workflow is zonder fouten voltooid.
