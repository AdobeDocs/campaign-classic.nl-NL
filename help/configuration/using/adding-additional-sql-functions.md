---
product: campaign
title: Extra SQL-functies toevoegen
description: Meer informatie over het definiëren van extra SQL-functies
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# Aanvullende SQL-functies definiëren{#adding-additional-sql-functions}

Met Adobe Campaign kan de gebruiker definiëren **hun eigen functies** die tot SQL functies kunnen toegang hebben, zowel die aangeboden door het gegevensbestand als die die niet reeds beschikbaar in de console zijn. Dit is nuttig voor geaggregeerde functies (gemiddelde, maximum, som) bijvoorbeeld, die alleen op de server kunnen worden berekend of wanneer de database een eenvoudigere manier biedt om bepaalde functies te implementeren, in plaats van &quot;handmatig&quot; de expressie in de console te schrijven (bijvoorbeeld datumbeheer).

Dit mechanisme kan ook worden gebruikt als u een recente of ongewone SQL-functie van de database-engine wilt gebruiken, die nog niet door de Adobe Campaign-console wordt aangeboden.

Zodra deze functies zijn toegevoegd, zullen zij in de uitdrukkingsredacteur enkel als andere vooraf bepaalde functies verschijnen.

>[!IMPORTANT]
>
>SQL de functievraag in de console wordt niet meer van nature verzonden naar de server. Daarom wordt het hier beschreven mechanisme **de enige manier om te roepen** op de ongeplande SQL functieserver.

## Installatie {#installation}

De functie(s) die moet worden toegevoegd, bevinden zich in een **&quot;package&quot;-bestand in XML-indeling**, waarvan de structuur in de volgende alinea nader wordt beschreven.

Als u de toepassing vanuit de console wilt installeren, selecteert u de **Gereedschappen/Geavanceerd/Importeren** opties in het menu, en vervolgens **[!UICONTROL Install from file]** en volgt u de instructies in de wizard Importeren.

>[!IMPORTANT]
>
>Waarschuwing: zelfs als de lijst met geïmporteerde functies direct in de functie-editor wordt weergegeven, zijn ze pas bruikbaar als Adobe Campaign opnieuw is gestart.

## Algemene structuur van het te importeren pakket {#general-structure-of-package-to-import}

De functie(s) die moet worden toegevoegd, vindt u in de **&quot;package&quot;-bestand** in XML-indeling. Hier volgt een voorbeeld:

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "7.1"
  buildNumber = "10000">

  <entities schema="xtk:funcList">
    <funcList name="myList" namespace="cus">
      <group name="date" label="Personalized date">
        <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
                  minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
          <providerPart provider="MSSQL,Sybase,PostgreSQL" body="extract(year from age($1))-18"/>
        </function>
      </group>
    </funcList>
  </entities>
