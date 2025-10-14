---
product: campaign
title: 'Aan de slag met enquêtes '
description: Aan de slag met campagneenquêtes
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 3%

---

# Aan de slag met enquêtes {#about-surveys}

Adobe Campaign bevat een grafische module voor het definiëren en publiceren van webtoepassingen. Hiermee maakt u pagina&#39;s, zoals een bewerkingsformulier op een extranet, of meldingsformulieren, inclusief gegevens uit de database met tabellen, grafieken, invoerformulieren, enz. Met deze functie kunt u webpagina&#39;s ontwerpen en plaatsen waarin gebruikers gegevens kunnen opzoeken of invoeren.

>[!AVAILABILITY]
>
>Het beheer van enquêtes is niet beschikbaar in Campaign v8 in de context van een implementatie van een Enterprise (FFDA). Leer meer in [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/config/architecture/ffda/enterprise-deployment){target="_blank"} .


De facultatieve **toe:voegen-op van het 0&rbrace; Onderzoek &lbrace;laat u een nieuw type van de toepassing van het Web tot stand brengen en leiden online vragenlijsten, zoals vormen om profielinformatie toe te voegen of te wijzigen, om aan of te ondertekenen van een informatiedienst, of een vorm van de mededingingsingang in te tekenen.** Zodra de antwoorden zijn verzameld, worden zij opgeslagen in het gegevensbestand of in lokale variabelen. Het gegevensmodel kan dynamisch worden uitgebreid via de antwoorden op vragenlijsten. U kunt de resultaten in real time bekijken, de reacties filtreren, en hen analyseren gebruikend specifieke grafieken.

Dit hoofdstuk specificeert om **Enquêtes**, gebied en paginabeheer, opslagwijzen en verslagen tot stand te brengen en te beheren.

Leer hoe te om uw eerste onderzoek in [&#x200B; tot stand te brengen deze pagina &#x200B;](getting-started-with-surveys.md).

>[!NOTE]
>
>* De gedetailleerde stappen voor het creëren van een standaardvorm van het Web zijn beschikbaar in [&#x200B; dit document &#x200B;](../../web/using/about-web-forms.md).
>
>* Het toepassingsbeheer van het Web is gedetailleerd in [&#x200B; dit document &#x200B;](../../web/using/about-web-applications.md). Raadpleeg dit hoofdstuk voor meer informatie.

## Functiebereik {#campaign-surveys-scope}

In Adobe Campaign, gebruik [&#128279;](../../web/using/about-web-forms.md) de toepassingen van het 0&rbrace; Web aan:

* Formulieren met meerdere pagina&#39;s maken,
* Meertalige formulieren beheren met een geïntegreerd vertaalhulpprogramma
* Grafische interface, paginalay-out met meerdere kolommen beheren,
* personalisatie toevoegen en veldpositie definiëren;
* Voorwaardelijke weergave van enquêtevelden volgens antwoorden,
* Weergave voorwaardepagina,
* Gegevens controleren vóór goedkeuring, afhankelijk van het type gegevens dat wordt verwacht (nummer, e-mailadres, datums, enz.) en verplichte velden;
* Uitnodigingen/meldingen per e-mail verzenden
* Fouten en eindpagina&#39;s personaliseren,
* Afbeeldingen, video&#39;s, hypertextkoppelingen, captcha, enz. toevoegen in formulieren

De optionele module voor het maken van enquêtes biedt een gebruikersvriendelijke gebruikersinterface en de volgende aanvullende functies:

* Dynamische extensie van de database: het maken van antwoorden die geen deel uitmaken van het oorspronkelijke gegevensmodel. [Meer informatie](../../surveys/using/managing-answers.md#storing-collected-answers).
* Score-beheer. [Meer informatie](../../surveys/using/managing-answers.md#score-management).
* Willekeurige weergave van vragen. [Meer informatie](../../surveys/using/building-a-survey.md#adding-questions).
* Real time tracking van antwoorden. [Meer informatie](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking).
* Speciale rapporten genereren. [Meer informatie](../../surveys/using/publish-track-and-use-collected-data.md#reports-on-surveys).


## Implementatiestappen {#surveys-implementation-steps}

Pas de volgende stappen toe om een enquête te maken en te leveren en de resultaten ervan te verwerken:

1. Maak de pagina&#39;s van de enquête en de inhoud ervan (invoervelden, vervolgkeuzelijsten, vragen, enz.).
1. Bepaal hoe antwoorden moeten worden opgeslagen. U kunt een stap voor het laden van gegevens invoegen om het formulier vooraf te laden met gegevens die al in de database staan. U kunt ook een testvak toevoegen.
1. Publish, levert de enquête vervolgens aan de ontvangers (bijvoorbeeld de link in een levering of op een website opnemen).
1. Reacties controleren en rapporten weergeven.

Voor meer informatie bij het vormen en het rangschikken van deze stappen, verwijs naar [&#x200B; dit document &#x200B;](../../web/using/about-web-forms.md). In dit hoofdstuk worden alleen configuraties beschreven die specifiek zijn voor enquêtes.

>[!CAUTION]
>
>Om privacyredenen raden we aan HTTPS te gebruiken voor alle externe bronnen.

## Instellingen {#settings}

Standaard zijn enquêtes beschikbaar in het knooppunt **[!UICONTROL Resources > Online > Web Applications]** van de Adobe Campaign-structuur.

Instellingen worden opgeslagen in de volgende mappen:

* **[!UICONTROL Administration > Configuration > Form rendering]**: bevat de renderingsjablonen voor de webformulierpresentatie (toepassingen en enquêtes).
* **[!UICONTROL Resources > Templates > Web application templates]** : bevat de formuliersjablonen. Als u een formulier wilt maken, moet u beginnen met een sjabloon.

>[!NOTE]
>
>De details van montages zijn beschikbaar in [&#x200B; dit document &#x200B;](../../web/using/about-web-forms.md).
