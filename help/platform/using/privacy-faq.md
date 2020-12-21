---
solution: Campaign Classic
product: campaign
title: Privacy en toestemming
description: Meer informatie over privacy en toestemming
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 5639f08ad709597d5f5c9e6bbd6932cffcbde40f
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 97%

---


# Veelgestelde vragen over privacy {#privacy-faq}

Dit zijn een paar veelgestelde vragen over privacy en toestemming bij het gebruik van Adobe Campaign.

## Belangrijke termen {#key-terms}

### Wat zijn de belangrijkste termen in verband met privacy?

De onderstaande items zijn gekoppeld aan de belangrijkste termen en begrippen in verband met privacy en toestemming in Adobe Campaign:

* [Regels voor privacybeheer](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Persoonsgegevens en persona&#39;s](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Toegangsrecht en recht om te worden vergeten](../../platform/using/privacy-management.md#right-access-forgotten)
* [Toestemming, retentie en rollen](../../platform/using/privacy-management.md#consent-retention-roles)

## Gereedheid voor privacywetgeving {#privacy-regulations-readiness}

### Wat stelt Adobe Campaign voor om te voldoen aan de nieuwste privacyregels?

Adobe geeft geen juridisch advies. U kunt het beste samenwerken met uw eigen juridisch adviseurs om ervoor te zorgen dat alle noodzakelijke stappen worden gezet in de aanloop naar gereedheid voor de AVG, CCPA, PDPA, LGPD of andere toepasselijke wetgeving.

**Voorbereiden op verzoeken om toegang tot en verwijdering van gegevens**

* Identificeer een proces voor de ontvangst van/reactie op verzoeken van betrokkenen, inclusief het aanwijzen van een contactpunt voor privacy.

* Bekijk de verschillende klantgegevens die in Adobe Campaign zijn opgeslagen en bepaal de unieke ID’s (waarschijnlijk meer dan een).

* Stel een beleid en een proces vast voor validatie/authentificatie van de identiteit van de betrokkene.

* Zorg ervoor dat de reactie van de betrokkene gemakkelijk te begrijpen is.

**Toestemming overwegen**

* Zorg voor de noodzakelijke vermeldingen en updates van alle contactpunten voor het vastleggen van gegevens voor de AVG (denk bijvoorbeeld aan taal, een mechanisme voor toestemming en toestemmingslogs).

* Zorg ervoor dat alle marketing-e-mails koppelingen bevatten voor uitschrijving.

* Evalueer de algemene strategie voor e-mailmarketing om geospecifieke implementaties te bepalen.

**Gegevens begrijpen**

* Bekijk alle bronnen voor het importeren en vastleggen van gegevens waaruit gegevens naar Adobe Campaign gaan, en documenteer welke velden worden gebruikt voor uw marketingactiviteiten.

* Verwijder ongebruikte gegevenskenmerken uit uw Adobe Campaign-database.

* Gebruik de gegevens die in Adobe Campaign beschikbaar zijn, voor het doel dat is vastgelegd en bied uw ontvangers beter gepersonaliseerde ervaringen.

* U kunt toestemmingen voor gegevenstoegang reviewen en bijwerken zodat gebruikers van Adobe Campaign volledig gebruik kunnen maken van uitsluitend die gegevens die nodig zijn om hun campagnes te voeren, maar geen verdere toegang tot gegevens hebben.

* Zorg ervoor dat elke gebruiker van Adobe Campaign de juiste toegangsrechten heeft om de vereiste taken uit te voeren, maar geen extra rechten heeft om andere taken uit te voeren.

## Gebruikersbetrokkenheid behouden {#preserve-user-engagement}

### Hoe kunnen gegevenscontrollers toestemming krijgen met minimale gevolgen voor gebruikersbetrokkenheid?

In gevallen waarin voor bepaalde marketingactiviteiten toestemming nodig is, moet de toestemming van de consument actief zijn (d.w.z. geen stilzwijgende toestemming of van tevoren geselecteerde vakjes). De toestemming mag niet gebundeld zijn en ook geen voorwaarde zijn voor het aanbieden van de services.

Er kunnen zelfs gevallen zijn waarin bepaalde toestemmingen moeten worden vernieuwd om het gebruik van gegevens te kunnen voortzetten.

In plaats van deze strengere toestemmingsvereisten als een risico te zien voor het marktwezen kunnen marketeers ze beter verwelkomen als een echte aanwijzing voor merkbetrokkenheid en loyaliteit, klanttevredenheid en vertrouwen.

## Toestemming beheren {#manage-consent}

### Hoe kunnen gegevenscontrollers in Adobe Campaign toestemming beheren?

Adobe Campaign biedt al mogelijkheden om op meer niveaus dan de meeste marketeers toestemming te beheren via aangepaste gegevensvelden of via een of meer services.

Marketeers moeten bij hun juridisch adviseur informeren naar richtlijnen en vervolgens gebruikmaken van de ingebouwde opties van Adobe Campaign.

Dat kan bijvoorbeeld door het gegevensmodel in Adobe Campaign zodanig uit te breiden dat niet alleen wordt bijgehouden of mensen zich hebben aangemeld, maar ook het tijdstempel van de opt-in, en één of andere indicatie die de exacte reikwijdte van de toestemming vastlegt.

## Gegevensverwijdering {#data-deletion}

### Welke gegevens kunnen gegevenscontrollers in Adobe Campaign verwijderen als reactie op een klantverzoek van een betrokkene?

Alle gegevens die aan de betrokkene zijn gekoppeld, worden verwijderd, inclusief ingebouwde en aangepaste tabellen.

Technisch gezien worden alle gegevens verwijderd die met `integrity="own"` aan de betrokkene zijn gekoppeld.

Als gegevenscontroller kunt u dit aanpassen door de integriteit te wijzigen van koppelingen die in de gegevensplanningen zijn gedefinieerd (bijvoorbeeld als u een zakelijke rechtvaardiging hebt om bepaalde gegevens niet te verwijderen).

### Welke invloed heeft het verwijderen van verzendings- en trackinglogs op rapporten?

Rapporten in Adobe Campaign zijn gebaseerd op indicatoren die worden berekend aan de hand van samengevoegde gegevens uit verzendings- en trackinglogs. Daardoor zou de verwijdering van individuele logboeken geen invloed moeten hebben op de cijfers die in de rapporten worden weergegeven.

## Gegevens opnieuw importeren {#re-import-data}

### Moet ik er rekening mee houden dat gegevens op een later tijdstip opnieuw kunnen worden geïmporteerd?

In Adobe Campaign worden records vaak geüpload vanuit een externe gegevensbron.

Als gegevenscontroller moet u ervoor zorgen dat u, wanneer u een verwijderingsverzoek ontvangt, alle noodzakelijke gegevens over de betrokkene van al uw systemen verwijdert.

## Opnieuw aanmelden {#opt-in-again}

**Kan een betrokkene, wiens gegevens uit Adobe Campaign zijn gewist, zich later opnieuw aanmelden?**

Een betrokkene kan zich opnieuw aanmelden of als nieuwe ontvanger worden toegevoegd nadat zijn of haar gegevens uit Adobe Campaign zijn gewist.

U kunt de audit trail gebruiken waarin wordt vermeld wanneer de eerdere verwijdering is uitgevoerd en wanneer de nieuwe ontvanger is gemaakt.