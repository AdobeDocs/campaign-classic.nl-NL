---
product: campaign
title: 'Aan de slag met enquêtes '
description: Aan de slag met campagneenquêtes
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 86963746d3de3396963d221ddbd1ef7d89733d2f
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 4%

---

# Aan de slag met enquêtes {#about-surveys}

Adobe Campaign bevat een grafische module voor het definiëren en publiceren van webtoepassingen. Hiermee maakt u pagina&#39;s, zoals een bewerkingsformulier op een extranet, of meldingsformulieren, inclusief gegevens uit de database met tabellen, grafieken, invoerformulieren, enz. Met deze functie kunt u webpagina&#39;s ontwerpen en plaatsen waarin gebruikers gegevens kunnen opzoeken of invoeren.

Met de optionele **Survey** add-on kunt u een nieuw type webtoepassing maken en beheren voor het maken en beheren van online vragenlijsten, zoals formulieren voor het toevoegen of wijzigen van profielgegevens, voor het abonneren op of het opzeggen van een informatieservice of een formulier voor mededingingsgegevens. Zodra de antwoorden zijn verzameld, worden zij opgeslagen in het gegevensbestand of in lokale variabelen. Het gegevensmodel kan dynamisch worden uitgebreid via de antwoorden op vragenlijsten. U kunt de resultaten in real time bekijken, de reacties filtreren, en hen analyseren gebruikend specifieke grafieken.

In dit hoofdstuk wordt beschreven hoe u **Enquêtes**, veld- en paginabeheer, opslagmodi en records kunt maken en beheren.

[!DNL :bulb:] Leer hoe u uw eerste enquête maakt op  [deze pagina](getting-started-with-surveys.md).

>[!NOTE]
>
>* De gedetailleerde stappen voor het creëren van een standaardvorm van het Web zijn beschikbaar in [dit document](../../web/using/about-web-forms.md).
   >
   >
* Webtoepassingsbeheer wordt beschreven in [dit document](../../web/using/about-web-applications.md). Raadpleeg dit hoofdstuk voor meer informatie.


## Functiebereik {#campaign-surveys-scope}

In Adobe Campaign, gebruik [de toepassingen van het Web](../../web/using/about-web-forms.md) aan:

* Formulieren met meerdere pagina&#39;s maken,
* Meertalige formulieren beheren met een geïntegreerd vertaalhulpprogramma
* Grafische interface, paginalay-out met meerdere kolommen beheren,
* Aanpassing toevoegen en veldpositie definiëren
* Voorwaardelijke weergave van enquêtevelden volgens antwoorden,
* Weergave voorwaardepagina,
* Gegevens controleren vóór goedkeuring, afhankelijk van het type gegevens dat wordt verwacht (nummer, e-mailadres, datums, enz.) en verplichte velden,
* Uitnodigingen/meldingen per e-mail verzenden
* Fouten en eindpagina&#39;s personaliseren,
* Afbeeldingen, video&#39;s, hypertextkoppelingen, captcha, enz. toevoegen in formulieren

De optionele module voor het maken van enquêtes biedt een gebruikersvriendelijke gebruikersinterface en de volgende aanvullende functies:

* Dynamische extensie van de database: het creëren van antwoorden die geen deel van het aanvankelijke gegevensmodel uitmaken. [Meer informatie](../../surveys/using/managing-answers.md#storing-collected-answers).
* Score-beheer. [Meer informatie](../../surveys/using/managing-answers.md#score-management).
* Willekeurige weergave van vragen. [Meer informatie](../../surveys/using/building-a-survey.md#adding-questions).
* Real time tracking van antwoorden. [Meer informatie](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking).
* Speciale rapporten genereren. [Meer informatie](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys).


## Implementatiestappen {#surveys-implementation-steps}

Pas de volgende stappen toe om een enquête te maken en te leveren en de resultaten ervan te verwerken:

1. Maak de pagina&#39;s van de enquête en de inhoud ervan (invoervelden, vervolgkeuzelijsten, vragen, enz.).
1. Bepaal hoe antwoorden moeten worden opgeslagen. U kunt een stap voor het laden van gegevens invoegen om het formulier vooraf te laden met gegevens die al in de database staan. U kunt ook een testvak toevoegen.
1. Publiceren en vervolgens de enquête aan ontvangers leveren (bijvoorbeeld een koppeling opnemen in een levering of in een website).
1. Reacties controleren en rapporten weergeven.

Voor meer informatie bij het vormen en het rangschikken van deze stappen, verwijs naar [dit document](../../web/using/about-web-forms.md). In dit hoofdstuk worden alleen configuraties beschreven die specifiek zijn voor enquêtes.

>[!CAUTION]
>
>Om privacyredenen raden we aan HTTPS te gebruiken voor alle externe bronnen.

## Instellingen {#settings}

Standaard zijn enquêtes beschikbaar in het knooppunt **[!UICONTROL Resources > Online > Web Applications]** van de Adobe Campaign-structuur.

Instellingen worden opgeslagen in de volgende mappen:

* **[!UICONTROL Administration > Configuration > Form rendering]**: Bevat de teruggevende malplaatjes voor de vormpresentatie van het Web (toepassingen en onderzoeken).
* **[!UICONTROL Resources > Templates > Web application templates]**: bevat de formuliersjablonen. Als u een formulier wilt maken, moet u beginnen met een sjabloon.

>[!NOTE]
>
>De details van montages zijn beschikbaar in [dit document](../../web/using/about-web-forms.md).
