---
product: campaign
title: Campagne-responsbeheer configureren
description: Leer hoe te om de Manager van de Reactie van de Campagne te vormen
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1a115ca9-2532-4bd3-be77-814e43250c51
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---

# Campagne-responsbeheer configureren{#configuration}

![](../../assets/v7-only.svg)

Deze sectie is bedoeld voor personen die verantwoordelijk zijn voor het configureren van reactiebeheer. Het veronderstelt een bepaalde hoeveelheid kennis over het uitbreiden van schema&#39;s, het bepalen van werkschema&#39;s, en SQL programmering.

Dit laat u begrijpen hoe te om het standaardgegevensmodel aan de specifieke aard van een transactietabel buiten Adobe Campaign met de lijst van individuen aan te passen. Deze tabel met personen kan samenvallen met de tabel met beschikbare personen in Adobe Campaign of met een andere tabel

De meethypothese wordt gestart door de workflow van het bewerkingsproces ( **[!UICONTROL operationMgt]**). Elke hypothese vertegenwoordigt een afzonderlijk proces dat asynchroon wordt uitgevoerd met een uitvoeringsstatus (Bewerkt, In behandeling, Voltooid, Mislukt, enz.) en gecontroleerd door een planner die prioritaire beperkingen, beperking van het aantal gelijktijdige processen, de lage activiteitenpagina en automatische uitvoering met frequentie beheert.

## Schema&#39;s configureren {#configuring-schemas}

>[!CAUTION]
>
>Wijzig niet de ingebouwde schema&#39;s van de toepassing, maar gebruik eerder het mechanisme van de schemauitbreiding. Anders worden gewijzigde schema&#39;s niet bijgewerkt op het moment van toekomstige upgrades van de toepassing. Dit kan leiden tot storingen tijdens het gebruik van Adobe Campaign.

De integratie van de toepassing is vereist alvorens de reactiemodule te gebruiken, om de diverse te meten lijsten (transacties, transactiedetails) evenals hun verhouding met leveringen, aanbiedingen en individuen te bepalen.

### Standaardschema&#39;s {#standard-schemas}

Het schema **[!UICONTROL nms:remaMatch]** uit de doos bevat de lijst van het reactielogboek, d.w.z. de verhouding tussen individuen, hypothese en transactietabel. Dit schema wordt gebruikt als overervingsschema voor de definitieve bestemmingstabel van de reactielogboeken.

Het schema **[!UICONTROL nms:remaMatchRcp]** wordt ook standaard geleverd en bevat de opslag van reactielogboeken voor Adobe Campaign-ontvangers ( **[!UICONTROL nms:recipient]** ). Om te kunnen worden gebruikt, moet het worden uitgebreid tot een transactietabel (met aankopen enz.).

### Transactietabellen en transactiegegevens {#transaction-tables-and-transaction-details}

De transactietabel moet directe koppelingen naar personen bevatten.

U kunt ook een tabel met transactiegegevens toevoegen. Dit is niet rechtstreeks verbonden met individuen.

Als we bijvoorbeeld een ontvangstbewijs nemen, is een transactietabel gekoppeld aan een contactpersoon (kwitantietabel) en is een kwitantielijsttabel alleen gekoppeld aan de kwitantietabel (detailtabel). U kunt de hypothese dan vormen direct op het niveau waarop de lijst van de ontvangstenkredietlijn met de ontvangstentabel verbonden is.

>[!NOTE]
>
>Als u de kwitantie-id wilt behouden die het verwachte gedrag in de hypothesen beschrijft, kunt u de sjabloon nms:remaMatchRcp-tabel uitbreiden om de id eraan toe te voegen (in dit geval is er geen ROI-berekening gekoppeld aan deze velden).

We raden u aan een gebeurtenisdatum toe te voegen.

In het volgende schema ziet u hoe u verbinding maakt tussen de verschillende tabellen nadat de configuratie is voltooid:

![](assets/response_data_model.png)

### Responsbeheer en ontvangers {#response-management-with-adobe-campaign-recipients}

In dit voorbeeld integreren we een aankooptabel in onze responsbeheermodule met behulp van de ingebouwde ontvankelijke Adobe Campaign-tabel **[!UICONTROL nms:recipient]**.

De lijst van reactie meldt op een **[!UICONTROL nms:remaMatchRcp]** ontvanger wordt uitgebreid om een verbinding aan het schema van de kooplijst toe te voegen. In het volgende voorbeeld wordt de aankooptabel **demo:purchase** genoemd.

1. Selecteer via de Adobe Campaign-verkenner **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**.
1. Klik met de rechtermuisknop **Ontvanger** en selecteer **[!UICONTROL Actions]** en **[!UICONTROL Modify the options of the targeting dimensions]**.

   ![](assets/delivery_mapping1.png)

1. U kunt **[!UICONTROL Extension namespace]** in het volgende venster personaliseren, dan klik **[!UICONTROL Next]**.

   ![](assets/delivery_mapping2.png)

