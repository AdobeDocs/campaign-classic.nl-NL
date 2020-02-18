---
title: Tags op uw site invoegen
seo-title: Tags op uw site invoegen
description: Tags op uw site invoegen
seo-description: null
page-status-flag: never-activated
uuid: e5e4a431-2093-4d5a-acd2-0040b6ce3519
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 57988b00-62cc-43d3-a2eb-bfed5bff7dc1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Tags op uw site invoegen{#inserting-tags-in-your-site}

## Eenvoudige methode {#simple-method}

Deze methode bestaat uit het verzenden van een HTTP-aanroep naar de omleidingsserver door een **`<img>`** HTML-tag in te voegen in de HTML-broncode van de webpagina die u wilt bijhouden.

>[!IMPORTANT]
>
>Deze methode gebruikt de cookies die door de webbrowser worden verzonden om de ontvanger te identificeren en is niet 100% betrouwbaar.

**Voorbeeld**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

De ingevoegde tag neemt contact op met de omleidingsserver.

![](assets/d_ncs_integration_webtracking_structure2.png)

Wanneer u een pagina definieert die in de console moet worden bijgehouden, kunt u een voorbeeld van een webtrackingtag genereren om deze te kopiëren en in de broncode van uw webpagina te plakken.

Als u echter tags van het type TRANSACTION gebruikt, moet u de voorbeeldtag wijzigen met JavaScript om de transactiegegevens (hoeveelheid, aantal items) en alle informatie die in een extensieschema is gedefinieerd in te voegen.

### Statische invoeging van tags {#static-insertion-of-tags}

Als u statische tags wilt invoegen, kopieert en plakt u gewoon de tags die door de console zijn gegenereerd of die u handmatig hebt gemaakt in de bron van uw webpagina.

**Voorbeeld**: invoeging van een tag voor webtracering op een pagina waarop een formulier wordt weergegeven.

```
<html>
  <...>
  <body>
  <script>
      document.write("<img height='0' width='0' alt='' src='https://localhost/r/" + Math.random().toString() + "?tagid=home'>");
    </script>
    <noscript>
     <img height='0' width='0' alt='' src='https://localhost/r/?tagid=home'>
    </noscript>
    <h1>My site</h1>
    <form action="http://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

Een webtrackingtag van het type TRANSACTION wordt ingevoegd in de bevestigingspagina (&quot;amount.md&quot;).

```
<html>
  <body>
    <script>
      function getURLparam(name) 
      {
        var m = location.search.match new RegExp("[?&]" + name + "=([^&]+)"));
        return m ? unescape(m[1]) : "";
      }
 
       var params = "https://localhost/r/" + Math.random().toString() + "?tagid=amount&amount="
                      +getURLparam("amount")+"&article="+getURLparam("quantity");
       document.write("<img height='0' width='0' src='"+params+"'/>");
    </script>

    <h1>Approval confirmation</h1>
  </body>
</html>
```

### Dynamisch genereren van tags voor webtracking {#dynamic-generation-of-web-tracking-tags}

Wanneer uw webpagina&#39;s dynamisch worden gegenereerd, kunt u de tag web tracking tijdens het genereren van de pagina toevoegen.

**Voorbeeld**: Webspatiëring toegevoegd aan JSP&#39;s.

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <img height='0' width='0' alt='' src='https://localhost/r/<%=new Random().nextInt()%>?tagid=home'>
    <h1>My site</h1>
    <form action="https://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <%  
      String strParams = new Random().nextInt() + "?tagid=amount";
      strParams += "&amount="+request.getParameter("amount");
      strParams += "&article="+request.getParameter("quantity");
    %>
    <img height='0' width='0' alt=''
     src='http://localhost/r/<%=strParams%>'>
    <h1>Approval confirmation</h1>
    </body>
</html>
```

## Optimale methode {#optimum-method-}

Als u wenst om de informatie te controleren die naar de omleidingsserver wordt verzonden, is de betrouwbaarste manier de vraag van HTTP synchroon uit te voeren zelf gebruikend een pagina die taal produceert.

De URL die u bouwt, moet de syntaxisregels naleven die in de volgende markering van het [Web worden bepaald: definitie](../../configuration/using/web-tracking-tag--definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>Voor omleiding en webtracering worden cookies gebruikt. Het is belangrijk dat de webserver die de synchrone HTTP-aanroep uitvoert zich in hetzelfde domein bevindt als de omleidingsserver. De verschillende HTTP-uitwisselingen moeten de cookies &#39;id&#39;, &#39;uuid&#39; en &#39;uuid230&#39; overbrengen.

**Voorbeeld**: Dynamische generatie in Java, met verificatie van ontvangers op basis van hun accountnummer.

```
[...]
  // Recipient account, amount and articles
  String strAccount = request.getParameter("account");
  String strAmount = request.getParameter("amount");
  String strArticle = request.getParameter("article");

  StringBuffer strCookies = new StringBuffer();
  String strSetCookie = null;

  // Get cookies from client request
  Cookie[] cookies = request.getCookies();
  for(int i=0; i< cookies.length; i++ )
  {
    Cookie c = cookies[i];
    String strName = c.getName();
    if( strName.equals("id") || strName.equals("uuid") || strName.equals("uuid230") )
      // Helper function to add cookies in string
      AddCookie(strCookies, c);
  }
  // Now perform a synchronous HTTP request to inform redirection server
  // Add a tagid in auto-discover mode, and a default jobId to use (in hexa)
  StringBuffer strURL = new StringBuffer("https://www.adobe.com/r/a?tagid=cmd_page%7Ct&jobid=27EE");
  if( strAccount != null )
    AddParameter(strURL, "rcpid", "saccount="+strAccount);
  if( strAmount != null )
    AddParameter(strURL, "amount", strAmount);
  if( strArticle != null )
    AddParameter(strURL, "article", strArticle);
  
  URL url = new URL(strURL.toString());
  HttpURLConnection connection = (HttpURLConnection)url.openConnection();
  // Add the client cookies
  if( strCookies.length() > 0 )
    connection.setRequestProperty("Cookie", strCookies.toString());

  int errcode = connection.getResponseCode();

  // Now add the Adobe Campaign cookies if the server returned one :
  if( errcode == 200 )
  {
    strSetCookie = connection.getHeaderField("Set-Cookie");
    if( strSetCookie != null && strSetCookie.length() > 0 )
      response.addHeader("Set-Cookie", strSetCookie);
  }
  [...]
```

