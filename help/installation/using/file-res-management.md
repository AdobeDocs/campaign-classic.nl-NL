---
product: campaign
title: Bestands- en resourcebeheer
feature: Installation, Application Settings
description: Leer hoe u het beheer van bestanden en bronnen configureert in de campagne
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 2%

---

# Bestands- en resourcebeheer{#file-and-resmanagement}



## Bestandsindeling voor uploaden beperken {#limiting-uploadable-files}

Gebruik de **uploadWhiteList** om de bestandstypen te beperken die beschikbaar zijn voor uploaden op de Adobe Campaign-server.

Dit kenmerk is beschikbaar in het dialoogvenster **dataStore** element van het **serverConf.xml** bestand. Alle parameters die beschikbaar zijn in het dialoogvenster **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

De standaardwaarde van dit kenmerk is **.+** en kunt u elk bestandstype uploaden.

Als u de mogelijke indelingen wilt beperken, vervangt u de kenmerkwaarde door een geldige reguliere Java-expressie. U kunt verschillende waarden invoeren door deze met een komma te scheiden.

Bijvoorbeeld: **uploadWhiteList=&quot;.&#42;.png,&#42;.jpg&quot;** Hiermee kunt u PNG- en JPG-indelingen uploaden naar de server. Er worden geen andere indelingen geaccepteerd.

U kunt belangrijke dossiers ook verhinderen worden geupload door de Server van het Web te vormen. [Meer informatie](web-server-configuration.md)

>[!NOTE]
>
>De **uploadWhiteList** -kenmerk beperkt de bestandstypen die beschikbaar zijn voor uploaden op de Adobe Campaign-server. Wanneer de publicatiemodus echter **Volgserver(s)** of **Andere Adobe Campaign-server(s)** de **uploadWhitelist** kenmerken moeten ook op die servers worden bijgewerkt.

## Configuratie proxyverbinding {#proxy-connection-configuration}

U kunt de Campagneserver met een extern systeem door een volmacht verbinden, gebruikend **Bestandsoverdracht** workflowactiviteit, bijvoorbeeld. Om dit te bereiken, moet u vormen **proxyConfig** van de **serverConf.xml** een specifieke opdracht gebruiken. Alle parameters beschikbaar in het dialoogvenster **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

De volgende proxyverbindingen zijn mogelijk: HTTP, HTTPS, FTP, SFTP. Houd er rekening mee dat vanaf 20.2 de campagneversie de parameters HTTP en HTTPS protocol **niet meer beschikbaar**. Deze parameters worden nog steeds hieronder vermeld, aangezien ze in eerdere gebouwen beschikbaar blijven - waaronder 9032.

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

Als u interne verbindingen hebt die door de volmacht zouden moeten gaan, voeg hen in de opheffingsparameter toe.

Als u de proxyverbinding tijdelijk wilt uitschakelen, stelt u de ingeschakelde parameter in op &quot;false&quot; of &quot;0&quot;.

Als u de iOS HTTP/2-connector via een proxy moet gebruiken, worden de volgende HTTP-proxymodi ondersteund:

* HTTP zonder verificatie
* HTTP-basisverificatie

Als u de proxymodus wilt activeren, moet de volgende wijziging worden uitgevoerd in het dialoogvenster `serverconf.xml` bestand:

```
<nmac useHTTPProxy="true">
```

Voor meer informatie over deze iOS HTTP/2-connector raadpleegt u deze [page](../../delivery/using/about-mobile-app-channel.md).

## Overheidsmiddelen beheren {#managing-public-resources}

Om voor het publiek toegankelijk te zijn, moeten de beelden die in e-mail en openbare middelen verbonden aan campagnes worden gebruikt op een extern toegankelijke server aanwezig zijn. Ze kunnen vervolgens beschikbaar zijn voor externe ontvangers of operatoren. [Meer informatie](../../installation/using/deploying-an-instance.md#managing-public-resources).

De openbare middelen worden opgeslagen in **/var/res/instance** directory van de installatiemap van Adobe Campaign.

De overeenkomende URL is: **http://server/res/instance** waar **instance** is de naam van de instantie tracking.

U kunt een andere map opgeven door een knooppunt toe te voegen aan de **conf-`<instance>`.xml** bestand om opslag op de server te configureren. Dit betekent dat de volgende regels moeten worden toegevoegd:

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
