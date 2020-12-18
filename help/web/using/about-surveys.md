---
solution: Campaign Classic
product: campaign
title: 'Aan de slag met enquêtes '
description: Aan de slag met campagneenquêtes
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: e76eb171aac1f7088ff8647f99c928ec349b24fc
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 1%

---


# Aan de slag met enquêtes {#about-surveys}

Adobe Campaign bevat een grafische module voor het definiëren en publiceren van webtoepassingen. Hiermee maakt u pagina&#39;s, zoals een bewerkingsformulier op een extranet, of meldingsformulieren, inclusief gegevens uit de database met tabellen, grafieken, invoerformulieren, enz. Met deze functionaliteit kunt u webpagina&#39;s ontwerpen en plaatsen waar gebruikers informatie kunnen opzoeken of invoeren.

Met de optionele **Beoordelingsmodule** kunt u een nieuw type webtoepassing maken en beheren voor het maken en beheren van online vragenlijsten, zoals formulieren voor het toevoegen of wijzigen van profielgegevens, voor het abonneren op of het opzeggen van een informatieservice of een formulier voor mededingingsgegevens. Zodra de antwoorden zijn verzameld, worden zij opgeslagen in het gegevensbestand of in lokale variabelen. Het gegevensmodel kan dynamisch worden uitgebreid via de antwoorden op vragenlijsten. U kunt de resultaten in real time bekijken, de reacties filtreren, en hen analyseren gebruikend specifieke grafieken.

In dit hoofdstuk wordt de methode beschreven voor het maken en beheren van **Enquêtes**, veld- en paginabeheer, opslagmodi en records.

De stappen voor het creëren van een standaardvorm van het Web zijn gedetailleerd in [deze sectie](../../web/using/about-web-forms.md).

Webtoepassingsbeheer wordt beschreven in [deze sectie](../../web/using/about-web-applications.md). Raadpleeg dit hoofdstuk voor meer informatie.

>[!CAUTION]
>
>Om privacyredenen raden we aan HTTPS te gebruiken voor alle externe bronnen.

## Functiebereik {#campaign-surveys-scope}

In Adobe Campaign hebben webtoepassingen in het algemeen toegang tot de volgende functies:

* Formulier maken met meerdere pagina&#39;s,
* Meertalig beheer van enquêtes met een geïntegreerd vertaalhulpmiddel;
* Grafische paginabeheerinterface, paginalay-out met meerdere kolommen,
* Rendering van personalisatie en veldpositie,
* Voorwaardelijke weergave van enquêtevelden volgens antwoorden,
* Voorwaardelijke paginaweergave,
* Gegevens vóór goedkeuring controleren, afhankelijk van het type gegevens dat wordt verwacht (nummer, e-mailadres, datums enz.) en verplichte velden,
* Uitnodigingen/meldingen via e-mail verzenden,
* Personalisatie van fouten en eindberichten
* Gebruik van afbeeldingen, video&#39;s, hypertextkoppelingen, captcha, enzovoort.

>[!NOTE]
>
>Alle configuraties die zijn gekoppeld aan webformulieren worden beschreven in [deze sectie](../../web/using/about-web-forms.md). Raadpleeg dit document voor meer informatie over concepten en webformulierfuncties met Adobe Campaign.

De optionele module voor het maken van enquêtes (**Beoordeling**) biedt de volgende aanvullende functies:

* Dynamische extensie van de database: het creëren van antwoorden die geen deel van het aanvankelijke gegevensmodel uitmaken. Raadpleeg [Opgeslagen antwoorden opslaan](../../web/using/managing-answers.md#storing-collected-answers) voor meer informatie.
* Score-beheer. Raadpleeg [Score management](../../web/using/managing-answers.md#score-management) voor meer informatie.
* Willekeurige weergave van vragen. Raadpleeg [Vragen toevoegen](../../web/using/building-a-survey.md#adding-questions) voor meer informatie hierover.
* Real time tracking van antwoorden. Voor meer op dit, verwijs naar [Reactie het volgen](../../web/using/publish--track-and-use-collected-data.md#response-tracking).
* Speciale rapporten genereren. Raadpleeg [Rapporten over enquêtes](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys) voor meer informatie hierover.

Vergeleken met de toepassingen van het Web, hebben de onderzoeken een vereenvoudigde grafische interface met een verminderd aantal het uitgeven controles.

## Implementatiestappen voor enquêtes {#surveys-implementation-steps}

Pas de volgende stappen toe om een enquête te maken en te leveren en de resultaten ervan te verwerken:

1. Maak de pagina&#39;s van de enquête en de inhoud ervan (invoervelden, vervolgkeuzelijsten, vragen, enz.).
1. Bepaal hoe antwoorden moeten worden opgeslagen.

   U kunt een stap voor het laden van gegevens invoegen om het formulier vooraf te laden met gegevens die al in de database staan. U kunt ook een testvak toevoegen.

1. Publiceren en vervolgens de enquête aan ontvangers leveren (bijvoorbeeld een koppeling opnemen in een levering of in een website).
1. Reacties controleren en rapporten weergeven.

Voor meer informatie bij het vormen en het rangschikken van deze stappen, verwijs naar [deze sectie](../../web/using/about-web-forms.md). In dit hoofdstuk worden alleen configuraties beschreven die specifiek zijn voor enquêtes.

## Configuratie {#surveys-configuration} enquêtes

Enquêtes worden opgeslagen in het knooppunt **[!UICONTROL Resources > Online > Web Applications]** van de Adobe Campaign-structuur. Configuraties vindt u in de volgende mappen:

* **[!UICONTROL Administration > Configuration > Form rendering]**: Bevat de teruggevende malplaatjes voor de vormpresentatie van het Web (toepassingen en onderzoeken).
* **[!UICONTROL Resources > Templates > Web application templates]**: bevat de formuliersjablonen. Als u een formulier wilt maken, moet u beginnen met een sjabloon.

>[!NOTE]
>
>De informatie van de configuratie is beschikbaar in [deze sectie](../../web/using/about-web-forms.md).

