---
title: Filtervoorwaarden definiëren
seo-title: Filtervoorwaarden definiëren
description: Filtervoorwaarden definiëren
seo-description: null
page-status-flag: never-activated
uuid: 2ed5d0bd-88fd-4eff-baf0-ed1b097269da
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: creating-queries
discoiquuid: 8e575da0-c51a-4106-a826-3e1771e63649
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Filtervoorwaarden definiëren{#defining-filter-conditions}

## De operator kiezen {#choosing-the-operator}

Binnen het filtreren voorwaarden, moet u twee waarden verbinden samen gebruikend een exploitant.

![](assets/query_editor_nveau_96.png)

Hieronder volgt een lijst met de beschikbare operatoren:

<table> 
 <thead> 
  <tr> 
   <th> Operator<br /> </th> 
   <th> Doel<br /> </th> 
   <th> Voorbeeld<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Gelijk aan</span><br /> </td> 
   <td> Retourneert een resultaat dat identiek is aan de gegevens die zijn ingevoerd in de tweede kolom Waarde.<br /> </td> 
   <td> <strong>Achternaam (@lastName) gelijk aan 'Jones'</strong>retourneert alleen ontvangers met als achternaam Jones.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Groter dan</span><br /> </td> 
   <td> Retourneert een waarde die groter is dan de ingevoerde waarde.<br /> </td> 
   <td> <strong>Leeftijd (@tijdperk) groter dan 50</strong>, geeft alle waarden groter dan '50', d.w.z. "51", "52", enz.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Kleiner dan</span><br /> </td> 
   <td> Retourneert een waarde die kleiner is dan de ingevoerde waarde.<br /> </td> 
   <td> <strong>Aanmaakdatum (@created) voor 'DaysAgo(100)'</strong>, retourneert alle ontvangers die minder dan 100 dagen geleden zijn gemaakt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Groter dan of gelijk aan</span><br /> </td> 
   <td> Retourneert alle waarden die gelijk zijn aan of groter zijn dan de ingevoerde waarde.<br /> </td> 
   <td> <strong>Leeftijd (@age) groter dan of gelijk aan '30'</strong>, retourneert alle ontvangers van 30 jaar of ouder.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Kleiner dan of gelijk aan</span><br /> </td> 
   <td> Retourneert alle waarden die gelijk zijn aan of lager zijn dan de ingevoerde waarde.<br /> </td> 
   <td> <strong>Leeftijd (@age) kleiner dan of gelijk aan '60'</strong>, retourneert alle ontvangers van 60 jaar of ouder.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Niet gelijk aan</span><br /> </td> 
   <td> Retourneert alle waarden die niet identiek zijn aan de ingevoerde waarde.<br /> </td> 
   <td> <strong>Taal (@taal) gelijk aan 'Engels'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Begint met</span><br /> </td> 
   <td> Retourneert de resultaten die beginnen met de ingevoerde waarde.<br /> </td> 
   <td> <strong>Account # (@account) begint met '32010'.</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Begint niet met</span><br /> </td> 
   <td> Retourneert de resultaten die niet beginnen met de ingevoerde waarde.<br /> </td> 
   <td> <strong>Account # (@account) begint niet met '20'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bevat</span><br /> </td> 
   <td> Retourneert de resultaten die ten minste de ingevoerde waarde bevatten.<br /> </td> 
   <td> <strong>E-maildomein (@domain) bevat 'mail'</strong>, retourneert alle domeinnamen die 'mail' bevatten. Het domein 'gmail.com' wordt dus ook geretourneerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bevat</span> niet <br /> </td> 
   <td> Retourneert resultaten die niet de ingevoerde waarde bevatten.<br /> </td> 
   <td> <strong>E-maildomein (@domein) bevat geen 'vo'</strong>. In dit geval worden domeinnamen die 'vo' bevatten, niet geretourneerd. De domeinnaam voila.fr wordt niet weergegeven in de resultaten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">leuk</span><br /> </td> 
   <td> <span class="uicontrol">Zoals</span> lijkt het op de operator <span class="uicontrol">Bevat</span> . Hiermee kunt u een <span class="uicontrol">%</span> jokerteken in de waarde invoegen.<br /> </td> 
   <td> <strong>Achternaam (@lastName) zoals 'Jon%s'</strong>. Hier wordt het jokerteken gebruikt als een joker om de naam Jones te vinden, mocht de operator de ontbrekende letter tussen de 'n' en 's' vergeten hebben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Niet leuk</span><br /> </td> 
   <td> Is gelijkaardig aan <span class="uicontrol">als</span> . Hiermee kunt u de ingevoerde waarde niet herstellen. Ook hier moet de ingevoerde waarde het teken <span class="uicontrol">%</span> wild bevatten.<br /> </td> 
   <td> <strong>Achternaam (@lastName) houdt niet van 'Smi%h'</strong>. Hier worden de ontvangers met de achternaam 'Smi%h' niet geretourneerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is leeg</span><br /> </td> 
   <td> In dit geval komt het resultaat dat we zoeken overeen met een lege waarde in de tweede kolom Waarde.<br /> </td> 
   <td> <strong>Mobiele (@mobilePhone) is leeg</strong> en retourneert alle ontvangers die geen mobiel nummer hebben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is niet leeg</span><br /> </td> 
   <td> Werkt in omgekeerde volgorde naar de operator <span class="uicontrol">Is leeg</span> . Het is niet nodig gegevens in te voeren in de tweede kolom Waarde.<br /> </td> 
   <td> <strong>E-mail (@email) is niet leeg</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is opgenomen in</span><br /> </td> 
   <td> Retourneert resultaten die zijn opgenomen in de aangegeven waarden. Deze waarden moeten door een komma worden gescheiden.<br /> </td> 
   <td> <strong>Geboortedatum (@geboortedatum) is opgenomen in 12-10-1979.12-10-1984'</strong>, en retourneert de ontvangers die geboren zijn tussen deze data. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is niet opgenomen in</span><br /> </td> 
   <td> Werkt zoals <span class="uicontrol">Is inbegrepen in</span> exploitant. Hier, willen wij ontvangers uitsluiten die op de ingegane waarden worden gebaseerd.<br /> </td> 
   <td> <strong>Geboortedatum (@geboortedatum) is niet opgenomen in 10-12-1979.12-10-1984"</strong>. Anders dan in het vorige voorbeeld worden ontvangers die binnen deze datums geboren zijn, niet geretourneerd.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## EN, OF, BEHALVE {#using-and--or--except}

Voor vragen die verscheidene het filtreren voorwaarden gebruiken, moet u verbindingen tussen de voorwaarden bepalen. Er zijn drie mogelijke koppelingen:

* **[!UICONTROL And]** Hiermee kunt u twee filtervoorwaarden combineren.
* **[!UICONTROL Or]** laat u een alternatief aanbieden,
* **[!UICONTROL Except]** Hiermee kunt u een uitzondering definiëren.

Klik op **[!UICONTROL And]** (standaard aangeboden) en kies een optie in de vervolgkeuzelijst.

![](assets/query_condition_modif_01.png)

* **[!UICONTROL And]**: voegt een voorwaarde toe en laat overfiltreren toe.
* **[!UICONTROL Or]**: voegt een voorwaarde toe en laat overfiltreren toe.

   In het volgende voorbeeld kunt u ontvangers vinden waarvan het e-maildomein &quot;orange.co.uk&quot; OF waarvan de postcode begint met &quot;NW&quot;.

   ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Except]**: als u twee filters hebt en de eerste geen waarde retourneert, maakt dit type koppeling een uitzondering.

   In het volgende voorbeeld, willen wij ontvangers terugkeren waarvan e-maildomein &quot;orange.co.uk&quot;BEHALVE bevat als de achternaam van de ontvanger &quot;Smith&quot;is.

   ![](assets/query_condition_modif_03.png)

