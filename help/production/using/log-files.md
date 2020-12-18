---
solution: Campaign Classic
product: campaign
title: Logboekbestanden
description: Logboekbestanden
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---


# Logboekbestanden{#log-files}

De logbestanden zijn als volgt ingedeeld:

![](assets/d_ncs_directory.png)

Elke **nlserver** module produceert een logboekdossier dat in de volgende folder wordt bewaard: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

De **nlserver syslogd** module bewaart de logboeken aan de schijf. Deze module is gelijkaardig aan Unix **syslog daemon**, maar is aangepast voor verenigbaarheid tussen Unix en Vensters. De andere Adobe Campaign-modules slaan hun logbestanden niet op de schijf op. zij delegeren deze taak aan **syslogd** module door het UDP pakketten te verzenden.

Standaard is op het Adobe Campaign-platform de **syslogd**-module geïnstalleerd, maar het is mogelijk een andere **syslog daemon** te gebruiken. Deze module leidt tot de logboekdossiers in **log** folder.

De logboeken van modules met meerdere instanties worden opgeslagen in de volgende map: **`<installation directory>`/var/default/log/**. Hetzelfde logbestand wordt door alle instanties gedeeld (bijvoorbeeld **web.log**).

De logboeken van de andere modules worden opgeslagen in een subfolder die na de instantie wordt genoemd. Elke instantie heeft zijn eigen logboekdossiers.

Logbestanden met meerdere instanties worden weergegeven in de volgende tabel:

| Bestand | Beschrijving |
|---|---|
| web.log | Logboeken van de module Web (clientconsole, rapporten, SOAP API, enz.) |
| webmdl.log | Logbestanden van de omleidingsmodule |
| watchdog.log | Logbestanden van de Adobe Campaign-module voor procesbewaking |
| trackinglogd.log | Logboeken bijhouden |

De mono-instantie logboekdossiers zijn vermeld in de volgende lijst:

| Bestand | Beschrijving |
|---|---|
| mta.log | logbestanden van de mta-module |
| mtachild.log | Logboeken voor verwerking van berichten |
| wfserver.log | Logbestanden van de workflowserver-module |
| runwf.log | Logbestanden voor workflowuitvoering |
| inMail.log | Logboek van de module Stuiteren |
| logins.log | Hiermee worden alle aanmeldpogingen bij Adobe Campaign geregistreerd (geslaagd of niet) |

>[!IMPORTANT]
>
>De map **redir** bestaat alleen op redirection servers. De submap **url** bevat de overeenkomsten van de URL&#39;s die moeten worden omgeleid, en de submap **log** bevat de logbestanden voor bijhouden. Om volgende logboeken te produceren, moet **trackinglogd** module lopen.

Voor prestaties en opslagoptimalisering, wordt het logins.log- dossier verdeeld in veelvoudige dossiers, één elke dag (logins.yy-mm-dd.log) met een maximum van 365 bewaarde dossiers. Het aantal dagen kan in serverConf.xml, onder syslogd (**maxNumberOfLoginsFiles** optie) worden veranderd. Zie de documentatie op [server configuratiedossier](../../installation/using/the-server-configuration-file.md#syslogd).

Standaard zijn de logbestanden beperkt tot twee bestanden van 10 MB per module en per instantie. Het tweede bestand wordt aangeroepen: **`<modulename>`_2.log**. De grootte van de logboeken is daarom beperkt tot 2*10MB per module en per instantie.

U kunt echter grotere bestanden behouden. Om dit toe te laten, verander de waarde van **maxFileSizeMb=&quot;10&quot;** plaatsen in **syslogd** knoop van **conf/serverConf.xml** dossier. Deze waarde vertegenwoordigt de maximumgrootte in MB van een logboekdossier.

Als u wenst om verdere niveaus van detail in de logboeken te handhaven, kunt u de modules van Adobe Campaign met de **-verbose** parameter beginnen:

**nlserver start  `<MODULE>`@`<INSTANCE>` -verbose**
