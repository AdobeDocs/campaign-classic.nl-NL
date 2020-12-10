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
source-wordcount: '2011'
ht-degree: 0%

---


# `<element>` element  {#element--element}

## Inhoudsmodel {#content-model-4}

element:==(attribute | compute string | debindex | Standaard | element | Help | Verbinden | Sleutel | sysFilter | vertaaldStandaard)

## Kenmerken {#attributes-4}

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

Er zijn vier typen `<element>` elementen in Adobe Campaign:

* Hoofdmap `<element>`: definieert de naam van de SQL-tabel die overeenkomt met het schema.
* Structuur `<element>`: definieert een groep van `<element>`   of   `<attribute>`    elementen.
* Koppeling `<element>`: definieert een koppeling. Deze elementen moeten het kenmerk &quot;@type=link&quot; bevatten.
* XML `<element>`: definieert een veld van het teksttype &quot;mData&quot;. Dit element moet het kenmerk &quot;@type=xml&quot; bevatten.

## Kenmerkbeschrijving {#attribute-description-4}

* **_operation (string)**: definieert het type schrijven in de database.

   Dit kenmerk wordt vooral gebruikt bij het uitbreiden van out-of-the-box schema&#39;s.

   Toegankelijke waarden zijn:

   * &quot;none&quot;: verzoening alleen. Dit betekent dat Adobe Campaign het element zal herstellen zonder het bij te werken of een fout te genereren als het niet bestaat.
   * &quot;insertOrUpdate&quot;: bijwerken met invoeging. Dit betekent dat Adobe Campaign het element bijwerkt of maakt als het niet bestaat.
   * &quot;invoegen&quot;: invoeging. Dit betekent dat Adobe Campaign het element invoegt zonder te controleren of het bestaat.
   * &quot;update&quot;: bijwerken. Dit betekent dat Adobe Campaign het element zal bijwerken of een fout zal produceren als het niet bestaat.
   * &quot;delete&quot;: verwijderen. Dit betekent dat Adobe Campaign elementen herstelt en verwijdert.

* **geavanceerd (Booleaans)**: als deze optie is geactiveerd (@advanced=&quot;true&quot;), kunt u het kenmerk verbergen in de lijst met beschikbare velden die toegankelijk zijn voor het configureren van een lijst in een formulier.
* **aggregaat (tekenreeks)**: Hiermee kunt u de definitie van een schema kopiëren  `<element>`  via een ander schema. Dit kenmerk ontvangt een schemadeclaratie in de vorm van een &quot;namespace:name&quot;.
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

