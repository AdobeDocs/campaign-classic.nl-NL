---
product: campaign
title: Interaction - Databuffer
description: Interaction - Databuffer
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---

# Interaction - Databuffer{#interaction-data-buffer}

![](../../assets/v7-only.svg)

U kunt een zone van de gegevensbuffer vormen om de binnenkomende prestaties van de Interactie te verhogen door de berekeningen van de aanbiedingsvoorstel te desynchroniseren. Deze configuratie moet in het eigen configuratiedossier van de instantie (config-Instance.xml) worden uitgevoerd.

In Adobe Campaign is een **gegevensbufferzone** geïntroduceerd in de Interactiemodule. Hierdoor kunt u de prestaties van inkomende interactie **verhogen door de items te desynchroniseren en berekeningen aan te bieden.**

Het heeft slechts betrekking op binnenkomende Interactie, hetzij door een vraag (met of zonder vraaggegevens), of door een statusupdate (updateStatus).

Om een rij te vermijden wanneer het schrijven van voorstellen met betrekking tot een ontvanger, produceert een nieuw proces een **gegevensbufferzone** die voorstellen om toestaat om asynchroon **geschreven te zijn**. Deze gegevensbufferzone wordt periodiek gelezen en leeggemaakt. De standaardwaarde is ongeveer één seconde. Het schrijven van het voorstel is daarom gegroepeerd.

>[!NOTE]
>
>Deze parameter is essentieel als u Interactie met een verdeelde architectuur gebruikt.

Gegevensbufferzone **configuration** kan in het configuratiedossier van de instantie (config-Instance.xml) worden gedaan.

>[!CAUTION]
>
>Sommige configuraties kunnen slechts door Adobe voor plaatsingen worden uitgevoerd die door Adobe worden ontvangen. Bijvoorbeeld, om tot de server en de dossiers van de instantieconfiguratie toegang te hebben. Raadpleeg de sectie [Modellen hosten](../../installation/using/hosting-models.md) of [deze pagina](../../installation/using/capability-matrix.md) voor meer informatie over de verschillende implementaties.
>
>Om het even welke veranderingen die aan de configuratie worden aangebracht vereisen een nieuw begin van de Webserver (Apache:IIS) en de processen van Adobe Campaign.\
>Nadat u de gegevensbufferzone hebt geconfigureerd, moet u ervoor zorgen dat er een aangepaste hardwareconfiguratie beschikbaar is. (hoeveelheid aanwezig geheugen).


Nadat u de gegevensbufferzone hebt geconfigureerd, moet u ervoor zorgen dat er een aangepaste hardwareconfiguratie beschikbaar is. (hoeveelheid aanwezig geheugen).

De definitie voor een schrijfdaemon (proces genoemd: interactie) is als volgt:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Als u Binnenkomende interactie gebruikt, moet het @autostart-kenmerk &quot;true&quot; zijn om het proces automatisch te starten wanneer de Adobe Campaign-server wordt gestart.

Details van argument:

```
 args: Start-up parameters 
 autoStart: Automatic start Default: false 
 callDataSize: Max. number of characters stored in the shared memory for call data
 Default: 0 
 initScript: ID of JavaScript to execute when starting the process 
 maxProcessMemoryAlertMb: Alert concerning the amount of RAM consumed (in Mb) by a given process Default: 1800 
 maxProcessMemoryWarningMb: Warning concerning the amount of RAM consumed (in Mb) by a given process Default: 1600 
 maxSharedEntries: Max. number of events stored in the shared memory. Default: 25000 
 nextOffersSize: Maximum number of eligible offers sorted right after propositions, to be stored for statistics Default: 0 
 processRestartTime: Time of the day when the process is automatically restartedDefault: '06:00:00' 
 runLevel: Priority at start Default: 10 
 targetKeySize: Max. number of characters stored in the shared memory for identifying individuals Default: 16 
```
