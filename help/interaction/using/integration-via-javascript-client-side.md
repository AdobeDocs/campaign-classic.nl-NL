---
product: campaign
title: Integratie via JavaScript (clientzijde)
description: Integratie via JavaScript (clientzijde)
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a9842e59-120c-4a35-abdf-6540a0bbdd6d
source-git-commit: 349c3dfd936527e50d7d3e03aa3408b395502da0
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 2%

---

# Integratie via JavaScript (clientzijde){#integration-via-javascript-client-side}



Als u de Interactie-engine op een webpagina wilt aanroepen, voegt u een aanroep van een JavaScript-code rechtstreeks in de pagina in. Deze vraag keert de aanbiedingsinhoud in gerichte terug

element.

Adobe raadt u aan de integratiemethode voor JavaScript te gebruiken.

Het script dat URL aanroept ziet er als volgt uit:

```
<script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=" type="text/javascript"></script>
```

De &quot;**env**&quot;parameter ontvangt de interne naam van het levende milieu gewijd aan anonieme interactie.

Om een aanbieding te presenteren, moeten wij een milieu en een aanbiedingsruimte in Adobe Campaign creëren, dan de pagina van de HTML vormen.

In de volgende gebruiksgevallen worden de mogelijke opties voor het integreren van aanbiedingen via JavaScript beschreven.

## HTML, modus {#html-mode}

### Een anonieme aanbieding presenteren {#presenting-an-anonymous-offer}

1. **voorbereidend de interactiemotor**

   Open de Adobe Campaign-interface en bereid een anonieme omgeving voor.

   Maak een aanbiedingsruimte die is gekoppeld aan de anonieme omgeving.

   Maak een aanbieding en geef deze weer in verband met de aanbiedingsruimte.

1. **Inhoud van de pagina van de HTML**

   De pagina HTML moet een

   element met een @id-kenmerk met de waarde van de interne naam van de gemaakte aanbiedingsruimte (&quot;i_internal name space&quot;). Het aanbod wordt in dit
element op interactie.

   In ons voorbeeld ontvangt het kenmerk @id de waarde &quot;i_SPC12&quot;, waarbij &quot;SPC12&quot; de interne naam is van de eerder gemaakte aanbiedingsruimte:

   ```
   <div id="i_SPC12"></div>
   ```

   In ons voorbeeld is de URL voor het aanroepen van het script als volgt (&quot;OE3&quot; is de interne naam van de live omgeving):

   ```
   <script id="interactionProposalScript" src="https://instance.adobe.org:8080/nl/interactionProposal.js?env=OE3" type="text/javascript"></script>
   ```

   >[!IMPORTANT]
   >
   >De tag `<script>` mag niet zelfsluitend zijn.

   Deze statische vraag zal automatisch een dynamische vraag produceren die alle parameters bevat nodig door de motor van de Interactie.

   Dit gedrag laat u verscheidene aanbiedingsruimten op de zelfde pagina gebruiken, die door één enkele vraag aan de motor worden beheerd.

1. **Resultaten in de pagina van de HTML**

   De inhoud van de aanbiedingsvertegenwoordiging is teruggekeerd aan de pagina van de HTML door de motor van de Interactie:

   ```
   <div id="banner_header">
     <div id="i_SPC12">
       <table>
         <tbody>
           <tr>
             <td><h3>Fly to Japan!</h3></td>
           </tr>
           <tr>
             <td><img width="150px" src="https://instance.adobe.org/res/Track/874fdaf72ddc256b2d8260bb8ec3a104.jpg"></td>
             <td>
               <p>Discover Japan for 2 weeks at an unbelievable price!!</p>
               <p><b>2345 Dollars - All inclusive</b></p>
             </td>
           </tr>
         </tbody>
       </table>
     </div>
     <script src="https://instance.adobe.org:8080/nl/interactionProposal.js?env=OE3" id="interactionProposalScript" type="text/javascript"></script>
   </div>
   ```

