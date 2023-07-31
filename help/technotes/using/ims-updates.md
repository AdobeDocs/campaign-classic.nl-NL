---
product: campaign
title: Technote - Werk uw omgeving bij om verbinding te maken met Adobe Campaign met IMS
description: Campagne - IMS-updates
feature: Technote, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 7%

---

# Uw omgeving bijwerken voor verbinding met Adobe Campaign met IMS {#acc-ims-faq}



Op 30 juni zijn wijzigingen aangebracht in 2021 [Adobe Identity Management-systeem](https://helpx.adobe.com/enterprise/using/identity.html) (IMS) aanmeldingsmogelijkheden die van invloed kunnen zijn op uw vermogen om Adobe Campaign te blijven gebruiken. Leer hoe u ervoor kunt zorgen dat u Adobe Campaign Classic v7 zonder onderbreking blijft gebruiken.

## Wat is er veranderd?

Adobe Identity Management Service (IMS) biedt geen ondersteuning voor oude Internet Explorer-versies op **30 juni 2021**. [Meer informatie](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Adobe wil de IMS-functionaliteit behouden voor alle klanten van 30 juni 2021. IMS maakt deel uit van het beveiligingskader dat gebruikers toestaat zich aan te melden bij de clientconsole, dus Adobe Campaign.

Om deze functionaliteit te behouden, moeten klanten de clientconsole op de computer van elke gebruiker bijwerken en zorgen voor de nieuwste update van uw [Windows-versie](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), met **Internet Explorer 11** ingebouwd, wordt geïnstalleerd op de computer van elke gebruiker.

## Heeft dit gevolgen voor u?

Als u verbinding maakt met Campagne [via een Adobe ID](../../integrations/using/about-adobe-id.md), via Adobe Identity Management Service (IMS) en het uitvoeren van een oudere versie van Campagne dan de hieronder vermelde, is dit van invloed op u.

Als u al een upgrade hebt uitgevoerd maar een oude versie van Microsoft Internet Explorer gebruikt, moet u een upgrade uitvoeren naar Internet Explorer 11.

## Hoe kan ik bijwerken?

* Als gehoste klant heeft Adobe uw exemplaar(s) al bijgewerkt naar de nieuwere versie.

* Als klant op locatie/hybride klant moet u een upgrade uitvoeren naar een van de nieuwere versies die hierboven zijn vermeld om te profiteren van de nieuwe clientconsole en een naadloze overgang te garanderen **vóór 30 juni 2021**.

  U dient een upgrade uit te voeren naar een van de nieuwe versies die hieronder worden vermeld.

   * Gold Standard 11. [Meer informatie](../../rn/using/gold-standard.md)
   * Release van campagne 21.1.3. [Meer informatie](../../rn/using/latest-release.md)
   * Release van campagne 20.2.5.
   * Release van campagne 20.1.4.
   * Release van campagne 19.2.4.

  Deze versies worden geleverd met een nieuw verbindingsprotocol. Upgrade is verplicht voor zowel de campagneserver als de clientconsole: wanneer alle exemplaren zijn bijgewerkt, moet de clientconsole worden bijgewerkt naar deze versie en moet deze ook verbinding kunnen maken met de campagne na **30 juni 2021**.

Zorg bovendien voor de nieuwste update van uw [Windows-versie](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), met **Internet Explorer 11** ingebouwd, wordt geïnstalleerd op de computer van elke gebruiker.

## Veelgestelde vragen

**Hoe kan ik mijn versie van Campagne controleren?**

Leer hoe u uw versie kunt controleren [in deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**Hoe kan ik controleren of ik IMS gebruik?**

U kunt de verbindingsmodus als volgt controleren:

* Start de Campagne Client Console en open de verbindingsinstellingen voor de instantie. Als de **Verbinding maken met een Adobe ID** is geselecteerd, gebruikt u Adobe IMS.

  ![](../../integrations/using/assets/ims_1.png)

of

* Start de Campagne Client Console en controleer het verbindingsvenster. Als u verbinding maakt met een Adobe ID, zoals wordt weergegeven in het onderstaande scherm, gebruikt u IMS.

  ![](../../integrations/using/assets/adobeID.png)

**Verbindingswaarschuwing**

De volgende waarschuwing is zichtbaar voor gebruikers als ze hun clientconsole moeten bijwerken of een oude versie van Microsoft Internet Explorer moeten gebruiken: **U moet de meest recente update installeren naar Windows en/of uw Adobe-apps.**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

Als u een dergelijke waarschuwing ziet, moet u de meest recente updates van het besturingssysteem installeren dat u gebruikt. [Meer informatie](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

Als u de Internet Explorer-versie niet hebt bijgewerkt, wordt het volgende bericht weergegeven en kunt u geen verbinding meer maken met Adobe Campaign:

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>Voor vragen over deze wijzigingen neemt u contact op met de [Adobe-klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Nuttige koppelingen

* [Upgrade uw omgeving](../../production/using/build-upgrade.md)
* [Veelgestelde vragen over buildupgrades](../../platform/using/faq-build-upgrade.md)
* [De nieuwe clientconsole beschikbaar maken voor gebruikers](../../installation/using/client-console-availability-for-windows.md)
* [Campagne-clientconsole installeren](../../installation/using/installing-the-client-console.md)
* [Toegang tot Adobe-softwaredistributie](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html)
* [Campaign Classic-build downloaden](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
