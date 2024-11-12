---
product: campaign
title: De juiste doelgroep definiëren
description: Leer de beste praktijken bij het selecteren van uw publiek
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Audiences
role: User
hide: true
hidefromtoc: true
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 3%

---

# De juiste doelgroep definiëren {#define-the-right-audience}

De doelgroep is belangrijk: maak uw lijsten zorgvuldig, test uw e-mails op populaire e-mailclients en mobiele apparaten en controleer of uw e-maillijsten up-to-date zijn (zonder onbekende of verouderde adressen). U kunt ook proefdrukken verzenden waarmee u een volledige validatiecyclus kunt instellen.

Leer meer over doelpopulaties [ in deze sectie ](steps-defining-the-target-population.md)

## Doelgroep {#target-the-right-audience}

Wanneer u uw inhoud klaar hebt, moet u zorgvuldig bepalen wie uw bericht zal ontvangen.

Om uw levering succesvol te maken, wilt u de meest relevante gepersonaliseerde inhoud naar de juiste ontvangers verzenden. Met Adobe Campaign kunt u het meest nauwkeurige doel maken: u kunt ontvangers selecteren op basis van hun leeftijd, lokalisatie, wat ze hebben gekocht, als ze op een koppeling in een vorige levering klikken, enzovoort. Met Adobe Campaign kunt u ook testprofielen, controlegroepen en zaadadressen definiëren om te controleren of het doel correct is.

## Doeltoewijzingen {#target-mappings}

In Campaign Classic, door gebrek, richten de leveringsmalplaatjes **Ontvangers**. Adobe Campaign biedt andere doeltoewijzingen voor uw leveringen die u op basis van uw behoeften kunt wijzigen.

U kunt bijvoorbeeld leveren aan bezoekers van wie de profielen via sociale netwerken zijn verzameld of aan bezoekers die zijn geabonneerd op een informatieservice.

Deze afbeeldingen worden voorgesteld [ in deze sectie ](selecting-a-target-mapping.md).

U kunt ook een aangepaste doeltoewijzing maken en gebruiken. Raadpleeg [deze sectie](../../configuration/using/target-mapping.md) voor meer informatie.

## Externe ontvangers {#external-recipients}

U kunt leveren aan ontvangers die in een extern dossier eerder dan opgeslagen in het gegevensbestand worden opgeslagen. Leer meer [ in deze sectie ](steps-defining-the-target-population.md#selecting-external-recipients).

## Verzenden naar uw abonnees {#send-to-subscribers}

Om berichten naar de abonnees van een nieuwsbrief te verzenden, kunt u de abonnees aan de overeenkomstige informatiedienst direct richten. Leer meer [ in deze sectie ](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Ontvangers en zaadadressen testen {#test-recipients-seed-addresses}

Om uw levering te testen, gebruik proef alvorens naar het belangrijkste doel te verzenden.

Zorg ervoor dat u de juiste ontvangers voor het bewijs selecteert, omdat deze het formulier en de inhoud van het bericht valideren. De stappen voor het bepalen van de proefontvangers worden voorgesteld [ in deze sectie ](steps-defining-the-target-population.md#selecting-the-proof-target).

De zaadadressen worden gebruikt aan doelontvangers die niet aan de bepaalde doelcriteria voldoen om een levering te testen alvorens naar het belangrijkste doel te verzenden. Zij worden voorgesteld [ in deze sectie ](about-seed-addresses.md).

## Gedupliceerde adressen {#deduplicate-addresses}

Het is belangrijk om dubbele e-mailadressen te vermijden, omdat dit van invloed kan zijn op uw doel:

* Hetzelfde bericht kan meerdere keren worden verzonden wanneer een doel wordt gesplitst.

* Als een ontvanger zich afmeldt na het ontvangen van een bericht, zal hun dubbele profiel nog toekomstige berichten ontvangen.

Deduplicating adressen beschermt uw verzendende reputatie en verzekert goed quarantainebeheer.

**Verwante onderwerpen:**

* [ de activiteit van de Deduplicatie ](../../workflow/using/deduplication.md).
* [Hoofdlettergebruik: samenvoegfunctionaliteit van de deduplicatieactiviteit gebruiken](../../workflow/using/deduplication-merge.md)

## E-mailadressen indexeren {#index-addresses}

Om de prestaties van de SQL vragen te optimaliseren die in de toepassing worden gebruikt, kan een index van het belangrijkste element van het gegevensschema worden verklaard.

De stappen voor het toevoegen van een index aan het e-mailadres worden voorgesteld [ in deze sectie ](../../configuration/using/database-mapping.md#indexed-fields).
