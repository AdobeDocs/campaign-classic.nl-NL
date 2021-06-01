---
product: campaign
title: Workflowmachtigingen beheren
description: Leer hoe u workflowmachtigingen beheert
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Workflowmachtigingen beheren{#managing-rights}

Als ze geen beheerder zijn, hebben Adobe Campaign-operatoren toegangsrechten nodig voor het maken, uitvoeren of wijzigen van workflows.

In het algemeen moeten operatoren die op workflows reageren, toegang krijgen tot de bestanden met de gegevens die tijdens de verschillende activiteiten worden gebruikt (ontvangers, lijst met ontvangers, abonnementen, leveringen, enz.), en mogelijk tot hun subbestanden.

Ze moeten ook worden toegewezen aan de benoemde rechten die samenvallen met de acties die worden uitgevoerd door workflows die ze beïnvloeden (importeren van ontvangers, bestandstoegang, fusie, uitvoering van SQL-scripts, enzovoort).

Voor meer over het beheren van exploitanten en toestemmingen, verwijs naar dit [sectie](../../platform/using/access-management.md).

## Exploitantgroepen {#operator-groups-wf}

De volgende groepen operatoren zijn gekoppeld aan de workflow:

* Met de groep **[!UICONTROL Workflow execution]** kunt u de uitvoering en goedkeuring van doelworkflows beheren: De WORKFLOW met de naam right wordt toegewezen aan de operatoren van deze groep. Dit is vereist voor alle handelingen met betrekking tot workflows, naast toegangsrechten tot de gegevensbestanden. Standaard heeft de groep **[!UICONTROL Workflow execution]** alleen-lezen toegang tot standaard doelworkflowbestanden en werkstroomsjablonen. Operatoren in deze groep hebben ook lees- en schrijftoegang tot het goedkeuringsbestand dat in behandeling is.
* Met de groep **[!UICONTROL Workflow supervisors]** kunnen operatoren workflowgoedkeuringen beheren.
* De **[!UICONTROL Operation Managers]** groep om tot campagnewerkschema&#39;s toegang te hebben.

## Benoemde rechten {#named-rights}

Alleen de WORKFLOW met de naam right is specifiek voor workflows: hiermee kunt u workflows maken, starten en stoppen. Het genoemde recht is alleen van toepassing als het workflowbestand leesrechten bevat. Voor het richten van werkschema&#39;s, is het lezen recht op het **[!UICONTROL Profiles and Targets]** dossier noodzakelijk.

## Rekening {#workflow-execution-account} voor workflowuitvoering

U kunt de uitvoeringsrekening vormen die op het niveau van het werkschemamalplaatje moet worden gebruikt. Met de uitvoeringsaccount kunt u machtigingen rechtstreeks aan de workflow toewijzen, ongeacht de Adobe Campaign-operator die de uitvoering start. Standaard wordt elke workflow uitgevoerd met de rechten van de operator die de workflow heeft gestart.

Als u een uitvoeringsaccount wilt toewijzen aan een workflow, gaat u naar de lijst met workflowsjablonen en klikt u met de rechtermuisknop op de sjabloon die is gekoppeld aan de workflow. Kies **[!UICONTROL Action > Change execution account...]** en selecteer het account dat u wilt gebruiken.
