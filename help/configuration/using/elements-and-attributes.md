---
title: Elementen en kenmerken
seo-title: Elementen en kenmerken
description: Elementen en kenmerken
seo-description: null
page-status-flag: never-activated
uuid: 72b0128a-a453-4646-93e5-b399914abb76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5e24d94a-f9c1-4642-a881-dfc4b5492f14
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Elementen en kenmerken {#elements-and-attributes}

Bij het bewerken van een schema is een goedkeuringssysteem op basis van het bronschema (xtk:srcSchema) beschikbaar. Sommige fouten kunnen ook worden ontdekt wanneer het bijwerken van het gegevensbestand gebruikend de &quot;update van de structuur van het Gegevensbestand...&quot; wizard.

Standaard zijn in Adobe Campagne-schema&#39;s alle kenmerken van het type Boolean &#39;false&#39;. Om hen te activeren, moet u de attributen in het schema specificeren en zijn waarde plaatsen aan &quot;waar&quot;.

## `<attribute>` element {#attribute--element}

### Inhoudsmodel {#content-model}

kenmerk:==help

### Attributen {#attributes}

_operation (string), advanced (boolean), applyIf (string), autoIncrement (boolean), behoortTo (string), dataPolicy (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), edit (string), enum (string), expr (string), featureDate (boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqql ltable (string), target (MNTOKEN), template (string), translateDefault (string), translateExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

### Ouders {#parents}

`<element>`

### Kinderen {#children}

`<help>`

### Beschrijving {#description}

`<attribute>` Met elementen kunt u een veld in de database definiëren.

### Gebruik en gebruikscontext {#use-and-context-of-use}

`<attribute>` elementen moeten in een `<element>` element worden gedeclareerd.

De volgorde waarin `<attribute>` elementen in een database worden gedefinieerd, heeft `<srcschema>` geen invloed op de reeks voor het maken van velden in de database. De aanmaakvolgorde is alfabetisch.

### Beschrijving van kenmerk {#attribute-description}

* **_operation (string)**: definieert het type schrijven in de database.

   Dit kenmerk wordt vooral gebruikt bij het uitbreiden van out-of-the-box schema&#39;s.

   Toegankelijke waarden zijn:

   * &quot;none&quot;: verzoening alleen. Dit betekent dat het element wordt hersteld zonder het bij te werken of een fout te genereren als het niet bestaat.
   * &quot;insertOrUpdate&quot;: bijwerken met invoeging. Dit betekent dat Adobe Campaign het element bijwerkt of maakt als het niet bestaat.
   * &quot;invoegen&quot;: invoeging. Dit betekent dat Adobe Campaign het element invoegt zonder te controleren of het bestaat.
   * &quot;update&quot;: bijwerken. Dit betekent dat Adobe Campagne het element zal bijwerken of een fout zal produceren als het niet bestaat.
   * &quot;delete&quot;: verwijderen. Dit betekent dat in Adobe Campaign elementen worden hersteld en verwijderd.

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

* **dbEnum (tekenreeks)**: ontvangt de interne naam van een &quot;gesloten&quot;opsomming. De opsommingswaarden moeten in de `<srcschema>`code worden gedefinieerd.
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
* **length (tekenreeks)**: max. aantal tekens voor een waarde van het SQL-veld &quot;tekenreeks&quot;. Als het kenmerk &quot;@length&quot; niet is opgegeven, maakt Adobe Campagne automatisch een veld voor 255 tekens.
* **localizable (boolean)**: Als dit kenmerk is geactiveerd, geeft dit het gereedschap Verzameling de opdracht om de waarde van het kenmerk &quot;@label&quot; te herstellen voor vertaling (intern gebruik).
* **naam (MNTOKEN)**: naam van het kenmerk dat overeenkomt met de naam van het veld in de tabel. De waarde van het kenmerk &quot;@name&quot; moet kort zijn, bij voorkeur in het Engels, en voldoen aan XML-naamgevingsbeperkingen.

   Wanneer het schema naar de database wordt geschreven, worden automatisch voorvoegsels aan de veldnaam toegevoegd door Adobe Campaign:

   * &quot;i&quot;: voor het type &#39;integer&#39;.
   * &quot;d&quot;: prefix voor het type &#39;double&#39;.
   * &quot;s&quot;: voorvoegsel voor het tekenreekstype.
   * &quot;ts&quot;: voorvoegsel voor het type &#39;date&#39;.
   Als u de naam van het veld in de tabel volledig wilt definiëren, gebruikt u de optie &quot;@sqlname&quot; bij het definiëren van een kenmerk.

* **notNull (boolean)**: Hiermee kunt u het gedrag van Adobe Campaign opnieuw definiëren met betrekking tot het beheer van NULL-records in de database. Numerieke velden zijn standaard niet null en tekenreeks- en datumtekstvelden kunnen null zijn.
* **pkgStatus (tekenreeks)**: tijdens het exporteren van pakketten worden waarden in aanmerking genomen, afhankelijk van de waarde van &quot;@pkgStatus&quot;:

   * &quot;always&quot;: altijd aanwezig
   * &quot;never&quot;: nooit
   * &quot;default (or none)&quot;: de waarde wordt uitgevoerd behalve als het de standaardwaarde is of als het geen intern gebied is dat niet met andere instanties compatibel zou zijn.

* **ref (tekenreeks)**: this attribute define a reference to an `<attribute>` element shared by various schema&#39;s (definition factoring). De definitie wordt niet gekopieerd naar het huidige schema.
* **vereist (Booleaans)**: als dit kenmerk is geactiveerd (@required=&quot;true&quot;), wordt het veld gemarkeerd in de interface. Het label van het veld wordt rood in formulieren.
* **sql (Boolean)**: als dit kenmerk wordt geactiveerd (@sql=&quot;true&quot;), wordt de opslag van het SQL-kenmerk afgedwongen, zelfs als het element dat het kenmerk bevat de eigenschap xml=&quot;true&quot; heeft.
* **sqlDefault (tekenreeks)**: Met dit kenmerk kunt u de standaardwaarde definiëren waarmee rekening wordt gehouden bij het bijwerken van de database als het kenmerk @notNull is geactiveerd. Als dit attribuut na de attributenverwezenlijking wordt toegevoegd, zal het schemagedrag niet veranderen zelfs voor de nieuwe verslagen. Als u het schema wilt wijzigen en de waarde voor nieuwe records wilt bijwerken, moet u het kenmerk verwijderen en opnieuw maken.
* **sqlname (tekenreeks)**: van het veld tijdens het maken van de tabel. Als @sqlname niet wordt gespecificeerd, wordt de waarde van het &quot;@name&quot;attribuut gebruikt door gebrek. Wanneer het schema in het gegevensbestand wordt geschreven, worden de prefixen automatisch toegevoegd afhankelijk van het type van gebied.
* **sjabloon (tekenreeks)**: dit attribuut bepaalt een verwijzing naar een `<attribute>` element dat door verscheidene schema&#39;s wordt gedeeld. De definitie wordt automatisch gekopieerd naar het huidige schema.
* **translateDefault (tekenreeks)**: Als een kenmerk &quot;@default&quot; wordt gevonden, kunt u met het kenmerk &quot;@translateDefault&quot; een expressie opnieuw definiëren die overeenkomt met de expressie die is gedefinieerd in @default, die moet worden verzameld met het gereedschap Vertalen (intern gebruik).
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
   *  string
   * tijd
   * timespan
   * uuid
   Als het kenmerk &quot;@type&quot; leeg blijft, koppelt Adobe Campagne standaard een tekenreeks (STRING) met een lengte van 100 naar het veld.

   Als het veld van het type STRING is en de naam van het veld niet wordt opgegeven door de aanwezigheid van het kenmerk &quot;@sqlname&quot;, wordt de naam van het veld in de database automatisch voorafgegaan door een &#39;s&#39;. Deze werkmodus is vergelijkbaar met velden van het type INTEGER (i), DUBBELE (d) en DATES (ts).

* **userEnum (tekenreeks)**: ontvangt de interne naam van een &quot;open&quot; opsomming. De waarden van de opsomming kunnen door de gebruiker in de interface worden bepaald.
* **visibleIf (string)**: Hiermee definieert u een voorwaarde in de vorm van een XTK-expressie om het kenmerk weer te geven of te verbergen.

   >[!IMPORTANT]
   >
   >Het kenmerk is verborgen, maar de gegevens ervan zijn toegankelijk.

* **xml (Boolean)**: als deze optie is geactiveerd, hebben de waarden van het veld geen gekoppeld SQL-veld. Adobe Campaign maakt een tekstveld met de naam &#39;mData&#39; voor het opslaan van records. Dit betekent dat er op deze velden geen filters of sortering plaatsvindt.

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

## `<compute-string>` element {#compute-string--element}

### Inhoudsmodel {#content-model-1}

compute-string:==EMPTY

### Attributen {#attributes-1}

@expr

### Ouders {#parents-1}

`<element>`

### Kinderen {#children-1}

Geen

### Beschrijving {#description-1}

Met het `<compute-string>` element kunt u een tekenreeks genereren op basis van een XTK-expressie om een &#39;gebouwd&#39; label in de interface weer te geven op basis van verschillende waarden.

### Gebruik en gebruikscontext {#use-and-context-of-use-1}

Wanneer geen `<compute-string>` wordt bepaald, is een `<compute-string>` element ingegaan door gebrek met de waarden van de primaire sleutel in het schema.

### Beschrijving van kenmerk {#attribute-description-1}

* **expr (tekenreeks)**: XTK en/of Xpath-expressie

### Voorbeelden {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Resultaat van de tekenreeks berekend op een ontvanger: &quot;Jan Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

## `<condition>` element {#condition--element}

### Inhoudsmodel {#content-model-2}

condition:==EMPTY

### Attributen {#attributes-2}

* @boolOperator (tekenreeks)
* @enabledIf (string)
* @expr (tekenreeks)

### Ouders {#parents-2}

`<sysfilter>`

### Kinderen {#children-2}

Geen

### Beschrijving {#description-2}

Met dit element kunt u een filtervoorwaarde definiëren.

### Gebruik en gebruikscontext {#use-and-context-of-use-2}

Eén `<sysfiler>` element kan verschillende filtervoorwaarden bevatten.

### Beschrijving van kenmerk {#attribute-description-2}

* **boolOperator (tekenreeks)**: als verscheidene binnen het zelfde `<conditions>` `<sysfilter>` element worden bepaald, laat dit attribuut u hen combineren. Standaard is de logische koppeling tussen `<condition>` elementen &quot;AND&quot;. Met het kenmerk &quot;@boolOperator&quot; kunt u koppelingen van het type &quot;OR&quot; en &quot;AND&quot; combineren.
* **enabledIf (string)**: activeringstest voorwaarde.
* **expr (tekenreeks)**: een XTK-expressie.

### Voorbeelden {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```

## `<dbindex>` element {#dbindex--element}

### Inhoudsmodel {#content-model-3}

index:==keyfield

### Attributen {#attributes-3}

* @_operation (tekenreeks)
* @applicableIf (tekenreeks)
* @label (tekenreeks)
* @name (MNTOKEN)
* @unique (boolean)

### Ouders {#parents-3}

`<element>`

### Kinderen {#children-3}

`<keyfield>`

### Beschrijving {#description-3}

Met dit element kunt u een index definiëren die is gekoppeld aan een tabel.

### Gebruik en gebruikscontext {#use-and-context-of-use-3}

Het is mogelijk om verscheidene indexen te bepalen. Een index kan verwijzen naar een of meer velden in de tabel. De indexverklaring volgt gewoonlijk de definitie van het belangrijkste schemaelement.

De volgorde van de `<keyfield>` elementen die in een definitie worden gedefinieerd, `<dbindex>` is erg belangrijk. Het eerste criterium `<keyfield>` moet het indexeringscriterium zijn waarop de vragen hoofdzakelijk zijn gebaseerd.

De naam van de index in de database wordt berekend door de naam van de tabel en de naam van de index samen te voegen. Bijvoorbeeld: Tabelnaam &quot;Voorbeeld&quot;, Namespace &quot;Cus&quot;, indexnaam &quot;MyIndex&quot;-> naam van het indexveld tijdens het opvragen van indexitems: &quot;CusSample_myIndex&quot;.

### Beschrijving van kenmerk {#attribute-description-3}

* **_operation (string)**: definieert het type schrijven in de database.

   Dit kenmerk wordt vooral gebruikt bij het uitbreiden van out-of-the-box schema&#39;s.

   Toegankelijke waarden zijn:

   * &quot;none&quot;: verzoening alleen. Dit betekent dat het element wordt hersteld zonder het bij te werken of een fout te genereren als het niet bestaat.
   * &quot;insertOrUpdate&quot;: bijwerken met invoeging. Dit betekent dat Adobe Campaign het element bijwerkt of maakt als het niet bestaat.
   * &quot;invoegen&quot;: invoeging. Dit betekent dat Adobe Campaign het element invoegt zonder te controleren of het bestaat.
   * &quot;update&quot;: bijwerken. Dit betekent dat Adobe Campagne het element zal bijwerken of een fout zal produceren als het niet bestaat.
   * &quot;delete&quot;: verwijderen. Dit betekent dat in Adobe Campaign elementen worden hersteld en verwijderd.

* **applyIf (string)**: voorwaarde voor het in aanmerking nemen van de index - ontvangt een uitdrukking XTK.
* **label (tekenreeks)**: indexlabel.
* **naam (MNTOKEN)**: unieke indexnaam.
* **uniek (Booleaans)**: als deze optie is geactiveerd (@unique=&quot;true&quot;), garandeert het kenmerk de unieke kwaliteit van de index in alle velden.

### Voorbeelden {#examples-3}

Creation of an index on the &quot;id&quot; field. (Het kenmerk &quot;@unique&quot; op het `<dbindex>` element activeert het toevoegen van het trefwoord &quot;UNIQUE&quot; SQL wanneer de index in de database wordt gemaakt (query).

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

## `<element>` element {#element--element}

### Inhoudsmodel {#content-model-4}

element:==(attribute| compute string| debindex| Standaard| element| Help| Verbinden| Sleutel| sysFilter| vertaaldStandaard)

### Attributen {#attributes-4}

_operation (string), advanced (boolean), aggregaat (string), applyIf (string), automatische schakeling (boolean), behoortTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAsField (boolean) lean), doesNotSupportDiff (boolean), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink (model) string), folderProcess (string), fullLoad (boolean), hiërarchical (boolean), hiërarchicalPath (string), img (string), inout (string), integriteit (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), noDbIndex (boolean), noKey boolean), ordered (boolean), overflowtable (boolean), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (boolean), revCardinality (string), revDesc (string), revExternalJoin (boolean), revIntegrity (string) Label (string), revLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), target (MNTOKEN), template (string), temporaryTable (boolean), translateDefault (string), translateExpr (tekenreeks), type (MNTOKEN), unbound (Boolean), gebruiker (Boolean), userEnum (tekenreeks), visibleIf (tekenreeks), xml (Boolean), xmlChildren (Boolean)

