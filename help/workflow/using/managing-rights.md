---
solution: Campaign Classic
product: campaign
title: Rechten beheren
description: Rechten beheren
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 1%

---


# Rechten beheren{#managing-rights}

Als ze geen beheerder zijn, hebben Adobe Campaign-operatoren toegangsrechten nodig voor het maken, uitvoeren of wijzigen van workflows.

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
