---
solution: Campaign Classic
product: campaign
title: De opmaak van webformulieren definiëren
description: De opmaak van webformulieren definiëren
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 2%

---


# De opmaak van webformulieren definiëren{#defining-web-forms-layout}

## Containers {#creating-containers} maken

Met containers kunt u de velden van een pagina combineren en de lay-out ervan configureren. om de elementen op de pagina in te delen.

Voor elke pagina van het formulier worden containers gemaakt met de knop **[!UICONTROL Containers]** op de werkbalk.

![](assets/s_ncs_admin_survey_containers_add.png)

Gebruik een container om elementen van de pagina te groeperen zonder een label toe te voegen aan de definitieve rendering. Elementen worden gegroepeerd in de containersubstructuur. Met standaardcontainers kunt u de lay-out beheren.

Bijvoorbeeld:

![](assets/s_ncs_admin_survey_containers_std_arbo.png)

De positie van labels wordt toegepast op elementen die onder de container in de hiërarchie worden geplaatst. Het kan voor elk element indien nodig worden overbelast. Voeg kolommen toe of verwijder kolommen om de lay-out te veranderen. Zie [De velden op de pagina plaatsen](#positioning-the-fields-on-the-page).

In het bovenstaande voorbeeld ziet de rendering er als volgt uit:

![](assets/s_ncs_admin_survey_containers_std_ex.png)

## De velden op de pagina {#positioning-the-fields-on-the-page} plaatsen

De indeling van het webformulier wordt per pagina gedefinieerd in elke container en kan zo nodig worden overgeladen.

Pagina&#39;s worden opgesplitst in kolommen: elke pagina bevat een bepaald aantal kolommen . Elk veld van de pagina neemt **n** cellen in. Containers nemen ook een bepaald aantal kolommen in en de velden die deze bevatten, bezetten een bepaald aantal cellen.

Pagina&#39;s worden standaard op één kolom gebouwd en elk element neemt één cel in beslag. Dit betekent dat velden onder elkaar worden weergegeven, waarbij elke regel een hele regel beslaat, zoals hieronder wordt getoond:

![](assets/s_ncs_admin_survey_container_ex.png)

In het volgende voorbeeld, is de standaardconfiguratie gehouden. De pagina neemt één kolom in, die vier containers bevat.

![](assets/s_ncs_admin_survey_container_ex0.png)

Elke container neemt één kolom in beslag en elk element neemt één cel in beslag:

![](assets/s_ncs_admin_survey_container_ex0a.png)

De rendering ziet er als volgt uit:

![](assets/s_ncs_admin_survey_container_ex0_rend.png)

U kunt de weergaveparameters aanpassen om de volgende rendering te verkrijgen:

![](assets/s_ncs_admin_survey_container_ex1_rend.png)

In het bovenstaande voorbeeld neemt elk invoerveld, elke titel en elke afbeelding één cel in de kolommen van de containers in.

U kunt de opmaak in elke container wijzigen. In ons voorbeeld kunt u de inhoud van container 4 over twee kolommen verspreiden en de elementen verdelen.

![](assets/s_ncs_admin_survey_container_ex2_rend.png)

De titel en de lijst beslaan elk één cel (en dus een hele regel van de container) en het selectievakje is over twee cellen verdeeld. Het aantal cellen dat aan het invoerveld wordt toegewezen, wordt op het tabblad **[!UICONTROL General]** of **[!UICONTROL Advanced]** gedefinieerd, afhankelijk van het veldtype:

![](assets/s_ncs_admin_survey_container_ex2.png)

## De positie van labels definiëren {#defining-the-position-of-labels}

U kunt de uitlijning van velden en labels in het formulier definiëren.

Standaard worden de weergaveparameters voor velden en andere inhoud van de pagina overgenomen van de algemene configuratie van het formulier, de configuratie van de pagina of de configuratie van de bovenliggende container, als deze bestaat.

De algemene weergaveparameters voor het gehele formulier worden opgegeven in het vak met formuliereigenschappen. Met het tabblad **[!UICONTROL Rendering]** kunt u de positie van labels selecteren.

![](assets/s_ncs_admin_survey_label_position.png)

Deze positie kan voor elke pagina, elke container, en elk gebied, via **[!UICONTROL Advanced]** tabel worden overbelast.

De volgende uitlijningen worden ondersteund:

* Overgenomen: de uitlijning wordt overgeërfd van het bovenliggende element (standaardwaarde), d.w.z. de bovenliggende container indien aanwezig, of anders de pagina.
* Links/rechts: het label rechts of links van het veld wordt geplaatst;
* Boven/onder: het etiket boven of onder het veld wordt geplaatst;
* Verborgen: wordt het label niet weergegeven.

