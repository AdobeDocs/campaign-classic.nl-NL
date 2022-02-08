---
product: campaign
title: Elementen en kenmerken
description: indexelement
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 1%

---

# indexelement {#dbindex--element}

![](../../../assets/v7-only.svg)

## Inhoudsmodel {#content-model-3}

index:==keyfield

## Attributen {#attributes-3}

* @_operation (tekenreeks)
* @applicableIf (tekenreeks)
* @label (tekenreeks)
* @name (MNTOKEN)
* @unique (boolean)

## Ouders {#parents-3}

`<element>`

## Kinderen {#children-3}

`<keyfield>`

## Beschrijving {#description-3}

Met dit element kunt u een index definiëren die is gekoppeld aan een tabel.

## Gebruik en gebruikscontext {#use-and-context-of-use-3}

Het is mogelijk om verscheidene indexen te bepalen. Een index kan verwijzen naar een of meer velden in de tabel. De indexverklaring volgt gewoonlijk de definitie van het belangrijkste schemaelement.

De volgorde van de `<keyfield>` elementen gedefinieerd in a `<dbindex>` is zeer belangrijk. De eerste `<keyfield>` moet het indexeringscriterium zijn waarop de vragen hoofdzakelijk zijn gebaseerd.

De naam van de index in de database wordt berekend door de naam van de tabel en de naam van de index samen te voegen. Bijvoorbeeld: Tabelnaam &quot;Voorbeeld&quot;, Namespace &quot;Cus&quot;, indexnaam &quot;MyIndex&quot;-> naam van het indexveld tijdens het opvragen van indexitems: &quot;CusSample_myIndex&quot;.

## Beschrijving van kenmerk {#attribute-description-3}

* **_operation (string)**: definieert het type schrijven in de database.

   Dit kenmerk wordt vooral gebruikt bij het uitbreiden van out-of-the-box schema&#39;s.

   Toegankelijke waarden zijn:

   * &quot;none&quot;: verzoening alleen. Dit betekent dat Adobe Campaign het element zal herstellen zonder het bij te werken of een fout te genereren als het niet bestaat.
   * &quot;insertOrUpdate&quot;: bijwerken met invoeging. Dit betekent dat Adobe Campaign het element bijwerkt of maakt als het niet bestaat.
   * &quot;invoegen&quot;: invoeging. Dit betekent dat Adobe Campaign het element invoegt zonder te controleren of het bestaat.
   * &quot;update&quot;: bijwerken. Dit betekent dat Adobe Campaign het element zal bijwerken of een fout zal produceren als het niet bestaat.
   * &quot;delete&quot;: verwijderen. Dit betekent dat Adobe Campaign elementen herstelt en verwijdert.

* **applyIf (string)**: voorwaarde voor het in aanmerking nemen van de index - ontvangt een uitdrukking XTK.
* **label (tekenreeks)**: indexlabel.
* **naam (MNTOKEN)**: unieke indexnaam.
* **unique (boolean)**: als deze optie is geactiveerd (@unique=&quot;true&quot;), garandeert het kenmerk de unieke kwaliteit van de index in alle velden.

## Voorbeelden {#examples-3}

Creation of an index on the &quot;id&quot; field. (het kenmerk &quot;@unique&quot; op het tabblad `<dbindex>` element brengt het toevoegen van het sleutelwoord &quot;UNIQUE&quot;SQL teweeg wanneer de index in het gegevensbestand (vraag) wordt gecreeerd.

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

Een samengestelde index maken op de velden &quot;@mail&quot; en &quot;@phoneNumber&quot;:

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```
