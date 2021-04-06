---
solution: Campaign Classic
product: campaign
title: Bounce-kwalificatie bijwerken na een ISP-uitgang
description: Leer hoe te om stuitkwalificatie na een ISP stroomonderbreking bij te werken.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
translation-type: tm+mt
source-git-commit: 3b5a6e6f03d9cb26ed372c3df069cbada36756a2
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 1%

---

# Bounce-kwalificatie bijwerken na een ISP-uitgang {#update-bounce-qualification.md}

## Context

In het geval van een stroomonderbreking van ISP, kunnen de e-mails die door Campaign worden verzonden niet met succes aan hun ontvanger worden geleverd: deze e - mails worden ten onrechte als bounces gemarkeerd .

In december 2020 resulteerde een wereldwijde uitgave bij Gmail in een onjuiste opgave van sommige e-mailberichten die naar geldige Gmail-adressen werden verzonden, door Gmail-servers met de volgende bounce: *&quot;550-5.1.1 De e-mailaccount die u probeerde te bereiken bestaat niet.&quot;*

Google heeft verklaard dat de Gmail-storingen en -storingen die dit probleem hebben veroorzaakt, op 14 december om 6:55 zijn begonnen en op 15 december om 18:09 uur zijn geëindigd. Uit onze gegevensanalyse bleek ook dat Gmail op 16 december om 2:06u EST een zeer korte spiraal heeft doorgemaakt, waarbij de meerderheid op 15 december tussen 2:00 uur EST en 18:30 uur EST heeft plaatsgevonden.

>[!NOTE]
>
>U kunt het Google Workspace Status Dashboard op [deze pagina](https://www.google.com/appsstatus#hl=en&amp;v=status) controleren.


Per standaard stuitverwerkingslogica voegde Adobe Campaign deze ontvangers automatisch toe aan de quarantainelijst met een **[!UICONTROL Status]**-instelling van **[!UICONTROL Quarantine]**. Om dit te verbeteren, moet u uw quarantainetabel in Campagne bijwerken door deze ontvangers te vinden en te verwijderen, of hun **[!UICONTROL Status]** te veranderen in **[!UICONTROL Valid]** zodat de nachtelijke schoonmaakwerkschema hen zal verwijderen.

Om de ontvangers te vinden die door deze Gmail- kwestie werden beïnvloed, of in het geval dat dit opnieuw met een andere ISP gebeurt, gelieve de instructies hieronder te zien.

## Proces voor bijwerken

U zult een vraag op uw quarantainelijst moeten in werking stellen om alle ontvangers uit te filteren Gmail (of andere ISP) die potentieel door de stroomonderbreking werden beïnvloed zodat kunnen zij uit de quarantainelijst worden verwijderd, en inbegrepen in toekomstige e-mailleveringen van de Campagne.

Gebaseerd op het tijdkader van het incident, hieronder zijn de geadviseerde richtlijnen voor deze vraag.

>[!IMPORTANT]
>
>Deze datums/tijden zijn gebaseerd op de tijdzone van de Oost-Standard (EST). Pas de tijdzone van de instantie aan.

* Voor de instanties van de Campagne met SMTP stuitert reactieinformatie op het **[!UICONTROL Error text]** gebied van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;550-5.1.1 Het e-mailaccount dat u probeert te bereiken, bestaat niet&quot; EN  **fouttekst (quarantainetekst)** bevat &quot;support.google.com&quot; **
   * **Status bijwerken (@lastModified)** op of na 14-12-2020 6:55:00
   * **Status bijwerken (@lastModified)** op of vóór 16-12-2020 6:00:00

* Voor campagneinstanties met de binnenkomende informatie van de E-mailregel in het **[!UICONTROL Error text]** gebied van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-maildomein (@domein)** gelijk aan &quot;gmail.com&quot; OF E-maildomein (@domein) gelijk aan &quot;googlemail.com&quot;
   * **Status bijwerken (@lastModified)** op of na 14-12-2020 6:55:00
   * **Status bijwerken (@lastModified)** op of vóór 16-12-2020 6:00:00

Zodra u de lijst van beïnvloede ontvangers hebt, kunt u of hen plaatsen aan een status van **[!UICONTROL Valid]** zodat zullen zij uit de quarantainelijst door **[!UICONTROL Database cleanup]** werkschema worden verwijderd, of enkel hen schrappen van de lijst.

**Verwante onderwerpen:**
* [Leveringsfouten begrijpen](../../delivery/using/understanding-delivery-failures.md)
* [Kwalificatie van niet-bezorgde e-mails](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
