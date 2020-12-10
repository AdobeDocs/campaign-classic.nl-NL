---
solution: Campaign Classic
product: campaign
title: Elementen en kenmerken
description: Elementen en kenmerken
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '1552'
ht-degree: 0%

---


# `<attribute>` element  {#attribute--element}

## Inhoudsmodel {#content-model}

kenmerk:==help

## Kenmerken {#attributes}

_operation (string), advanced (boolean), applyIf (string), autoIncrement (boolean), behoortTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), edit (string), enum (string), expr (string), featureDate (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqql ltable (string), target (MNTOKEN), template (string), translateDefault (string), translateExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

## Ouders {#parents}

`<element>`

## Kinderen {#children}

`<help>`

## Beschrijving {#description}

`<attribute>` Met elementen kunt u een veld in de database definiëren.

## Gebruik en gebruikscontext {#use-and-context-of-use}

`<attribute>` elementen moeten in een  `<element>` element worden gedeclareerd.

De opeenvolging waarin `<attribute>` elementen in `<srcschema>` worden bepaald beïnvloedt niet de opeenvolging van de gebiedsverwezenlijking in het gegevensbestand. De aanmaakvolgorde is alfabetisch.

## Kenmerkbeschrijving {#attribute-description}

* **_operation (string)**: definieert het type schrijven in de database.

   Dit kenmerk wordt vooral gebruikt bij het uitbreiden van out-of-the-box schema&#39;s.

   Toegankelijke waarden zijn:

   * &quot;none&quot;: verzoening alleen. Dit betekent dat Adobe Campaign het element zal herstellen zonder het bij te werken of een fout te genereren als het niet bestaat.
   * &quot;insertOrUpdate&quot;: bijwerken met invoeging. Dit betekent dat Adobe Campaign het element bijwerkt of maakt als het niet bestaat.
   * &quot;invoegen&quot;: invoeging. Dit betekent dat Adobe Campaign het element invoegt zonder te controleren of het bestaat.
   * &quot;update&quot;: bijwerken. Dit betekent dat Adobe Campaign het element zal bijwerken of een fout zal produceren als het niet bestaat.
   * &quot;delete&quot;: verwijderen. Dit betekent dat Adobe Campaign elementen herstelt en verwijdert.

* **geavanceerd (Booleaans)**: als deze optie is geactiveerd (@advanced=&quot;true&quot;), kunt u het kenmerk verbergen in de lijst met beschikbare velden die toegankelijk zijn voor het configureren van een lijst in een formulier.
* **applyIf (string)**: Met dit kenmerk kunt u velden optioneel maken. Het `<attribute>` element zal in aanmerking worden genomen wanneer het bijwerken van het gegevensbestand wanneer de beperking wordt nageleefd. &quot;applyIf&quot; ontvangt een XTK-expressie.
* **autoIncrement (Boolean)**: als deze optie is geactiveerd, wordt het veld een teller. Hierdoor kunt u een waarde verhogen (meestal id&#39;s). (extern gebruik)
* **behoortTo (tekenreeks)**: neemt de naam en de naamruimte van de tabel die het veld deelt en vult het schema in waarin het kenmerk wordt gedeclareerd. (alleen gebruikt in een `<schema>`).
* **dataPolicy (tekenreeks)**: kunt u goedkeuringsbeperkingen opgeven voor waarden die zijn toegestaan in het SQL- of XML-veld. De waarden voor dit kenmerk zijn:

   * &quot;none&quot;: geen waarde
   * &quot;smartCase&quot;: eerste letters hoofdletters
   * &quot;lowerCase&quot;: alle kleine letters
   * &quot;upperCase&quot;: Alles in hoofdletters
   * &quot;email&quot;: e-mailadres
   * &quot;Telefoon&quot;: telefoonnummer
   * &quot;identificatiecode&quot;: id-naam
   * &quot;resIdentifier&quot;: bestandsnaam

* **dbEnum (tekenreeks)**: ontvangt de interne naam van een &quot;gesloten&quot;opsomming. De opsommingswaarden moeten in `<srcschema>` worden bepaald.
* **defOnDuplicate (boolean)**: Als dit kenmerk wordt geactiveerd, wordt de standaardwaarde (gedefinieerd in @default) automatisch opnieuw toegepast op de record wanneer een record wordt gedupliceerd.
* **default (string)**: Hiermee kunt u de waarde van het standaardveld definiëren (aanroepen van een functie, standaardwaarde). Dit kenmerk ontvangt een XTK-expressie.
* **desc (tekenreeks)**: Hiermee kunt u een beschrijving van het kenmerk invoegen. Deze beschrijving wordt getoond in de statusbar van de interface.
* **bewerken (tekenreeks)**: This attribute specifies the type of input which will be used in the form linked to the schema.
* **enum (tekenreeks)**: ontvangt de naam van de opsomming die aan het veld is gekoppeld. De opsomming kan in het zelfde schema of in een ver schema worden opgenomen.
* **expr (tekenreeks)**: definieert een expressie voor veldprecalculatie. Dit kenmerk ontvangt een Xpath- of een XTK-expressie.
* **feature (tekenreeks)**: definieert een kenmerkveld: Deze velden worden gebruikt voor het uitbreiden van de gegevens in een bestaande tabel, maar met opslag in een bijlage-tabel. Accepteerde waarden zijn:

   * &quot;shared&quot;: de inhoud wordt opgeslagen in een gedeelde tabel per gegevenstype
   * &quot;toegewezen&quot;: de inhoud wordt opgeslagen in een speciale tabel

   SQL-kenmerktabellen worden automatisch gebaseerd op het kenmerktype:

   * toegewezen: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * gedeeld: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Er zijn twee typen kenmerkvelden: eenvoudige oà¹-velden, waar één enkele waarde is toegestaan op de karakteristieken, en o à¹ multiple choice velden, waar de eigenschap is gekoppeld aan een collectie element dat meerdere waarden kan bevatten.

   Wanneer een kenmerk in een schema wordt bepaald, moet dit schema een hoofdsleutel hebben die op één enkel gebied wordt gebaseerd (de samengestelde sleutels zijn niet geoorloofd).

* **featureDate (boolean)**: kenmerk gekoppeld aan het veld &quot;@feature&quot;-kenmerken. Als de waarde &quot;true&quot; is, kunt u erachter komen wanneer de waarde voor het laatst is bijgewerkt.
* **img (tekenreeks)**: Hiermee kunt u een pad definiëren voor een afbeelding die is gekoppeld aan een veld (naamruimte + naam van afbeelding) (bijvoorbeeld: img=&quot;cus:mypicture.jpg&quot;). De afbeelding moet fysiek naar de toepassingsserver worden geïmporteerd.
* **label (tekenreeks)**: label gekoppeld aan het veld, meestal bestemd voor de gebruiker in de interface. Hiermee voorkomt u naamgevingsbeperkingen.
* **length (tekenreeks)**: max. aantal tekens voor een waarde van het SQL-veld &quot;tekenreeks&quot;. Als het kenmerk &quot;@length&quot; niet is opgegeven, maakt Adobe Campaign automatisch een veld voor 255 tekens.
* **localizable (boolean)**: Als dit kenmerk is geactiveerd, geeft dit het gereedschap Verzameling de opdracht om de waarde van het kenmerk &quot;@label&quot; te herstellen voor vertaling (intern gebruik).
* **naam (MNTOKEN)**: naam van het kenmerk dat overeenkomt met de naam van het veld in de tabel. De waarde van het kenmerk &quot;@name&quot; moet kort zijn, bij voorkeur in het Engels, en voldoen aan XML-naamgevingsbeperkingen.

   Als het schema naar de database wordt geschreven, worden automatisch voorvoegsels aan de veldnaam toegevoegd door Adobe Campaign:

   * &quot;i&quot;: voor het type &#39;integer&#39;.
   * &quot;d&quot;: prefix voor het type &#39;double&#39;.
   * &quot;s&quot;: voorvoegsel voor het tekenreekstype.
   * &quot;ts&quot;: voorvoegsel voor het type &#39;date&#39;.

   Als u de naam van het veld in de tabel volledig wilt definiëren, gebruikt u de optie &quot;@sqlname&quot; bij het definiëren van een kenmerk.

* **notNull (boolean)**: Hiermee kunt u het Adobe Campaign-gedrag voor het beheer van NULL-records in de database opnieuw definiëren. Numerieke velden zijn standaard niet null en tekenreeks- en datumtekstvelden kunnen null zijn.
* **pkgStatus (tekenreeks)**: tijdens het exporteren van pakketten worden waarden in aanmerking genomen, afhankelijk van de waarde van &quot;@pkgStatus&quot;:

   * &quot;always&quot;: altijd aanwezig
   * &quot;never&quot;: nooit
   * &quot;default (or none)&quot;: de waarde wordt uitgevoerd behalve als het de standaardwaarde is of als het geen intern gebied is dat niet met andere instanties compatibel zou zijn.

* **ref (tekenreeks)**: this attribute define a reference to an  `<attribute>` element shared by various schema&#39;s (definition factoring). De definitie wordt niet gekopieerd naar het huidige schema.
* **vereist (Booleaans)**: als dit kenmerk is geactiveerd (@required=&quot;true&quot;), wordt het veld gemarkeerd in de interface. Het label van het veld wordt rood in formulieren.
* **sql (Boolean)**: als dit kenmerk wordt geactiveerd (@sql=&quot;true&quot;), wordt de opslag van het SQL-kenmerk afgedwongen, zelfs als het element dat het kenmerk bevat de eigenschap xml=&quot;true&quot; heeft.
* **sqlDefault (tekenreeks)**: Met dit kenmerk kunt u de standaardwaarde definiëren waarmee rekening wordt gehouden bij het bijwerken van de database als het kenmerk @notNull is geactiveerd. Als dit attribuut na de attributenverwezenlijking wordt toegevoegd, zal het schemagedrag niet veranderen zelfs voor de nieuwe verslagen. Als u het schema wilt wijzigen en de waarde voor nieuwe records wilt bijwerken, moet u het kenmerk verwijderen en opnieuw maken.
* **sqlname (tekenreeks)**: van het veld tijdens het maken van de tabel. Als @sqlname niet wordt gespecificeerd, wordt de waarde van het &quot;@name&quot;attribuut gebruikt door gebrek. Wanneer het schema in het gegevensbestand wordt geschreven, worden de prefixen automatisch toegevoegd afhankelijk van het type van gebied.
* **sjabloon (tekenreeks)**: this attribute define a reference to an  `<attribute>` element shared by various schema&#39;s. De definitie wordt automatisch gekopieerd naar het huidige schema.
* **translateDefault (tekenreeks)**: Als een kenmerk &quot;@default&quot; wordt gevonden, kunt u met het kenmerk &quot;@translateDefault&quot; een expressie opnieuw definiëren die overeenkomt met de expressie die in @default is gedefinieerd, en die worden verzameld met het gereedschap Vertalen (intern gebruik).
* **translateExpr (tekenreeks)**: Als er een kenmerk &quot;@expr&quot; aanwezig is, kunt u met het kenmerk &quot;@translateExpr&quot; een expressie opnieuw definiëren die overeenkomt met de expressie die is gedefinieerd in @expr, die moet worden verzameld met het gereedschap Vertalen (intern gebruik).
* **type (MNTOKEN)**: veldtype.

   Veldtypen zijn algemeen. Afhankelijk van het type database dat is geïnstalleerd, wijzigt Adobe Campaign het gedefinieerde type in een waarde die specifiek is voor de database die tijdens de structuurupdate is geïnstalleerd.

   Lijst met beschikbare typen:

   * ALLE
   * bin
   * opblazen
   * boolean
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * double
   * enum
   * zweven
   * html
   * int64
   * link
   * lang
   * memo
   * MNTOKEN
   * procent
   * primarykey
   * kort
   * string
   * tijd
   * timespan
   * uuid

   Als het kenmerk &quot;@type&quot; leeg blijft, koppelt Adobe Campaign standaard een tekenreeks (STRING) met een lengte van 100 aan het veld.

   Als het veld van het type STRING is en de naam van het veld niet wordt opgegeven door de aanwezigheid van het kenmerk &quot;@sqlname&quot;, wordt de naam van het veld in de database automatisch voorafgegaan door een &#39;s&#39;. Deze werkmodus is vergelijkbaar met velden van het type INTEGER (i), DUBBELE (d) en DATES (ts).

* **userEnum (tekenreeks)**: ontvangt de interne naam van een &quot;open&quot; opsomming. De waarden van de opsomming kunnen door de gebruiker in de interface worden bepaald.
* **visibleIf (string)**: Hiermee definieert u een voorwaarde in de vorm van een XTK-expressie om het kenmerk weer te geven of te verbergen.

   >[!IMPORTANT]
   >
   >Het kenmerk is verborgen, maar de gegevens ervan zijn toegankelijk.

* **xml (Boolean)**: als deze optie is geactiveerd, hebben de waarden van het veld geen gekoppeld SQL-veld. Adobe Campaign maakt een tekstveld &#39;mData&#39; voor het opslaan van records. Dit betekent dat er op deze velden geen filters of sortering plaatsvindt.

### Voorbeelden {#examples}

Voorbeeld van opsommingswaarden waarvan de waarden in de database worden opgeslagen:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

Declaratie van een XML-veld met &quot;@datapoPolicy&quot;:

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

Voorbeeld met &quot;@applicableIf&quot;: het kenmerk &quot;contains&quot; wordt alleen gecreëerd als het aantal landen groter is dan 20.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

Voorbeeld met &quot;@feature&quot; van het type &quot;shared&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

Voorbeeld met &quot;@feature&quot; van het type &quot;toegewezen&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
