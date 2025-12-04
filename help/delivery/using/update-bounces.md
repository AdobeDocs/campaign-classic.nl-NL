---
product: campaign
title: Kwalificatie van niet-bezorging bijwerken na een ISP-uitval
description: Leer hoe te om stuitkwalificatie na een ISP stroomonderbreking bij te werken
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 3%

---

# Onjuiste hard bounces bijwerken na een ISP-storing {#update-bounces}



## Context{#update-bounce-context}

Als een internetprovider buiten beschouwing blijft, kunnen e-mails die via Campagne worden verzonden niet succesvol aan de ontvanger worden bezorgd: deze e-mails worden ten onrechte gemarkeerd als steunkleuren.

Globale problemen bij Apple of Gmail kunnen er bijvoorbeeld toe leiden dat sommige e-mailberichten die naar geldige Apple- of Gmail-adressen worden verzonden, onjuist worden teruggestuurd als ongeldige e-mailadressen door de ISP-servers met de volgende reacties:

* &quot;550 5.1.1 &#39;E-mailadres&#39;: opzoekopdracht geslaagd voor gebruiker, maar geen gebruikersrecord gevonden.&quot;

* &quot;Ontworpen voor 550 &#39;e-mailadres&#39;-ontvanger&quot;

Let op: als het uitstellen van de melding &quot;452 gevraagde actie afgebroken: probeer het later opnieuw&quot; wordt waargenomen, worden deze automatisch opnieuw geprobeerd en zijn geen acties nodig. Zij zouden moeten verbeteren aangezien ISP volledige capaciteit terugkrijgt.

>[!NOTE]
>
>U kunt het dashboard van de Status van het Systeem van Apple op [&#x200B; deze pagina &#x200B;](https://www.apple.com/support/systemstatus/){_blank} controleren.
>
>U kunt het Dashboard van de Status van Google Workspace op [&#x200B; deze pagina &#x200B;](https://www.google.com/appsstatus#hl=en&v=status){_blank} controleren.
>

## Gevolgen{#update-bounce-impact}

Als een internetprovider buiten beschouwing blijft, kunnen e-mails die via Campagne worden verzonden niet succesvol aan de ontvanger worden bezorgd: deze e-mails worden ten onrechte gemarkeerd als steunkleuren.

Volgens de standaardlogica voor stuitverwerking heeft Adobe Campaign deze ontvangers automatisch toegevoegd aan de quarantainelijst met een **[!UICONTROL Status]** instelling van **[!UICONTROL Quarantine]** . U kunt dit corrigeren door uw quarantainetabel in Campagne bij te werken door deze ontvangers te zoeken en te verwijderen of door hun **[!UICONTROL Status]** in **[!UICONTROL Valid]** te wijzigen zodat deze tijdens de nachtelijke opschoonworkflow worden verwijderd.

Zie de onderstaande instructies voor meer informatie over de ontvangers die door dit probleem zijn beïnvloed.

## Proces voor bijwerken{#update-bounce-update}

U moet een vraag op uw quarantainetabel in werking stellen om alle beïnvloede ontvangers - bijvoorbeeld voor Apple, de adressen die omvatten, @icloud.com, @me.com, @mac.com - die potentieel door de stroomonderbreking werden beïnvloed zodat zij uit de quarantainelijst kunnen worden verwijderd, en in toekomstige e-mailleveringen van de Campagne worden omvat.

Gebaseerd op het timeframe van het incident, en ISP, hieronder zijn de geadviseerde richtlijnen voor deze vraag.

* Voor Campagneomgevingen met informatie over de regel Inbound-e-mail in het veld **[!UICONTROL Error text]** van de quarantainelijst:

   * **tekst van de Fout (quarantainetekst)** bevat &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-maildomein (@domein)** is gelijk aan domain1.com OF **E-maildomein (@domein)** gelijk aan domain2.com OF **E-maildomein (@domein)** gelijk aan domain3.com
   * **status van de Update (@lastModified)** op of na `MM/DD/YYYY HH:MM:SS AM`
   * **status van de Update (@lastModified)** op of vóór `MM/DD/YYYY HH:MM:SS PM`

* Voor Campagneomgevingen met SMTP-stuiteringsresponsinformatie in het veld **[!UICONTROL Error text]** van de quarantainelijst:

   * **de tekst van de Fout (quarantainetekst)** bevat &quot;550-5.1.1&quot;EN **Tekst van de Fout (quarantainetekst)** bevat &quot;support.ISP.com&quot;

     waar &quot;support.ISP.com&quot; kan zijn: bijvoorbeeld &quot;support.apple.com&quot; of &quot;support.google.com&quot;

   * **status van de Update (@lastModified)** op of na `MM/DD/YYYY HH:MM:SS AM`
   * **status van de Update (@lastModified)** op of vóór `MM/DD/YYYY HH:MM:SS PM`


Als u de lijst met betrokken ontvangers hebt, kunt u ze instellen op de status **[!UICONTROL Valid]** zodat ze via de **[!UICONTROL Database cleanup]** -workflow uit de quarantainelijst worden verwijderd of gewoon uit de tabel verwijderen.

**Verwante onderwerpen:**
* [Leveringsfouten begrijpen](delivery-failures-quarantine.md)
* [Bounce mail-kwalificatie](delivery-failures-quarantine.md#bounce-mail-qualification)
