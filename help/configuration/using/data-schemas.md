---
product: campaign
title: Gegevensschema’s
description: Aan de slag met schema's voor campagnegegevens
feature: Schema Extension
role: Data Engineer, Developer
exl-id: d4446035-3988-4d89-b7df-7b8528c2e371
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 1%

---

# Gegevensschema’s{#data-schemas}

## Principes {#principles}

Als u de schema&#39;s wilt bewerken, maken en configureren, klikt u op het knooppunt **[!UICONTROL Administration > Configuration > Data schemas]** van de Adobe Campaign-clientconsole.

>[!NOTE]
>
>Ingebouwde gegevensschema&#39;s kunnen alleen worden verwijderd door een beheerder van uw Adobe Campaign Classic-console.

![](assets/d_ncs_integration_schema_navtree.png)

In het bewerkveld wordt de XML-inhoud van het bronschema weergegeven:

![](assets/d_ncs_integration_schema_edition.png)

>[!NOTE]
>
>Met het besturingselement &#39;Naam&#39; kunt u de schemasleutel invoeren die bestaat uit de naam en naamruimte. De kenmerken &quot;name&quot; en &quot;namespace&quot; van het hoofdelement van het schema worden automatisch bijgewerkt in de XML-bewerkingszone van het schema.

In de voorvertoning wordt het uitgebreide schema automatisch gegenereerd:

![](assets/d_ncs_integration_schema_edition2.png)

>[!NOTE]
>
>Wanneer het bronschema wordt opgeslagen, wordt het genereren van het uitgebreide schema automatisch gestart.

Als u de volledige structuur van een schema moet controleren, kunt u het voorproeflusje gebruiken. Als het schema is uitgebreid, zult u al zijn uitbreidingen dan kunnen visualiseren. Als aanvulling geeft het tabblad Documentatie alle schemakenmerken en -elementen weer, en de bijbehorende eigenschappen (SQL-veld, type/lengte, label, beschrijving). Het tabblad Documentatie geldt alleen voor gegenereerde schema&#39;s. Voor meer op dit, verwijs naar [ Regenererende schema&#39;s ](../../configuration/using/regenerating-schemas.md) sectie.

## Voorbeeld: een tabel met contracten maken {#example--creating-a-contract-table}

In het volgende voorbeeld, willen wij een nieuwe lijst voor **contracten** in het gegevensbestandmodel van het gegevensbestand van Adobe Campaign tot stand brengen. In deze tabel kunt u voor elk contract de voor- en achternaam en het e-mailadres van de houder en de medehouder opslaan.

Hiervoor moet u het schema van de tabel maken en de databasestructuur bijwerken om de bijbehorende tabel te genereren. Pas de volgende stappen toe:

1. Bewerk het knooppunt **[!UICONTROL Administration > Configuration > Data schemas]** van de Adobe Campaign-structuur en klik op **[!UICONTROL New]** .
1. Kies de optie **[!UICONTROL Create a new table in the data model]** en klik op **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_create_new_schema.png)

1. Geef een naam voor de tabel en een naamruimte op.

   ![](assets/s_ncs_configuration_create_new_param.png)

   >[!NOTE]
   >
   >Standaard worden schema&#39;s die door gebruikers worden gemaakt, opgeslagen in de naamruimte &#39;cus&#39;. Voor meer op dit, verwijs naar [ Identificatie van een schema ](../../configuration/using/about-schema-reference.md#identification-of-a-schema).

1. Maak de inhoud van de tabel. Wij adviseren gebruikend de ingangsmedewerker om ervoor te zorgen geen montages ontbreken. Klik hiertoe op de knop **[!UICONTROL Insert]** en kies het type instelling dat u wilt toevoegen.

   ![](assets/s_ncs_configuration_create_new_content.png)

1. Definieer de instellingen voor de tabel met contracten:

   ```
   <srcSchema desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract" mappingType="sql" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <element desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract"
              name="Contracts" autopk="true">
              <attribute name="holderName" label="Holder last name" type="string"/>
              <attribute name="holderFirstName" label="Holder first name" type="string"/>
              <attribute name="holderEmail" label="Holder email" type="string"/>
              <attribute name="co-holderName" label="Co-holder last name" type="string"/>           
              <attribute name="co-holderFirstName" label="Co-holder first name" type="string"/>           
              <attribute name="co-holderEmail" label="Co-holder email" type="string"/>    
              <attribute name="date" label="Subscription date" type="date"/>     
              <attribute name="noContract" label="Contract number" type="long"/>  
     </element>
   </srcSchema>
   ```

   Voeg het type contract toe en plaats een index op het contractaantal.

   ```
   <srcSchema _cs="Contracts (cus)" desc="Active contracts" entitySchema="xtk:srcSchema" img="ncm:channels.png"
              label="Contracts" labelSingular="Contract" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <enumeration basetype="byte" name="typeContract">
       <value label="Home" name="home" value="0"/>
       <value label="Car" name="car" value="1"/>
       <value label="Health" name="health" value="2"/>
       <value label="Pension fund" name="pension fund" value="2"/>
     </enumeration>
     <element autopk="true" desc="Active contracts" img="ncm:channels.png" label="Contracts"
              labelSingular="Contract" name="Contracts">
       <attribute label="Holder last name" name="holderName" type="string"/>
       <attribute label="Holder first name" name="holderFirstName" type="string"/>
       <attribute label="Holder email" name="holderEmail" type="string"/>
       <attribute label="Co-holder last name" name="co-holderName" type="string"/>
       <attribute label="Co-holder first name" name="co-holderFirstName" type="string"/>
       <attribute label="Co-holder email" name="co-holderEmail" type="string"/>
       <attribute label="Subscription date" name="date" type="date"/>
      <attribute desc="Type of contract" enum="cus:Contracts:typeContract" label="Type of contract"
                  name="type" type="byte"/>
       <attribute label="Contract number" name="noContract" type="long"/>
       <dbindex name="noContract" unique="true">
         <keyfield xpath="@noContract"/>
       </dbindex>
     </element>
   </srcSchema>
   ```

1. Sla het schema op om de structuur te genereren:

   ![](assets/s_ncs_configuration_structure.png)

1. Werk de databasestructuur bij om de tabel te maken waarnaar het schema wordt gekoppeld. Voor meer op dit, verwijs naar [ het Bijwerken van de gegevensbestandstructuur ](../../configuration/using/updating-the-database-structure.md).
