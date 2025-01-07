---
product: campaign
title: Elementen en kenmerken - kenmerkelement
description: Elementen en kenmerken
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 0%

---

# kenmerkelement {#attribute--element}


## Inhoudsmodel {#content-model}

kenmerk:==help

## Attributen {#attributes}

_operation (string), advanced (boolean), applyIf (string), autoIncrement (boolean), behoortTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), edit (string), enum (string), expr (string), featureDate (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqql ltable (string), target (MNTOKEN), template (string), translateDefault (string), translateExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

## Ouders {#parents}

`<element>`

## Kinderen {#children}

`<help>`

## Beschrijving {#description}

Met `<attribute>` -elementen kunt u een veld in de database definiëren.

## Gebruik en gebruikscontext {#use-and-context-of-use}

`<attribute>` -elementen moeten in een `<element>` -element worden gedeclareerd.

De volgorde waarin `<attribute>` -elementen in een `<srcschema>` worden gedefinieerd, heeft geen invloed op de volgorde waarin velden worden gemaakt in de database. De aanmaakvolgorde is alfabetisch.

## Beschrijving van kenmerk {#attribute-description}

* **_operation (koord)**: bepaalt het type van het schrijven in het gegevensbestand.

  Dit kenmerk wordt vooral gebruikt bij het uitbreiden van out-of-box schema&#39;s.

  Toegankelijke waarden zijn:

   * &quot;none&quot;: verzoening alleen. Dit betekent dat Adobe Campaign het element zal herstellen zonder het bij te werken of een fout te genereren als het niet bestaat.
   * &quot;insertOrUpdate&quot;: update met invoeging. Dit betekent dat Adobe Campaign het element bijwerkt of maakt als het niet bestaat.
   * &quot;insert&quot;: invoeging. Dit betekent dat Adobe Campaign het element invoegt zonder te controleren of het bestaat.
   * &quot;update&quot;: update. Dit betekent dat Adobe Campaign het element zal bijwerken of een fout zal produceren als het niet bestaat.
   * &quot;delete&quot;: schrapping. Dit betekent dat Adobe Campaign elementen herstelt en verwijdert.

* **geavanceerd (boolean)**: wanneer deze optie (@advanced= &quot;waar&quot;) wordt geactiveerd, laat het u de attributen op de lijst van beschikbare gebieden verbergen toegankelijk voor het vormen van een lijst in een vorm.
* **applyIf (koord)**: dit attribuut laat u gebieden facultatief maken. Het element `<attribute>` wordt in aanmerking genomen bij het bijwerken van de database wanneer aan de beperking wordt voldaan. &quot;applyIf&quot; ontvangt een XTK-expressie.
* **autoIncrement (boolean)**: als deze optie wordt geactiveerd, wordt het gebied een teller. Hierdoor kunt u een waarde verhogen (meestal id&#39;s). (extern gebruik)
* **behoortTo (koord)**: neemt de naam en namespace van de lijst die het gebied deelt, en bevolkt het schema waar de attributen worden verklaard. (Wordt alleen gebruikt in een `<schema>` ).
* **dataPolicy (koord)**: laat u toe om goedkeuringsbeperkingen op waarden te specificeren die op het SQL of gebied van XML worden toegestaan. De waarden voor dit kenmerk zijn:

   * &quot;none&quot;: geen waarde
   * &quot;smartCase&quot;: hoofdletters van eerste letters
   * &quot;lowerCase&quot;: alle kleine letters
   * &quot;upperCase&quot;: alle hoofdletters
   * &quot;email&quot;: e-mailadres
   * &quot;Telefoon&quot;: telefoonnummer
   * &quot;id&quot;: id-naam
   * &quot;resIdentifier&quot;: bestandsnaam

* **dbEnum (koord)**: ontvangt de interne naam van een &quot;gesloten&quot;opsomming. De opsommingswaarden moeten in `<srcschema>` worden gedefinieerd.
* **defOnDuplicate (boolean)**: als dit attribuut wordt geactiveerd, wanneer een verslag wordt gedupliceerd wordt de standaardwaarde (die in @default wordt bepaald) automatisch opnieuw toegepast op het verslag.
* **gebrek (koord)**: laat u de waarde van het standaardgebied (vraag aan een functie, standaardwaarde) bepalen. Dit kenmerk ontvangt een XTK-expressie.
* **desc (koord)**: laat u een beschrijving van de attributen opnemen. Deze beschrijving wordt gebruikt om te begrijpen wat het element is en waarvoor het wordt gebruikt. U kunt het in het formulier weergeven.
* **geef (koord) uit**: dit attribuut specificeert het type van input die in de vorm verbonden aan het schema zal worden gebruikt.
* **opsomming (koord)**: ontvangt de naam van de opsomming verbonden aan het gebied. De opsomming kan in het zelfde schema of in een ver schema worden opgenomen.
* **expr (koord)**: bepaalt een uitdrukking van de gebiedsuitrekking. Dit kenmerk ontvangt een Xpath- of een XTK-expressie.
* **eigenschap (koord)**: bepaalt een kenmerkengebied: Deze gebieden worden gebruikt voor het uitbreiden van de gegevens in een bestaande lijst, maar met opslag in een bijlage lijst. Accepteerde waarden zijn:

   * &quot;shared&quot;: de inhoud wordt opgeslagen in een gedeelde tabel per gegevenstype
   * &quot;toegewezen&quot;: de inhoud wordt opgeslagen in een speciale tabel

  SQL-kenmerktabellen worden automatisch gebaseerd op het kenmerktype:

   * toegewezen: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Er zijn twee types van eigenschapgebieden: eenvoudige à <sup> 1 </sup> gebieden waar één enkele waarde op het kenmerk wordt toegelaten, en o <sup> 1 </sup> veelvoudige keuzevelden, waar het kenmerk met een inzamelingselement verbonden is dat verscheidene waarden kan bevatten.

  Wanneer een eigenschap in een schema wordt bepaald, moet dit schema een belangrijkste sleutel hebben die op één enkel gebied wordt gebaseerd (de samengestelde sleutels zijn niet geoorloofd).

* **featureDate (boolean)**: attribuut verbonden aan het &quot;@feature&quot;eigenschapgebied. Als de waarde &quot;true&quot; is, kunt u erachter komen wanneer de waarde voor het laatst is bijgewerkt.
* **img (koord)**: laat u een weg voor een beeld bepalen verbonden aan een gebied (namespace + beeldnaam) (voorbeeld: img=&quot;cus:mypicture.jpg&quot;). De afbeelding moet fysiek naar de toepassingsserver worden geïmporteerd.
* **etiket (koord)**: etiket verbonden aan het gebied, meestal bestemd aan de gebruiker in de interface. Hiermee voorkomt u naamgevingsbeperkingen.
* **lengte (koord)**: max. aantal tekens voor een waarde van het SQL-veld &quot;tekenreeks&quot;. Als het kenmerk &quot;@length&quot; niet is opgegeven, maakt Adobe Campaign automatisch een veld voor 255 tekens.
* **localizable (boolean)**: als het wordt geactiveerd, vertelt dit attribuut het inzamelingshulpmiddel om de waarde van het &quot;@label&quot;attribuut voor vertaling (intern gebruik) terug te krijgen.
* **naam (MNTOKEN)**: naam van de attributen die de naam van het gebied in de lijst zullen aanpassen. De waarde van het kenmerk &quot;@name&quot; moet kort zijn, bij voorkeur in het Engels, en voldoen aan XML-naamgevingsbeperkingen.

  Als het schema naar de database wordt geschreven, worden automatisch voorvoegsels aan de veldnaam toegevoegd door Adobe Campaign:

   * &quot;i&quot;: prefix voor het type &#39;integer&#39;.
   * &quot;d&quot;: prefix voor het type &#39;double&#39;.
   * &quot;s&quot;: voorvoegsel voor het tekenreekstype.
   * &quot;ts&quot;: voorvoegsel voor het type &#39;date&#39;.

  Als u de naam van het veld in de tabel volledig wilt definiëren, gebruikt u de optie &quot;@sqlname&quot; bij het definiëren van een kenmerk.

* **notNull (boolean)**: laat u het gedrag van Adobe Campaign betreffende het beheer van ONGELDIGE verslagen in het gegevensbestand opnieuw bepalen. Numerieke velden zijn standaard niet null en tekenreeks- en datumtekstvelden kunnen null zijn.
* **pkgStatus (koord)**: tijdens pakketuitvoer, worden de waarden in aanmerking genomen afhankelijk van de waarde &quot;@pkgStatus&quot;:

   * &quot;always&quot;: always present
   * &quot;never&quot;: nooit aanwezig
   * &quot;default (or none)&quot;: de waarde wordt geëxporteerd, behalve als dit de standaardwaarde is of als het geen intern veld is dat niet compatibel zou zijn met andere instanties.

* **ref (koord)**: dit attribuut bepaalt een verwijzing naar een `<attribute>` element dat door verscheidene schema&#39;s wordt gedeeld (definitie factoring). De definitie wordt niet gekopieerd naar het huidige schema.
* **vereist (boolean)**: als dit attribuut (@required= &quot;waar&quot;) wordt geactiveerd, wordt het gebied benadrukt in de interface. Het label van het veld wordt rood in formulieren.
* **sql (boolean)**: als dit attribuut (@sql= &quot;waar&quot;) wordt geactiveerd, dwingt het opslag van de SQL attributen, zelfs wanneer het element dat de attributen bevat het xml= &quot;waar&quot;bezit heeft.
* **sqlDefault (koord)**: dit attribuut laat u toe om de standaardwaarde te bepalen die in rekening wordt gebracht voor het bijwerken van het gegevensbestand als het @notNull attribuut wordt geactiveerd. Als dit attribuut na de attributenverwezenlijking wordt toegevoegd, zal het schemagedrag niet veranderen zelfs voor de nieuwe verslagen. Als u het schema wilt wijzigen en de waarde voor nieuwe records wilt bijwerken, moet u het kenmerk verwijderen en opnieuw maken.
* **sqlname (koord)**: van het gebied tijdens lijstverwezenlijking. Als @sqlname niet wordt gespecificeerd, wordt de waarde van het &quot;@name&quot;attribuut gebruikt door gebrek. Wanneer het schema in het gegevensbestand wordt geschreven, worden de prefixen automatisch toegevoegd afhankelijk van het type van gebied.
* **malplaatje (koord)**: dit attribuut bepaalt een verwijzing naar een `<attribute>` element dat door verscheidene schema&#39;s wordt gedeeld. De definitie wordt automatisch gekopieerd naar het huidige schema.
* **translateDefault (koord)**: als een &quot;@default&quot;attribuut wordt gevonden, zal &quot;@translateDefault&quot;u toelaten om een uitdrukking opnieuw te bepalen die in @default wordt bepaald, die door het vertaalhulpmiddel (intern gebruik) moet worden verzameld.
* **translatedExpr (koord)**: als een &quot;@expr&quot;attribuut aanwezig is, laat het &quot;@translateExpr&quot;attribuut u toe om een uitdrukking opnieuw te bepalen die in @expr wordt bepaald, die door het vertaalhulpmiddel (intern gebruik) moet worden verzameld.
* **type (MNTOKEN)**: gebiedstype.

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
   * primaire sleutel
   * kort
   * string
   * tijd
   * timespan
   * uuid

  Als het kenmerk &quot;@type&quot; leeg blijft, koppelt Adobe Campaign standaard een tekenreeks (STRING) met een lengte van 100 aan het veld.

  Als het veld van het type STRING is en de naam van het veld niet wordt opgegeven door de aanwezigheid van het kenmerk &quot;@sqlname&quot;, wordt de naam van het veld in de database automatisch voorafgegaan door een &#39;s&#39;. Deze werkmodus is vergelijkbaar met velden van het type INTEGER (i), DUBBELE (d) en DATES (ts).

* **userEnum (koord)**: ontvangt de interne naam van een &quot;open&quot;opsomming. De waarden van de opsomming kunnen door de gebruiker in de interface worden bepaald.
* **visibleIf (koord)**: bepaalt een voorwaarde in de vorm van een uitdrukking van XTK om de attributen te tonen of te verbergen.

  >[!IMPORTANT]
  >
  >Het kenmerk is verborgen, maar de gegevens ervan zijn toegankelijk.

* **xml (boolean)**: als deze optie wordt geactiveerd, hebben de waarden van het gebied geen verbonden SQL gebied. Adobe Campaign maakt een tekstveld &#39;mData&#39; voor het opslaan van records. Dit betekent dat er op deze velden geen filters of sortering plaatsvindt.

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

Voorbeeld met een kenmerk &quot;@applicableIf&quot;: het kenmerk &quot;contains&quot; wordt alleen gemaakt als het aantal landen groter is dan 20.

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
