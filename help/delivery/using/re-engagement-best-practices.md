---
title: Implementatie
seo-title: Implementatie
description: Implementatie
seo-description: null
page-status-flag: never-activated
uuid: 883bad1c-c35b-4c48-9dca-c0cb947facb6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 853f26ad-d373-49a5-952e-4197ffc3d904
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 30f313cecf1c3d7c65f6524a3f86a1c28b35f679

---


# Leverbaarheid verbeteren door opnieuw aan te melden{#re-engagement}

Bij het implementeren van de leverbaarheid bestaat een aantal van de beste praktijken uit het proberen om een gezonde abonneebasis te behouden en de leveringsbaarheid te verbeteren via strategieën voor herbetrokkenheid.

* Het handhaven van een gezonde abonneebasis is één van de belangrijkste aspecten om goede en verenigbare levering te verzekeren. Veel problemen met betrekking tot de leverbaarheid zijn het gevolg van slechte gegevenspraktijken en slecht onderhoud.
* Een van de meest voorkomende problemen waarmee marketeers vandaag worden geconfronteerd, is inactieve abonneeactiviteiten (ook wel lage of niet-actieve abonnementen genoemd) die een negatief effect kunnen hebben op de levering van e-mail en een laag investeringsrendement.

>[!NOTE]
>
>Neem voor meer informatie over campagnestrategieën voor herbetrokkenheid en de leveringsservices van Adobe contact op met uw Deliverability consultant of neem contact op met uw Adobe-verkoopagent.

## Hoe bekijkt ISPs niet-betrokkenheidsactiviteit? {#how-do-isps-view-non-engagement-activity-}

Jarenlang, hebben ISPs overeenkomst terugkoppelt metriek van hun gebruikers gebruikt om te beslissen waar te om berichten te plaatsen, of of zij hen bij allen zouden moeten leveren. De betrokkenheid van de gebruiker bestaat uit zowel positieve als negatieve terugkoppelen en ISPs controleren beide op een constante basis. Geen betrokkenheid hebben is misschien een van de belangrijkste bijdragers van negatieve betrokkenheid. Vanuit een leverbaarheidsperspectief, kan het constant verzenden van campagnes naar gebruikers die geen overeenkomst tonen de algemene reputatie van uw IP adres en domeinen ook verminderen.

ISP&#39;s zoals AOL, Gmail, Microsoft en Yahoo! niet-betrokkenheid weergeven als ongewenste e-mail en berichten omleiden naar de spammap. Bovendien zijn deze abonnees mogelijk niet langer eigenaar van het e-mailaccount en kan dit worden gebruikt als een &#39;gerecycleerde&#39; spamval. Dit betekent dat het adres een tijdje ongeldig was en alle berichten worden verworpen. Als uw systeem van het abonneebeheer geen &quot;hard gefactureerde&quot;adressen verwijdert, is het zeer waarschijnlijk het posten van spamvallen die tot significante leveringskwesties leiden.

## Hoe moet u inactiviteit aanpakken? {#how-should-you-approach-inactivity-}

Gelukkig kunnen klanten die het Adobe Campagne-platform gebruiken inactiviteit binnen hun exemplaar bekijken door open te bekijken en gegevens volgens het segment te klikken. Aangezien niet-betrokkenheid levering kan belemmeren, kan de eerste gedachte zijn om abonnees uit het gegevensbestand enkel te verwijderen. In sommige gevallen kan dit echter een verkeerde optie blijken. Daarom is een strategie van hernieuwde betrokkenheid (ook wel een win-backstrategie genoemd) de beste aanbeveling om de abonnees te behouden die in het ontvangen van post geïnteresseerd zijn, en geleidelijk degenen te elimineren die geen activiteit meer tonen.

## Werken herbetrokkenheidscampagnes echt? {#do-re-engagement-campaigns-really-work-}

Volgens een studie over het retourpad werden er herplaatsingscampagnes uitgevoerd met een resultaat van 12% open rente in vergelijking met een gemiddelde van 14% voor normale campagnes. Hoewel slechts 24% van de abonnees de campagne voor een nieuwe betrokkenheid had gelezen, leest ongeveer 45% van hen de daaropvolgende berichten.