In dit voorbeeld ziet u een filter waarmee u het volgende kunt weergeven: ontvangers die Spaans spreken, OR zijn vrouwen met mobiele nummers, OR ontvangers zonder accountnummer, en wiens bedrijfsnaam begint met de letter &quot;N&quot;.

![](assets/query_editor_nveau_31.png)

## Prioriteitsvoorwaarden {#prioritizing-conditions}

In deze sectie wordt uitgelegd hoe u voorwaarden kunt prioriteren dankzij de blauwe pijlen op de werkbalk.

* Met de pijl die naar rechts wijst, kunt u een niveau van ronde haakjes aan het filter toevoegen.
* Met de pijl die naar links wijst, kunt u een geselecteerd haakjesniveau uit het filter verwijderen.

   ![](assets/query_condition_modif_04.png)

* Met de verticale pijlen kunt u een voorwaarde verplaatsen en zo de uitvoeringsvolgorde wijzigen.

In dit voorbeeld ziet u hoe u de pijl kunt gebruiken om een haakjesniveau te verwijderen. Begin bij de volgende filtervoorwaarde: **[!UICONTROL City equal to London OR gender equal to male and mobile not indicated OR account # starts with "95" and company name starts with "A"]**.

Plaats de cursor op de filtervoorwaarde en klik op de **[!UICONTROL Gender (@gender) equal to Male]** **[!UICONTROL Remove a parenthesis level]** pijl.

![](assets/query_editor_nveau_32.png)

De **[!UICONTROL Gender (@gender) equal to Male]** voorwaarde is uit het haakje verwijderd. Het is op hetzelfde niveau gegaan als de voorwaarde &quot;Stad is gelijk aan Londen&quot;. Deze voorwaarden zijn met elkaar verbonden (**[!UICONTROL And]**).

## Gegevens selecteren om te extraheren {#selecting-data-to-extract}

De beschikbare velden verschillen per tabel. Alle velden worden opgeslagen in een hoofdknooppunt dat bekend staat als de **[!UICONTROL Main element]**. In het volgende voorbeeld bevinden de beschikbare velden zich in de ontvangende tabel. Velden worden altijd in alfabetische volgorde weergegeven.

Het detail van het geselecteerde veld wordt onder in het venster weergegeven. Het **[!UICONTROL Email domain]** veld is bijvoorbeeld een **[!UICONTROL Calculated SQL field]** en de extensie is **[!UICONTROL (@domain)]**.

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>Gebruik het **[!UICONTROL Search]** gereedschap om een beschikbaar veld te zoeken.

Dubbelklik op een beschikbaar veld om dit toe te voegen aan de uitvoerkolommen. Aan het einde van de query maakt elk geselecteerd veld een kolom in het **[!UICONTROL Data preview]** venster.

![](assets/query_editor_nveau_01.png)

Geavanceerde velden worden niet standaard weergegeven. Klik **[!UICONTROL Display advanced fields]** in de rechterbenedenhoek van de beschikbare velden om alles weer te geven. Klik nogmaals om terug te keren naar de vorige weergave.

In de tabel voor ontvangers zijn de geavanceerde velden bijvoorbeeld **Boolean 1**, **[!UICONTROL Boolean 2]**, **[!UICONTROL Boolean 3]**, **[!UICONTROL Foreign key of "Folder" link]** enzovoort.

Het volgende voorbeeld toont de geavanceerde gebieden van de ontvankelijke lijst.

![](assets/query_editor_nveau_53.png)

De verschillende categorieën velden:

<table> 
 <thead> 
  <tr> 
   <th> Pictogram<br /> </th> 
   <th> Beschrijving<br /> </th> 
   <th> Voorbeelden<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_47.png" /> </td> 
   <td> Eenvoudig veld<br /> </td> 
   <td> E-mail, geslacht, enz.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_48.png" /> </td> 
   <td> Primaire sleutel. Met dit SQL-veld kunt u een record in een tabel identificeren.<br /> </td> 
   <td> Ontvangers van id's zijn primaire sleutels en id's zijn per definitie uniek.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> Buitenlandse sleutel. Wordt gebruikt als een koppeling naar een andere tabel.<br /> </td> 
   <td> Ontvanger buitenlandse sleutel, buitenlandse servicetoets, enz.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> Berekend veld. Dit type veld wordt op verzoek berekend met behulp van de waarden in de database.<br /> </td> 
   <td> Leeftijd, e-maildomein, enz.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_49.png" /> </td> 
   <td> Veld met lange teksten.<br /> </td> 
   <td> Opmerking, volledig adres, enzovoort.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_50.png" /> </td> 
   <td> Geïndexeerde SQL-velden. <br /> </td> 
   <td> Volledige naam, ISO-code enz. <br /> </td> 
  </tr> 
 </tbody> 
</table>

Koppeling maken naar een tabel en verzamelingselement:

<table> 
 <thead> 
  <tr> 
   <th> Pictogram<br /> </th> 
   <th> Beschrijving<br /> </th> 
   <th> Voorbeeld<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_51.png" /> </td> 
   <td> Met name koppelingen naar een tabel. Deze komen overeen met 1-1 type associaties. Een instantie van de brontabel kan slechts één instantie van de doeltabel bevatten. Er kan bijvoorbeeld slechts één ontvanger aan een land zijn gekoppeld.<br /> </td> 
   <td> Map, provincie, land, enz. <br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> Het element van de inzameling op een specifieke lijst. Deze komen overeen met 1-N type associaties. Eén exemplaar van de brontabel valt samen met meerdere exemplaren van de doeltabel, maar één instantie van de doeltabel kan slechts één instantie van de brontabel bevatten. Eén ontvanger kan bijvoorbeeld een abonnement nemen op 'n'-abonnementbrieven.<br /> </td> 
   <td> Abonnementen, lijsten, uitsluitingslogboeken, enz.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Gebruik de **[!UICONTROL Add]** knop (boven de zijpictogrambalk) om een uitvoerkolom toe te voegen waarin u de expressie wilt bewerken. Raadpleeg [Building-expressies](#building-expressions)voor meer informatie over het bewerken van een expressie.
>* Verwijder een uitvoerkolom door op rood &#39;x&#39; te klikken (**Verwijderen**).
>* Wijzig de volgorde van de uitvoerkolommen met de pijlen.
>* Het **[!UICONTROL Distribution of values]** dient als een manier om de verdeling van de waarden van het geselecteerde veld te bekijken (bijvoorbeeld de distributies die gekoppeld zijn aan de ontvangende steden, de ontvangende talen, enz.).


## Berekende velden maken {#creating-calculated-fields}

Voeg zo nodig een kolom toe tijdens het opmaken van gegevens. Een berekend veld voegt een kolom toe aan de sectie met de voorvertoning van gegevens. Klik **[!UICONTROL Add a calculated field]**.

![](assets/query_editor_nveau_43.png)

Er zijn vier typen berekende velden:

* **[!UICONTROL Fixed string]**: Hiermee kunt u een tekenreeks met tekens toevoegen.

   ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL String with JavaScript tags]**: Met de waarde van het berekende veld wordt een reeks tekens en JavaScript-instructies gecombineerd.

   ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL JavaScript expression]**: De waarde van het berekende veld is het resultaat van een JavaScript-functieevaluatie. De geretourneerde waarde kan worden getypt (getal, datum, enz.).

   ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Enumerations]**: Met dit type veld kunt u de inhoud van een van de uitvoerkolommen in een nieuwe kolom gebruiken of wijzigen.

   Het is mogelijk om de bronwaarde van een kolom te gebruiken en het een bestemmingswaarde te geven. Deze bestemmingswaarde zal in de nieuwe outputkolom worden getoond.

   Een voorbeeld van het toevoegen van berekend gebiedstype **[!UICONTROL Enumerations]** is beschikbaar, verwijs naar [deze sectie](../../workflow/using/adding-enumeration-type-calculated-field.md).

   ![](assets/query_editor_nveau_63.png)

   Het berekende **[!UICONTROL Enumerations]** type veld kan vier voorwaarden bevatten:

   * **[!UICONTROL Keep the source value]** Hiermee herstelt u de bronwaarde in het doel zonder deze te wijzigen.
   * **[!UICONTROL Use the following value]** Hiermee kunt u een standaarddoelwaarde voor niet-gedefinieerde bronwaarden invoeren.
   * **[!UICONTROL Generate a warning and continue]** waarschuwt de gebruiker dat de bronwaarde niet kan worden gewijzigd.
   * **[!UICONTROL Generate an error and reject the line]** voorkomt dat de regel wordt berekend en geïmporteerd.

