---
product: campaign
title: Aanvullende parameters voor webtracking
description: Meer informatie over parameters voor webtracking
feature: Configuration, Instance Settings
role: Developer
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Aanvullende parameters voor webtracking{#additional-parameters}

## Definitie van parameters {#definition-of-parameters}

Uw Adobe Campaign-platform biedt standaard twee webtrackingparameters van het type TRANSACTION:

* **bedrag**: vertegenwoordigt de hoeveelheid een transactie,
* **artikel**: vertegenwoordigt het aantal punten in een transactie.

Deze parameters worden bepaald in het **nms:webTrackingLog** schema, en zijn enkele indicatoren die in het melden worden gezien.

Als u aanvullende parameters wilt definiëren, moet u dit schema uitbreiden.

**Voorbeeld**:

```
<srcSchema extendedSchema="nms:webTrackingLog" label="Web Tracking"
           mappingType="sql" name="webTrackingLog" 
           namespace="cus" xtkschema="xtk:srcSchema">

  <element name="webTrackingLog">
    <attribute desc="Payment method" label="Payment method" length="10" name="mode" type="string"/>
    <attribute desc="Offer code" label="Offer code" length="5" name="code" type="string"/>
  </element>
</srcSchema>
```

U kunt de waarden van deze parameters tonen door de volgende logboeklijst (van een levering of een ontvanger) te vormen.

## Serverconfiguratie omleiden {#redirection-server-configuration}

In de serverconfiguratie, kunt u het maximumaantal karakters bepalen waarmee voor uw Web het volgen parameters moet worden rekening gehouden.

>[!IMPORTANT]
>
>Als u het maximumaantal tekens verhoogt waarmee rekening moet worden gehouden, kan dit van invloed zijn op de webprestaties van uw platform.

Om dit te doen, wijzig **webTrackingParamSize** attributen van het **`<trackinglogd>`** element in het **serverConf.xml** dossier. Dit dossier wordt bewaard in **conf** subdirectory van de de installatiemap van Adobe Campaign.

**Voorbeeld**:

De standaardwaarde is 64 tekens. Deze waarde laat u rekening houden met de **hoeveelheid** en **artikel** (&quot;bedrag=xxxxxxxx&amp;article=xxxxxxxx&quot;) standaardparameters.

Door rekening te houden met beide parameters (grootte van naam + grootte van waarde) die in het bovenstaande voorbeeld van het extensieschema worden vermeld, kunt u de configuratie wijzigen om 100 tekens in aanmerking te nemen (&quot;bedrag=xxxxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxx&amp;code=xxxxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Wanneer de configuratie is gewijzigd, moet u:

* Stop de webserver die als host fungeert voor de omleidingsmodule (Apache, IIS, enz.),
* Stop de server van Adobe Campaign: **netto stop nlserver6** in Vensters, **/etc/init.d/nlserver6 stop** in Linux,

  >[!NOTE]
  >
  >Beginnend 20.1, adviseren wij het gebruiken van het volgende bevel in plaats daarvan (voor Linux): **systemctl stop nlserver**

* In Linux, schrap de gedeelde geheugensegmenten gebruikend het **ipcrm** bevel,
* Start de Adobe Campaign-server opnieuw: **net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux,

  >[!NOTE]
  >
  >Beginnend 20.1, adviseren wij het gebruiken van het volgende bevel in plaats daarvan (voor Linux): **systeemctl begin nlserver**

* Start de webserver opnieuw.

**Voorbeeld**: die rekening houdend met de configuratie onder Linux.

```
adobe@selma:~$ systemctl stop nlserver
adobe@selma:~$ systemctl stop apache2
adobe@selma:~$ ipcs shm

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x52020679 2097153    adobe   666        93608      8                       

------ Semaphore Arrays --------
key        semid      owner      perms      nsems     
0x52020678 4227081    adobe   666        1         

------ Message Queues --------
key        msqid      owner      perms      used-bytes   messages    

adobe@selma:~$ ipcrm shm 2097153                             
1 resource(s) deleted
adobe@selma:~$ systemctl start nlserver
adobe@selma:~$ systemctl start apache2
```

>[!NOTE]
>
>Voor Linux, als u de grootte van **webTrackingParamSize** of **maxSharedLogs** parameters verhoogt, kunt u de grootte van het gedeelde geheugen (SHM) moeten verhogen.
