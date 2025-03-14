---
product: campaign
title: Omgevingen dupliceren
description: Omgevingen dupliceren
feature: Monitoring
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 1%

---

# Omgevingen dupliceren{#duplicating-environments}



## Inleiding {#introduction}

### Overzicht {#overview}

>[!IMPORTANT]
>
>Als u geen toegang hebt tot de server en de database (gehoste omgevingen), kunt u de hieronder beschreven procedures niet uitvoeren. Neem contact op met de Adobe.

Voor het gebruik van Adobe Campaign moeten een of meer omgevingen worden geïnstalleerd en geconfigureerd: ontwikkeling, test, productie, enz.

Elke omgeving bevat een Adobe Campaign-instantie en elke Adobe Campaign-instantie is gekoppeld aan een of meer databases. De toepassingsserver kan een of meer processen uitvoeren: bijna al deze hebben directe toegang tot de instantiedatabase.

In deze sectie worden de processen beschreven die moeten worden toegepast om een Adobe Campaign-omgeving te dupliceren, dat wil zeggen om een bronomgeving te herstellen naar een doelomgeving, wat resulteert in twee identieke werkomgevingen.

Hiervoor voert u de volgende stappen uit:

1. Maak een kopie van de databases op alle instanties in de bronomgeving.
1. Herstel deze kopieën in alle gevallen van de doelomgeving.
1. Stel **nms:freeseInstance.js in werking** voorzichtigheidsmanuscript op het doelmilieu alvorens het op te starten.

   Dit proces heeft geen invloed op de servers en hun configuratie.

   >[!NOTE]
   >
   >In de context van Adobe Campaign, combineert a **voorzichtigheid** acties die u alle processen laten tegenhouden die met de buitenkant in wisselwerking staan: logboeken, het volgen, leveringen, campagnewerkschema&#39;s, enz.\
   >Deze stap is nodig om te voorkomen dat berichten meerdere keren worden verzonden (eenmaal vanuit de nominale omgeving en één vanuit de gedupliceerde omgeving).

   >[!IMPORTANT]
   >
   >Eén omgeving kan meerdere instanties bevatten. Elke Adobe Campaign-instantie is onderworpen aan een licentieovereenkomst. Controleer uw licentieovereenkomst om te zien hoeveel omgevingen u kunt hebben.\
   >Met de onderstaande procedure kunt u een omgeving overbrengen zonder dat dit invloed heeft op het aantal omgevingen en instanties dat u hebt geïnstalleerd.

### Voordat u begint {#before-you-start}

>[!IMPORTANT]
>
>Wij adviseren sterk het runnen van een volledige steun van de gegevensbestanden voor alle instanties van de bron en doelmilieu&#39;s alvorens het overdrachtsproces te beginnen. Op deze manier kunt u, als zich een probleem voordoet, de back-ups herstellen en terugkeren naar de oorspronkelijke configuratie.

Dit proces werkt alleen als de bron- en doelomgevingen hetzelfde aantal instanties, hetzelfde doel (marketinginstantie, leveringsinstantie) en vergelijkbare configuraties hebben. De technische configuratie moet aan softwarevereisten voldoen. Dezelfde onderdelen moeten op beide omgevingen zijn geïnstalleerd.

## Implementatie {#implementation}

### Overdrachtsprocedure {#transfer-procedure}

Deze sectie zal u helpen de stappen begrijpen die voor het overbrengen van een bronmilieu aan een doelmilieu via een gevalsstudie worden vereist: ons doel hier is een productiemilieu (**prod** instantie) aan een ontwikkelomgeving (**dev** instantie) te herstellen om in een context te werken die zo dicht mogelijk aan het &quot;levende&quot;platform is.

De volgende stappen moeten met grote zorg worden uitgevoerd: sommige processen kunnen nog in uitvoering zijn wanneer de bronmilieugegevensbestanden worden gekopieerd. Voorzichtigheid (stap 3 hieronder) verhindert berichten tweemaal worden verzonden en handhaaft gegevensconsistentie.

