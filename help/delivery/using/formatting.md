---
product: campaign
title: Opmaak
description: Opmaak
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Email Design
role: User, Developer, Data Engineer
exl-id: d9688dc4-20c6-4a9a-990f-465f39b2faa2
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1451'
ht-degree: 0%

---

# Opmaak{#formatting}

## JavaScript-sjablonen {#javascript-templates}

Een JavaScript-sjabloon is een HTML- of tekstdocument dat JavaScript-code bevat. Deze wordt op dezelfde manier samengesteld als e-mailinhoud in een leveringsactie.

### Identificatie van een JavaScript-template {#identification-of-a-javascript-template}

Een JavaScript-sjabloon wordt net als schema&#39;s en formulieren aangeduid met de naam en naamruimte ervan. Het wordt echter aanbevolen de optie **.js** aan de sjabloonnaam toe te voegen.

### Structuur van een JavaScript-sjabloon {#structure-of-a-javascript-template}

Voorbeeld van een opmaaksjabloon voor JavaScript HTML op basis van het schema &quot;cus:book&quot;:

```
<html>
  <body>
    <!-- Title of book -->
    <h1><%= content.@name %></h1>
    <ul>
      <% for each(var chapter in content.chapter) { %>
        <li><%= chapter.@name %></li>
      <% }%>
    </ul>
  </body>
</html>
```

De verschillende richtlijnen van JavaScript zijn als volgt:

* De gebieden van de fusie: toont de inhoud van de gegevens met de **`<%= <source> %>`** syntaxis waar `<source>` het brongebied van de te tonen gegevens is.
* Instructieblokken: voert een reeks JavaScript-instructies uit die tussen de tags &lt;% en %> staan.

Het **inhoud** voorwerp vertegenwoordigt het belangrijkste element van het document van inputXML.

In ons voorbeeld geeft de volgende regel de inhoud van de naam van het naamboek weer:

```
<h1><%= content.@name %></h1>
```

De volgende code herhaalt op het `<chapter>` inzamelingselement:

```
<% for each(var chapter in content.chapter) { %>
  <li><%= chapter.@name %></li>
<% }%>
```

De kenmerken en elementen van de inhoud worden weergegeven als JavaScript-objecten en respecteren de structuur van het brondocument.

**Voorbeeld**:

* **inhoud.@name**: wint de waarde van het &quot;naam&quot;attribuut van het belangrijkste element terug
* **inhoud.@`['name']`**: identiek aan de **inhoud.@name** syntaxis
* **content.chapter.length**: keert het aantal elementen op het `<chapter` inzamelingselement terug
* **content.chapter `[0]`.@name**: haalt de naam van het eerste `<chapter>` -element op
* **chapter.name ()**: keert de naam van het `<chapter>` element terug
* **chapter.parent ().name ()**: keert de naam van het ouderelement van `<chapter>` terug

>[!CAUTION]
>
>Omdat het &#39;-&#39;-teken is gereserveerd in de JavaScript-taal, moet het herstel van de waarde van elk kenmerk of element dat dit teken bevat, worden uitgevoerd via de `['<field>']` -syntaxis.
>
>Bijvoorbeeld: `content.@['offer-id']` .

Alle kracht van een programmeertaal (variabelen, lussen, voorwaardelijke tests, functies, enz.). ) is beschikbaar om het uitvoerdocument samen te stellen. SOAP API&#39;s zijn toegankelijk om het uitvoerdocument te verrijken.

Voorbeelden:

* Voorwaardelijke test:

  ```
  <% if (content.@number == 1 || content.@language == 'en') { %>
  <!-- Content to be displayed if test is true--> 
  <% } %>
  ```

* Functieaanroep:

  ```
  <!-- Displays a horizontal bar -->
  ;<% function DisplayHorizontalBar() { %>
    <hr/>
  <% } %> 
  
  <!-- The same function in a block  -->
  <% 
  function DisplayHorizontalBar2()
  {
    document.write('<hr/>');
  }
  %> 
  
  <!-- Returns the value in uppercase -->
  <% 
  function formatName(value)
  { 
    return value.toUpperCase(); 
  }
  %>
  
  <!-- Call functions -->
  <%= DisplayHorizontalBar1() %>
  <%= DisplayHorizontalBar2() %>
  <%= formatName(content.@name) %>
  ```

