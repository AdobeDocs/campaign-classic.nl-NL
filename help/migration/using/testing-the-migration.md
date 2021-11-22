---
product: campaign
title: De migratie testen
description: De migratie testen
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 9ba2199eabf91381e87661f30c9af8aa0ce4cc26
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 1%

---

# De migratie testen{#testing-the-migration}

![](../../assets/v7-only.svg)

## Algemene procedure {#general-procedure}

Afhankelijk van uw configuratie zijn er verschillende manieren om migratietests uit te voeren.

U moet over een test-/ontwikkelomgeving beschikken om migratietests uit te voeren. Voor ontwikkelomgevingen geldt een licentie: controleer uw licentieovereenkomst of neem contact op met de verkoopservice van Adobe Campaign.

1. Stop alle ontwikkelingen in uitvoering en zorg ervoor dat ze in de productieomgeving terechtkomen.
1. Maak een steun van het gegevensbestand van de ontwikkelomgeving.
1. Stop alle Adobe Campaign-processen op de ontwikkelingsinstantie.
1. Maak een back-up van de database van de productieomgeving en herstel deze als ontwikkelomgeving.
1. Voordat u de Adobe Campaign-services start, voert u de **vriesinstantie.js** het waarschuwings manuscript dat u het gegevensbestand van om het even welke voorwerpen laat ontruimen die toen de steun werd begonnen in werking gesteld.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >De opdracht wordt standaard gestart **drogen** en geeft een overzicht van alle aanvragen die door die opdracht zijn uitgevoerd, zonder deze te starten. Gebruik **run** in de opdracht.

1. Zorg ervoor dat uw back-ups correct zijn door ze te herstellen. Zorg ervoor dat u toegang hebt tot uw database, tabellen, gegevens, enzovoort.
1. Test de migratieprocedure in de ontwikkelomgeving.

   De volledige procedures worden in de [Vereisten voor migratie naar Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) sectie.

1. Als de migratie van de ontwikkelomgeving succesvol is, kunt u de productieomgeving migreren.

>[!IMPORTANT]
>
>Vanwege wijzigingen in de gegevensstructuur is het niet mogelijk gegevenspakketten te importeren en te exporteren tussen een v5-platform en een v7-platform.

>[!NOTE]
>
>De opdracht Adobe Campaign-update (**postupgrade**) kunt u bronnen synchroniseren en schema&#39;s en de database bijwerken. Deze bewerking kan slechts eenmaal en alleen op de toepassingsserver worden uitgevoerd. Na het synchroniseren van bronnen, **postupgrade** laat u ontdekken of de synchronisatie om het even welke fouten of waarschuwingen produceert.

## Migratiehulpmiddelen {#migration-tools}

Met verschillende opties kunt u de impact van een migratie meten en de mogelijke problemen identificeren. Deze opties moeten worden uitgevoerd:

* in de **config** opdracht:

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* of na de upgrade:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>U moet de opdracht **-instance:`<instanceame>`** optie. We raden u niet aan het **-allinstances** optie.

### -showCustomEntities en -showDeletteEntities options {#showcustomentities-and--showdeletedentities-options}

* De **-showCustomEntities** geeft de lijst met alle niet-standaardobjecten weer:

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   Voorbeeld van een verzonden bericht:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* De **-showDeletteEntities** geeft de lijst weer van alle standaardobjecten die ontbreken in de database of het bestandssysteem. Voor elk ontbrekend object wordt het pad opgegeven.

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   Voorbeeld van een verzonden bericht:

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### Verificatieproces {#verification-process}

Geïntegreerd als norm in het postupgrade bevel, laat dit proces u waarschuwingen en fouten tonen die de migratie zouden kunnen doen ontbreken. **Als er fouten worden weergegeven, is de migratie niet uitgevoerd.** Als dit gebeurt, corrigeert u alle fouten en start u de postupgrade opnieuw.

U kunt het verificatieproces zelfstandig (zonder migratie) starten met de opdracht:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>Negeer alle waarschuwingen en fouten met de JST-310040-code.

De volgende expressies worden gezocht (hoofdlettergevoelig):

<table> 
 <thead> 
  <tr> 
   <th> Uitdrukking<br /> </th> 
   <th> Foutcode<br /> </th> 
   <th> Het type Log<br /> </th> 
   <th> Opmerkingen<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Waarschuwing<br /> </td> 
   <td> Dit type syntaxis wordt niet meer ondersteund in de personalisatie van de levering. Zie <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. Anders moet u controleren of het waardetype correct is.<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Waarschuwing<br /> </td> 
   <td> Deze bibliotheek mag niet worden gebruikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> aanmelden(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Waarschuwing<br /> </td> 
   <td> Deze verbindingsmethode mag niet meer worden gebruikt. Zie <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">Geïdentificeerde webtoepassingen</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall()<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Waarschuwing<br /> </td> 
   <td> Deze functie wordt alleen ondersteund wanneer deze wordt gebruikt in JavaScript-code die wordt uitgevoerd vanuit een beveiligingszone die zich in <strong>sessionTokenOnly</strong> in.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Fout<br /> </td> 
   <td> Dit type fout leidt tot een migratiefout. Zie <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> Fout<br /> </td> 
   <td> Dit type fout leidt tot een migratiefout. Zie <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. Als u foutlogbestanden voor webtoepassingen met een overzichtstype krijgt (migratie vanuit v6.02), raadpleegt u <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Campagne configureren</a>.<br /> </td> 
  </tr>
  <tr> 
   <td> crmDeploymentType="onpremise"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> Fout<br /> </td> 
   <td> Dit type implementatie wordt niet meer ondersteund. Office 365 en On-premise Microsoft CRM connectorimplementatietype zijn nu afgekeurd. 
   </br>Als u een van deze verouderde implementatietypen gebruikt in een externe account, moet deze externe account worden verwijderd en moet u vervolgens het volgende uitvoeren <b>postupgrade</b> gebruiken. 
   </br>Als u wilt overschakelen op de webAPI-implementatie, raadpleegt u <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Webtoepassingen</a>.<br /> </td>
  </tr> 
 </tbody> 
</table>

Er wordt ook een coherentiecontrole van de database en het schema uitgevoerd.

### Herstellen, optie {#restoration-option}

Met deze optie kunt u objecten die zich buiten het vak bevinden herstellen als ze waren gewijzigd. Voor elk hersteld object wordt een back-up van de wijzigingen opgeslagen in de geselecteerde map:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>We raden u ten zeerste aan absolute mappaden te gebruiken en de structuur van de mappenstructuur te behouden. Bijvoorbeeld: backupFolder\nms\srcSchema\billing.xml.

### Hervatten van migratie {#resuming-migration}

Als u na een migratiemislukking opnieuw begint, hervat het van de zelfde plaats het werd tegengehouden.