### Ouders {#parents-4}

`<srcschema>`

`<element>`

### Kinderen {#children-4}

* `<attribute>`
* `<compute-string>`
* `<dbindex>`
* `<default>`
* `<element>`
* `<help>`
* `<join>`
* `<key>`
* `<sysfilter>`
* `<translateddefault>`

### Beschrijving {#description-4}

Adobe Campagne bevat vier typen `<element>` elementen:

* Hoofdmap `<element>` : definieert de naam van de SQL-tabel die overeenkomt met het schema.
* Structuur `<element>` : definieert een groep `<element>` of `<attribute>` elementen.
* Koppeling `<element>` : definieert een koppeling. Deze elementen moeten het kenmerk &quot;@type=link&quot; bevatten.
* XML `<element>` : definieert een veld van het teksttype &quot;mData&quot;. Dit element moet het kenmerk &quot;@type=xml&quot; bevatten.

### Beschrijving van kenmerk {#attribute-description-4}

* **_operation (string)**: definieert het type schrijven in de database.

   Dit kenmerk wordt vooral gebruikt bij het uitbreiden van out-of-the-box schema&#39;s.

   Toegankelijke waarden zijn:

   * &quot;none&quot;: verzoening alleen. Dit betekent dat het element wordt hersteld zonder het bij te werken of een fout te genereren als het niet bestaat.
   * &quot;insertOrUpdate&quot;: bijwerken met invoeging. Dit betekent dat Adobe Campaign het element bijwerkt of maakt als het niet bestaat.
   * &quot;invoegen&quot;: invoeging. Dit betekent dat Adobe Campaign het element invoegt zonder te controleren of het bestaat.
   * &quot;update&quot;: bijwerken. Dit betekent dat Adobe Campagne het element zal bijwerken of een fout zal produceren als het niet bestaat.
   * &quot;delete&quot;: verwijderen. Dit betekent dat in Adobe Campaign elementen worden hersteld en verwijderd.

