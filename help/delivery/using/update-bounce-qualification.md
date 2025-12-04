---
product: campaign
title: De stuitkwalificatie bijwerken na Apple 2021-storing
description: Leer hoe u de stuiterende kwalificatie bijwerkt na een Apple 2021-storing
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Onjuiste harde grenzen bijwerken na Apple-storing {#update-bounce-qualification.md}

## Context

Op 26 april 2021 leidde een wereldwijde uitgave bij Apple ertoe dat sommige e-mailberichten die naar geldige Apple-e-mailadressen werden verzonden onjuist werden teruggestuurd als ongeldige e-mailadressen door Apple-servers met de volgende reactie: &quot;550 5.1.1 &#39;email address&#39;: user lookup success but no user record found.&quot;

Dit probleem is op 26-4-17-2010 opgetreden en duurde 7 uur &#39;s middags.

>[!NOTE]
>
>U kunt het dashboard van de Status van het Systeem van Apple op [&#x200B; deze pagina &#x200B;](https://www.apple.com/support/systemstatus/) controleren.

Als een internetprovider buiten beschouwing blijft, kunnen e-mails die via Campagne worden verzonden niet succesvol aan de ontvanger worden bezorgd: deze e-mails worden ten onrechte gemarkeerd als steunkleuren.

Volgens de standaardlogica voor stuitverwerking heeft Adobe Campaign deze ontvangers automatisch toegevoegd aan de quarantainelijst met een **[!UICONTROL Status]** instelling van **[!UICONTROL Quarantine]** . U kunt dit corrigeren door uw quarantainetabel in Campagne bij te werken door deze ontvangers te zoeken en te verwijderen of door hun **[!UICONTROL Status]** in **[!UICONTROL Valid]** te wijzigen zodat deze tijdens de nachtelijke opschoonworkflow worden verwijderd.

Om de ontvangers te vinden die door deze kwestie werden beïnvloed, of in het geval dat dit opnieuw met een andere ISP gebeurt, gelieve de instructies hieronder te zien.

## Proces voor bijwerken

U moet een query uitvoeren op uw quarantainetabel om alle Apple-ontvangers uit te filteren, waaronder @icloud.com, @me.com, @mac.com, die mogelijk zijn beïnvloed door de storing, zodat ze kunnen worden verwijderd uit de quarantainelijst en kunnen worden opgenomen in toekomstige e-mailleveringen voor campagnes.

Gebaseerd op het tijdkader van het incident, hieronder zijn de geadviseerde richtlijnen voor deze vraag.

>[!IMPORTANT]
>
>Deze datums/tijden zijn gebaseerd op de tijdzone van de Oost-Standard (EST). Pas de tijdzone van uw instantie aan.

* Voor Campagne-instanties met SMTP-responsgegevens voor stuiteren in het veld **[!UICONTROL Error text]** van de quarantainelijst:

   * **Tekst van de Fout (quarantainetekst)** bevat &quot;gebruikersraadplegingssucces maar geen gevonden gebruikersverslag&quot;EN **Tekst van de Fout (quarantainetekst)** bevat &quot;support.apple.com&quot;
   * **status van de Update (@lastModified)** op of na 4/26/2021 07 :00: 00 AM
   * **status van de Update (@lastModified)** op of vóór 4/26/2021 01 :00: 00 PM

* Voor campagneinstanties met informatie over de regel Inbound Email in het veld **[!UICONTROL Error text]** van de quarantainelijst:

   * **tekst van de Fout (quarantainetekst)** bevat &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-maildomein (@domein)** is gelijk aan icloud.com OF **E-maildomein (@domein)** gelijk aan me.com OF **E-maildomein (@domein)** gelijk aan mac.com
   * **status van de Update (@lastModified)** op of na 4/26/2021 07 :00: 00 AM
   * **status van de Update (@lastModified)** op of vóór 4/26/2021 01 :00: 00 PM

Als u de lijst met betrokken ontvangers hebt, kunt u ze instellen op de status **[!UICONTROL Valid]** zodat ze via de **[!UICONTROL Database cleanup]** -workflow uit de quarantainelijst worden verwijderd of gewoon uit de tabel verwijderen.

**Verwante onderwerpen:**
* [Leveringsfouten begrijpen](delivery-failures-quarantine.md)
* [Bounce mail-kwalificatie](delivery-failures-quarantine.md#bounce-mail-qualification)
