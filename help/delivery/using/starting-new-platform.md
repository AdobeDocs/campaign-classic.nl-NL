---
title: Een nieuw platform starten met Adobe Campagne Classic
description: Leer meer over het beheren van de leverbaarheid wanneer u een nieuw platform start met Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Een nieuw platform starten {#starting-new-platform}

Het handhaven van uw domein en IP adresreputatie is essentieel. Hieronder vindt u een advies voor het instellen van een nieuw platform.

Het beginnen om e-mails op een nieuw platform te verzenden is een gevoelige stap omdat het platform geen geschiedenis van gebruik en geen reputatie heeft (wanneer de verzendende IPs nooit voor dit doel zijn gebruikt). ISPs is natuurlijk verdacht van IP adressen die nooit zijn gebruikt om e-mail te verzenden en die plotseling beginnen grote volumes van e-mailverkeer te verzenden. In feite, gebruiken spammers over het algemeen &quot;onbekende&quot;IP adressen (d.w.z. adressen die nooit op de zwarte lijst zijn gezet) om het grootste mogelijke aantal berichten vóór opsporing te verzenden.

Je kunt niet verwachten dat je aan het begin van de productiefase een operationele snelheid bereikt in termen van productie. Bovendien zou u niet moeten proberen om berichten aan dit tarief te verzenden aangezien het ISPs zou kunnen leiden om de verzendende adressen te blokkeren en de rest van de aanloopfase ernstig te compromitteren.

Het beginnen van een platform gebeurt vaak wanneer het gebruiken van een lijst van adressen voor het eerst en die niet volledig gekwalificeerd kunnen zijn. Als u naar ongeldige adressen verzendt of naar honeypot-adressen, zal dit bijdragen aan het verminderen van de reputatie van het platform. Als u een lijst van ongeldige adressen hebt, is het in uw beste belang om het in de quarantainetabel (**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**) in te voeren alvorens voor het eerst te verzenden. Als, allen het zelfde, u wenst om de ongeldige adressen opnieuw te kwalificeren, is het verreweg verkieslijk om dit te doen zodra de reputatie van het platform en beetje door beetje wordt gevestigd om het gebruik van slechte adressen in tijd &quot;te &quot;verwateren&quot;.

Een overzicht geven van de beginselen die bij het opstarten moeten worden gevolgd:

* Ongeldige adressen importeren in de quarantainetabel (als u deze informatie hebt)
* De doorvoersnelheid beperken (technische instelling: beperking van het aantal tapijten)
* De verzonden volumes geleidelijk verhogen: Wijs niet de volledige database vanaf het allereerste begin aan, maar voeg een extra fractie van de lijst toe telkens wanneer u verzendt; dit zou u moeten toelaten om het volume bij elke stap te verhogen terwijl het verminderen van het algemene tarief van ongeldige adressen
* Regelmatig verzenden: Tot op zekere hoogte is het beter regelmatig kleine opnamen te sturen dan sporadisch grote campagnes
* Nauwe aandacht besteden aan de leveringsrapporten: hoge foutenindicatoren kunnen betekenen een technische instelling slecht gevormd is.