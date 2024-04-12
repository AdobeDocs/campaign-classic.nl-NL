---
product: campaign
title: Interactie - Gegevensbuffer
description: Interactie - Gegevensbuffer
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Interactie - Gegevensbuffer{#interaction-data-buffer}



U kunt een zone van de gegevensbuffer vormen om de binnenkomende prestaties van de Interactie te verhogen door de berekeningen van de aanbiedingsvoorstel te desynchroniseren. Deze configuratie moet in het eigen configuratiedossier van de instantie (config-Instance.xml) worden uitgevoerd.

In Adobe Campaign **gegevensbufferzone** is geïntroduceerd in de module Interactie. Hierdoor kunt u **hogere prestaties** van inkomende Interactie door voorraad en aanbiedingsberekeningen te desynchroniseren.

Het heeft slechts betrekking op binnenkomende Interactie, hetzij door een vraag (met of zonder vraaggegevens), of door een statusupdate (updateStatus).

Om een rij te vermijden wanneer het schrijven van voorstellen met betrekking tot een ontvanger, produceert een nieuw proces een **gegevensbufferzone** dat het mogelijk maakt voorstellen te doen **asynchroon geschreven**. Deze gegevensbufferzone wordt periodiek gelezen en leeggemaakt. De standaardwaarde is ongeveer één seconde. Het schrijven van het voorstel is daarom gegroepeerd.

>[!NOTE]
>
>Deze parameter is essentieel als u Interactie met een verdeelde architectuur gebruikt.

Gegevensbufferzone **configuratie** kan in het de configuratiedossier van de instantie (config-Instance.xml) worden gedaan.

>[!CAUTION]
>
>Sommige configuraties kunnen slechts door Adobe voor plaatsingen worden uitgevoerd die door Adobe worden ontvangen. Bijvoorbeeld, om tot de server en de dossiers van de instantieconfiguratie toegang te hebben. Voor meer informatie over de verschillende implementaties raadpleegt u de [Hostmodellen](../../installation/using/hosting-models.md) van [deze pagina](../../installation/using/capability-matrix.md).
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
