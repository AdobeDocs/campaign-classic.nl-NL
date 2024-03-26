---
product: campaign
title: De stuitkwalificatie bijwerken na Apple 2021-storing
description: Leer hoe u de stuiterende kwalificatie bijwerkt na een Apple 2021-storing
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Onjuiste harde grenzen bijwerken na Apple-storing {#update-bounce-qualification.md}

## Context

Op 26 april 2021 leidde een wereldwijde uitgave bij Apple ertoe dat sommige e-mailberichten die naar geldige Apple-e-mailadressen werden verzonden onjuist werden teruggestuurd als ongeldige e-mailadressen door Apple-servers met de volgende reactie: &quot;550 5.1.1 &#39;email address&#39;: user lookup success but no user record found.&quot;

Dit probleem is op 26-4-17-2010 opgetreden en duurde 7 uur &#39;s middags.

>[!NOTE]
>
>U kunt het Apple System Status Dashboard inschakelen [deze pagina](https://www.apple.com/support/systemstatus/).

Als een internetprovider buiten beschouwing blijft, kunnen e-mails die via Campagne worden verzonden niet succesvol aan de ontvanger worden bezorgd: deze e-mails worden ten onrechte gemarkeerd als steunkleuren.

Volgens de standaardlogica voor stuitverwerking heeft Adobe Campaign deze ontvangers automatisch aan de quarantainelijst toegevoegd met een **[!UICONTROL Status]** instellen van **[!UICONTROL Quarantine]**. Om dit te verbeteren, moet u uw quarantainetabel in Campagne bijwerken door deze ontvangers te vinden en te verwijderen, of hun te veranderen **[!UICONTROL Status]** tot **[!UICONTROL Valid]** zodat de nachtelijke schoonmaakworkflow ze verwijdert.

Om de ontvangers te vinden die door deze kwestie werden beïnvloed, of in het geval dat dit opnieuw met een andere ISP gebeurt, gelieve de instructies hieronder te zien.

## Proces voor bijwerken

U moet een query uitvoeren op uw quarantainetabel om alle Apple-ontvangers uit te filteren, waaronder @icloud.com, @me.com, @mac.com, die mogelijk zijn beïnvloed door de storing, zodat ze kunnen worden verwijderd uit de quarantainelijst en kunnen worden opgenomen in toekomstige e-mailleveringen voor campagnes.

Gebaseerd op het tijdkader van het incident, hieronder zijn de geadviseerde richtlijnen voor deze vraag.

>[!IMPORTANT]
>
>Deze datums/tijden zijn gebaseerd op de tijdzone van de Oost-Standard (EST). Pas de tijdzone van uw instantie aan.

* Voor Campagne-instanties met SMTP-responsgegevens voor stuiteren in het dialoogvenster **[!UICONTROL Error text]** veld van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;user lookup success but no user record found&quot; EN **Fouttekst (quarantainetekst)** bevat &quot;support.apple.com&quot;
   * **Status bijwerken (@lastModified)** 26-04-2021 07:00:00
   * **Status bijwerken (@lastModified)** 26-04-2021 01:00:22:00

* Voor campagneinstanties met de informatie over de binnenkomende e-mailregel in het dialoogvenster **[!UICONTROL Error text]** veld van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-maildomein (@domein)** gelijk aan icloud.com OR **E-maildomein (@domein)** gelijk aan me.com OR **E-maildomein (@domein)** is gelijk aan mac.com
   * **Status bijwerken (@lastModified)** 26-04-2021 07:00:00
   * **Status bijwerken (@lastModified)** 26-04-2021 01:00:22:00

Als u de lijst met betrokken ontvangers hebt, kunt u deze instellen op de status **[!UICONTROL Valid]** zodat zij uit de quarantainelijst worden verwijderd door **[!UICONTROL Database cleanup]** of deze uit de tabel verwijderen.

**Verwante onderwerpen:**
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Bounce mail-kwalificatie](understanding-delivery-failures.md#bounce-mail-qualification)