* Declaraties en variabele call:

  ```
  <%  var counter = 0; %>
  
  <%= counter += 10 %>
  ```

* Een naam van een ontvanger ophalen en weergeven met statische methoden:

  ```
  <% var recipient = nms.recipient.get(1246); %>
  <%= recipient.lastName %>
  ```

* Terugwinning en vertoning van een ontvankelijke naam met niet statische methodes:

  ```
  <% var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr="@id=1246"/>
      </where>
    </queryDef>);
  
    var recipient = query.ExecuteQuery();
  %>
  
  <%= recipient.@lastName %>
  ```

### Een JavaScript-sjabloon opnemen {#including-a-javascript-template}

U kunt een bibliotheek van functies of variabelen voor later gebruik vormen. Dit doen, voer het malplaatje van JavaScript met de **eval** functie in. Hiermee kunt u contexten verrijken met extra functies die zijn gedeclareerd in andere JavaScript-sjablonen.

**Voorbeeld**: het invoeren van het {**malplaatje 2} common.jsp.**

```
<% eval(xtk.javascript.get("cus:common.js").data);  %>
```

### Een JavaScript-sjabloon bewerken {#editing-a-javascript-template}

In de bewerkingszone kunt u de inhoud van de JavaScript-sjabloon vullen:

![](assets/d_ncs_content_form16.png)

>[!NOTE]
>
>Het bijbehorende schema van het gegevensmodel moet worden ingevuld voor de initialisatie van JavaScript-objecten.

Als u de voorvertoning van het uitvoerdocument wilt genereren, selecteert u op elk gewenst moment een inhoud en een uitvoerindeling (HTML, Tekst, XML) en klikt u op **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form17.png)

>[!NOTE]
>
>U hoeft de wijzigingen niet op te slaan om een voorvertoning van het uitvoerdocument weer te geven.

### Voorbeeld van het maken en gebruiken van een JavaScript-sjabloon {#example-of-how-to-create-and-use-a-javascript-template}

Hieronder vindt u de configuratie die is vereist voor het implementeren van het volgende inhoudsbeheer met behulp van een JavaScript-sjabloon:

![](assets/d_ncs_content_sample_1.png)

In dit voorbeeld worden de volgende stappen uitgevoerd:

1. Creeer het volgende schema (in dit geval: **neo:news**):

   ```
   <srcSchema _cs="Invitation (neo)"   entitySchema="xtk:srcSchema" img="xtk:schema.png" label="Invitation" mappingType="sql" name="news" namespace="neo" xtkschema="xtk:srcSchema">
   
     <enumeration basetype="string" default="en" name="language">
       <value label="Français" name="fr" value="fr"/>
       <value label="English" name="gb" value="gb"/>
     </enumeration>
   
     <enumeration basetype="string" name="css">
       <value label="Blue" name="bl" value="blue"/>
       <value label="Orange" name="or" value="orange"/>
     </enumeration>
   
     <element label="Intervenants" name="attendee">
       <key internal="true" name="id">
         <keyfield xpath="@id"/>
       </key>
       <attribute label="Name" name="name" type="string"/>
       <element label="Image" name="image" target="xtk:fileRes" type="link"/>
       <attribute label="Description" name="description" type="string"/>
       <attribute default="Gid()" label="Id" name="id" type="long"/>
     </element>
   
     <element label="Invitation" name="news" template="ncm:content" xmlChildren="true">
   
       <compute-string expr="@name"/>
       <attribute enum="language" label="Language" name="language" type="string"/>
       <attribute enum="css" label="Stylesheet" name="css" type="string"/>
       <attribute label="Title" name="title" type="string"/>
       <element label="Presentation" name="presentation" type="html"/>
       <attribute label="Date" name="date" type="date"/>
       <element label="Attendees list" name="attendeesList" ordered="true" ref="attendee" unbound="true"/>
   
     </element>
   </srcSchema>
   ```

