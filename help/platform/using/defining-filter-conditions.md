---
product: campaign
title: Filtervoorwaarden definiëren
description: Filtervoorwaarden definiëren
feature: Query Editor
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: platform
content-type: reference
topic-tags: creating-queries
exl-id: b62e23e5-f1b7-44c4-82d9-95c6b3240352
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '3307'
ht-degree: 34%

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
   <td> <span class="uicontrol">Equal to</span> <br /> </td> 
   <td> Retourneert een resultaat dat identiek is aan de gegevens die zijn ingevoerd in de tweede kolom Waarde.<br /> </td> 
   <td> <strong>Achternaam (@lastName) is gelijk aan 'Jones'</strong>, retourneert alleen ontvangers met als achternaam Jones.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Greater than</span> <br /> </td> 
   <td> Retourneert een waarde die groter is dan de ingevoerde waarde.<br /> </td> 
   <td> <strong>Leeftijd (@leeftijd) groter dan 50</strong>alle waarden boven "50", d.w.z. "51", "52" enz.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Less than</span> <br /> </td> 
   <td> Retourneert een waarde die kleiner is dan de ingevoerde waarde.<br /> </td> 
   <td> <strong>Aanmaakdatum (@created) vóór 'DaysAgo(100)'</strong>, worden alle ontvangers geretourneerd die minder dan 100 dagen geleden zijn gemaakt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Greater than or equal to</span> <br /> </td> 
   <td> Retourneert alle waarden die gelijk zijn aan of groter zijn dan de ingevoerde waarde.<br /> </td> 
   <td> <strong>Leeftijd (@leeftijd) groter dan of gelijk aan '30'</strong>, worden alle ontvangers vanaf 30 jaar geretourneerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Less than or equal to</span> <br /> </td> 
   <td> Retourneert alle waarden die gelijk zijn aan of lager zijn dan de ingevoerde waarde.<br /> </td> 
   <td> <strong>Leeftijd (@leeftijd) kleiner dan of gelijk aan '60'</strong>, worden alle ontvangers vanaf 60 jaar geretourneerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Niet gelijk aan</span> <br /> </td> 
   <td> Retourneert alle waarden die niet identiek zijn aan de ingevoerde waarde.<br /> </td> 
   <td> <strong>Taal (@taal) gelijk aan 'Engels'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Begint met</span> <br /> </td> 
   <td> Retourneert de resultaten die beginnen met de ingevoerde waarde.<br /> </td> 
   <td> <strong>Account # (@account) begint met '32010'.</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Begint niet met</span> <br /> </td> 
   <td> Retourneert de resultaten die niet beginnen met de ingevoerde waarde.<br /> </td> 
   <td> <strong>Account # (@account) begint niet met '20'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Contains</span> <br /> </td> 
   <td> Retourneert de resultaten die ten minste de ingevoerde waarde bevatten.<br /> </td> 
   <td> <strong>E-maildomein (@domein) bevat 'mail'</strong>, worden alle domeinnamen geretourneerd die 'mail' bevatten. Het domein 'gmail.com' wordt dus ook geretourneerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bevat niet</span> <br /> </td> 
   <td> Retourneert resultaten die niet de ingevoerde waarde bevatten.<br /> </td> 
   <td> <strong>E-maildomein (@domain) bevat geen 'vo'</strong>. In dit geval worden domeinnamen die 'vo' bevatten, niet geretourneerd. De domeinnaam voila.fr wordt niet weergegeven in de resultaten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Like</span> <br /> </td> 
   <td> <span class="uicontrol">Like</span> lijkt heel sterk op de operator <span class="uicontrol">Contains</span>. Hiermee kunt u een <span class="uicontrol">%</span> jokerteken in de waarde.<br /> </td> 
   <td> <strong>Achternaam (@lastName) zoals 'Jon%s'</strong>. Hier wordt het jokerteken gebruikt als een joker om de naam Jones te vinden, mocht de operator de ontbrekende letter tussen de 'n' en 's' vergeten hebben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Not like</span> <br /> </td> 
   <td> Is gelijkaardig aan <span class="uicontrol">leuk</span> . Hiermee kunt u de ingevoerde waarde niet herstellen. Ook hier moet de ingevoerde waarde het jokerteken <span class="uicontrol">%</span> bevatten.<br /> </td> 
   <td> <strong>Achternaam (@lastName) is niet zoals 'Smi%h'</strong>. Hier worden de ontvangers met de achternaam 'Smi%h' niet geretourneerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is empty</span> <br /> </td> 
   <td> In dit geval komt het resultaat dat we zoeken overeen met een lege waarde in de tweede kolom Waarde.<br /> </td> 
   <td> <strong>Mobiel (@mobilePhone) is leeg</strong> retourneert alle ontvangers die geen mobiel nummer hebben.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is niet leeg</span> <br /> </td> 
   <td> Werkt in omgekeerde volgorde naar de <span class="uicontrol">Is leeg</span> operator. Het is niet nodig gegevens in te voeren in de tweede kolom Waarde.<br /> </td> 
   <td> <strong>E-mail (@email) is niet leeg</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is opgenomen in</span> <br /> </td> 
   <td> Retourneert resultaten die zijn opgenomen in de aangegeven waarden. Deze waarden moeten door een komma worden gescheiden.<br /> </td> 
   <td> <strong>Geboortedatum (@geboortedatum) is opgenomen in "10-12-1979,12-10-1984"</strong>, worden de ontvangers tussen deze datums geretourneerd. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is niet opgenomen in</span> <br /> </td> 
   <td> Werkt net als de <span class="uicontrol">Is opgenomen in</span> operator. Hier, willen wij ontvangers uitsluiten die op de ingegane waarden worden gebaseerd.<br /> </td> 
   <td> <strong>Geboortedatum (@geboortedatum) is niet opgenomen in "10-12-1979,12-10-1984"</strong>. Anders dan in het vorige voorbeeld worden ontvangers die binnen deze datums geboren zijn, niet geretourneerd.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## GEBRUIK EN, OF, BEHALVE {#using-and--or--except}

