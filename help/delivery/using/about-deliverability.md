---
title: Over de leveringsmogelijkheden in Adobe Campagne Classic
description: Meer informatie over het beheren van de beschikbaarheid in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e6617614ae22b73c6783f9775f441e5e25ae19e3
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---


# Over leverbaarbaarheid{#about-deliverability}

**De leverbaarheid** bestaat uit het meten van het succes van uw campagnes die uw ontvangers&#39; inbox bereiken zonder te stuiteren, of als spam worden gemerkt.

Adobe Campaign biedt een aantal tools om de prestaties van uw platform bij te houden. In dit gedeelte worden ook de belangrijkste beginselen beschreven waarmee u rekening moet houden bij het beheren en optimaliseren van de leverbaarbaarheid.

## Configuratie {#configuration}

Deze functie is beschikbaar via een speciaal pakket in Adobe Campaign. Dit pakket moet zijn geïnstalleerd om het te kunnen gebruiken. Start vervolgens de server opnieuw om rekening te houden met het pakket.
* Voor gehoste en hybride clients wordt de **afleveringsbewaking** op uw exemplaar geconfigureerd door technische ondersteuning en consultants van Adobe. Neem voor meer informatie contact op met de manager van uw Adobe-account.

* Voor installaties op locatie moet u het **[!UICONTROL Deliverability monitoring (Email Deliverability)]** pakket installeren via **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Zie Klassieke standaardpakketten [voor campagne](../../installation/using/installing-campaign-standard-packages.md)installeren voor meer informatie.

In Adobe Campaign Classic wordt de **leveringscontrole** beheerd door de **[!UICONTROL Refresh for deliverability]** workflow. Het wordt geïnstalleerd door gebrek op alle instanties en laat u de lijst van de bounce kwalificatieregels van de post, de lijst van domeinen en de lijst van MXs initialiseren. Nadat het **[!UICONTROL Deliverability monitoring (Email Deliverability)]** pakket is geïnstalleerd, wordt deze workflow elke avond uitgevoerd om de lijst met regels regelmatig bij te werken en kunt u de leverbaarheid van het platform actief beheren.

## Achtergrond {#background}

E-maillevering is een grote uitdaging voor marketeers - of ze nu een paar duizend berichten of een paar miljard berichten sturen. Één op vijf berichten bereikt nooit inbox, of hun voorgenomen ontvanger.

Zodra het als &quot;technische kwestie&quot;voor de afdeling van IT wordt vermeld, blijft de postleverbaarheid hoger op de marketing agenda. Dat komt omdat slimme markten inzien dat hoewel veel van de elementen van de markt van technische aard zijn, de leverbaarheid uiteindelijk een zakelijke kwestie is met aanzienlijke gevolgen voor de inkomsten.

Kijk eens naar de e-mailmarketingtrechter. De leverbaarheid bepaalt het aantal ontvangen berichten, die beurtelings elke volgende fase van de trechter beïnvloeden. Minder ontvangen e-mailberichten leiden tot minder openen, minder klikken en minder conversies. **Voor bedrijven met een grote database kan het verschil tussen gemiddelde en grote leverantie letterlijk honderdduizenden tot miljoenen dollars aan inkomsten betekenen.**

![](assets/deliverability_overview_1.png)

Door te kiezen voor gemiddelde (80%) leverantie, laten marketeers aanzienlijke omzettingen - en dollars - op tafel.

Wat is precies e-mailleverbaarheid? En hoe kunnen marketeers de leveringspercentages verbeteren om de mond van de trechter te verbreden en meer resultaten uit hun e-mailcampagnes te persen?

De e-mailleverbaarheid verwijst naar de reeks kenmerken die bepalen of een bericht zijn bestemming, via een persoonlijk e-mailadres, binnen een korte tijd, en met de verwachte kwaliteit in termen van inhoud en formaat kan bereiken. Deze kenmerken vallen in vier hoofdcategorieën: gegevenskwaliteit, bericht en inhoud, verzendende infrastructuur, en reputatie. Samen vormen ze de basis voor een succesvol e-mailprogramma. In dit overzicht worden de vier basisprincipes van het succes van e-maillevering beschreven en worden de beste praktijken geboden voor het bereiken van de Postvak IN en het aansturen van meer inkomsten uit marketingprogramma&#39;s voor e-mail.

<!--![](assets/deliverability_overview_2.png)-->
