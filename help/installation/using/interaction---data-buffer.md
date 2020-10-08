---
title: Interactie - Databuffer
seo-title: Interactie - Databuffer
description: Interactie - Databuffer
seo-description: null
page-status-flag: never-activated
uuid: 4cb742b5-6bde-43e8-b26b-16f27dd65f72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: cbfdeb2f-4f20-45b8-8cc0-89362f9ea9c1
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 6%

---


# Interactie - Databuffer{#interaction-data-buffer}

>[!NOTE]
>
>Sommige configuraties kunnen slechts door Adobe voor plaatsingen worden uitgevoerd die door Adobe worden ontvangen. Bijvoorbeeld, om tot de server en de dossiers van de instantieconfiguratie toegang te hebben. Meer over de verschillende plaatsingen leren, verwijs naar de [Hosting modelsectie](../../installation/using/hosting-models.md) of naar [dit artikel](https://helpx.adobe.com/nl/campaign/kb/acc-on-prem-vs-hosted.html).

In Adobe Campaign is een **gegevensbufferzone** geïntroduceerd in de module Interactie. Dit staat u toe om prestaties **van binnenkomende Interactie te** verhogen door voorraad en aanbiedingsberekeningen te desynchroniseren.

Het heeft slechts betrekking op binnenkomende Interactie, hetzij door een vraag (met of zonder vraaggegevens), of door een statusupdate (updateStatus).

Om een rij te vermijden wanneer het schrijven van voorstellen met betrekking tot een ontvanger, produceert een nieuw proces een **gegevensbufferzone** die voorstellen om asynchroon **te** schrijven toestaat. Deze gegevensbufferzone wordt periodiek gelezen en leeggemaakt. De standaardwaarde is ongeveer één seconde. Het schrijven van het voorstel is daarom gegroepeerd.

De **configuratie** van de de bufferzone van gegevens kan in het configuratiedossier van de instantie (config-Instance.xml) worden gedaan.

>[!NOTE]
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

