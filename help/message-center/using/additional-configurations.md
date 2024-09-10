---
product: campaign
title: Aanvullende configuraties
description: Leer hoe u aanvullende configuraties voor Transactieberichten in Adobe Campaign Classic instelt
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 4%

---

# Aanvullende configuraties {#mc-additional-configurations}



## Drempels controleren {#monitoring-thresholds}

U kunt de waarschuwingsdrempels (oranje) en waakzame drempels (rood) van de indicatoren vormen die in het **de dienstniveau van het Centrum van het Bericht** en **de verwerkingstijd van het Centrum van het Bericht** rapporten verschijnen (verwijs naar [ de transactionele overseinenrapporten van de Toegang ](../../message-center/using/about-transactional-messaging-reports.md)).

Hiervoor voert u de volgende stappen uit:

1. Open de plaatsingstovenaar op de **uitvoeringsinstantie**.

1. Ga naar de pagina **[!UICONTROL Message Center]** .

1. Gebruik de pijlen om de drempels te veranderen.

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>Het aantal gebeurtenissen die in rij in behandeling zijn wordt getoond in de [ sectie van de indicatoren van het Systeem ](../../production/using/monitoring-processes.md#system-indicators) van de het procescontrole pagina van Adobe Campaign. Voor meer informatie over de plaatsingstovenaar, verwijs naar [ deze sectie ](../../installation/using/deploying-an-instance.md#deployment-assistant).

## Gebeurtenissen opschonen {#purging-events}

U kunt de [ plaatsingstovenaar ](../../production/using/database-cleanup-workflow.md#deployment-assistant) gebruiken om te vormen hoe lang het gegeven in het gegevensbestand moet worden opgeslagen.

De ontruiming van de gebeurtenis wordt uitgevoerd automatisch door het [ opschoonwerkschema van het Gegevensbestand ](../../production/using/database-cleanup-workflow.md). Dit werkschema zuiveert de gebeurtenissen die op de uitvoeringsinstanties en de gebeurtenissen worden ontvangen en worden opgeslagen die op een controleinstantie worden gearchiveerd.

Gebruik de pijlen naar wens om de instellingen voor leegmaken te wijzigen.

Instellingen voor het opschonen van gebeurtenissen op een besturingsinstantie:

![](assets/messagecenter_delete_events_001.png)

Instellingen voor het opschonen van gebeurtenissen op een uitvoeringsinstantie:

![](assets/messagecenter_delete_events_002.png)

Voor meer op het werkschema van de gegevensbestandschoonmaak, zie [ deze sectie ](../../production/using/database-cleanup-workflow.md).


## Technische workflows {#technical-workflows}

U moet ervoor zorgen dat de technische werkschema&#39;s op de controleinstantie en de verschillende uitvoeringsinstanties inderdaad zijn gecreeerd en begonnen alvorens om het even welke transactionele berichtmalplaatjes op te stellen.

De diverse technische werkschema&#39;s met betrekking tot transactioneel overseinen (het Centrum van het Bericht) worden verdeeld tussen de controleinstantie en de uitvoeringsinstantie(s).

### Workflows voor besturingsinstanties {#control-instance-workflows}

In de besturingsinstantie moet u één archiveringsworkflow maken voor elke **[!UICONTROL Message Center execution instance]** externe account, ongeacht of u een of meerdere uitvoeringsinstanties hebt geregistreerd. Klik op de knop **[!UICONTROL Create the archiving workflow]** om de workflow te maken en te starten.

![](assets/messagecenter_archiving_002.png)

Deze werkschema&#39;s kunnen dan van het **Beleid > de Productie > het Centrum van het Bericht** omslag worden betreden. Nadat de workflows voor archivering zijn gemaakt, worden deze automatisch gestart.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

### Workflows voor uitvoeringsinstanties {#execution-instance-workflows}

Op de uitvoeringsinstantie(s), kunnen de technische werkschema&#39;s voor transactioneel overseinen van het **Beleid > de Productie > het Centrum van het Bericht** omslag worden betreden. Je moet ze gewoon starten. De workflows in de lijst zijn:

* **[!UICONTROL Processing batch events]** (interne naam: **[!UICONTROL batchEventsProcessing]** ): met deze workflow kunt u batchgebeurtenissen in een wachtrij onderbreken voordat ze aan een berichtsjabloon zijn gekoppeld.
* **[!UICONTROL Processing real time events]** (interne naam: **[!UICONTROL rtEventsProcessing]** ): met deze workflow kunt u real-time gebeurtenissen in een wachtrij onderbreken voordat deze aan een berichtsjabloon worden gekoppeld.
* **[!UICONTROL Update event status]** (interne naam: **[!UICONTROL updateEventStatus]** ): met deze workflow kunt u een status aan de gebeurtenis toewijzen.

  De volgende gebeurtenisstatussen zijn beschikbaar:

   * **[!UICONTROL Pending]** : de gebeurtenis bevindt zich in de wachtrij. Er is nog geen berichtsjabloon aan toegewezen.
   * **[!UICONTROL Pending delivery]** : de gebeurtenis bevindt zich in de wachtrij, er is een berichtsjabloon toegewezen aan de gebeurtenis en deze wordt verwerkt door de levering.
   * **[!UICONTROL Sent]** : deze status wordt gekopieerd uit de leveringslogboeken. Dit betekent dat de levering is verzonden.
   * **[!UICONTROL Ignored by the delivery]** : deze status wordt gekopieerd uit de leveringslogboeken. Het betekent dat de levering is genegeerd.
   * **[!UICONTROL Delivery failed]** : deze status wordt gekopieerd uit de leveringslogboeken. Het betekent dat de levering is mislukt.
   * **[!UICONTROL Event not taken into account]** : de gebeurtenis kan niet worden gekoppeld aan een berichtsjabloon. De gebeurtenis wordt niet verwerkt.

### Workflowschema voor archivering

Vermijd het wijzigen van het **archiverende werkschema** dat op de controleinstantie loopt. Anders kunnen sommige gegevens die worden opgehaald uit de uitvoeringsinstantie, verloren gaan.

Als u het het archiveren werkschema wijzigt, moet u het **volgen werkschema** programma op de uitvoeringsinstantie ook veranderen om het archiveringswerkschemaprogramma op de controleinstantie aan te passen.

## Multibranding configureren {#configuring-multibranding}

In deze sectie wordt één oplossing beschreven voor het configureren van URL&#39;s voor bijhouden en spiegelen per merk, voor transactieberichten in Adobe Campaign.

### Vereisten {#prerequisites}

* Alle gastheren moeten aan het configuratiedossier van de instantie (`config-<instance>.xml`) worden toegevoegd.
* Aan elk merk moet een subdomein worden toegewezen.
* U moet een HTTPS-certificaat voor alle merken hebben als de webtracering wordt uitgevoerd op HTTPS-pagina&#39;s.

Om multibranding te vormen, moet u zowel uitvoeringsinstanties als controleinstantie vormen.

### Uitvoeringsinstantie {#execution-instance}

Voer in de uitvoeringsinstantie(s) de onderstaande stappen uit:

1. Maak één extern account per merk.

   >[!NOTE]
   >
   >Leer hoe te om een uitvoerinstantie tot stand te brengen externe rekening in [ deze sectie ](../../message-center/using/configuring-instances.md#control-instance).

1. Breid het schema nms:extAccount uit om het volgen URL toe te voegen:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >Leer hoe te om een bestaand schema in [ uit te breiden Uitbreidend een schema ](../../configuration/using/extending-a-schema.md) sectie.

1. Wijzig de vorm nms:extAccount:

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. Wijzig de opties NmsTracking_OpenFormula en NmsTracking_ClickFormula om de externe account te gebruiken in plaats van een globale optie.

   Hiervoor vervangt u:

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   met:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >Deze wijzigingen kunnen leiden tot conflicten tijdens de upgrade. Mogelijk moet u deze formules handmatig samenvoegen met de nieuwe versie.

### Control-instantie {#control-instance}

Voor de controleinstantie, moet u leveringsmalplaatjes en externe rekeningen verbinden.

Hiervoor voert u de volgende stappen uit:

1. Creeer één externe rekening per merk met de zelfde interne naam zoals die op de [ uitvoeringsinstantie ](#execution-instance) wordt bepaald (stap 1).

1. Eén standaardleveringssjabloon per merk maken.

   >[!NOTE]
   >
   >    Leer hoe te om een leveringsmalplaatje in [ tot stand te brengen deze sectie ](../../delivery/using/creating-a-delivery-template.md#creating-a-new-template).

1. In de leveringsmalplaatje **[!UICONTROL Properties]**, plaats het verpletteren aan de externe rekening van het merk.
