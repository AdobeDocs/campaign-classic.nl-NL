---
title: Specifieke configuraties in v6.02
seo-title: Specifieke configuraties in v6.02
description: Specifieke configuraties in v6.02
seo-description: null
page-status-flag: never-activated
uuid: ea072af3-fdc1-4828-ad13-d4327de1eaf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: 87a6cbda-54a6-4dae-8224-e06dc217f4fc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# Specifieke configuraties in v6.02{#specific-configurations-in-v6-02}

In de volgende sectie wordt beschreven welke aanvullende configuratie is vereist voor het migreren van versie 6.02. U zou ook de montages moeten vormen die in de [Algemene configuratiesectie](../../migration/using/general-configurations.md) worden gedetailleerd.

## Webtoepassingen {#web-applications}

Als u migreert op basis van versie 6.02, worden mogelijk foutlogboeken weergegeven met betrekking tot webtoepassingen van het overzichtstype. Voorbeelden van foutberichten:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Deze webtoepassingen maakten gebruik van SQLData en zijn niet compatibel met versie 7 vanwege de verhoogde beveiliging. Deze fouten leiden tot een migratiefout.

Als u deze webtoepassingen niet hebt gebruikt, voert u het volgende opschoonscript uit en voert u de postupgrade opnieuw uit:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Als u deze webtoepassingen hebt gewijzigd en deze wilt blijven gebruiken in v7, moet u de optie **allowSQLInjection** activeren in uw verschillende beveiligingszones en de postupgrade opnieuw starten. Raadpleeg de sectie [SQLData](../../migration/using/general-configurations.md#sqldata) voor meer informatie hierover.

## Gebruikersvriendelijkheid: Homepage en navigatie {#user-friendliness--home-page-and-navigation}

>[!IMPORTANT]
>
>Als u v6.02-webtoepassingen van het overzichtstype wilt blijven gebruiken, moet u de optie **allowSQLInjection** activeren in uw verschillende beveiligingszones voordat de upgrade wordt uitgevoerd. Raadpleeg [webtoepassingen](#web-applications).

Na een migratie van versie 6.02 wordt de startpagina van Adobe Campaign v6.02 niet meer weergegeven, maar is deze nog steeds toegankelijk en compatibel met Adobe Campaign v7.

Als u de v6.02-startpagina wilt blijven gebruiken, moet u na de migratie een pakket voor &quot;compatibiliteit&quot; installeren.

Hiertoe importeert u het compatibiliteitspakket:

Klik **[!UICONTROL Tools > Advanced > Import package]** en kies het **pakket campagneMigration.xml** in **`\nl\datakit\nms\[Your language]\package\optional`**.

Om toegang tot de v6.02 het type van Toepassing van het Web interfaces toe te staan, moet de **sessionTokenOnly** optie van de serverconfiguratie in het **serverConf.xml** - dossier worden geactiveerd:

```
sessionTokenOnly="true"
```

Deze optie wijzigt de veiligheidsniveaus om interfacecompatibiliteit te verzekeren.

Nadat het pakket is geïnstalleerd, wordt de startpagina van Adobe Campagne v7 vervangen door uw oude v6.02-startpagina, compleet met de algemene configuraties van v7 (blauwe webpaginabanner).

![](assets/dashboards.png)

Alle koppelingen op deze homepage zijn gekoppeld aan v7-schermen, behalve de lijsten (**[!UICONTROL operation list]**, **[!UICONTROL delivery tracking in operations]** enz.) die een koppeling vormen naar het overzicht van versie 6.02 (webtoepassingen).

![](assets/dashboards2.png)

Als u een ander overzicht wilt toevoegen dat is geconfigureerd in v6.02, moet u dit vanuit het dashboard toevoegen aan de startpagina. (**[!UICONTROL Administration > Access management > Dashboard]**).

>[!NOTE]
>
>Vergeet niet de verbinding te verbreken en vervolgens de console opnieuw te verbinden om de wijzigingen te registreren.

## Berichtencentrum {#message-center}

Na een migratie van de controleinstantie van het Centrum van het Bericht, moet u de transactionele berichtmalplaatjes voor hen opnieuw publiceren om te werken.

In v7 zijn de namen van transactionele berichtsjablonen op uitvoeringsinstanties gewijzigd. Zij worden momenteel vooraf bepaald door de exploitantnaam die aan de controleinstantie beantwoordt waarop zij, bijvoorbeeld **control1_template1_rt** worden gecreeerd (waar **control1** de naam van de exploitant is). Als u een significant volume van malplaatjes hebt, adviseren wij schrappend oude malplaatjes op controleinstanties.
