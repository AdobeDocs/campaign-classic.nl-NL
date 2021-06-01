---
product: campaign
title: Een webapplicatie ontwerpen
description: Een webapplicatie ontwerpen
audience: web
content-type: reference
topic-tags: web-applications
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 3%

---

# Een webapplicatie ontwerpen{#designing-a-web-application}

Webtoepassingen worden volgens hetzelfde principe gemaakt en beheerd als [online enquêtes](../../web/using/about-surveys.md).

De functionele verschillen zijn echter als volgt:

* Webtoepassingen gebruiken geen gearchiveerde velden. Gegevens kunnen daarom alleen in databasevelden of lokale variabelen worden opgeslagen.
* Er zijn geen ingebouwde rapporten over de toepassingen van het Web.
* Er worden extra velden aangeboden, vooral voor het maken van tabellen en grafieken.

>[!CAUTION]
>
>Het wordt hoogst geadviseerd dat de toegepaste configuraties voortdurend worden gecontroleerd om het even welke fouten vroeg in het de toepassingsbouwproces van het Web te ontdekken. Als u de rendering van een wijziging wilt controleren, slaat u de toepassing op en klikt u op het subtabblad **[!UICONTROL Preview]**.
>
>Totdat de toepassing van het Web wordt gepubliceerd, kunnen de veranderingen niet door het eind worden gezien - gebruiker.

## Het opnemen van grafieken in een toepassing {#inserting-charts-in-a-web-application}

U kunt grafieken in de toepassingen van het Web omvatten. Hiervoor selecteert u met de vervolgkeuzelijst met grafieken in de taakbalk het type diagram dat u wilt invoegen.

![](assets/s_ncs_admin_webapps_bar_graph.png)

U kunt ook het menu **[!UICONTROL Add a chart]** selecteren.

![](assets/s_ncs_admin_webapps_graph.png)

## Tabellen invoegen in een webtoepassing {#inserting-tables-in-a-web-application}

Als u een tabel wilt toevoegen, selecteert u het type tabel dat u wilt gebruiken in de vervolgkeuzelijst met tabellen op de taakbalk.

![](assets/s_ncs_admin_webapps_bar_table.png)

U kunt ook het type tabel selecteren in het keuzemenu.

![](assets/s_ncs_admin_webapps_table.png)

## Overzicht-type de toepassingen van het Web {#overview-type-web-applications}

De interface van Adobe Campaign gebruikt vele toepassingen van het Web om, tot ontvangers, leveringen, campagnes, voorraden, enz. toegang te hebben te beheren en in wisselwerking te staan.

Deze worden in de interface weergegeven in de vorm van dashboards met slechts één pagina.

De uit-van-de-doos toepassingen van het Web worden opgeslagen in de **[!UICONTROL Administration > Configuration > Web applications]** knoop.

## Formuliertype webtoepassingen bewerken {#edit-forms-type-web-applications}

De toepassingen van het formulierWeb voor een extranet bewerken worden gekenmerkt door:

* Een voorlaadvenster

   In de meeste gevallen moeten de gegevens die worden weergegeven, vooraf worden geladen. Omdat de gebruikers die tot deze vormen toegang hebben (via een toegangscontrole) worden geïdentificeerd, wordt het vooraf laden niet noodzakelijk gecodeerd.

* Een opslagvak
* Pagina&#39;s toevoegen

   Terwijl de &quot;overzicht&quot;-typeToepassingen van het Web allen één enkele pagina hebben, geef vormen een opeenvolging van pagina&#39;s uit die op specifieke criteria (tests, selecties, profiel van verbonden exploitant, enz.) worden gebaseerd.

De verrichting van dit type van de toepassing van het Web is gelijkaardig aan **Enquêtes**, maar zonder geschiedenisbeheer of gebiedsarchivering. Gebruikers krijgen meestal toegang via een aanmeldingspagina waar zij zich moeten identificeren.
