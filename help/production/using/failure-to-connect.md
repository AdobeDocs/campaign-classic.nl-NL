---
solution: Campaign Classic
product: campaign
title: Mislukte verbinding
description: Mislukte verbinding
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: cb6a2247e3b7617511aecf3d2d19985af0216494
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 2%

---


# Mislukte verbinding{#failure-to-connect}

De redenen voor een verbindingsprobleem kunnen meerdere zijn en zijn afhankelijk van verschillende contexten.

U kunt de volgende tests uitproberen. Neem contact op met de **Adobe Campaign-ondersteuning** als de verbindingsfout zich blijft voordoen.



<table> 
 <thead> 
  <tr> 
   <th>Controles<br /> </th> 
   <th>Resolutie<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td>Hebt u toegang tot internet vanaf uw computer?</td> 
   <td>Controleer of u verbinding kunt maken met websites op internet (bijvoorbeeld). Als u geen verbinding kunt maken, is het probleem op uw computer. Neem contact op met de systeembeheerder.</td>
  </tr>
  <tr> 
   <td>Kunt u via een andere service verbinding maken met de server die als host fungeert voor Adobe Campaign?</td> 
   <td>Verbind met de server via SSH of een andere manier. Als dit niet mogelijk is, heeft uw hostbedrijf een probleem. Neem contact op met de systeembeheerder.</td>
  </tr>
  <tr> 
   <td>Reageert de webserver?</td> 
   <td>Verbinding maken met de URL voor servertoegang van Adobe Campaign via een webbrowser: **" http(s):// <urlserver>`**. Als de server niet reageert, wordt de webserver gestopt op de computer. Neem contact op met de systeembeheerder van het hostbedrijf om de service opnieuw te starten.</td>
  </tr>
  <tr> 
   <td>Is Adobe Campaign correct geïntegreerd?</td> 
   <td>Aanmelden bij: **" http(s)://<urlserver>/r/test`* URL. De server moet het volgende berichttype retourneren

    &quot;
    &lt;redir status=&#39;OK&#39; date=&#39;YYY/MM/DD HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;hostname>&#39; localHost=&#39;&lt;server>&#39;/>
    &quot;
    
    Als u dit resultaat niet verkrijgt, controleer uw configuratie van de webserver of er rekening is gehouden met integratie.&lt;/td>
</tr>
  <tr> 
   <td>Is de module Adobe Campaign Web gestart?</td> 
   <td>
   Maak verbinding met de volgende URL: **" http(s)://<URLSERVER>/nl/jsp/logon.jsp`** * Als u een Tomcat Java-fout verkrijgt:

    Is de integratie van JAVA correct uitgevoerd? Adobe Campaign heeft een SUN JDK nodig.
    
    Het is geïntegreerd in het bestand **`[pad van toepassing]&quot;/nl6/customer.sh**
    
    * Als u een lege pagina krijgt:
    
    Is de Adobe Campaign Web module gestart? U kunt het volgende verkrijgen:
    
    &quot;
    nlserver
    pdumpHH:MM:SS > Toepassingsserver voor Adobe Campaign Classic (7.X YY.R build XXX@SHA1) van DD/MM/YYYY
    [...]
    web@default (27515) - 55,2 Mb
    [...]
    &quot;
    
    * Als dit niet het geval is:
    
    &quot;
    
    nlserver start web&quot;&lt;/td>
</tr>
  <tr>
  	<td>Controleer de algemene configuratie van de beveiligingszones.</td>
  	<td>Raadpleeg voor meer informatie over het configureren van beveiligingszones [dit gedeelte] (../../installation/using/configuring-campaign-server.md#define-security-zones)</td>
  </tr>
 </tbody> 
</table>
