---
product: campaign
title: Problemen met verzenden van levering
description: Meer informatie over leveringsprestaties en hoe u problemen met betrekking tot leveringsbewaking kunt oplossen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 1%

---

# Problemen met verzenden van levering {#delivery-troubleshooting}

Deze sectie maakt een lijst van gemeenschappelijke kwesties u kunt ontmoeten wanneer het verzenden van leveringen, en hoe te om hen problemen op te lossen.

Bovendien, zorg ervoor u de beste praktijken en controlelijst volgt die in [ wordt gedetailleerd deze pagina ](delivery-performances.md) om uw leveringen te verzekeren presteren goed.

**Verwante onderwerpen:**

* [Leveringsstatussen](delivery-statuses.md)
* [Leveringsdashboard](delivery-dashboard.md)
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)

## Trage leveringen {#slow-deliveries}

Nadat u op de knop **[!UICONTROL Send]** hebt geklikt, lijkt het alsof de levering langer duurt dan normaal. Dit kan worden veroorzaakt door verschillende elementen:

* Sommige e-mailproviders hebben mogelijk uw IP-adressen aan een lijst van gewezen personen toegevoegd. In dit geval, controleer uw uitzendingen en raadpleeg [ deze sectie ](about-deliverability.md).

* Uw levering is mogelijk te groot om snel te worden verwerkt, dit kan gebeuren met een hoge JavaScript-personalisatie of als uw levering meer dan 60 kB weegt. Verwijs naar Adobe Campaign v8 [ beste praktijken van de Levering ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html){target="_blank"}.  voor meer informatie over richtlijnen voor inhoud.

* Throttling zou binnen Adobe Campaign MTA kunnen voorgekomen zijn. Dit wordt veroorzaakt door:

   * Berichten gebeëindigd (**[!UICONTROL quotas met]** bericht): de quota die door de verklarende MX regels worden verklaard die in Campagne worden bepaald zijn voldaan. Voor meer informatie over dit bericht, verwijs naar [ deze pagina ](deliverability-faq.md). Meer over MX regels leren, verwijs naar [ deze sectie ](../../installation/using/email-deliverability.md#about-mx-rules).

   * Berichten gepended (**[!UICONTROL dynamic flow control]** bericht): De campagne MTA heeft fouten ontmoet wanneer het proberen om berichten voor bepaalde ISP te leveren die een vertraging veroorzaakt om te groot van een foutendichtheid te vermijden en zo het onder ogen zien van potentiële lijst van gewezen personen.

* Een systeemprobleem kan ervoor zorgen dat servers niet met elkaar kunnen communiceren: dit kan het hele verzendproces vertragen. Controleer de servers om ervoor te zorgen dat er geen geheugen of middelkwesties zijn die Campagne in het proces kunnen beïnvloeden om de verpersoonlijkingsgegevens bijvoorbeeld te krijgen.

## Geplande leveringen {#scheduled-deliveries-}

Als de leveringen niet op nauwkeurige geplande datum uitvoeren, kan het met een verschil tussen de tijdzone van servers verwant zijn. De instantie voor midsourcing en de productie-instantie kunnen zich in verschillende tijdzones bevinden.

Als voorbeeld, als de mid-sourcing instantie in de tijdzone van Brisbane is en de productieinstantie in Darwin tijdzone is, zijn beide tijdstreken een half uur van elkaar gescheiden, dan in het controlelogboek zou u duidelijk zien dat als de levering voor productie bij 11 :56 gepland is, de zelfde levering gepland voor midden bij 12 :26 zou zijn die een verschil van een half uur heeft.

## Mislukte status {#failed-status}

Als de status van een e-maillevering **[!UICONTROL Failed]** is, kan deze worden gekoppeld aan een uitgave met verpersoonlijkingsblokken. De blokken van de verpersoonlijking in een levering kunnen fouten produceren wanneer de schema&#39;s niet de leveringsafbeelding aanpassen, bijvoorbeeld.

Leveringslogboeken zijn essentieel om te leren waarom een levering is mislukt. Hier zijn mogelijke fouten die u van leveringslogboeken kunt ontdekken:

* Ontvangersberichten ontbreken met een &quot;Onbereikbare&quot;fout die verklaart:

  ```
  Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
  ```

  De oorzaak van deze kwestie is bijna altijd een verpersoonlijking binnen HTML die op een lijst of een gebied probeert te roepen dat niet is bepaald of in kaart gebracht in het stroomopwaartse richten of in de het doelafbeelding van de levering.

  Om dit te verbeteren, moeten de werkschema en leveringsinhoud worden herzien om specifiek te bepalen welke verpersoonlijking probeert om de lijst in kwestie te roepen en of de lijst of niet kan worden in kaart gebracht. Van daar, of het verwijderen van de vraag aan deze lijst in HTML of het bevestigen van de afbeelding aan de levering zou de weg aan resolutie zijn.

* In het midsourcingimplementatiemodel kan het volgende bericht worden weergegeven in de leveringslogboeken:

  ```
  Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
  ```

  De oorzaak hangt samen met prestatieproblemen. Het betekent dat de marketinginstantie te veel tijd besteedt aan het samenstellen van gegevens voordat ze deze naar de server voor midsourcing verzenden.

  Om dit op te lossen, adviseren wij een vacuüm en een herdex op het gegevensbestand uit te voeren. Voor meer informatie over gegevensbestandonderhoud, verwijs naar [ deze sectie ](../../production/using/recommendations.md).

  U moet ook alle werkstromen met een geplande activiteit opnieuw beginnen, en alle werkschema&#39;s in ontbroken status. Verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/scheduler.html){target="_blank"}.

* Wanneer een levering mislukt, kan de volgende fout in de leveringslogboeken verschijnen:

  ```
  DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
  ```

  Gewoonlijk betekent deze fout dat er een verpersoonlijkingsgebied of een blok binnen e-mail is dat meer dan één waarden voor de ontvanger heeft. Er wordt een verpersoonlijkingsblok gebruikt en het haalt meer dan één record op voor een bepaalde ontvanger.

  Om dit op te lossen, controleer de gebruikte verpersoonlijkingsgegevens, en controleer dan het doel voor ontvangers die meer dan één ingang voor om het even welk van die gebieden hebben. U kunt ook een **[!UICONTROL Deduplication]** -activiteit gebruiken in de doelworkflow voordat u de levering uitvoert om te controleren of er slechts één verpersoonlijkingsveld tegelijk is. Voor meer informatie over deduplicatie, verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/deduplication.html){target="_blank"}.

* Sommige levering kan mislukken met een &quot;Onbereikbare&quot;fout die verklaart:

  ```
  Inbound email bounce (rule 'Auto_replies' has matched this bounce).
  ```

  Dit betekent dat de levering is geslaagd, maar Adobe Campaign heeft een automatisch antwoord van de ontvanger ontvangen (bijvoorbeeld een antwoord &quot;Buiten-kantoor&quot;) dat overeenkwam met de regels voor inkomende e-mail &quot;Auto_responses&quot;.

  Het e-mailbericht met het automatische antwoord wordt genegeerd door Adobe Campaign en het adres van de ontvanger wordt niet verzonden naar quarantines.
