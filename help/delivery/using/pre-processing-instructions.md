---
solution: Campaign Classic
product: campaign
title: Voorverwerkingsinstructies voor bijgehouden URL's
description: Meer informatie over instructies voor voorbewerking die moeten worden gebruikt om de URL van een e-mailbericht te scripten, zodat deze nog steeds wordt bijgehouden.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 768fe62db4efd1217c22973c7e5dc31097d67bae
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 1%

---


# Voorverwerkingsinstructies {#pre-processing-instructions}

U kunt een specifieke syntaxis in de bezorginhoud gebruiken om instructies toe te voegen en de URL van het bijgehouden e-mailbericht te scripten. De &lt;%@-instructies zijn geen JavaScript: Deze syntaxis is specifiek voor Adobe Campaign.

Zij zijn alleen van toepassing in de context van leveringsinhoud. Dit is de enige manier om een script te maken voor de URL van een e-mail en deze nog steeds te laten bijhouden (behalve URL-parameters). Deze kunnen worden beschouwd als een automatische kopie/plakbewerking die tijdens de afleveringsanalyse is toegepast voordat de koppelingen naar de track worden gedetecteerd.

Er zijn drie typen instructies:

* &quot;**include**&quot;: vooral om sommige code in opties, verpersoonlijkingsblokken, externe dossiers, of pagina&#39;s te factoreren
* &quot;**value**&quot;: toegang geven tot velden van levering, leveringsvariabelen en aangepaste objecten die in de levering zijn geladen
* &quot;**foreach**&quot;: om een array te herhalen die als een aangepast object is geladen.

Zij kunnen direct van de leveringstovenaar worden getest. Ze worden toegepast in de voorvertoning van de inhoud en wanneer u op de knop Tekstspatiëring klikt, wordt de lijst met URL&#39;s weergegeven.

## [!DNL include] {#include}

De volgende voorbeelden worden het meest gebruikt:

* De koppeling voor de spiegelpagina opnemen: `<%@ include view="MirrorPage" %>`
* URL spiegel: &quot;Weergeven als een `<a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page"`
* URL zonder abonnement: `<%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>`
* Andere voorbeelden:
   * `<%@ include file='http://www.google.com' %>`
   * `<%@ include file='file:///X:/france/service/test.html' %>`
   * `<%@ include option='NmsServer_URL' %>`

Gebruik de verpersoonlijkingsknoop in de leveringstovenaar om de correcte syntaxis te krijgen.

## [!DNL value] {#value}

Deze instructie geeft toegang tot parameters van de levering die voor alle ontvangers constant zijn.

Syntaxis:

`<%@ value object="myObject" xpath="@myField" index="1" %>`

Waar:

* **[!DNL object]**: naam van het object (voorbeeld: levering, provider, enzovoort).
Object kan:
   * &quot;levering&quot;: voor de huidige levering (zie details en beperkingen in de onderafdeling hieronder).
   * &quot;provider&quot;: voor de huidige leverancier/het verpletteren (nms:externalAccount).
   * Een extra scriptobject: als een object in de context wordt geladen via: **Eigenschappen** > **Personalisatie** > **Objecten toevoegen in de uitvoeringscontext**.
   * Item van de foreach-lus: zie de onderstaande sectie [Foreach](#foreach).
* **[!DNL xpath]**: xpath of the field.
* **[!DNL index]** (optioneel): als  **[!DNL object]** een array is (voor extra scriptobjecten), index item in de array (Begint bij 0).

### [!DNL delivery] object {#delivery-object}

Voor personalisatie van e-mail, is het leveringsvoorwerp op twee manieren toegankelijk:

* In JavaScript. Bijvoorbeeld: `<%= delivery.myField %>`.

   In de levering van het JavaScript-object worden aangepaste velden niet ondersteund. Zij werken in de voorproef, maar niet in MTA omdat MTA tot het out-of-the-box leveringsschema kan slechts toegang hebben.

* Via `<%@ value object="delivery"` voorbewerking.

Voor de instructie `<%@ value object="delivery" xpath="@myCustomField" %>` geldt een andere beperking voor leveringen die via mid-sourcing worden verzonden. Het aangepaste veld @myCustomField moet aan de nms worden toegevoegd:leveringsschema op zowel marketing- als midsourcingsplatforms.

>[!NOTE]
>
>Gebruik de volgende syntaxis voor leverparameters/variabelen (met behulp van het leveringsobject):
>
>`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### [!DNL value] in een JavaScript-sectie  {#value-in-javascript}

Als u het gebruik van &lt;%@-waarde in JavaScript-secties wilt toestaan, worden twee speciale objecten vervangen door &lt;% en %>:

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

Bijvoorbeeld:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## [!DNL foreach] {#foreach}

Met deze instructie kunt u een herhaling uitvoeren op een array van objecten die in de levering zijn geladen om afzonderlijke koppelingen bij te houden die betrekking hebben op de objecten.

Syntaxis:

`<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>`

Waar:

* &quot;object&quot;: De naam van het object waarvan moet worden begonnen, is doorgaans een extra scriptobject, maar het kan een levering zijn.
* &quot;xpath&quot; (optioneel): xpath of the collection to loop on. De standaardwaarde is &quot;.&quot;, wat betekent dat het object de array is die moet worden doorlopen.
* &quot;index&quot; (optioneel): als xpath niet &quot;.&quot; is en object is een array zelf, itemindex van object (begint bij 0).
* &quot;item&quot; (optioneel): naam van een nieuw object dat toegankelijk is met &lt;%@-waarde in de foreach-lus. Standaard met de naam van de koppeling in het schema.

Voorbeeld:

Laad in de leveringseigenschappen/personalisatie een array met artikelen en een tabel met de relatie tussen ontvanger en artikelen.

Het weergeven van koppelingen naar deze artikelen kan eenvoudig met een JavaScript worden uitgevoerd:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Met deze oplossing worden de koppelingen naar alle artikelen zonder onderscheid bijgehouden. U kunt weten dat een ontvanger op een artikelkoppeling heeft geklikt, maar u kunt niet weten welk artikel.

De oplossing is:

1. Laad alle mogelijke artikelen vooraf in een extra scriptarray van de levering - articleList[] - wat betekent dat er een eindig aantal mogelijke artikelen moet zijn.
1. Schrijf een JavaScript-functie aan het begin van de inhoud.

   ```
   <%@ value object='startScript' %>
   function displayArticle(articleId)
   {
     <%@ foreach object="articleList" item="article" %>
       if( articleId == <% value object="article" xpath="@id" %> ) 
       {
         <%@ value object='endScript' %>
           <a href="http://nl.net?a.jsp?article=<%@ value object="article" xpath="@id" %>">article</a>
         <%@ value object='startScript' %>
       } 
     <%@ end @%>
   }
   <%@ value object='endScript' %>
   ```
1. Geef het artikel weer door de functie aan te roepen.

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```

