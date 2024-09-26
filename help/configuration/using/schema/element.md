---
product: campaign
title: Schemaelementen en -kenmerken - element
description: element
feature: Schema Extension
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: 728848eab059fc669c241346a2ff1feebd79222c
workflow-type: tm+mt
source-wordcount: '2029'
ht-degree: 0%

---

# element {#element--element}

![](../../../assets/v7-only.svg)

## Inhoudsmodel {#content-model-4}

element:==(attribute | compute-string | dbindex | default | element | help | join | key | sysFilter | translateDefault)

## Attributen {#attributes-4}

_operation (string), advanced (boolean), aggregaat (string), applyIf (string), automatische schakeling (boolean), behoortTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAsField (boolean) lean), doesNotSupportDiff (boolean), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink (model) string), folderProcess (string), fullLoad (boolean), hiërarchical (boolean), hiërarchicalPath (string), img (string), inout (string), integriteit (string), label (string), labelSingular (string), length (string), localizable (boolean), name (MNTOKEN), noDbIndex (boolean), noKey boolean), ordered (boolean), overflowtable (boolean), pkSequence (string), pkgStatus (string), ref (string), required (boolean), revAdvanced (boolean), revCardinality (string), revDesc (string), revExternalJoin (boolean), revIntegrity (string) Label (string), revLink (string), revTarget (string), revVisibleIf (string), sql (boolean), sqlname (string), sqltable (string), tableSpace (string), tableSpaceIndex (string), target (MNTOKEN), template (string), temporaryTable (boolean), translateDefault (string), translateExpr (tekenreeks), type (MNTOKEN), unbound (Boolean), gebruiker (Boolean), userEnum (tekenreeks), visibleIf (tekenreeks), xml (Boolean), xmlChildren (Boolean)

## Ouders {#parents-4}

`<srcschema>`

`<element>`

## Kinderen {#children-4}

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

## Beschrijving {#description-4}

Er zijn vier typen `<element>` -elementen in Adobe Campaign:

* Basis `<element>` : definieert de naam van de SQL-tabel die overeenkomt met het schema.
* Structuur `<element>` : definieert een groep van `<element>`   of   `<attribute>`    elementen.
* Koppeling `<element>` : definieert een koppeling. Deze elementen moeten het kenmerk &quot;@type=link&quot; bevatten.
* XML `<element>` : definieert het veld &#39;mData&#39; van het teksttype. Dit element moet het kenmerk &quot;@type=xml&quot; bevatten.

## Beschrijving van kenmerk {#attribute-description-4}

* **_operation (koord)**: bepaalt het type van het schrijven in het gegevensbestand.

  Dit kenmerk wordt vooral gebruikt bij het uitbreiden van out-of-box schema&#39;s.

  Toegankelijke waarden zijn:

   * &quot;none&quot;: verzoening alleen. Dit betekent dat Adobe Campaign het element zal herstellen zonder het bij te werken of een fout te genereren als het niet bestaat.
   * &quot;insertOrUpdate&quot;: update met invoeging. Dit betekent dat Adobe Campaign het element bijwerkt of maakt als het niet bestaat.
   * &quot;insert&quot;: invoeging. Dit betekent dat Adobe Campaign het element invoegt zonder te controleren of het bestaat.
   * &quot;update&quot;: update. Dit betekent dat Adobe Campaign het element zal bijwerken of een fout zal produceren als het niet bestaat.
   * &quot;delete&quot;: schrapping. Dit betekent dat Adobe Campaign elementen herstelt en verwijdert.

