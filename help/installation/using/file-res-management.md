---
product: campaign
title: Bestands- en resourcebeheer
feature: Installation, Application Settings
description: Leer hoe u het beheer van bestanden en bronnen configureert in de campagne
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---

# Bestands- en resourcebeheer{#file-and-resmanagement}



## Bestandsindeling voor uploaden beperken {#limiting-uploadable-files}

Gebruik het **uploadWhiteList** attribuut om de dossiertypes te beperken beschikbaar voor upload op de server van Adobe Campaign.

Dit attribuut is beschikbaar binnen het **element 0&rbrace; dataStore &lbrace;van het** serverConf.xml **dossier.** Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in deze [ sectie ](../../installation/using/the-server-configuration-file.md).

De standaardwaarde van dit kenmerk is **.+** en laat u om het even welk dossiertype uploaden.

Als u de mogelijke indelingen wilt beperken, vervangt u de kenmerkwaarde door een geldige reguliere Java-expressie. U kunt verschillende waarden invoeren door deze met een komma te scheiden.

Bijvoorbeeld: **uploadWhiteList=&quot;.&#42; .png,.&#42; .jpg&quot;** zal u PNG en JPG formaten op de server laten uploaden. Er worden geen andere indelingen geaccepteerd.

U kunt belangrijke dossiers ook verhinderen worden geupload door de Server van het Web te vormen. [Meer informatie](web-server-configuration.md)

>[!NOTE]
>
>Het **uploadWhiteList** attribuut beperkt de dossiertypes beschikbaar voor upload op de server van Adobe Campaign. Nochtans, wanneer de publicatiemodus **het Volgen server(s)** of **Andere server(s) van Adobe Campaign** is, moet het **uploadWhitelist** attribuut ook op die servers worden bijgewerkt.

## Configuratie proxyverbinding {#proxy-connection-configuration}

U kunt de server van de Campagne met een extern systeem door een volmacht verbinden, gebruikend de het werkschemaactiviteit van de Overdracht van het a **Dossier** bijvoorbeeld. Om dit te bereiken, moet u de **proxyConfig** sectie van het **serverConf.xml** dossier door een specifiek bevel vormen. Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in deze [ sectie ](../../installation/using/the-server-configuration-file.md).

De volgende proxyverbindingen zijn mogelijk: HTTP, HTTPS, FTP, SFTP. Gelieve te merken op dat de beginnende versie van de Campagne 20.2, de HTTP en HTTPS protocolparameters **niet meer beschikbaar** zijn. Deze parameters worden nog steeds hieronder vermeld, aangezien ze in eerdere gebouwen beschikbaar blijven - waaronder 9032.

>[!CAUTION]
>
>Alleen de standaardverificatiemodus wordt ondersteund. NTLM-verificatie wordt niet ondersteund.
>
>SOCKS-proxy&#39;s worden niet ondersteund.
>

U kunt de volgende opdracht gebruiken:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

protocolparameters zijn &quot;http&quot;, &quot;https&quot; of &quot;ftp&quot;.

Als u FTP instelt op dezelfde poort als HTTP/HTTPS-verkeer, kunt u het volgende gebruiken:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

De opties &quot;http&quot; en &quot;https&quot; worden alleen gebruikt wanneer de protocolparameter &quot;ftp&quot; is en geven aan of de tunnelmethode op de opgegeven poort via HTTPS of via HTTP wordt uitgevoerd.

Als u verschillende poorten gebruikt voor FTP/SFTP- en HTTP/HTTPS-verkeer via proxyserver, moet u de parameter &#39;ftp&#39;-protocol instellen.


Bijvoorbeeld:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Voer vervolgens het wachtwoord in.

HTTP-verbindingen worden gedefinieerd in de parameter proxyHTTP:

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS-verbindingen worden gedefinieerd in de parameter proxyHTTPS:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP-/FTPS-verbindingen worden gedefinieerd in de proxyFTP-parameter:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Als u dezelfde proxy voor verschillende verbindingstypen gebruikt, wordt alleen proxyHTTP gedefinieerd met useSingleProxy ingesteld op &quot;1&quot; of &quot;true&quot;.

Als u interne verbindingen hebt die niet door de volmacht zouden moeten gaan, voeg hen in de opheffingsparameter toe.

Als u de proxyverbinding tijdelijk wilt uitschakelen, stelt u de ingeschakelde parameter in op &quot;false&quot; of &quot;0&quot;.

Als u de iOS HTTP/2-connector via een proxy moet gebruiken, worden de volgende HTTP-proxymodi ondersteund:

* HTTP zonder verificatie
* HTTP-basisverificatie

Als u de proxymodus wilt activeren, moet de volgende wijziging worden uitgevoerd in het `serverconf.xml` -bestand:

```
<nmac useHTTPProxy="true">
```

Voor meer informatie over deze schakelaar van iOS HTTP/2, verwijs naar deze [ pagina ](../../delivery/using/about-mobile-app-channel.md).

## Overheidsmiddelen beheren {#managing-public-resources}

Om voor het publiek toegankelijk te zijn, moeten de beelden die in e-mail en openbare middelen verbonden aan campagnes worden gebruikt op een extern toegankelijke server aanwezig zijn. Ze kunnen vervolgens beschikbaar zijn voor externe ontvangers of operatoren. [Meer informatie](../../installation/using/deploying-an-instance.md#managing-public-resources).

De openbare middelen worden opgeslagen in de **/var/res/instance** folder van de de installatiemap van Adobe Campaign.

De passende URL is: **http://server/res/instance** waar **instantie** de naam van de volgende instantie is.

U kunt een andere folder specificeren door een knoop aan het **conf- `<instance>` .xml** dossier toe te voegen om opslag op de server te vormen. Dit betekent dat de volgende regels moeten worden toegevoegd:

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

In dit geval, zou nieuwe URL voor de openbare middelen die in het hogere gedeelte van het venster van de plaatsingstovenaar worden gegeven aan deze omslag moeten richten.
