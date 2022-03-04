---
product: campaign
title: Leveringsstatussen
description: Meer informatie over de statussen die beschikbaar zijn op het dashboard voor levering
feature: Monitoring, Deliverability
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 4%

---

# Leveringsstatussen {#delivery-statuses}

![](../../assets/common.svg)

<!--ajouter intro 

ajouter screenshot -->

Zodra een levering is verzonden, toont het leveringsdashboard een status die u toestaat om te controleren als het verzenden succesvol was. Mogelijke statussen worden beschreven in de onderstaande sectie.

![](assets/delivery-status.png)

Voor meer details over de verschillende leveringsmislukkingen kunt u ontmoeten, en hoe te om hen op te lossen, verwijs naar [deze pagina](understanding-delivery-failures.md).

**Verwante onderwerpen:**

* [Leveringsdashboard](delivery-dashboard.md)
* [Problemen met een levering oplossen](delivery-troubleshooting.md)
* [Aan de slag met de prestaties](about-deliverability.md)

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
   <td> De levering werd correct verzonden naar de berichtenleverancier (maar de ontvanger ontving het niet noodzakelijk).<br /> </td> 
  </tr> 
  <tr> 
   <td> Genegeerd<br /> </td> 
   <td> De levering is niet naar de ontvanger verzonden vanwege een fout met hun adres. Het was of op lijst van gewezen personen, quarantined, niet verstrekt of een duplicaat. <br /> </td> 
  </tr> 
  <tr> 
   <td> Mislukt<br /> </td> 
   <td> De levering kan de ontvanger bijvoorbeeld niet bereiken vanwege een ongeldig adres of een volledig postvak. Het kan ook met een kwestie met verpersoonlijkingsblokken worden verbonden aangezien zij fouten kunnen produceren wanneer de schema's niet de leveringsafbeelding aanpassen. Zie <a href="understanding-delivery-failures.md" target="_blank">Leveringsfouten begrijpen</a><br /> </td> 
  </tr>
  <tr> 
   <td> In behandeling<br /> </td> 
   <td> De levering is klaar om te worden verzonden en zal door de leveringsserver (MTA) worden verwerkt. Zie <a href="#pending-status" target="_blank">Status in behandeling</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Niet van toepassing<br /> </td> 
   <td> De levering werd in aanmerking genomen door de server (MTA) maar niet verwerkt.<br /> </td> 
  </tr>  
  <tr> 
   <td> Aflevering geannuleerd<br /> </td> 
   <td> De levering is geannuleerd door een operator.<br /> </td> 
  </tr> 
  <tr> 
   <td> Door de dienstverlener in aanmerking genomen<br /> </td> 
   <td> De SMS-serviceprovider heeft de levering ontvangen.<br /> Voor gehoste of hybride installaties, als u hebt geüpgraded naar de <a href="sending-with-enhanced-mta.md" target="_blank">Enhanced MTA</a>, werd het bericht met succes van Campagne aan Verbeterde MTA afgelost.</td> 
  </tr> 
  <tr> 
   <td> Ontvangen op mobiel<br /> </td> 
   <td> De ontvanger heeft het SMS op zijn mobiele apparaat ontvangen.<br /> </td> 
  </tr>
  <tr> 
   <td> Verzonden naar de serviceprovider<br /> </td> 
   <td> De levering werd verzonden naar de dienstverlener van SMS maar nog niet ontvangen.<br />
   </td> 
  </tr> 
  <tr> 
   <td> Voorbereid<br /> </td> 
   <td> De intermediaire status die slechts voor externe schakelaars zoals het mobiele kanaal wordt gebruikt. Het volgt de status "In afwachting"en is de externe schakelaar die de volgende status zal bepalen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Ga voor meer informatie over het optimaliseren van de leverbaarheid van Adobe Campaign-e-mails naar [deze sectie](about-deliverability.md). Raadpleeg voor een diepgaandere analyse van de leverbaarbaarheid de [Adobe Handleiding voor beste praktijken voor aflevering](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl).

## Status in behandeling {#pending-status}

Na bevestiging van uw levering, kunt u zien dat de status van uw levering is **[!UICONTROL Pending]**. Deze status houdt in dat het uitvoeringsproces wacht op de beschikbaarheid van bepaalde bronnen.

De **[!UICONTROL Pending]** de status kan eerst betekenen dat de levering gepland is en in behandeling is tot de opgegeven datum. Raadpleeg voor meer informatie de [Leveringsplanning](steps-sending-the-delivery.md#scheduling-the-delivery-sending) sectie.

Als de levering niet wordt verzonden en de status van de levering blijft **[!UICONTROL Pending]**, kan het resultaat zijn van:

* MTA (de Agent van de Overdracht van het Bericht), die modules en processen op de leveringsserver in werking stelt en die e-mail het verzenden beheert, kan niet zijn begonnen, of kan moeten opnieuw worden begonnen.

   Voer de volgende stappen uit om dit te controleren en de module indien nodig te starten:

   >[!NOTE]
   >
   >Deze bewerking kan worden uitgevoerd met een **op locatie** of **hybride** het ontvangen model met toegang tot de server van de Campagne (zie [hostmodellen](../../installation/using/hosting-models.md)).

   1. Controleer of uw `mta@<instance>` modules worden gelanceerd op uw servers MTA.

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
      >Vervangen `<INSTANCENAME>` met de naam van uw instantie (productie, ontwikkeling, enz.). De instantienaam wordt geïdentificeerd via de configuratiebestanden: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* De levering kan een affiniteit gebruiken die niet op de verzendende server wordt gevormd.

   In dit geval, controleer de configuratie van het verkeersbeheer (IP affiniteit) en gebruik **[!UICONTROL Managing affinities with IP addresses]** veld voor koppeling van leveringen aan de MTA die de affiniteit beheert. Voor meer informatie over affiniteiten raadpleegt u [deze sectie](../../installation/using/configure-delivery-settings.md).

* Als er te veel campagnes worden uitgevoerd, blijft de status &quot;In behandeling&quot; behouden.

   De limiet van gelijktijdige campagnes wordt bepaald in het gedeelte **[!UICONTROL NmsOperation_LimitConcurrency]** optie. De standaardwaarde is 10.

   Meer informatie over opties in [deze pagina](../../installation/using/configuring-campaign-options.md).


**Verwante onderwerpen:**

* [Leveringslogboeken en geschiedenis](#delivery-logs-and-history)
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Typen leveringsfouten en redenen](understanding-delivery-failures.md#delivery-failure-types-and-reasons)