Voor vragen die verscheidene het filtreren voorwaarden gebruiken, moet u verbindingen tussen de voorwaarden bepalen. Er zijn drie mogelijke koppelingen:

* **[!UICONTROL And]** Hiermee kunt u twee filtervoorwaarden combineren.
* **[!UICONTROL Or]** laat u een alternatief aanbieden,
* **[!UICONTROL Except]** Hiermee kunt u een uitzondering definiëren.

Klikken **[!UICONTROL And]** (standaard beschikbaar) en kies een optie in de vervolgkeuzelijst.

![](assets/query_condition_modif_01.png)

* **[!UICONTROL And]**: voegt een voorwaarde toe en schakelt overfiltering in.
* **[!UICONTROL Or]**: voegt een voorwaarde toe en schakelt overfiltering in.

  In het volgende voorbeeld kunt u ontvangers vinden waarvan het e-maildomein &quot;orange.co.uk&quot; OF waarvan de postcode begint met &quot;NW&quot;.

  ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Except]**: als u twee filters hebt en de eerste geen waarde retourneert, maakt dit type koppeling een uitzondering.

  In het volgende voorbeeld, willen wij ontvangers terugkeren waarvan e-maildomein &quot;orange.co.uk&quot;BEHALVE bevat als de achternaam van de ontvanger &quot;Smith&quot;is.

  ![](assets/query_condition_modif_03.png)

In dit voorbeeld wordt een filter weergegeven waarmee u het volgende kunt weergeven: ontvangers die Spaans spreken, OF vrouwen met mobiele nummers zijn, OF ontvangers zonder accountnummer waarvan de naam begint met de letter &quot;N&quot;.

![](assets/query_editor_nveau_31.png)

## Prioriteitsvoorwaarden {#prioritizing-conditions}

In deze sectie wordt uitgelegd hoe u voorwaarden kunt prioriteren dankzij de blauwe pijlen op de werkbalk.

* Met de pijl die naar rechts wijst, kunt u een niveau van ronde haakjes aan het filter toevoegen.
* Met de pijl die naar links wijst, kunt u een geselecteerd haakjesniveau uit het filter verwijderen.

  ![](assets/query_condition_modif_04.png)

* Met de verticale pijlen kunt u een voorwaarde verplaatsen en zo de uitvoeringsvolgorde wijzigen.