* **geavanceerd (Booleaans)**: als deze optie is geactiveerd (@advanced=&quot;true&quot;), kunt u het kenmerk verbergen in de lijst met beschikbare velden die toegankelijk zijn voor het configureren van een lijst in een formulier.
* **aggregaat (tekenreeks)**: Hiermee kunt u de definitie van een schema kopiëren `<element>` via een ander schema. Dit kenmerk ontvangt een schemadeclaratie in de vorm van een &quot;namespace:name&quot;.
* **applyIf (string)**: voorwaarde voor het toepassen van de index. Dit kenmerk ontvangt een XTK-expressie.
* **Automatisch (Booleaans)**: als deze optie is geactiveerd (automatische controle=&quot;true&quot;), wordt automatisch een unieke sleutel gedefinieerd. Deze optie mag alleen worden gebruikt voor het hoofdelement van het schema. Waarschuwing: Adobe Campaign garandeert alleen dat de gegenereerde sleutel uniek is. Het is niet gegarandeerd dat de hoofdwaarden opeenvolgend en incrementeel zijn.
* **dataPolicy (tekenreeks)**: kunt u goedkeuringsbeperkingen opgeven voor waarden die zijn toegestaan in het SQL-veld. De waarden voor dit kenmerk zijn:

   * &quot;none&quot;: geen waarde
   * &quot;smartCase&quot;: eerste letters hoofdletters
   * &quot;lowerCase&quot;: alle kleine letters
   * &quot;upperCase&quot;: Alles in hoofdletters
   * &quot;email&quot;: e-mailadres
   * &quot;Telefoon&quot;: telefoonnummer
   * &quot;identificatiecode&quot;: id-naam
   * &quot;resIdentifier&quot;: bestandsnaam

