---
solution: Campaign Classic
product: campaign
title: Beheer
description: Beheer
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 9c78d8f469bade41717eb854e8cec00859c1d4e3
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# Beheer{#administration}

Automatisch opstarten van de Adobe Campaign-modules (**web**, **mta**, **wfserver**, enz.) wordt geleverd door de **nlserver**-server.

Als u Adobe Campaign installeert, wordt de computer automatisch zo geconfigureerd dat de **nlserver**-service wordt opgestart tijdens de opstartprocedure.

De volgende opdrachten worden gebruikt om de Adobe Campaign-service handmatig te starten en af te sluiten:

* In Windows:

   * **netwerkbeginserver6**
   * **netstop nlserver6**

* In Linux (als hoofdmap):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>Vanaf 20.1 raden we u aan in plaats daarvan de volgende opdracht te gebruiken (voor Linux): **systemctl start nlserver** / **systemctl stop nlserver**

Hier volgt een lijst met de gebruikelijke beheeropdrachten die in Linux toegankelijk zijn (zoals **Adobe Campaign**):

* Alle begonnen Adobe Campaign-modules weergeven: **/etc/init.d/nlserver6 pdump** of **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >Door de parameter **-who** toe te voegen aan de opdracht **pdump** kunt u informatie verzamelen over de huidige verbindingen (gebruikers en processen).\
   >De opdracht **/etc/init.d/nlserver6 status** (zonder de parameter &quot;-who&quot;) retourneert:
   >
   >    * 0 als alle processen worden uitgevoerd.
   >    * 1 als een proces ontbreekt.
   >    * 2 als er geen proces wordt uitgevoerd.
   >    * een andere waarde als er een fout is.


* Een module voor meerdere instanties of mono-instanties starten/stoppen (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

   **nlserver start`<module>[@<instance>]`**

   **nlserver-stop`<module>[@<instance>][-immediate][-noconsole]`**

   U kunt ook de opdracht **Nlserver opnieuw starten`<module>[@<instance>]`** gebruiken om een module opnieuw te starten.

   Voorbeeld:

   **nlserver start web**

   **nlserver start mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web-direct**

   **nlserver start web opnieuw**

   >[!NOTE]
   >
   >* Als de instantie niet is opgegeven, wordt de instantie &#39;default&#39; gebruikt.
   >* In het geval van een noodsituatie, gebruik **-direct** optie om een directe stilstand aan het proces (gelijkwaardig aan het bevel van Unix **te dwingen - 9**).
   >* Gebruik de optie **-noconsole** om ervoor te zorgen dat de gestarte module niets op de console zal tonen. Zijn logboeken zullen aan de schijf via **syslogd** module worden geschreven.
   >* Gebruik de optie **-verbose** om aanvullende informatie over proceshandelingen weer te geven.

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
      Met deze optie voegt u aanvullende logbestanden toe. We raden u aan om de processen opnieuw te starten zonder de optie **-verbose** als u de gewenste informatie hebt gevonden, om overbelasting van logbestanden te voorkomen.


* Start alle Adobe Campaign-processen op (gelijk aan het starten van de **nlserver6**-service):

   **nlserver watchdog -noconsole**

* Sluit alle Adobe Campaign-processen af (gelijk aan het afsluiten van de **nlserver6**-service):

   **Uitschakelen van server**

* Laad de **nlserver web** moduleconfiguratie (en de module van de Webserver uitbreiding, waar van toepassing) opnieuw wanneer **serverConf.xml** en **config-`<instance>  .xml </instance>`** dossiers zijn uitgegeven.

   **nlserver config-reload**

   >[!NOTE]
   >
   >Sommige configuratieveranderingen worden niet dynamisch in aanmerking genomen; Adobe Campaign moet worden afgesloten en opnieuw worden opgestart.

