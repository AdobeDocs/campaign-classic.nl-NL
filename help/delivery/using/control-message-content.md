---
product: campaign
title: Informatie over leverbaarbaarheid in Adobe Campaign Classic
description: Meer informatie over het beheren van de leverbaarheid in Adobe Campaign
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
role: User
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: de6e86eb2304a88e836c5759b87d7f38446ed357
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 5%

---

# De inhoud van uw bericht bepalen{#control-message-content}

Om ervoor te zorgen dat je e-mailberichten bij je ontvangers terechtkomen en je e-mailsnelheid verbeteren, moeten ze een aantal regels in acht nemen. Anders, kan de inhoud van bepaalde berichten als spam worden ontdekt. Adobe Campaign biedt u verschillende gereedschappen om ervoor te zorgen dat uw inhoud aan deze regels voldoet.

Volg de onderstaande principes bij het ontwerpen van uw berichtinhoud:

* [ adres van de Afzender ](#sender-address): het adres moet de afzender uitdrukkelijk identificeren. Het domein moet eigendom zijn van en geregistreerd zijn bij de afzender. Het domeinregister mag niet worden geprivatiseerd.
* [ Personalization ](#personalization): het personaliseren van inhoud en het bepalen van een verzendende tijd per ontvanger verhoogt de kansen van uw bericht dat wordt geopend.
* Afbeeldingen en tekst: respecteer een goede verhouding tussen tekst en afbeelding (bijvoorbeeld 60% tekst en 40% afbeeldingen).
* [ verbinding Unsubscription ](#opt-out) en landende pagina: de unsubscription verbinding is essentieel. Het formulier moet zichtbaar en geldig zijn en moet functioneel zijn.
* Voorproef: gebruik de hulpmiddelen die door Adobe Campaign worden aangeboden om de inhoud van uw e-mail te controleren en te optimaliseren ([ Inbox teruggevend ](#message-responsiveness), [ SpamAssassin ](#spamassassin)).

Voor extra uiteinden om leverbaarheid te optimaliseren wanneer het ontwerpen van inhoud, zie de ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html) Gids van de Beste praktijken van de Levering van de Adobe van 0}.[

>[!NOTE]
>
>Voor meer informatie bij het uitgeven van e-mailinhoud, zie [ de e-mailinhoud ](defining-the-email-content.md) bepalen en [ gepersonaliseerde inhoud ](design-and-personalize.md) bouwen.

## Adres van afzender {#sender-address}

Bepaalde ISPs controleren de geldigheid van het afzenderadres (**[!UICONTROL From]**) alvorens berichten goed te keuren. Een slecht geformuleerd adres kan ertoe leiden dat het door de ontvangende server wordt verworpen.

U moet ervoor zorgen dat het juiste adres wordt opgegeven op instantieniveau (menu **[!UICONTROL Tools > Advanced > deployment wizard...]**) of in de meest gebruikte scenario&#39;s.

Ga voor meer informatie naar [deze pagina](defining-the-email-content.md).

## Personalization {#personalization}

Om de ervaring van ontvangers te verbeteren en ze uw e-mail te laten openen, kunt u in Adobe Campaign uw berichten personaliseren.

Voor meer bij het gebruiken van verpersoonlijkingsgebieden in Adobe Campaign, zie [ deze sectie ](personalization-fields.md).

Sommige uiteinden om verpersoonlijking te optimaliseren wanneer het bouwen van uw inhoud wordt voorgesteld in [ deze sectie ](design-and-personalize.md#optimize-personalization).

## Koppeling en formulier uitschakelen {#opt-out}

Door gebrek, wanneer het bericht wordt geanalyseerd, controleert de a [ typologieregel ](steps-validating-the-delivery.md#validation-process-with-typologies) of een opt-out verbinding is omvat en produceert een waarschuwing als het mist. U kunt deze regel zodanig wijzigen dat er een fout optreedt in plaats van een eenvoudige waarschuwing en dat een levering wordt gestopt zonder deze koppeling.

U moet controleren of de koppeling om te weigeren correct werkt voordat u de koppeling verzendt. Wanneer u bijvoorbeeld de proefdruk verzendt, moet u controleren of de koppeling geldig is, of het formulier online is en of bij validatie de waarde van het veld **[!UICONTROL No longer contact this recipient]** wordt gewijzigd in **[!UICONTROL Yes]** . Deze controle moet u systematisch uitvoeren, omdat een menselijke fout altijd mogelijk is bij het invoeren van de koppeling of bij het wijzigen van het formulier.

Leer hoe te om een opt-out verbinding [ in deze sectie ](personalization-blocks.md#personalization-blocks-example) op te nemen.

Als er een probleem wordt vastgesteld met betrekking tot het opzeggen van een abonnement nadat de levering is gestart, is het nog steeds mogelijk om handmatig een abonnement op te zeggen (met behulp van bijvoorbeeld de functie voor het bijwerken van de massa) voor de ontvangers die op de koppeling om te weigeren klikken, zelfs als zij hun keuze niet konden bevestigen.

Als algemene regel geldt dat u ontvangers die zich willen afmelden, niet in de weg wilt staan door van hen te verlangen dat ze bijvoorbeeld velden invullen zoals hun e-mailadres of naam. Het formulier mag maar één validatieknop hebben en de koppeling moet alleen op de gecodeerde id worden uitgevoerd.

Het aanvragen van aanvullende bevestiging is niet betrouwbaar: een gebruiker kan twee e-mailadressen hebben die zijn omgeleid naar hetzelfde vak (bijvoorbeeld: firstname.lastname@club.com en firstname.lastname@internet-club.com). Als de ontvanger zich alleen het eerste adres kan herinneren en zich via een naar de andere verzonden bericht wil afmelden, zal het formulier dit weigeren omdat de gecodeerde id en het ingevoerde e-mailadres niet overeenkomen.

## Inboxrendering {#message-responsiveness}

Voordat u uw bericht verzendt, kunt u de reactiesnelheid van uw bericht testen door te controleren hoe uw bericht eruitziet op verschillende apparaten. Dit is om ervoor te zorgen dat het op een optimale manier op een verscheidenheid van Webcliënten, Webpost en apparaten zal worden getoond.

Om dit mogelijk te maken, legt Adobe Campaign de weergave vast en stelt deze beschikbaar in een specifiek rapport. Op deze manier kunt u het voorbeeld van het verzonden bericht bekijken in de verschillende contexten waarin het bericht mogelijk wordt ontvangen.

Voor meer op dit, zie [ Inbox teruggevend ](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign kan worden gevormd om met SpamAssassin te werken. Dit maakt het mogelijk om e-mailberichten te scoren om te bepalen of een bericht het risico loopt om als spam door de anti-anti-spamhulpmiddelen worden beschouwd die op ontvangstbewijs worden gebruikt.

Voordat u met de levering begint, kunt u op het tabblad **[!UICONTROL Preview]** de risico&#39;s evalueren. Het resultaat van de test wordt aangegeven met een waarschuwingsbericht.

Leer meer in deze [ sectie ](spamassassin.md).