1. Creeer de verbonden **[!UICONTROL Content management]** typevorm (**neo:news**)

   ```
   <form _cs="News (neo)" entitySchema="xtk:form"  img="xtk:form.png" label="News"  name="news" namespace="neo" type="contentForm" xtkschema="xtk:form">
   
     <container type="iconbox">
       <container label="Invitation">
         <input xpath="@langue"/>
         <input xpath="@css"/>
         <input xpath="@title"/>
         <input xpath="@date"/>
         <input xpath="presentation"/>
       </container>
   
       <container label="Intervenants">
         <container toolbarCaption="Liste des intervenants" type="notebooklist" xpath="attendeesList" xpath-label="@nom">
           <container>
             <input xpath="@nom"/>
             <input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
               <sysFilter>
                 <condition expr="@isImage = true"/>
               </sysFilter>
             </input>
             <input xpath="@description"/>
           </container>
         </container>
       </container>
     </container>
   
   </form>
   ```

1. Maak de JavaScript-sjablonen met de inhoud van berichten voor de indelingen HTML en Tekst.

   * In ons voorbeeld geldt voor HTML:

     ```
     <html>     
       <head>         
         <title>Newsletter</title>
          <style type="text/css">
           .body {font-family:Verdana, Arial, Helvetica, sans-serif; font-size:10px; color:#514c48; margin-left: auto; margin-right: auto;}
           .body table {width:748; border: solid 1px; cellpadding:0; cellspacing:0"}
          </style>
       </head>     
       <body>
         <p><center><%= mirrorPage %></center></p>
         <center>
           <table>      
            <tr>
             <td>                                                         
               <img src="[LOGO]"/>                                   
             </td>
             <td>
               <h1><%= content.@title %></h1>
             </td>
            </tr>
            <tr>
     
            <td>
             <div >                                    
               <h0><%= hello,</h0>                              
               <p><%= content.presentation %></p>                                          
     
               <h0>Useful information</h0>                              
               <p>                                  
                 <img src="[IMAGE 1]"/>When? <br/><%= formatDate(content.@date, "%2D %Bl %4Y") %> From 10 AM in your bookshop.</p><br/>                                       
               <p>                                  
                 <img src="[IMAGE 2]"/>Who? <br>Meet our favorite authors and illustrators and get a signed copy of their book.</p><br/>                                                         
               <p>                                  
                 <img src="[IMAGE 3]"/>Attendance is free but there is a limited number of seats: sign up now!</p>
           </div>
           </td>
     
             <td>                                                    
              <div style="text-align:left; width:210; height:400px; background:url([IMAGE DE FOND])">
     
                 <h0><%= participant %></h0>
                 <%
                 var i
                 var iLength = content.attendeesList.length()
                 for (i=0; i<iLength; i++)
                 { %>
                 <p>
                   <%= generateImgTag(content.attendeesList[i].@["image-id"]) %>  <%= content.attendeesList[i].@description %>
                 </p>  
                 <% }  
                 %>                              
              </div2>
             </td>
         </tr>
       </table>
     </center>
     </body>    
     </html>
     ```

   * Voor de tekst:

     ```
     <%= content.@title %>
     <%= content.presentation %>
     
     *** When? On <%= formatDate(content.@date, "%2D %Bl %4Y") %> From 10 AM in your bookshop.
     
     *** Who? Come and meet our favorite authors and illustrators and get a signed copy of their books. 
     
     *** Attendance is free but there is a limited number of seats: sign up now!
     
     Guests:
     ******************
     <%
     var i
     var iLength = content.attendeesList.length()
     //for (i=(iLength-1); i>-1; i--)
     for( i=0 ; i<iLength ; i++ )
       { %>
       Description <%= i %> : <%= content.attendeesList[i].@description %>
       <% }  
     %>
     ```

1. Maak nu de publicatiesjabloon die voor beide indelingen wordt gebruikt:

   * Voor HTML:

     ![](assets/d_ncs_content_sample_2.png)

   * Voor tekst:

     ![](assets/d_ncs_content_sample_3.png)

