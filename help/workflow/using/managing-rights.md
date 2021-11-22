---
product: campaign
title: Workflowmachtigingen beheren
description: Leer hoe u workflowmachtigingen beheert
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Workflowmachtigingen beheren{#managing-rights}

![](../../assets/common.svg)

Als ze geen beheerder zijn, hebben Adobe Campaign-operatoren toegangsrechten nodig voor het maken, uitvoeren of wijzigen van workflows.

In het algemeen moeten operatoren die op workflows reageren, toegang krijgen tot de bestanden met de gegevens die tijdens de verschillende activiteiten worden gebruikt (ontvangers, lijst met ontvangers, abonnementen, leveringen, enz.), en mogelijk tot hun subbestanden.

Ze moeten ook worden toegewezen aan de benoemde rechten die samenvallen met de acties die worden uitgevoerd door workflows die ze beïnvloeden (importeren van ontvangers, bestandstoegang, fusie, uitvoering van SQL-scripts, enzovoort).

Raadpleeg deze voor meer informatie over het beheren van operatoren en machtigingen [sectie](../../platform/using/access-management.md).

## Exploitantgroepen {#operator-groups-wf}

De volgende groepen operatoren zijn gekoppeld aan de workflow:

* De **[!UICONTROL Workflow execution]** Met de groep kunt u de uitvoering en goedkeuring van workflows voor doelwitten beheren: De WORKFLOW met de naam right wordt toegewezen aan de operatoren van deze groep. Dit is vereist voor alle handelingen met betrekking tot workflows, naast toegangsrechten tot de gegevensbestanden. Standaard worden de **[!UICONTROL Workflow execution]** Deze groep heeft alleen-lezen toegang tot standaard doelworkflowbestanden en werkstroomsjablonen. Operatoren in deze groep hebben ook lees- en schrijftoegang tot het goedkeuringsbestand dat in behandeling is.
* De **[!UICONTROL Workflow supervisors]** in groep kunnen operatoren workflowgoedkeuringen beheren.
* De **[!UICONTROL Operation Managers]** groeperen voor toegang tot workflows voor campagnes.

## Benoemde rechten {#named-rights}

Alleen de WORKFLOW met de naam right is specifiek voor workflows: hiermee kunt u workflows maken, starten en stoppen. Het genoemde recht is alleen van toepassing als het workflowbestand leesrechten bevat. Voor doelgerichte workflows kunt u de leesvolgorde op de knop **[!UICONTROL Profiles and Targets]** bestand is noodzakelijk.

## Workflow-uitvoeringsaccount {#workflow-execution-account}

U kunt de uitvoeringsrekening vormen die op het niveau van het werkschemamalplaatje moet worden gebruikt. Met de uitvoeringsaccount kunt u machtigingen rechtstreeks aan de workflow toewijzen, ongeacht de Adobe Campaign-operator die de uitvoering start. Standaard wordt elke workflow uitgevoerd met de rechten van de operator die de workflow heeft gestart.

Als u een uitvoeringsaccount wilt toewijzen aan een workflow, gaat u naar de lijst met workflowsjablonen en klikt u met de rechtermuisknop op de sjabloon die is gekoppeld aan de workflow. Kies **[!UICONTROL Action > Change execution account...]** Selecteer vervolgens de account die u wilt gebruiken.
