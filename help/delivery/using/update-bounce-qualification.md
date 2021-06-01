---
product: campaign
title: Bouncekwalificatie bijwerken na een ISP-uitval
description: Leer hoe te om stuitkwalificatie na een ISP stroomonderbreking bij te werken.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# Onjuiste harde grenzen bijwerken na afbreking van Apple {#update-bounce-qualification.md}

## Context

Op 26 april 2021 leidde een wereldwijd probleem bij Apple ertoe dat sommige e-mailberichten die naar geldige Apple-e-mailadressen werden verzonden, onjuist werden teruggestuurd als ongeldige e-mailadressen door Apple-servers met de volgende stuiterende reactie:  &quot;550 5.1.1 &quot;E-mailadres&quot;: opzoekresultaat gebruiker is gelukt, maar er is geen gebruikersrecord gevonden.&quot;

Dit probleem is op 26-4-17-2010 opgetreden en duurde 7 uur &#39;s middags.

>[!NOTE]
>
>U kunt het dashboard van de Status van het Systeem van Apple op [deze pagina](https://www.apple.com/support/systemstatus/) controleren.

In het geval van een stroomonderbreking van ISP, kunnen de e-mails die door Campaign worden verzonden niet met succes aan hun ontvanger worden geleverd: deze e - mails worden ten onrechte als bounces gemarkeerd .

Per standaard stuitverwerkingslogica voegde Adobe Campaign deze ontvangers automatisch toe aan de quarantainelijst met een **[!UICONTROL Status]**-instelling van **[!UICONTROL Quarantine]**. Om dit te verbeteren, moet u uw quarantainetabel in Campagne bijwerken door deze ontvangers te vinden en te verwijderen, of hun **[!UICONTROL Status]** te veranderen in **[!UICONTROL Valid]** zodat de nachtelijke schoonmaakwerkschema hen zal verwijderen.

Om de ontvangers te vinden die door deze kwestie werden beïnvloed, of in het geval dat dit opnieuw met een andere ISP gebeurt, gelieve de instructies hieronder te zien.

## Proces voor bijwerken

U moet een query uitvoeren op uw quarantainetabel om alle Apple-ontvangers (waaronder @icloud.com, @me.com, @mac.com) die mogelijk door het probleem zijn beïnvloed, uit te filteren zodat ze uit de quarantainelijst kunnen worden verwijderd en kunnen worden opgenomen in toekomstige e-mailleveringen voor campagnes.

Gebaseerd op het tijdkader van het incident, hieronder zijn de geadviseerde richtlijnen voor deze vraag.

>[!IMPORTANT]
>
>Deze datums/tijden zijn gebaseerd op de tijdzone van de Oost-Standard (EST). Pas de tijdzone van de instantie aan.

* Voor de instanties van de Campagne met SMTP stuitert reactieinformatie op het **[!UICONTROL Error text]** gebied van de quarantainelijst:

   * **De tekst van de fout (quarantainetekst)** bevat &quot;het succes van de gebruikersraadpleging maar geen gevonden gebruikersverslag&quot;en de tekst van de  **Fout (quarantainetekst)**  bevat &quot;support.apple.com&quot;
   * **Status bijwerken (@lastModified)** op of na 26-4-2021 07:00:00
   * **Status bijwerken (@lastModified)** op of vóór 26-4-2021 01:00:00 PM

* Voor campagneinstanties met de binnenkomende informatie van de E-mailregel in het **[!UICONTROL Error text]** gebied van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-maildomein (@domein)** gelijk aan icloud.com OR  **Email domein (@domein)** gelijk aan me.com OF  **E-maildomein (@domein)** gelijk aan mac.com
   * **Status bijwerken (@lastModified)** op of na 26-4-2021 07:00:00
   * **Status bijwerken (@lastModified)** op of vóór 26-4-2021 01:00:00 PM

Zodra u de lijst van beïnvloede ontvangers hebt, kunt u of hen plaatsen aan een status van **[!UICONTROL Valid]** zodat zullen zij uit de quarantainelijst door **[!UICONTROL Database cleanup]** werkschema worden verwijderd, of enkel hen schrappen van de lijst.

**Verwante onderwerpen:**
* [Leveringsfouten begrijpen](../../delivery/using/understanding-delivery-failures.md)
* [Kwalificatie van niet-bezorgde e-mails](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
