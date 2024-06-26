---
product: campaign
title: Een webapplicatie ontwerpen
description: Een webapplicatie ontwerpen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 4%

---

# Een webapplicatie ontwerpen{#designing-a-web-application}



Webtoepassingen worden volgens hetzelfde principe als [webformulieren](about-web-forms.md).

>[!CAUTION]
>
>Gebruik de **[!UICONTROL Preview]** subtabblad om fouten tijdens het ontwerpen van webtoepassingen te controleren. De profieltest die wordt gebruikt om een voorvertoning van uw webtoepassing weer te geven, moet zich bevinden in een map met **[!UICONTROL Access rights]** voor de **[!UICONTROL Web application agent]** operator. </br>Totdat de toepassing van het Web wordt gepubliceerd, worden de veranderingen niet blootgesteld aan eind - gebruikers.

## Het opnemen van grafieken in een toepassing van het Web {#inserting-charts-in-a-web-application}

U kunt grafieken in de toepassingen van het Web omvatten. Hiervoor selecteert u met de vervolgkeuzelijst met grafieken in de taakbalk het type diagram dat u wilt invoegen.

![](assets/s_ncs_admin_webapps_bar_graph.png)

U kunt ook de optie **[!UICONTROL Add a chart]** -menu.

![](assets/s_ncs_admin_webapps_graph.png)

## Tabellen invoegen in een webtoepassing {#inserting-tables-in-a-web-application}

Als u een tabel wilt toevoegen, selecteert u het type tabel dat u wilt gebruiken in de vervolgkeuzelijst met tabellen op de taakbalk.

![](assets/s_ncs_admin_webapps_bar_table.png)

U kunt ook het type tabel selecteren in het keuzemenu.

![](assets/s_ncs_admin_webapps_table.png)

## Overzicht-type de toepassingen van het Web {#overview-type-web-applications}

De interface van Adobe Campaign gebruikt vele toepassingen van het Web om, tot ontvangers, leveringen, campagnes, voorraden, enz. toegang te hebben te beheren en in wisselwerking te staan.

Deze worden in de interface weergegeven in de vorm van dashboards met slechts één pagina.

De toepassingen van het out-of-box Web worden opgeslagen in **[!UICONTROL Administration > Configuration > Web applications]** knooppunt.

## Formuliertype webtoepassingen bewerken {#edit-forms-type-web-applications}

De toepassingen van het formulierWeb voor een extranet bewerken worden gekenmerkt door:

* Een voorlaadvenster

  In de meeste gevallen moeten de gegevens die worden weergegeven, vooraf worden geladen. Omdat de gebruikers die tot deze vormen toegang hebben (via een toegangscontrole) worden geïdentificeerd, wordt het vooraf laden niet noodzakelijk gecodeerd.

* Een vak voor opslaan
* Pagina&#39;s toevoegen

  Terwijl de &quot;overzicht&quot;-typeToepassingen van het Web allen één enkele pagina hebben, geef vormen een opeenvolging van pagina&#39;s uit die op specifieke criteria (tests, selecties, profiel van verbonden exploitant, enz.) worden gebaseerd.