Klik op het veld **[!UICONTROL Detail of calculated field]** om de details van het ingevoegde veld weer te geven.

Klik op het **[!UICONTROL Remove the calculated field]** kruisje om dit berekende veld te verwijderen.

![](assets/query_editor_nveau_58.png)

## Expressies maken {#building-expressions}

Met het gereedschap voor het bewerken van expressies kunt u aggregaten berekenen, functies genereren of een formule bewerken met behulp van een expressie.

In het volgende voorbeeld ziet u hoe u een telling op een primaire toets uitvoert.

Voer de volgende stappen uit:

1. Klik **[!UICONTROL Add]** in het **[!UICONTROL Data to extract]** venster. Selecteer in het **[!UICONTROL Formula type]** venster een type formule om de expressie in te voeren.

   Er zijn verschillende typen beschikbare formules: **[!UICONTROL Field only]**, **[!UICONTROL Aggregate]**, **[!UICONTROL Expression]**.

   Selecteer **[!UICONTROL Process on an aggregate function]**, en **[!UICONTROL Count]**. Klik **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_54.png)

1. De primaire sleutel wordt berekend.

   ![](assets/query_editor_nveau_88.png)

Hier volgt een gedetailleerde weergave van de opties die beschikbaar zijn in het **[!UICONTROL Formula types]** venster:

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Field only]** Hiermee kunt u terugkeren naar het **[!UICONTROL Field to select]** venster.
1. **[!UICONTROL Aggregate (Process on an aggregate function)]**. Hier volgen enkele voorbeelden van het gebruik van aggregaten:

   * **[!UICONTROL Count]** Hiermee kunt u een aantal primaire sleutels uitvoeren.
   * **[!UICONTROL Sum]** Hiermee kunt u alle aankopen optellen die een klant gedurende een jaar heeft gedaan.
   * **[!UICONTROL Maximum value]** laat u de klanten vinden die de meeste &quot; n &quot; producten hebben gekocht.
   * **[!UICONTROL Minimum value]** Hiermee kunt u klanten doorzoeken en zoeken naar klanten die zich onlangs op een aanbieding hebben geabonneerd.
   * **[!UICONTROL Average]**. Met deze functie kunt u de gemiddelde leeftijd van de ontvangers berekenen.

      Met het **[!UICONTROL Distinct]** vak kunt u unieke en niet-nulwaarden van een kolom herstellen. Bijvoorbeeld, kunt u alle het volgen logboeken van een ontvanger terugkrijgen en deze het volgen logboeken worden veranderd in waarde 1 aangezien zij allen de zelfde ontvanger aangaan.

