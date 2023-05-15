---
product: campaign
title: Lokale goedkeuring
description: Lokale goedkeuring
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 2d9cbfc8-1f99-4b38-8460-77c7c986e9ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# Lokale goedkeuring{#local-approval}



Wanneer het in een het richten werkschema wordt geïntegreerd, **[!UICONTROL Local approval]** Met activiteit kunt u een goedkeuringsproces voor ontvangers instellen voordat de levering wordt verzonden.

![](assets/local_validation_0.png)

>[!CAUTION]
>
>Om deze activiteit te gebruiken, moet u de Verdeelde module van de Marketing hebben gekocht, die een optie van de Campagne is. Controleer hiervoor uw licentieovereenkomst.

Voor een voorbeeld van het **[!UICONTROL Local approval]** activiteit met een distributiemalplaatje, verwijs naar [De lokale goedkeuringsactiviteit gebruiken](using-the-local-approval-activity.md).

Begin door een etiket voor de activiteit in te voeren en **[!UICONTROL Action to execute]** veld:

![](assets/local_validation_1.png)

* Selecteer **[!UICONTROL Target approval notification]** optie om een bericht te verzenden e-mail naar lokale supervisors vóór de levering, vragend hen om de ontvangers goed te keuren die aan hen worden toegewezen.

   ![](assets/local_validation_intro_2.png)

* **Incrementele query**: laat u een vraag uitvoeren en zijn uitvoering plannen. Zie de [Incrementele query](incremental-query.md) sectie.

   ![](assets/local_validation_intro_3.png)

## Doelgoedkeuring {#target-approval-notification}

In dit geval worden de **[!UICONTROL Local approval]** de activiteit wordt geplaatst tussen upstream gericht en de levering:

![](assets/local_validation_2.png)

De velden die moeten worden ingevuld in het geval van een kennisgeving voor goedkeuring als doel zijn:

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**: Selecteer de **[!UICONTROL Specified in the transition]** als u een **[!UICONTROL Split]** type activiteit om de doelpopulatie te beperken. In dit geval wordt de distributiesjabloon in de splitsingsactiviteit ingevoerd. Als u de doelpopulatie niet beperkt, selecteert u de optie **[!UICONTROL Explicit]** en voert u hier de distributiesjabloon in in het dialoogvenster **[!UICONTROL Data distribution]** veld.

   Raadpleeg voor meer informatie over het maken van een sjabloon voor gegevensdistributie [Het aantal subsetrecords per gegevensdistributie beperken](split.md#limiting-the-number-of-subset-records-per-data-distribution).

* **[!UICONTROL Approval management]**

   * Selecteer de leveringssjabloon en het onderwerp dat voor het e-mailbericht wordt gebruikt. Er is een standaardsjabloon beschikbaar: **[!UICONTROL Local approval notification]**. U kunt ook een beschrijving toevoegen die boven de lijsten met ontvangers wordt weergegeven in de goedkeurings- en feedbackberichten.
   * Geef de **[!UICONTROL Approval type]** dat overeenkomt met de goedkeuringstermijn (datum of uiterste datum vanaf het begin van de goedkeuring). Op deze datum wordt de workflow opnieuw gestart en wordt bij het bepalen van de doelen geen rekening gehouden met de ontvangers die niet zijn goedgekeurd. Zodra de berichten zijn verzonden, wordt de activiteit een rij gevormd zodat de lokale supervisors hun contacten kunnen goedkeuren.

      >[!NOTE]
      >
      >Wanneer het goedkeuringsproces wordt gestart, wordt de activiteit standaard drie dagen voortgezet.

      U kunt ook een of meer herinneringen toevoegen om lokale toezichthouders te laten weten dat de deadline nadert. Om dit te doen, klik **[!UICONTROL Add a reminder]** koppeling.

* **[!UICONTROL Complementary set]**: de **[!UICONTROL Generate complement]** Met deze optie kunt u een tweede set genereren die alle niet-goedgekeurde doelen bevat.

   >[!NOTE]
   >
   >Deze optie is standaard uitgeschakeld.

## Feedbackrapport leveren {#delivery-feedback-report}

In dit geval worden de **[!UICONTROL Local approval]** activiteit wordt geplaatst na levering:

![](assets/local_validation_4.png)

In het geval van een feedbackrapport voor levering moeten de volgende velden worden ingevuld:

![](assets/local_validation_workflow_4.png)

* Selecteer **[!UICONTROL Specified in the transition]** als de levering is ingevoerd tijdens een eerdere activiteit. Selecteren **[!UICONTROL Explicit]** om de levering in de lokale goedkeuringsactiviteit te specificeren.
* Selecteer de leveringssjabloon en het object van het e-mailbericht. Er is een standaardsjabloon: **[!UICONTROL Local approval notification]**.

## Voorbeeld: Workflowlevering goedkeuren {#example--approving-a-workflow-delivery}

In dit voorbeeld wordt getoond hoe u een goedkeuringsproces voor workflowlevering instelt. Raadpleeg voor meer informatie over het maken van workflows voor levering de [Voorbeeld: leveringsworkflow](delivery.md#example--delivery-workflow) sectie.

Een exploitant kan een levering op één van twee manieren goedkeuren: het gebruiken van de Web-pagina verbonden in het e-mailbericht, of via de console.

* Webgoedkeuring

   Met het e-mailbericht dat naar beheerders van de groep Beheerders wordt verzonden, kunt u het leveringsdoel goedkeuren. Het bericht gebruikt de gedefinieerde tekst en de JavaScript-expressie wordt vervangen door de berekende waarde (in dit geval &#39;574&#39;)

   Klik op de desbetreffende koppeling en meld u aan bij de Adobe Campaign-console om de levering goed te keuren.

   ![](assets/new-workflow-valid-webaccess.png)

   Maak een keuze en klik op de knop **[!UICONTROL Submit]** knop.

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* Goedkeuring via de console

   In de boomstructuur worden de **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** knooppunt bevat de lijst met taken die moeten worden goedgekeurd door de operator die momenteel is verbonden. In de lijst moet één regel worden weergegeven. Dubbelklik op deze regel om te reageren. Het volgende venster wordt weergegeven:

![](assets/new-workflow-7.png)

Selecteren **Ja** en klik vervolgens op **[!UICONTROL Approve]**. U ontvangt een bericht met de mededeling dat de reactie is opgenomen.

Ga terug naar het workflowscherm: Na tien seconden of zo, wordt het diagram getoond als volgt:

![](assets/new-workflow-8.png)

De workflow heeft de opdracht **[!UICONTROL Delivery control]** taak, wat in dit geval betekent dat de eerder gemaakte levering wordt gestart. De workflow is zonder fouten voltooid.
