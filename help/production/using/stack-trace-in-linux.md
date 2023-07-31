---
product: campaign
title: Stacktracering in Linux
description: Stacktracering in Linux
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 91662d6d-2177-4440-b31f-7b031bd953cb
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 16%

---

# Stacktracering in Linux{#stack-trace-in-linux}



A **stacktracering** vertegenwoordigt een spoor in een **kern** tekstbestand. Dit bestand wordt gegenereerd als er een computerfout optreedt. De oorsprong van de fout kan worden geïdentificeerd.

>[!NOTE]
>
>* A **kern** bestand heeft een naam **kern.`<num>`**.
>* **gdb - De GNU-foutopsporing** moet op de computer zijn geïnstalleerd.
>

Technische ondersteuning van Adobe Campaign kan u hierom vragen **stacktracering**. Voer de volgende opdrachten in Linux in om deze te verkrijgen:

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

In dit geval voert u gewoon de volgende opdracht uit door **nlserver** met het uitvoerbare bestand van Adobe Campaign:

```
gdb nlserver <coreFile>
```

Bijvoorbeeld:

```
gdb nlserver.1823 <coreFile>
```
