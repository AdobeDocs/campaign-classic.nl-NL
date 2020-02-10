---
title: Logbestanden
seo-title: Logbestanden
description: Logbestanden
seo-description: null
page-status-flag: never-activated
uuid: 266bc067-0218-4b3e-941c-dc5cd0b6a10d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: fac3e3ec-82a7-4087-ba88-2b28b0f69d1c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f018df9a2f7516b92f1f25a757065ef268136a5

---


# Logbestanden{#log-files}

De logbestanden zijn als volgt ingedeeld:

![](assets/d_ncs_directory.png)

Elke **nlserver** -module genereert een logbestand dat in de volgende map is opgeslagen: **`<installation directory>`/var/`<instance>`/log/`<module>`.log **.

De logbestanden worden opgeslagen op de schijf in de **systeemlogmodule** van de server. Deze module is gelijkaardig aan Unix **syslog daemon**, maar is aangepast voor verenigbaarheid tussen Unix en Vensters. In de andere Adobe Campagnemodules worden hun logbestanden niet op de schijf opgeslagen. zij delegeren deze taak aan de **syslogd** module door het pakketten UDP te verzenden.

Standaard is op het Adobe Campaign-platform de **syslogd** -module geïnstalleerd, maar u kunt ook een andere **syslog daemon** gebruiken. Deze module maakt de logbestanden in de **logmap** .

De logboeken van modules met meerdere instanties worden opgeslagen in de volgende map: **`<installation directory>`/var/default/log/**. Hetzelfde logbestand wordt door alle instanties gedeeld (bijvoorbeeld**web.log **).

De logboeken van de andere modules worden opgeslagen in een subfolder die na de instantie wordt genoemd. Elke instantie heeft zijn eigen logboekdossiers.

Logbestanden met meerdere instanties worden weergegeven in de volgende tabel:

| Bestand | Beschrijving |
|---|---|
| web.log | Logboeken van de module Web (clientconsole, rapporten, SOAP API, enz.) |
| webmdl.log | Logbestanden van de omleidingsmodule |
| waakhond.log | Logbestanden van de controlemodule voor het Adobe Campagne-proces |
| trackinglogd.log | Logboeken bijhouden |

De mono-instantie logboekdossiers zijn vermeld in de volgende lijst:

| Bestand | Beschrijving |
|---|---|
| mta.log | logbestanden van de mta-module |
| mtachild.log | Logboeken voor verwerking van berichten |
| wfserver.log | Logbestanden van de workflowserver-module |
| runwf.log | Logbestanden voor workflowuitvoering |
| inMail.log | Logboek van de module Stuiteren |
| logins.log | Hiermee worden alle aanmeldpogingen voor Adobe Campaign geregistreerd (al dan niet voltooid) |

>[!CAUTION]
>
>De map **redir** bestaat alleen op redirection servers. De submap **url** bevat de overeenkomsten met de URL&#39;s die moeten worden omgeleid, en het subdirectory- **logbestand** bevat de trackinglogboeken. Om het volgen logboeken te produceren, moet de **gevolgde logd** module lopen.

Voor prestaties en opslagoptimalisering, wordt het logins.log- dossier verdeeld in veelvoudige dossiers, één elke dag (logins.yy-mm-dd.log) met een maximum van 365 bewaarde dossiers. Het aantal dagen kan worden gewijzigd in serverConf.xml onder syslogd (optie **maxNumberOfLoginsFiles** ). Zie de documentatie op het dossier [van de](../../installation/using/the-server-configuration-file.md#syslogd)serverconfiguratie.

Standaard zijn de logbestanden beperkt tot twee bestanden van 10 MB per module en per instantie. Het tweede bestand wordt aangeroepen: **`<modulename>`_2.log **. De grootte van de logboeken is daarom beperkt tot 2*10MB per module en per instantie.

U kunt echter grotere bestanden behouden. Om dit toe te laten, verander de waarde van **maxFileSizeMb=&quot;10&quot;** plaatsen in de **syslogd** knoop van het **conf/serverConf.xml** dossier. Deze waarde vertegenwoordigt de maximumgrootte in MB van een logboekdossier.

Als u meer detailniveaus in de logboeken wilt behouden, kunt u de modules van de Campagne van Adobe met de **-verbose** parameter beginnen:

**nlserver start`<MODULE>`@`<INSTANCE>`-verbose**
