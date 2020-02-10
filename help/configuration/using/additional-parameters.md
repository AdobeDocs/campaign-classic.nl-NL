---
title: Aanvullende parameters
seo-title: Aanvullende parameters
description: Aanvullende parameters
seo-description: null
page-status-flag: never-activated
uuid: c223c84a-f8fd-43d3-9deb-b1c19d442c65
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 1b2ae224-8406-4506-b589-6e5f6631e87f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# Aanvullende parameters{#additional-parameters}

## Definitie van parameters {#definition-of-parameters}

Het Adobe Campagne-platform biedt standaard twee webtrackingparameters van het type TRANSACTION:

* **bedrag**: het bedrag van een transactie vertegenwoordigt;
* **artikel**: geeft het aantal items in een transactie aan.

Deze parameters worden gedefinieerd in het **nms:webTrackingLog** -schema en zijn enkele van de indicatoren die worden weergegeven in de rapportage.

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

>[!CAUTION]
>
>Als u het maximumaantal tekens verhoogt waarmee rekening moet worden gehouden, kan dit van invloed zijn op de webprestaties van uw platform.

Hiervoor wijzigt u het **kenmerk webTrackingParamSize** van het **`<trackinglogd>`** element in het bestand **serverConf.xml** . Dit bestand wordt opgeslagen in de submap **conf** van de installatiemap van Adobe Campagne.

**Voorbeeld**:

De standaardwaarde is 64 tekens. Met deze waarde kunt u rekening houden met de standaardparameters **voor Hoeveelheid** en **Artikel** (&quot;bedrag=xxxxxxxx&amp;article=xxxxxxxx&quot;).

Door rekening te houden met beide parameters (grootte van naam + grootte van waarde) die in het bovenstaande voorbeeld van het extensieschema worden vermeld, kunt u de configuratie wijzigen om 100 tekens in aanmerking te nemen (&quot;bedrag=xxxxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxx&amp;code=xxxxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

Wanneer de configuratie is gewijzigd, moet u:

* Stop de webserver die als host fungeert voor de omleidingsmodule (Apache, IIS, enz.),
* Stop de Adobe Campaign-server: **netstop nlserver6** in Windows, **/etc/init.d/nlserver6 stop** in Linux;
* Verwijder in Linux de gedeelde geheugensegmenten met behulp van de **IPcrm** -opdracht.
* Start de Adobe Campagne-server opnieuw: **Net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux,
* Start de webserver opnieuw.

**Voorbeeld**: rekening houdend met de configuratie onder Linux.

```
adobe@selma:~$ /etc/init.d/nlserver6 stop
adobe@selma:~$ /etc/init.d/apache stop
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
adobe@selma:~$ /etc/init.d/nlserver6 start
adobe@selma:~$ /etc/init.d/apache start
```

>[!NOTE]
>
>Als u voor Linux de grootte van de parameters **webTrackingParamSize** of **maxSharedLogs** verhoogt, moet u mogelijk de grootte van het gedeelde geheugen (SHM) verhogen.

