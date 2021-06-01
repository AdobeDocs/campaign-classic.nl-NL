---
product: campaign
title: Gebeurtenisverwerking
description: Leer hoe de transactieberichten worden verwerkt in Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: b46a483594f210c4530a934194c6d2b73deaeaf9
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 2%

---

# Gebeurtenisverwerking {#about-event-processing}

In de context van het transactieoverseinen, wordt een gebeurtenis geproduceerd door een extern informatiesysteem en verzonden naar Adobe Campaign via de **[!UICONTROL PushEvent]** en **[!UICONTROL PushEvents]** methodes (zie [Gebeurtenisbeschrijving](../../message-center/using/event-description.md)).

Deze gebeurtenis bevat gegevens die aan de gebeurtenis zijn gekoppeld, zoals het [type](../../message-center/using/creating-event-types.md) (bevestiging van de bestelling, aanmaak van account op een website, enz.), e-mailadres of mobiel nummer, en andere informatie waarmee u het transactiebericht vóór de levering kunt verrijken en personaliseren (contactgegevens van de klant, taal van het bericht, e-mailindeling, enz.).

Voorbeeld van gebeurtenisgegevens:

![](assets/messagecenter_events_request_001.png)

## Stappen voor gebeurtenisverwerking {#event-processing}

Om transactionele berichtengebeurtenissen te verwerken, worden de volgende stappen toegepast op de uitvoeringsinstantie(s):

1. [Gebeurtenisverzameling](#event-collection)
1. [Gebeurtenisoverdracht naar een berichtsjabloon](#routing-towards-a-template)
1. Gebeurtenisverrijking met personalisatiegegevens
1. [Uitvoering van levering](../../message-center/using/delivery-execution.md)
1. [Recycling van ](#event-recycling) gebeurtenissen waarvan de gekoppelde levering is mislukt (via een Adobe Campaign-workflow)

Zodra alle stappen hierboven door de uitvoeringsinstantie worden uitgevoerd, ontvangt elke gerichte ontvanger een gepersonaliseerd bericht.

>[!NOTE]
>
>Voor meer op de instanties van het transactionele overseinen, zie [Transactionele overseinenarchitectuur](../../message-center/using/transactional-messaging-architecture.md).


## Gebeurtenisverzameling {#event-collection}

Gebeurtenissen die door het informatiesysteem worden gegenereerd, kunnen in twee modi worden verzameld:

* Met aanroepen van SOAP-methoden kunt u gebeurtenissen in Adobe Campaign duwen: Met de methode PushEvent kunt u één gebeurtenis tegelijk verzenden. Met de methode PushEvents kunt u meerdere gebeurtenissen tegelijk verzenden. Zie [Gebeurtenisbeschrijving](../../message-center/using/event-description.md) voor meer informatie.

* Door een workflow te maken kunt u gebeurtenissen herstellen door bestanden of via een SQL-gateway te importeren (met de optie [Federated Data Access](../../installation/using/about-fda.md)).

Zodra zij worden verzameld, worden de gebeurtenissen verdeeld door technische werkschema&#39;s tussen echt - tijd en partijrijen van de uitvoeringsinstantie(s), terwijl het wachten om aan een berichtmalplaatje worden verbonden.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Bij de uitvoeringsinstanties moeten de mappen **[!UICONTROL Real time events]** of **[!UICONTROL Batch events]** niet worden ingesteld als weergaven, omdat dit tot problemen met toegangsrechten kan leiden. Raadpleeg [deze sectie](../../platform/using/access-management-folders.md) voor meer informatie over het instellen van een map als weergave.

## Routering naar een sjabloon {#routing-towards-a-template}

Nadat de berichtsjabloon op de uitvoeringsinstantie(s) is gepubliceerd, worden automatisch twee sjablonen gegenereerd: Een gebeurtenis die moet worden gekoppeld aan een realtime-gebeurtenis en een gebeurtenis die moet worden gekoppeld aan een batchgebeurtenis.

De verpletterende stap bestaat uit het verbinden van een gebeurtenis aan het aangewezen berichtmalplaatje, dat op wordt gebaseerd:

* Het gebeurtenistype dat is opgegeven in de eigenschappen van de gebeurtenis zelf:

   ![](assets/messagecenter_event_type_001.png)

* Het gebeurtenistype dat in de eigenschappen van het berichtmalplaatje wordt gespecificeerd:

   ![](assets/messagecenter_event_type_002.png)

Door gebrek, baseert het verpletteren zich op de volgende informatie:

* Het gebeurtenistype
* Het kanaal dat moet worden gebruikt (standaard: e-mail)
* De meest recente leveringstemplate, gebaseerd op de publicatiedatum

## Status van gebeurtenis {#event-statuses}

Met **Gebeurtenisgeschiedenis** onder **[!UICONTROL Message Center]** > **[!UICONTROL Event history]** worden alle verwerkte gebeurtenissen in één weergave gegroepeerd. Ze kunnen worden gecategoriseerd op gebeurtenistype of op **status**. Deze statussen zijn:

* **In behandeling**: De gebeurtenis kan zijn:

   * Een gebeurtenis die zojuist is verzameld en nog niet is verwerkt. In de kolom **[!UICONTROL Number of errors]** wordt de waarde 0 weergegeven. De e-mailsjabloon is nog niet gekoppeld.
   * Een gebeurtenis die is verwerkt, maar waarvan de bevestiging onjuist is. In de kolom **[!UICONTROL Number of errors]** wordt een waarde weergegeven die niet 0 is. Als u wilt weten wanneer deze gebeurtenis opnieuw wordt verwerkt, raadpleegt u de kolom **[!UICONTROL Process requested on]**.

* **In afwachting van levering**: De gebeurtenis is verwerkt en de leveringssjabloon is gekoppeld. De e-mail is in afwachting van levering en het klassieke leveringsproces wordt toegepast. Voor meer informatie, kunt u [levering](../../delivery/using/about-message-tracking.md) openen.
* **Verzonden**,  **** genegeerd en  **leveringsfout**: Deze leveringsstatussen worden hersteld via de  **** updateEventsStatus-workflow. Voor meer informatie kunt u de relevante levering openen.
* **Gebeurtenis niet behandeld**: Het transactionele overseinen die fase verplettert ontbrak. Adobe Campaign heeft bijvoorbeeld het e-mailbericht dat als sjabloon voor de gebeurtenis fungeert, niet gevonden.
* **Gebeurtenis verlopen**: Het maximumaantal verzendpogingen is bereikt. De gebeurtenis wordt als null beschouwd.

## Recycling van gebeurtenissen {#event-recycling}

Als de levering van een bericht op een specifiek kanaal mislukt, kan Adobe Campaign het bericht opnieuw verzenden via een ander kanaal. Als een levering op het SMS-kanaal bijvoorbeeld mislukt, wordt het bericht opnieuw verzonden via het e-mailkanaal.

Hiervoor moet u een workflow configureren die alle gebeurtenissen opnieuw maakt met de status **Delivery error** en er een ander kanaal aan toewijst.

>[!CAUTION]
>
>Deze stap kan alleen worden uitgevoerd met behulp van een workflow en is daarom voorbehouden aan professionele gebruikers. Neem voor meer informatie contact op met de manager van uw Adobe-account.