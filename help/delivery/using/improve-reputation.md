---
solution: Campaign Classic
product: campaign
title: Je reputatie verbeteren bij het gebruik van Adobe Campaign Classic
description: Meer weten over het verbeteren van je reputatie bij het gebruik van Adobe Campaign Classic?
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 2%

---


# Uw reputatie verbeteren{#improve-reputation}

Verwijder dubbele e-mailadressen van uw doel om te voorkomen dat de ontvangers uitputten. Deze stap beschermt uw verzendende reputatie en verzekert goed quarantainebeheer. Adobe Campaign biedt de noodzakelijke hulpmiddelen aan om deze aanbevelingen uit te voeren en het risico te vermijden om aan de lijst van gewezen personen door ISP worden toegevoegd.

Om dubbel werk zoveel mogelijk te voorkomen, moeten de volgende acties worden uitgevoerd:

* De invoer moet zorgvuldig worden gevormd
* Let op bij het wijzigen van e-mailadressen
* Let op bij automatisch importeren
* Profielen moeten in verschillende mappen worden gesorteerd

Quarantainebeheer wordt weergegeven in [deze sectie](../../delivery/using/understanding-quarantine-management.md).

Hieronder vindt u meer informatie over duplicaat- en quarantainebeheer.

U kunt het verzonden e-mailvolume op IP adres controleren. Hiervoor is een schema-extensie nodig. U moet de uitlogingtabel uitbreiden om de &#39;public identifier&#39; toe te voegen en een workflow maken om de gegevens te extraheren en weer te geven. Neem contact op met de Adobe als u dit nodig hebt.

## Dupliceert {#duplicates}

Het hebben van dubbele e-mailadressen kan veelvoudige gevolgen hebben:

* Hetzelfde bericht wordt meerdere keren verzonden. Zelfs als Campagne standaard een deduplicatieprocedure uitvoert voordat het wordt verzonden, is er niets om te voorkomen dat hetzelfde bericht wordt verzonden door verschillende handelingen met dezelfde inhoud wanneer een doel wordt gesplitst.
* Abonnementsverzoeken worden niet geaccepteerd. Als een ontvanger zich afmeldt na het ontvangen van een bericht, zal zijn dubbel profiel nog verkiesbaar voor toekomstige berichten zijn.

Naast deze zijstap van opt-in procedures, zal deze situatie gebruikers waarschijnlijk leiden om de berichten als spam te beschouwen en een procedure van de lijst van gewezen personen bij ISP teweeg te brengen.

U moet bijzonder voorzichtig zijn wanneer het uitvoeren van verrichtingen op het gegevensbestand:

* De invoer moet zorgvuldig worden geconfigureerd, met name wanneer de verzoeningssleutel wordt gekozen.
* Gewijzigde e-mailadressen kunnen ook een bron van duplicaten zijn. Met name, kunnen twee adressen met verschillende domeinen aan de zelfde brievenbus worden verpletterd, bijvoorbeeld in het geval van een bedrijf dat naam heeft veranderd en het vroegere domein voor een bepaalde periode heeft gehandhaafd: joe.doe@amce-co.com en joe.doe@acme-rebranded.com.
* Automatische invoer, hetzij van lijsten of van andere gegevensbestanden, is elementen waarmee rekening moet worden gehouden bij het beheer van profielen. Wat gebeurt er als u een profiel verwijdert of verplaatst in een andere partitie? Het kan opnieuw worden gemaakt in de eerste partitie door een automatische importbewerking, bijvoorbeeld wanneer een inkooporder wordt geplaatst.
* Het opslaan van profielen in verschillende mappen kan worden geïmplementeerd met behulp van weergaven in plaats van partities. Op deze manier, bent u zeker dat de profielen in de zelfde fysieke verdeling terwijl nog het toelaten van de adequate rechten worden getoond en worden geleid.

Er zijn echter gevallen waarin duplicaten tussen de verschillende partities normaal zijn. Bij het verzenden van documenten voor derden of voor verschillende bedrijfsentiteiten is het bijvoorbeeld logisch dat dezelfde persoon om verschillende redenen een ontvanger is. Het is echter zelden normaal om duplicaten binnen dezelfde partitie te zoeken.

## Quarantines {#quarantines}

Adobe Campaign beheert een lijst met in quarantaine geplaatste adressen. De ontvangers de waarvan adressen quarantined zijn uitgesloten door gebrek tijdens de leveringsanalyse: zij zijn niet gericht . Een e-mailadres kan in quarantaine worden geplaatst bijvoorbeeld wanneer inbox volledig is of als het adres niet bestaat. In alle gevallen komt quarantining overeen met de specifieke regels die hieronder worden beschreven.

Quarantainebeheer wordt weergegeven in [deze sectie](../../delivery/using/understanding-quarantine-management.md).