* **dbEnum (tekenreeks)**: ontvangt de interne naam van een &quot;gesloten&quot;opsomming. De opsommingswaarden moeten in de `<srcschema>`code worden gedefinieerd.
* **defOnDuplicate (boolean)**: Als dit kenmerk wordt geactiveerd, wordt de standaardwaarde (gedefinieerd in @default) automatisch opnieuw toegepast op de record wanneer een record wordt gedupliceerd.
* **default (string)**: Hiermee kunt u elementgedrag definiëren (aanroepen van een functie, standaardwaarde). Dit kenmerk ontvangt een XTK-expressie.
* **desc (tekenreeks)**: Hiermee kunt u een beschrijving van het element invoegen. Deze beschrijving wordt getoond in de statusbar van de interface.
* **displayAsField (boolean)**: Als dit kenmerk is geactiveerd, `<element>` wordt een koppelingstype weergegeven als een veld in de boomstructuurweergave van de schema&#39;s (&quot;Structuur&quot; tabblad). Op deze manier is het mogelijk om een koppeling weer te geven als een lokaal veld en het gedrag ervan te wijzigen tijdens een query. Wanneer het element wordt gevonden in SELECT van een query, wordt de waarde van het koppelingsdoel gebruikt. Wanneer het element in WAAR van een vraag wordt gevonden, zal de onderliggende sleutel van de verbinding worden gebruikt.
* **bewerken (tekenreeks)**: This attribute specifies the type of input that will be used in the form linked to the schema.
* **enum (tekenreeks)**: ontvangt de naam van de opsomming die aan het veld is gekoppeld. De opsomming kan in het zelfde schema of in een ver schema worden opgenomen.
* **expr (tekenreeks)**: this attribute define a calculate field for which no definition is stored in the table. Het ontvangt een Xpath- of een XTK-expressie (string).
* **externalJoin (boolean)**: extern samenvoegen in een element van het type &quot;link&quot;.
* **feature (tekenreeks)**: definieert een kenmerkveld: Deze velden worden gebruikt voor het uitbreiden van de gegevens in een bestaande tabel, maar met opslag in een bijlage-tabel. Accepteerde waarden zijn:

   * &quot;shared&quot;: de inhoud wordt opgeslagen in een gedeelde tabel per gegevenstype
   * &quot;toegewezen&quot;: de inhoud wordt opgeslagen in een speciale tabel
   SQL-kenmerktabellen worden automatisch gebaseerd op het kenmerktype:

   * toegewezen: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * gedeeld: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   Er zijn twee typen kenmerkvelden: eenvoudige velden waar één waarde is toegestaan op het kenmerk, en meerkeuzevelden, waar het kenmerk is gekoppeld aan een verzamelingselement dat meerdere waarden kan bevatten.

   Wanneer een kenmerk in een schema wordt bepaald, moet dit schema een hoofdsleutel hebben die op één enkel gebied wordt gebaseerd (de samengestelde sleutels zijn niet geoorloofd).

* **featureDate (boolean)**: kenmerk gekoppeld aan het veld &quot;@feature&quot;-kenmerken. Als de waarde &quot;true&quot; is, kunt u erachter komen wanneer de waarde voor het laatst is bijgewerkt.
* **filterPath (tekenreeks)**: this attribute receive an Xpath and lets you define a filter on a field.
* **folderLink (tekenreeks)**: dit kenmerk ontvangt de naam van de koppeling waarmee u de bestanden met entiteiten kunt herstellen.
* **folderModel (tekenreeks)**: Hiermee definieert u het type map waarin de entiteit kan worden opgeslagen. Dit kenmerk wordt alleen gedefinieerd als &quot;@folderLink&quot; aanwezig is.
* **folderProcess (tekenreeks)**: definieert de koppeling waar de instanties van het entiteitmodel worden opgeslagen. Dit kenmerk wordt alleen gedefinieerd als &quot;@folderLink&quot; aanwezig is.
* **fullLoad (boolean)**: dit kenmerk dwingt de weergave van alle records in een tabel tijdens de veldselectie in een formulier.
* **img (tekenreeks)**: ontvangt het pad van een afbeelding die aan een element is gekoppeld. De waarde van dit kenmerk is van het type &quot;namespace:image name&quot;. Bijvoorbeeld: img=&quot;cus:myImage.jpg&quot;. De afbeelding moet fysiek naar de toepassingsserver worden geïmporteerd.
* **integriteit (tekenreeks)**: referentiële integriteit van het voorkomen van de brontabel in de richting van de doeltabel.

   Toegankelijke waarden zijn:

   * &quot;definitie&quot;: Adobe Campaign verwijdert de entiteit niet als ernaar wordt verwezen via de koppeling
   * &quot;normal&quot;: als u de broninstantie verwijdert, worden de sleutels van de koppeling op de doelinstantie geïnitialiseerd (standaardmodus). Bij dit type integriteit worden alle externe toetsen geïnitialiseerd
   * &quot;eigen&quot;: het schrappen van het bronvoorkomen teweegbrengt de schrapping van het doelvoorkomen
   * &quot;kopie&quot;: vergelijkbaar met &quot;eigen&quot; (in geval van verwijdering) of dubbel voorkomen (in geval van duplicatie)
   * &quot;neutraal&quot;: doet niets

* **label (tekenreeks)**: elementlabel.
* **labelSingular (string)**: label (enkelvoudige vorm) van het element dat in sommige delen van de interface wordt gebruikt.
* **length (tekenreeks)**: max. Het aantal tekens dat is geautoriseerd voor een waarde van het SQL-veld voor het type &quot;string&quot;.
* **localizable (boolean)**: Als dit kenmerk is geactiveerd, geeft dit het gereedschap Verzameling de opdracht om de waarde van het kenmerk &quot;@label&quot; te herstellen voor vertaling (intern gebruik).
* **naam (MNTOKEN)**: interne naam van het element dat overeenkomt met de naam van de tabel. De waarde van het kenmerk &quot;@name&quot; moet kort zijn, bij voorkeur in het Engels, en voldoen aan naamgevingsbeperkingen die zijn gekoppeld aan XML.

   Als het schema naar de database wordt geschreven, worden automatisch voorvoegsels aan de veldnaam toegevoegd door Adobe Campaign.

   * &quot;i&quot;: voor het type &#39;integer&#39;.
   * &quot;d&quot;: prefix voor het type &#39;double&#39;.
   * &quot;s&quot;: voorvoegsel voor het tekenreekstype.
   * &quot;ts&quot;: voorvoegsel voor het type &#39;date&#39;.
   Om de naam van de lijst op een autonome manier te bepalen, moet u het &quot;@sqltable&quot;attribuut in de definitie van het belangrijkste schemaelement gebruiken.