* **dbEnum (tekenreeks)**: ontvangt de interne naam van een &quot;gesloten&quot;opsomming. De opsommingswaarden moeten in `<srcschema>` worden bepaald.
* **defOnDuplicate (boolean)**: Als dit kenmerk wordt geactiveerd, wordt de standaardwaarde (gedefinieerd in @default) automatisch opnieuw toegepast op de record wanneer een record wordt gedupliceerd.
* **default (string)**: Hiermee kunt u elementgedrag definiëren (aanroepen van een functie, standaardwaarde). Dit kenmerk ontvangt een XTK-expressie.
* **desc (tekenreeks)**: Hiermee kunt u een beschrijving van het element invoegen. Deze beschrijving wordt getoond in de statusbar van de interface.
* **displayAsField (boolean)**: Als dit kenmerk is geactiveerd,  `<element>`  wordt een koppelingstype weergegeven als een veld in de boomstructuurweergave van de schema&#39;s (&quot;Structuur&quot; tabblad). Op deze manier is het mogelijk om een koppeling weer te geven als een lokaal veld en het gedrag ervan te wijzigen tijdens een query. Wanneer het element wordt gevonden in SELECT van een query, wordt de waarde van het koppelingsdoel gebruikt. Wanneer het element in WAAR van een vraag wordt gevonden, zal de onderliggende sleutel van de verbinding worden gebruikt.
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
* **ordered (boolean)**: als het kenmerk is geactiveerd (ordered=&quot;true&quot;), behoudt Adobe Campaign de declaratiereeks van het element in een XML-verzamelingselement.
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
* **revIntegrity (tekenreeks)**: dit attribuut bepaalt de integriteit op het doelschema. Dezelfde waarden als het kenmerk &quot;@integriteit&quot; zijn geautoriseerd. Adobe Campaign geeft standaard de &quot;normale&quot; waarde aan dit kenmerk.
* **revLabel (tekenreeks)**: label van de tegenovergestelde koppeling.
* **revLink (tekenreeks)**: naam van de tegenovergestelde koppeling. Als de waarde &quot;_NONE_&quot;is, zal geen tegenovergestelde verbinding in het bestemmingsschema worden gecreeerd.
* **revTarget (tekenreeks)**: doel van de tegenovergestelde koppeling.
* **sql (Boolean)**: als dit kenmerk is geactiveerd (@sql=&quot;true&quot;), wordt de opslag van het SQL-element afgedwongen, zelfs als het element de eigenschap xml=&quot;true&quot; heeft.
* **sqlname (tekenreeks)**: naam van het veld tijdens maken van tabel. Als &quot;@sqlname&quot; niet is opgegeven, wordt standaard de waarde van het kenmerk &quot;@name&quot; gebruikt. Bij het schrijven van het schema naar de tabel worden de voorvoegsels automatisch toegevoegd, afhankelijk van het veldtype.
* **sqltable (tekenreeks)**: voor het hoofdelement van het schema, laadt dit attribuut de naam van de SQL lijst die door gebrek wordt geproduceerd. Als &quot;@sqltable&quot; niet wordt gespecificeerd, zal de standaardnaam als dit worden gestructureerd: naamruimte (hoofdletter van eerste letter), gevolgd door de waarde van het SrcSchema &quot;@name&quot;.
* **tableSpace (tekenreeks)**: Met dit kenmerk kunt u een nieuwe gegevensopslagruimte voor een tabel opgeven (geldig op het hoofdniveau  `<element>`).
* **tableSpaceIndex (tekenreeks)**: Met dit kenmerk kunt u een nieuwe tabelruimte voor indexopslag voor een tabel opgeven (geldig op het hoofdniveau  `<element>`).
* **doel (MNTOKEN)**: ontvangt de naam van het doelschema wanneer u een koppeling tussen tabellen maakt. Dit kenmerk is alleen actief voor elementen van het type &quot;link&quot;.
* **sjabloon (tekenreeks)**: this attribute define a reference to an  `<element>` element shared by various schema&#39;s. De definitie wordt automatisch gekopieerd naar het huidige schema.
* **translateDefault (tekenreeks)**: Als een kenmerk &quot;@default&quot; wordt gevonden, kunt u met het kenmerk &quot;@translateDefault&quot; een expressie opnieuw definiëren die overeenkomt met de expressie die in @default is gedefinieerd, en die worden verzameld met het gereedschap Vertalen (intern gebruik).
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
   * string
   * tijd
   * timespan
   * uuid

* **niet geconsolideerd (Boolean)**: als het attribuut wordt geactiveerd (unbound= &quot;waar&quot;), wordt de verbinding verklaard als inzamelingselement voor een kardinaliteit 1-N.
* **userEnum (tekenreeks)**: ontvangt de interne naam van een &quot;open&quot; opsomming. Opsommingswaarden kunnen door de gebruiker in de interface worden gedefinieerd.
* **xml (Boolean)**: Als deze optie is geactiveerd, worden alle waarden die in het element zijn gedefinieerd, opgeslagen in XML in het veld &#39;mData&#39; van het type TEXT. Dit betekent dat er op deze velden geen filters of sortering zullen plaatsvinden.
* **xmlChildren (boolean)**: de opslagcapaciteit van de strijdkrachten voor elk kind (  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
