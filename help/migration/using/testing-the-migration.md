---
product: campaign
title: De migratie testen
description: De migratie testen
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Migratietests{#testing-the-migration}



## Algemene procedure {#general-procedure}

Afhankelijk van uw configuratie zijn er verschillende manieren om migratietests uit te voeren.

U moet over een test-/ontwikkelomgeving beschikken om migratietests uit te voeren. Adobe Campaign-omgevingen zijn onderworpen aan licentie: controleer uw licentieovereenkomst of neem contact op met uw Adobe.

1. Stop alle ontwikkelingen in uitvoering en zorg ervoor dat ze in de productieomgeving terechtkomen.
1. Maak een steun van het gegevensbestand van de ontwikkelomgeving.
1. Stop alle Adobe Campaign-processen op de ontwikkelingsinstantie.
1. Maak een back-up van de database van de productieomgeving en herstel deze als ontwikkelomgeving.
1. Alvorens de diensten van Adobe Campaign te beginnen, stel **vriesinstance.js** voorzichtigheidsmanuscript in werking dat u het gegevensbestand van om het even welke voorwerpen laat ontruimen die in werking waren toen de steun werd begonnen.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Het bevel lanceert door gebrek op **droge** wijze, en maakt een lijst van alle verzoeken die door dat bevel werden uitgevoerd, zonder hen te lanceren. Om voorzichtigheidsverzoeken uit te voeren, gebruik **looppas** in het bevel.

1. Zorg ervoor dat uw back-ups correct zijn door ze te herstellen. Zorg ervoor dat u toegang hebt tot uw database, tabellen, gegevens, enzovoort.
1. Test de migratieprocedure in de ontwikkelomgeving.
1. Als de migratie van de ontwikkelomgeving succesvol is, kunt u de productieomgeving migreren.

>[!CAUTION]
>
>Vanwege wijzigingen in de gegevensstructuur is het niet mogelijk gegevenspakketten te importeren en te exporteren tussen een v5-platform en een v7-platform.


## Migratieprogramma&#39;s {#migration-tools}

Met verschillende opties kunt u de impact van een migratie meten en de mogelijke problemen identificeren. Deze opties moeten worden uitgevoerd:

* in het **config** bevel:

  ```
  nlserver.exe config <option> -instance:<instance-name>
  ```

* of na de upgrade:

  ```
  nlserver.exe config -postupgrade <option> -instance:<instance-name>
  ```

>[!NOTE]
>
>* U moet **- instantie gebruiken:`<instanceame>`** optie. We raden u niet aan de optie **-allinstances** te gebruiken.
>* Het de updatebevel van Adobe Campaign (**postupgrade**) laat u middelen synchroniseren en schema&#39;s en het gegevensbestand bijwerken. Deze bewerking kan slechts eenmaal en alleen op de toepassingsserver worden uitgevoerd. Na het synchroniseren van middelen, laat het **postupgrade** bevel u ontdekken of de synchronisatie om het even welke fouten of waarschuwingen produceert.

### Niet-standaard of ontbrekende objecten

* Met de optie **-showCustomEntities** wordt de lijst met alle niet-standaardobjecten weergegeven:

  ```
  nlserver.exe config -showCustomEntities -instance:<instance-name>
  ```

  Voorbeeld van een verzonden bericht:

  ```
  xtk_migration:opsecurity2 xtk:entity
  ```

* De **- showDeletteEntities** optie toont de lijst van alle standaardvoorwerpen die in het gegevensbestand of het dossiersysteem ontbreken. Voor elk ontbrekend object wordt het pad opgegeven.

  ```
  nlserver.exe config -showDeletedEntities -instance:<instance-name>
  ```

  Voorbeeld van een verzonden bericht:

  ```
  Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
  ```

### Verificatieproces {#verification-process}

Geïntegreerd als norm in het postupgrade bevel, laat dit proces u waarschuwingen en fouten tonen die de migratie zouden kunnen doen ontbreken. **als de fouten worden getoond, is de migratie niet uitgevoerd.** Als dit gebeurt, corrigeert u alle fouten en start u de postupgrade opnieuw.

U kunt het verificatieproces zelfstandig (zonder migratie) starten met de opdracht:

```
nlserver.exe config -postupgrade -check -instance:<instance-name>
```

>[!NOTE]
>
>Met de JST-310040-code kunt u alle waarschuwingen en fouten negeren.

De volgende expressies worden gezocht (hoofdlettergevoelig):

<table> 
 <thead> 
  <tr> 
   <th> Uitdrukking <br /> </th> 
   <th> Foutcode <br /> </th> 
   <th> Logtype <br /> </th> 
   <th> Opmerkingen <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001 <br /> </td> 
   <td> Waarschuwing <br /> </td> 
   <td> Dit type syntaxis wordt niet meer ondersteund in de personalisatie van de levering. <br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002 <br /> </td> 
   <td> Waarschuwing <br /> </td> 
   <td> Deze bibliotheek moet niet worden gebruikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> aanmelden(<br /> </td> 
   <td> PU-0003 <br /> </td> 
   <td> Waarschuwing <br /> </td> 
   <td> Deze verbindingsmethode moet niet meer worden gebruikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall() <br /> </td> 
   <td> PU-0004 <br /> </td> 
   <td> Waarschuwing <br /> </td> 
   <td> Deze functie wordt slechts gesteund wanneer het in de code van JavaScript wordt gebruikt die van een veiligheidsstreek wordt uitgevoerd die op <strong> sessionTokenOnly </strong> wijze is.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005 <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Dit type van fout leidt tot een migratiemislukking.<br /> </td> 
  </tr> 
  <tr> 
   <td> crmDeploymentType= "onpremise"<br /> </td> 
   <td> PU-0007 <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Dit type implementatie wordt niet meer ondersteund. Office 365 en On-premise Microsoft CRM connectorimplementatietype zijn nu afgekeurd. 
   </br> als u één van deze afgekeurde plaatsingstypes in een externe rekening gebruikt, zou deze externe rekening moeten worden geschrapt en u zou dan het <b> postupgrade </b> bevel moeten in werking stellen. 
   </br> om in de plaatsing van Web API te veranderen, verwijs naar <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank"> toepassingen van het Web </a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1 (mscrmWorkflow/sfdcWorkflow) <br /> </td> 
   <td> PU-0008 <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Microsoft CRM, Salesforce, Oracle CRM On Demand action zijn niet meer beschikbaar. Om de gegevenssynchronisatie tussen Adobe Campaign en een systeem van CRM te vormen, moet u de <a href="../../workflow/using/crm-connector.md" target="_blank"> schakelaar van CRM </a> gebruiken richtend activiteit.<br /> </td>
  </tr> 
 </tbody> 
</table>

Er wordt ook een coherentiecontrole van de database en het schema uitgevoerd.

### Herstellen, optie {#restoration-option}

Met deze optie kunt u objecten uit de doos herstellen als ze waren gewijzigd. Voor elk hersteld object wordt een back-up van de wijzigingen opgeslagen in de geselecteerde map:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instance-name>
```

>[!NOTE]
>
>We raden u ten zeerste aan absolute mappaden te gebruiken en de structuur van de mappenstructuur te behouden. Bijvoorbeeld: backupFolder\nms\srcSchema\billing.xml.

### De migratie hervatten {#resuming-migration}

Als u na een migratiemislukking opnieuw begint, hervat het van de zelfde plaats het werd tegengehouden.
