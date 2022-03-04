---
product: campaign
title: Het script maken
description: Leer hoe u A/B-tests kunt uitvoeren met een speciale praktijkcase
feature: A/B Testing
exl-id: 4143d1b7-0e2b-4672-ad57-e4d7f8fea028
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 4%

---

# Het script maken {#step-5--creating-the-script}

![](../../assets/common.svg)

De keus van de leveringsinhoud die voor de resterende bevolking wordt bestemd wordt berekend door een manuscript. Met dit script wordt de informatie over de levering met de hoogste snelheid van het openen hersteld en wordt de inhoud naar de uiteindelijke levering gekopieerd.

## Voorbeeld van een script {#example-of-a-script}

Het volgende script kan worden gebruikt zoals in de doelworkflow. Raadpleeg [deze sectie](#implementation) voor meer informatie.

```
 // query the database to find the winner (best open rate)
   var winner = xtk.queryDef.create(
     <queryDef schema="nms:delivery" operation="get">
       <select>
         <node expr="@id"/>
         <node expr="@label"/>
         <node expr="[@operation-id]"/>
         <node expr="[@workflow-id]"/>
       </select>
       <where>
         <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
       </where>
       <orderBy>
         <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
       </orderBy>
     </queryDef>).ExecuteQuery()
   
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)

   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"

   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]

   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
 
   // save the delivery in database
   delivery.save()
 
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
```

Voor een gedetailleerde uitleg van het script raadpleegt u [deze sectie](#details-of-the-script).

## Implementatie {#implementation}

1. Open uw **[!UICONTROL JavaScript code]** activiteit.
1. Het aangeboden script kopiëren in [Voorbeeld van een script](#example-of-a-script) in de **[!UICONTROL JavaScript code]** venster.

   ![](assets/use_case_abtesting_configscript_002.png)

1. In de **[!UICONTROL Label]** Voer de naam van het script in, dus

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. Sluit de **[!UICONTROL JavaScript code]** activiteit.
1. Sla uw workflow op.

## Details van het script {#details-of-the-script}

In deze sectie worden de verschillende delen van het script en de bijbehorende uitvoermodus beschreven.

* Het eerste deel van het script is een query. De **queryDef** kunt u herstellen vanaf **NmsDelivery** de leveringen die worden gemaakt door de doelworkflow uit te voeren en deze te sorteren op basis van hun geschatte openingssnelheid, waarna de informatie uit de levering met de hoogste openingsfrequentie wordt hersteld.

   ```
   // query the database to find the winner (best open rate)
      var winner = xtk.queryDef.create(
        <queryDef schema="nms:delivery" operation="get">
          <select>
            <node expr="@id"/>
            <node expr="@label"/>
            <node expr="[@operation-id]"/>
          </select>
          <where>
            <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
          </where>
          <orderBy>
            <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
          </orderBy>
        </queryDef>).ExecuteQuery()
   ```

* De levering met de hoogste snelheid van opent wordt gedupliceerd.

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* Het label van de gedupliceerde levering wordt gewijzigd en het woord **final** wordt toegevoegd.

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* De levering wordt gekopieerd naar het campagnedashboard.

   ```
   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]
   ```

   ```
   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
   ```

* De levering wordt opgeslagen in de database.

   ```
   // save the delivery in database
   delivery.save()
   ```

* De unieke id van de gedupliceerde levering wordt opgeslagen in de workflowvariabele.

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

## Andere selectiecriteria {#other-selection-criteria}

In het bovenstaande voorbeeld kunt u de inhoud van een levering selecteren op basis van de snelheid waarmee e-mails worden geopend. U kunt het aanpassen om zich op andere levering-specifieke indicatoren te baseren:

* Best geklikt doorvoer: `[indicators/@recipientClickRatio]`,
* Hoogste reactiviteitspercentage (e-mail geopend en klik in het bericht): `[indicators/@reactivity]`,
* Laagste klachtenpercentage: `[indicators/@refusedRatio]` (gebruik de false-waarde voor het kenmerk sortDesc),
* Hoogste conversiesnelheid: `[indicators/@transactionRatio]`,
* Aantal bezochte pagina&#39;s na ontvangst van een bericht: `[indicators/@totalWebPage]`,
* Laagste abonnement: `[indicators/@optOutRatio]`,
* Transactiebedrag: `[indicators/@amount]`.

U kunt nu de uiteindelijke levering definiëren. [Meer informatie](a-b-testing-uc-final-delivery.md).
