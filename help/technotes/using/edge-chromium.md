---
product: campaign
title: TechNote - Microsoft Edge Chromium inschakelen voor uw Campagne-omgeving
description: Campagne - Edge Chromium
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: 095919608e08a0bf8ad1487fa5ec0a1ddb443c7b
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 11%

---

# Microsoft Edge Chromium inschakelen voor uw omgeving {#edge-conf}

![](../../assets/v7-only.svg)


## Wat is er veranderd?

Na het einde van de levensduur van Microsoft Internet Explorer 11 gebruikt de HTML-renderingengine voor dashboards in de clientconsole Edge Chromium, vanaf Campaign Classic v7.3.

Naast de installatie van de Microsoft Edge Webview 2-runtime, die nu [vereist voor elke installatie van de clientconsole](../../installation/using/installing-the-client-console.md#webview), Microsoft Edge Chromium moet zijn ingeschakeld voor uw exemplaar(s).

## Heeft dit gevolgen voor u?

Als uw omgeving is bijgewerkt naar Campaign Classic v7.3 (of hoger), heeft dit gevolgen voor u.

## Hoe kan ik bijwerken?

* Als **gehost** Adobe heeft Microsoft Edge Chromium al ingeschakeld voor uw exemplaar(s). Er is geen aanvullende actie vereist.

* Als **op locatie/hybride** moet u Microsoft Edge Chromium inschakelen voor uw exemplaar(s).

   Bij de upgrade naar Campaign Classic v7.3 (en hoger) wordt een nieuwe `webView2Mode` kenmerk is beschikbaar in het configuratiebestand van de Campagneserver `serverConf.xml`. Dit kenmerk moet zijn ingeschakeld.

   Hiervoor voert u de volgende stappen uit op al uw omgevingen (MKT, MID, RT):

   1. Het configuratiebestand van de Campagneserver bewerken (`serverConf.xml`)
   1. In de `<web>` module, set `webView2Mode = "1"`
   1. Voer de volgende opdracht uit om de serverconfiguratie opnieuw te laden:

      ```
      nlserver config -reload
      ```

   1. Voer de volgende opdracht uit om de webserver opnieuw te starten:

      ```
      nlserver restart web
      ```

   1. Als uw omgeving Apache als webserver gebruikt, voert u de volgende opdracht uit om Apache opnieuw te starten:

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
