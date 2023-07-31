---
product: campaign
title: SOAP-methoden in JavaScript
feature: Configuration, Instance Settings
description: SOAP-methoden in JavaScript
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 9%

---

# SOAP-methoden in JavaScript{#soap-methods-in-javascript}

Dit is het JavaScript dat op de Adobe Campaign-server wordt uitgevoerd.

## Statische methoden {#static-methods}

De statische methodes van de ZEEP worden betreden door een methode op het voorwerp aan te halen dat het schema vertegenwoordigt. Schema&#39;s zijn eigenschappen van &#39;namespace&#39;-objecten. Deze naamruimten zijn algemene variabelen, zodat bijvoorbeeld xtk- of nms-variabelen de overeenkomende naamruimten vertegenwoordigen

In het volgende voorbeeld wordt de statische PostEvent-methode van het schema xtk:workflow aangeroepen:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Niet-statische methoden {#non-static-methods}

Om niet-statische methodes van de ZEEP te gebruiken, is het noodzakelijk eerst om een entiteit terug te winnen gebruikend &quot;krijgen&quot;of &quot;creeer&quot;methodes op de overeenkomstige schema&#39;s.

In het volgende voorbeeld wordt de methode ExecuteQuery van het schema &quot;xtk:queryDef&quot; aangeroepen:

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
