---
product: campaign
title: Kwalificatie van niet-bezorging bijwerken na een ISP-uitval
description: Leer hoe te om stuitkwalificatie na een ISP stroomonderbreking bij te werken
feature: Deliverability
hide: true
hidefromtoc: true
source-git-commit: f320c905f50c69a40678729b009a4c238a462e3c
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 2%

---

# Bijwerken onjuiste harde grenzen na een ISP stroomonderbreking {#update-bounces}

![](../../assets/common.svg)

## Context{#update-bounce-context}

In het geval van een stroomonderbreking van ISP, kunnen de e-mails die door Campaign worden verzonden niet met succes aan hun ontvanger worden geleverd: deze e - mails worden ten onrechte als bounces gemarkeerd .

Globale problemen bij Apple of Gmail kunnen er bijvoorbeeld toe leiden dat sommige e-mailberichten die naar geldige Apple- of Gmail-adressen worden verzonden, onjuist worden teruggestuurd als ongeldige e-mailadressen door de ISP-servers met de volgende reacties:

* &quot;550 5.1.1 &quot;E-mailadres&quot;: opzoekresultaat gebruiker is gelukt, maar er is geen gebruikersrecord gevonden.&quot;

* &quot;Ontworpen voor 550 &#39;e-mailadres&#39;-ontvanger&quot;

Merk op dat als het uitstel met het bericht &quot;452 gevraagde actie aborteerde: Probeer het later opnieuw&quot; wordt waargenomen - deze worden automatisch opnieuw geprobeerd en er zijn geen acties nodig. Zij zouden moeten verbeteren aangezien ISP volledige capaciteit terugkrijgt.

>[!NOTE]
>
>U kunt het Apple System Status Dashboard inschakelen [deze pagina](https://www.apple.com/support/systemstatus/){_blank}.
>
>U kunt het Google Workspace Status Dashboard inschakelen [deze pagina](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}.

## Gevolgen{#update-bounce-impact}

In het geval van een stroomonderbreking van ISP, kunnen de e-mails die door Campaign worden verzonden niet met succes aan hun ontvanger worden geleverd: deze e - mails worden ten onrechte als bounces gemarkeerd .

Adobe Campaign heeft deze ontvangers automatisch aan de quarantainelijst toegevoegd met een **[!UICONTROL Status]** instellen van **[!UICONTROL Quarantine]**. Om dit te verbeteren, moet u uw quarantainetabel in Campagne bijwerken door deze ontvangers te vinden en te verwijderen, of hun te veranderen **[!UICONTROL Status]** tot **[!UICONTROL Valid]** zodat de nachtelijke schoonmaakworkflow ze verwijdert.

Zie de onderstaande instructies voor meer informatie over de ontvangers die door dit probleem zijn beïnvloed.

## Proces voor bijwerken{#update-bounce-update}

U moet een vraag op uw quarantainetabel in werking stellen om alle beïnvloede ontvangers - bijvoorbeeld voor Apple, de adressen die, @icloud.com, @me.com, @mac.com omvatten - uit te filteren die potentieel door de stroomonderbreking werden beïnvloed zodat kunnen zij uit de quarantainelijst worden verwijderd, en in toekomstige de e-mailleveringen van de Campagne worden omvat.

Gebaseerd op het timeframe van het incident, en ISP, hieronder zijn de geadviseerde richtlijnen voor deze vraag.

* Voor Campagne v8- en Campaign Classic v7-omgevingen met informatie over de regels voor inkomende e-mail in het dialoogvenster **[!UICONTROL Error text]** veld van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-maildomein (@domein)** is gelijk aan domain1.com OR **E-maildomein (@domein)** is gelijk aan domain2.com OR **E-maildomein (@domein)** is gelijk aan domain3.com
   * **Status bijwerken (@lastModified)** op of na MM/DD/YYYY HH:MM:SS AM
   * **Status bijwerken (@lastModified)** op of vóór MM/DD/YYYY HH:MM:SS PM

* Voor Campaign Classic v7-instanties met SMTP-responsgegevens voor stuiteren in het dialoogvenster **[!UICONTROL Error text]** veld van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;550-5.1.1&quot; EN **Fouttekst (quarantainetekst)** bevat &quot;support.ISP.com&quot;

      waar &quot;support.ISP.com&quot; kan zijn: bijvoorbeeld &quot;support.apple.com&quot; of &quot;support.google.com&quot;

   * **Status bijwerken (@lastModified)** op of na MM/DD/YYYY HH:MM:SS AM
   * **Status bijwerken (@lastModified)** op of vóór MM/DD/YYYY HH:MM:SS PM


Als u de lijst met betrokken ontvangers hebt, kunt u deze instellen op de status **[!UICONTROL Valid]** zodat zij uit de quarantainelijst worden verwijderd door **[!UICONTROL Database cleanup]** of deze uit de tabel verwijderen.

**Verwante onderwerpen:**
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Kwalificatie van niet-bezorgde e-mails](understanding-delivery-failures.md#bounce-mail-qualification)