1. Controleer of in de categorie **[!UICONTROL Response management]** het selectievakje **[!UICONTROL Generate a storage schema for reactions]** is ingeschakeld.

   Klik vervolgens op **[!UICONTROL Define additional fields...]** om de gerelateerde transactietabellen te selecteren en voeg de gewenste velden toe aan de extensie van het schema nms:remaMatchRcp.

   ![](assets/delivery_mapping3.png)

Het gemaakte schema ziet er als volgt uit:

```
<srcSchema _cs="Reactions (Recipients) (cus)" entitySchema="xtk:srcSchema" extendedSchema="nms:remaMatchRcp" 
img="nms:remaMatch.png" implements="xtk:persist" label="Reactions (Recipients)" mappingType="sql"
name="remaMatchRcp" namespace="cus">  
 <element label="Reactions (Recipients)" name="remaMatchRcp">    
  <key internal="true" name="match">      
   <keyfield xlink="hypothesis"/>      
   <keyfield xlink="broadLog"/>      
   <keyfield xlink="proposition"/>    
  </key>    
  <attribute label="Quantity" name="quantity" type="long"/>    
  <element name="purchase" target="demo:purchase" type="link"/>    
  <element name="hypothesis" revLabel="Reactions (Recipients)" revLink="remaMatchRcp"/>    
  <element applicableIf="HasPackage('nms:coreInteraction')" label="Proposition" name="proposition" target="nms:propositionRcp" type="link"/>   
  <element desc="Message (Delivery log)" label="Message" name="broadLog" target="nms:broadLogRcp" type="link"/>    
  <element label="Respondent" name="responder" target="nms:recipient" type="link"/>  
 </element>  
 <createdBy _cs="Administrator (admin)"/>  
 <modifiedBy _cs="Administrator (admin)"/>
</srcSchema>
```

### Het beheer van de reactie met een gepersonaliseerde ontvankelijke lijst {#response-management-with-a-personalized-recipient-table}

In dit voorbeeld integreren we een aankooptabel in onze responsbeheermodule met een andere individuele tabel dan de tabel voor ontvangers die beschikbaar is in Adobe Campaign.

* Creeer een nieuw schema van het reactielogboek dat van het **[!UICONTROL nms:remaMatch]** schema wordt afgeleid.

   Aangezien de lijst van individuen van de lijst van ontvangers van Adobe Campaign verschillend is, is het noodzakelijk om een nieuw schema van de reactielogboeken tot stand te brengen die op het **[!UICONTROL nms:remaMatch]** schema worden gebaseerd. Vul vervolgens het bestand in met koppelingen naar de leveringslogboeken en de aankooptabel.

   In het volgende voorbeeld gebruiken we het schema **demo:wideLogPers** en de transactietabel **demo:purchase**:

   ```
   <srcSchema desc="Linking of a recipient transaction to a hypothesis"    
   img="nms:remaMatch.png" label="Responses on persons" labelSingular="Responses on a person" name="remaMatchPers" namespace="nms">
     <element name="remaMatchPers" template="nms:remaMatch">
       <key internal="true" name="match">
         <keyfield xlink="hypothesis"/>
        <keyfield xlink="purchase"/>
       </key>
   
       <element name="hypothesis" revLabel="Response logs for persons" revLink="remaMatchPers"/>
       <element applicableIf="HasPackage('nms:interaction')" label="Proposition" name="proposition"
                target="demo:propositionPers" type="link"/>
       <element label="Delivery log" name="broadLog" target="demo:broadLogPers" type="link"/>
     </element>
   </srcSchema>
   ```

* Wijzig de hypothesevorm in het schema **[!UICONTROL nms:remaHypothesis]**.

   Standaard is de lijst met responslogboeken zichtbaar in de logboeken van de geadresseerde. U moet daarom het hypotheseformulier wijzigen om de nieuwe reactielogboeken te bekijken die tijdens de vorige stap zijn gemaakt.

   Bijvoorbeeld:

   ```
    <container type="visibleGroup" visibleIf="[context/@remaMatchStorage]= 'demo:remaMatchPers'">
                 <input hideEditButtons="true" img="nms:remaMatch.png" nolabel="true" refresh="true"
                  toolbarCaption="Responses generated by the hypothesis" type="linklist"
                  xpath="remaMatchPers">
             <input xpath="[.]"/>
             <input xpath="@controlGroup"/>
           </input>
      </container> 
   ```

## Indicatoren beheren {#managing-indicators}

De module van de Manager van de Reactie komt met een lijst van vooraf bepaalde indicatoren. U kunt echter ook andere maatindicatoren toevoegen.

Hiertoe moet u de hypothesetabel uitbreiden door twee velden in te voegen voor elke nieuwe indicator:

* de eerste voor de doelpopulatie,
* de tweede voor de controlegroep.

Bijvoorbeeld:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:remaHypothesis" label="Measurement hypothesis" 
md5="1D4DED54FF8EC2432AED6736EDE6F547" name="remaHypothesis" namespace="demo" xtkschema="xtk:srcSchema">  
    <element name="remaHypothesis">    
        <element name="indicators">      
            <!-- Quantity -->      
            <attribute label="Total contacted" name="contactReactedTotalQuantity" type="long"/>
            <attribute label="Total number of people in the control group" name="proofReactedTotalquantity" type="long"/> 
        </element> 
    </element>
</srcSchema>
```