* **noDbIndex (boolean)**: Hiermee kunt u opgeven dat het element niet wordt geïndexeerd.
* **ordered (boolean)**: als het kenmerk is geactiveerd (ordered=&quot;true&quot;), behoudt Adobe Campagne de declaratiereeks voor elementen in een XML-verzamelingselement.
* **pkSequence (tekenreeks)**: ontvangt de naam van de opeenvolging die voor het berekenen van een auto-stijgende sleutel moet worden gebruikt. Dit kenmerk mag alleen worden gebruikt als een automatisch incrementele sleutel is gedefinieerd voor het hoofdelement van het schema.
* **pkgStatus (tekenreeks)**: tijdens de uitvoer van pakketten worden waarden in aanmerking genomen als functie van de waarde van deze eigenschap:

   * &quot;always&quot;: het element zal altijd aanwezig zijn
   * &quot;never&quot;: het element zal nooit aanwezig zijn
   * &quot;default (or none)&quot;: het element wordt geëxporteerd tenzij het het standaardelement is of als het geen intern veld is en niet compatibel zou zijn met andere instanties

* **ref (tekenreeks)**: this attribute define a reference to an >element> element shared by various schema&#39;s (definition factoring). De definitie wordt niet gekopieerd naar het huidige schema.
* **vereist (Booleaans)**: als dit kenmerk is geactiveerd (@required=&quot;true&quot;), wordt het veld gemarkeerd in de interface. Het label van het veld wordt rood in formulieren.
* **revAdvanced (boolean)**: als dit kenmerk wordt geactiveerd, geeft dit aan dat de tegenovergestelde koppeling een &quot;geavanceerde&quot; koppeling is.
* **revCardinality (string)**: dit kenmerk definieert de kardinaliteit van een koppeling tussen twee tabellen. Het wordt gebruikt in een &quot;verbinding&quot;type `<element>`.

   Mogelijke waarden zijn:

   * &quot;single&quot;: Eenvoudige koppeling van het type 1-1
   * &quot;niet geconsolideerd&quot;: 1-N de verbinding van de typeinzameling
   Als het kenmerk niet is opgegeven tijdens het maken van koppelingen, is de standaardinstelling 1-N.

* **revDesc (tekenreeks)**: this attribute receive a description linked to the reverse link.
* **revExternalJoin (boolean)**: wanneer geactiveerd, laat dit attribuut u de externe zich aan op de tegenovergestelde verbinding dwingen.
* **revIntegrity (tekenreeks)**: dit attribuut bepaalt de integriteit op het doelschema. Dezelfde waarden als het kenmerk &quot;@integriteit&quot; zijn geautoriseerd. Standaard geeft Adobe Campaign de waarde &quot;normal&quot; aan dit kenmerk.
* **revLabel (tekenreeks)**: label van de tegenovergestelde koppeling.
* **revLink (tekenreeks)**: naam van de tegenovergestelde koppeling. Als de waarde &quot;_NONE_&quot;is, zal geen tegenovergestelde verbinding in het bestemmingsschema worden gecreeerd.
* **revTarget (tekenreeks)**: doel van de tegenovergestelde koppeling.
* **sql (Boolean)**: als dit kenmerk is geactiveerd (@sql=&quot;true&quot;), wordt de opslag van het SQL-element afgedwongen, zelfs als het element de eigenschap xml=&quot;true&quot; heeft.
* **sqlname (tekenreeks)**: naam van het veld tijdens maken van tabel. Als &quot;@sqlname&quot; niet is opgegeven, wordt standaard de waarde van het kenmerk &quot;@name&quot; gebruikt. Bij het schrijven van het schema naar de tabel worden de voorvoegsels automatisch toegevoegd, afhankelijk van het veldtype.
* **sqltable (tekenreeks)**: voor het hoofdelement van het schema, laadt dit attribuut de naam van de SQL lijst die door gebrek wordt geproduceerd. Als &quot;@sqltable&quot; niet wordt gespecificeerd, zal de standaardnaam als dit worden gestructureerd: naamruimte (hoofdletter van eerste letter), gevolgd door de waarde van het SrcSchema &quot;@name&quot;.
* **tableSpace (tekenreeks)**: Met dit kenmerk kunt u een nieuwe gegevensopslagruimte voor een tabel opgeven (geldig op het hoofdniveau `<element>`).
* **tableSpaceIndex (tekenreeks)**: Met dit kenmerk kunt u een nieuwe tabelruimte voor indexopslag voor een tabel opgeven (geldig op het hoofdniveau `<element>`).
* **doel (MNTOKEN)**: ontvangt de naam van het doelschema wanneer u een koppeling tussen tabellen maakt. Dit kenmerk is alleen actief voor elementen van het type &quot;link&quot;.
* **sjabloon (tekenreeks)**: dit attribuut bepaalt een verwijzing naar een `<element>` element dat door verscheidene schema&#39;s wordt gedeeld. De definitie wordt automatisch gekopieerd naar het huidige schema.
* **translateDefault (tekenreeks)**: Als een kenmerk &quot;@default&quot; wordt gevonden, kunt u met het kenmerk &quot;@translateDefault&quot; een expressie opnieuw definiëren die overeenkomt met de expressie die is gedefinieerd in @default, die moet worden verzameld met het gereedschap Vertalen (intern gebruik).
* **translateExpr (tekenreeks)**: Als een kenmerk &quot;@expr&quot; wordt gevonden, kunt u met het kenmerk &quot;@translateExpr&quot; een expressie opnieuw definiëren die overeenkomt met de expressie die is gedefinieerd in &quot;@expr&quot; en die wordt verzameld met het gereedschap Vertalen (intern gebruik).
* **type (MNTOKEN)**: Hiermee definieert u het type gegevens dat in het element wordt opgeslagen.

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
   *  string
   * tijd
   * timespan
   * uuid

