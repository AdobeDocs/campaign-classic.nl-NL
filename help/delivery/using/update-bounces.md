---
product: campaign
title: Kwalificatie van niet-bezorging bijwerken na een ISP-uitval
description: Leer hoe te om stuitkwalificatie na een ISP stroomonderbreking bij te werken
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: 209ccbcac20052826dad0c55b35173be20b10114
workflow-type: tm+mt
source-wordcount: '495'
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
>U kunt het Apple System Status Dashboard inschakelen [deze pagina](https://www.apple.com/support/systemstatus/){_blank}.
>
>U kunt het Google Workspace Status Dashboard inschakelen [deze pagina](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}.
>

## Gevolgen{#update-bounce-impact}

Als een internetprovider buiten beschouwing blijft, kunnen e-mails die via Campagne worden verzonden niet succesvol aan de ontvanger worden bezorgd: deze e-mails worden ten onrechte gemarkeerd als steunkleuren.

Volgens de standaardlogica voor stuitverwerking heeft Adobe Campaign deze ontvangers automatisch aan de quarantainelijst toegevoegd met een **[!UICONTROL Status]** instellen van **[!UICONTROL Quarantine]**. Om dit te verbeteren, moet u uw quarantainetabel in Campagne bijwerken door deze ontvangers te vinden en te verwijderen, of hun te veranderen **[!UICONTROL Status]** tot **[!UICONTROL Valid]** zodat de nachtelijke schoonmaakworkflow ze verwijdert.

Zie de onderstaande instructies voor meer informatie over de ontvangers die door dit probleem zijn beïnvloed.

## Proces voor bijwerken{#update-bounce-update}

U moet een vraag op uw quarantainetabel in werking stellen om alle beïnvloede ontvangers - bijvoorbeeld voor Apple, de adressen die omvatten, @icloud.com, @me.com, @mac.com - die potentieel door de stroomonderbreking werden beïnvloed zodat zij uit de quarantainelijst kunnen worden verwijderd, en in toekomstige e-mailleveringen van de Campagne worden omvat.

Gebaseerd op het timeframe van het incident, en ISP, hieronder zijn de geadviseerde richtlijnen voor deze vraag.

* Voor Campagneomgevingen met informatie over de binnenkomende e-mailregel in het dialoogvenster **[!UICONTROL Error text]** veld van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-maildomein (@domein)** gelijk aan domain1.com OR **E-maildomein (@domein)** gelijk aan domain2.com OR **E-maildomein (@domein)** is gelijk aan domain3.com
   * **Status bijwerken (@lastModified)** op of na `MM/DD/YYYY HH:MM:SS AM`
   * **Status bijwerken (@lastModified)** op of voor `MM/DD/YYYY HH:MM:SS PM`

* Voor Campagneomgevingen met SMTP-stuiteringsresponsinformatie in het dialoogvenster **[!UICONTROL Error text]** veld van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;550-5.1.1&quot; EN **Fouttekst (quarantainetekst)** bevat &quot;support.ISP.com&quot;

     waar &quot;support.ISP.com&quot; kan zijn: bijvoorbeeld &quot;support.apple.com&quot; of &quot;support.google.com&quot;

   * **Status bijwerken (@lastModified)** op of na `MM/DD/YYYY HH:MM:SS AM`
   * **Status bijwerken (@lastModified)** op of voor  `MM/DD/YYYY HH:MM:SS PM`


Als u de lijst met betrokken ontvangers hebt, kunt u deze instellen op de status **[!UICONTROL Valid]** zodat zij uit de quarantainelijst worden verwijderd door **[!UICONTROL Database cleanup]** of deze uit de tabel verwijderen.

**Verwante onderwerpen:**
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Bounce mail-kwalificatie](understanding-delivery-failures.md#bounce-mail-qualification)
