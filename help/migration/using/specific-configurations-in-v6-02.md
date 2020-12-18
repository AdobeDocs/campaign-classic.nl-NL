---
solution: Campaign Classic
product: campaign
title: Specifieke configuraties in v6.02
description: Specifieke configuraties in v6.02
audience: migration
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 3%

---


# Specifieke configuraties in v6.02{#specific-configurations-in-v6-02}

In de volgende sectie wordt beschreven welke aanvullende configuratie is vereist voor het migreren van versie 6.02. U zou ook de montages moeten vormen die in [Algemene configuraties](../../migration/using/general-configurations.md) sectie worden gedetailleerd.

## Webapplicaties {#web-applications}

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

Als u deze webtoepassingen hebt gewijzigd en deze wilt blijven gebruiken in v7, moet u de optie **allowSQLInjection** in uw verschillende beveiligingszones activeren en de postupgrade opnieuw starten. Raadpleeg de sectie [SQLData](../../migration/using/general-configurations.md#sqldata) voor meer informatie hierover.

## Gebruikersvriendelijkheid: Startpagina en navigatie {#user-friendliness--home-page-and-navigation}

>[!IMPORTANT]
>
>Als u v6.02 overzicht-type van Web toepassingen wilt blijven gebruiken, moet u **allowSQLInjection** optie in uw verschillende veiligheidsstreken vóór de postupgrade activeren. Zie [Webtoepassingen](#web-applications).

Na een migratie van versie 6.02 wordt de Adobe Campaign v6.02-startpagina niet meer weergegeven, maar is deze nog steeds toegankelijk en compatibel met Adobe Campaign v7.

Als u de v6.02-startpagina wilt blijven gebruiken, moet u na de migratie een pakket voor &quot;compatibiliteit&quot; installeren.

Hiertoe importeert u het compatibiliteitspakket:

Klik **[!UICONTROL Tools > Advanced > Import package]** en kies **campagneMigration.xml** pakket in **`\nl\datakit\nms\[Your language]\package\optional`**.

Om toegang tot de v6.02 het type van Toepassing van het Web interfaces toe te staan, moet **sessionTokenOnly** de optie van de serverconfiguratie in **serverConf.xml** dossier worden geactiveerd:

```
sessionTokenOnly="true"
```

Deze optie wijzigt de veiligheidsniveaus om interfacecompatibiliteit te verzekeren.

Nadat het pakket is geïnstalleerd, wordt de Adobe Campaign v7-startpagina vervangen door uw oude v6.02-startpagina, compleet met de algemene configuraties van v7 (blauwe webpaginabanner).

![](assets/dashboards.png)

Alle koppelingen op deze homepage zijn gekoppeld aan v7-schermen, behalve de lijsten (**[!UICONTROL operation list]**, **[!UICONTROL delivery tracking in operations]**, enz.) die een koppeling vormen naar het overzicht van versie 6.02 (webtoepassingen).

![](assets/dashboards2.png)

Als u een ander overzicht wilt toevoegen dat is geconfigureerd in v6.02, moet u dit vanuit het dashboard toevoegen aan de startpagina. (**[!UICONTROL Administration > Access management > Dashboard]**).

>[!NOTE]
>
>Vergeet niet de verbinding te verbreken en vervolgens de console opnieuw te verbinden om de wijzigingen te registreren.

## Berichtmidden {#message-center}

Na een migratie van de controleinstantie van het Centrum van het Bericht, moet u de transactionele berichtmalplaatjes voor hen opnieuw publiceren om te werken.

In v7 zijn de namen van transactionele berichtsjablonen op uitvoeringsinstanties gewijzigd. Ze worden momenteel voorafgegaan door de naam van de operator die overeenkomt met de besturingsinstantie waarop ze zijn gemaakt, bijvoorbeeld **control1_template1_rt** (waarbij **control1** de naam van de operator is). Als u een significant volume van malplaatjes hebt, adviseren wij schrappend oude malplaatjes op controleinstanties.
