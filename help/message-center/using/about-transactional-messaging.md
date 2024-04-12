---
product: campaign
title: Aan de slag met transactionele berichten
description: Meer informatie over het Adobe Campaign Classic-operatieprincipe voor berichten en de belangrijkste stappen
feature: Transactional Messaging, Message Center
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 4%

---


# Aan de slag met transactionele berichten {#about-transactional-messaging}



## Overzicht {#overview}

**Transactieberichten** (Berichtencentrum) is een module van de Campagne die voor het beheren van de berichten van de douanetrekker wordt ontworpen die van gebeurtenissen worden geproduceerd die door een extern informatiesysteem worden verzonden.

Een transactiebericht is een individuele en unieke communicatie die in real time door een leverancier zoals een website wordt verzonden. Dit wordt vooral verwacht, omdat het belangrijke informatie bevat die de ontvanger wil controleren of bevestigen.

Transactionele berichtenmogelijkheden worden ontworpen om scalability te steunen en de dienst te verlenen 24/7.

* **Wanneer is het te verwachten?** Omdat dit bericht belangrijke informatie bevat, verwacht de gebruiker dat het in echt - tijd wordt verzonden. De vertraging tussen de gebeurtenis die wordt geactiveerd en het bericht dat aankomt, moet daarom zeer kort zijn.

* **Waarom is het belangrijk?** Over het algemeen zijn er voor een transactiebericht hoge open tarieven. Het moet daarom zorgvuldig worden ontworpen, omdat het een sterke invloed kan hebben op het gedrag van de klanten, aangezien het de relatie met de klant definieert.

* **Bijvoorbeeld?** Het kan een welkomstbericht zijn na het maken van een account, een bevestiging dat een bestelling is verzonden, een factuur, een bericht ter bevestiging van een wijziging van het wachtwoord, een melding nadat een klant door uw website is gebladerd, een communicatie over de onbeschikbaarheid van het product, een accountverklaring, enz.

>[!IMPORTANT]
>
>Voor Transactioneel overseinen is een specifieke licentie vereist. Controleer hiervoor uw licentieovereenkomst.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## Operationeel beginsel van het transactieverkeer {#transactional-messaging-operating-principle}

De module van het Overseinen van Adobe Campaign Transactional integreert in een informatiesysteem dat gebeurtenissen terugkeert die in gepersonaliseerde transactionele berichten moeten worden veranderd. Deze berichten kunnen individueel of in partijen via e-mail, SMS of push-berichten worden verzonden.

Deze functie is afhankelijk van een specifieke architectuur, waarbij de **uitvoeringsinstantie** wordt gescheiden van de **besturingsinstantie**. Deze distributie zorgt voor een hogere beschikbaarheid en een beter beheer van de belasting. Zie voor meer informatie [Transactionele berichtenarchitectuur](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>Als u nieuwe gebruikers wilt maken voor instanties die worden gehost op de Adobe Cloud in Message Center, moet u contact opnemen met [Klantenservice Adoben](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). De gebruikers van het Centrum van het bericht zijn specifieke exploitanten die specifieke toestemmingen vereisen om toegang te hebben **[!UICONTROL Real time events (nmsRtEvent)]** mappen.

Het algemene proces van het transactieoverseinen kan als volgt worden beschreven:

![](assets/transactional-msg-overview.png)

Stel dat u een bedrijf bent met een website waar uw klanten producten kunnen kopen.

Met Adobe Campaign kunt u een meldingsbericht verzenden naar klanten die producten aan hun winkelwagentje hebben toegevoegd. Wanneer een van hen uw website verlaat zonder door te gaan met hun aankopen (externe gebeurtenis die een Campagne-gebeurtenis activeert), wordt er automatisch een e-mailbericht over het verlaten van de winkelwagen naar hen verzonden (levering van transactiemeldingen).

De belangrijkste stappen om dit in te voeren zijn hieronder beschreven [deze sectie](#key-steps).

>[!NOTE]
>
>Adobe Campaign geeft voorrang aan het verwerken van transactieberichten boven elke andere levering.

## Belangrijkste stappen {#key-steps}

De belangrijkste stappen bij het maken en beheren van persoonlijke transactiemeldingen in Adobe Campaign worden hieronder samengevat.

### Stappen om op de controleinstantie uit te voeren

Op de **besturingsinstantie** moet u de volgende handelingen uitvoeren:

1. [Een gebeurtenistype maken](../../message-center/using/creating-event-types.md).
1. [De berichtsjabloon maken en ontwerpen](../../message-center/using/creating-the-message-template.md). Tijdens deze stap moet u een gebeurtenis koppelen aan uw bericht.
1. [Het bericht testen](../../message-center/using/testing-message-templates.md).
1. [De berichtsjabloon publiceren](../../message-center/using/publishing-message-templates.md).

>[!NOTE]
>
>Alle bovenstaande stappen worden uitgevoerd op de **besturingsinstantie**. Het publiceren van het malplaatje op de controleinstantie zal het op allen ook publiceren **uitvoeringsinstanties**. Voor meer op de instanties van het transactionele overseinen, zie [Transactionele berichtenarchitectuur](../../message-center/using/transactional-messaging-architecture.md).

### Gebeurtenisverwerking op de uitvoeringsinstantie

Nadat u de transactiemplate hebt ontworpen en gepubliceerd, worden de onderstaande hoofdstappen uitgevoerd op het **uitvoeringsinstantie**:

1. Wanneer de gebeurtenis door het externe informatiesysteem wordt gegenereerd, worden de relevante gegevens via de **PushEvent** en **PushEvents** methoden. Zie [Gebeurtenisverzameling](../../message-center/using/about-event-processing.md#event-collection).
1. De gebeurtenis is gekoppeld aan de juiste berichtsjabloon. Zie [Het verpletteren aan een malplaatje](../../message-center/using/about-event-processing.md#routing-towards-a-template).
1. Zodra het verrijkingsstadium volledig is, wordt de levering verzonden. Zie [Uitvoering van levering](../../message-center/using/delivery-execution.md). Elke beoogde ontvanger ontvangt een gepersonaliseerd bericht.

## Verwante onderwerpen {#related-topics}

* [Aan de slag met communicatiekanalen](../../delivery/using/communication-channels.md)
* [Belangrijkste stappen bij het maken van de levering](../../delivery/using/steps-about-delivery-creation-steps.md)
* [Architectuur van transactionele berichten](../../message-center/using/transactional-messaging-architecture.md)
* [Rapporten van transactionele berichten openen ](../../message-center/using/about-transactional-messaging-reports.md)
