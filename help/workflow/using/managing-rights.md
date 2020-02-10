---
title: Rechten beheren
seo-title: Rechten beheren
description: Rechten beheren
seo-description: null
page-status-flag: never-activated
uuid: 07039fec-c957-4548-acc7-22dc7827a54b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f78603e9-f6ff-4ebe-941b-b3fbd1924b71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Rechten beheren{#managing-rights}

Als ze geen beheerder zijn, hebben Adobe Campagnebeheerders toegangsrechten nodig voor het maken, uitvoeren of wijzigen van workflows.

In het algemeen moeten operatoren die op workflows reageren, toegang krijgen tot de bestanden met de gegevens die tijdens de verschillende activiteiten worden gebruikt (ontvangers, lijst met ontvangers, abonnementen, leveringen, enz.), en mogelijk tot hun subbestanden.

Ze moeten ook worden toegewezen aan de benoemde rechten die samenvallen met de acties die worden uitgevoerd door workflows die ze beïnvloeden (importeren van ontvangers, bestandstoegang, fusie, uitvoering van SQL-scripts, enzovoort).

Raadpleeg deze [sectie](../../platform/using/access-management.md)voor meer informatie over het beheren van operatoren en machtigingen.

## Exploitantgroepen {#operator-groups}

De volgende groepen operatoren zijn gekoppeld aan de workflow:

* Met de **[!UICONTROL Workflow execution]** groep kunt u de uitvoering en goedkeuring van doelworkflows beheren: De WORKFLOW met de naam right wordt toegewezen aan de operatoren van deze groep. Dit is vereist voor alle handelingen met betrekking tot workflows, naast toegangsrechten tot de gegevensbestanden. Standaard heeft de **[!UICONTROL Workflow execution]** groep alleen-lezen toegang tot standaarddoelworkbestanden en werkstroomsjablonen. Operatoren in deze groep hebben ook lees- en schrijftoegang tot het goedkeuringsbestand dat in behandeling is.
* De **[!UICONTROL Workflow supervisors]** groep laat exploitanten werkschemagoedkeuringen beheren.
* De **[!UICONTROL Operation Managers]** groep voor toegang tot workflows voor campagnes.

## Benoemde rechten {#named-rights}

Alleen de WORKFLOW met de naam right is specifiek voor workflows: hiermee kunt u workflows maken, starten en stoppen. Het genoemde recht is alleen van toepassing als het workflowbestand leesrechten bevat. Voor doelworkflows is het lezen van het **[!UICONTROL Profiles and Targets]** bestand naar rechts nodig.

## Workflow-uitvoeringsaccount {#workflow-execution-account}

U kunt de uitvoeringsrekening vormen die op het niveau van het werkschemamalplaatje moet worden gebruikt. Met de uitvoeringsaccount kunt u machtigingen rechtstreeks aan de workflow toewijzen, ongeacht de Adobe Campaign-operator die de uitvoering start. Standaard wordt elke workflow uitgevoerd met de rechten van de operator die de workflow heeft gestart.

Als u een uitvoeringsaccount wilt toewijzen aan een workflow, gaat u naar de lijst met workflowsjablonen en klikt u met de rechtermuisknop op de sjabloon die is gekoppeld aan de workflow. Kies **[!UICONTROL Action > Change execution account...]** vervolgens het account dat u wilt gebruiken.
