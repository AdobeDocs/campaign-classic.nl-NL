---
solution: Campaign Classic
product: campaign
title: Gepersonaliseerde waarschuwingen verzenden naar operatoren
description: Leer hoe u persoonlijke waarschuwingen naar operatoren kunt sturen
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---


# Gepersonaliseerde waarschuwingen verzenden naar operatoren{#sending-personalized-alerts-to-operators}

In dit voorbeeld willen wij een alarm naar een exploitant verzenden die de naam van profielen zal bevatten die een nieuwsbrief opende maar niet de verbinding klikte het bevat.

De voornaam- en achternaamvelden van de profielen zijn gekoppeld aan de **[!UICONTROL Recipients]**-doeldimensie, terwijl de **[!UICONTROL Alert]**-activiteit is gekoppeld aan de **[!UICONTROL Operator]**-doeldimensie. Als gevolg hiervan is er geen veld beschikbaar tussen de twee doeldimensies om een afstemming uit te voeren en de velden voor de voornaam en achternaam op te halen en deze weer te geven in de activiteit Waarschuwing.

Het proces bestaat uit het ontwikkelen van een workflow zoals hieronder:

1. Gebruik een **[!UICONTROL Query]** activiteit om gegevens te richten.
1. Voeg een **[!UICONTROL JavaScript code]** activiteit in het werkschema toe om de bevolking van de vraag aan de instantievariabele te bewaren.
1. Gebruik een **[!UICONTROL Test]** activiteit om het aantal populaties te controleren.
1. Gebruik een **[!UICONTROL Alert]** activiteit om een alarm naar een exploitant, afhankelijk van het **[!UICONTROL Test]** activiteitenresultaat te verzenden.

![](assets/uc_operator_1.png)

## De populatie opslaan in de instantievariabele {#saving-the-population-to-the-instance-variable}

Voeg de code hieronder in **[!UICONTROL JavaScript code]** activiteit toe.

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

* De **[!UICONTROL queryDef schema]** markering zou aan de naam van de het richten dimensie moeten beantwoorden die in de vraagactiviteit wordt gebruikt.
* De tag **[!UICONTROL node expr]** moet overeenkomen met de naam van de velden die u wilt ophalen.

![](assets/uc_operator_3.png)

Volg onderstaande stappen om deze gegevens op te halen:

1. Klik met de rechtermuisknop op de uitgaande overgang van de activiteit **[!UICONTROL Query]** en selecteer **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. Klik met de rechtermuisknop op de lijst en selecteer **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. De query voor dimensie en veldnamen wordt in de lijst weergegeven.

   ![](assets/uc_operator_6.png)

## Het aantal populaties testen {#testing-the-population-count}

Voeg de code hieronder in **[!UICONTROL Test]** activiteit toe om te controleren of bevat de gerichte bevolking minstens 1 profiel.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## De waarschuwing {#setting-up-the-alert} instellen

Nu de populatie aan de instantievariabele met de gewenste gebieden is toegevoegd, kunt u deze informatie in **[!UICONTROL Alert]** activiteit toevoegen.

Hiervoor voegt u op het tabblad **[!UICONTROL Source]** de onderstaande code toe:

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
>Met de opdracht **[!UICONTROL <%= item.target.recipient.@fieldName %>]** kunt u een van de velden toevoegen die via de activiteit **[!UICONTROL JavaScript code]** aan de instantievariabele zijn opgeslagen.\
>U kunt zo veel velden toevoegen als u wilt, mits deze zijn ingevoegd in de JavaScript-code.

![](assets/uc_operator_8.png)

