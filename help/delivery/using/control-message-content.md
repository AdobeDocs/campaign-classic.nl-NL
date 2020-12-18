---
solution: Campaign Classic
product: campaign
title: Informatie over leverbaarbaarheid in Adobe Campaign Classic
description: Meer weten over het beheren van de leverbaarbaarheid in Adobe Campaign Classic?
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# De inhoud van uw bericht besturen{#control-message-content}

Om de e-mailleverbaarheid te verbeteren en ervoor te zorgen dat de e-mails bij de ontvangers terechtkomen, moet het e-mailbericht voldoen aan een aantal onderstaande regels.

## Adres van afzender {#sender-address}

Bepaalde ISPs controleert de geldigheid van het afzenderadres (van) alvorens berichten goed te keuren. Een slecht geformuleerd adres kan ertoe leiden dat het door de ontvangende server wordt verworpen. U moet ervoor zorgen dat een correct adres op instantieniveau (menu **[!UICONTROL Tools > Advanced > Deployment wizard...]**) of in de het vaakst gebruikte scenario&#39;s wordt gegeven.

## Koppeling en formulier {#opt-out} uitschakelen

Wanneer het bericht wordt geanalyseerd, controleert standaard een typologische regel of een opt-out-koppeling is opgenomen en wordt een waarschuwing gegenereerd als deze ontbreekt. U kunt deze regel zodanig wijzigen dat er een fout optreedt in plaats van een eenvoudige waarschuwing en dat een levering wordt gestopt zonder deze koppeling.

U moet controleren of de koppeling om te weigeren correct werkt voordat u de koppeling verzendt. Wanneer u bijvoorbeeld de proefdruk verzendt, moet u controleren of de koppeling geldig is, of het formulier online is en of bij validatie de waarde van het veld **[!UICONTROL No longer contact this recipient]** wordt gewijzigd in **[!UICONTROL Yes]**. Deze controle moet u systematisch uitvoeren, omdat een menselijke fout altijd mogelijk is bij het invoeren van de koppeling of bij het wijzigen van het formulier.

Als er een probleem wordt vastgesteld met betrekking tot het opzeggen van een abonnement nadat de levering is gestart, is het nog steeds mogelijk om handmatig een abonnement op te zeggen (met behulp van bijvoorbeeld de functie voor het bijwerken van de massa) voor de ontvangers die op de koppeling om te weigeren klikken, zelfs als zij hun keuze niet konden bevestigen.

Als algemene regel geldt dat u ontvangers die zich willen afmelden, niet in de weg wilt staan door van hen te verlangen dat ze bijvoorbeeld velden invullen zoals hun e-mailadres of naam. Het formulier mag maar één validatieknop hebben en de koppeling moet alleen op de gecodeerde id worden uitgevoerd. Aanvullende bevestiging aanvragen is niet betrouwbaar: een gebruiker kan twee e-mailadressen naar hetzelfde vak hebben omgeleid (bijvoorbeeld: firstname.lastname@club.com en firstname.lastname@internet-club.com). Als de ontvanger zich alleen het eerste adres kan herinneren en zich via een naar de andere verzonden bericht wil afmelden, zal het formulier dit weigeren omdat de gecodeerde id en het ingevoerde e-mailadres niet overeenkomen.

## SpamAssassin {#spamassassin}

Adobe Campaign kan worden gevormd om met SpamAssassin te werken. Dit maakt het mogelijk om e-mailberichten te scoren om te bepalen of een bericht het risico loopt om als spam door de anti-anti-spamhulpmiddelen worden beschouwd die op ontvangstbewijs worden gebruikt.

Voordat u met de levering begint, kunt u op het tabblad Voorbeeld de risico&#39;s evalueren. Het resultaat van de test wordt aangegeven met een waarschuwingsbericht.

Meer informatie vindt u in deze [sectie](../../delivery/using/spamassassin.md).