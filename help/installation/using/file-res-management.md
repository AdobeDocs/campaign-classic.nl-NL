---
solution: Campaign Classic
product: campaign
title: Bestands- en bronbeheer
description: Leer hoe u het beheer van bestanden en bronnen configureert in de campagne
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 1%

---

# Bestands- en resourcebeheer{#file-and-resmanagement}

## Bestandsindeling voor uploaden beperken {#limiting-uploadable-files}

Gebruik het **uploadWhiteList** attribuut om de dossiertypes te beperken beschikbaar voor upload op de server van Adobe Campaign.

Dit kenmerk is beschikbaar in het **dataStore**-element van het **serverConf.xml**-bestand. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

De standaardwaarde van dit kenmerk is **.+** en laat u om het even welk dossiertype uploaden.

Als u de mogelijke indelingen wilt beperken, vervangt u de kenmerkwaarde door een geldige reguliere Java-expressie. U kunt verschillende waarden invoeren door deze met een komma te scheiden.

Bijvoorbeeld: **uploadWhiteList=&quot;.*.png,.Met *.jpg&quot;** kunt u PNG- en JPG-indelingen uploaden naar de server. Er worden geen andere indelingen geaccepteerd.

>[!NOTE]
>
>In Internet Explorer moet het volledige bestandspad worden gecontroleerd door de reguliere expressie.

U kunt belangrijke dossiers ook verhinderen worden geupload door de Server van het Web te vormen. [Meer informatie](web-server-configuration.md)

## Configuratie proxyverbinding {#proxy-connection-configuration}

U kunt de Campagneserver met een extern systeem door een volmacht verbinden, gebruikend een **de werkschemaactiviteit van de Overdracht van het Dossier** bijvoorbeeld. Hiervoor moet u de sectie **proxyConfig** van het bestand **serverConf.xml** via een specifieke opdracht configureren. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

De volgende proxyverbindingen zijn mogelijk: HTTP, HTTPS, FTP, SFTP. Houd er rekening mee dat de HTTP- en HTTPS-protocolparameters **niet meer beschikbaar zijn** vanaf de campagneversie 20.2. Deze parameters worden nog steeds hieronder vermeld, aangezien ze in eerdere gebouwen beschikbaar blijven - waaronder 9032.

>[!CAUTION]
>
>Alleen de standaardverificatiemodus wordt ondersteund. NTLM-verificatie wordt niet ondersteund.
>
>SOCKS-proxy&#39;s worden niet ondersteund.


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

## Overheidsbronnen beheren {#managing-public-resources}

Om voor het publiek toegankelijk te zijn, moeten de beelden die in e-mail en openbare middelen verbonden aan campagnes worden gebruikt op een extern toegankelijke server aanwezig zijn. Ze kunnen vervolgens beschikbaar zijn voor externe ontvangers of operatoren. [Meer informatie](../../installation/using/deploying-an-instance.md#managing-public-resources).

Openbare bronnen worden opgeslagen in de map **/var/res/instance** van de installatiemap van Adobe Campaign.

De overeenkomende URL is: **http://server/res/instance** waarbij **instance** de naam van de volgende instantie is.

U kunt een andere folder specificeren door een knoop aan **conf-`<instance>`.xml** dossier toe te voegen om opslag op de server te vormen. Dit betekent dat de volgende regels moeten worden toegevoegd:

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
