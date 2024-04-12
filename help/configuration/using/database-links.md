---
product: campaign
title: Databasetoewijzing
description: Databasetoewijzing
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: e05dcd81-bbca-4767-8da3-ea064f7f6c8e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 1%

---

# Beheer van koppeling {#links--relation-between-tables}

Een koppeling beschrijft de koppeling tussen de ene tabel en de andere.

Hieronder worden ook de soorten verenigingen genoemd, die ook kardinaliteiten worden genoemd.

* Kardinaliteit 1-1: één instantie van de brontabel kan maximaal één overeenkomende instantie van de doeltabel hebben.
* Kardinaliteit 1-N: één voorkomen van de bronlijst kan verscheidene overeenkomstige voorkomen van de doellijst hebben, maar één voorkomen van de doellijst kan hoogstens één overeenkomstige voorkomen van de bronlijst hebben.
* Kardinaliteit N-N: één instantie van de brontabel kan meerdere corresponderende instanties van de doeltabel hebben, en omgekeerd.

In de gebruikersinterface worden kardinaliteiten weergegeven met een specifiek pictogram.

Voor het samenvoegen van relaties met een tabel/database voor campagnes:

* ![](assets/join_with_campaign11.png) : Kardinaliteit 1-1. Bijvoorbeeld tussen een ontvanger en een huidige orde. Een ontvanger kan aan slechts één voorkomen van de huidige ordetabel tegelijkertijd worden verwant.
* ![](assets/externaljoin11.png) : Kardinaliteit 1-1, externe verbinding. Bijvoorbeeld tussen een ontvanger en hun land. Een ontvanger kan slechts aan één voorkomen van het lijstland worden verwant. De inhoud van de landentabel wordt niet opgeslagen.
* ![](assets/join_with_campaign1n.png) : Kardinaliteit 1-N. Bijvoorbeeld tussen een ontvanger en de abonnementstabel. Een ontvanger kan zijn verwant aan verscheidene voorkomen op de abonnementstabel.

Voor join-relaties met FDA (Federated Database Access):

* ![](assets/join_fda_11.png) : Kardinaliteit 1-1
* ![](assets/join_fda_1m.png) : Kardinaliteit 1-N

Raadpleeg voor meer informatie over FDA-tabellen [Een externe database openen](../../installation/using/about-fda.md).

Een koppeling moet worden gedeclareerd in het schema met de externe sleutel van de tabel die is gekoppeld via het hoofdelement:

```sql
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Koppelingen voldoen aan de volgende regels:

* De definitie van een koppeling wordt ingevoerd op een **link**-type **`<element>`** met de volgende kenmerken:

   * **name**: naam van koppeling in de brontabel
   * **target**: naam van doelschema
   * **label**: label van koppeling
   * **revLink** (optioneel): naam van de omgekeerde koppeling in het doelschema (standaard automatisch afgetrokken)
   * **integriteit** (facultatief): referentiële integriteit van het voorkomen van de bronlijst aan het voorkomen van de doellijst.
Mogelijke waarden zijn:

      * **definiëren**: het is mogelijk om de broninstantie te verwijderen als er niet langer naar wordt verwezen door een doelinstantie
      * **normaal**: als u de broninstantie verwijdert, worden de toetsen van de koppeling naar de doelinstantie (standaardmodus) geïnitialiseerd. Bij dit type integriteit worden alle externe toetsen geïnitialiseerd
      * **eigen**: als u de broninstantie verwijdert, wordt de doelinstantie verwijderd
      * **owncopy**: gelijk aan **eigen** (in geval van verwijdering) of dupliceert de voorvallen (in geval van duplicatie)
      * **neutraal**: geen specifiek gedrag

   * **revIntegrity** (optioneel): integriteit in het doelschema (optioneel, standaard &quot;normaal&quot;)
   * **revCardinality** (optioneel): met de waarde &quot;single&quot; wordt de kardinaliteit gevuld met type 1-1 (standaard 1-N)
   * **externalJoin** (optioneel): forceert de buitenste verbinding
   * **revExternalJoin** (optioneel): hiermee wordt de buitenste verbinding op de omgekeerde koppeling gedwongen

* Een koppeling verwijst naar een of meer velden van de brontabel naar de doeltabel. De velden waaruit de verbinding bestaat ( `<join>`  -element) hoeft niet te worden gevuld omdat deze automatisch worden afgetrokken met de interne sleutel van het doelschema.
* Er wordt automatisch een index toegevoegd aan de externe sleutel van de koppeling in het uitgebreide schema.
* Een verbinding bestaat uit twee half-verbindingen, waar het eerste van het bronschema wordt verklaard en het tweede automatisch in het uitgebreide schema van het doelschema wordt gecreeerd.
* Een samenvoeging kan een buitenste samenvoeging zijn als **externalJoin** wordt toegevoegd, met de waarde &quot;true&quot; (wordt ondersteund in PostSQL).

>[!NOTE]
>
>Standaard zijn koppelingen de elementen die aan het einde van het schema worden gedeclareerd.

## Voorbeeld: omgekeerde koppeling {#example-1}

In het onderstaande voorbeeld declareren we een 1-N relatie tot de schematabel &quot;cus:company&quot;:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Het gegenereerde schema:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

De koppelingsdefinitie wordt aangevuld met de velden waaruit de verbinding bestaat, d.w.z. de primaire sleutel met zijn XPath (&quot;@id&quot;) in het doelschema en de buitenlandse sleutel met zijn XPath (&quot;@company-id&quot;) in het schema.

De buitenlandse sleutel wordt automatisch toegevoegd in een element dat de zelfde kenmerken zoals het bijbehorende gebied in de bestemmingslijst, met de volgende noemende overeenkomst gebruikt: naam van doelschema dat door naam van bijbehorend gebied (&quot;bedrijf-identiteitskaart&quot;in ons voorbeeld) wordt gevolgd.

Uitgebreid schema van het doel (&quot;cus:company&quot;):

```sql
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

