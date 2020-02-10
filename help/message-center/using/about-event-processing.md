---
title: Gebeurtenisverwerking
seo-title: Gebeurtenisverwerking
description: Gebeurtenisverwerking
seo-description: null
page-status-flag: never-activated
uuid: 6c3e02b3-0d4d-4661-952a-e4915ca9ef92
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: a78c9986-7c49-47db-99a0-9f0949c4dee7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c2c53041d8a19a491b8ec4da12a8a0ced25cf9a

---


# Gebeurtenisverwerking{#about-event-processing}

In de context van transactiemelding, wordt een gebeurtenis geproduceerd door een extern informatiesysteem en verzonden naar de Campagne van Adobe via de **[!UICONTROL PushEvent]** en **[!UICONTROL PushEvents]** methodes (zie de beschrijving [van de](../../message-center/using/event-description.md)Gebeurtenis). Het bevat gegevens die aan de gebeurtenis zijn gekoppeld, zoals het type (bevestiging van de bestelling of het maken van een account op bijvoorbeeld een website), het e-mailadres of het mobiele nummer, en andere informatie waarmee u het transactiemelding vóór levering kunt verrijken en personaliseren. Dit kunnen de contactgegevens van de klant, de taal van het bericht of het e-mailformaat zijn.

Voorbeeld van gebeurtenisgegevens:

![](assets/messagecenter_events_request_001.png)

Om transactionele overseinengebeurtenissen te verwerken, moeten de volgende stappen worden toegepast:

1. Gebeurtenisverzameling,
1. De verrijking van de gebeurtenis voorafgaand aan wordt overgebracht naar een berichtmalplaatje (als u de verrijkingsoptie beschikbaar voor de module van het de transactieoverseinen van de Campagne verwierf),
1. Gebeurtenisoverdracht naar een berichtsjabloon,
1. Verrijking van gebeurtenissen met personalisatiegegevens,
1. Uitvoering van de levering,
1. Recycling van gebeurtenissen waarvan de gekoppelde levering is mislukt (deze stap kan worden uitgevoerd via een Adobe Campagne-workflow).

## Gebeurtenisstatussen {#event-statuses}

In de **gebeurtenisgeschiedenis**, onder **[!UICONTROL Message Center]** > **[!UICONTROL Event history]** , worden alle verwerkte gebeurtenissen gegroepeerd in één weergave. Ze kunnen worden gecategoriseerd op gebeurtenistype of op **status**. Deze statussen zijn:

* **In behandeling**: Dit betekent dat het evenement:

   * een gebeurtenis die zojuist is verzameld en nog niet is verwerkt. In de **[!UICONTROL Number of errors]** kolom wordt de waarde 0 weergegeven. De e-mailsjabloon is nog niet gekoppeld.
   * een gebeurtenis is verwerkt, maar waarvan de bevestiging onjuist is. De **[!UICONTROL Number of errors]** kolom toont een waarde die niet 0 is. Raadpleeg de **[!UICONTROL Process requested on]** kolom als u wilt weten wanneer deze gebeurtenis opnieuw wordt verwerkt.

* **In afwachting van levering**: de gebeurtenis is verwerkt en de leveringstemplate is gekoppeld. De e-mail is in afwachting van levering en het klassieke leveringsproces wordt toegepast. Voor meer informatie kunt u de levering openen. Zie [Aflevering](../../delivery/using/about-message-tracking.md).
* **Verzonden**, **genegeerd** en **leveringsfout**: deze leveringsstatussen worden hersteld via de **updateEventsStatus** -workflow. Voor meer informatie kunt u de relevante levering openen.
* **Gebeurtenis niet behandeld**: het Centrum dat van het Bericht verplettert ontbrak fase. Adobe Campaign heeft bijvoorbeeld het e-mailbericht dat als sjabloon voor de gebeurtenis fungeert, niet gevonden.
* **Gebeurtenis verlopen**: het maximumaantal verzendpogingen is bereikt. De gebeurtenis wordt als null beschouwd.
