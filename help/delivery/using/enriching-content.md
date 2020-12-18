---
solution: Campaign Classic
product: campaign
title: Content verrijken
description: Content verrijken
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---


# Content verrijken{#enriching-content}

Met aggregators kunt u de inhoud verrijken met externe gegevens. Dit gegeven komt uit generische vragen of verbonden lijsten.

## Algemene vragen {#generic-queries}

De vragen worden gevormd via het publicatiesjabloon in **[!UICONTROL Aggregator]** tabel.

De opgehaalde gegevens verrijken het XML-uitvoerdocument via het hoofdelement.

Voorbeeld van terugkeer van een vraag op het ontvankelijke schema (**nms:ontvanger**):

```
<book name="Content Management">
  ...
  <collection-recipient>
    <recipient lastName="Doe" firstName="John" email="john.doe@aolf.com">
    ...
  </collection-recipient>
</book>
```

Het element **`<collection-recipient>`** vertegenwoordigt het inputelement van het document resulterend uit een vraag. De opgehaalde gegevens worden onder dit element geretourneerd. in ons voorbeeld, een ontvankelijke lijst.

### Een query {#adding-a-query} toevoegen

De queryparameters worden bewerkt met een wizard.

1. Geef op de eerste pagina het label en het schema op met de gegevens die moeten worden opgehaald.

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >Het bewerkingsgebied **Weg** wordt gebruikt om het element van de vraagoutput anders te noemen.

1. Op de volgende pagina kunt u de gegevens selecteren die u wilt ophalen.

   ![](assets/d_ncs_content_query2.png)

1. De volgende pagina bepaalt de filtervoorwaarde.

   ![](assets/d_ncs_content_query3.png)

1. Op de laatste pagina wordt een voorvertoning geopend van de gegevens die door de query worden geretourneerd.

   ![](assets/d_ncs_content_query4.png)

## Gekoppelde tabellen {#linked-tables}

Met koppelingen kunt u externe gegevens ophalen die zijn gekoppeld aan de inhoud.

Er zijn twee typen gekoppelde gegevens:

* Koppelingen naar inhoud: dit is de native modus voor inhoudsbeheer. De inhoud van de koppeling wordt automatisch in het XML-uitvoerdocument geïntegreerd.
* Koppelingen naar externe tabellen geven toegang tot alle andere tabellen in de database met als beperking het ophalen van de gegevens van de geselecteerde koppeling met een aggregator.

### Koppelen naar een inhoudsschema {#link-to-a-content-schema}

Een inhoudskoppeling wordt als volgt gedeclareerd in het gegevensschema:

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

De definitie van de koppeling wordt ingevuld in een **tekenreeks**-type **`<element>`** en het **expandSchemaTarget**-attribuut verwijst naar het doelschema (&quot;cus:hoofdstuk&quot; in ons voorbeeld). Het schema waarnaar wordt verwezen, moet een inhoudsschema zijn.

De inhoud van het doelelement verrijkt het koppelingselement, dat wil zeggen het element **`<chapter>`** in ons voorbeeldschema:

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>De **Berekende tekenreeks** van de koppeling wordt weergegeven vanuit het **computeString**-kenmerk.

In het invoerformulier wordt het bewerkingsbeheer van de koppeling als volgt gedeclareerd:

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

Met het pictogram **[!UICONTROL Magnifier]** kunt u het bewerkingsformulier van het gekoppelde element openen.

#### Koppelingsverzameling {#link-collection}

Als u een verzameling koppelingen wilt vullen, voegt u het **unbound=&quot;true&quot;**-kenmerk toe aan de definitie van het koppelingselement in het gegevensschema:

```
<element expandSchemaTarget="cus:chapter" label="List of chapters" name="chapter"  ordered="true" unbound="true"/>
```

De inhoud van het doelelement verrijkt elk verzamelingselement:

```
<chapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</chapter>
```

In het invoerformulier wordt het besturingselement voor de lijst als volgt gedeclareerd:

```
<input editable="false" nolabel="true" toolbarCaption="List of chapters" type="articleList" xpath="chapter" zoom="true"/>
```

