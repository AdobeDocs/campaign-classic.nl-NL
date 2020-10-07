---
title: Beheer
seo-title: Beheer
description: Beheer
seo-description: null
page-status-flag: never-activated
uuid: 376efec1-1647-43b4-b72f-2603214c7cc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 860be8be-f28c-4836-b4fb-e91c6a4616c6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 1%

---


# Beheer{#administration}

Automatisch opstarten van de Adobe Campaign-modules (**web**, **mta**, **wfserver**, enz.) wordt geleverd door de **nlserver** .

Als u Adobe Campaign installeert, wordt de computer automatisch zo geconfigureerd dat de **Nlserver** -service wordt opgestart tijdens de opstartvolgorde.

De volgende opdrachten worden gebruikt om de Adobe Campaign-service handmatig te starten en af te sluiten:

* In Windows:

   * **netwerkbeginserver6**
   * **netstop nlserver6**

* In Linux (als hoofdmap):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>Vanaf 20.1 raden we u aan in plaats daarvan de volgende opdracht te gebruiken (voor Linux): **systemCtl start nlserver** / **systemctl stop nlserver**

Hier volgt een lijst met de gebruikelijke beheeropdrachten die in Linux (zoals **Adobe Campaign**) toegankelijk zijn:

* Alle begonnen Adobe Campaign-modules weergeven: **/etc/init.d/nlserver6 pdump** of **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >Door de parameter **-who** toe te voegen aan de opdracht **pdump** kunt u informatie over de huidige verbindingen (gebruikers en processen) verzamelen.\
   >De statusopdracht **/etc/init.d/nlserver6** (zonder de parameter &quot;-who&quot;) retourneert:
   >
   >    * 0 als alle processen worden uitgevoerd.
   >    * 1 als een proces ontbreekt.
   >    * 2 als er geen proces wordt uitgevoerd.
   >    * een andere waarde als er een fout is.


* Start/stop een meervoudige instantie- of mono-instance-module (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver******,inmail):

   **nlserver start`<module>[@<instance>]`**

   **nlserver-stop`<module>[@<instance>][-immediate][-noconsole]`**

   U kunt een module ook opnieuw starten met de **opdracht Opnieuw starten`<module>[@<instance>]`** van de server.

   Voorbeeld:

   **nlserver start web**

   **nlserver start mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web-direct**

   **nlserver start web opnieuw**

   >[!NOTE]
   > 
   >    * Als de instantie niet is opgegeven, wordt de instantie &#39;default&#39; gebruikt.
   >    * In het geval van een noodsituatie, gebruik de **-directe** optie om een onmiddellijke halt toe te roepen aan het proces (gelijkwaardig aan het bevel van Unix **doden -9**).
   >    * Gebruik de optie **-noconsole** om ervoor te zorgen dat de gestarte module niets op de console zal tonen. Zijn logboeken zullen aan de schijf via de **syslogd** module worden geschreven.
   >    * Gebruik de **-uitgebreide** optie om extra informatie over procesacties te tonen.

      >    
      >      
      Voorbeeld:
      >    
      >      
      **webbreedbeeldscherm opnieuw starten**
      >    
      >      
      **nlserver start mta@myinstance -verbose**
      >    
      >      
      Met deze optie voegt u aanvullende logbestanden toe. We raden u aan om de processen opnieuw te starten zonder de optie **-verbose** zodra u de gewenste informatie hebt gevonden, om overbelasting van logbestanden te voorkomen.


* Start alle Adobe Campaign-processen op (gelijk aan het starten van de **Nlserver6** -service):

   **nlserver watchdog -noconsole**

* Sluit alle Adobe Campaign-processen af (gelijk aan het sluiten van de **Nlserver6** -service):

   **Uitschakelen van server**

* Laad de configuratie van de **nlserver** -webmodule (en de extensiemodule van de webserver, indien van toepassing) opnieuw wanneer de bestanden **serverConf.xml** en **config-`<instance>  .xml </instance>`** zijn bewerkt.

   **nlserver config-reload**

   >[!NOTE]
   >
   >Sommige configuratieveranderingen worden niet dynamisch in aanmerking genomen; Adobe Campaign moet worden afgesloten en opnieuw worden opgestart.

