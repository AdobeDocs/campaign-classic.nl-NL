---
title: Interactie - Gegevensbuffer
seo-title: Interactie - Gegevensbuffer
description: Interactie - Gegevensbuffer
seo-description: null
page-status-flag: never-activated
uuid: 4cb742b5-6bde-43e8-b26b-16f27dd65f72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: cbfdeb2f-4f20-45b8-8cc0-89362f9ea9c1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Interactie - Gegevensbuffer{#interaction-data-buffer}

>[!NOTE]
>
>Sommige configuraties kunnen alleen door Adobe worden uitgevoerd voor implementaties die worden gehost door Adobe. Bijvoorbeeld, om tot de server en de dossiers van de instantieconfiguratie toegang te hebben. Meer over de verschillende plaatsingen leren, verwijs naar de [Hosting modelsectie](../../installation/using/hosting-models.md) of naar [dit artikel](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

In de Campagne van Adobe, is een gebied **van de** gegevensbuffer geïntroduceerd in de module van de Interactie. Dit staat u toe om prestaties **van binnenkomende Interactie te** verhogen door voorraad en aanbiedingsberekeningen te desynchroniseren.

Het heeft slechts betrekking op binnenkomende Interactie, hetzij door een vraag (met of zonder vraaggegevens), of door een statusupdate (updateStatus).

Om een rij te vermijden wanneer het schrijven van voorstellen met betrekking tot een ontvanger, produceert een nieuw proces een **gegevensbufferzone** die voorstellen om asynchroon **te** schrijven toestaat. Deze gegevensbufferzone wordt periodiek gelezen en leeggemaakt. De standaardwaarde is ongeveer één seconde. Het schrijven van het voorstel is daarom gegroepeerd.

De **configuratie** van de de bufferzone van gegevens kan in het configuratiedossier van de instantie (config-Instance.xml) worden gedaan.

>[!NOTE]
>
>Voor alle wijzigingen die in de configuratie worden aangebracht, moeten de webserver (Apache:IIS) en de Adobe Campagne-processen opnieuw worden gestart.\
>Nadat u de gegevensbufferzone hebt geconfigureerd, moet u ervoor zorgen dat er een aangepaste hardwareconfiguratie beschikbaar is. (hoeveelheid aanwezig geheugen).

Nadat u de gegevensbufferzone hebt geconfigureerd, moet u ervoor zorgen dat er een aangepaste hardwareconfiguratie beschikbaar is. (hoeveelheid aanwezig geheugen).

De definitie voor een schrijfdaemon (proces genoemd: interactie) is als volgt:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Als u Binnenkomende interactie gebruikt, moet het @autostart-kenmerk &quot;true&quot; zijn om het proces automatisch te starten wanneer de Adobe Campagneserver wordt gestart.

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