In dit voorbeeld ziet u hoe u de pijl kunt gebruiken om een haakjesniveau te verwijderen. Begin bij de volgende filtervoorwaarde: **[!UICONTROL City equal to London OR gender equal to male and mobile not indicated OR account # starts with "95" and company name starts with "A"]**.

Plaats de cursor op de knop **[!UICONTROL Gender (@gender) equal to Male]** filtervoorwaarde en klik op **[!UICONTROL Remove a parenthesis level]** pijl.

![](assets/query_editor_nveau_32.png)

De **[!UICONTROL Gender (@gender) equal to Male]** voorwaarde is uit het haakje verwijderd. Het is op hetzelfde niveau gegaan als de voorwaarde &quot;Stad is gelijk aan Londen&quot;. Deze voorwaarden houden verband met elkaar (**[!UICONTROL And]**).

## Gegevens selecteren om te extraheren {#selecting-data-to-extract}

De beschikbare velden verschillen per tabel. Alle velden worden opgeslagen in een hoofdknooppunt, bekend als de **[!UICONTROL Main element]**. In het volgende voorbeeld bevinden de beschikbare velden zich in de ontvangende tabel. Velden worden altijd in alfabetische volgorde weergegeven.

Het detail van het geselecteerde veld wordt onder in het venster weergegeven. Bijvoorbeeld de **[!UICONTROL Email domain]** field is a **[!UICONTROL Calculated SQL field]** en de uitbreiding ervan **[!UICONTROL (@domain)]**.

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>Gebruik de **[!UICONTROL Search]** om een beschikbaar veld te zoeken.

Dubbelklik op een beschikbaar veld om dit toe te voegen aan de uitvoerkolommen. Aan het einde van de query maakt elk geselecteerd veld een kolom in het dialoogvenster **[!UICONTROL Data preview]** venster.

![](assets/query_editor_nveau_01.png)

Geavanceerde velden worden niet standaard weergegeven. Klikken **[!UICONTROL Display advanced fields]** in de rechterbenedenhoek van de beschikbare velden om alles weer te geven. Klik nogmaals om terug te keren naar de vorige weergave.

In de tabel met ontvangers zijn de geavanceerde velden bijvoorbeeld **Boolean 1**, **[!UICONTROL Boolean 2]**, **[!UICONTROL Boolean 3]**, **[!UICONTROL Foreign key of "Folder" link]**, enz.

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
   <td> Ontvanger buitenlandse sleutel, buitenlandse servicesleutel, enz.<br /> </td> 
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
>* Gebruik de **[!UICONTROL Add]** (boven de zijpictogrambalk) om een uitvoerkolom toe te voegen waarin u de expressie wilt bewerken. Raadpleeg voor meer informatie over het bewerken van een expressie [deze sectie](#building-expressions).
>* Een uitvoerkolom verwijderen door op rood &#39;x&#39; te klikken (**Verwijderen**).
>* Wijzig de volgorde van de uitvoerkolommen met de pijlen.
>* De **[!UICONTROL Distribution of values]** dient als een manier om de verdeling van de waarden van het geselecteerde veld te bekijken (bijvoorbeeld de distributies die gekoppeld zijn aan de ontvangende steden, de ontvangende talen, enz.).

## Berekende velden maken {#creating-calculated-fields}

Voeg zo nodig een kolom toe tijdens het opmaken van gegevens. Een berekend veld voegt een kolom toe aan de sectie met de voorvertoning van gegevens. Klik op **[!UICONTROL Add a calculated field]**.

![](assets/query_editor_nveau_43.png)

Er zijn vier typen berekende velden:

* **[!UICONTROL Fixed string]**: hiermee kunt u een tekenreeks met tekens toevoegen.

  ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL String with JavaScript tags]**: de waarde van het berekende veld combineert een tekenreeks met tekens en JavaScript-instructies.

  ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL JavaScript expression]**: de waarde van het berekende veld is het resultaat van een JavaScript-functieevaluatie. De geretourneerde waarde kan worden getypt (getal, datum, enz.).

  ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Enumerations]**: Met dit type veld kunt u de inhoud van een van de uitvoerkolommen in een nieuwe kolom gebruiken of wijzigen.

  Het is mogelijk om de bronwaarde van een kolom te gebruiken en het een bestemmingswaarde te geven. Deze bestemmingswaarde zal in de nieuwe outputkolom worden getoond.

  Een voorbeeld van het toevoegen van berekend veldtype **[!UICONTROL Enumerations]** is beschikbaar, raadpleeg [deze sectie](../../workflow/using/adding-enumeration-type-calculated-field.md).

  ![](assets/query_editor_nveau_63.png)

  De **[!UICONTROL Enumerations]** het berekende tekstveld kan vier voorwaarden bevatten:

   * **[!UICONTROL Keep the source value]** Hiermee herstelt u de bronwaarde in het doel zonder deze te wijzigen.
   * **[!UICONTROL Use the following value]** Hiermee kunt u een standaarddoelwaarde voor niet-gedefinieerde bronwaarden invoeren.
   * **[!UICONTROL Generate a warning and continue]** waarschuwt de gebruiker dat de bronwaarde niet kan worden gewijzigd.
   * **[!UICONTROL Generate an error and reject the line]** voorkomt dat de regel wordt berekend en geïmporteerd.

