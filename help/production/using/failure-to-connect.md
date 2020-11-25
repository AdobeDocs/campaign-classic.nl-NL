---
solution: Campaign Classic
product: campaign
title: Mislukte verbinding
description: Mislukte verbinding
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 57063c1ed0100b171bda93e273c399c40d8e980a
workflow-type: tm+mt
source-wordcount: '343'
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
   <td>Verbinding maken met de URL voor servertoegang van Adobe Campaign via een webbrowser: <b>http(s):// &lt;urlserver&gt;</b>. Als de server niet reageert, wordt de webserver gestopt op de computer. Neem contact op met de systeembeheerder van het hostbedrijf om de service opnieuw te starten.</td>
  </tr>
  <tr> 
   <td>Is Adobe Campaign correct geïntegreerd?</td> 
   <td>Aanmelden bij: <b>http(s):///&lt;urlserver&gt;/r/test</b> URL. De server moet het volgende berichttype retourneren:

    &lt;pre>
    &lt;redir status=&#39;OK&#39; date=&#39;YYYY/MM/DD HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;hostname>&#39; localHost=&#39;&lt;server>&#39;/>
    &lt;/pre>
Als u dit resultaat niet verkrijgt, controleer in uw de serverconfiguratie van het Web dat de integratie in acht wordt genomen.</td>
</tr>
  <tr> 
   <td>Is de module Adobe Campaign Web gestart?</td> 
   <td>Maak verbinding met de volgende URL: <b>http(s)://&gt;URLSERVER&lt;/nl/jsp/logon.jsp</b>* Als u een Tomcat Java-fout verkrijgt:

Is de integratie van JAVA correct uitgevoerd? Adobe Campaign heeft een SUN JDK nodig.

Het is geïntegreerd in het bestandspad [van de toepassing]/nl6/customer.sh

* Als u een lege pagina krijgt:
Is de module Adobe Campaign Web gestart? U zou moeten verkrijgen:

<pre>
nlserver pdumpHH:MM:SS &gt; Toepassingsserver voor Adobe Campaign Classic (7.X YY.R build XXX@SHA1) van DD/MM/YYYY[...]web@default (27515) - 55,2 Mb[...]
</pre>
* Zo niet, start u de toepassing opnieuw met de volgende opdracht:

<pre>        
nlserver start web
</pre>
</td>
</tr>
  <tr>
  	<td>Controleer de algemene configuratie van de beveiligingszones.</td>
  	<td>Raadpleeg voor meer informatie over het configureren van beveiligingszones [dit gedeelte] (../../installation/using/configuring-campaign-server.md#define-security-zones)</td>
  </tr>
 </tbody> 
</table>
