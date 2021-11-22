---
product: campaign
title: E-mails verzenden naar Japanse mobiele telefoons met Adobe Campaign Classic
description: Leer hoe u e-mailberichten configureert, ontwerpt en verzendt die op een Japanse mobiele telefoon worden gelezen.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 44634227-2340-49c4-b330-740c739ea551
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# E-mails verzenden naar Japanse mobiele telefoons {#sending-emails-on-japanese-mobiles}

![](../../assets/common.svg)

## E-mailindelingen voor Japanse mobiele apparaten {#email-formats-for-japanese-mobiles}

Adobe Campaign beheert drie specifieke Japanse indelingen voor e-mail op mobiele apparaten: **Deco-mail** (DoCoMo mobiles), **E-mail negeren** (Softbank-mobieltjes) en **Decoration Mail** (KDDI AU-mobiles). Deze formaten leggen bijzondere coderings, structuur, en groottebeperkingen op. Meer informatie over beperkingen en aanbevelingen vindt u in [deze sectie](#limitations-and-recommendations).

Opdat de ontvanger berichten in één van deze formaten correct ontvangt, adviseren wij selecterend **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** of **[!UICONTROL Decoration Mail (KDDI AU)]** in het corresponderende profiel:

![](assets/deco-mail_03.png)

Als u echter de **[!UICONTROL Email format]** optie als **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** of **[!UICONTROL Text]** Adobe Campaign detecteert automatisch (bij het verzenden van het e-mailbericht) de Japanse indeling voor gebruik, zodat het bericht correct wordt weergegeven.

Dit automatische detectiesysteem is gebaseerd op de lijst met vooraf gedefinieerde domeinen die zijn gedefinieerd in het dialoogvenster **[!UICONTROL Management of Email Formats]** mailregel ingesteld. Raadpleeg voor meer informatie over het beheren van e-mailindelingen [deze pagina](../../installation/using/email-deliverability.md#managing-email-formats).

## Beperkingen en aanbevelingen {#limitations-and-recommendations}

Voor het verzenden van e-mails die worden gelezen op een mobiel apparaat dat wordt gebruikt door een Japanse provider (Softbank, DoCoMo, KDDI AU) gelden een aantal beperkingen.

Daarom moet u:

* Alleen afbeeldingen in JPEG- of GIF-indeling gebruiken
* Creeer een levering met tekst en HTML secties die strikt lager zijn dan 10 000 bytes (voor KDDI AU en DoCoMo)
* Afbeeldingen gebruiken waarvan de totale grootte (vóór codering) lager is dan 100 kB
* Gebruik niet meer dan 20 afbeeldingen per bericht
* Gebruik een indeling voor kleiner formaat HTML (er is een beperkt aantal tags beschikbaar voor elke-operator)

>[!NOTE]
>
>Wanneer u uw bericht maakt, moet u rekening houden met de beperkingen die specifiek zijn voor elke operator. Zie:
>
>* Raadpleeg voor DoCoMo [deze pagina](https://www.nttdocomo.co.jp/service/developer/make/content/deco_mail/index.html)
>* Voor KDDI AU, verwijs naar [deze pagina](https://www.au.com/ezfactory/tec/spec/decorations/template.html)
>* Raadpleeg voor Softbank [deze pagina](https://www.support.softbankmobile.co.jp/partner/home_tech3/index.cfm)


## E-mailinhoud testen {#testing-the-email-content}

### Een voorbeeld van het bericht bekijken {#previewing-the-message}

Met Adobe Campaign kunt u controleren of de berichtindeling is aangepast voor verzending naar een Japanse mobiele telefoon.

Nadat u de inhoud hebt gedefinieerd en het onderwerp van de e-mail hebt ingevoerd, kunt u de weergave en opmaak controleren wanneer het bericht wordt gemaakt.

In de **[!UICONTROL Preview]** tabblad van het venster Inhoud bewerken, klikken **[!UICONTROL More... > Deco-mail diagnostic]** biedt de volgende mogelijkheden:

* Controleren of de HTML-inhoudscodes voldoen aan de Japanse indelingsbeperkingen
* Controleer of het aantal afbeeldingen in het bericht de limiet van de indeling (20 afbeeldingen) niet overschrijdt
* De totale berichtgrootte controleren (minder dan 100 kB)

   ![](assets/deco-mail_06.png)

### Typologieregel uitvoeren {#running-typology-rule}

Naast de diagnose van de voorvertoning wordt een tweede controle uitgevoerd bij de verzending van een bewijs of een levering: een specifieke typologieregel; **[!UICONTROL Deco-mail check]**, wordt tijdens de analyse gestart.

>[!IMPORTANT]
>
>Deze typologieregel wordt alleen uitgevoerd als ten minste een van de ontvangers is geconfigureerd om e-mails te ontvangen in **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** of **[!UICONTROL Decoration Mail (KDDI AU)]** gebruiken.

Met deze typologieregel kunt u ervoor zorgen dat de levering voldoet aan de [indelingsbeperkingen](#limitations-and-recommendations) door de Japanse operatoren worden gedefinieerd, met name ten opzichte van de totale grootte van de e-mail, de grootte van de HTML- en tekstsecties, het aantal afbeeldingen in de berichten en de tags in de inhoud van de HTML.

### Proeven verzenden {#sending-proofs}

U kunt proefdrukken verzenden om de levering te testen. Als u de proefdruk verzendt en vervangende adressen gebruikt, voert u adressen in die overeenkomen met de e-mailindeling van het gebruikte profiel.

U kunt bijvoorbeeld het adres van een profiel vervangen door test@softbank.ne.jp als de e-mailindeling voor dit profiel vooraf is gedefinieerd op **[!UICONTROL Decore Mail (Softbank)]**.

![](assets/deco-mail_05.png)

## Berichten verzenden {#sending-messages}

Voor het verzenden van een e-mailbericht naar ontvangers met Japanse e-mailindelingen via Campagne zijn twee opties mogelijk:

* Twee leveringen maken: één voor Japanse ontvangers en een andere voor andere ontvangers - verwijs naar [deze sectie](#designing-a-specific-delivery-for-japanese-formats).
* Eén levering maken en Adobe Campaign detecteert automatisch de te gebruiken indeling - raadpleeg [deze sectie](#designing-a-delivery-for-all-formats).

### Een specifieke levering ontwerpen voor Japanse indelingen {#designing-a-specific-delivery-for-japanese-formats}

U kunt een werkstroom maken die twee leveringen bevat: Een voor lezen op een Japans mobiel en een ander voor ontvangers met een standaard e-mailformaat.

Om dit te doen, gebruik **[!UICONTROL Split]** activiteit in uw werkschema en bepaal de Japanse e-mailformaten (Deco-mail, Decoration Mail en Decore Mail) als het filtreren voorwaarden.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### Een levering ontwerpen voor alle indelingen {#designing-a-delivery-for-all-formats}

Als Adobe Campaign de indelingen dynamisch beheert op basis van het domein (profielen met e-mailindelingen die zijn gedefinieerd als **[!UICONTROL Unknown]**, **[!UICONTROL HTML]** of **[!UICONTROL Text]** ), kunt u dezelfde levering naar al uw ontvangers verzenden.

Het berichtcontact zal correct voor de gebruikers op Japanse mobiele telefoons, enkel zoals voor de standaardontvangers tonen.

>[!IMPORTANT]
>
>Let erop dat u de speciale functies respecteert die aan elke Japanse e-mailindeling (Deco-mail, Decoration Mail en Decoration Mail) zijn gekoppeld. Voor meer informatie over beperkingen raadpleegt u [deze sectie](#limitations-and-recommendations).
