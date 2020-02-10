---
title: Integratie via JavaScript (clientzijde)
seo-title: Integratie via JavaScript (clientzijde)
description: Integratie via JavaScript (clientzijde)
seo-description: null
page-status-flag: never-activated
uuid: 19cafecd-cf13-458a-857e-0a45c346f4ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 7453d768-31eb-4372-aae3-27527cd5c79b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Integratie via JavaScript (clientzijde){#integration-via-javascript-client-side}

Als u de interactie-engine op een webpagina wilt aanroepen, voegt u een aanroep van een JavaScript-code rechtstreeks in op de pagina. Deze vraag keert de aanbiedingsinhoud in gerichte terug

    element.

Adobe raadt u aan de JavaScript-integratiemethode te gebruiken.

Het script dat URL aanroept ziet er als volgt uit:

```
<script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=" type="text/javascript"></script>
```

De &quot;**env**&quot;parameter ontvangt de interne naam van het levende milieu gewijd aan anonieme interactie.

Om een aanbieding te presenteren, moeten wij een milieu en een aanbiedingsruimte in de Campagne van Adobe tot stand brengen, dan de HTML- pagina vormen.

In de volgende gebruiksgevallen worden de mogelijke opties beschreven voor het integreren van aanbiedingen via JavaScript.

## HTML-modus {#html-mode}

### Een anonieme aanbieding presenteren {#presenting-an-anonymous-offer}

1. **De interactie-engine voorbereiden**

   Open de interface van de Campagne van Adobe en bereid een anonieme milieu voor.

   Maak een aanbiedingsruimte die is gekoppeld aan de anonieme omgeving.

   Maak een aanbieding en geef deze weer in verband met de aanbiedingsruimte.

1. **Inhoud van de HTML-pagina**

   De HTML-pagina moet een

   element met een @id-kenmerk met de waarde van de interne naam van de gemaakte aanbiedingsruimte (&quot;i_internal name space&quot;). Het aanbod zal in dit element door Interaction worden opgenomen.

   In ons voorbeeld ontvangt het kenmerk @id de waarde &quot;i_SPC12&quot;, waarbij &quot;SPC12&quot; de interne naam is van de eerder gemaakte aanbiedingsruimte:

   ```
   <div id="i_SPC12"></div>
   ```

   In ons voorbeeld is de URL voor het aanroepen van het script als volgt (&quot;OE3&quot; is de interne naam van de live omgeving):

   ```
   <script id="interactionProposalScript" src="https://instance.adobe.org:8080/nl/interactionProposal.js?env=OE3" type="text/javascript"></script>
   ```

   >[!CAUTION]
   >
   >De `<script>` tag mag niet zelfsluitend zijn.

   Deze statische vraag zal automatisch een dynamische vraag produceren die alle parameters bevat nodig door de motor van de Interactie.

   Dit gedrag laat u verscheidene aanbiedingsruimten op de zelfde pagina gebruiken, die door één enkele vraag aan de motor worden beheerd.

1. **Resultaten in de HTML-pagina**

   De inhoud van de aanbiedingsrepresentatie wordt door de Interaction-engine geretourneerd aan de HTML-pagina:

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

Om een aanbieding aan een geïdentificeerde contact voor te stellen, is het proces gelijkaardig zoals hier beschreven: Een anonieme aanbieding [](#presenting-an-anonymous-offer)presenteren. In de inhoud van de webpagina moet u het volgende script toevoegen waarmee de contactpersoon tijdens de aanroep naar de engine wordt geïdentificeerd:

```
<script type="text/javascript">
  interactionTarget = <contact_identifier>;
</script>
```

1. Ga naar de aanbiedingsruimte die door de webpagina wordt opgeroepen, klik **[!UICONTROL Advanced parameters]** en voeg een of meer identificatietoetsen toe.

   ![](assets/interaction_htmlmode_001.png)

   In dit voorbeeld is de identificatiecode samengesteld, omdat deze zowel op de e-mail als op de naam van de ontvanger is gebaseerd.

1. Tijdens de Web-pagina vertoning, laat de manuscriptevaluatie u ontvankelijke identiteitskaart op de aanbiedingsmotor overgaan. Als de id een samenstelling heeft, worden de toetsen weergegeven in dezelfde volgorde als in de geavanceerde instellingen en worden ze van elkaar gescheiden door een|.

   In het volgende voorbeeld is de contactpersoon aangemeld bij de website en is deze via e-mail en naam herkend tijdens het aanroepen naar de Interaction-engine.

   ```
   <script type="text/javascript">
     interactionTarget = myEmail|myName;
   </script>
   ```

### Een HTML-renderfunctie gebruiken {#using-an-html-rendering-function}

Als u de representatie van de HTML-aanbieding automatisch wilt genereren, kunt u een renderfunctie gebruiken.

1. Ga naar de aanbiedingsruimte en klik op de **[!UICONTROL Edit functions]** koppeling.
1. Selecteer **[!UICONTROL Overload the HTML rendering function]**.
1. Ga naar het **[!UICONTROL HTML rendering]** lusje en neem de variabelen op die de gebieden aanpassen voor de aanbiedingsinhoud in de aanbiedingsruimte worden bepaald.

   ![](assets/interaction_htmlmode_002.png)

   In dit voorbeeld wordt de aanbieding weergegeven in de vorm van een banner op een webpagina en bestaat deze uit een klikbare afbeelding en een titel die overeenkomen met de velden die zijn gedefinieerd in de inhoud van de aanbieding.

## XML-modus {#xml-mode}

### Een voorstel presenteren {#presenting-an-offer}

De interactie laat u een knoop van XML aan de HTML- pagina terugkeren die omhoog de aanbiedingsmotor roept. Dit XML-knooppunt kan worden verwerkt door functies die aan de kant van de klant moeten worden ontwikkeld.

De vraag aan de motor van de Interactie kijkt als dit:

```
<script type="text/javascript" id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=&cb="></script>
```

De parameter &quot;**env**&quot; ontvangt de interne naam van de live omgeving.

De parameter &quot;**cb**&quot; ontvangt de naam van de functie die het XML-knooppunt leest dat wordt geretourneerd door de engine die het (callback) proposition(s) bevat. Deze parameter is optioneel.

De parameter &quot;**t**&quot; ontvangt de waarde van het doel, alleen voor een geïdentificeerde interactie. Deze parameter kan ook met de **interactionTarget** variabele worden overgegaan. Deze parameter is optioneel.

De parameter &quot;**c**&quot; ontvangt de lijst met interne namen van de categorieën. Deze parameter is optioneel.

De parameter &quot;**th**&quot; ontvangt de lijst met thema&#39;s. Deze parameter is optioneel.

De parameter &quot;**gctx**&quot;ontvangt globale vraaggegevens (context) aan de volledige pagina. Deze parameter is optioneel.

Het geretourneerde XML-knooppunt ziet er als volgt uit:

```
<propositions>
 <proposition id="" offer-id="" weight="" rank="" space="" div=""> //proposition identifiers
   ...XML content defined in Adobe Campaign...
 </proposition>
 ...
</propositions>
```

In het volgende gebruiksgeval worden de configuraties beschreven die in Adobe Campagne moeten worden uitgevoerd om de modus XML in te schakelen en wordt vervolgens het resultaat van de aanroep naar de engine in de HTML-pagina weergegeven.

1. **Een omgeving en een aanbiedingsruimte maken**

   Raadpleeg [Live/Design-omgevingen](../../interaction/using/live-design-environments.md)voor meer informatie over het maken van een omgeving.

   Raadpleeg [Aanbiedingsruimten](../../interaction/using/creating-offer-spaces.md)maken voor meer informatie over het maken van een aanbiedingsruimte.

1. **Het aanbiedingsschema uitbreiden om nieuwe velden toe te voegen**

   Met dit schema worden de volgende velden gedefinieerd: Titel nummer 2 en prijs.

   De naam van het schema in het voorbeeld is **focus:aanbieding**

   ```
   <srcSchema _cs="Marketing offers (cus)" created="2013-01-18 17:14:20.762Z" createdBy-id="0"
              desc="" entitySchema="xtk:srcSchema" extendedSchema="nms:offer" img="nms:offer.png"
              label="Marketing offers" labelSingular="Marketing offers" lastModified="2013-01-18 15:20:18.373Z"
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

   >[!CAUTION]
   >
   >Elk element moet tweemaal worden gedefinieerd. CDATA-typeelementen (&quot;_jst&quot;) kunnen personalisatievelden bevatten.
   >
   >Vergeet niet de databasestructuur bij te werken. Zie [deze sectie](../../configuration/using/updating-the-database-structure.md)voor meer informatie.

   >[!NOTE]
   >
   >U kunt het aanbiedingsschema uitbreiden om nieuwe velden toe te voegen in batch- en eenheidsmodus en in elke gewenste indeling (tekst, HTML en XML).

1. **De aanbiedingsformule uitbreiden om nieuwe velden te bewerken en een bestaand veld te wijzigen**

   Bewerk het invoerformulier **Aanbieding (nsm)** .

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

   >[!CAUTION]
   >
   >De velden van het formulier ( `<input>`) moeten verwijzen naar de CDATA-typeelementen die in het gemaakte schema zijn gedefinieerd.

   De rendering in het formulier met aanbiedingsweergaven ziet er als volgt uit:

   ![](assets/interaction_xmlmode_form.png)

   De velden **[!UICONTROL Title 2]** en **[!UICONTROL Price]** zijn toegevoegd en het **[!UICONTROL Destination URL]** veld wordt niet meer weergegeven.

1. **Een aanbieding maken**

   Raadpleeg Een aanbieding [maken voor meer informatie over het maken van aanbiedingen](../../interaction/using/creating-an-offer.md).

   In het volgende gebruiksgeval wordt de aanbieding als volgt vermeld:

   ![](assets/interaction_xmlmode_offer.png)

1. Goedkeuren of laten goedkeuren door iemand anders, dan activeren op de aanbiedingsruimte die bij de laatste stap is gecreëerd, zodat deze beschikbaar wordt gesteld in de gekoppelde live omgeving.
1. **De vraag van de motor en resultaat op de HTML- pagina**

   De aanroep van de interactieengine in de HTML-pagina ziet er als volgt uit:

   ```
   <script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=OE7&cb=alert" type="text/javascript">
   ```

   De waarde van de parameter &quot;**env**&quot; is de interne naam van de live omgeving.

   De waarde van de parameter &quot;**cb**&quot; is de naam van de functie die het XML-knooppunt moet interpreteren dat door de engine wordt geretourneerd. In ons voorbeeld opent de aangeroepen functie een modaal venster (alert() functie).

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

Het is mogelijk een XML-renderfunctie te gebruiken om een aanbiedingspresentatie te maken. Deze functie wijzigt het XML-knooppunt dat tijdens de aanroep naar de engine wordt geretourneerd naar de HTML-pagina.

1. Ga naar de aanbiedingsruimte en klik op de **[!UICONTROL Edit functions]** koppeling.
1. Selecteer **[!UICONTROL Overload the XML rendering function]**.
1. Ga naar het **[!UICONTROL XML rendering]** lusje en neem de gewenste functie op.

   De functie kan er als volgt uitzien:

   ```
   function (proposition) {
     delete proposition.@id;
     proposition.@newAttribute = "newValue";
   } 
   ```

![](assets/interaction_xmlmode_001.png)