1. **[!UICONTROL Expression]** opent het **[!UICONTROL Edit the expression]** venster. Zo kunt u telefoonnummers met te veel cijfers detecteren. Dit kunnen invoerfouten zijn.

   ![](assets/query_editor_nveau_71.png)

   Zie [Lijst met functies](#list-of-functions)voor een lijst met alle beschikbare functies.

## Lijst met functies {#list-of-functions}

Als u een **[!UICONTROL Expression]** typeformule kiest, wordt u doorgestuurd naar het venster &quot;De expressie bewerken&quot;. Verschillende categorieën functies kunnen aan de beschikbare velden worden gekoppeld: **[!UICONTROL Aggregates]**, **[!UICONTROL String]**, **[!UICONTROL Date]**, **[!UICONTROL Numerical]**, **[!UICONTROL Currency]**, **[!UICONTROL Geomarketing]**, **[!UICONTROL Windowing function]** en **[!UICONTROL Others]**.

De expressie-editor ziet er als volgt uit:

![](assets/s_ncs_user_filter_define_expression.png)

Hiermee kunt u velden in de databasetabellen selecteren en er geavanceerde functies aan toevoegen. De volgende functies zijn beschikbaar:

**Aggregaten**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong>Syntaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Avg</strong><br /> </td> 
   <td> Hiermee wordt het gemiddelde van een kolom met getaltypen geretourneerd<br /> </td> 
   <td> Avg(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Aantal</strong><br /> </td> 
   <td> Telt de waarden in een kolom die niet 'null' zijn<br /> </td> 
   <td> Count(&lt;value&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>CountAll</strong><br /> </td> 
   <td> Telt de geretourneerde waarden (alle velden)<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Aftelbaar</strong><br /> </td> 
   <td> Telt de verschillende waarden van een kolom die niet 'null' zijn<br /> </td> 
   <td> Countdifferent(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Max</strong><br /> </td> 
   <td> Retourneert de maximumwaarde van een getal, tekenreeks of datumtekstkolom<br /> </td> 
   <td> Max(&lt;value&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Min</strong><br /> </td> 
   <td> Hiermee wordt de minimumwaarde van een kolom met een getal, tekenreeks of datumtype geretourneerd<br /> </td> 
   <td> Min(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>StdDev</strong><br /> </td> 
   <td> Hiermee wordt de standaardafwijking van een getal, tekenreeks of datumkolom geretourneerd<br /> </td> 
   <td> StdDev(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Som</strong><br /> </td> 
   <td> Hiermee wordt de som van de waarden van een getal, tekenreeks of kolom met het gegevenstype geretourneerd<br /> </td> 
   <td> Sum(&lt;value&gt;)<br /></td> 
  </tr> 
 </tbody> 
</table>

**String**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong>Syntaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull2</strong><br /> </td> 
   <td> Geeft aan of alle parameters niet null en niet leeg zijn<br /> </td> 
   <td> AllNonNull2(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull3</strong><br /> </td> 
   <td> Geeft aan of alle parameters niet null en niet leeg zijn<br /> </td> 
   <td> AllNonNull3(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ascii</strong><br /> </td> 
   <td> Retourneert de ASCII-waarde van het eerste teken in de tekenreeks.<br /> </td> 
   <td> Ascii(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Char</strong><br /> </td> 
   <td> Hiermee wordt het teken geretourneerd dat overeenkomt met de ASCII-code 'n'<br /> </td> 
   <td> Char(&lt;number&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> Retourneert de positie van tekenreeks 2 in tekenreeks 1.<br /> </td> 
   <td> Charindex(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> Retourneert de nde (van 1 tot en met n) regel van de tekenreeks<br /> </td> 
   <td> GetLine(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> Retourneert de derde parameter als de eerste twee parameters gelijk zijn. Indien niet, wordt de laatste parameter geretourneerd<br /> </td> 
   <td> IfEquals(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> Geeft aan of het als parameter doorgegeven memo null is<br /> </td> 
   <td> IsMemoNull(&lt;memo&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords</strong><br /> </td> 
   <td> Voegt de doorgegeven tekenreeksen samen als parameters. Voegt indien nodig spaties tussen de tekenreeksen toe.<br /> </td> 
   <td> JuxtWords(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords3</strong><br /> </td> 
   <td> Voegt de doorgegeven tekenreeksen samen als parameters. Voegt indien nodig spaties tussen de tekenreeksen toe<br /> </td> 
   <td> JuxtWords3(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>LPad</strong><br /> </td> 
   <td> Hiermee wordt de voltooide tekenreeks links geretourneerd<br /> </td> 
   <td> LPad(&lt;string&gt;, &lt;number&gt;, &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Links</strong><br /> </td> 
   <td> Retourneert de eerste n tekens van de tekenreeks<br /> </td> 
   <td> Left(&lt;string&gt;, &lt;number&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Lengte</strong><br /> </td> 
   <td> Retourneert de lengte van de tekenreeks<br /> </td> 
   <td> Lengte (&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Onder</strong><br /> </td> 
   <td> Hiermee wordt de tekenreeks in kleine letters geretourneerd<br /> </td> 
   <td> Lower(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ltrim</strong><br /> </td> 
   <td> Hiermee worden spaties links van de tekenreeks verwijderd<br /> </td> 
   <td> Ltrim(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Md5Digest</strong><br /> </td> 
   <td> Retourneert een hexadecimale representatie van de toets MD5 van een tekenreeks<br /> </td> 
   <td> Md5Digest(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>MemoContains</strong><br /> </td> 
   <td> Hiermee wordt opgegeven of het memo de tekenreeks bevat die als parameter is doorgegeven<br /> </td> 
   <td> MemoContains(&lt;memo&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> Hiermee wordt de voltooide tekenreeks aan de rechterkant geretourneerd<br /> </td> 
   <td> RPad(&lt;string&gt;, &lt;number&gt;, &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Rechts</strong><br /> </td> 
   <td> Retourneert de laatste n tekens van de tekenreeks<br /> </td> 
   <td> Right(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> Hiermee worden spaties rechts van de tekenreeks verwijderd<br /> </td> 
   <td> Rtrim(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Slim</strong><br /> </td> 
   <td> Retourneert de tekenreeks met de eerste letter van elk woord in hoofdletters<br /> </td> 
   <td> Smart(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Subtekenreeks</strong><br /> </td> 
   <td> Hiermee wordt de subtekenreeks opgehaald die begint op teken n1 van de tekenreeks en lengte n2<br /> </td> 
   <td> Substring(&lt;string&gt;, &lt;offset&gt;, &lt;length&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> Zet het getal om in een tekenreeks<br /> </td> 
   <td> ToString(&lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Bovenkant</strong><br /> </td> 
   <td> Hiermee wordt de tekenreeks in hoofdletters geretourneerd<br /> </td> 
   <td> Upper(&lt;string&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> Retourneert de externe sleutel van een koppeling die als een parameter is doorgegeven als de andere twee parameters gelijk zijn<br /> </td> 
   <td> VirtualLink(&lt;number&gt;, &lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> Retourneert de externe (tekst) sleutel van een koppeling die als parameter wordt doorgegeven als de andere twee parameters gelijk zijn<br /> </td> 
   <td> VirtualLinkStr(&lt;string&gt;, &lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>dataLength</strong><br /> </td> 
   <td> Hiermee wordt de tekenreeksgrootte geretourneerd<br /> </td> 
   <td> dataLength(&lt;string&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Datum**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong>Syntaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AddDays</strong><br /> </td> 
   <td> Hiermee voegt u een aantal dagen toe aan een datum<br /> </td> 
   <td> AddDays(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> Hiermee voegt u een aantal uren toe aan een datum<br /> </td> 
   <td> AddHours(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> Hiermee wordt een aantal minuten toegevoegd aan een datum<br /> </td> 
   <td> AddMinutes(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> Hiermee voegt u een aantal maanden toe aan een datum<br /> </td> 
   <td> AddMonths(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> Hiermee wordt een aantal seconden toegevoegd aan een datum<br /> </td> 
   <td> AddSeconds(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddYaren</strong><br /> </td> 
   <td> Hiermee wordt een aantal jaren toegevoegd aan een datum<br /> </td> 
   <td> AddYear(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DateOnly</strong><br /> </td> 
   <td> Retourneert alleen de datum (met tijd om 00:00)*<br /> </td> 
   <td> DateOnly(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Dag</strong><br /> </td> 
   <td> Retourneert het getal dat de dag van de datum vertegenwoordigt<br /> </td> 
   <td> Dag (&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DayOfYear</strong><br /> </td> 
   <td> Retourneert het getal van de dag in het jaar van de datum<br /> </td> 
   <td> DayOfYear(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> Retourneert de datum die overeenkomt met de huidige datum min n dagen<br /> </td> 
   <td> DaysAgo(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> Retourneert de datum (geheel getal jjjjmmdd) die overeenkomt met de huidige datum min n dagen<br /> </td> 
   <td> DaysAgoInt(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> Aantal dagen tussen twee datums<br /> </td> 
   <td> DaysDiff(&lt;einddatum&gt;, &lt;begindatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> Retourneert de leeftijd in dagen van een datum<br /> </td> 
   <td> DaysOld(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> Hiermee wordt de huidige systeemdatum van de server geretourneerd<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Uur</strong><br /> </td> 
   <td> Retourneert het uur van de datum<br /> </td> 
   <td> Uur(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>HoursDiff</strong><br /> </td> 
   <td> Retourneert het aantal uren tussen twee datums<br /> </td> 
   <td> HoursDiff(&lt;einddatum&gt;, &lt;begindatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Minuut</strong><br /> </td> 
   <td> Retourneert de minuten van de datum<br /> </td> 
   <td> Minuut(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> Retourneert het aantal minuten tussen twee datums<br /> </td> 
   <td> MinutesDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Maand</strong><br /> </td> 
   <td> Retourneert het getal dat de maand van de datum vertegenwoordigt<br /> </td> 
   <td> Maand (&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsAgo</strong><br /> </td> 
   <td> Retourneert de datum die overeenkomt met de huidige datum min n maanden<br /> </td> 
   <td> MonthsAgo(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> Retourneert het aantal maanden tussen twee datums<br /> </td> 
   <td> MonthsDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> Retourneert de leeftijd in maanden van een datum<br /> </td> 
   <td> MonthsOld(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Seconde</strong><br /> </td> 
   <td> Hiermee worden de seconden van de datum geretourneerd<br /> </td> 
   <td> Second(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> Retourneert het aantal seconden tussen twee datums<br /> </td> 
   <td> SecondsDiff(&lt;einddatum&gt;, &lt;begindatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Subdagen</strong><br /> </td> 
   <td> Hiermee trekt u een aantal dagen van een datum af<br /> </td> 
   <td> SubDays(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubHours</strong><br /> </td> 
   <td> Hiermee wordt een aantal uren van een datum afgetrokken<br /> </td> 
   <td> SubHours(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMinutes</strong><br /> </td> 
   <td> Hiermee wordt een aantal minuten van een datum afgetrokken<br /> </td> 
   <td> SubMinutes(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Submaanden</strong><br /> </td> 
   <td> Hiermee trekt u een aantal maanden van een datum af<br /> </td> 
   <td> SubMonths(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubSeconds</strong><br /> </td> 
   <td> Trekt een aantal seconden van een datum af<br /> </td> 
   <td> SubSeconds(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Subjaren</strong><br /> </td> 
   <td> Hiermee trekt u een aantal jaren van een datum af<br /> </td> 
   <td> Subjaren(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> Converteert een datum + tijd als datum<br /> </td> 
   <td> TotDatum (&lt;datum + tijd&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> Zet een tekenreeks om in een datum + tijd<br /> </td> 
   <td> ToDateTime(&lt;string&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> Rondt een datum+tijd aan het dichtstbijzijnde tweede<br /> </td> 
   <td> TruncDate(@lastModified, &lt;aantal seconden&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> Rondt een datum + tijd aan een bepaalde precisie die in seconden wordt uitgedrukt<br /> </td> 
   <td> TruncDateTZ(&lt;date&gt;, &lt;number of seconds&gt;, &lt;time zone&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> Rondt een datum af op het kwartaal<br /> </td> 
   <td> TruncQuarter(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> Rondt het tijdsdeel af tot de dichtstbijzijnde seconde<br /> </td> 
   <td> TruncTim(e&lt;date&gt;, &lt;number of seconds&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Rondt een datum af naar de week<br /> </td> 
   <td> TruncWeek(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> Rondt een datum + tijd tot 1 januari van het jaar<br /> </td> 
   <td> TruncYear(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Retourneert het getal dat de dag in de week van de datum vertegenwoordigt<br /> </td> 
   <td> WeekDay(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Jaar</strong><br /> </td> 
   <td> Retourneert het getal dat het jaar van de datum vertegenwoordigt<br /> </td> 
   <td> Jaar (&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Jaar en maand</strong><br /> </td> 
   <td> Retourneert het getal dat het jaar en de maand van de datum vertegenwoordigt.<br /> </td> 
   <td> YearAndMonth(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearDiff</strong><br /> </td> 
   <td> Retourneert het aantal jaren tussen de twee datums<br /> </td> 
   <td> YarenDiff(&lt;einddatum&gt;, &lt;begindatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>JarenOud</strong><br /> </td> 
   <td> Retourneert de leeftijd in jaren van een datum<br /> </td> 
   <td> YearOld(&lt;date&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Merk op dat de functie van **Dateonly** rekening houdt met timezone van de server, niet de exploitant.

**Numeriek**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong>Syntaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Abs</strong><br /> </td> 
   <td> Retourneert de absolute waarde van een getal<br /> </td> 
   <td> Abs(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> Retourneert het laagste gehele getal dat groter is dan of gelijk is aan een getal<br /> </td> 
   <td> Ceil(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> Retourneert het grootste gehele getal dat groter is dan of gelijk is aan een getal<br /> </td> 
   <td> Floor(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Groter</strong><br /> </td> 
   <td> Retourneert de grootste van twee getallen<br /> </td> 
   <td> Greatest(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Minste</strong><br /> </td> 
   <td> Retourneert het laagste van twee getallen<br /> </td> 
   <td> Least(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> Retourneert de rest van de integer-deling van n1 door n2<br /> </td> 
   <td> Mod(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Percentage</strong><br /> </td> 
   <td> Retourneert de verhouding van twee getallen uitgedrukt als een percentage<br /> </td> 
   <td> Percentage (&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Willekeurig</strong><br /> </td> 
   <td> Hiermee wordt de willekeurige waarde geretourneerd<br /> </td> 
   <td> Random()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rond</strong><br /> </td> 
   <td> Rondt een getal af naar n decimalen<br /> </td> 
   <td> Round(&lt;number&gt;, &lt;number of decimal&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ondertekenen</strong><br /> </td> 
   <td> Hiermee wordt het teken van het getal geretourneerd<br /> </td> 
   <td> Sign(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> Hiermee wordt een geheel getal omgezet in een zwevende waarde<br /> </td> 
   <td> ToDouble(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> Zet een float om in een 64-bits geheel getal<br /> </td> 
   <td> ToInt64(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> Hiermee wordt een zwevende waarde omgezet in een geheel getal<br /> </td> 
   <td> ToInteger(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> Aantal decimalen n1 tot n2<br /> </td> 
   <td> Trunc(&lt;n1&gt;, &lt;n2&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

1. Valuta

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong>Syntaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ConvertCurrency</strong><br /> </td> 
   <td> Hiermee wordt een bedrag in een bronvaluta omgezet in een bedrag in een doelvaluta<br /> </td> 
   <td> ConvertCurrency(&lt;bedrag&gt;, &lt;bronvaluta&gt;, &lt;doelvaluta&gt;, &lt;conversiedatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>FormatCurrency</strong><br /> </td> 
   <td> Maakt het weergegeven bedrag op basis van de geselecteerde valutainstellingen op<br /> </td> 
   <td> FormatCurrency(&lt;bedrag&gt;, &lt;currency&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Geomarketing**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong>Syntaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Afstand</strong><br /> </td> 
   <td> Retourneert de afstand tussen twee punten die worden gedefinieerd door hun lengte en breedte, uitgedrukt in graden.<br /> </td> 
   <td> Afstand (&lt;Lengtegraad A&gt;, &lt;Latitude A&gt;, &lt;Lengtegraad B&gt;, &lt;Latitude B&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Overige**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong>Syntaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Case</strong><br /> </td> 
   <td> Retourneert waarde 1 als de voorwaarde true is. Zo niet, dan wordt waarde 2 geretourneerd.<br /> </td> 
   <td> Case(When(&lt;condition&gt;, &lt;value 1&gt;), else(&lt;value 2&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> Hiermee verwijdert u de markering in de waarde<br /> </td> 
   <td> ClearBit(&lt;identifier&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Coalesce</strong><br /> </td> 
   <td> Retourneert waarde 2 als waarde 1 nul of null is, anders wordt waarde 1 geretourneerd<br /> </td> 
   <td> Coalesce(&lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Decode</strong><br /> </td> 
   <td> Retourneert waarde 3 als waarde 1 = waarde 2. Indien geen waarde 4 wordt geretourneerd.<br /> </td> 
   <td> Decode(&lt;value 1&gt;, &lt;value 2&gt;, &lt;value 3&gt;, &lt;value 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> Retourneert waarde 1 (mag alleen worden gebruikt als parameter van de case-functie)<br /> </td> 
   <td> else(&lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> Extraheert het domein van een e-mailadres<br /> </td> 
   <td> GetEmailDomain(&lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> Hiermee wordt de URL van de server van de spiegel opgehaald<br /> </td> 
   <td> GetMirrorURL(&lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Iif</strong><br /> </td> 
   <td> Retourneert waarde 1 als de expressie true is. Zo niet, retourneert waarde 2<br /> </td> 
   <td> Iif(&lt;condition&gt;, &lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> Geeft aan of de markering zich in de waarde bevindt<br /> </td> 
   <td> IsBitSet(&lt;identifier&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> Retourneert waarde 2 als tekenreeks 1 leeg is. Retourneert anders waarde 3<br /> </td> 
   <td> IsEmptyString(&lt;value 1&gt;, &lt;value 2&gt;, &lt;value 3&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> Retourneert de lege tekenreeks als het argument NULL is<br /> </td> 
   <td> NoNull(&lt;value&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> Retourneert het regelnummer<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> Hiermee wordt de vlag in de waarde geforceerd<br /> </td> 
   <td> SetBit(&lt;identifier&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> Hiermee wordt een getal omgezet in een Booleaanse waarde<br /> </td> 
   <td> ToBoolean(&lt;number&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>Wanneer</strong><br /> </td> 
   <td> Retourneert waarde 1 als de expressie true is. Zo niet, dan wordt waarde 2 geretourneerd (mag alleen worden gebruikt als parameter van de case-functie)<br /> </td> 
   <td> When(&lt;condition&gt;, &lt;value 1&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Vensterfuncties**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
   <td> <strong>Syntaxis</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Desc</strong><br /> </td> 
   <td> Hiermee wordt een aflopende sortering toegepast<br /> </td> 
   <td> Desc(&lt;value 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> Hiermee wordt het resultaat binnen de partitie gesorteerd<br /> </td> 
   <td> OrderBy(&lt;value 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>PartitionBy</strong><br /> </td> 
   <td> Verdeelt het resultaat van een vraag op een lijst<br /> </td> 
   <td> PartitionBy(&lt;value 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> Hiermee genereert u een regelnummer op basis van de tabelpartitie en een sorteervolgorde.<br /> </td> 
   <td> RowNum(PartitionBy(&lt;value 1&gt;), OrderBy(&lt;value 1&gt;))<br /> </td> 
  </tr> 
 </tbody> 
</table>