* **niet geconsolideerd (Boolean)**: als het attribuut wordt geactiveerd (unbound= &quot;waar&quot;), wordt de verbinding verklaard als inzamelingselement voor een kardinaliteit 1-N.
* **userEnum (tekenreeks)**: ontvangt de interne naam van een &quot;open&quot; opsomming. Opsommingswaarden kunnen door de gebruiker in de interface worden gedefinieerd.
* **xml (Boolean)**: Als deze optie is geactiveerd, worden alle waarden die in het element zijn gedefinieerd, opgeslagen in XML in het veld &#39;mData&#39; van het type TEXT. Dit betekent dat er op deze velden geen filters of sortering zullen plaatsvinden.
* **xmlChildren (boolean)**: de opslagcapaciteit van de strijdkrachten voor elk kind ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`

## `<enumeration>` element {#enumeration--element}

### Inhoudsmodel {#content-model-5}

opsomming:==(help| value)

### Attributen {#attributes-5}

* @basetype (tekenreeks)
* @default (tekenreeks)
* @desc (tekenreeks)
* @label (tekenreeks)
* @name (tekenreeks)
* @template (tekenreeks)

### Ouders {#parents-5}

`<srcschema>`

### Kinderen {#children-5}

* `<help>`
* `<value>`

### Beschrijving {#description-5}

Met dit element kunnen we een waardenopsomming definiëren. Een opsomming behoort tot het schema waarin het wordt bepaald, maar het is toegankelijk via een ander schema.

### Gebruik en gebruikscontext {#use-and-context-of-use-4}

Opsommingen worden gedefinieerd aan het begin van een schema (voordat het hoofdelement wordt gedefinieerd).

### Beschrijving van kenmerk {#attribute-description-5}

* **basetype (tekenreeks)**: type van de waarden die in de opsomming zijn opgeslagen.

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
   * DOMDocument
   * DOMElement
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
   *  string
   * tijd
   * timespan
   * uuid

* **default (string)**: Standaardwaarde. De standaardwaarde kan ook een van de waarden zijn die in de opsomming worden gedefinieerd.
* **desc (tekenreeks)**: opsommingsbeschrijving.
* **label (tekenreeks)**: opsommingslabel.
* **name (string)**: interne naam van de opsomming.
* **sjabloon (tekenreeks)**: dit attribuut bepaalt een verwijzing naar een `<enumeration>` element dat door verscheidene schema&#39;s wordt gedeeld. De definitie wordt automatisch gekopieerd naar het huidige schema.

### Voorbeelden {#examples-4}

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

Definitie van een opsomming met standaardwaarde:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```

## `<help>` element {#help--element}

### Inhoudsmodel {#content-model-6}

help:==EMPTY

### Attributen {#attributes-6}

Geen

### Ouders {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

### Kinderen {#children-6}

Geen

### Beschrijving {#description-6}

Met dit element kunt u een `<element>` of `<attribute>` element beschrijven. Het mag alleen tekst bevatten en wordt opgeslagen in XML in de database.

### Beschrijving van kenmerk {#attribute-description-6}

Dit element heeft geen kenmerken.

### Voorbeelden {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```

## `<join>` element {#join--element}

### Inhoudsmodel {#content-model-7}

join:==EMPTY

### Attributen {#attributes-7}

* @dstFilterExpr (tekenreeks)
* @xpath-dst (tekenreeks)
* @xpath-src (tekenreeks)

### Ouders {#parents-7}

`<element>`

### Kinderen {#children-7}

Geen

### Beschrijving {#description-7}

Hiermee kunt u de velden definiëren waarmee een samenvoeging tussen SQL-tabellen wordt gemaakt.

### Gebruik en gebruikscontext {#use-and-context-of-use-5}

Een `<join>` element kan alleen worden gebruikt als het bovenliggende `<element>` element van het type &#39;link&#39; is. Dit betekent dat het bovenliggende element het kenmerk &quot;@type=link&quot; moet hebben gedeclareerd.

U hoeft de naam en naamruimte van de externe tabel in het `<join>` element niet op te geven. Ze moeten in het bovenliggende element worden opgegeven `<element>`.

Door overeenkomst, worden de verbindingen bepaald aan het eind van het schema.

Als het `<join>` element niet wordt gespecificeerd wanneer het element van het verbindingstype wordt bepaald, zal de verbinding automatisch op de primaire sleutels van beide lijsten worden geplaatst.

### Beschrijving van kenmerk {#attribute-description-7}

* **dstFilterExpr (tekenreeks)**: Met dit kenmerk kunt u het aantal waarden in de externe tabel beperken.
* **xpath-dst (tekenreeks)**: this attribute receive an Xpath (@name attribute of the remote table).
* **xpath-src (tekenreeks)**: this attribute receive an Xpath (@name attribute in the current schema).

### Voorbeelden {#examples-6}

Koppeling tussen het veld E-mail van de huidige tabel en het veld @compagny-id van de externe tabel:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Gefilterde koppeling naar de tabel &quot;cus:Country&quot;, gebaseerd op de inhoud van het veld &quot;@country&quot;, die de waarde &quot;EN&quot; moet bevatten:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```

## `<key>` element {#key--element}

### Inhoudsmodel {#content-model-8}

key:==keyfield

### Attributen {#attributes-8}

* @allowEmptyPart (boolean)
* @applicableIf (tekenreeks)
* @internal (boolean)
* @label (tekenreeks)
* @name (MNTOKEN)
* @noDbIndex (boolean)

### Ouders {#parents-8}

`<element>`

### Kinderen {#children-8}

`<keyfield>`

### Beschrijving {#description-8}

Met dit element kunt u een sleutel definiëren voor het identificeren van een record in de tabel.

Een tabel moet minstens één sleutel hebben.

### Gebruik en gebruikscontext {#use-and-context-of-use-6}

Normaliter worden toetsen gedeclareerd na het hoofdelement van het schema en de indexen.

Een sleutel wordt een samengestelde sleutel genoemd als het verscheidene gebieden (d.w.z. verscheidene `<keyfield>` kinderen) omvat. Gebruik geen samengestelde sleutel om een primaire sleutel te definiëren.

Als het hoofdelement van het schema het kenmerk &quot;@autopk=true&quot; bevat, is de primaire sleutel uniek. We kunnen slechts één primaire sleutel per schema hebben.

De eerste 1000 id&#39;s zijn gereserveerd, dus als een reeks waarden moet worden gedefinieerd voor toetsen, begint u bij 1000.

### Beschrijving van kenmerk {#attribute-description-8}

* **allowEmptyPart (boolean)**: in het geval van een samengestelde sleutel, als dit attribuut wordt geactiveerd, wordt zij als geldig beschouwd als minstens één van zijn sleutels niet leeg is. Als dit het geval is, is de lege nodewaarde &quot;0&quot;(boolean of voor alle soorten numerieke gegevens). Standaard moeten alle toetsen waaruit een samengestelde sleutel bestaat, worden ingevoerd.
* **applyIf (string)**: Met dit kenmerk kunt u de sleutel optioneel maken. In deze code wordt de voorwaarde gedefinieerd op basis waarvan de sleuteldefinitie wordt toegepast. Dit kenmerk ontvangt een XTK-expressie.
* **internal (boolean)**: als dit kenmerk is geactiveerd, laat Adobe Campaign weten dat de sleutel primair is.
* **label (tekenreeks)**: label van de toets.
* **naam (MNTOKEN)**: interne naam van de sleutel.
* **noDbIndex (boolean)**: als deze is geactiveerd (noDbIndex=&quot;true&quot;), wordt het veld dat overeenkomt met de sleutel niet geïndexeerd.

### Voorbeelden {#examples-------}

Verklaring van een samengestelde sleutel die het veld &quot;@expr&quot; of &quot;alias&quot; leeg maakt:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Verklaring van een primaire sleutel op het gebied van de &quot;Naam&quot;van type STRING in een `<srcschema>` en de overeenkomstige SQL vraag:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

## `<keyfield>` element {#keyfield--element}

### Inhoudsmodel {#content-model-9}

keyfield:==EMPTY

### Attributen {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

### Ouders {#parents-9}

`<key>`  ,  `<dbindex />`

### Kinderen {#children-9}

Geen

### Beschrijving {#description-9}

Dit element definieert de velden die moeten worden geïntegreerd in een index of een sleutel.

### Beschrijving van kenmerk {#attribute-description-9}

* **xlink (MNTOKEN)**: Hiermee kunt u automatisch verwijzen naar externe sleutels die zijn gedefinieerd in de samenvoeging voor een relatietabel (N-N koppeling).
* **xpath (MNTOKEN)**: definitie van een index of een sleutel op een `<attribute>` element. Dit kenmerk ontvangt een Xpath dat het pad naar het schemakenmerk definieert dat de sleutel of de index definieert.

### Voorbeelden {#examples-}

Selectie van het veld &#39;sName&#39; in een index met een Xpath-bewerking voor &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```

