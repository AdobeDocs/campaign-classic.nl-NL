---
product: campaign
title: Workflowuitvoering
description: Workflowuitvoering
feature: Monitoring, Workflows
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---

# Workflowuitvoering{#workflow-execution}



In de onderstaande sectie vindt u informatie over algemene problemen met betrekking tot de uitvoering van workflows en hoe u deze problemen kunt oplossen.

Raadpleeg de volgende secties voor meer informatie over workflows:

* [Workflows](../../workflow/using/about-workflows.md)
* [Een workflow starten](../../workflow/using/starting-a-workflow.md)
* [Levenscyclus van workflow](../../workflow/using/workflow-life-cycle.md)
* [Tips en trucs bij het gebruik van workflows](../../workflow/using/workflow-best-practices.md)

## Zo snel mogelijk starten in campagnes {#start-as-soon-as-possible-in-campaigns}

In sommige gevallen worden workflows die worden uitgevoerd vanuit een campagne, niet gestart wanneer op de knop **[!UICONTROL Start]** knop. In plaats van te beginnen gaat het naar de status &quot;Zo snel mogelijk beginnen&quot;.

Dit probleem kan verschillende oorzaken hebben: volg de onderstaande stappen om het op te lossen:

1. Controleer de [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) technische workflowstatus. Deze workflow beheert taken of workflows in een campagne. Als dit mislukt, worden workflows niet gestart of gestopt. Start de toepassing opnieuw om de workflows voor de campagne te hervatten.

   Raadpleeg voor meer informatie over technische workflows controle [deze pagina](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Nadat de workflow opnieuw is gestart, moet u de volgende taken uitvoeren (klik met de rechtermuisknop op de knop **[!UICONTROL Scheduler]** activiteit / **[!UICONTROL Execute pending task(s) now]**) om na te gaan of er bij een van de activiteiten opnieuw sprake is van een mislukking.

   Als het werkschema nog ontbreekt, controleer het controlelogboek voor specifieke fout, los dienovereenkomstig problemen op, dan opnieuw begin het werkschema opnieuw.

1. Controleer de **[!UICONTROL wfserver]** modulestaat in **[!UICONTROL Monitoring]** tabblad, toegankelijk vanaf de startpagina van het Campaign Classic (zie [Monitoringprocessen](../../production/using/monitoring-processes.md)). Dit proces is verantwoordelijk voor het uitvoeren van alle workflows.

   Een beheerder kan ook controleren of de **wfserver@`<instance>`** wordt op de hoofdtoepassingsserver gestart met de onderstaande opdracht.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Als de module niet actief is, neemt u contact op met de klantenservice van de Adobe. Als u een installatie op locatie hebt, moet een beheerder de service opnieuw starten met de onderstaande opdracht.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Vervangen **`<instance-name>`** met de naam van uw instantie (productie, ontwikkeling, enz.). De instantienaam wordt geïdentificeerd via de configuratiebestanden:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Raadpleeg voor meer informatie over het opnieuw opstarten van modules [deze sectie](../../production/using/usual-commands.md#module-launch-commands).

1. Controleer of de **aantal campagneprocessen dat wordt uitgevoerd** op het geval is meer dan de drempel. Er is een limiet gedefinieerd door [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) optie op hoeveel campagneprocessen parallel op de instantie kunnen lopen. Wanneer deze limiet is bereikt, blijft de workflow in de status &quot;Zo snel mogelijk starten&quot; staan, zolang het aantal actieve workflows de limiet overschrijdt.

   U kunt dit probleem oplossen door ongewenste workflows te stoppen en mislukte leveringen te verwijderen. Als de drempelwaarde is bereikt, kunnen nieuwe processen worden uitgevoerd.

   Om het aantal werkstromen te controleren die van uw instantie lopen, adviseren wij gebruikend de vooraf bepaalde meningen, toegankelijk door gebrek in **[!UICONTROL Administration]** / **[!UICONTROL Audit]** map. Raadpleeg [deze sectie](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status) voor meer informatie.

   >[!IMPORTANT]
   >
   >De **[!UICONTROL NmsOperation_LimitConcurrency]** drempelwaarde voor opties kan leiden tot prestatieproblemen voor uw instantie. Voer dit in geen geval alleen uit en neem contact op met uw Adobe Campaign-contactpersoon.

Raadpleeg voor meer informatie over hoe u uw workflows kunt controleren [deze sectie](../../workflow/using/monitoring-workflow-execution.md).

## Beginnen in uitvoering {#start-in-progress}

Als werkstromen niet worden uitgevoerd en hun status is **Beginnen in uitvoering** Dit kan betekenen dat de workflowmodule niet wordt gestart.

Voer de volgende stappen uit om dit te controleren en de module indien nodig te starten:

1. Controleer de **[!UICONTROL wfserver]** modulestaat in **[!UICONTROL Monitoring]** tabblad, toegankelijk vanaf de startpagina van het Campaign Classic (zie [Monitoringprocessen](../../production/using/monitoring-processes.md)).

   Een beheerder kan ook controleren of de **wfserver@`<instance>`** wordt op de hoofdtoepassingsserver gestart met de onderstaande opdracht.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Raadpleeg voor meer informatie over het controleren van modules [deze sectie](../../production/using/usual-commands.md#monitoring-commands-).

1. Als de module niet actief is, neemt u contact op met de klantenservice van de Adobe. Als u een installatie op locatie hebt, moet een beheerder deze opnieuw starten met de onderstaande opdracht.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Vervangen **`<instance-name>`** met de naam van uw instantie (productie, ontwikkeling, enz.). De instantienaam wordt geïdentificeerd via de configuratiebestanden:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Raadpleeg voor meer informatie over het opnieuw opstarten van modules [deze sectie](../../production/using/usual-commands.md#module-launch-commands).

## Mislukte workflow {#failed-workflow}

Als een werkstroom mislukt, voert u de volgende stappen uit:

1. Controleer het werkstroomjournaal. Raadpleeg voor meer informatie de [Uitvoering van controlewerkstroom](../../workflow/using/monitoring-workflow-execution.md) en [Logboeken weergeven](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) secties.
1. Technische workflows controleren. Zie voor meer informatie de [deze sectie](../../workflow/using/monitoring-technical-workflows.md).
1. Zoek naar mislukkingen op de individuele werkschemaactiviteiten.
