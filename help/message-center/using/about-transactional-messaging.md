---
product: campaign
title: Aan de slag met transactionele berichten
description: 'Meer informatie over het Adobe Campaign Classic-principe voor het bedienen van berichten en de belangrijkste stappen. '
audience: message-center
content-type: reference
topic-tags: introduction
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 6%

---


# Aan de slag met transactionele berichten {#about-transactional-messaging}

![](../../assets/v7-only.svg)

## Overzicht {#overview}

**Transactioneel overseinen**  (het Centrum van het Bericht) is een module van de Campagne die voor het beheren van de berichten van de douanetrekker wordt ontworpen die van gebeurtenissen worden geproduceerd die door een extern informatiesysteem worden verzonden.

Een transactiebericht is een individuele en unieke communicatie die in real time door een leverancier zoals een website wordt verzonden. Dit wordt vooral verwacht, omdat het belangrijke informatie bevat die de ontvanger wil controleren of bevestigen.

Transactionele berichtenmogelijkheden worden ontworpen om scalability te steunen en de dienst te verlenen 24/7.

* **Wanneer komt het?** Omdat dit bericht belangrijke informatie bevat, verwacht de gebruiker dat het in echt - tijd wordt verzonden. De vertraging tussen de gebeurtenis die wordt geactiveerd en het bericht dat aankomt, moet daarom zeer kort zijn.

* **Waarom is het belangrijk?** Over het algemeen zijn er voor een transactiebericht hoge open tarieven. Het moet daarom zorgvuldig worden ontworpen, omdat het een sterke invloed kan hebben op het gedrag van de klanten, aangezien het de relatie met de klant definieert.

* **Bijvoorbeeld?** Het kan een welkomstbericht zijn na het maken van een account, een bevestiging dat een bestelling is verzonden, een factuur, een bericht ter bevestiging van een wijziging van het wachtwoord, een melding nadat een klant door uw website is gebladerd, een communicatie over de onbeschikbaarheid van het product, een accountverklaring, enz.

>[!IMPORTANT]
>
>Voor Transactioneel overseinen is een specifieke licentie vereist. Controleer uw licentieovereenkomst.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## Werkingsprincipe voor transactieberichten {#transactional-messaging-operating-principle}

De module van het Overseinen van Adobe Campaign Transactional integreert in een informatiesysteem dat gebeurtenissen terugkeert die in gepersonaliseerde transactionele berichten moeten worden veranderd. Deze berichten kunnen individueel of in partijen via e-mail, SMS of push-berichten worden verzonden.

Deze eigenschap baseert zich op een specifieke architectuur, waar **uitvoeringsinstantie** van **control instantie** wordt gescheiden. Deze distributie zorgt voor een hogere beschikbaarheid en een beter beheer van de belasting. Voor meer op dit, zie [Transactionele overseinenarchitectuur](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>Als u nieuwe gebruikers wilt maken voor de uitvoering van Message Center-instanties die worden gehost op Adobe Cloud, moet u contact opnemen met [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). De gebruikers van het Centrum van het bericht zijn specifieke exploitanten die specifieke toestemmingen aan toegang **[!UICONTROL Real time events (nmsRtEvent)]** omslagen vereisen.

Het algemene proces van het transactieoverseinen kan als volgt worden beschreven:

![](assets/transactional-msg-overview.png)

Stel dat u een bedrijf bent met een website waar uw klanten producten kunnen kopen.

Met Adobe Campaign kunt u een meldingsbericht verzenden naar klanten die producten aan hun winkelwagentje hebben toegevoegd. Wanneer een van hen uw website verlaat zonder door te gaan met hun aankopen (externe gebeurtenis die een Campagne-gebeurtenis activeert), wordt er automatisch een e-mailbericht over het verlaten van de winkelwagen naar hen verzonden (levering van transactiemeldingen).

De belangrijkste stappen voor het plaatsen van dit in plaats zijn hieronder in [dit sectie](#key-steps) beschreven.

>[!NOTE]
>
>Adobe Campaign geeft voorrang aan het verwerken van transactieberichten boven elke andere levering.

## Belangrijkste stappen {#key-steps}

De belangrijkste stappen bij het maken en beheren van persoonlijke transactiemeldingen in Adobe Campaign worden hieronder samengevat.

### Stappen om op de controleinstantie uit te voeren

Op **control instance**, moet u de volgende acties uitvoeren:

1. [Maak een gebeurtenistype](../../message-center/using/creating-event-types.md).
1. [Maak en ontwerp de berichtsjabloon](../../message-center/using/creating-the-message-template.md). Tijdens deze stap moet u een gebeurtenis koppelen aan uw bericht.
1. [Test het bericht](../../message-center/using/testing-message-templates.md).
1. [Publiceer de berichtsjabloon](../../message-center/using/publishing-message-templates.md).

>[!NOTE]
>
>Alle bovenstaande stappen worden uitgevoerd op de **besturingsinstantie**. Het publiceren van het malplaatje op de controleinstantie zal het op alle **uitvoeringsinstanties** ook publiceren. Voor meer op de instanties van het transactionele overseinen, zie [Transactionele overseinenarchitectuur](../../message-center/using/transactional-messaging-architecture.md).

### Gebeurtenisverwerking op de uitvoeringsinstantie

Zodra u het transactionele berichtmalplaatje ontwierp en publiceerde, als een overeenkomstige gebeurtenis wordt teweeggebracht, worden de belangrijkste hieronder stappen uitgevoerd op **uitvoeringsinstantie**:

1. Wanneer de gebeurtenis door het externe informatiesysteem wordt geproduceerd, worden de relevante gegevens verzonden naar Campagne via **PushEvent** en **PushEvents** methodes. Zie [Gebeurtenisverzameling](../../message-center/using/about-event-processing.md#event-collection).
1. De gebeurtenis is gekoppeld aan de juiste berichtsjabloon. Zie [Verpletterend naar een malplaatje](../../message-center/using/about-event-processing.md#routing-towards-a-template).
1. Zodra het verrijkingsstadium volledig is, wordt de levering verzonden. Zie [Uitvoering van levering](../../message-center/using/delivery-execution.md). Elke beoogde ontvanger ontvangt een gepersonaliseerd bericht.

## Verwante onderwerpen {#related-topics}

* [Aan de slag met communicatiekanalen](../../delivery/using/communication-channels.md)
* [Belangrijkste stappen bij het maken van de levering](../../delivery/using/steps-about-delivery-creation-steps.md)
* [Architectuur van transactionele berichten](../../message-center/using/transactional-messaging-architecture.md)
* [Rapporten van transactionele berichten openen ](../../message-center/using/about-transactional-messaging-reports.md)
