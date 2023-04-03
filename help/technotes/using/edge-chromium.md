---
product: campaign
title: TechNote - Microsoft Edge Chromium inschakelen voor uw Campagne-omgeving
description: Campagne - Edge Chromium
hide: true
hidefromtoc: true
source-git-commit: d9f57d4e5b6f880907040344ece40546456a2321
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 12%

---


# Microsoft Edge Chromium inschakelen voor uw omgeving {#edge-conf}

![](../../assets/v7-only.svg)


## Wat is er veranderd?

Na afloop van de levensduur van Microsoft Internet Explorer 11 gebruikt de HTML-renderingengine voor Adobe Services (aanmeldingspagina) in de clientconsole nu Microsoft Edge Chromium, vanaf Campaign Classic v7.3.

Naast de installatie van de Microsoft Edge Webview 2-runtime, die nu [vereist voor elke installatie van de clientconsole](../../installation/using/installing-the-client-console.md#webview), Microsoft Edge Chromium moet zijn ingeschakeld voor uw exemplaar(s).

## Heeft dit gevolgen voor u?

Als uw omgeving is bijgewerkt naar Campaign Classic v7.3 (of hoger), heeft dit gevolgen voor u.

## Hoe kan ik bijwerken?

* Als **gehost** Adobe heeft Microsoft Edge Chromium al ingeschakeld voor uw exemplaar(s).

* Als **op locatie/hybride** moet u Microsoft Edge Chromium inschakelen voor uw exemplaar(s).

   Bij de upgrade naar Campaign Classic v7.3 (en hoger) wordt een nieuwe `webView2Mode` kenmerk is beschikbaar in het configuratiebestand van de Campagneserver `serverConf.xml`. Dit kenmerk moet zijn ingeschakeld.

   Hiervoor voert u de volgende stappen uit op al uw omgevingen (MKT, MID, RT):

   1. Het configuratiebestand van de Campagneserver bewerken (`serverConf.xml`)
   1. In de `<web>` module, set `webView2Mode = "1"`
   1. Laad de serverconfiguratie opnieuw

      ```
      nlserver config -reload
      ```

   1. De webserver opnieuw starten

      ```
      nlserver restart web
      ```

   1. Start Apache opnieuw als uw omgeving op Apache wordt uitgevoerd

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>Voor vragen over deze wijzigingen neemt u contact op met de [Adobe-klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Verwante onderwerpen

* [Upgrade uw omgeving](../../production/using/build-upgrade.md)
* [Veelgestelde vragen over buildupgrades](../../platform/using/faq-build-upgrade.md)
* [Campagne-clientconsole installeren](../../installation/using/installing-the-client-console.md)

