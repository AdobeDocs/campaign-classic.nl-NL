---
product: campaign
title: Informatie over leverbaarbaarheid in Adobe Campaign Classic
description: Meer informatie over het beheren van de leverbaarheid in Adobe Campaign
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
role: User
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 6%

---

# De inhoud van uw bericht bepalen{#control-message-content}


Om ervoor te zorgen dat je e-mailberichten bij je ontvangers terechtkomen en je e-mailsnelheid verbeteren, moeten ze een aantal regels in acht nemen. Anders, kan de inhoud van bepaalde berichten als spam worden ontdekt. Adobe Campaign biedt u verschillende gereedschappen om ervoor te zorgen dat uw inhoud aan deze regels voldoet.

Volg de onderstaande principes bij het ontwerpen van uw berichtinhoud:

* [Adres van afzender](#sender-address): het adres moet de afzender uitdrukkelijk identificeren. Het domein moet eigendom zijn van en geregistreerd zijn bij de afzender. Het domeinregister mag niet worden geprivatiseerd.
* [Personalisatie](#personalization): het personaliseren van inhoud en het bepalen van een verzendingstijd per ontvanger verhogen de kansen van uw bericht dat wordt geopend.
* Afbeeldingen en tekst: respecteer een goede verhouding tussen tekst en afbeelding (bijvoorbeeld 60% tekst en 40% afbeeldingen).
* [Koppeling met abonnement opheffen](#opt-out) en landingspagina: de koppeling om het abonnement op te zeggen is essentieel. Het formulier moet zichtbaar en geldig zijn en moet functioneel zijn.
* Voorbeeld: gebruik de gereedschappen van Adobe Campaign om de inhoud van uw e-mail te controleren en te optimaliseren ([Inbox-rendering](#message-responsiveness), [SpamAssassin](#spamassassin)).

Voor meer tips voor het optimaliseren van de leesbaarheid bij het ontwerpen van inhoud raadpleegt u de [Handleiding voor beste praktijken bij de levering van Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html).

>[!NOTE]
>
>Voor meer informatie over het bewerken van e-mailinhoud raadpleegt u [De e-mailinhoud definiëren](defining-the-email-content.md) en [Aangepaste inhoud maken](design-and-personalize.md).

## Adres van afzender {#sender-address}

Bepaalde ISPs controleren de geldigheid van het afzenderadres (**[!UICONTROL From]**) voordat berichten worden geaccepteerd. Een slecht geformuleerd adres kan ertoe leiden dat het door de ontvangende server wordt verworpen.

U moet ervoor zorgen dat het juiste adres wordt opgegeven op instantieniveau (menu **[!UICONTROL Tools > Advanced > Deployment wizard...]**) of in de meest gebruikte scenario&#39;s.

Ga voor meer informatie naar [deze pagina](defining-the-email-content.md).

## Personalisatie {#personalization}

Om de ervaring van ontvangers te verbeteren en ze uw e-mail te laten openen, kunt u in Adobe Campaign uw berichten personaliseren.

Ga voor meer informatie over het gebruik van personalisatievelden in Adobe Campaign naar [deze sectie](personalization-fields.md).

Enkele tips voor het optimaliseren van personalisatie tijdens het maken van uw inhoud worden weergegeven in [deze sectie](design-and-personalize.md#optimize-personalization).

## Koppeling en formulier uitschakelen {#opt-out}

Wanneer het bericht wordt geanalyseerd, wordt standaard een [typologieregel](steps-validating-the-delivery.md#validation-process-with-typologies) Hiermee wordt gecontroleerd of een opt-out-koppeling is opgenomen en wordt een waarschuwing gegenereerd als deze ontbreekt. U kunt deze regel zodanig wijzigen dat er een fout optreedt in plaats van een eenvoudige waarschuwing en dat een levering wordt gestopt zonder deze koppeling.

U moet controleren of de koppeling om te weigeren correct werkt voordat u de koppeling verzendt. Als u bijvoorbeeld de proefdruk verzendt, controleert u of de koppeling geldig is, of het formulier online is en of de waarde van de optie **[!UICONTROL No longer contact this recipient]** veld naar **[!UICONTROL Yes]**. Deze controle moet u systematisch uitvoeren, omdat een menselijke fout altijd mogelijk is bij het invoeren van de koppeling of bij het wijzigen van het formulier.

Meer informatie over het invoegen van een koppeling om te weigeren [in deze sectie](personalization-blocks.md#personalization-blocks-example).

Als er een probleem wordt vastgesteld met betrekking tot het opzeggen van een abonnement nadat de levering is gestart, is het nog steeds mogelijk om handmatig een abonnement op te zeggen (met behulp van bijvoorbeeld de functie voor het bijwerken van de massa) voor de ontvangers die op de koppeling om te weigeren klikken, zelfs als zij hun keuze niet konden bevestigen.

Als algemene regel geldt dat u ontvangers die zich willen afmelden, niet in de weg wilt staan door van hen te verlangen dat ze bijvoorbeeld velden invullen zoals hun e-mailadres of naam. Het formulier mag maar één validatieknop hebben en de koppeling moet alleen op de gecodeerde id worden uitgevoerd.

Het aanvragen van aanvullende bevestiging is niet betrouwbaar: een gebruiker kan twee e-mailadressen hebben die zijn omgeleid naar hetzelfde vak (bijvoorbeeld: firstname.lastname@club.com en firstname.lastname@internet-club.com). Als de ontvanger zich alleen het eerste adres kan herinneren en zich via een naar de andere verzonden bericht wil afmelden, zal het formulier dit weigeren omdat de gecodeerde id en het ingevoerde e-mailadres niet overeenkomen.

## Inboxrendering {#message-responsiveness}

Voordat u uw bericht verzendt, kunt u de reactiesnelheid van uw bericht testen door te controleren hoe uw bericht eruitziet op verschillende apparaten. Dit is om ervoor te zorgen dat het op een optimale manier op een verscheidenheid van Webcliënten, Webpost en apparaten zal worden getoond.

Om dit mogelijk te maken, legt Adobe Campaign de weergave vast en stelt deze beschikbaar in een specifiek rapport. Op deze manier kunt u het voorbeeld van het verzonden bericht bekijken in de verschillende contexten waarin het bericht mogelijk wordt ontvangen.

Zie voor meer informatie [Inbox-rendering](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign kan worden gevormd om met SpamAssassin te werken. Dit maakt het mogelijk om e-mailberichten te scoren om te bepalen of een bericht het risico loopt om als spam door de anti-anti-spamhulpmiddelen worden beschouwd die op ontvangstbewijs worden gebruikt.

Voordat u met de levering begint, **[!UICONTROL Preview]** kunt u de risico&#39;s evalueren. Het resultaat van de test wordt aangegeven met een waarschuwingsbericht.

Meer informatie in deze [sectie](spamassassin.md).