</package>
```

* De **name**, **namespace** en **label** uitsluitend ter informatie. Zij laten u een samenvatting van het pakket in de geïnstalleerde pakketlijst (Ontdekkingsreiziger/Beleid/het beheer van het Pakket/Geïnstalleerde pakketten) bekijken.
* De **buildVersion** en **buildNumber** velden zijn verplicht. Ze moeten overeenkomen met het servernummer waarmee de console is verbonden. Deze informatie vindt u in het vak &quot;Help/Info&quot;.
* de volgende blokken, **entiteiten** en **funclist** zijn verplicht. In funcList zijn de velden &quot;name&quot; en &quot;namespace&quot; verplicht, maar de gebruiker kan zelf beslissen welke naam hij of zij gebruikt en geven de functielijst op unieke wijze aan.

   Dit betekent dat als een andere lijst met functies met dezelfde naamruimte/naamcombinatie (hier &quot;cus::myList&quot;) wordt geïmporteerd, de eerder geïmporteerde functies worden verwijderd. Omgekeerd geldt dat als u dit naamruimte-/naampaar wijzigt, de nieuwe reeks geïmporteerde functies wordt toegevoegd aan de vorige.

* De **groep** Met een element kunt u de functiegroep opgeven waarin de geïmporteerde functie(s) worden weergegeven in de functie-editor. Het kenmerk @name kan een naam zijn die al bestaat (in welk geval de functies worden toegevoegd aan de desbetreffende groep) of een nieuwe naam (in welk geval de functie wordt weergegeven in een nieuwe groep).
* Herinnering: mogelijke waarden voor het kenmerk @name in het dialoogvenster `<group>` element are:

   ```
     name="aggregate"      ( label="Aggregates"         )
     name="string"             ( label="String"           )
     name="date"               ( label="Date"             )
     name="numeric"          ( label="Numeric"        )
     name="geomarketing" ( label="Geomarketing"     )
     name="other"              ( label="Others"           )
     name="window"          ( label="Windowing functions" )
   ```

>[!IMPORTANT]
>
>Zorg ervoor dat u het kenmerk @label invult: dit is de naam die wordt weergegeven in de lijst met beschikbare functies. Als u niets invoert, heeft de groep geen naam. Als u echter een andere naam invoert dan de bestaande naam, verandert de naam van de hele groep.

Als u functies wilt toevoegen aan verschillende groepen, kunt u verschillende `<group>`  elementen worden in dezelfde lijst bijgehouden.

Tot slot `<group>` -element kan de definitie van een of meer functies bevatten, dat is het doel van het pakketbestand. De  `<function>`   het element wordt in de volgende alinea nader beschreven.

## Functiebeschrijving &lt;function>&lt;/function> {#function-descriptor--function-}

Het onderhavige geval is een algemeen geval waarin wij de **functie-implementatie**.

Hieronder ziet u een voorbeeld van een functie van &quot;relatieve rijpheid&quot; die, op basis van een leeftijd, aangeeft hoeveel jaren de persoon als volwassen wordt beschouwd.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

De **@name** in het veld wordt de naam van de functie weergegeven en in het veld args wordt de lijst met parameters weergegeven die in de beschrijving wordt weergegeven. In dit geval wordt de functie weergegeven als &quot;relativeMaturity&quot; ( `<age>` )&quot; in het venster Functie selecteren.

* **help** Dit is het veld dat onder aan het venster van de expressieeditor wordt weergegeven.
* **@display** is een informatief bericht.

   >[!NOTE]
   >
   >In de kenmerken @help en @display vertegenwoordigt de tekenreeks &quot;$1&quot; de naam die is gegeven in de eerste functieparameter (hier, &quot;Leeftijd&quot;). $2, $3... zou de volgende parameters vertegenwoordigen. In het @body-kenmerk dat hieronder wordt beschreven, geeft $1 de argumentwaarde aan die tijdens de aanroep aan de functie wordt doorgegeven.

   >[!NOTE]
   >
   >De beschrijving moet een tekenreeks zijn met geldige XML-tekens: Let op het gebruik van &#39;&lt;&#39; en &#39;>&#39; in plaats van &lt; en >.

* **@type** Dit is het type geretourneerde waarde van de functie en is een standaardwaarde (lang, tekenreeks, byte, datumtime..). Als het wordt weggelaten, bepaalt de server het beste type onder de beschikbare types binnen de uitdrukking die de functie uitvoert.
* **@minArgs** en **maxArgs** Hiermee wordt het aantal parameters (minimum en maximum) voor een parameter opgegeven. Voor een functie met 2 parameters zijn minArgs en maxArgs bijvoorbeeld 2 en 2. Voor drie parameters, plus 1 optioneel, zijn deze respectievelijk 3 en 4.
* Tot slot **providerPart** element verstrekt de functie implementatie.

   * De **provider** attribuut is mandatory, it specifies the database systems for which the implementation is provided. Zoals getoond in het voorbeeld, wanneer de uitdrukkingssyntaxis of onderliggende functies verschillen, kunnen de alternatieve implementaties volgens het gegevensbestand worden verstrekt.
   * De **@body** bevat de functie-implementatie. Opmerking: deze implementatie moet een expressie zijn in de databasetaal (niet een codeblok). Afhankelijk van de databases kunnen expressies subquery&#39;s zijn (&quot;(selecteer kolom in de tabel waarin...)&quot;) die slechts één waarde retourneren. Dit is bijvoorbeeld het geval in Oracle (de query moet tussen haakjes worden geschreven).

   >[!NOTE]
   >
   >Als slechts één of twee gegevensbestanden waarschijnlijk door de bepaalde functie worden gevraagd, kunnen wij altijd slechts de definities verstrekken die aan deze gegevensbestanden beantwoorden.

## Functiebeschrijving &#39;Pass-through&#39; {#pass-through--function-descriptor}

Een speciale functiebeschrijving is de **&quot;pass-through&quot;** blok, met een niet gespecificeerd &quot;leverancier&quot;gegevensbestandsysteem. In dit geval kan de implementatie van de &#39;body&#39; slechts één functieaanroep bevatten met een syntaxis die niet afhankelijk is van de gebruikte database. Ondertussen is het blok &quot;ProviderPart&quot; uniek.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

In dit geval dient het toevoegen van een functie alleen om een databasefunctie te maken die niet standaard beschikbaar zou zijn geweest, nu zichtbaar voor de client.

## Voorbeelden {#examples}

Meer functievoorbeelden vindt u in het vooraf gedefinieerde pakket &quot;xtkdatakitfuncList.xml&quot;.