1. U kunt deze inhoudssjabloon dan gebruiken in uw leveringen.

   Voor meer op dit, verwijs naar [ Gebruikend een inhoudsmalplaatje ](using-a-content-template.md).

## XSL Stylesheets {#xsl-stylesheets}

Met XSLT kunt u een XML-document wijzigen in een uitvoerdocument. Afhankelijk van de uitvoermethode van de stijlpagina kan het resulterende document worden gegenereerd in HTML, platte tekst of een andere XML-structuur.

Deze transformatie wordt op zijn beurt in XML in een document gedetaillerd dat als stylesheet wordt bekend.

### Een stijlpagina identificeren {#identifying-a-stylesheet}

Een stijlpagina wordt geïdentificeerd door zijn naam en namespace, enkel als schema&#39;s en vormen. Het wordt echter aanbevolen de extensie **.xsl** toe te voegen aan de naam van de stijlpagina.

De identificatiesleutel van een stijlblad is een koord dat door namespace en de naam wordt gevormd die door een dubbelpunt wordt gescheiden; bijvoorbeeld: **cus:book.xsl**.

### Structuur van een stijlblad {#structure-of-a-stylesheet}

Voorbeeld van een opmaakstijlpagina voor HTML op basis van het voorbeeldschema &quot;cus:book&quot;:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>
  <!-- Point of entry of the stylesheet -->
  <xsl:template match="/book">
    <html>
      <body>
        <!-- Book title -->
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <!-- List of chapters -->
          <xsl:for-each select="child::chapter">
            <li><xsl:value-of select="@name"/></li>
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

Een stijlpagina is een XML-document dat aan de volgende regels voldoet:

* de kenmerkwaarden liggen tussen aanhalingstekens;
* een element moet een openingsmarkering en een sluitmarkering hebben;
* vervang de tekens &#39;&lt;&#39; of &#39;&amp;&#39; door de entiteiten **&#39;&lt;&#39;** of **&#39;&amp;&#39;** ,
* elk element van XSL moet **xsl** gebruiken namespace.

Een stijlpagina moet beginnen met de markering voor het XSL-hoofdelement **`<xsl:stylesheet>`** en eindigen met de markering **`</xsl:stylesheet>`** . De XSL-naamruimte moet als volgt worden gedefinieerd in de openingsmarkering:

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

Het element **`<xsl:output>`** geeft de indeling van het gegenereerde document op. Geef de gewenste set tekens en de uitvoerindeling op.

```
<xsl:output encoding="ISO-8859-1" method="html"/>
```

In de volgende instructies wordt de configuratie van de stijlpagina voor de opmaak van het uitvoerdocument beschreven.

```
<xsl:template match="/book">
  <html>
    <body>
      <!-- Book title -->
      <h1><xsl:value-of select="@name"/></h1>
      <lu>
        <!-- List of chapters -->
        <xsl:for-each select="child::chapter">
          <li><xsl:value-of select="@name"/></li>
        </xsl:for-each>
      </lu>
    </body>
  </html>
</xsl:template>
```

Door gebrek, zoekt de bewerker van XSLT het **malplaatje** dat op de wortel of de belangrijkste knoop van het document van inputXML van toepassing is. De bouw van het outputdocument begint met dit **malplaatje**.

In ons voorbeeld wordt een HTML-pagina gegenereerd vanuit het schema &quot;cus:book&quot; door de naam van het boek en de lijst met hoofdstukken weer te geven.

>[!NOTE]
>
>Raadpleeg een XSLT-referentiedocument voor meer informatie over de XSLT-taal.

### HTML/XML weergeven {#displaying-html-xml}

Om een **html** gebied te tonen, gebruik **onbruikbaar maken-output-escaping= &quot;ja&quot;** optie van de **`<xsl:value-of>`** richtlijn. Zo voorkomt u dat tekens door hun XML-entiteit worden vervangen (bijvoorbeeld &lt; met &lt;).

De **`<xsl:text>`** richtlijn met **disable-output-escaping= &quot;ja&quot;** optie laat u de markeringen van JavaScript voor verpersoonlijkingsgebieden of voorwaardelijke tests opnemen.

