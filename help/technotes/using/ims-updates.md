---
product: campaign
title: Technote - Werk uw omgeving bij om verbinding te maken met Adobe Campaign met IMS
description: Campagne - IMS-updates
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 62fc46e45078fce56eadda3518251e61244bf5d0
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 4%

---

# Uw omgeving bijwerken voor verbinding met Adobe Campaign met IMS {#acc-ims-faq}



Op 30 juni, zijn 2021 veranderingen aangebracht in [ Adobe Identity Management Systeem ](https://helpx.adobe.com/nl/enterprise/using/identity.html) (IMS) login mogelijkheden die uw capaciteit konden beïnvloeden om Adobe Campaign te blijven gebruiken. Leer hoe u ervoor kunt zorgen dat u Adobe Campaign Classic v7 zonder onderbreking blijft gebruiken.

## Wat is er veranderd?

De Dienst van Adobe Identity Management (IMS) stopte ondersteunend oude versies van Internet Explorer op **30 Juni, 2021**. [Meer informatie](https://helpx.adobe.com/nl/x-productkb/global/update-operating-system-and-browser.html).

Adobe wil de IMS-functionaliteit behouden voor alle klanten van 30 juni 2021. IMS maakt deel uit van het beveiligingskader dat gebruikers toestaat zich aan te melden bij de clientconsole, dus Adobe Campaign.

Om deze functionaliteit te bewaren, moeten de klanten de Console van de Cliënt op de machine van elke gebruiker bijwerken, en de recentste update van uw [ versie van Vensters ](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems) verzekeren, met **ingebouwde Internet Explorer 11**, op de machine van elke gebruiker geïnstalleerd is.

## Heb je invloed op?

Als u met Campagne [ via Adobe ID ](../../integrations/using/about-adobe-id.md) verbindt, door de Dienst van Identity Management van Adobe (IMS), en het runnen van een oudere versie van Campagne dan hieronder vermeld, wordt u beïnvloed.

Als u al een upgrade hebt uitgevoerd maar een oude versie van Microsoft Internet Explorer gebruikt, moet u een upgrade uitvoeren naar Internet Explorer 11.

## Hoe kan ik bijwerken?

* Als gehoste klant heeft Adobe uw exemplaar(s) al bijgewerkt naar de nieuwere versie.

* Als klant op-gebouw/hybride, moet u aan één van de nieuwere hierboven vermelde versies bevorderen om van de nieuwe Console van de Cliënt te profiteren en een naadloze overgang **vóór 30 Juni, 2021** te verzekeren.

  U dient een upgrade uit te voeren naar een van de nieuwe versies die hieronder worden vermeld.

   * Gold Standard 11. [Meer informatie](../../rn/using/gold-standard.md)
   * Release van campagne 21.1.3. [Meer informatie](../../rn/using/latest-release.md)
   * Release van campagne 20.2.5.
   * Release van campagne 20.1.4.
   * Release van campagne 19.2.4.

  Deze versies worden geleverd met een nieuw verbindingsprotocol. De verbetering is verplicht voor zowel de server van de Campagne als de Console van de Cliënt: zodra alle instanties worden bevorderd, moet de Console van de Cliënt aan deze versie evenals aan Campagne na **kunnen worden bevorderd 30 Juni, 2021**.

Bovendien verzeker de recentste update van uw [ versie van Vensters ](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), met **ingebouwde Internet Explorer 11**, op de machine van elke gebruiker geïnstalleerd is.

## Veelgestelde vragen

**Hoe kan ik mijn versie van de Campagne controleren?**

Leer hoe te om uw versie [ in deze sectie ](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) te controleren.


**Hoe kan ik controleren als ik IMS gebruik?**

U kunt de verbindingsmodus als volgt controleren:

* Start de Campagne Client Console en open de verbindingsinstellingen voor de instantie. Als **verbindt met een Adobe ID** optie wordt geselecteerd, gebruikt u Adobe IMS.

  ![](../../integrations/using/assets/ims_1.png)

of

* Start de Campagne Client Console en controleer het verbindingsvenster. Als u verbinding maakt met een Adobe ID, zoals wordt weergegeven in het onderstaande scherm, gebruikt u IMS.

  ![](../../integrations/using/assets/adobeID.png)

**Bericht van de Waarschuwing van de Verbinding**

Het volgende waarschuwingsbericht is zichtbaar aan gebruikers als zij hun Console van de Cliënt moeten bijwerken of een oude versie van Microsoft Internet Explorer gebruiken: **u moet recentste installeren die aan Vensters en/of uw Adobe apps wordt bijgewerkt.**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

Als u een dergelijke waarschuwing ziet, moet u de meest recente updates van het besturingssysteem installeren dat u gebruikt. [Meer informatie](https://helpx.adobe.com/nl/x-productkb/global/update-operating-system-and-browser.html)

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
* [ Toegang Adobe de Distributie van de Software ](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=nl-NL)
* [ Download Campaign Classic build ](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