* **geavanceerd (boolean)**: wanneer deze optie (@advanced= &quot;waar&quot;) wordt geactiveerd, laat het u de attributen op de lijst van beschikbare gebieden verbergen toegankelijk voor het vormen van een lijst in een vorm.
* **aggregaat (koord)**: laat u de definitie van een `<element>` via een ander schema kopiëren. Dit kenmerk ontvangt een schemadeclaratie in de vorm van een &quot;namespace:name&quot;.
* **applyIf (koord)**: voorwaarde voor het toepassen van de index. Dit kenmerk ontvangt een XTK-expressie.
* **automatische (boolean)**: als deze optie wordt geactiveerd (automatische controle= &quot;waar&quot;), zal een unieke sleutel automatisch worden bepaald. Deze optie mag alleen worden gebruikt voor het hoofdelement van het schema. Waarschuwing: Adobe Campaign garandeert alleen dat de gegenereerde sleutel uniek is. Het is niet gegarandeerd dat de hoofdwaarden opeenvolgend en incrementeel zijn.
* **dataPolicy (koord)**: laat u toe om goedkeuringsbeperkingen op waarden te specificeren die op het SQL gebied worden toegestaan. De waarden voor dit kenmerk zijn:

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
* **gebrek (koord)**: laat u elementengedrag (vraag aan een functie, standaardwaarde) bepalen. Dit kenmerk ontvangt een XTK-expressie.
* **desc (koord)**: laat u een beschrijving van het element opnemen. Deze beschrijving wordt gebruikt om te begrijpen wat het element is en waarvoor het wordt gebruikt. U kunt het in het formulier weergeven.
* **displayAsField (boolean)**: als dit attribuut wordt geactiveerd, zal een &quot;verbinding&quot;type `<element>` als gebied in de boomstructuurmening van de schema&#39;s (&quot;Structuur&quot;tabel) worden getoond. Op deze manier is het mogelijk om een koppeling weer te geven als een lokaal veld en het gedrag ervan te wijzigen tijdens een query. Wanneer het element wordt gevonden in SELECT van een query, wordt de waarde van het koppelingsdoel gebruikt. Wanneer het element in WAAR van een vraag wordt gevonden, zal de onderliggende sleutel van de verbinding worden gebruikt.
* **geef (koord) uit**: dit attribuut specificeert het type van input die in de vorm verbonden aan het schema zal worden gebruikt.
* **opsomming (koord)**: ontvangt de naam van de opsomming verbonden aan het gebied. De opsomming kan in het zelfde schema of in een ver schema worden opgenomen.
* **expr (koord)**: dit attribuut bepaalt een berekend gebied waarvoor geen definitie in de lijst wordt opgeslagen. Het ontvangt een Xpath- of een XTK-expressie (string).
* **externalJoin (boolean)**: externe sluit zich aan in een &quot;verbinding&quot;typeelement.
* **eigenschap (koord)**: bepaalt een kenmerkengebied: Deze gebieden worden gebruikt voor het uitbreiden van de gegevens in een bestaande lijst, maar met opslag in een bijlage lijst. Accepteerde waarden zijn:

   * &quot;shared&quot;: de inhoud wordt opgeslagen in een gedeelde tabel per gegevenstype
   * &quot;toegewezen&quot;: de inhoud wordt opgeslagen in een speciale tabel

  SQL-kenmerktabellen worden automatisch gebaseerd op het kenmerktype:

   * toegewezen: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * shared: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Er zijn twee typen kenmerkvelden: eenvoudige velden waarvoor één waarde is toegestaan op het kenmerk, en meerkeuzevelden waarin het kenmerk is gekoppeld aan een verzamelingselement dat meerdere waarden kan bevatten.

  Wanneer een eigenschap in een schema wordt bepaald, moet dit schema een belangrijkste sleutel hebben die op één enkel gebied wordt gebaseerd (de samengestelde sleutels zijn niet geoorloofd).

* **featureDate (boolean)**: attribuut verbonden aan het &quot;@feature&quot;eigenschapgebied. Als de waarde &quot;true&quot; is, kunt u erachter komen wanneer de waarde voor het laatst is bijgewerkt.
* **filterPath (koord)**: dit attribuut ontvangt een Xpath en laat u een filter op een gebied bepalen.
* **folderLink (koord)**: dit attribuut ontvangt de naam van de verbinding die u de dossiers laat terugkrijgen die entiteiten bevatten.
* **folderModel (koord)**: bepaalt het type van omslag dat entiteitopslag toelaat. Dit kenmerk wordt alleen gedefinieerd als &quot;@folderLink&quot; aanwezig is.
* **folderProcess (koord)**: bepaalt de verbinding waar de instanties van het entiteitmodel worden opgeslagen. Dit kenmerk wordt alleen gedefinieerd als &quot;@folderLink&quot; aanwezig is.
* **fullLoad (boolean)**: dit attribuut dwingt de vertoning van alle verslagen in een lijst tijdens gebiedsselectie in een vorm.
* **img (koord)**: ontvangt de weg van een beeld verbonden aan een element. De waarde van dit kenmerk is van het type &quot;namespace:image name&quot;. Bijvoorbeeld: img=&quot;cus:myImage.jpg&quot;. De afbeelding moet fysiek naar de toepassingsserver worden geïmporteerd.
* **integriteit (koord)**: referentiële integriteit van het voorkomen van de bronlijst naar de doellijst.

  Toegankelijke waarden zijn:

   * &quot;define&quot;: Adobe Campaign verwijdert de entiteit niet als ernaar wordt verwezen via de koppeling
   * &quot;normal&quot;: wanneer de broninstantie wordt verwijderd, worden de toetsen van de koppeling op de doelinstantie geïnitialiseerd (standaardmodus). Bij dit type integriteit worden alle externe toetsen geïnitialiseerd
   * &quot;own&quot;: als u de broninstantie verwijdert, wordt de doelinstantie verwijderd
   * &quot;eigen exemplaar&quot;: vergelijkbaar met &quot;eigen&quot; (in geval van verwijdering) of duplicaten van voorvallen (in geval van duplicatie)
   * &quot;neutral&quot;: doet niets

