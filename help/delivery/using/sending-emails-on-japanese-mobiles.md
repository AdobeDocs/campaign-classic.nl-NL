---
product: campaign
title: E-mails verzenden naar Japanse mobiele telefoons met Adobe Campaign Classic
description: Leer hoe u e-mailberichten configureert, ontwerpt en verzendt die op een Japanse mobiele telefoon worden gelezen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Email, Email Design
role: User
hide: true
hidefromtoc: true
exl-id: 44634227-2340-49c4-b330-740c739ea551
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# E-mails verzenden naar Japanse mobiele telefoons {#sending-emails-on-japanese-mobiles}

## E-mailindelingen voor Japanse mobiele apparaten {#email-formats-for-japanese-mobiles}

Adobe Campaign beheert drie specifieke Japanse formaten voor e-mail op mobiles: **Deco-mail** (mobiele telefoons van DoCoMo), **Decore Mail** (mobiele telefoons van Softbank) en **Decoration Mail** (mobiele telefoons van KDDI AU). Deze formaten leggen bijzondere coderings, structuur, en groottebeperkingen op. Leer meer over beperkingen en aanbevelingen in [ deze sectie ](#limitations-and-recommendations).

Als u wilt dat de ontvanger berichten in een van deze indelingen correct ontvangt, raden we u aan **[!UICONTROL Deco-mail (DoCoMo)]** , **[!UICONTROL Decore Mail (Softbank)]** of **[!UICONTROL Decoration Mail (KDDI AU)]** in het bijbehorende profiel te selecteren:

![](assets/deco-mail_03.png)

Als u de optie **[!UICONTROL Email format]** echter als **[!UICONTROL Unknown]** , **[!UICONTROL HTML]** of **[!UICONTROL Text]** laat, detecteert Adobe Campaign automatisch (bij het verzenden van het e-mailbericht) de Japanse indeling voor gebruik, zodat het bericht correct wordt weergegeven.

Dit automatische detectiesysteem is gebaseerd op de lijst met vooraf gedefinieerde domeinen die zijn gedefinieerd in de set met mailregels van **[!UICONTROL Management of Email Formats]** . Voor meer bij het beheren van e-mailformaten, verwijs naar [ deze pagina ](../../installation/using/email-deliverability.md#managing-email-formats).

## Beperkingen en aanbevelingen {#limitations-and-recommendations}

Voor het verzenden van e-mails die worden gelezen op een mobiel apparaat dat wordt gebruikt door een Japanse provider (Softbank, DoCoMo, KDDI AU) gelden een aantal beperkingen.

Daarom moet u:

* Alleen afbeeldingen in JPEG- of GIF-indeling gebruiken
* Een levering maken met tekst en HTML-secties die strikt lager zijn dan 10 000 bytes (voor KDDI AU en DoCoMo)
* Afbeeldingen met een totale grootte (vóór codering) van minder dan 100 kB gebruiken
* Gebruik niet meer dan 20 afbeeldingen per bericht
* Gebruik een HTML-indeling van beperkte grootte (een beperkt aantal tags is beschikbaar voor elke operator)

>[!NOTE]
>
>Bij het maken van uw bericht moet rekening worden gehouden met beperkingen die specifiek zijn voor elke operator. Raadpleeg de productdocumentatie.


## De e-mailinhoud testen {#testing-the-email-content}

### Een voorvertoning van het bericht weergeven {#previewing-the-message}

Met Adobe Campaign kunt u controleren of de berichtindeling is aangepast voor verzending naar een Japanse mobiele telefoon.

Nadat u de inhoud hebt gedefinieerd en het onderwerp van de e-mail hebt ingevoerd, kunt u de weergave en opmaak controleren wanneer het bericht wordt gemaakt.

Als u op het tabblad **[!UICONTROL Preview]** van het venster voor het bewerken van inhoud op **[!UICONTROL More... > Deco-mail diagnostic]** klikt, kunt u het volgende doen:

* Controleren of de HTML-inhoudscodes voldoen aan de Japanse indelingsbeperkingen
* Controleer of het aantal afbeeldingen in het bericht de limiet van de indeling (20 afbeeldingen) niet overschrijdt
* De totale berichtgrootte controleren (minder dan 100 kB)

  ![](assets/deco-mail_06.png)

### Typologieregel uitvoeren {#running-typology-rule}

Naast de diagnose van de voorvertoning wordt een tweede controle uitgevoerd bij het verzenden van een bewijs of levering: tijdens de analyse wordt een specifieke typologieregel, **[!UICONTROL Deco-mail check]** , gestart.

>[!IMPORTANT]
>
>Deze typologieregel wordt alleen uitgevoerd als ten minste een van de ontvangers is geconfigureerd voor het ontvangen van e-mails in de indeling **[!UICONTROL Deco-mail (DoCoMo)]** , **[!UICONTROL Decore Mail (Softbank)]** of **[!UICONTROL Decoration Mail (KDDI AU)]** .

Deze typologieregel staat u toe om ervoor te zorgen dat de levering de [ formaatbeperkingen ](#limitations-and-recommendations) respecteert die door de Japanse exploitanten, met name met betrekking tot de totale grootte van e-mail, de grootte van HTML en tekstsecties, het aantal beelden in de berichten, en de markeringen in de inhoud van HTML worden bepaald.

### Proefdrukken verzenden {#sending-proofs}

U kunt proefdrukken verzenden om de levering te testen. Als u de proefdruk verzendt en vervangende adressen gebruikt, voert u adressen in die overeenkomen met de e-mailindeling van het gebruikte profiel.

U kunt bijvoorbeeld het adres van een profiel vervangen door test@softbank.ne.jp als de e-mailindeling voor dit profiel vooraf is gedefinieerd op **[!UICONTROL Decore Mail (Softbank)]** .

![](assets/deco-mail_05.png)

## Berichten verzenden {#sending-messages}

Voor het verzenden van een e-mailbericht naar ontvangers met Japanse e-mailindelingen via Campagne zijn twee opties mogelijk:

* Creeer twee leveringen: één slechts voor Japanse ontvangers en een andere voor andere ontvangers - verwijs naar [ deze sectie ](#designing-a-specific-delivery-for-japanese-formats).
* Creeer één enkele levering en Adobe Campaign zal automatisch het formaat ontdekken te gebruiken - verwijs naar [ deze sectie ](#designing-a-delivery-for-all-formats).

### Een specifieke levering ontwerpen voor Japanse indelingen {#designing-a-specific-delivery-for-japanese-formats}

U kunt een werkstroom maken die twee leveringen bevat: een die op een Japans mobiel moet worden gelezen en een ander voor ontvangers met een standaard e-mailformaat.

Hiervoor gebruikt u de **[!UICONTROL Split]** -activiteit in uw workflow en definieert u de Japanse e-mailindelingen (Deco-mail, Decoration Mail en Decoration Mail) als filtervoorwaarden.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### Een levering voor alle indelingen ontwerpen {#designing-a-delivery-for-all-formats}

Wanneer Adobe Campaign de indelingen dynamisch beheert op basis van het domein (profielen met e-mailindelingen die zijn gedefinieerd als **[!UICONTROL Unknown]** , **[!UICONTROL HTML]** of **[!UICONTROL Text]** ), kunt u dezelfde levering naar al uw ontvangers verzenden.

Het berichtcontact zal correct voor de gebruikers op Japanse mobiele telefoons, enkel zoals voor de standaardontvangers tonen.

>[!IMPORTANT]
>
>Let erop dat u de speciale functies respecteert die aan elke Japanse e-mailindeling (Deco-mail, Decoration Mail en Decoration Mail) zijn gekoppeld. Voor meer informatie over beperkingen, verwijs naar [ deze sectie ](#limitations-and-recommendations).