Er is een omgekeerde koppeling naar de tabel &quot;cus:receiving&quot; toegevoegd met de volgende parameters:

* **name**: wordt automatisch afgetrokken van de naam van het bronschema (kan worden afgedwongen met het kenmerk &quot;revLink&quot; in de koppelingsdefinitie in het bronschema)
* **revLink**: naam van omgekeerde koppeling
* **target**: sleutel van gekoppeld schema (&quot;focus:ontvanger&quot;-schema)
* **ongebonden**: de koppeling wordt gedeclareerd als een verzamelingselement voor een kardinaliteit van 1 N (standaard)
* **integriteit**: &quot;define&quot;door gebrek (kan met het &quot;revIntegrity&quot;attribuut in de verbindingsdefinitie op het bronschema worden gedwongen).

## Voorbeeld: eenvoudige koppeling {#example-2}

In dit voorbeeld, verklaren wij een verbinding aan de &quot;nms:adres&quot;schemalijst. De join is een outer join en wordt expliciet gevuld met het e-mailadres van de ontvanger en het veld &quot;@address&quot; van de gekoppelde tabel (&quot;nms:address&quot;).

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

## Voorbeeld: unieke kardinaliteit {#example-3}

In dit voorbeeld maken we een 1-1 relatie met de schematabel &quot;cus:extension&quot;:

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

## Voorbeeld: koppelen naar een map {#example-4}

In dit voorbeeld wordt een koppeling naar een map gedeclareerd (&quot;xtk:folder&quot;-schema):

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

De standaardwaarde retourneert de id van het eerste toepasselijke parametertype-bestand dat is ingevoerd in de functie &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;.

## Voorbeeld: een sleutel maken op een koppeling {#example-5}

In dit voorbeeld maken we een sleutel op een koppeling (&quot;bedrijf&quot; naar het schema &quot;cus:bedrijf&quot;) met het **xlink** -kenmerk en een veld in de tabel (&quot;email&quot;):

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Het gegenereerde schema:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

De definitie van de naamsleutel &quot;companyEmail&quot; is uitgebreid met de buitenlandse sleutel van de koppeling &quot;bedrijf&quot;. Met deze sleutel wordt een unieke index voor beide velden gegenereerd.

## Meer informatie

Klik op de volgende koppelingen voor meer informatie:

* [Aan de slag met schema&#39;s](about-schema-reference.md)
* [Schemastructuur](schema-structure.md)
* [Databasetoewijzing](database-mapping.md)
* [Sleutelbeheer](database-keys.md)
* [Campaign datamodel](about-data-model.md)