Klik op de knop **[!UICONTROL Detail of calculated field]** om de details van het ingevoegde veld weer te geven.

Als u dit berekende veld wilt verwijderen, klikt u op de knop **[!UICONTROL Remove the calculated field]** kruis.

![](assets/query_editor_nveau_58.png)

## Expressies maken {#building-expressions}

Met het gereedschap voor het bewerken van expressies kunt u aggregaten berekenen, functies genereren of een formule bewerken met een expressie.

In het volgende voorbeeld ziet u hoe u een telling op een primaire toets uitvoert.

Voer de volgende stappen uit:

1. Klikken **[!UICONTROL Add]** in de **[!UICONTROL Data to extract]** venster. In de **[!UICONTROL Formula type]** Selecteer een type formule om de expressie in te voeren.

   Er zijn verschillende typen beschikbare formules: **[!UICONTROL Field only]**, **[!UICONTROL Aggregate]**, **[!UICONTROL Expression]**.

   Selecteren **[!UICONTROL Process on an aggregate function]**, en **[!UICONTROL Count]**. Klik op **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_54.png)

1. De primaire sleutel wordt berekend.

   ![](assets/query_editor_nveau_88.png)

Hier volgt een gedetailleerde weergave van de opties in het dialoogvenster **[!UICONTROL Formula types]** venster:

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Field only]** Hiermee kunt u terugkeren naar de **[!UICONTROL Field to select]** venster.
1. **[!UICONTROL Aggregate (Process on an aggregate function)]**. Hier volgen enkele voorbeelden van het gebruik van aggregaten:

   * **[!UICONTROL Count]** Hiermee kunt u een aantal primaire sleutels uitvoeren.
   * **[!UICONTROL Sum]** Hiermee kunt u alle aankopen optellen die een klant gedurende een jaar heeft gedaan.
   * **[!UICONTROL Maximum value]** laat u de klanten vinden die de meeste &quot; n &quot; producten hebben gekocht.
   * **[!UICONTROL Minimum value]** Hiermee kunt u klanten doorzoeken en zoeken naar klanten die zich onlangs op een aanbieding hebben geabonneerd.
   * **[!UICONTROL Average]**. Met deze functie kunt u de gemiddelde leeftijd van de ontvangers berekenen.

     De **[!UICONTROL Distinct]** kunt u unieke en niet-nulwaarden van een kolom herstellen. Bijvoorbeeld, kunt u alle het volgen logboeken van een ontvanger terugkrijgen en deze het volgen logboeken worden veranderd in waarde 1 aangezien zij allen de zelfde ontvanger aangaan.