## `<method>` element {#method--element}

### Inhoudsmodel {#content-model-10}

methode:==( help:| Parameters)

### Attributen {#attributes-10}

* @_operation (tekenreeks)
* @access (tekenreeks)
* @const (Boolean)
* @hidden (boolean)
* @label (tekenreeks)
* @library (tekenreeks)
* @name (MNTOKEN)
* @pkonly (boolean)
* @static (boolean)

### Ouders {#parents-10}

`<methods>`  ,  `<interface />`

### Kinderen {#children-10}

* `<help>`
* `<parameters>`

### Beschrijving {#description-10}

Met dit element kunt u een SOAP-methode definiëren.

### Gebruik en gebruikscontext {#use-and-context-of-use-7}

SOAP-methoden maken toepassingsprocessen mogelijk.

De &quot;@bibliotheek&quot; is nodig voor het declareren van een nieuwe methode (niet-native): de naamruimte en de naam die voor de bibliotheek worden gebruikt, zijn onafhankelijk van de naamruimte en naam van het schema waarin de declaratie zich bevindt.

### Beschrijving van kenmerk {#attribute-description-10}

* **toegang (tekenreeks)**: this attribute define access control for using the method. Als dit kenmerk ontbreekt, is identificatie verplicht. Beschikbare waarden zijn: &#39;anoniem&#39;, &#39;admin&#39; en &#39;sql&#39;.
* **const (Boolean)**: als deze eigenschap is geactiveerd, betekent dit dat de gedeclareerde methode de entiteit wijzigt
* **label (tekenreeks)**: label van de methode.
* **bibliotheek (tekenreeks)**: deze methode is niet native voor de toepassing. Dit kenmerk neemt de waarde van de methodebibliotheek waar de methodedefinitie is gevonden (nms:mylibrary.js).
* **naam (MNTOKEN)**: unieke methodenaam.
* **static (boolean)**: als dit attribuut wordt geactiveerd, wordt de methode beschouwd als autonoom, moeten alle parameters aan de methode worden gespecificeerd wanneer het omhoog wordt geroepen.

### Voorbeelden {#examples-7}

Definitie van de methode &quot;Abonneren&quot; in het tekstvak:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```

## `<methods>` element {#methods--element}

### Inhoudsmodel {#content-model-11}

methoden:==method

### Attributen {#attributes-11}

Geen

### Ouders {#parents-11}

`<srcschema>`

### Kinderen {#children-11}

methode

### Beschrijving {#description-11}

Met dit element kunt u een `<method>` element definiëren. Het is verplicht een methode te declareren.

### Beschrijving van kenmerk {#attribute-description-11}

Dit element heeft geen kenmerken.

### Voorbeelden {#examples-8}

```
<methods async="true"
...// definition of one or more <method
</methods>
```

## `<param>` element {#param--element}

### Inhoudsmodel {#content-model-12}

param:==help

### Attributen {#attributes-12}

* @_operation (tekenreeks)
* @desc (tekenreeks)
* @enum (tekenreeks)
* @inout (tekenreeks)
* @label (tekenreeks)
* @localizable (tekenreeks)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (tekenreeks)

### Ouders {#parents-12}

`<parameters>`

### Kinderen {#children-12}

`<help>`

### Beschrijving {#description-12}

Met dit element kunt u een parameter definiëren voor het aanroepen van een SOAP-methode.

### Beschrijving van kenmerk {#attribute-description-12}

* **desc (tekenreeks)**: beschrijving die betrekking heeft op het `<param>` element.
* **inout (tekenreeks)**: this attribute define whether or not the parameter is at the input (in) or output (out) of the SOAP call. Als dit kenmerk niet wordt opgegeven, wordt de standaardparameter invoer (&quot;@inout=in&quot;).
* **label (tekenreeks)**: `<param>` label
* **localizable (tekenreeks)**: Als dit kenmerk is geactiveerd, geeft dit het gereedschap Verzameling de opdracht om de waarde van het kenmerk &quot;@label&quot; te herstellen voor vertaling (intern gebruik).
* **naam (MNTOKEN)**: interne naam van de `<param>`
* **type (tekenreeks)**: this attribute define the type of `<param>` element

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
   * DOMDocument
   * DOMElement
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
   *  string
   * tijd
   * timespan
   * uuid

### Voorbeelden {#examples-9}

Definitie van de inkomende instelling &quot;serviceName&quot; van het tekenreekstype:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```

## `<parameters>` element {#parameters--element}

### Inhoudsmodel {#content-model-13}

parameters:==param

### Attributen {#attributes-13}

Geen

### Ouders {#parents-13}

`<method>`

### Kinderen {#children-13}

`<param>`

### Beschrijving {#description-13}

Dit element definieert een groep `<parameter>` elementen.

### Gebruik en gebruikscontext {#use-and-context-of-use-8}

Dit element is verplicht, zelfs voor één `<param>` onderliggend element van het `<method>` element.

### Beschrijving van kenmerk {#attribute-description-13}

