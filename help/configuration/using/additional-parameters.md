---
product: campaign
title: Aanvullende parameters voor webtracking
description: Meer informatie over parameters voor webtracking
feature: Configuration, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Aanvullende parameters voor webtracking{#additional-parameters}

## Definitie van parameters {#definition-of-parameters}

Uw Adobe Campaign-platform biedt standaard twee webtrackingparameters van het type TRANSACTION:

* **bedrag**: staat voor het bedrag van een transactie;
* **artikel**: geeft het aantal items in een transactie aan.

Deze parameters worden gedefinieerd in het dialoogvenster **nms:webTrackingLog** en zijn enkele van de indicatoren die worden weergegeven in de rapportage.

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

Om dit te doen, wijzig **webTrackingParamSize** kenmerk van de **`<trackinglogd>`** in het **serverConf.xml** bestand. Dit bestand wordt opgeslagen in het dialoogvenster **conf** subdirectory van de installatiemap van Adobe Campaign.

**Voorbeeld**:

De standaardwaarde is 64 tekens. Met deze waarde kunt u rekening houden met **bedrag** en **artikel** (&quot;bedrag=xxxxxxxx&amp;article=xxxxxxxx&quot;) standaardparameters.

Door rekening te houden met beide parameters (grootte van naam + grootte van waarde) die in het bovenstaande voorbeeld van het extensieschema worden vermeld, kunt u de configuratie wijzigen om 100 tekens in aanmerking te nemen (&quot;bedrag=xxxxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxx&amp;code=xxxxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Wanneer de configuratie is gewijzigd, moet u:

* Stop de webserver die als host fungeert voor de omleidingsmodule (Apache, IIS, enz.),
* Stop de Adobe Campaign-server: **netstop nlserver6** in Windows **/etc/init.d/nlserver6 stop** in Linux,

  >[!NOTE]
  >
  >Vanaf 20.1 raden we u aan in plaats daarvan de volgende opdracht te gebruiken (voor Linux): **systemctl stop nlserver**

* Verwijder in Linux de gedeelde geheugensegmenten met behulp van de **ipcrm** opdracht,
* Start de Adobe Campaign-server opnieuw: **netwerkbeginserver6** in Windows **/etc/init.d/nlserver6 start** in Linux,

  >[!NOTE]
  >
  >Vanaf 20.1 raden we u aan in plaats daarvan de volgende opdracht te gebruiken (voor Linux): **systeemserver voor opstarten**

* Start de webserver opnieuw.

**Voorbeeld**: rekening houdend met de configuratie onder Linux.

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
>Voor Linux, als u de grootte van **webTrackingParamSize** of **maxSharedLogs** parameters, moet u mogelijk de grootte van het gedeelde geheugen (SHM) verhogen.
