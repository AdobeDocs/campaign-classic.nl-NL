---
product: campaign
title: Webserverconfiguratie
description: Leer meer over Web-server configuratie belangrijkste beste praktijken.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Webserverconfiguratie {#web-server-configuration}

![](../../assets/v7-only.svg)

Hieronder vindt u een aantal van de belangrijkste aanbevolen werkwijzen voor Apache/IIS-configuratie (webserver).

* Standaardfoutpagina&#39;s wijzigen.

* Oude SSL-versie en -ciphers uitschakelen:

   **Op Apache**, bewerkt u /etc/apache2/mods-available/ssl.conf. Hier volgt een voorbeeld:

   * SSLProProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **Op IIS** (zie de [documentatie](https://support.microsoft.com/en-us/kb/245030)), voert de volgende configuratie uit:

   * Registersubsleutel toevoegen in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Om het systeem toe te laten om de protocollen te gebruiken die niet door gebrek (zoals TLS 1.2) zullen worden besproken, verander de DWORD waardegegevens van de waarde DisabledByDefault in 0x0 in de volgende registratiesleutels onder **Protocollen** toets:

      SCHANNEL\Protocollen\TLS 1.2\Client

      SCHANNEL\Protocollen\TLS 1.2\Server
   **SSL x.0 uitschakelen**

   SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: DWORD-waarde (32 bits) tot 1

   SCHANNEL\Protocols\SSL 3.0\Server: Ingeschakeld: DWORD-waarde (32 bits) tot 0

* Verwijder de **TRACE** methode:

   **Op Apache**, bewerken in /etc/apache2/conf.d/security: TraceEnable **Uit**

   **Op IIS** (zie de [documentatie](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)), voert de volgende configuratie uit:

   * Controleer of **Verzoek filteren** rolineservice of -functie is geïnstalleerd.
   * In de **Verzoek filteren** klikt u op het tabblad Werkwoorden van HTTP en vervolgens op Verwerpt. Voer in het deelvenster Handelingen TRACE in het dialoogvenster Openen in.

* Verwijder de banner:

   **Op Apache**, /etc/apache2/conf.d/security bewerken:

   * ServerSignature **Uit**
   * ServerTokens **Prod**

   **Op IIS**, voert de volgende configuratie uit:

   * Installeren **URLScan**.
   * Bewerk de **Urlscan.ini** bestand dat **RemoveServerHeader=1**


* Beperk de querygrootte om te voorkomen dat belangrijke bestanden worden geüpload:

   **Op Apache**, voegt u de **LimitRequestBody** compileraanwijzing (grootte in bytes) in / directory.

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **Op IIS** (zie de [documentatie](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), stelt u de **maxAllowedContentLength** (maximale toegestane lengte van inhoud) in de filteropties voor inhoud.

Verwante onderwerpen:

* [Adobe Marketing Cloud-compatibiliteitsoverzicht](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Overzicht van Adobe Campaign Security](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf) (PDF)