![](assets/deliverability_implementation_1.png)

## Hoe maak je een campagne voor een nieuwe betrokkenheid? {#how-do-you-create-a-re-engagement-campaign-}

### Fase 1 {#phase-1}

* De eerste stap is abonnees te identificeren die zeer weinig aan geen open of klikactiviteit hebben, en dienovereenkomstig deze groep te segmenteren die op een vastgestelde tijdkader wordt gebaseerd. De duimregel is om abonnees te bekijken die geen e-mail binnen de afgelopen 90 dagen hebben geopend of geklikt. Dit varieert echter afhankelijk van de aard van de activiteit (bijvoorbeeld seizoensgebonden verzending).
* Een ander punt om in mening te houden terwijl het bepalen van termijnen is dat ISPs en zwarte lijst bedrijven vinden om betrokkenheid overal tussen 1.5 en 1.8 jaar te zijn. Daarnaast worden gedragsactiviteiten zoals aankopen en website-activiteit, of andere aanraakpunten, zoals voorkeuren tijdens de aanmeldfase of het eerste contactpunt, uitgevoerd.

### Fase 1 {#phase-2}

* Zodra een segment wordt bepaald, is de volgende stap een re-betrokkenheidscampagne te creëren die aan de abonnee volgens de metriek behandelt die zijn geïdentificeerd. Het creëren van een onderwerpregel zal helpen de rente van de abonnee verhogen. Volgens een onderzoek van de Weg van de Terugkeer, produceren de onderwerplijnen en de inhoud die &quot;Wij missen u&quot;hogere reactiesnelheden dan &quot;wij willen u terug&quot;.
* Een prikkel kan ook worden aangeboden om met e-mail opnieuw in dienst te nemen. Wanneer u aanbiedingen met kortingen overweegt, kunt u het beste dollarbedragen versus percentages gebruiken. Het Weg van de terugkeer stelt ook voor dit te doen aangezien het hogere reactiesnelheden zal veroorzaken. Ten slotte is het ook nuttig om splitstests uit te voeren om de respons en succespercentages te beoordelen.

### Fase 3 {#phase-3}

De volgende stap bestaat uit het bepalen van de frequentie van de campagne voor het opnieuw toewijzen van taken. In tegenstelling tot herbevestigingsberichten, zijn de herbetrokkenheidscampagnes bedoeld om de abonnee met een reeks e-mails in de loop der tijd terug te winnen. In het volgende voorbeeld ziet u een voorbeeld van de frequentie.

![](assets/deliverability_implementation_2.png)

Abonnees die zich met de campagne bezighouden door de open- of klikactiviteiten te volgen, worden weer toegevoegd aan de betreffende lijst met abonnees.

### Fase 4 {#phase-4}

* De volgende fase is om abonnees te identificeren die voortdurend geen activiteit tonen en geleidelijk het verzenden van e-mails naar hen over een periode te verminderen. Als er het afgelopen jaar geen activiteit is, is het goed om het e-mailabonnement van de abonnees in de wacht te zetten. Hoewel ze geen interesse hebben getoond in de e-mailinhoud, is het altijd de laatste kans om hun abonnement opnieuw te activeren door een eenmalige herbevestigingscampagne te verzenden.
* Herbevestigingscampagnes zijn een goede manier om abonnees die lange tijd inactief zijn te vragen of zij op de abonnementenlijst willen blijven. Wanneer u de campagne maakt, is het raadzaam een koppeling &quot;Klik hier&quot; toe te voegen, zodat zij de actie kunnen bevestigen en hun adres kunnen verifiëren. Op deze manier kan de handeling in de database worden opgenomen. Hieronder ziet u een voorbeeld van een e-mailbericht voor bevestiging:

   ![](assets/deliverability_implementation_3.png)

   Zodra de abonnee een actie heeft ondernomen, kan een landingspagina met de bevestiging van hun herabonnement worden aangeboden. Hieronder ziet u een voorbeeld van de landingspagina:

   ![](assets/deliverability_implementation_4.png)
