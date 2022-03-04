---
product: campaign
title: Geavanceerde parameters
description: Geavanceerde parameters
feature: Workflows, Data Management
exl-id: 6c90ac2f-0d2b-48b0-9245-3e5e3a3d027c
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 1%

---

# Geavanceerde parameters{#advanced-parameters}

![](../../assets/common.svg)

Het eigenschappenscherm van een activiteit heeft een **[!UICONTROL Advanced]** tabblad waarin u een gedrag kunt definiëren in het geval van fouten, de uitvoeringsperiode voor de activiteit; en kunt u een initialisatiescript invoeren. Er zijn twee versies van dit tabblad:

* een vereenvoudigde versie (voor **[!UICONTROL Start]** en **[!UICONTROL End]** activiteiten, bijvoorbeeld)

   ![](assets/wf-advanced-basic.png)

* een meer gedetailleerde versie ( voor de **[!UICONTROL Query]** activiteit, bijvoorbeeld)

   ![](assets/wf-advanced-full.png)

De velden die moeten worden ingevoerd in het **[!UICONTROL Advanced]** worden in de volgende secties beschreven.

## Naam {#name}

Dit veld bevat de interne naam van de activiteit.

## Afbeelding {#image}

In dit veld kunt u de afbeelding wijzigen die aan een activiteit is gekoppeld. Raadpleeg voor meer informatie hierover [Activiteitenafbeeldingen wijzigen](managing-activity-images.md).

## Execution {#execution}

In dit veld kunt u de actie definiëren die moet worden uitgevoerd wanneer de taak wordt geactiveerd. Er zijn drie mogelijke opties:

Deze opties worden over het algemeen geselecteerd in het winkelwagentje door met de rechtermuisknop op de activiteit te klikken.

* **[!UICONTROL Normal]**: de activiteit wordt uitgevoerd zoals gebruikelijk.
* **[!UICONTROL Do not activate]**: deze taak en alle volgende taken (in dezelfde vertakking) worden niet uitgevoerd.
* **[!UICONTROL Activate but do not execute]**: deze taak en alle volgende taken (in dezelfde vertakking) worden automatisch gestopt. Dit kan handig zijn als u er wilt zijn wanneer de taak wordt gestart. Als u de taak handmatig wilt uitvoeren, klikt u met de rechtermuisknop op de activiteit en selecteert u **[!UICONTROL Normal execution]**.

## affiniteit {#affinity}

U kunt ervoor kiezen de uitvoering van een workflow of workflowactiviteit op een specifieke computer af te dwingen. Hiervoor moet u een of meer eigenschappen definiëren op het niveau van de workflow of de desbetreffende activiteit.

De configuratie van de workflow voor hoge beschikbaarheid wordt in dit [sectie](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).


## Max. uitvoeringstermijn {#max--execution-period}

In dit veld kunt u een waarschuwing instellen wanneer de taak te lang duurt. Het heeft geen invloed op de workflowbewerking. Als de taak niet tegen tijd wordt gebeëindigd **[!UICONTROL Max. execution period]** is voorbij, de **[!UICONTROL Instance monitoring]** Er verschijnt een waarschuwing voor deze workflow. Deze pagina is toegankelijk via de **[!UICONTROL Monitoring]** van de startpagina.

## Gedrag {#behavior}

In dit veld kunt u het gedrag definiëren dat moet worden toegepast bij het gebruik van asynchrone taken. Er zijn twee mogelijke opties:

* **[!UICONTROL Several tasks authorized]**: verscheidene taken kunnen tegelijkertijd worden uitgevoerd, zelfs als eerste niet gebeëindigd is.
* **[!UICONTROL The current task has priority]**: de lopende taken hebben voorrang . Zolang een taak bezig is, zal geen andere taak worden uitgevoerd.

## Tijdzone {#time-zone}

In dit veld kunt u de tijdzone van de activiteit selecteren. Voor meer informatie hierover: [Tijdzones beheren](managing-time-zones.md).

## Bij fouten {#in-case-of-errors}

In dit veld kunt u de actie definiëren die moet worden uitgevoerd wanneer de activiteit fouten bevat. Er zijn twee mogelijke opties:

* **[!UICONTROL Suspend the process]**: de workflow wordt automatisch gestopt. Zijn status verandert in **[!UICONTROL Failed]**. Als het probleem is opgelost, start u de workflow opnieuw.
* **[!UICONTROL Ignore]**: deze taak en alle volgende taken (in dezelfde vertakking) worden niet uitgevoerd. Dit kan handig zijn voor terugkerende taken. Als de tak een eerder geplaatste planner heeft, zal het zoals gewoonlijk op de volgende uitvoeringsdatum beginnen.
* **[!UICONTROL Abort on error]**: de workflow wordt automatisch gestopt en kan niet opnieuw worden gestart. Zijn status verandert in **[!UICONTROL Failed]**.

## Initialisatiescript {#initialization-script}

In dit veld kunt u variabelen initialiseren of eigenschappen van activiteit wijzigen. Raadpleeg voor meer informatie: [JavaScript-scripts en -sjablonen](javascript-scripts-and-templates.md).

## Opmerking {#comment}

De **[!UICONTROL Comment]** Veld is een gratis veld waarmee u een beschrijving kunt toevoegen.