### Een geïdentificeerd aanbod presenteren {#presenting-an-identified-offer}

Om een aanbieding aan een geïdentificeerd contact voor te stellen, is het proces gelijkaardig zoals hier gedetailleerd: [ Presenterend een anonieme aanbieding ](#presenting-an-anonymous-offer). In de inhoud van de webpagina moet u het volgende script toevoegen waarmee de contactpersoon tijdens de aanroep naar de engine wordt geïdentificeerd:

```
<script type="text/javascript">
  interactionTarget = <contact_identifier>;
</script>
```

1. Ga naar de aanbiedingsruimte die door de webpagina wordt aangeroepen, klik op **[!UICONTROL Advanced parameters]** en voeg een of meer identificatietoetsen toe.

   ![](assets/interaction_htmlmode_001.png)

   In dit voorbeeld is de identificatiesleutel samengesteld omdat deze zowel op de e-mail als op de naam van de ontvanger is gebaseerd.

1. Tijdens de Web-pagina vertoning, laat de manuscriptevaluatie u ontvankelijke identiteitskaart op de aanbiedingsmotor overgaan. Als de id een samenstelling heeft, worden de toetsen weergegeven in dezelfde volgorde als in de geavanceerde instellingen en worden ze van elkaar gescheiden door een |.

   In het volgende voorbeeld is de contactpersoon aangemeld bij de website en is deze via e-mail en naam herkend tijdens het aanroepen naar de Interaction-engine.

   ```
   <script type="text/javascript">
     interactionTarget = myEmail|myName;
   </script>
   ```

### Een HTML-renderfunctie gebruiken {#using-an-html-rendering-function}

Als u de representatie van de HTML-aanbieding automatisch wilt genereren, kunt u een renderfunctie gebruiken.

1. Ga naar de aanbiedingsruimte en klik op **[!UICONTROL Edit functions]** .
1. Selecteer **[!UICONTROL Overload the HTML rendering function]**.
1. Ga naar het tabblad **[!UICONTROL HTML rendering]** en voeg de variabelen die overeenkomen met de velden die voor de aanbiedingsinhoud zijn gedefinieerd, in de aanbiedingsruimte in.

   ![](assets/interaction_htmlmode_002.png)

   In dit voorbeeld wordt de aanbieding weergegeven in de vorm van een banner op een webpagina en bestaat deze uit een klikbare afbeelding en een titel die overeenkomen met de velden die zijn gedefinieerd in de inhoud van de aanbieding.

## XML-modus {#xml-mode}

### Een voorstel presenteren {#presenting-an-offer}

De interactie laat u een knoop van XML aan de pagina terugkeren van de HTML die de aanbiedingsmotor omhoog roept. Dit XML-knooppunt kan worden verwerkt door functies die aan de kant van de klant moeten worden ontwikkeld.

De vraag aan de motor van de Interactie kijkt als dit:

```
<script type="text/javascript" id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=&cb="></script>
```

De &quot;**env**&quot;parameter ontvangt de interne naam van het levende milieu.

De &quot;**cb**&quot;parameter ontvangt de naam van de functie die de knoop van XML zal lezen die door de motor is teruggekeerd die (callback) proposition(s) bevat. Deze parameter is optioneel.

De &quot;**t**&quot;parameter ontvangt de waarde van het doel, slechts voor een geïdentificeerde interactie. Deze parameter kan ook met de **interactionTarget** variabele worden overgegaan. Deze parameter is optioneel.

De &quot;**c**&quot;parameter ontvangt de lijst van interne namen van de categorieën. Deze parameter is optioneel.

De &quot;**de**&quot;parameter ontvangt de lijst van thema&#39;s. Deze parameter is optioneel.

De &quot;**gctx**&quot;parameter ontvangt globale vraaggegevens (context) aan de volledige pagina. Deze parameter is optioneel.

Het geretourneerde XML-knooppunt ziet er als volgt uit:

```
<propositions>
 <proposition id="" offer-id="" weight="" rank="" space="" div=""> //proposition identifiers
   ...XML content defined in Adobe Campaign...
 </proposition>
 ...
</propositions>
```

Het volgende gebruiksgeval specificeert de configuraties om in Adobe Campaign uit te voeren om de wijze van XML toe te laten dan het resultaat van de vraag aan de motor op de pagina van de HTML tonen.

1. **Creërend een milieu en een aanbiedingsruimte**

   Voor meer bij het creëren van een milieu, verwijs naar [ Levend/de milieu&#39;s van het Ontwerp ](../../interaction/using/live-design-environments.md).

   Voor meer bij het creëren van een aanbiedingsruimte, verwijs naar [ Creërend aanbiedingsruimten ](../../interaction/using/creating-offer-spaces.md).

1. **Uitbreidend het aanbiedingsschema om nieuwe gebieden toe te voegen**

   In dit schema worden de volgende velden gedefinieerd: Titel nummer 2 en prijs.

   De naam van het schema in het voorbeeld is **focus:aanbieding**

   ```
   <srcSchema _cs="Marketing offers (cus)" created="2 AAAA-MM-DD HH:MM:SS.762Z" createdBy-id="0"
              desc="" entitySchema="xtk:srcSchema" extendedSchema="nms:offer" img="nms:offer.png"
              label="Marketing offers" labelSingular="Marketing offers" lastModified="AAAA-MM-DD HH:MM:SS.373Z"
              mappingType="sql" md5="F14A7AA009AE1FCE31B0611E72866AC3" modifiedBy-id="0"
              name="offer" namespace="cus" xtkschema="xtk:srcSchema">
     <createdBy _cs="Administrator (admin)"/>
     <modifiedBy _cs="Administrator (admin)"/>
     <element img="nms:offer.png" label="Marketing offers" labelSingular="Marketing offer"
              name="offer">
       <element label="Content" name="view">
         <element label="Price" name="price" type="long" xml="true"/>
         <element label="Title 2" name="title2" type="string" xml="true"/>
   
         <element advanced="true" desc="Price calculation script." label="Script price"
                  name="price_jst" type="CDATA" xml="true"/>
         <element advanced="true" desc="Title calculation script." label="Script title"
                  name="title2_jst" type="CDATA" xml="true"/>
       </element>
     </element>
   </srcSchema>
   ```

   >[!IMPORTANT]
   >
   >Elk element moet tweemaal worden gedefinieerd. CDATA-typeelementen (&quot;_jst&quot;) kunnen personalisatievelden bevatten.
   >
   >Vergeet niet de databasestructuur bij te werken. Raadpleeg [deze sectie](../../configuration/using/updating-the-database-structure.md) voor meer informatie.

   >[!NOTE]
   >
   >U kunt het aanbiedingsschema uitbreiden om nieuwe velden zowel in batch- als eenheidsmodus en in elke gewenste indeling (tekst, HTML en XML) toe te voegen.

1. **Uitbreidend de aanbiedingsformule om nieuwe gebieden uit te geven en een bestaand gebied** te wijzigen

   Bewerk de **Aanbieding (nsm)** inputvorm.

   Voeg in de sectie Weergaven de twee nieuwe velden in met de volgende inhoud:

   ```
   <input label="Title 2" margin-right="5" prebuildSubForm="false" type="subFormLink"
                        xpath="title2_jst">
                   <form label="Edit title 2" name="editForm" nothingToSave="true">
                     <input nolabel="true" toolbarAlign="horizontal" type="jstEdit"
                            xpath="." xpathInsert="/ignored/customizeTitle2">
                       <container>
                         <input menuId="viewMenuBuilder" options="inbound" type="customizeBtn"
                                xpath="/ignored/customizeTitle2"/>
                       </container>
                     </input>
                   </form>
                 </input>
                 <input nolabel="true" type="edit" xpath="title2_jst"/>
   
                 <input label="Price" margin-right="5" prebuildSubForm="false" type="subFormLink"
                        xpath="price_jst">
                   <form label="Edit price" name="editForm" nothingToSave="true">
                     <input nolabel="true" toolbarAlign="horizontal" type="jstEdit"
                            xpath="." xpathInsert="/ignored/customizePrice">
                       <container>
                         <input menuId="viewMenuBuilder" options="inbound" type="customizeBtn"
                                xpath="/ignored/customizePrice"/>
                       </container>
                     </input>
                   </form>
                 </input>
                 <input colspan="2" label="Prix" nolabel="true" type="number" xpath="price_jst"/>
   ```

   Opmerking toevoegen aan het doel-URL-veld:

   ![](assets/interaction_xmlmode_form_001.png)

   >[!IMPORTANT]
   >
   >De velden van het formulier ( `<input>` ) moeten verwijzen naar de CDATA-typeelementen die zijn gedefinieerd in het gemaakte schema.

   De rendering in het formulier met aanbiedingsweergaven ziet er als volgt uit:

   ![](assets/interaction_xmlmode_form.png)

   De velden **[!UICONTROL Title 2]** en **[!UICONTROL Price]** zijn toegevoegd en het veld **[!UICONTROL Destination URL]** wordt niet meer weergegeven.

1. **Een aanbieding maken**

   Voor meer bij het creëren van aanbiedingen, verwijs naar [ Creërend een aanbieding ](../../interaction/using/creating-an-offer.md).

   In het volgende gebruiksgeval wordt de aanbieding als volgt vermeld:

   ![](assets/interaction_xmlmode_offer.png)

1. Goedkeuren of laten goedkeuren door iemand anders, dan activeren op de aanbiedingsruimte die bij de laatste stap is gecreëerd, zodat deze beschikbaar wordt gesteld in de gekoppelde live omgeving.
1. **vraag van de Motor en resultaat op de pagina van de HTML**

   De vraag aan de interactiemotor in de pagina van de HTML ziet als volgt:

   ```
   <script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=OE7&cb=alert" type="text/javascript">
   ```

   De waarde van de &quot;**env**&quot;parameter is de interne naam van het levende milieu.

   De waarde van de &quot;**cb**&quot;parameter is de naam van de functie die de knoop van XML moet interpreteren die door de motor is teruggekeerd. In ons voorbeeld opent de aangeroepen functie een modaal venster (alert() functie).

   Het XML-knooppunt dat door de Interaction-engine wordt geretourneerd, ziet er als volgt uit:

   ```
   <propositions>
    <proposition id="a28002" offer-id="10322005" weight="1" rank="1" space="SPC14" div="i_SPC14">
     <xmlOfferView>
      <title>Travel to Russia</title>
      <price>3456</price>
      <description>Discover this vacation package!INCLUDES 10 nights. FEATURES buffet breakfast daily. BONUS 5th night free.</description>
      <image>
       <path>https://myinstance.com/res/Track/ae1d2113ed732d58a3beb441084e5960.jpg</path>
       <alt>Travel to Russia</alt>
      </image>
     </xmlOfferView>
    </proposition>
   </propositions>
   ```

### Een renderfunctie gebruiken {#using-a-rendering-function-}

Het is mogelijk een XML-renderfunctie te gebruiken om een aanbiedingspresentatie te maken. Deze functie wijzigt de knoop van XML die aan de pagina van de HTML tijdens de vraag aan de motor is teruggekeerd.

1. Ga naar de aanbiedingsruimte en klik op **[!UICONTROL Edit functions]** .
1. Selecteer **[!UICONTROL Overload the XML rendering function]**.
1. Ga naar de tab **[!UICONTROL XML rendering]** en voeg de gewenste functie in.

   De functie kan er als volgt uitzien:

   ```
   function (proposition) {
     delete proposition.@id;
     proposition.@newAttribute = "newValue";
   } 
   ```

![](assets/interaction_xmlmode_001.png)