* **etiket (koord)**: elementetiket.
* **labelSingular (koord)**: etiket (enige vorm) van het element dat in sommige delen van de interface wordt gebruikt.
* **lengte (koord)**: max. Het aantal tekens dat is geautoriseerd voor een waarde van het SQL-veld voor het type &quot;string&quot;.
* **localizable (boolean)**: als het wordt geactiveerd, vertelt dit attribuut het inzamelingshulpmiddel om de waarde van het &quot;@label&quot;attribuut voor vertaling (intern gebruik) terug te krijgen.
* **naam (MNTOKEN)**: interne naam van het element dat de naam van de lijst aanpast. De waarde van het kenmerk &quot;@name&quot; moet kort zijn, bij voorkeur in het Engels, en voldoen aan naamgevingsbeperkingen die zijn gekoppeld aan XML.

  Als het schema naar de database wordt geschreven, worden automatisch voorvoegsels aan de veldnaam toegevoegd door Adobe Campaign.

   * &quot;i&quot;: prefix voor het type &#39;integer&#39;.
   * &quot;d&quot;: prefix voor het type &#39;double&#39;.
   * &quot;s&quot;: voorvoegsel voor het tekenreekstype.
   * &quot;ts&quot;: voorvoegsel voor het type &#39;date&#39;.

  Om de naam van de lijst op een autonome manier te bepalen, moet u het &quot;@sqltable&quot;attribuut in de definitie van het belangrijkste schemaelement gebruiken.

* **noDbIndex (boolean)**: laat u specificeren dat het element niet zal worden geïndexeerd.
* **bevolen (boolean)**: als het attribuut (ordered= &quot;waar&quot;) wordt geactiveerd, houdt Adobe Campaign de opeenvolging van de elementendeclaratie in een de inzamelingselement van XML.
* **pkSequence (koord)**: ontvangt de naam van de opeenvolging die voor het berekenen van een auto-stijgende sleutel moet worden gebruikt. Dit kenmerk mag alleen worden gebruikt als een automatisch incrementele sleutel is gedefinieerd voor het hoofdelement van het schema.
* **pkgStatus (koord)**: tijdens pakketuitvoer, zullen de waarden als functie van de waarde van dit attribuut worden in aanmerking genomen:

   * &quot;always&quot;: het element zal altijd aanwezig zijn
   * &quot;never&quot;: het element zal nooit aanwezig zijn
   * &quot;default (or none)&quot;: het element wordt geëxporteerd tenzij het het standaardelement is of als het geen intern veld is en niet compatibel zou zijn met andere instanties

* **ref (koord)**: dit attribuut bepaalt een verwijzing naar een >element> element dat door verscheidene schema&#39;s wordt gedeeld (definitie factoring). De definitie wordt niet gekopieerd naar het huidige schema.
* **vereist (boolean)**: als dit attribuut (@required= &quot;waar&quot;) wordt geactiveerd, wordt het gebied benadrukt in de interface. Het label van het veld wordt rood in formulieren.
* **revAdvanced (boolean)**: wanneer geactiveerd, specificeert dit attribuut dat de tegenovergestelde verbinding een &quot;geavanceerde&quot;verbinding is.
* **revCardinality (koord)**: dit attribuut bepaalt de kardinaliteit van een verband tussen twee lijsten. Deze wordt gebruikt in het type &quot;link&quot; `<element>` .

  Mogelijke waarden zijn:

   * &quot;single&quot; : eenvoudige koppeling van het type 1-1
   * &quot;unbound&quot;: koppeling voor verzameling van het type 1-N

  Als het kenmerk niet is opgegeven tijdens het maken van koppelingen, is de standaardinstelling 1-N.

