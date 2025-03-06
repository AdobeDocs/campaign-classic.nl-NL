---
product: campaign
title: Gepersonaliseerde waarschuwingen verzenden naar operatoren
description: Leer hoe u persoonlijke waarschuwingen naar operatoren kunt sturen
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 2%

---

# Gepersonaliseerde waarschuwingen verzenden naar operatoren{#sending-personalized-alerts-to-operators}



In dit voorbeeld willen wij een alarm naar een exploitant verzenden die de naam van profielen zal bevatten die een nieuwsbrief opende maar niet de verbinding klikte het bevat.

De velden voor de voornaam en achternaam van de profielen zijn gekoppeld aan de doeldimensie van **[!UICONTROL Recipients]** , terwijl de activiteit van **[!UICONTROL Alert]** is gekoppeld aan de doeldimensie van **[!UICONTROL Operator]** . Als gevolg hiervan is er geen veld beschikbaar tussen de twee doeldimensies om een afstemming uit te voeren en de velden voor de voornaam en achternaam op te halen en deze weer te geven in de activiteit Waarschuwing.

Het proces bestaat uit het samenstellen van een workflow zoals hieronder beschreven:

1. Gebruik een **[!UICONTROL Query]** -activiteit om gegevens als doel in te stellen.
1. Voeg een **[!UICONTROL JavaScript code]** activiteit in het werkschema toe om de bevolking van de vraag aan de instantievariabele te bewaren.
1. Gebruik een **[!UICONTROL Test]** -activiteit om het aantal inwoners te controleren.
1. Gebruik een **[!UICONTROL Alert]** -activiteit om een waarschuwing naar een operator te sturen, afhankelijk van het **[!UICONTROL Test]** -resultaat.

![](assets/uc_operator_1.png)

## De populatie opslaan in de instantievariabele {#saving-the-population-to-the-instance-variable}

Voeg de onderstaande code toe aan de **[!UICONTROL JavaScript code]** -activiteit.

```
var query = xtk.queryDef.create(  
    <queryDef schema="temp:query" operation="select">  
      <select>  
       <node expr="[target/recipient.@firstName]"/>  
       <node expr="[target/recipient.@lastName]"/>  
      </select>  
     </queryDef>  
  );  
  var items = query.ExecuteQuery();
```

Zorg ervoor dat de Javascript-code overeenkomt met uw workflowgegevens:

* De tag **[!UICONTROL queryDef schema]** moet overeenkomen met de naam van de doeldimensie die wordt gebruikt in de queryactiviteit.
* De tag **[!UICONTROL node expr]** moet overeenkomen met de naam van de velden die u wilt ophalen.

![](assets/uc_operator_3.png)

Volg onderstaande stappen om deze gegevens op te halen:

1. Klik met de rechtermuisknop op de uitgaande overgang van de **[!UICONTROL Query]** -activiteit en selecteer vervolgens **[!UICONTROL Display the target]** .

   ![](assets/uc_operator_4.png)

1. Klik met de rechtermuisknop op de lijst en selecteer vervolgens **[!UICONTROL Configure list]** .

   ![](assets/uc_operator_5.png)

1. De query voor dimensie en veldnamen wordt in de lijst weergegeven.

   ![](assets/uc_operator_6.png)

## Het aantal inwoners testen {#testing-the-population-count}

Voeg de onderstaande code toe aan de **[!UICONTROL Test]** -activiteit om te controleren of de doelpopulatie ten minste 1 profiel bevat.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## De waarschuwing instellen {#setting-up-the-alert}

Nu de populatie is toegevoegd aan de instantievariabele met de gewenste gebieden, kunt u deze informatie in de **[!UICONTROL Alert]** activiteit toevoegen.

Voeg hiertoe op het tabblad **[!UICONTROL Source]** de onderstaande code toe:

```
<ul>
<%
var items = new XML(instance.vars.items)
for each (var item in items){
%>
<li><%= item.target.@firstName %> <%= item.target.@lastName %></li>
<%
} %></ul>
```

>[!NOTE]
>
>Met de opdracht **[!UICONTROL <%= item.target.recipient.@fieldName %>]** kunt u een van de velden toevoegen die via de **[!UICONTROL JavaScript code]** -activiteit zijn opgeslagen in de instantievariabele.\
>U kunt zo veel velden toevoegen als u wilt, zolang deze maar in de JavaScript-code zijn ingevoegd.

![](assets/uc_operator_8.png)
