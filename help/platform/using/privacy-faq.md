---
solution: Campaign Classic
product: campaign
title: Privacy en toestemming
description: Meer informatie over privacy en toestemming
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 9e31f69fde38dcdc7f4e6d3ba3fb17911f96ded8
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# Veelgestelde vragen over privacy {#privacy-faq}

Hier volgen enkele veelgestelde vragen over privacy en toestemming bij gebruik van Adobe Campaign.

## Belangrijkste voorwaarden {#key-terms}

**Wat zijn de belangrijkste termen met betrekking tot privacy?**

De onderstaande items zijn gekoppeld aan de belangrijkste termen en concepten met betrekking tot privacy en toestemming in Adobe Campaign:

* [Regels inzake privacybeheer](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Persoonlijke gegevens en personen](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Recht op toegang en recht om te worden vergeten](../../platform/using/privacy-management.md#right-access-forgotten)
* [Toestemming, bewaring en rollen](../../platform/using/privacy-management.md#consent-retention-roles)

## Gereedheid van privacyregels {#privacy-regulations-readiness}

**Wat is het voorstel van Adobe Campaign om de meest recente privacyregels na te leven?**

Adobe geeft geen juridisch advies. U zou met uw eigen juridische adviseur moeten samenwerken om ervoor te zorgen zij alle noodzakelijke stappen in de richting van GDPR, CCPA, PDPA, LGPD of enige andere toepasselijke regelgevende bereidheid ondernemen.

**Voorbereiden op verzoeken om gegevens te openen en te verwijderen**

* Identificeer een proces om te ontvangen/op de verzoeken van het Gegevensonderwerp te antwoorden, met inbegrip van het aanwijzen van een Punt van de Privacy van Contact.

* Bekijk de verschillende klantgegevens die in Adobe Campaign zijn opgeslagen en bepaal unieke id&#39;s (er zijn waarschijnlijk meer dan één).

* Bepaal een bevestiging/authentificatiebeleid en een proces voor de identiteitsbevestiging van het Onderwerp van Gegevens.

* Zorg ervoor dat de reactie van het onderwerp van Gegevens gemakkelijk te begrijpen is.

**Goedkeuring overwegen**

* Alle aanraakpunten voor gegevensvastlegging voor GDPR (d.w.z. taal, toestemmingsmechanisme en toestemmingslogboeken) vermelden en zo nodig bijwerken.

* Zorg ervoor dat alle e-mails met marketingberichten de afmeldingskoppelingen bevatten.

* Algemene strategie voor e-mailmarketing evalueren om geospecifieke implementaties te bepalen.

**Gegevens begrijpen**

* Bekijk alle bronnen voor het importeren en vastleggen van gegevens waar gegevens naar Adobe Campaign stromen en documenteer welke velden worden gebruikt voor uw marketingactiviteiten.

* Verwijder ongebruikte gegevenskenmerken uit uw Adobe Campaign-database.

* Gebruik de gegevens die in Adobe Campaign beschikbaar zijn voor de intentie die is vastgelegd en geef uw ontvangers een betere persoonlijke ervaring.

* Rechten voor gegevenstoegang controleren en bijwerken om ervoor te zorgen dat gebruikers van Adobe Campaign volledig gebruikmaken van alleen de gegevens die nodig zijn om hun campagnes uit te voeren, maar niet van andere gegevens.

* Zorg ervoor dat elke gebruiker van Adobe Campaign over de juiste toegangsrechten beschikt om de vereiste taken uit te voeren, maar niet over andere rechten om aanvullende taken uit te voeren.

## Gebruikersbetrokkenheid behouden {#preserve-user-engagement}

**Hoe kunnen gegevenscontrollers toestemming krijgen met minimale gevolgen voor de betrokkenheid van gebruikers?**

In die gevallen waarin voor bepaalde marketingactiviteiten toestemming nodig is, moet de toestemming van de consument actief zijn (d.w.z. geen stilzwijgen als instemmings- of voorcontroledoos), ontbundeld zijn en mag deze niet afhankelijk zijn van het aanbieden van de diensten.

Er kunnen zelfs gevallen zijn waarin bepaalde toestemmingen moeten worden vernieuwd om het gebruik van gegevens te kunnen voortzetten.

In plaats van te denken aan deze strengere toestemmingsvereisten als een risico voor het verhandelbare heelal, zouden de verkopers hen als ware indicator van merkbetrokkenheid en loyaliteit, evenals klantentevredenheid en vertrouwen kunnen omarmen.

## Toestemming beheren {#manage-consent}

**Hoe kunnen gegevensverantwoordelijken hun toestemming in Adobe Campaign beheren?**

Adobe Campaign biedt al mogelijkheden om de toestemming op meer niveaus te beheren dan de meeste marketers gebruiken via aangepaste gegevensvelden of via een of meer services.

Marketers moeten hun juridische adviseur vragen hoe ze verder kunnen gaan en vervolgens gebruik maken van de reeds in Adobe Campaign ingebouwd capaciteiten.

Bijvoorbeeld, uitbreiding van het gegevensmodel in Adobe Campaign tot spoor niet alleen als mensen hebben gekozen, maar ook het tijdstempel van de opt-in, en één of ander type indicator die de precieze reikwijdte van de toestemming weerspiegelt.

## Gegevensverwijdering {#data-deletion}

**Welke gegevens kunnen de Controllers van Gegevens in Adobe Campaign in antwoord op een klantenverzoek door een Onderwerp van Gegevens schrappen?**

Alle gegevens die aan het onderwerp van Gegevens worden geassocieerd zullen worden geschrapt met inbegrip van uit-van-de-doos en douanetabellen.

Technisch gezien `integrity="own"` worden alle gegevens met betrekking tot de betrokkene verwijderd.

Als Controlemechanisme van Gegevens, hebt u de optie om dit aan te passen door de integriteit van verbindingen te veranderen die in de gegevensschema&#39;s worden bepaald (bijvoorbeeld, voor het geval u een bedrijfsrechtvaardiging hebt om bepaalde gegevens niet te schrappen).

**Hoe worden rapporten beïnvloed wanneer levering en het volgen logboeken worden geschrapt?**

Rapporten in Adobe Campaign zijn gebaseerd op indicatoren die zijn berekend op geaggregeerde gegevens uit bezorgings- en trackinglogboeken. Dientengevolge, zou het verwijderen van de individuele logboeken niet de metriek beïnvloeden die op de rapporten wordt getoond.

## Gegevens opnieuw importeren {#re-import-data}

**In Adobe Campaign wordt record vaak vanuit een externe gegevensbron geüpload. Moet ik er rekening mee houden dat gegevens op een later tijdstip opnieuw kunnen worden geïmporteerd?**

Als Controlemechanisme van Gegevens zult u moeten ervoor zorgen dat wanneer u een schrappingsverzoek ontvangt, u alle noodzakelijke gegevens over het Onderwerp van Gegevens van al uw systemen schrapt.

## Opnieuw aanmelden {#opt-in-again}

**Kan een betrokkene, wiens gegevens uit Adobe Campaign zijn gewist, later opnieuw inloggen?**

Een betrokkene kan zich opnieuw aanmelden of als nieuwe ontvanger worden toegevoegd nadat zijn gegevens uit Adobe Campaign zijn gewist.

U kunt het auditspoor gebruiken dat details toen de vorige schrapping werd uitgevoerd en wanneer de nieuwe ontvanger is gecreeerd.