Geen

### Voorbeelden {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```

## `<srcschema>` element {#srcschema--element}

### Inhoudsmodel {#content-model-14}

srcSchema:==(kenmerk| gemaaktDoor| Gegevens| element| opsomming| Help| interface| Methode| gewijzigdDoor)

### Attributen {#attributes-14}

gemaakt (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (string), img (string), implements (string), label (string), labelSingular (string), lastModified (datetime), library (boolean), mappingType (string), modifiedBy-id (long), name (string); namespace (tekenreeks), useRecycleBin (Boolean), view (boolean), xtkschema (tekenreeks)

### Ouders {#parents-14}

Geen

### Kinderen {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

### Beschrijving {#description-14}

Het `<srcschema>` is het hoofdelement van een schema. Dit is het invoerpunt voor de definitie van het schema.

### Gebruik en gebruikscontext {#use-and-context-of-use-9}

De presentatie van het schema is beschikbaar in [Ongeveer schemaverwijzing](../../configuration/using/about-schema-reference.md) en [de structuur](../../configuration/using/schema-structure.md)van het Schema.

### Beschrijving van kenmerk {#attribute-description-14}

* **gemaakt (datetime)**: this attribute provided information on the date and time of schema creation. Het heeft een formulier &#39;Datum en tijd&#39;. De weergegeven waarden worden opgehaald van de server. De tijd wordt getoond in formaat UTC.
* **createdBy-id (long)**: is het herkenningsteken van de exploitant die het schema creeerde.
* **desc (tekenreeks)**: schemabeschrijving
* **entiteitSchema (tekenreeks)**: basisschema waarop syntaxis en goedkeuring zijn gebaseerd (standaard voor Adobe Campagne: xtk:srcSchema). Wanneer u het huidige schema opslaat, zal de Campagne van Adobe zijn grammatica met het schema goedkeuren dat in de @xtkschema attributen wordt verklaard.
* **extendedSchema (tekenreeks)**: ontvangt de naam van het out-of-the-box schema waarop de huidige schemauitbreiding gebaseerd is. Het formulier is &quot;namespace:name&quot;.
* **img (tekenreeks)**: pictogram gekoppeld aan het schema (kan worden gedefinieerd in de wizard Schema maken).
* **label (tekenreeks)**: schemalabel.
* **labelSingular (string)**: label (enkelvoudig) voor weergave in de interface.
* **lastModified (datetime)**: this attribute provided information on the date and time of the last modification. Het heeft een formulier &#39;Datum en tijd&#39;. De weergegeven waarden worden opgehaald van de server. De tijd wordt getoond in formaat UTC.
* **bibliotheek (Booleaans)**: gebruik van het schema als bibliotheek en niet als entiteit. Naar dit schema kan daarom door andere schema&#39;s worden verwezen dankzij de kenmerken &quot;@ref&quot; en &quot;@template&quot;.
* **mappingType (tekenreeks)**:

   * &quot;sql&quot;: databasetoewijzing
   * &quot;textFile&quot;: tekstbestandstoewijzing
   * &quot;xmlFile&quot;: XML-bestandstoewijzing
   * &quot;binaryFile&quot;: binaire bestandstoewijzing

* **modifiedBy-id (long)**: komt overeen met de id van de operator die het schema heeft gewijzigd.
* **name (string)**: unieke schemanaam.
* **naamruimte (tekenreeks)**: naamruimte van het schema (standaard: nms, xtk, nl). Wanneer het creëren van een nieuw schema voor een project, adviseren wij dat u specifieke namespace gebruikt.
* **useRecycleBin (Boolean)**: Hiermee activeert u de prullenbak-functie in de toepassing. Verwijderde records worden in de prullenbak geplaatst voordat ze definitief worden verwijderd. Deze functie is alleen beschikbaar in de modus &quot;Aflevering&quot;.
* **weergave (Booleaans)**: als het wordt geactiveerd (@view=&quot;waar&quot;), zal het schema als mening worden gebruikt. De updatewizard voor de databasestructuur houdt geen rekening met het schema. Deze optie wordt vooral gebruikt voor het verwijzen naar externe tabellen.
* **xtkschema (tekenreeks)**: naam van het schema dat schema grammatica bepaalt (xtk:srcSchema door gebrek).

### Voorbeelden {#examples-11}

`<srcschema>` element of the &quot;nms:delivery&quot; out of the box schema

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```

## `<sysfilter>` element {#sysfilter--element}

### Inhoudsmodel {#content-model-15}

sysFilter:==condition

### Attributen {#attributes-15}

Geen

### Ouders {#parents-15}

`<element>`

### Kinderen {#children-15}

`<condition>`

### Beschrijving {#description-15}

Met dit element kunt u een filter definiëren.

### Beschrijving van kenmerk {#attribute-description-15}

Dit element heeft geen kenmerken.

### Voorbeelden {#examples-12}

Definitie van een filter met een voorwaarde voor het kenmerk @name:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```

## `<value>` element {#value--element}

### Inhoudsmodel {#content-model-16}

waarde:==help

### Attributen {#attributes-16}

* @applicableIf (tekenreeks)
* @desc (tekenreeks)
* @enabledIf (string)
* @img (tekenreeks)
* @label (tekenreeks)
* @name (tekenreeks)
* @value (tekenreeks)

### Ouders {#parents-16}

`<enumeration>`

### Kinderen {#children-16}

`<help>`

### Beschrijving {#description-16}

Met dit element kunt u de waarden definiëren die in een opsomming zijn opgeslagen.

### Beschrijving van kenmerk {#attribute-description-16}

* **applyIf (string)**: Met dit kenmerk kunt u een opsommingswaarde optioneel maken. Er wordt een XTK-expressie ontvangen.
* **desc (tekenreeks)**: beschrijving van de opsommingswaarde.
* **enabledIf (string)**: voorwaarde voor het activeren van de opsommingswaarde.
* **img (tekenreeks)**: afbeelding die is gekoppeld aan de opsomming in het formulier &quot;namespace:image_name&quot;. De afbeelding moet op de toepassingsserver worden geïmporteerd.
* **label (tekenreeks)**: label van de opsommingswaarde.
* **name (string)**: interne naam van de opsommingswaarde.
* **value (string)**: waarde van de opsommingswaarde. Het type waarde wordt gedefinieerd op basis van het type opsomming. Wanneer de opsomming van het type tekenreeks is, mag deze alleen tekenreekstype waarden bevatten.

### Voorbeelden {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