>[!IMPORTANT]
>
>* De volgende procedure is geldig in de taal PostgreSQL. Als de SQL-taal anders is (bijvoorbeeld Oracle), moeten de SQL-query&#39;s worden aangepast.
>* De bevelen hieronder zijn binnen de context van a **prod** instantie en a **dev** instantie onder PostgreSQL van toepassing.
>

### Stap 1 - Maak een steun van de bronmilieu (prod) gegevens {#step-1---make-a-backup-of-the-source-environment--prod--data}

De databases kopiëren

Begin door alle gegevensbestanden van het bronmilieu te kopiëren. De bewerking is afhankelijk van de database-engine en valt onder de verantwoordelijkheid van de databasebeheerder.

Onder PostgreSQL, is het bevel:

```
pg_dump mydatabase > mydatabase.sql
```

### Stap 2 - de configuratie van het doelmilieu (dev) uitvoeren {#step-2---export-the-target-environment-configuration--dev-}

De meeste configuratieelementen zijn verschillend voor elke omgeving: externe accounts (midsourcing, routering, enz.), technische opties (platformnaam, database-id, e-mailadressen en standaard-URL&#39;s, enz.).

Alvorens het brongegevensbestand op het doelgegevensbestand te bewaren, moet u de configuratie van het doelmilieu (dev) uitvoeren. Om dit te doen, voer de inhoud van deze twee lijsten uit: **xtkoption** en **nmsextaccount**.

Met deze exportbewerking kunt u de configuratie van de ontwikkelaar behouden en alleen de gegevens van de ontwikkelaar vernieuwen (workflows, sjablonen, webtoepassingen, ontvangers, enzovoort).

Hiervoor voert u een pakketexport uit voor de volgende twee elementen:

* Exporteer de **xtk:option** lijst in een &quot;options_dev.xml&quot;dossier, zonder de verslagen met de volgende interne namen: &quot;WdbcTimeZone&quot;, &quot;NmsServer_LastPostUpgrade&quot;en &quot;NmsBroadcast_RegexRules&quot;.
* In een &quot;extaccount_dev.xml&quot;dossier, voer **nms:extAccount** lijst voor alle verslagen uit waarvan identiteitskaart niet 0 (@id &lt;> 0) is.

Controleer of het aantal geëxporteerde opties/accounts gelijk is aan het aantal regels dat in elk bestand moet worden geëxporteerd.

>[!NOTE]
>
>Het aantal regels dat in een pakketexport wordt geëxporteerd, is 1000 regels. Als het aantal opties of externe rekeningen meer dan 1000 bedraagt, moet u meerdere exportbewerkingen uitvoeren.
> 
>Raadpleeg [deze sectie](../../platform/using/working-with-data-packages.md#exporting-packages) voor meer informatie.

>[!NOTE]
>
>Wanneer de tabel NCMext-account wordt geëxporteerd, worden wachtwoorden die betrekking hebben op de externe accounts (bijvoorbeeld wachtwoorden voor midsourcing, Berichtencentrum uitvoeren, SMPP, IMS en andere externe accounts) niet geëxporteerd. Zorg ervoor dat u vooraf toegang hebt tot de juiste wachtwoorden, omdat deze mogelijk opnieuw moeten worden ingevoerd nadat de externe accounts weer in de omgeving zijn geïmporteerd.

### Stap 3 - Stop het doelmilieu (dev) {#step-3---stop-the-target-environment--dev-}

U moet de processen van Adobe Campaign op alle doelmilieuservers tegenhouden. Deze bewerking is afhankelijk van uw besturingssysteem.

U kunt alle processen tegenhouden, of slechts die die aan het gegevensbestand schrijven.

Als u alle processen wilt stoppen, gebruikt u de volgende opdrachten:

* In Windows:

  ```
  net stop nlserver6
  ```

* In Linux:

  ```
  /etc/init.d/nlserver6 stop
  ```

Gebruik het volgende bevel om te controleren dat alle processen zijn tegengehouden:

```
nlserver pdump
```

>[!NOTE]
>
>In Vensters, kan het **webmdl** proces nog actief zijn zonder andere verrichtingen te beïnvloeden.

U kunt ook controleren of er nog geen systeemprocessen actief zijn.

Hiervoor gebruikt u het volgende proces:

* In Vensters: open de **manager van de Taak** en controleer dat er geen **nlserver.exe** processen zijn.
* In Linux: voer de **ps aux | grep nlserver** bevel en controle dat er geen **nlserver** processen zijn.

### Stap 4 - Herstel de gegevensbestanden in het doelmilieu (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Om de brongegevensbestanden in het doelmilieu te herstellen, gebruik het volgende bevel:

```
psql mydatabase < mydatabase.sql
```

### Stap 5 - Let op de doelomgeving (dev) {#step-5---cauterize-the-target-environment--dev-}

Om storingen te voorkomen, mogen de processen die verband houden met het verzenden van de levering en het uitvoeren van de workflow niet automatisch worden uitgevoerd wanneer de doelomgeving wordt geactiveerd.

Voer hiertoe de volgende opdracht uit:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Stap 6 - Controle van de opwarming {#step-6---check-cauterization}

1. Controleer of het enige leveringsgedeelte het gedeelte is waarvan de id is ingesteld op 0:

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Controleer of de update van de leveringsstatus correct is:

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Controleer of de update van de workflowstatus correct is:

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Stap 7 - begin het proces van het Web van het doelmilieu (dev) opnieuw {#step-7---restart-the-target-environment-web-process--dev-}

Start in de doelomgeving de Adobe Campaign-processen voor alle servers opnieuw.

>[!NOTE]
>
>Alvorens Adobe Campaign op het **dev** milieu opnieuw te beginnen, kunt u een extra veiligheidsprocedure toepassen: begin slechts de **Web** module.
>  
>Om dit te doen, geef het de configuratiedossier van uw instantie uit (**config-dev.xml**), dan voeg &quot;_&quot;karakter vóór autoStart= &quot;waar&quot;opties voor elke module (mta, staat, enz.) toe.

Voer het volgende bevel in werking om het proces van het Web te beginnen:

```
nlserver start web
```

Gebruik de volgende opdracht om te controleren of alleen het webproces is gestart:

```
nlserver pdump
```

Controleer of toegang tot de functies van de clientconsole mogelijk is.

### Stap 8 - Importopties en externe accounts in de doelomgeving (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>Alleen het webproces moet in deze stap worden gestart. Als dit niet het geval is, stop andere lopende processen alvorens verder te gaan

Controleer vooral de waarden van verschillende regels bestanden voordat u ze importeert (bijvoorbeeld: &#39;NmsTracking_Pointer&#39; voor de optietabel en de leverings- of mid-sourcingaccounts voor de tabel van de externe account)

Om de configuratie van het doelmilieu gegevensbestand (dev) in te voeren:

1. Open de beheerconsole van de database en wis de externe accounts (table nms:extAccount) waarvan de id niet 0 is (@id &lt;> 0).
1. Importeer in de Adobe Campaign-console het pakket options_dev.xml dat eerder is gemaakt via de functionaliteit van het importpakket.

   Controleer of de opties inderdaad zijn bijgewerkt in het knooppunt **[!UICONTROL Administration > Platform > Options]** .

1. Importeer in de Adobe Campaign-console het bestand extaccount_dev.xml dat eerder is gemaakt via de functionaliteit voor het importeren van pakketten

   Controleer of externe databases inderdaad zijn geïmporteerd in de **[!UICONTROL Administration > Platform > External accounts]** .

### Stap 9 - Start alle processen opnieuw en wijzig gebruikers (dev) {#step-9---restart-all-processes-and-change-users--dev-}

Gebruik de volgende opdrachten om de Adobe Campaign-processen te starten:

* In Windows:

  ```
  net start nlserver6
  ```

* In Linux:

  ```
  /etc/init.d/nlserver6 start
  ```

Gebruik de volgende opdracht om te controleren of de processen zijn gestart:

```
nlserver pdump
```

Wijzig gebruikers om te zoeken naar de gebruikers die al op het ontwikkelplatform bestonden.
