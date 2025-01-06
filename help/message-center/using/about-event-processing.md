---
product: campaign
title: Gebeurtenisverwerking
description: Leer hoe de transactieberichten worden verwerkt in Adobe Campaign Classic
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 2%

---

# Gebeurtenisverwerking {#about-event-processing}



In de context van transactioneel overseinen, wordt een gebeurtenis geproduceerd door een extern informatiesysteem en verzonden naar Adobe Campaign via **[!UICONTROL PushEvent]** en **[!UICONTROL PushEvents]** methodes (zie [ de beschrijving van de Gebeurtenis ](../../message-center/using/event-description.md)).

Deze gebeurtenis bevat gegevens met betrekking tot de gebeurtenis, zoals zijn [ type ](../../message-center/using/creating-event-types.md) (ordesbevestiging, rekeningsverwezenlijking op een website, enz.), e-mailadres of mobiel aantal, evenals andere informatie die u het transactiebericht vóór levering (de informatie van het klantencontact, taal van het bericht, e-mailformaat, enz.) verrijkt en personaliseert.

Voorbeeld van gebeurtenisgegevens:

![](assets/messagecenter_events_request_001.png)

## Stappen voor gebeurtenisverwerking {#event-processing}

Om transactionele berichtengebeurtenissen te verwerken, worden de volgende stappen toegepast op de uitvoeringsinstantie(s):

1. [Gebeurtenisverzameling](#event-collection)
1. [Gebeurtenisoverdracht naar een berichtsjabloon](#routing-towards-a-template)
1. Gebeurtenisverrijking met personalisatiegegevens
1. [Uitvoering van levering](../../message-center/using/delivery-execution.md)
1. [ Recycling van gebeurtenissen ](#event-recycling) de waarvan verbonden levering ontbrak (via een werkschema van Adobe Campaign)

Zodra alle stappen hierboven door de uitvoeringsinstantie worden uitgevoerd, ontvangt elke gerichte ontvanger een gepersonaliseerd bericht.

>[!NOTE]
>
>Voor meer op de instanties van het transactionele overseinen, zie [ Transactionele overseinenarchitectuur ](../../message-center/using/transactional-messaging-architecture.md).


## Gebeurtenisverzameling {#event-collection}

Gebeurtenissen die door het informatiesysteem worden gegenereerd, kunnen in twee modi worden verzameld:

* Met aanroepen van SOAP methoden kunt u gebeurtenissen in Adobe Campaign duwen: met de methode PushEvent kunt u één gebeurtenis tegelijk verzenden. Met de methode PushEvents kunt u verschillende gebeurtenissen tegelijk verzenden. Voor meer op dit, zie [ beschrijving van de Gebeurtenis ](../../message-center/using/event-description.md).

* Het creëren van een werkschema laat u gebeurtenissen terugkrijgen door dossiers of via een SQL gateway (met de [ Verdeelde optie van de Toegang van Gegevens ](../../installation/using/about-fda.md) in te voeren).

Zodra zij worden verzameld, worden de gebeurtenissen verdeeld door technische werkschema&#39;s tussen echt - tijd en partijrijen van de uitvoeringsinstantie(s), terwijl het wachten om aan een berichtmalplaatje worden verbonden.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Op uitvoeringsinstanties moeten de mappen **[!UICONTROL Real time events]** of **[!UICONTROL Batch events]** niet worden ingesteld als weergaven, omdat dit tot problemen met toegangsrechten kan leiden. Voor meer bij het plaatsen van een omslag als mening, verwijs naar [ deze sectie ](../../platform/using/access-management-folders.md).

## Routering naar een sjabloon {#routing-towards-a-template}

Nadat de berichtsjabloon op de uitvoeringsinstantie(s) is gepubliceerd, worden automatisch twee sjablonen gegenereerd: een sjabloon die aan een realtime-gebeurtenis moet worden gekoppeld en een sjabloon dat aan een batchgebeurtenis moet worden gekoppeld.

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

De **geschiedenis van de Gebeurtenis**, onder **[!UICONTROL Message Center]** > **[!UICONTROL Event history]**, groepeert alle verwerkte gebeurtenissen in één enkele mening. Zij kunnen door gebeurtenistype of door **status** worden gecategoriseerd. Deze statussen zijn:

* **In afwachting**: De gebeurtenis kan zijn:

   * Een gebeurtenis die zojuist is verzameld en nog niet is verwerkt. In de kolom **[!UICONTROL Number of errors]** wordt de waarde 0 weergegeven. De e-mailsjabloon is nog niet gekoppeld.
   * Een gebeurtenis is verwerkt, maar de bevestiging is onjuist. De kolom **[!UICONTROL Number of errors]** toont een waarde die niet 0 is. Raadpleeg de kolom **[!UICONTROL Process requested on]** als u wilt weten wanneer deze gebeurtenis opnieuw wordt verwerkt.

* **Hangende levering**: De gebeurtenis werd verwerkt en het leveringsmalplaatje is verbonden. De e-mail is in afwachting van levering en het klassieke leveringsproces wordt toegepast. Voor meer informatie kunt u de levering openen.
* **Verzonden**, **genegeerde** en **fout van de Levering**: Deze leveringsstatussen worden teruggekregen via het **updateEventsStatus** werkschema. Voor meer informatie kunt u de relevante levering openen.
* **Gebeurtenis niet behandeld**: Het transactionele overseinen die fase verplettert ontbrak. Adobe Campaign heeft bijvoorbeeld het e-mailbericht dat als sjabloon voor de gebeurtenis fungeert, niet gevonden.
* **Gebeurtenis verliep**: Het maximumaantal verzendt pogingen werd bereikt. De gebeurtenis wordt als null beschouwd.

## Recycling van gebeurtenissen {#event-recycling}

Als de levering van een bericht op een specifiek kanaal mislukt, kan Adobe Campaign het bericht opnieuw verzenden via een ander kanaal. Als een levering op het SMS-kanaal bijvoorbeeld mislukt, wordt het bericht opnieuw verzonden via het e-mailkanaal.

Om dit te doen, moet u een werkschema vormen dat alle gebeurtenissen met de **fout van de Levering** status ontspant, en een verschillend kanaal aan hen toewijst.

>[!CAUTION]
>
>Deze stap kan alleen worden uitgevoerd met behulp van een workflow en is daarom voorbehouden aan professionele gebruikers. Neem voor meer informatie contact op met het accountmanager van de Adobe.