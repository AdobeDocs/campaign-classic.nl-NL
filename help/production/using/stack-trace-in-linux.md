---
title: Stacktracering in Linux
seo-title: Stacktracering in Linux
description: Stacktracering in Linux
seo-description: null
page-status-flag: never-activated
uuid: d839df47-902f-4b92-bc78-536fc4fb6c98
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 60f306ea-4593-4e56-896e-8933277ee26a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 14%

---


# Stacktracering in Linux{#stack-trace-in-linux}

Een **stapelspoor** vertegenwoordigt een spoor in een **kerntypedossier** . Dit bestand wordt gegenereerd als er een computerfout optreedt. De oorsprong van de fout kan worden geïdentificeerd.

>[!NOTE]
>
>* Een **kernbestand** krijgt de naam **core.`<num>`**.
>* **gdb - De GNU-foutopsporing** moet op de computer zijn geïnstalleerd.

>



Technische ondersteuning van Adobe Campaign kan u vragen om deze **stacktracering**. Voer de volgende opdrachten in Linux in om deze te verkrijgen:

```
su - neolane
gdb nlserver <coreFile>
//You get lots of output but the stack trace (or Back trace) can be obtained with : 
(gdb) bt
// and forward all the output : 
#0 0x0836c189 in ObjectValue::SetPropertyTarget ()
#1 0x082623b3 in CXtkScriptProperty::VDeclareProperties ()
#2 0x0826a835 in CXtkScriptContext::OnGetProperty ()
#3 0x08370b3d in JavaScriptGetProperty ()
#4 0x557b8aa7 in js_Interpret () from /usr/local/neolane/nl6/lib/libmozjs.so
#5 0x557afb97 in js_Execute () from /usr/local/neolane/nl6/lib/libmozjs.so
#6 0x5578921f in JS_ExecuteScript () from /usr/local/neolane/nl6/lib/libmozjs.so
#7 0x08370468 in JavaScriptSource::Evaluate ()
#8 0x0848fa03 in JSTDeliveryContext::ProcessScript ()
#9 0x0848fcb6 in JSTDeliveryContext::ProcessTemplate ()
#10 0x08460d2b in CDeliveryToolbox::CreateMailMessage ()
#11 0x080d51fe in CMtaQueue::PrepareMessages ()
#12 0x080d2b07 in CMtaQueue::Prepare ()
#13 0x080dca38 in CMtaChild::OnRun ()
#14 0x0814792c in ThreadStartRoutine ()
#15 0x55575b63 in start_thread () from /lib/tls/libpthread.so.0
#16 0x5565918a in clone () from /lib/tls/libc.so.6
```

De technische steun van Adobe Campaign zou u kunnen vragen om dit bevel in werking te stellen gebruikend specifiek uitvoerbaar (door ons te leveren).

In dit geval voert u gewoon de volgende opdracht uit door **nlserver** te vervangen door het uitvoerbare bestand dat door Adobe Campaign wordt geleverd:

```
gdb nlserver <coreFile>
```

Bijvoorbeeld:

```
gdb nlserver.1823 <coreFile>
```

