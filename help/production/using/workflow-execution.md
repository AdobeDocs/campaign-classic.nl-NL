---
title: Workflow-uitvoering
seo-title: Workflow-uitvoering
description: Workflow-uitvoering
seo-description: null
page-status-flag: never-activated
uuid: 115256f6-bdf2-4594-885c-e90d02a25b80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 7d8828c5-5776-49ca-b4f7-a4a6aaaa9db1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---


# Workflow-uitvoering{#workflow-execution}

In de onderstaande sectie vindt u informatie over algemene problemen met betrekking tot de uitvoering van workflows en hoe u deze problemen kunt oplossen.

Raadpleeg de volgende secties voor meer informatie over workflows:

* [Workflows](../../workflow/using/about-workflows.md)
* [Een workflow starten](../../workflow/using/starting-a-workflow.md)
* [Levenscyclus van werkstroom](../../workflow/using/workflow-life-cycle.md)
* [Tips en trucs bij het gebruik van workflows](../../workflow/using/workflow-best-practices.md)

## Zo snel mogelijk starten in campagnes {#start-as-soon-as-possible-in-campaigns}

In sommige gevallen worden workflows die worden uitgevoerd vanuit een campagne, niet gestart wanneer op de **[!UICONTROL Start]** knop wordt geklikt. In plaats van te beginnen gaat het naar de status &quot;Zo snel mogelijk beginnen&quot;.

Dit probleem kan verschillende oorzaken hebben: volg de onderstaande stappen om het op te lossen:

1. Controleer de status van de [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) technische workflow. Deze workflow beheert taken of workflows in een campagne. Als dit mislukt, worden workflows niet gestart of gestopt. Start de toepassing opnieuw om de workflows voor de campagne te hervatten.

   Raadpleeg [deze pagina](../../workflow/using/monitoring-technical-workflows.md)voor meer informatie over technische workflows die worden gecontroleerd.

   >[OPMERKING]
   >
   >Nadat u de workflow opnieuw hebt gestart, dient u de volgende taken uit te voeren (klik met de rechtermuisknop op de **[!UICONTROL Scheduler]** activiteit / **[!UICONTROL Execute pending task(s) now]**) om te controleren of er bij een van de activiteiten opnieuw een fout optreedt.

   Als het werkschema nog ontbreekt, controleer het controlelogboek voor specifieke fout, los dienovereenkomstig problemen op, dan opnieuw begin het werkschema opnieuw.

1. Controleer de **[!UICONTROL wfserver]** modulestaat op het **[!UICONTROL Monitoring]** lusje, toegankelijk van de Klassieke homepage van de Campagne (zie de processen [van de](../../production/using/monitoring-processes.md)Controle). Dit proces is verantwoordelijk voor het uitvoeren van alle workflows.

   Een beheerder kan ook controleren of de **wfserver@`<instance>`**-module op uw hoofdtoepassingsserver wordt gestart met de onderstaande opdracht.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Neem contact op met de klantenservice van Adobe als de module niet actief is. Als u een installatie op locatie hebt, moet een beheerder de service opnieuw starten met de onderstaande opdracht.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Vervangen **`<instancename>`** door de naam van uw instantie (productie, ontwikkeling, enz.). De instantienaam wordt geïdentificeerd via de configuratiebestanden:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Raadpleeg [deze sectie](../../production/using/usual-commands.md#module-launch-commands)voor meer informatie over het opnieuw opstarten van modules.

1. Controleer of het **aantal campagneprocessen dat op de instantie wordt uitgevoerd** , groter is dan de drempel. Er is een limiet die door de [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) optie wordt gedefinieerd voor het aantal campagneprocessen dat parallel op de instantie kan worden uitgevoerd. Wanneer deze limiet is bereikt, blijft de workflow in de status &quot;Zo snel mogelijk starten&quot; staan, zolang het aantal actieve workflows de limiet overschrijdt.

   U kunt dit probleem oplossen door ongewenste workflows te stoppen en mislukte leveringen te verwijderen. Als de drempelwaarde is bereikt, kunnen nieuwe processen worden uitgevoerd.

   Om het aantal werkstromen te controleren die van uw instantie lopen, adviseren wij gebruikend de vooraf bepaalde meningen, toegankelijk door gebrek in **[!UICONTROL Administration]** / **[!UICONTROL Audit]** omslag. Raadpleeg [deze pagina](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)voor meer informatie.

   >[VOORZIENING]
   >
   >Als u de **[!UICONTROL NmsOperation_LimitConcurrency]** optiedrempel verhoogt, kunnen er prestatieproblemen optreden. Voer dit in geen geval zelfstandig uit en neem contact op met uw Adobe-contactpersoon voor campagnes.

Raadpleeg [deze sectie](../../workflow/using/monitoring-workflow-execution.md)voor meer informatie over hoe u de workflows kunt controleren.

## Beginnen in uitvoering {#start-in-progress}

Als werkstromen niet worden uitgevoerd en hun status **Begin lopend** is, zou dit kunnen betekenen dat de werkschemamodule niet wordt gelanceerd.

Voer de volgende stappen uit om dit te controleren en de module indien nodig te starten:

1. Controleer de **[!UICONTROL wfserver]** modulestaat op het **[!UICONTROL Monitoring]** lusje, toegankelijk van de Klassieke homepage van de Campagne (zie de processen [van de](../../production/using/monitoring-processes.md)Controle).

   Een beheerder kan ook controleren of de **wfserver@`<instance>`**-module op uw hoofdtoepassingsserver wordt gestart met de onderstaande opdracht.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Voor meer op hoe te om modules te controleren, verwijs naar [deze sectie](../../production/using/usual-commands.md#monitoring-commands-).

1. Neem contact op met de klantenservice van Adobe als de module niet actief is. Als u een installatie op locatie hebt, moet een beheerder deze opnieuw starten met de onderstaande opdracht.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Vervangen **`<instancename>`** door de naam van uw instantie (productie, ontwikkeling, enz.). De instantienaam wordt geïdentificeerd via de configuratiebestanden:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Raadpleeg [deze sectie](../../production/using/usual-commands.md#module-launch-commands)voor meer informatie over het opnieuw opstarten van modules.

## Mislukte workflow {#failed-workflow}

Als een werkstroom mislukt, voert u de volgende stappen uit:

1. Controleer het werkstroomjournaal. Raadpleeg voor meer informatie de secties Uitvoering [van de](../../workflow/using/monitoring-workflow-execution.md) controlewerkstroom en Logboeken [](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) weergeven.
1. Technische workflows controleren. For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. Zoek naar mislukkingen op de individuele werkschemaactiviteiten.
