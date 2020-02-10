---
title: Multibranding configureren
seo-title: Multibranding configureren
description: Multibranding configureren
seo-description: null
page-status-flag: never-activated
uuid: 61b4235c-da03-4da8-b14b-7ffb12c8d4c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 907d82c8-9262-4952-b8df-21144dd55824
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d5eac80743d4cc82cdf55aa9287e8bb4fcc84356

---


# Multibranding configureren{#configuring-multibranding}

In deze sectie wordt één oplossing beschreven voor het configureren van URL&#39;s voor bijhouden en spiegelen van pagina&#39;s per merk, voor transactieberichten in Adobe Campagne.

## Vereisten {#prerequisites}

* Alle gastheren moeten aan het configuratiedossier van de instantie (`config-<instance>.xml`) worden toegevoegd.
* Aan elk merk moet een subdomein worden toegewezen.
* U moet een HTTPS-certificaat voor alle merken hebben als de webtracering wordt uitgevoerd op HTTPS-pagina&#39;s.

## Normaal proces {#typical-process}

Om multibranding te vormen, moet u zowel uitvoeringsinstanties als controleinstantie vormen. Voer in de uitvoeringsinstanties de volgende stappen uit:

1. Maak één extern account per merk.

   >[!NOTE]
   >
   >Het maken van een externe account van het type uitvoeringsinstantie wordt weergegeven in de sectie [Control-instantie](../../message-center/using/creating-a-shared-connection.md#control-instance) .

1. Breid het schema nms:extAccount uit om het volgen URL toe te voegen:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >Het uitbreiden van een bestaand schema wordt voorgesteld in het [Uitbreiden van een schemasectie](../../configuration/using/extending-a-schema.md) .

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

   >[!CAUTION]
   >
   >Deze wijzigingen kunnen leiden tot conflicten tijdens de upgrade. Mogelijk moet u deze formules handmatig samenvoegen met de nieuwe versie.

Voor de controleinstantie, moet u leveringsmalplaatjes en externe rekeningen verbinden. Hiervoor moet u:

1. Maak één extern account per merk met dezelfde interne naam als in stap 1.
1. Eén standaardleveringssjabloon per merk maken.
1. In de leveringsmalplaatje **[!UICONTROL Properties]** , plaats het verpletteren aan de externe rekening van het merk.

