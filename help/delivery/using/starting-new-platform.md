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
source-git-commit: a1192bc804e752d13af869da66ba0505c077ed19
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---


# Een nieuw platform starten {#starting-new-platform}

Het handhaven van uw domein en IP adresreputatie is essentieel wanneer vestiging een nieuw platform.

* Het verzenden van e-mails is een gevoelige stap omdat het platform geen geschiedenis van gebruik heeft en, wanneer de verzendende IP&#39;s nooit voor dit doel zijn gebruikt, geen reputatie.

* ISPs is natuurlijk verdacht van IP adressen die nooit zijn gebruikt om e-mail te verzenden en die plotseling beginnen grote volumes van e-mailverkeer te verzenden. Spammers gebruiken doorgaans &quot;onbekende&quot; IP-adressen (adressen die nog nooit op de zwarte lijst staan) om het grootst mogelijke aantal berichten vóór detectie te verzenden.

* Je kunt niet verwachten dat je aan het begin van de productiefase een operationele snelheid bereikt in termen van productie. Bovendien zou u niet moeten proberen om berichten aan dit tarief te verzenden aangezien het ISPs zou kunnen leiden om de verzendende adressen te blokkeren en de rest van de aanloopfase ernstig te compromitteren.

Hieronder staan de belangrijkste beginselen die moeten worden gevolgd bij het opstarten van een nieuw platform:

* Als u deze informatie hebt, **importeert u ongeldige adressen in de quarantainetabel**.
Het beginnen van een platform gebeurt vaak wanneer het gebruiken van een lijst van adressen voor het eerst en die niet volledig gekwalificeerd kunnen zijn. Als u naar ongeldige adressen of naar honingpotadressen verzendt, zal dit tot het verminderen van de reputatie van het platform bijdragen.

   * Als u een lijst van ongeldige adressen hebt, is het in uw beste belang om het in de quarantainetabel (beschikbaar door het **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** menu) in te voeren alvorens voor het eerst te verzenden.
   * Als, allen het zelfde, u wenst om de ongeldige adressen opnieuw te kwalificeren, is het verreweg verkieslijk om dit te doen zodra de reputatie van het platform en beetje door beetje wordt gevestigd om het gebruik van slechte adressen in tijd &quot;te &quot;verwateren&quot;.
   Voor meer op dit, zie het [Optimaliseren van uw levering door quarantines](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines).
* **Beperk de productiesnelheid** door het aantal tapes te beperken. Neem voor meer informatie over het aanpassen van deze technische instelling contact op met de beheerder van de Adobe-campagne.
* **De verzonden** volumes progressief verhogen om te voorkomen dat ze als spam worden gemarkeerd. Wijs niet de hele database vanaf het begin aan, maar voeg een extra fractie van de lijst toe telkens als u de gegevens verzendt. Dit zou u moeten toelaten om het volume bij elke stap te verhogen terwijl het verminderen van het algemene tarief van ongeldige adressen. U kunt golven gebruiken om een vloeiende ontwikkeling van de opstartfase te garanderen. Zie [Verzenden met meerdere golven](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)voor meer informatie.
* **Verzend regelmatig**. In zekere zin is het beter om regelmatig kleine opnamen te sturen in plaats van sporadisch grote campagnes.
* **Let goed op de leveringsrapporten**. De hoge foutenindicatoren kunnen betekenen een technisch plaatsen slecht gevormd is. Zie [Levering](../../delivery/using/monitoring-a-delivery.md)controleren voor meer informatie.

**Verwante onderwerpen**:
* [Verhoog uw e-mailreputatie met opwarming van IP](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [Alles over spamovervullingen](https://helpx.adobe.com/campaign/kb/spam-traps.html)