Voorbeelden:

* De inhoud van een veld van het type &quot;html&quot; weergeven:

  ```
  <xsl:value-of select="summary" disable-output-escaping="yes"/>
  ```

* Het verpersoonlijkingsgebied **&lt;%= receiving.email %>** opnemen:

  ```
  <xsl:text disable-output-escaping="yes"><%= recipient.email %></xsl:text>
  ```

* Het toevoegen van de voorwaardelijke test **&lt;% als (ontvanger.language == &#39;en&#39;) `{` %>**:

  ```
  <xsl:text disable-output-escaping="yes"><% if (recipient.language == 'en') { %></xsl:text>
  ```

### Inclusief stijlbladen {#including-stylesheets}

Het is mogelijk om een bibliotheek van malplaatjes of variabelen op te bouwen die onder verscheidene stylesheets moeten worden gedeeld. Het &quot;longMonth&quot;**malplaatje**, hierboven voorgesteld, is een typisch voorbeeld van het voordeel om van een malplaatje ver in een stijlblad de plaats te bepalen zodat het later opnieuw kan worden gebruikt.

De aanwijzing **`<xsl:include>`** geeft de naam aan van de stijlpagina die in het document moet worden opgenomen.

**Voorbeeld**: met inbegrip van het &quot;common.xsl&quot;stijlblad.

```
<? xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:include href="common.xsl"/> 
  <xsl:output encoding="ISO-8859-1" method="jsp" indent="yes"/>
  ...
</xsl:stylesheet>
```

>[!NOTE]
>
>De naam van de naamruimte mag niet worden ingevoerd in de verwijzing naar de stijlpagina die moet worden opgenomen. Deze stijlpagina wordt standaard gemaakt met de naamruimte van de gebruiker.

### Een stijlpagina bewerken {#editing-a-stylesheet}

Met de bewerkingszone kunt u de inhoud van het stijlblad vullen:

![](assets/d_ncs_content_form14.png)

Als u een voorvertoning van het uitvoerdocument wilt genereren, selecteert u een inhoudsinstantie en de indeling (HTML, Tekst, XML) en klikt u op **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form15.png)

>[!NOTE]
>
>U hoeft de wijzigingen in de stijlpagina niet op te slaan om de voorvertoning van het uitvoerdocument weer te geven.

## Afbeeldingsbeheer {#image-management}

### Verwijzing naar afbeelding {#image-referencing}

Naar de afbeeldingen die u opgeeft in het HTML-uitvoerdocument, kan worden verwezen met absolute of relatieve verwijzingen.

Het relatieve van verwijzingen voorzien laat u URL van de server ingaan die de beelden in **bevat NcmRessourcesDir** en **NcmRessourcesDirPreview** opties. Deze opties bevatten de locatie van afbeeldingen die u wilt publiceren en voorvertonen in de Adobe Campaign-clientconsole.

Deze twee opties zijn toegankelijk via het scherm voor optiebeheer in de map **[!UICONTROL Administration > Platform > Options]** .

**Voorbeeld**:

* NcmResourcesDir = &quot;https://server/images/&quot;
* NcmResourcesDirPreview = &quot;x:/images/&quot;

Tijdens stijlpaginaverwerking, wordt het **_resPath** attribuut op het belangrijkste element van het document van inputXML automatisch gevuld met één of andere opties afhankelijk van context (voorproef of publicatie).

Voorbeeld van het gebruik van de plaatsingsoptie voor afbeeldingen en het gebruik ervan voor een afbeelding:

```
<img src="<%= content.@_resPath %>/newsletter/image.png"/>
```

>[!NOTE]
>
>We raden u aan een variabele te declareren die de referentie bevat van de server waar de afbeeldingen zijn opgeslagen (&quot;resPath&quot; in ons voorbeeld).

### Overheidsmiddelen gebruiken {#using-public-resources}

U kunt **[!UICONTROL Public resources]** ook gebruiken om afbeeldingen te declareren en te uploaden naar de server, afhankelijk van de instantie-instellingen die u hebt ingevoerd in de implementatietovenaar.