![](assets/d_ncs_content_link2.png)

Er wordt een standaardkolom weergegeven om de **Tekenreeks berekenen** van de beoogde elementen weer te geven.

### Koppelingen naar externe tabellen {#links-to-external-tables}

Een koppeling naar een externe tabel wordt als volgt gedeclareerd in het gegevensschema:

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

De definitie van de koppeling wordt ingevuld op een **link**-type **`<element>`** en het **target** attribuut verwijst naar het doelschema (&quot;nms:ontvanger&quot; in ons voorbeeld).

Door overeenkomst, moeten de verbindingen van het belangrijkste element van het gegevensschema worden verklaard.

De **Berekende tekenreeks** en de sleutel van het doelelement verrijken de **`<name>-id`**- en **`<name>-cs`**-kenmerken op het hoofdelement.

In ons voorbeeld wordt de koppeling gevuld in het schema &quot;cus:book&quot;. De inhoud van de koppelingsgegevens bevindt zich in de kenmerken &quot;mainContact-id&quot; en &quot;mainContact-cs&quot;:

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

Besturingselement voor bewerken van koppeling wordt als volgt gedeclareerd:

```
<input xpath="mainContact"/>
```

![](assets/d_ncs_content_link3.png)

U kunt de keuze van doelelementen beperken door het element **`<sysfilter>`** toe te voegen via de koppelingsdefinitie in het invoerformulier:

```
<input xpath="mainContact">
  <!-- Filter the selection of the link on the Adobe domain -->
  <sysFilter>
    <condition expr="@domain =  'adobe.com '"/>
  </sysFilter>
</input>
```

>[!NOTE]
>
>Deze beperking geldt ook voor inhoudskoppelingen.

#### Koppelingsverzameling {#link-collection-1}

De definitie van de verzameling is identiek aan de definitie van een lijst met verzamelingselementen:

```
<element label="List of contacts" name="contact" unbound="true">
  <element label="Recipient" name="recipient" target="nms:recipient" type="link"/>
</element>
```

In het invoerformulier wordt het besturingselement voor de lijst als volgt gedeclareerd:

```
<input nolabel="true" toolbarCaption="List of contacts" type="list" xpath="contact">
  <input xpath="recipient"/>
</input>
```

![](assets/d_ncs_content_link4.png)

>[!NOTE]
>
>De lijst is editable en laat u de verbinding van een &quot;verbinding&quot;hierboven voorgesteld controle selecteren.

De inhoud van het doelelement verrijkt elk verzamelingselement in het uitvoerdocument:

```
<contact id="11504978621" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>
<contact id="11504982510" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/>
```

#### Linkaggregatie {#link-aggregation}

De inhoud van elke verbinding waarnaar wordt verwezen is beperkt tot de interne sleutel en **Berekent koord** van het gerichte element.

Een JavaScript-script wordt gebruikt om de inhoud van de koppelingen te verrijken via SOAP-query&#39;s.

**Voorbeeld**: De naam van de ontvanger toevoegen aan de koppeling &quot;mainContact&quot; en de koppelingen voor de verzameling &quot;contact&quot;:

```
// Update <mainContact> link
var mainContactId = content.@['mainContact-id']
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr={"@id="+mainContactId}/>
      </where>
    </queryDef>)

var recipient = query.ExecuteQuery()
content.mainContact.@lastName = recipient.@lastName

// Update <contact> link collection
for each(var contact in content.contact)
{
  var contactId = contact.@['recipient-id']
  var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr={"@id="+contactId}/>
      </where>
    </queryDef>
  )
  
  var recipient = query.ExecuteQuery()
  contact.@lastName = recipient.@lastName
}
```

Het resultaat dat na de uitvoering van het script wordt bereikt:

```
<mainContact lastName="Doe"/>

<contact id="11504978621" lastName="Doe" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>  
<contact id="11504982510" lastName="Martinez" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/> 
```

De inhoud van de JavaScript-code wordt toegevoegd via de map **[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]** en moet voor elke transformatie worden ingevuld in de publicatiesjabloon.

![](assets/d_ncs_content_link5.png)

