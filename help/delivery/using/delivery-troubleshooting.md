---
solution: Campaign Classic
product: campaign
title: Problemen oplossen
description: Leer meer over leveringsprestaties en hoe te om kwesties met betrekking tot levering controle problemen op te lossen.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: f3ba836bbb5a5f82d6a7868dcb15edc8e61b9a5b
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 1%

---


# Bezig met verzenden van probleemoplossing {#delivery-troubleshooting}

Deze sectie maakt een lijst van gemeenschappelijke kwesties u kunt ontmoeten wanneer het verzenden van leveringen, en hoe te om hen problemen op te lossen.

Bovendien, zorg ervoor u de beste praktijken en controlelijst volgt die in [deze pagina](../../delivery/using/delivery-performances.md) wordt gedetailleerd om uw leveringen te verzekeren goed presteren.

**Verwante onderwerpen:**

* [Leveringsstatus](../../delivery/using/delivery-statuses.md)
* [Delivery dashboard](../../delivery/using/delivery-dashboard.md)
* [Leveringsfouten begrijpen](../../delivery/using/understanding-delivery-failures.md)

## Trage leveringen {#slow-deliveries}

Nadat u op de knop **[!UICONTROL Send]** hebt geklikt, lijkt het langer te duren voordat de levering is uitgevoerd. Dit kan worden veroorzaakt door verschillende elementen:

* Sommige e-mailproviders hebben mogelijk uw IP-adressen aan een lijst van afgewezen personen toegevoegd. In dit geval, controleer uw uitzendingen en raadpleeg [deze sectie](../../delivery/using/about-deliverability.md).

* Uw levering is mogelijk te groot om snel te worden verwerkt, dit kan gebeuren met een hoge mate van personalisatie in JavaScript of als uw levering meer dan 60 kbytes weegt. Raadpleeg de Adobe Campaign [Best practices voor levering](../../delivery/using/delivery-best-practices.md) voor meer informatie over richtlijnen voor inhoud.

* Throttling zou binnen Adobe Campaign MTA kunnen voorgekomen zijn. Dit wordt veroorzaakt door:

   * Gebeëindigde berichten (**[!UICONTROL quotas met]** bericht): er is voldaan aan de quota die zijn aangegeven in de declaratieve MX-regels die in de campagne zijn vastgesteld. Raadpleeg [deze pagina](../../delivery/using/deliverability-faq.md) voor meer informatie over dit bericht. Meer over MX regels leren, verwijs naar [deze pagina](../../delivery/using/technical-recommendations.md#mx-rules).

   * Gebeëindigde berichten (**[!UICONTROL dynamic flow control]** bericht): Campagne MTA heeft fouten ontmoet wanneer het proberen om berichten voor bepaalde ISP te leveren die een vertraging veroorzaakt om te grote van een foutendichtheid te vermijden en zo potentiële lijst van afgewezen personen onder ogen te zien.

* Door een systeemprobleem kunnen servers niet met elkaar communiceren: dit kan het hele verzendingsproces vertragen . Controleer de servers om ervoor te zorgen dat er geen geheugen of middelkwesties zijn die Campagne in het proces kunnen beïnvloeden om de verpersoonlijkingsgegevens bijvoorbeeld te krijgen.

## Geplande leveringen {#scheduled-deliveries-}

Als de leveringen niet op nauwkeurige geplande datum uitvoeren, kan het met een verschil tussen de tijdzone van servers verwant zijn. De instantie voor midsourcing en de productie-instantie kunnen zich in verschillende tijdzones bevinden.

Als de instantie van de midsourcing zich bijvoorbeeld in de tijdzone van Brisbane bevindt en de productie-instantie zich in de tijdzone van Darwin bevindt, zijn beide tijdzones een half uur van elkaar verwijderd, dan zou u in het auditlogboek duidelijk zien dat als de levering gepland is voor productie om 11:56, de zelfde levering gepland voor midden om 12:26 zou zijn die een verschil van een half uur heeft.

## Status {#failed-status} is mislukt

Als de status van een e-maillevering **[!UICONTROL Failed]** is, kan het met een kwestie met verpersoonlijkingsblokken worden verbonden. De blokken van de verpersoonlijking in een levering kunnen fouten produceren wanneer de schema&#39;s niet de leveringsafbeelding aanpassen, bijvoorbeeld.

De logboeken van de levering zijn zeer belangrijk om te leren waarom een levering ontbrak. Hier zijn mogelijke fouten die u van leveringslogboeken kunt ontdekken:

* Ontvangersberichten ontbreken met een &quot;Onbereikbare&quot;fout die verklaart:

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   De oorzaak van deze kwestie is bijna altijd een verpersoonlijking binnen HTML die op een lijst of een gebied probeert te roepen dat niet is bepaald of in het stroomopwaartse richten of in de het doelafbeelding van de levering in kaart gebracht.

   Om dit te verbeteren, moeten de werkschema en leveringsinhoud worden herzien om specifiek te bepalen welke verpersoonlijking probeert om de lijst in kwestie te roepen en of de lijst of niet kan worden in kaart gebracht. Van daar, of het verwijderen van de vraag aan deze lijst in HTML of het bevestigen van de afbeelding aan de levering zou de weg aan resolutie zijn.

* In het midsourcingimplementatiemodel kan het volgende bericht worden weergegeven in de leveringslogboeken:

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   De oorzaak hangt samen met prestatieproblemen. Het betekent dat de marketinginstantie te veel tijd besteedt aan het samenstellen van gegevens voordat ze deze naar de server voor midsourcing verzenden.

   Om dit op te lossen, adviseren wij een vacuüm en een herdex op het gegevensbestand uit te voeren. Raadpleeg [deze sectie](../../production/using/recommendations.md) voor meer informatie over databaseonderhoud.

   U moet ook alle werkstromen met een geplande activiteit opnieuw beginnen, en alle werkschema&#39;s in ontbroken status. Zie [deze sectie](../../workflow/using/scheduler.md).

* Wanneer een levering mislukt, kan de volgende fout in de leveringslogboeken verschijnen:

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   Gewoonlijk betekent deze fout dat er een verpersoonlijkingsgebied of een blok binnen e-mail is dat meer dan één waarden voor de ontvanger heeft. Er wordt een verpersoonlijkingsblok gebruikt en het haalt meer dan één record op voor een bepaalde ontvanger.

   Om dit op te lossen, controleer de gebruikte verpersoonlijkingsgegevens, en controleer dan het doel voor ontvangers die meer dan één ingang voor om het even welk van die gebieden hebben. U kunt een **[!UICONTROL Deduplication]** activiteit in het richten werkschema vóór de leveringsactiviteit ook gebruiken om te controleren er slechts één verpersoonlijkingsgebied tegelijkertijd is. Raadpleeg [deze pagina](../../workflow/using/deduplication.md) voor meer informatie over deduplicatie.

* Sommige levering kan mislukken met een &quot;Onbereikbare&quot;fout die verklaart:

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   Dit betekent dat de levering is geslaagd, maar Adobe Campaign heeft een automatisch antwoord van de ontvanger ontvangen (bijvoorbeeld een antwoord &quot;Buiten-kantoor&quot;) dat overeenkwam met de regels voor inkomende e-mail &quot;Auto_responses&quot;.

   Het e-mailbericht met het automatische antwoord wordt genegeerd door Adobe Campaign en het adres van de ontvanger wordt niet verzonden naar quarantines.
