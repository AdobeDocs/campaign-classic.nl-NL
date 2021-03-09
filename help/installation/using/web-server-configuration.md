---
solution: Campaign Classic
product: campaign
title: Webserverconfiguratie
description: Leer meer over Web-server configuratie belangrijkste beste praktijken.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Configuratie webserver {#web-server-configuration}

Hieronder vindt u een aantal van de belangrijkste aanbevolen werkwijzen voor Apache/IIS-configuratie (webserver).

* Standaardfoutpagina&#39;s wijzigen.

* Oude SSL-versie en -ciphers uitschakelen:

   **Bewerk /etc/apache2/mods-available/ssl.conf op Apache**. Hier volgt een voorbeeld:

   * SSLProProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **Voor IIS**  (zie de  [documentatie](https://support.microsoft.com/en-us/kb/245030)), voer de volgende configuratie uit:

   * Registersubsleutel toevoegen in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Om het systeem toe te laten om de protocollen te gebruiken die niet door gebrek (zoals TLS 1.2) zullen worden besproken, verander de DWORD waardegegevens van de waarde DisabledByDefault in 0x0 in de volgende registratiesleutels onder **Protocols** sleutel:

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **SSL x.0 uitschakelen**

   SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: DWORD-waarde (32 bits) tot 1

   SCHANNEL\Protocols\SSL 3.0\Server: Ingeschakeld: DWORD-waarde (32 bits) tot 0

* Verwijder de methode **TRACE**:

   **Bewerk in Apache** de map /etc/apache2/conf.d/security: TracerenInschakelen  **uit**

   **Voor IIS**  (zie de  [documentatie](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), voer de volgende configuratie uit:

   * Zorg ervoor dat **Verzoek het Filtreren** de roldienst of de eigenschap geïnstalleerd is.
   * Klik in het deelvenster **Verzoek filteren** op het tabblad Werkwoorden van HTTP en klik vervolgens op Verwerping weigeren. Voer in het deelvenster Handelingen TRACE in het dialoogvenster Openen in.

* Verwijder de banner:

   **Bewerk /etc/apache2/conf.d/security op Apache**:

   * ServerSignature **Off**
   * ServerTokens **Prod**

   **Voor IIS**  (zie de  [documentatie](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), voer de volgende configuratie uit:

   * Installeer **URLScan**.
   * Bewerk het bestand **Urlscan.ini** om **RemoveServerHeader=1** te hebben


* Beperk de querygrootte om te voorkomen dat belangrijke bestanden worden geüpload:

   **Voor Apache**  (zie de  [documentatie](http://httpd.apache.org/docs/2.2/mod/core.html#limitrequestbody)), voeg de  **** LimitRequestBodyDirective (grootte in bytes) in / directory toe.

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **Voor IIS**  (zie de  [documentatie](http://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), plaats  **maxAllowedContentLength**  (maximum toegestane inhoudslengte) in de inhoud het filtreren opties.

Verwante onderwerpen:

* [Adobe Marketing Cloud-compatibiliteitsoverzicht](https://marketing.adobe.com/resources/help/en_US/xref/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf)  (PDF)
* [Adobe Campaign Security-overzicht](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf)  (PDF)
