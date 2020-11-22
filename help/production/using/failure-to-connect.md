---
solution: Campaign Classic
product: campaign
title: Mislukte verbinding
description: Mislukte verbinding
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---


# Mislukte verbinding{#failure-to-connect}

De redenen hiervoor kunnen meerdere zijn en zijn afhankelijk van verschillende contexten.

Controleer de algemene configuratie van de beveiligingszones.

>[!NOTE]
>
>Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#defining-security-zones)voor meer informatie over het configureren van beveiligingszones.

Controleer de volgende informatie:

1. **Netwerkcontroles**

   * Hebt u toegang tot internet vanaf uw computer?

      Controleer of u verbinding kunt maken met websites op internet (bijvoorbeeld). Als u geen verbinding kunt maken, is het probleem op uw computer. Neem contact op met de systeembeheerder.

   * Kunt u via een andere service verbinding maken met de server die als host fungeert voor Adobe Campaign?

      Verbind met de server via SSH of een andere manier. Als dit niet mogelijk is, heeft uw hostbedrijf een probleem. Neem contact op met de systeembeheerder.

1. **Controles aan de serverzijde** van het Web (IIS/apache/etc.)

   * Reageert de webserver?

      Verbinding maken met de URL voor servertoegang van Adobe Campaign via een webbrowser: **http(en)://`<urlserver>`**. Als de server niet reageert, wordt de webserver gestopt op de computer. Neem contact op met de systeembeheerder van het hostbedrijf om de service opnieuw te starten.

   * Is Adobe Campaign correct geïntegreerd?

      Aanmelden bij: **http(s):/// `<urlserver>`/r/test** URL. De server moet het volgende berichttype retourneren

      ```
      <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      ```

      Als u dit resultaat niet verkrijgt, controleer in uw de serverconfiguratie van het Web dat de integratie in acht wordt genomen.

1. **Controles aan de zijde van de Adobe Campaign**

   * Is de module Adobe Campaign Web gestart?

      Maak verbinding met de volgende URL: **http(s)://`<URLSERVER>`/nl/jsp/logon.jsp**

      * Als u een Tomcat Java-fout verkrijgt:

         Is de integratie van JAVA correct uitgevoerd? Adobe Campaign heeft een SUN JDK nodig.

         Het is geïntegreerd in het bestand **`[path of application]`/nl6/customer.sh**

      * Als u een lege pagina krijgt:

         Is de module Adobe Campaign Web gestart? U zou moeten verkrijgen:

         ```
         nlserver pdump
         HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
         [...]
         web@default (27515) - 55.2 Mb
         [...]
         ```

      * Zo niet, start u de toepassing opnieuw met de volgende opdracht:

         ```
         nlserver start web
         ```
>[!NOTE]
>
>Als u een reactie van het volgende type krijgt wanneer u de Adobe Campaign-modules opsomt: **nlserver pdump**
>HH:MM:SS > Toepassingsserver voor Adobe Campaign Classic (7.X YY.R build XXX@SHA1) van DD/MM/YYYY Geen taken U moet de volledige Adobe Campaign-toepassing opnieuw starten. Hiervoor gebruikt u de volgende opdracht: **nlserver watchdog -svc -noconsole **
