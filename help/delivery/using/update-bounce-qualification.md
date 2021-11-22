---
product: campaign
title: Kwalificatie van niet-bezorging bijwerken na een ISP-uitval
description: Leer hoe te om stuitkwalificatie na een ISP stroomonderbreking bij te werken.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: cee019432c64eaaefac86a27b731355242fd1555
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# Onjuiste harde grenzen bijwerken na Apple-storing {#update-bounce-qualification.md}

![](../../assets/common.svg)

## Context

Op 26 april 2021 leidde een wereldwijde uitgave bij Apple ertoe dat sommige e-mailberichten die naar geldige Apple-e-mailadressen werden verzonden, onjuist werden teruggestuurd als ongeldige e-mailadressen door Apple-servers met de volgende reactie: &quot;550 5.1.1 &quot;E-mailadres&quot;: opzoekresultaat gebruiker is gelukt, maar er is geen gebruikersrecord gevonden.&quot;

Dit probleem is op 26-4-17-2010 opgetreden en duurde 7 uur &#39;s middags.

>[!NOTE]
>
>U kunt het Apple System Status Dashboard inschakelen [deze pagina](https://www.apple.com/support/systemstatus/).

In het geval van een stroomonderbreking van ISP, kunnen de e-mails die door Campaign worden verzonden niet met succes aan hun ontvanger worden geleverd: deze e - mails worden ten onrechte als bounces gemarkeerd .

Adobe Campaign heeft deze ontvangers automatisch aan de quarantainelijst toegevoegd met een **[!UICONTROL Status]** instellen van **[!UICONTROL Quarantine]**. Om dit te verbeteren, moet u uw quarantainetabel in Campagne bijwerken door deze ontvangers te vinden en te verwijderen, of hun te veranderen **[!UICONTROL Status]** tot **[!UICONTROL Valid]** zodat de nachtelijke schoonmaakworkflow ze verwijdert.

Om de ontvangers te vinden die door deze kwestie werden beïnvloed, of in het geval dat dit opnieuw met een andere ISP gebeurt, gelieve de instructies hieronder te zien.

## Proces voor bijwerken

U moet een query uitvoeren op uw quarantainetabel om alle Apple-ontvangers (waaronder @icloud.com, @me.com, @mac.com) die mogelijk door het probleem zijn beïnvloed, uit te filteren zodat ze uit de quarantainelijst kunnen worden verwijderd en kunnen worden opgenomen in toekomstige e-mailleveringen voor campagnes.

Gebaseerd op het tijdkader van het incident, hieronder zijn de geadviseerde richtlijnen voor deze vraag.

>[!IMPORTANT]
>
>Deze datums/tijden zijn gebaseerd op de tijdzone van de Oost-Standard (EST). Pas de tijdzone van de instantie aan.

* Voor Campagne-instanties met SMTP-responsgegevens voor stuiteren in het dialoogvenster **[!UICONTROL Error text]** veld van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;user lookup success but no user record found&quot; EN **Fouttekst (quarantainetekst)** bevat &quot;support.apple.com&quot;
   * **Status bijwerken (@lastModified)** 26-04-2021 07:00:00
   * **Status bijwerken (@lastModified)** 26-04-2021 01:00:22:00

* Voor campagneinstanties met de informatie over de binnenkomende e-mailregel in het dialoogvenster **[!UICONTROL Error text]** veld van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-maildomein (@domein)** gelijk aan icloud.com OR **E-maildomein (@domein)** gelijk aan me.com OR **E-maildomein (@domein)** gelijk aan mac.com
   * **Status bijwerken (@lastModified)** 26-04-2021 07:00:00
   * **Status bijwerken (@lastModified)** 26-04-2021 01:00:22:00

Als u de lijst met betrokken ontvangers hebt, kunt u deze instellen op de status **[!UICONTROL Valid]** zodat zij uit de quarantainelijst worden verwijderd door **[!UICONTROL Database cleanup]** of deze uit de tabel verwijderen.

**Verwante onderwerpen:**
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Kwalificatie van niet-bezorgde e-mails](understanding-delivery-failures.md#bounce-mail-qualification)
