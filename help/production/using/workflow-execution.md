---
solution: Campaign Classic
product: campaign
title: Workflowuitvoering
description: Workflowuitvoering
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: a9d58e25ab17baaabf4ff8c109b53e83c7d93218
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 3%

---


# Workflowuitvoering{#workflow-execution}

In de onderstaande sectie vindt u informatie over algemene problemen met betrekking tot de uitvoering van workflows en hoe u deze problemen kunt oplossen.

Raadpleeg de volgende secties voor meer informatie over workflows:

* [Workflows](../../workflow/using/about-workflows.md)
* [Een workflow starten](../../workflow/using/starting-a-workflow.md)
* [Levenscyclus van workflow](../../workflow/using/workflow-life-cycle.md)
* [Tips en trucs bij het gebruik van workflows](../../workflow/using/workflow-best-practices.md)

## Zo snel mogelijk starten in campagnes {#start-as-soon-as-possible-in-campaigns}

In sommige gevallen, beginnen de werkschema&#39;s die van een campagne worden uitgevoerd niet wanneer het klikken van **[!UICONTROL Start]** knoop. In plaats van te beginnen gaat het naar de status &quot;Zo snel mogelijk beginnen&quot;.

Dit probleem kan verschillende oorzaken hebben: volg de onderstaande stappen om het op te lossen:

1. Controleer de status van de [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) technische workflow. Deze workflow beheert taken of workflows in een campagne. Als dit mislukt, worden workflows niet gestart of gestopt. Start de toepassing opnieuw om de workflows voor de campagne te hervatten.

   Raadpleeg [deze pagina](../../workflow/using/monitoring-technical-workflows.md) voor meer informatie over technische workflows.

   >[!NOTE]
   >
   >Nadat de werkstroom opnieuw is gestart, dient u de volgende taken uit te voeren (klik met de rechtermuisknop op **[!UICONTROL Scheduler]** activiteit / **[!UICONTROL Execute pending task(s) now]**) om te controleren of er bij een van de activiteiten opnieuw een fout optreedt.

   Als het werkschema nog ontbreekt, controleer het controlelogboek voor specifieke fout, los dienovereenkomstig problemen op, dan opnieuw begin het werkschema opnieuw.

1. Controleer de **[!UICONTROL wfserver]** modulestaat op het **[!UICONTROL Monitoring]** lusje, toegankelijk van de homepage van Campaign Classic (zie [Bewaking processen](../../production/using/monitoring-processes.md)). Dit proces is verantwoordelijk voor het uitvoeren van alle workflows.

   Een beheerder kan ook controleren of de **wfserver@`<instance>`**-module is gestart op uw hoofdtoepassingsserver met de onderstaande opdracht.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Als de module niet actief is, neemt u contact op met de klantenservice van Adobe. Als u een installatie op locatie hebt, moet een beheerder de service opnieuw starten met de onderstaande opdracht.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Vervang **`<instancename>`** door de naam van de instantie (productie, ontwikkeling, enz.). De instantienaam wordt geïdentificeerd via de configuratiebestanden:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Raadpleeg [deze sectie](../../production/using/usual-commands.md#module-launch-commands) voor meer informatie over het opnieuw opstarten van modules.

1. Controleer of het **aantal campagneprocessen dat** op de instantie uitvoert meer dan de drempel is. Er is een limiet die door de optie [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) wordt gedefinieerd voor het aantal campagneprocessen dat parallel op de instantie kan worden uitgevoerd. Wanneer deze limiet is bereikt, blijft de workflow in de status &quot;Zo snel mogelijk starten&quot; staan, zolang het aantal actieve workflows de limiet overschrijdt.

   U kunt dit probleem oplossen door ongewenste workflows te stoppen en mislukte leveringen te verwijderen. Als de drempelwaarde is bereikt, kunnen nieuwe processen worden uitgevoerd.

   Om het aantal werkstromen te controleren die van uw instantie lopen, adviseren wij gebruikend de vooraf bepaalde meningen, die door gebrek in **[!UICONTROL Administration]** / **[!UICONTROL Audit]** omslag toegankelijk zijn. Raadpleeg [deze sectie](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status) voor meer informatie.

   >[!IMPORTANT]
   >
   >Als u de optiedrempel **[!UICONTROL NmsOperation_LimitConcurrency]** verhoogt, kunnen er prestatieproblemen optreden voor uw instantie. Voer dit in geen geval alleen uit en neem contact op met uw Adobe Campaign-contactpersoon.

Raadpleeg [deze sectie](../../workflow/using/monitoring-workflow-execution.md) voor meer informatie over hoe u workflows kunt controleren.

## Bezig met starten {#start-in-progress}

Als de werkschema&#39;s niet worden uitgevoerd en hun status **Begin lopend** is, zou dit kunnen betekenen dat de werkschemamodule niet wordt gelanceerd.

Voer de volgende stappen uit om dit te controleren en de module indien nodig te starten:

1. Controleer de **[!UICONTROL wfserver]** modulestaat op het **[!UICONTROL Monitoring]** lusje, toegankelijk van de homepage van Campaign Classic (zie [Bewaking processen](../../production/using/monitoring-processes.md)).

   Een beheerder kan ook controleren of de **wfserver@`<instance>`**-module is gestart op uw hoofdtoepassingsserver met de onderstaande opdracht.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Raadpleeg [deze sectie](../../production/using/usual-commands.md#monitoring-commands-) voor meer informatie over het bewaken van modules.

1. Als de module niet actief is, neemt u contact op met de klantenservice van Adobe. Als u een installatie op locatie hebt, moet een beheerder deze opnieuw starten met de onderstaande opdracht.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Vervang **`<instancename>`** door de naam van de instantie (productie, ontwikkeling, enz.). De instantienaam wordt geïdentificeerd via de configuratiebestanden:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Raadpleeg [deze sectie](../../production/using/usual-commands.md#module-launch-commands) voor meer informatie over het opnieuw opstarten van modules.

## Mislukte werkstroom {#failed-workflow}

Als een werkstroom mislukt, voert u de volgende stappen uit:

1. Controleer het werkstroomjournaal. Raadpleeg voor meer informatie de secties [Workflow-uitvoering controleren](../../workflow/using/monitoring-workflow-execution.md) en [Logbestanden weergeven](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).
1. Technische workflows controleren. Zie [deze sectie](../../workflow/using/monitoring-technical-workflows.md) voor meer informatie hierover.
1. Zoek naar mislukkingen op de individuele werkschemaactiviteiten.
