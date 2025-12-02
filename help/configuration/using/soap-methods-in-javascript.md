---
product: campaign
title: SOAP-methoden in JavaScript
feature: Configuration, Instance Settings
description: SOAP-methoden in JavaScript
role: Developer
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 9%

---

# SOAP-methoden in JavaScript{#soap-methods-in-javascript}

Dit is de JavaScript die wordt uitgevoerd op de Adobe Campaign-server.

## Statische methoden {#static-methods}

Statische SOAP-methoden worden benaderd door een methode aan te roepen voor het object dat het schema vertegenwoordigt. Schema&#39;s zijn eigenschappen van &#39;namespace&#39;-objecten. Deze naamruimten zijn algemene variabelen, zodat bijvoorbeeld xtk- of nms-variabelen de overeenkomende naamruimten vertegenwoordigen

Het volgende voorbeeld roept de statische methode PostEvent van het xtk :workflow schema aan:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Niet-statische methoden {#non-static-methods}

Als u niet-statische SOAP-methoden wilt gebruiken, moet u eerst een entiteit ophalen met de methoden &quot;get&quot; of &quot;create&quot; op de corresponderende schema&#39;s.

In het volgende voorbeeld wordt de methode ExecuteQuery van het schema &quot;xtk :queryDef&quot; aangeroepen:

```
var query = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
    </select>
  </queryDef>
)

var res = query.ExecuteQuery()

for each (var w in res.workflow) 
  logInfo(w.@internalName)
```

## Voorbeelden {#examples}

* Vraag op de ontvankelijke lijst met &quot;krijgt&quot;verrichting:

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="get">    
      <select>      
        <node expr="@firstName"/>      
        <node expr="@lastName"/>      
        <node expr="@email"/>    
      </select>    
      <where>      
        <condition expr="@email = 'peter.martinez@adobe.com'"/>    
      </where>  
    </queryDef>)
  
  var recipient = query.ExecuteQuery()
  
  logInfo(recipient.@firstName)
  logInfo(recipient.@lastName)
  ```

* Vraag op de ontvankelijke lijst met &quot;uitgezochte&quot;verrichting:

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="select">    
      <select>      
        <node expr="@email"/>      
        <node expr="@lastName"/>      
        <node expr="@firstName"/>    
      </select>    
      <where>      
        <condition expr="@age > 25"/>    
      </where>    
    </queryDef>)
  
  var res = query.ExecuteQuery()
  
  for each (var recipient in res.recipient) 
  {  
    logInfo(recipient.@email)  
    logInfo(recipient.@firstName)  
    logInfo(recipient.@lastName)
  }
  ```

* Gegevens naar de tabel met ontvangers schrijven:

  ```
  xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
  ```