* **revDesc (koord)**: dit attribuut ontvangt een beschrijving verbonden aan de tegenovergestelde verbinding.
* **revExternalJoin (boolean)**: wanneer geactiveerd, laat dit attribuut u de externe toetreden op de tegenovergestelde verbinding dwingen.
* **revIntegrity (koord)**: dit attribuut bepaalt de integriteit op het doelschema. Dezelfde waarden als het kenmerk &quot;@integriteit&quot; zijn geautoriseerd. Adobe Campaign geeft standaard de &quot;normale&quot; waarde aan dit kenmerk.
* **revLabel (koord)**: etiket van de tegenovergestelde verbinding.
* **revLink (koord)**: naam van de tegenovergestelde verbinding. Als de waarde &quot;_GEEN_&quot;is, zal geen tegenovergestelde verbinding in het bestemmingsschema worden gecreeerd.
* **revTarget (koord)**: doel van de tegenovergestelde verbinding.
* **sql (boolean)**: als dit attribuut (@sql= &quot;waar&quot;) wordt geactiveerd, dwingt het opslag van het SQL element, zelfs als het element het xml= &quot;waar&quot;bezit heeft.
* **sqlname (koord)**: naam van het gebied tijdens lijstverwezenlijking. Als &quot;@sqlname&quot; niet is opgegeven, wordt standaard de waarde van het kenmerk &quot;@name&quot; gebruikt. Bij het schrijven van het schema naar de tabel worden de voorvoegsels automatisch toegevoegd, afhankelijk van het veldtype.
* **sqltable (koord)**: voor het belangrijkste element van het schema, laadt dit attribuut de naam van de SQL lijst die door gebrek wordt geproduceerd. Als &quot;@sqltable&quot;niet wordt gespecificeerd, zal de standaardnaam als dit worden gestructureerd: namespace (eerste brief hoogste geval) gevolgd door de waarde van SrcSchema &quot;@name&quot;.
* **tableSpace (koord)**: dit attribuut laat u een nieuw gegeven specificeren dat tabelruimte voor een lijst (geldig op de wortel `<element>`) opslaat.
* **tableSpaceIndex (koord)**: dit attribuut laat u een nieuwe lijst van de indexopslag voor een lijst (geldig op de wortel `<element>`) specificeren.
* **doel (MNTOKEN)**: ontvangt de naam van het doelschema wanneer het creëren van een verband tussen lijsten. Dit kenmerk is alleen actief voor elementen van het type &quot;link&quot;.
* **malplaatje (koord)**: dit attribuut bepaalt een verwijzing naar een `<element>` element dat door verscheidene schema&#39;s wordt gedeeld. De definitie wordt automatisch gekopieerd naar het huidige schema.
* **translateDefault (koord)**: als een &quot;@default&quot;attribuut wordt gevonden, zal &quot;@translateDefault&quot;u toelaten om een uitdrukking opnieuw te bepalen die in @default wordt bepaald, die door het vertaalhulpmiddel (intern gebruik) moet worden verzameld.
* **translatedExpr (koord)**: als een &quot;@expr&quot;attribuut wordt gevonden, laat het &quot;@translateExpr&quot;attribuut u een uitdrukking opnieuw bepalen die in &quot;@expr&quot;wordt bepaald, en die door het vertaalhulpmiddel (intern gebruik) zal worden verzameld.
* **type (MNTOKEN)**: bepaalt het type van gegevens die in het element worden opgeslagen.

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

* **niet geconsolideerd (boolean)**: als het attribuut (unbound= &quot;waar&quot;) wordt geactiveerd, wordt de verbinding verklaard als inzamelingselement voor een kardinaliteit 1-N.
* **userEnum (koord)**: ontvangt de interne naam van een &quot;open&quot;opsomming. Opsommingswaarden kunnen door de gebruiker in de interface worden gedefinieerd.
* **xml (boolean)**: als deze optie wordt geactiveerd, worden alle waarden die in het element worden bepaald opgeslagen in XML in een &quot;mData&quot;gebied van het type van TEKST. Dit betekent dat er op deze velden geen filters of sortering zullen plaatsvinden.
* **xmlChildren (boolean)**: krachten opslag voor elk kind ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
