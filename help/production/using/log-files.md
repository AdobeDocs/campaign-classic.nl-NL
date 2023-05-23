---
product: campaign
title: Logboekbestanden
description: Logboekbestanden
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---

# Logboekbestanden{#log-files}



De logbestanden zijn als volgt ingedeeld:

![](assets/d_ncs_directory.png)

Elk **nlserver** wordt een logbestand gegenereerd dat in de volgende map is opgeslagen: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

De **nlserver-syslogd** slaat de logboeken op de schijf op. Deze module is vergelijkbaar met Unix **syslog daemon**, maar is aangepast voor compatibiliteit tussen Unix en Windows. De andere Adobe Campaign-modules slaan hun logbestanden niet op de schijf op. zij delegeren deze taak aan **syslogd** door het UDP-pakketten te verzenden.

Standaard heeft het Adobe Campaign-platform het **syslogd** op de module geïnstalleerd, maar het is mogelijk een andere **syslog daemon**. Deze module maakt de logbestanden in het dialoogvenster **log** directory.

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
>De **redir** alleen bestaat op omleidingsservers. De **url** subdirectory bevat de overeenkomende URL&#39;s die moeten worden omgeleid, en de subdirectory **log** bevat de trackinglogboeken. Om volgende logboeken te produceren, **trackinglogd** module moet actief zijn.

Voor prestaties en opslagoptimalisering, wordt het logins.log- dossier verdeeld in veelvoudige dossiers, één elke dag (logins.yy-mm-dd.log) met een maximum van 365 bewaarde dossiers. Het aantal dagen kan worden gewijzigd in serverConf.xml, onder syslogd (**maxNumberOfLoginsFiles** ). Zie de documentatie op de [serverconfiguratiebestand](../../installation/using/the-server-configuration-file.md#syslogd).

Standaard zijn de logbestanden beperkt tot twee bestanden van 10 MB per module en per instantie. Het tweede bestand wordt aangeroepen: **`<modulename>`_2.log**. De omvang van de stammen is daarom beperkt tot 2&#42;10 MB per module en per instantie.

U kunt echter grotere bestanden behouden. Als u dit wilt inschakelen, wijzigt u de waarde van de optie **maxFileSizeMb=&quot;10&quot;** in het dialoogvenster **syslogd** knooppunt van de **conf/serverConf.xml** bestand. Deze waarde vertegenwoordigt de maximumgrootte in MB van een logboekdossier.

Als u meer detailniveaus wilt behouden in de logboeken, kunt u de Adobe Campaign-modules starten met de **-verbose** parameter:

**nlserver start `<MODULE>`@`<INSTANCE>` -verbose**
