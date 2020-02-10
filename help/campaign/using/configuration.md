---
title: Configuratie
seo-title: Configuratie
description: Configuratie
seo-description: null
page-status-flag: never-activated
uuid: 59503b54-ad49-4b00-8ffb-52e6f6c62070
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: ed4afa5e-c184-4c8e-a086-41d87b863190
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Configuratie{#configuration}

Deze sectie is bedoeld voor personen die verantwoordelijk zijn voor het configureren van reactiebeheer. Het veronderstelt een bepaalde hoeveelheid kennis over het uitbreiden van schema&#39;s, het bepalen van werkschema&#39;s, en SQL programmering.

Zo kunt u begrijpen hoe u het standaardgegevensmodel kunt aanpassen aan de specifieke aard van een transactietabel die zich buiten Adobe Campaign bevindt, met de tabel van personen. Deze tabel met personen kan samenvallen met de tabel met beschikbare personen in Adobe Campaign of met een andere tabel

De meethypothese wordt gestart door de workflow van het bewerkingsproces ( **[!UICONTROL operationMgt]** ). Elke hypothese vertegenwoordigt een afzonderlijk proces dat asynchroon wordt uitgevoerd met een uitvoeringsstatus (Bewerkt, In behandeling, Voltooid, Mislukt, enz.) en gecontroleerd door een planner die prioritaire beperkingen, beperking van het aantal gelijktijdige processen, de lage activiteitenpagina en automatische uitvoering met frequentie beheert.

## Schema&#39;s configureren {#configuring-schemas}

>[!CAUTION]
>
>Wijzig niet de standaardschema&#39;s van de toepassing, maar gebruik eerder het mechanisme van de schemauitbreiding. Anders worden gewijzigde schema&#39;s niet bijgewerkt op het moment van toekomstige upgrades van de toepassing. Dit kan leiden tot storingen tijdens het gebruik van Adobe Campaign.

De integratie van de toepassing is vereist alvorens de reactiemodule te gebruiken, om de diverse te meten lijsten (transacties, transactiedetails) evenals hun verhouding met leveringen, aanbiedingen en individuen te bepalen.

### Standaardschema&#39;s {#standard-schemas}

Het out-of-the-box **[!UICONTROL nms:remaMatch]** schema bevat de tabel met het reactielogboek, d.w.z. de relatie tussen individuen, hypothese en transactietabel. Dit schema wordt gebruikt als overervingsschema voor de definitieve bestemmingstabel van de reactielogboeken.

Het **[!UICONTROL nms:remaMatchRcp]** schema wordt ook standaard geleverd. Het bevat de opslag van reactielogboeken voor Adobe Campaign-ontvangers ( **[!UICONTROL nms:recipient]** ). Om te kunnen worden gebruikt, moet het worden uitgebreid tot een transactietabel (met aankopen enz.).

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

### Responsbeheer met ontvangers van Adobe Campagne {#response-management-with-adobe-campaign-recipients}

In dit voorbeeld integreren we een aankooptabel in onze responsbeheermodule met behulp van de ontvankelijke tabel voor Adobe Campagne ( **[!UICONTROL nms:recipient]** ).

De lijst van reactielogboeken op een **[!UICONTROL nms:remaMatchRcp]** ontvanger wordt uitgebreid om een verbinding aan het schema van de kooplijst toe te voegen. In het volgende voorbeeld wordt de aankooptabel **demo:purchase** genoemd.

1. Selecteer via de Adobe Campaign-verkenner de optie **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**.
1. Klik met de rechtermuisknop op **Ontvanger** en selecteer **[!UICONTROL Actions]** en **[!UICONTROL Modify the options of the targeting dimensions]**.

   ![](assets/delivery_mapping1.png)

1. U kunt de afbeelding aanpassen **[!UICONTROL Extension namespace]** in het volgende venster en vervolgens klikken **[!UICONTROL Next]**.

   ![](assets/delivery_mapping2.png)

1. Controleer in de **[!UICONTROL Response management]** categorie of het **[!UICONTROL Generate a storage schema for reactions]** selectievakje is ingeschakeld.

   Klik vervolgens **[!UICONTROL Define additional fields...]** om de gerelateerde transactietabellen te selecteren en voeg de gewenste velden toe aan de extensie van het schema nms:remaMatchRcp.

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

In dit voorbeeld integreren we een aankooptabel in onze responsbeheermodule met een andere individuele tabel dan de tabel voor ontvangers die beschikbaar is in Adobe Campagne.

* Creërend een nieuw schema van het reactielogboek dat van het **[!UICONTROL nms:remaMatch]** schema wordt afgeleid.

   Aangezien de lijst van individuen van de lijst van de ontvangers van de Campagne van Adobe verschillend is, is het noodzakelijk om een nieuw schema van de reactielogboeken tot stand te brengen die op het **[!UICONTROL nms:remaMatch]** schema worden gebaseerd. Vul vervolgens het bestand in met koppelingen naar de leveringslogboeken en de aankooptabel.

   In het volgende voorbeeld gebruiken we het schema **demo:wideLogPers** en de **demo:purchase** transactie:

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

* De vorm van de hypothese wijzigen in het **[!UICONTROL nms:remaHypothesis]** schema.

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

## Beheer van indicatoren {#managing-indicators}

De module van de Manager van de Reactie komt met een lijst van vooraf bepaalde indicatoren. U kunt echter ook andere persoonlijke maatindicatoren toevoegen.

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

