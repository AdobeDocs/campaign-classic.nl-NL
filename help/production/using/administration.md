---
product: campaign
title: Beheer
description: Beheer
feature: Monitoring
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Beheer{#administration}



Automatisch opstarten van de Adobe Campaign-modules (**web**, **mta**, **wfserver**, enz.) wordt verstrekt door **nlserver** server.

Als u Adobe Campaign installeert, wordt de machine automatisch zo geconfigureerd dat de **nlserver** de dienst begint tijdens de laarsopeenvolging.

De volgende opdrachten worden gebruikt om de Adobe Campaign-service handmatig te starten en af te sluiten:

* In Windows:

   * **netwerkbeginserver6**
   * **netstop nlserver6**

* In Linux (als hoofdmap):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>Vanaf 20.1 raden we u aan in plaats daarvan de volgende opdracht te gebruiken (voor Linux): **systeemserver voor opstarten** / **systemctl stop nlserver**

Hier volgt een lijst met de gebruikelijke beheeropdrachten die in Linux toegankelijk zijn (zoals **Adobe Campaign**):

* Alle begonnen Adobe Campaign-modules weergeven: **/etc/init.d/nlserver6-pdump** of **/etc/init.d/nlserver6 status**

  >[!NOTE]
  >
  >De **-who** aan de **spuiten** kunt u informatie over de huidige verbindingen (gebruikers en processen) verzamelen.\
  >De **/etc/init.d/nlserver6 status** command (zonder de parameter &quot;-who&quot;) retourneert:
  >
  >    * 0 als alle processen worden uitgevoerd.
  >    * 1 als een proces ontbreekt.
  >    * 2 als er geen proces wordt uitgevoerd.
  >    * een andere waarde als er een fout is.
  >

* Een meervoudige instantie- of monoinstantiemodule starten/stoppen (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

  **nlserver start`<module>[@<instance>]`**

  **nlserver-stop`<module>[@<instance>][-immediate][-noconsole]`**

  U kunt ook de opdracht **opnieuw starten van server`<module>[@<instance>]`** gebruiken om een module opnieuw te starten.

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
  >* In geval van een noodsituatie gebruikt u de **-onmiddellijk** optie om een onmiddellijke stopzetting van het proces (gelijkwaardig aan het bevel van Unix) te dwingen **doden -9**).
  >* Gebruik de **-noconsole** om ervoor te zorgen dat de gestarte module niets op de console zal tonen. Zijn logbestanden worden via de **syslogd** -module.
  >* Gebruik de **-verbose** om aanvullende informatie over proceshandelingen weer te geven.
  >
  >   Voorbeeld:
  >
  >   **webbreedbeeldscherm opnieuw opstarten vanaf de server**
  >
  >   **nlserver start mta@myinstance -verbose**
  >
  >   Met deze optie voegt u aanvullende logbestanden toe. We raden u aan de processen opnieuw te starten zonder de **-verbose** als u de gewenste gegevens hebt gevonden, voorkomt u overbelasting van logbestanden.

* Alle Adobe Campaign-processen opstarten (gelijk aan het starten van de **nlserver6** service):

  **nlserver watchdog -noconsole**

* Sluit alle Adobe Campaign-processen af (gelijk aan het afsluiten van de **nlserver6** service):

  **Uitschakelen van server**

* Laad de **nlserver-web** moduleconfiguratie (en de module van de Webserver uitbreiding, indien van toepassing) wanneer **serverConf.xml** en **config-`<instance>  .xml </instance>`** bestanden zijn bewerkt.

  **nlserver config-reload**

  >[!NOTE]
  >
  >Sommige configuratieveranderingen worden niet dynamisch in aanmerking genomen; Adobe Campaign moet worden gesloten en dan opnieuw begonnen.
