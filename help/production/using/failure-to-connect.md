---
solution: Campaign Classic
product: campaign
title: Mislukte verbinding
description: Mislukte verbinding
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 85fae38f864b031f069058dae79ce6753dc4bf03
workflow-type: tm+mt
source-wordcount: '370'
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
<td>Aanmelden bij: <b>http(s):///&lt;urlserver&gt;/r/test</b> URL. De server moet het volgende berichttype retourneren: &lt;redir status='OK' date='YYY/MM/DD HH:MM:SS' build='XXXX' host='&lt;hostname&gt;' localHost='&lt;server&gt;'/&gt;Als u dit resultaat niet verkrijgt, controleert u uw webserverconfiguratie of er rekening is gehouden met integratie.</td>
</tr>
<tr> 
<td>Maak verbinding met de volgende URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Als u een Tomcat Java-fout verkrijgt, controleert u of de JAVA-integratie correct wordt uitgevoerd. Het is geïntegreerd in het bestand [pad van toepassing]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Maak verbinding met de volgende URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Als u een lege pagina krijgt, controleer of de module van het Web van Adobe Campaign is begonnen. Het PDump-bestand van de opdrachtserver moet de toepassingsserver retourneren voor Adobe Campaign Classic (7.X YY.R build XXX@SHA1) van DD/MM/YYYY. Zo niet, start de module opnieuw met het opdrachtendserver-startweb</td>
</tr>
<tr>
<td>Controleer de algemene configuratie van de beveiligingszones.</td>
<td>Raadpleeg <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>deze sectie voor meer informatie over het configureren van beveiligingszones.</a></td>
</tr>
<tr>
<td>De pdump van de bevelserver keert <b>Geen taken terug</b></td>
<td>U moet de hele Adobe Campaign-toepassing opnieuw starten. Hiervoor gebruikt u de volgende opdracht: <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