1. **[!UICONTROL Expression]** opent de **[!UICONTROL Edit the expression]** venster. Zo kunt u telefoonnummers met te veel cijfers detecteren. Dit kunnen invoerfouten zijn.

   ![](assets/query_editor_nveau_71.png)

   Voor een lijst met alle beschikbare functies raadpleegt u [Lijst met functies](#list-of-functions).

## Lijst met functies {#list-of-functions}

Als een **[!UICONTROL Expression]** de typeformule wordt gekozen, zult u aan het &quot;uitgeeft de uitdrukking&quot;venster worden genomen. Verschillende categorieën functies kunnen aan de beschikbare velden worden gekoppeld: **[!UICONTROL Aggregates]**, **[!UICONTROL String]**, **[!UICONTROL Date]**, **[!UICONTROL Numerical]**, **[!UICONTROL Currency]**, **[!UICONTROL Geomarketing]**, **[!UICONTROL Windowing function]** en **[!UICONTROL Others]**.

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
   <td> Hiermee wordt het gemiddelde van een kolom met het getaltype geretourneerd<br /> </td> 
   <td> Avg(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Aantal</strong><br /> </td> 
   <td> Telt de niet-null waarden van een kolom<br /> </td> 
   <td> Count()&lt;value&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>CountAll</strong><br /> </td> 
   <td> Telt de geretourneerde waarden (alle velden)<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Aftelbaar</strong><br /> </td> 
   <td> Telt de verschillende niet-null-waarden van een kolom<br /> </td> 
   <td> Countdifferent()&lt;value&gt;)<br /></td> 
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
   <td> Retourneert de standaardafwijking van een getal, tekenreeks of datumkolom<br /> </td> 
   <td> StdDev(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Som</strong><br /> </td> 
   <td> Hiermee wordt de som van de waarden van een getal, tekenreeks of kolom met het gegevenstype geretourneerd<br /> </td> 
   <td> Sum()&lt;value&gt;)<br /></td> 
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
   <td> Hiermee wordt het teken geretourneerd dat overeenkomt met de ASCII-code ‘n’<br /> </td> 
   <td> Char()&lt;number&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> Retourneert de positie van tekenreeks 2 in tekenreeks 1.<br /> </td> 
   <td> Charindex()&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> Retourneert de n-de (van 1 tot en met n) regel van de tekenreeks<br /> </td> 
   <td> GetLine()&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> Retourneert de derde parameter als de eerste twee parameters gelijk zijn. Indien niet, wordt de laatste parameter geretourneerd<br /> </td> 
   <td> IfEquals(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> Geeft aan of het als parameter doorgegeven memo null is<br /> </td> 
   <td> IsMemoNull()&lt;memo&gt;)<br /></td> 
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
   <td> LPad()&lt;string&gt;, &lt;number&gt;, &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Left</strong><br /> </td> 
   <td> Retourneert de eerste n tekens van de tekenreeks<br /> </td> 
   <td> Left(&lt;string&gt;, &lt;number&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Length</strong><br /> </td> 
   <td> Retourneert de lengte van de tekenreeks<br /> </td> 
   <td> Length()&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Lower</strong><br /> </td> 
   <td> Hiermee wordt de tekenreeks in kleine letters geretourneerd<br /> </td> 
   <td> Lower()&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ltrim</strong><br /> </td> 
   <td> Hiermee worden spaties links van de tekenreeks verwijderd<br /> </td> 
   <td> Ltrim()&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Md5Digest</strong><br /> </td> 
   <td> Retourneert een hexadecimale representatie van de MD5-toets van een tekenreeks<br /> </td> 
   <td> Md5Digest()&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>MemoContains</strong><br /> </td> 
   <td> Hiermee wordt opgegeven of het memo de tekenreeks bevat die als parameter is doorgegeven<br /> </td> 
   <td> MemoContains()&lt;memo&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> Hiermee wordt de voltooide tekenreeks aan de rechterkant geretourneerd<br /> </td> 
   <td> RPad(&lt;string&gt;, &lt;number&gt;, &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Right</strong><br /> </td> 
   <td> Retourneert de laatste n tekens van de tekenreeks<br /> </td> 
   <td> Right(&lt;tekenreeks&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> Hiermee worden spaties rechts van de tekenreeks verwijderd<br /> </td> 
   <td> Rtrim(&lt;tekenreeks&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Smart</strong><br /> </td> 
   <td> Retourneert de tekenreeks met de eerste letter van elk woord in hoofdletters<br /> </td> 
   <td> Smart(&lt;tekenreeks&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Substring</strong><br /> </td> 
   <td> Hiermee wordt de subtekenreeks opgehaald die begint op teken n1 van de tekenreeks en lengte n2<br /> </td> 
   <td> Substring(&lt;tekenreeks&gt;, &lt;offset&gt;, &lt;lengte&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> Zet het getal om in een tekenreeks<br /> </td> 
   <td> ToString(&lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Upper</strong><br /> </td> 
   <td> Hiermee wordt de tekenreeks in hoofdletters geretourneerd<br /> </td> 
   <td> Upper(&lt;tekenreeks&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> Retourneert de externe sleutel van een koppeling die als een parameter is doorgegeven als de andere twee parameters gelijk zijn<br /> </td> 
   <td> VirtualLink(&lt;nummer&gt;, &lt;nummer&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> Retourneert de externe sleutel (tekst) van een koppeling die als parameter wordt doorgegeven als de andere twee parameters gelijk zijn<br /> </td> 
   <td> VirtualLinkStr(&lt;tekenreeks&gt;, &lt;nummer&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>dataLength</strong><br /> </td> 
   <td> Retourneert de tekenreeksgrootte<br /> </td> 
   <td> dataLength()&lt;string&gt;)<br /> </td>  
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
   <td> AddDays(&lt;datum&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> Hiermee voegt u een aantal uren toe aan een datum<br /> </td> 
   <td> AddHours(&lt;datum&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> Hiermee voegt u een aantal minuten toe aan een datum<br /> </td> 
   <td> AddMinutes(&lt;datum&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> Hiermee voegt u een aantal maanden toe aan een datum<br /> </td> 
   <td> AddMonths(&lt;datum&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> Hiermee voegt u een aantal seconden toe aan een datum<br /> </td> 
   <td> AddSeconds(&lt;datum&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddYears</strong><br /> </td> 
   <td> Hiermee voegt u een aantal jaren toe aan een datum<br /> </td> 
   <td> AddYear(&lt;datum&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DateOnly</strong><br /> </td> 
   <td> Retourneert alleen de datum (met tijd om 00:00)*<br /> </td> 
   <td> DateOnly(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Day</strong><br /> </td> 
   <td> Retourneert het getal dat de dag van de datum vertegenwoordigt<br /> </td> 
   <td> Day(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DayOfYear</strong><br /> </td> 
   <td> Retourneert het getal van de dag in het jaar van de datum<br /> </td> 
   <td> DayOfYear(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> Retourneert de datum die overeenkomt met de huidige datum min n dagen<br /> </td> 
   <td> DaysAgo(&lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> Retourneert de datum (geheel getal jjjjmmdd) die overeenkomt met de huidige datum min n dagen<br /> </td> 
   <td> DaysAgoInt(&lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> Aantal dagen tussen twee datums<br /> </td> 
   <td> DaysDiff(&lt;einddatum&gt;, &lt;begindatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> Retourneert de leeftijd in dagen van een datum<br /> </td> 
   <td> DaysOld(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> Hiermee wordt de huidige systeemdatum van de server geretourneerd<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Hour</strong><br /> </td> 
   <td> Retourneert het uur van de datum<br /> </td> 
   <td> Hour(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>HoursDiff</strong><br /> </td> 
   <td> Retourneert het aantal uren tussen twee datums<br /> </td> 
   <td> HoursDiff(&lt;einddatum&gt;, &lt;begindatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Minute</strong><br /> </td> 
   <td> Retourneert de minuten van de datum<br /> </td> 
   <td> Minute(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> Retourneert het aantal minuten tussen twee datums<br /> </td> 
   <td> MinutesDiff(&lt;einddatum&gt;, &lt;begindatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Month</strong><br /> </td> 
   <td> Retourneert het getal dat de maand van de datum vertegenwoordigt<br /> </td> 
   <td> Month(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsAgo</strong><br /> </td> 
   <td> Retourneert de datum die overeenkomt met de huidige datum minus n maanden<br /> </td> 
   <td> MonthsAgo(&lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> Retourneert het aantal maanden tussen twee datums<br /> </td> 
   <td> MonthsDiff(&lt;einddatum&gt;, &lt;begindatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> Retourneert de leeftijd in maanden van een datum<br /> </td> 
   <td> MonthsOld(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Second</strong><br /> </td> 
   <td> Retourneert de seconden van de datum<br /> </td> 
   <td> Second(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> Retourneert het aantal seconden tussen twee datums<br /> </td> 
   <td> SecondsDiff(&lt;einddatum&gt;, &lt;begindatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubDays</strong><br /> </td> 
   <td> Hiermee trekt u een aantal dagen van een datum af<br /> </td> 
   <td> SubDays(&lt;datum&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubHours</strong><br /> </td> 
   <td> Hiermee trekt u een aantal uren van een datum af<br /> </td> 
   <td> SubHours(&lt;datum&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMinutes</strong><br /> </td> 
   <td> Hiermee trekt u een aantal aantal minuten van een datum af<br /> </td> 
   <td> SubMinutes(&lt;datum&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMonths</strong><br /> </td> 
   <td> Hiermee trekt u een aantal maanden van een datum af<br /> </td> 
   <td> SubMonths(&lt;datum&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubSeconds</strong><br /> </td> 
   <td> Hiermee trekt u een aantal seconden van een datum af<br /> </td> 
   <td> SubSeconds(&lt;datum&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubYears</strong><br /> </td> 
   <td> Hiermee trekt u een aantal jaren van een datum af<br /> </td> 
   <td> SubYears(&lt;datum&gt;, &lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> Converteert een datum + tijd als datum<br /> </td> 
   <td> ToDate(&lt;datum + tijd&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> Zet een tekenreeks om in een datum + tijd<br /> </td> 
   <td> ToDateTime(&lt;tekenreeks&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> Rondt een datum+tijd af naar de dichtstbijzijnde seconde<br /> </td> 
   <td> TruncDate(@lastModified, &lt;aantal seconden&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> Rondt een datum + tijd af naar een bepaalde precisie die in seconden wordt uitgedrukt<br /> </td> 
   <td> TruncDateTZ(&lt;datum&gt;, &lt;aantal seconden&gt;, &lt;tijdzone&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> Rondt een datum af naar het kwartaal<br /> </td> 
   <td> TruncQuarter(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> Rondt het tijdsdeel af naar de dichtstbijzijnde seconde<br /> </td> 
   <td> TruncTim(e&lt;date&gt;, &lt;number of="" seconds=""&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Rondt een datum af naar de week<br /> </td> 
   <td> TruncWeek(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> Rondt een datum + tijd naar 1 januari van het jaar<br /> </td> 
   <td> TruncYear(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Retourneert het getal dat de dag in de week van de datum vertegenwoordigt<br /> </td> 
   <td> WeekDay(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Year</strong><br /> </td> 
   <td> Retourneert het getal dat het jaar van de datum vertegenwoordigt<br /> </td> 
   <td> Year(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearAnd Month</strong><br /> </td> 
   <td> Retourneert het getal dat het jaar en de maand van de datum vertegenwoordigt.<br /> </td> 
   <td> YearAndMonth(&lt;datum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearDiff</strong><br /> </td> 
   <td> Retourneert het aantal jaren tussen de twee datums<br /> </td> 
   <td> YearsDiff(&lt;einddatum&gt;, &lt;begindatum&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsOld</strong><br /> </td> 
   <td> Retourneert de leeftijd in jaren van een datum<br /> </td> 
   <td> YearOld(&lt;datum&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Let erop dat de **Alleen datum** De functie houdt rekening met de tijdzone van de server, niet de exploitant.

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
   <td> Abs(&lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> Retourneert het laagste gehele getal dat groter is dan of gelijk is aan een getal<br /> </td> 
   <td> Ceil(&lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> Retourneert het grootste gehele getal dat groter is dan of gelijk is aan een getal<br /> </td> 
   <td> Floor(&lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Greatest</strong><br /> </td> 
   <td> Retourneert het hoogste van twee getallen<br /> </td> 
   <td> Greatest(&lt;nummer 1&gt;, &lt;nummer 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Least</strong><br /> </td> 
   <td> Retourneert het laagste van twee getallen<br /> </td> 
   <td> Least(&lt;nummer 1&gt;, &lt;nummer 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> Retourneert de rest van de integer-deling van n1 door n2<br /> </td> 
   <td> Mod(&lt;nummer 1&gt;, &lt;nummer 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Percent</strong><br /> </td> 
   <td> Retourneert de verhouding van twee getallen uitgedrukt als een percentage<br /> </td> 
   <td> Percent(&lt;nummer 1&gt;, &lt;nummer 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Random</strong><br /> </td> 
   <td> Hiermee wordt de willekeurige waarde geretourneerd<br /> </td> 
   <td> Random()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Round</strong><br /> </td> 
   <td> Rondt een getal af naar n decimalen<br /> </td> 
   <td> Round(&lt;nummer&gt;, &lt;aantal decimalen&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Sign</strong><br /> </td> 
   <td> Hiermee wordt het teken van het getal geretourneerd<br /> </td> 
   <td> Sign(&lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> Hiermee wordt een geheel getal omgezet in een zwevende waarde<br /> </td> 
   <td> ToDouble(&lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> Zet een zwevende waarde om in een 64-bits geheel getal<br /> </td> 
   <td> ToInt64(&lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> Hiermee wordt een zwevende waarde omgezet in een geheel getal<br /> </td> 
   <td> ToInteger(&lt;nummer&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> Kapt aantal decimalen af van n1 tot n2<br /> </td> 
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
   <td> ConvertCurrency()&lt;amount&gt;, &lt;source currency=""&gt;, &lt;target currency=""&gt;, &lt;conversion date=""&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>FormatCurrency</strong><br /> </td> 
   <td> Maakt het weergegeven bedrag op basis van de geselecteerde valutainstellingen op<br /> </td> 
   <td> FormatCurrency()&lt;amount&gt;, &lt;currency&gt;)<br /> </td>  
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
   <td> <strong>Distance</strong><br /> </td> 
   <td> Retourneert de afstand tussen twee punten die worden gedefinieerd door hun lengte en breedte, uitgedrukt in graden.<br /> </td> 
   <td> Distance(&lt;Lengtegraad A&gt;, &lt;Breedtegraad A&gt;, &lt;Lengtegraad B&gt;, &lt;Breedtegraad B&gt;)<br /> </td>  
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
   <td> Case(When(&lt;voorwaarde&gt;, &lt;waarde 1&gt;), Else(&lt;waarde 2&gt;))<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> Hiermee verwijdert u de markering in de waarde<br /> </td> 
   <td> ClearBit(&lt;identificatiecode&gt;, &lt;markering&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Coalesce</strong><br /> </td> 
   <td> Retourneert waarde 2 als waarde 1 null of nihil is, anders wordt waarde 1 geretourneerd<br /> </td> 
   <td> Coalesce(&lt;waarde 1&gt;, &lt;waarde 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Decode</strong><br /> </td> 
   <td> Retourneert waarde 3 als waarde 1 = waarde 2. Indien geen waarde 4.<br /> </td> 
   <td> Decode(&lt;waarde 1&gt;, &lt;waarde 2&gt;, &lt;waarde 3&gt;, &lt;waarde 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> Retourneert waarde 1 (mag alleen worden gebruikt als parameter van de case-functie)<br /> </td> 
   <td> else(&lt;value&gt;, &lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> Extraheert het domein uit een e-mailadres<br /> </td> 
   <td> GetEmailDomain(&lt;waarde&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> Hiermee wordt de URL van de server van de spiegelpagina opgehaald<br /> </td> 
   <td> GetMirrorURL(&lt;waarde&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Iif</strong><br /> </td> 
   <td> Retourneert waarde 1 als de expressie true is. Zo niet, retourneert waarde 2<br /> </td> 
   <td> Iif(&lt;voorwaarde&gt;, &lt;waarde 1&gt;, &lt;waarde 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> Geeft aan of de markering zich in de waarde bevindt<br /> </td> 
   <td> IsBitSet(&lt;identificatiecode&gt;, &lt;markering&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> Retourneert waarde 2 als tekenreeks 1 leeg is. Retourneert anders waarde 3<br /> </td> 
   <td> IsEmptyString()&lt;value&gt;, &lt;value&gt;, &lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> Retourneert de lege tekenreeks als het argument NULL is<br /> </td> 
   <td> NoNull(&lt;waarde&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> Retourneert het regelnummer<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> Hiermee wordt de markering in de waarde geforceerd<br /> </td> 
   <td> SetBit(&lt;identificatiecode&gt;, &lt;markering&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> Hiermee wordt een getal omgezet in een Booleaanse waarde<br /> </td> 
   <td> ToBoolean(&lt;nummer&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>When</strong><br /> </td> 
   <td> Retourneert waarde 1 als de expressie true is. Zo niet, dan wordt waarde 2 geretourneerd (mag alleen worden gebruikt als parameter van de case-functie)<br /> </td> 
   <td> When(&lt;voorwaarde&gt;, &lt;waarde 1&gt;)<br /> </td>  
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
   <td> Desc(&lt;waarde 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> Hiermee wordt het resultaat binnen de partitie gesorteerd<br /> </td> 
   <td> OrderBy(&lt;waarde 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>PartitionBy</strong><br /> </td> 
   <td> Verdeelt het resultaat van een query op een lijst<br /> </td> 
   <td> PartitionBy(&lt;waarde 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> Hiermee genereert u een regelnummer op basis van de tabelpartitie en een sorteervolgorde.<br /> </td> 
   <td> RowNum(PartitionBy(&lt;waarde 1&gt;), OrderBy(&lt;waarde 1&gt;))<br /> </td> 
  </tr> 
 </tbody> 
</table>
