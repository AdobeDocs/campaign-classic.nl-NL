---
product: campaign
title: Workflowuitvoering
description: Workflowuitvoering
feature: Monitoring, Workflows
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 2%

---

# Workflowuitvoering{#workflow-execution}



In de onderstaande sectie vindt u informatie over algemene problemen met betrekking tot de uitvoering van workflows en hoe u deze problemen kunt oplossen.

Raadpleeg de volgende secties voor meer informatie over workflows:

* [Workflows](../../workflow/using/about-workflows.md)
* [ Beginnend een werkschema ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/executing-a-workflow/start-a-workflow.html){target="_blank"}.
* [ het levenscyclus van het Werkschema ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html){target="_blank"}.
* [ Beste praktijken wanneer het gebruiken van werkschema&#39;s ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target="_blank"}.

## Zo snel mogelijk starten in campagnes {#start-as-soon-as-possible-in-campaigns}

In sommige gevallen worden workflows die worden uitgevoerd via een campagne, niet gestart wanneer wordt geklikt op de knop **[!UICONTROL Start]** . In plaats van te beginnen gaat het naar de status &quot;Zo snel mogelijk beginnen&quot;.

Dit probleem kan verschillende oorzaken hebben: volg de onderstaande stappen om het op te lossen:

1. Controleer de [**[!UICONTROL operationMgt]**](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/technical-workflows.html){target="_blank"} technische werkschemastatus. Deze workflow beheert taken of workflows in een campagne. Als dit mislukt, worden workflows niet gestart of gestopt. Start de toepassing opnieuw om de workflows voor de campagne te hervatten.

   Voor meer op technische werkschema&#39;s controle, verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html){target="_blank"}.

   >[!NOTE]
   >
   >Nadat u de workflow opnieuw hebt gestart, moet u de volgende taken uitvoeren (klik met de rechtermuisknop op **[!UICONTROL Scheduler]** activity / **[!UICONTROL Execute pending task(s) now]** ) om te controleren of er bij een van de activiteiten opnieuw een fout optreedt.

   Als het werkschema nog ontbreekt, controleer het controlelogboek voor specifieke fout, los dienovereenkomstig problemen op, dan opnieuw begin het werkschema opnieuw.

1. Controleer de **[!UICONTROL wfserver]** modulestaat in het **[!UICONTROL Monitoring]** lusje, toegankelijk van de homepage van Campaign Classic (zie [ processen van de Controle ](../../production/using/monitoring-processes.md)). Dit proces is verantwoordelijk voor het uitvoeren van alle workflows.

   Een admin gebruiker kan ook controleren dat de **wfserver@`<instance>`** module op uw belangrijkste toepassingsserver gebruikend het hieronder bevel wordt gelanceerd.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Neem contact op met de klantenservice van Adobe als de module niet actief is. Als u een installatie op locatie hebt, moet een beheerder de service opnieuw starten met de onderstaande opdracht.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Vervang **`<instance-name>`** door de naam van de instantie (productie, ontwikkeling, enz.). De instantienaam wordt geïdentificeerd via de configuratiebestanden:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Voor meer op hoe te om modules opnieuw te beginnen, verwijs naar [ deze sectie ](../../production/using/usual-commands.md#module-launch-commands).

1. Controle als het **aantal campagneprocessen die** op de instantie lopen meer dan de drempel is. Er is een limiet die door de optie [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) wordt gedefinieerd voor het aantal campagneprocessen dat parallel op de instantie kan worden uitgevoerd. Wanneer deze limiet is bereikt, blijft de workflow in de status &quot;Zo snel mogelijk starten&quot; staan, zolang het aantal actieve workflows de limiet overschrijdt.

   U kunt dit probleem oplossen door ongewenste workflows te stoppen en mislukte leveringen te verwijderen. Als de drempelwaarde is bereikt, kunnen nieuwe processen worden uitgevoerd.

   Als u het aantal workflows van uw instantie wilt controleren, raden we u aan de vooraf gedefinieerde weergaven te gebruiken, die standaard toegankelijk zijn in de map **[!UICONTROL Administration]** / **[!UICONTROL Audit]** . Raadpleeg de [Campaign v8-documentatie](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"} voor meer informatie.

   >[!IMPORTANT]
   >
   >Als u de optiedrempel van **[!UICONTROL NmsOperation_LimitConcurrency]** verhoogt, kunnen er prestatieproblemen optreden voor uw instantie. Voer dit in geen geval alleen uit en neem contact op met uw Adobe Campaign-contactpersoon.

Voor meer op hoe te om u werkschema&#39;s te controleren, verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}.

## Beginnen in uitvoering {#start-in-progress}

Als de werkschema&#39;s niet uitvoeren en hun status is **Begin lopend**, zou dit kunnen betekenen dat de werkschemamodule niet wordt gelanceerd.

Voer de volgende stappen uit om dit te controleren en de module indien nodig te starten:

1. Controleer de **[!UICONTROL wfserver]** modulestaat in het **[!UICONTROL Monitoring]** lusje, toegankelijk van de homepage van Campaign Classic (zie [ processen van de Controle ](../../production/using/monitoring-processes.md)).

   Een admin gebruiker kan ook controleren dat de **wfserver@`<instance>`** module op uw belangrijkste toepassingsserver gebruikend het hieronder bevel wordt gelanceerd.

   ```sql
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Voor meer op hoe te om modules te controleren, verwijs naar [ deze sectie ](../../production/using/usual-commands.md#monitoring-commands-).

1. Neem contact op met de klantenservice van Adobe als de module niet actief is. Als u een installatie op locatie hebt, moet een beheerder deze opnieuw starten met de onderstaande opdracht.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Vervang **`<instance-name>`** door de naam van de instantie (productie, ontwikkeling, enz.). De instantienaam wordt geïdentificeerd via de configuratiebestanden:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Voor meer op hoe te om modules opnieuw te beginnen, verwijs naar [ deze sectie ](../../production/using/usual-commands.md#module-launch-commands).

## Mislukte workflow {#failed-workflow}

Als een werkstroom mislukt, voert u de volgende stappen uit:

1. Controleer het werkstroomjournaal. Voor meer op dit, verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}.
1. Technische workflows controleren. Verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html){target="_blank"}.
1. Zoek naar mislukkingen op de individuele werkschemaactiviteiten.
