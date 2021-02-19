---
solution: Campaign Classic
product: campaign
title: Leveringsstatus
description: Meer informatie over de statussen die beschikbaar zijn op het dashboard voor levering.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: de0e4555d3e2c5dff8d86a22ff4db85953105db1
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 4%

---


# Leveringsstatus {#delivery-statuses}

<!--ajouter intro 

ajouter screenshot -->

Zodra een levering is verzonden, toont het leveringsdashboard een status die u toestaat om te controleren als het verzenden met succes is geweest. Mogelijke statussen worden beschreven in de onderstaande sectie.

![](assets/delivery-status.png)

Raadpleeg [deze pagina](../../delivery/using/understanding-delivery-failures.md) voor meer informatie over de verschillende leveringsfouten die u kunt tegenkomen en hoe u deze kunt oplossen.

**Verwante onderwerpen:**

* [Leveringsdashboard](../../delivery/using/delivery-dashboard.md)
* [Problemen met levering oplossen](../../delivery/using/delivery-troubleshooting.md)
* [Leverbaarheid](../../delivery/using/about-deliverability.md)

## Lijst van leveringsstatussen {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> Status<br /> </th> 
   <th> Definities en oplossingen<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Verzonden<br /> </td> 
   <td> De levering is correct verzonden naar de berichtenprovider (maar de ontvanger heeft het niet noodzakelijkerwijs ontvangen).<br /> </td> 
  </tr> 
  <tr> 
   <td> Genegeerd<br /> </td> 
   <td> De levering is niet naar de ontvanger verzonden vanwege een fout met zijn adres. Het was of op lijst van gewezen personen, quarantined, niet verstrekt of een duplicaat. <br /> </td> 
  </tr> 
  <tr> 
   <td> Mislukt<br /> </td> 
   <td> De levering kan de ontvanger bijvoorbeeld niet bereiken vanwege een ongeldig adres of een volledig postvak. Het kan ook met een kwestie met verpersoonlijkingsblokken worden verbonden aangezien zij fouten kunnen produceren wanneer de schema's niet de leveringsafbeelding aanpassen. Zie <a href="../../delivery/using/understanding-delivery-failures.md" target="_blank">Werken met leveringsfouten</a><br /> </td> 
  </tr>
  <tr> 
   <td> In behandeling<br /> </td> 
   <td> De levering is klaar om te worden verzonden en zal door de leveringsserver (MTA) worden verwerkt. Zie <a href="#pending-status" target="_blank">Status in behandeling</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Niet van toepassing<br /> </td> 
   <td> De levering is in aanmerking genomen door de server (MTA) maar niet verwerkt.<br /> </td> 
  </tr>  
  <tr> 
   <td> Aflevering geannuleerd<br /> </td> 
   <td> De levering is geannuleerd door een operator.<br /> </td> 
  </tr> 
  <tr> 
   <td> In aanmerking genomen door de dienstverlener<br /> </td> 
   <td> De dienstverlener van SMS ontving de levering.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ontvangen op mobiel<br /> </td> 
   <td> De ontvanger heeft het SMS ontvangen op zijn mobiele apparaat.<br /> </td> 
  </tr>
  <tr> 
   <td> Verzonden naar de serviceprovider<br /> </td> 
   <td> De levering is naar de SMS-serviceprovider verzonden maar nog niet ontvangen.<br />
   </td> 
  </tr> 
  <tr> 
   <td> Voorbereid<br /> </td> 
   <td> De intermediaire status die slechts voor externe schakelaars zoals het mobiele kanaal wordt gebruikt. Het volgt de status "In behandeling"en is de externe schakelaar die de volgende status zal bepalen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Als u wilt weten hoe u de leverbaarheid van uw Adobe Campaign-e-mails kunt optimaliseren, raadpleegt u de Adobe Campaign [Handleiding voor best practices op het gebied van aflevering](../../delivery/using/deliverability-key-points.md) en [deze pagina](../../delivery/using/about-deliverability.md).

## Status {#pending-status} in behandeling

Na het bevestigen van uw levering, kunt u zien dat de status van uw levering **[!UICONTROL Pending]** is. Deze status houdt in dat het uitvoeringsproces wacht op de beschikbaarheid van bepaalde bronnen.

De status **[!UICONTROL Pending]** kan eerst betekenen dat uw levering gepland is en tot de bepaalde datum in behandeling is. Voor meer op dit, verwijs naar [Het plannen van de Levering](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending) sectie.

Als uw levering niet wordt verzonden en zijn status **[!UICONTROL Pending]** blijft, kan het het resultaat van zijn:

* MTA (de Agent van de Transfert van het Bericht), die modules en processen op de leveringsserver in werking stelt en die e-mail het verzenden beheert, kan niet zijn begonnen, of moet opnieuw worden begonnen.

   Voer de volgende stappen uit om dit te controleren en de module indien nodig te starten:

   >[!NOTE]
   >
   >Deze bewerking kan worden uitgevoerd met een **on-premise** of **hybride** hostingmodel met toegang tot de Campagneserver (zie [hostmodellen](../../installation/using/hosting-models.md)).

   1. Controleer of uw `mta@<instance>` modules zijn gestart op uw MTA-servers.

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<INSTANCENAME> (9268) - 23.0 Mb
      [...]
      ```

   1. Als MTA niet vermeld is, begin het met het volgende bevel:

      ```
      nlserver start mta@<INSTANCENAME>
      ```

      >[!NOTE]
      >
      >Vervang `<INSTANCENAME>` door de naam van de instantie (productie, ontwikkeling, enz.). De instantienaam wordt geïdentificeerd via de configuratiebestanden: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* De levering kan een affiniteit gebruiken die niet op de verzendende server wordt gevormd.

   In dit geval, controleer de configuratie van het verkeersbeheer (IP affiniteit) en gebruik **[!UICONTROL Managing affinities with IP addresses]** gebied om leveringen aan MTA te verbinden die de affiniteit beheert. Zie [deze sectie](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters) voor meer informatie over affiniteiten.

* Wanneer te veel campagnes lopen, blijft de leveringsstatus in &quot;Hangende&quot;status.

   De limiet van gelijktijdige campagnes wordt gedefinieerd in de optie **[!UICONTROL NmsOperation_LimitConcurrency]**. De standaardwaarde is 10.

   Meer informatie over opties vindt u op [deze pagina](../../installation/using/configuring-campaign-options.md).


**Verwante onderwerpen:**

* [Leveringslogboeken en geschiedenis](#delivery-logs-and-history)
* [Leveringsfouten begrijpen](../../delivery/using/understanding-delivery-failures.md)
* [Typen leveringsfouten en redenen](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)