Vervolgens kunt u deze afbeeldingen in de inhoud oproepen. Hiervoor gebruikt u de volgende syntaxis in het inhoudsbeheerschema:

```
<element label="Image" name="image" target="xtk:fileRes" type="link"/>
```

In het formulier wordt het veld voor het selecteren van de afbeelding toegevoegd met de volgende syntaxis:

```
<input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
    <sysFilter>
      <condition expr="@isImage = true"/>
    </sysFilter>
  </input>
```

>[!NOTE]
>
>Voor meer op **[!UICONTROL Public resources]** en hoe te om hen te vormen en te gebruiken, verwijs naar [ deze sectie ](../../installation/using/deploying-an-instance.md#managing-public-resources).

## Datumweergave {#date-display}

In het XML-invoerdocument worden de datums opgeslagen in de interne XML-indeling: **`YYYY/MM/DD HH:MM:SS`** (voorbeeld `2018/10/01 12:23:30` ).

Adobe Campaign biedt functies voor datumopmaak voor de JavaScript-sjablonen en XSL-opmaakmodellen die hieronder worden beschreven.

### JavaScript-datumnotatie {#javascript-date-formatting}

Om een datum in het gewenste formaat te tonen, verstrekt Adobe Campaign de **formatDate** functie die als input de inhoud van de datum en een koord neemt die het outputformaat met de volgende syntaxis specificeren: **%4Y/%2M/%2D %2H%2N%2S** specificeren

Voorbeelden:

* Toon de datum in het **31/10/2018** formaat:

  ```
   <%= formatDate(content.@date, "%2D/%2M/%4Y") %>
  ```

* Toon de datum in het **formaat van juli 2018**:

  ```
  <%
   function displayDate(date)
    {
      var aMonth = 
      [ 'January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December' ];
  
      var month = formatDate(content.@date, "%2M")
      var year = formatDate(content.@date, "%4Y")
  
      return aMonth[month-1]+" "+year;
    }
  %>
  
  <%= displayDate(content.@date) %>
  ```

### XSL-datumopmaak {#xsl-date-formatting}

Er is geen standaardfunctie voor datumbeheer in XSLT-syntaxis. Om een datum in het gewenste formaat te tonen, verstrekt Adobe Campaign de externe functie **datum-formaat**. Deze functie neemt als invoer de inhoud van de datum en een tekenreeks die de uitvoerindeling opgeeft met de volgende syntaxis: **%4Y/%2M/%2D %2H%2N%2S**

Voorbeelden:

* Om de datum in **01/10/2018** formaat te tonen:

  ```
  <xsl:value-of select="external:date-format(@date, '%2D/%2M/%4Y')"/>
  ```

* Om de datum in het **formaat van juli 2018** te tonen:

  ```
  <!-- Returns the month in the form of a string with the month number as input -->
  <xsl:template name="longMonth">
    <xsl:param name="monthNumber"/>
  
    <xsl:choose>
      <xsl:when test="$monthNumber = 1">January</xsl:when>
      <xsl:when test="$monthNumber = 2">February</xsl:when>
      <xsl:when test="$monthNumber = 3">March</xsl:when>
      <xsl:when test="$monthNumber = 4">April</xsl:when>
      <xsl:when test="$monthNumber = 5">May</xsl:when>
      <xsl:when test="$monthNumber = 6">June</xsl:when>
      <xsl:when test="$monthNumber = 7">July</xsl:when>
      <xsl:when test="$monthNumber = 8">August</xsl:when>
      <xsl:when test="$monthNumber = 9">September</xsl:when>
      <xsl:when test="$monthNumber = 10">October</xsl:when>
      <xsl:when test="$monthNumber = 11">November</xsl:when>
      <xsl:when test="$monthNumber = 12">December</xsl:when>
    </xsl:choose>
  </xsl:template> 
  
  <!-- Display date -->
  <xsl:call-template name="longMonth">
    <xsl:with-param name="monthNumber">
      <xsl:value-of select="external:date-format(@date, '%2M')"/>
    </xsl:with-param>
  </xsl:call-template>
   <xsl:value-of select="external:date-format(@date, '%4y')"/>
  ```
