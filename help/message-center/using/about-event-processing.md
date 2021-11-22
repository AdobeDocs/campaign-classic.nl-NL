---
product: campaign
title: Gebeurtenisverwerking
description: Leer hoe de transactieberichten worden verwerkt in Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 2%

---

# Gebeurtenisverwerking {#about-event-processing}

![](../../assets/v7-only.svg)

In de context van transactiemeldingen wordt een gebeurtenis gegenereerd door een extern informatiesysteem en wordt deze via het **[!UICONTROL PushEvent]** en **[!UICONTROL PushEvents]** methoden (zie [Beschrijving van gebeurtenis](../../message-center/using/event-description.md)).

Deze gebeurtenis bevat gegevens die zijn gekoppeld aan de gebeurtenis, zoals [type](../../message-center/using/creating-event-types.md) (bevestiging van bestelling, het aanmaken van account op een website, enz.), e-mailadres of mobiel nummer, evenals andere informatie waarmee u het transactiemelding kunt verrijken en personaliseren vóór levering (contactgegevens van klant, taal van het bericht, e-mailindeling, enz.).

Voorbeeld van gebeurtenisgegevens:

![](assets/messagecenter_events_request_001.png)

## Stappen voor gebeurtenisverwerking {#event-processing}

Om transactionele berichtengebeurtenissen te verwerken, worden de volgende stappen toegepast op de uitvoeringsinstantie(s):

1. [Gebeurtenisverzameling](#event-collection)
1. [Gebeurtenisoverdracht naar een berichtsjabloon](#routing-towards-a-template)
1. Gebeurtenisverrijking met personalisatiegegevens
1. [Uitvoering van levering](../../message-center/using/delivery-execution.md)
1. [Recycling van gebeurtenissen](#event-recycling) waarvan de gekoppelde levering is mislukt (via een Adobe Campaign-workflow)

Zodra alle stappen hierboven door de uitvoeringsinstantie worden uitgevoerd, ontvangt elke gerichte ontvanger een gepersonaliseerd bericht.

>[!NOTE]
>
>Voor meer op de instanties van het transactionele overseinen, zie [Transactionele berichtenarchitectuur](../../message-center/using/transactional-messaging-architecture.md).


## Gebeurtenisverzameling {#event-collection}

Gebeurtenissen die door het informatiesysteem worden gegenereerd, kunnen in twee modi worden verzameld:

* Met aanroepen van SOAP-methoden kunt u gebeurtenissen in Adobe Campaign duwen: Met de methode PushEvent kunt u één gebeurtenis tegelijk verzenden. Met de methode PushEvents kunt u meerdere gebeurtenissen tegelijk verzenden. Zie voor meer informatie [Beschrijving van gebeurtenis](../../message-center/using/event-description.md).

* Als u een workflow maakt, kunt u gebeurtenissen herstellen door bestanden of via een SQL-gateway te importeren [Federale gegevenstoegang](../../installation/using/about-fda.md) ).

Zodra zij worden verzameld, worden de gebeurtenissen verdeeld door technische werkschema&#39;s tussen echt - tijd en partijrijen van de uitvoeringsinstantie(s), terwijl het wachten om aan een berichtmalplaatje worden verbonden.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>In de uitvoeringsinstanties worden de **[!UICONTROL Real time events]** of **[!UICONTROL Batch events]** mappen mogen niet worden ingesteld als weergaven, omdat dit tot problemen met toegangsrechten kan leiden. Raadpleeg voor meer informatie over het instellen van een map als weergave [deze sectie](../../platform/using/access-management-folders.md).

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

## Gebeurtenisstatussen {#event-statuses}

De **Gebeurtenisgeschiedenis**, onder **[!UICONTROL Message Center]** > **[!UICONTROL Event history]** Hiermee groepeert u alle verwerkte gebeurtenissen in één weergave. Ze kunnen worden gecategoriseerd op gebeurtenistype of op **status**. Deze statussen zijn:

* **In behandeling**: De gebeurtenis kan zijn:

   * Een gebeurtenis die zojuist is verzameld en nog niet is verwerkt. De **[!UICONTROL Number of errors]** geeft de waarde 0 aan in de kolom. De e-mailsjabloon is nog niet gekoppeld.
   * Een gebeurtenis die is verwerkt, maar waarvan de bevestiging onjuist is. De **[!UICONTROL Number of errors]** in de kolom wordt een waarde weergegeven die niet 0 is. Als u wilt weten wanneer deze gebeurtenis opnieuw wordt verwerkt, raadpleegt u de **[!UICONTROL Process requested on]** kolom.

* **In behandeling**: De gebeurtenis is verwerkt en de leveringssjabloon is gekoppeld. De e-mail is in afwachting van levering en het klassieke leveringsproces wordt toegepast. Voor meer informatie kunt u de levering openen.
* **Verzonden**, **Genegeerd** en **Afleveringsfout**: Deze leveringsstatussen worden teruggevorderd via de **updateEventsStatus** workflow. Voor meer informatie kunt u de relevante levering openen.
* **Gebeurtenis niet gedekt**: Het transactionele overseinen die fase verplettert ontbrak. Adobe Campaign heeft bijvoorbeeld het e-mailbericht dat als sjabloon voor de gebeurtenis fungeert, niet gevonden.
* **Gebeurtenis verlopen**: Het maximumaantal verzendpogingen is bereikt. De gebeurtenis wordt als null beschouwd.

## Recycling van gebeurtenissen {#event-recycling}

Als de levering van een bericht op een specifiek kanaal mislukt, kan Adobe Campaign het bericht opnieuw verzenden via een ander kanaal. Als een levering op het SMS-kanaal bijvoorbeeld mislukt, wordt het bericht opnieuw verzonden via het e-mailkanaal.

Hiertoe moet u een workflow configureren die alle gebeurtenissen opnieuw maakt met de **Afleveringsfout** en wijst er een ander kanaal aan toe.

>[!CAUTION]
>
>Deze stap kan alleen worden uitgevoerd met behulp van een workflow en is daarom voorbehouden aan professionele gebruikers. Neem voor meer informatie contact op met de manager van uw Adobe-account.