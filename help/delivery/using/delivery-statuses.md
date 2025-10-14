---
product: campaign
title: Leveringsstatussen
description: Meer informatie over de statussen op het dashboard voor levering
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Monitoring, Deliverability
role: User
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 3%

---

# Leveringsstatussen {#delivery-statuses}



<!--ajouter intro 

ajouter screenshot -->

Zodra een levering is verzonden, toont het leveringsdashboard een status die u toestaat om te controleren als het verzenden succesvol was. Mogelijke statussen worden beschreven in de onderstaande sectie.

![](assets/delivery-status.png)

Voor meer details op de verschillende leveringsmislukkingen kunt u ontmoeten, en hoe te om hen op te lossen, verwijs naar [&#x200B; deze pagina &#x200B;](understanding-delivery-failures.md).

**Verwante onderwerpen:**

* [Leveringsdashboard](delivery-dashboard.md)
* [Problemen met een levering oplossen](delivery-troubleshooting.md)
* [Aan de slag met de prestaties](about-deliverability.md)

## Lijst van leveringsstatussen {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> Status <br /> </th> 
   <th> Definities en oplossingen <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Verzonden<br /> </td> 
   <td> De levering werd correct verzonden naar de berichtleverancier (maar de ontvanger niet noodzakelijk het ontving).<br /> </td> 
  </tr> 
  <tr> 
   <td> Genegeerd <br /> </td> 
   <td> De levering is niet naar de ontvanger verzonden vanwege een fout met hun adres. Het was of op lijst van gewezen personen, quarantined, niet verstrekt of een duplicaat. <br /> </td> 
  </tr> 
  <tr> 
   <td> Mislukt <br /> </td> 
   <td> De levering kan de ontvanger bijvoorbeeld niet bereiken vanwege een ongeldig adres of een volledig postvak. Het kan ook met een kwestie met verpersoonlijkingsblokken worden verbonden aangezien zij fouten kunnen produceren wanneer de schema's niet de leveringsafbeelding aanpassen. Zie <a href="understanding-delivery-failures.md" target="_blank"> Begrip leveringsmislukkingen </a><br /> </td> 
  </tr>
  <tr> 
   <td> In behandeling <br /> </td> 
   <td> De levering is klaar om te worden verzonden en zal door de leveringsserver (MTA) worden verwerkt. Zie <a href="#pending-status" target="_blank"> Hangende status </a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Niet van toepassing <br /> </td> 
   <td> De levering werd in aanmerking genomen door de server (MTA) maar niet verwerkt.<br /> </td> 
  </tr>  
  <tr> 
   <td> Aflevering geannuleerd <br /> </td> 
   <td> De levering werd geannuleerd door een exploitant.<br /> </td> 
  </tr> 
  <tr> 
   <td> Rekening gehouden met door de dienstverlener <br /> </td> 
   <td> De SMS-serviceprovider heeft de levering ontvangen.<br /> voor ontvangen of hybride installaties, als u aan <a href="sending-with-enhanced-mta.md" target="_blank"> Verbeterde MTA </a> hebt bevorderd, werd het bericht met succes van Campagne aan Verbeterde MTA met succes afgelost.</td> 
  </tr> 
  <tr> 
   <td> Ontvangen op mobiel <br /> </td> 
   <td> De ontvanger ontving SMS op hun mobiele apparaat.<br /> </td> 
  </tr>
  <tr> 
   <td> Verzonden aan de dienstverlener <br /> </td> 
   <td> De levering werd verzonden naar de dienstverlener van SMS maar nog niet ontvangen.<br />
   </td> 
  </tr> 
  <tr> 
   <td> Voorbereid <br /> </td> 
   <td> De intermediaire status die slechts voor externe schakelaars zoals het mobiele kanaal wordt gebruikt. Het volgt de "Hangende"status en is de externe schakelaar die de volgende status zal bepalen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Leren hoe te om de leverbaarheid van uw e-mails van Adobe Campaign te optimaliseren, verwijs naar [&#x200B; deze sectie &#x200B;](about-deliverability.md). Voor een diepere duik op leverability, verwijs naar de [&#x200B; Gids van de Beste praktijken van de Levering van Adobe &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl).

## Status in behandeling {#pending-status}

Nadat u de levering hebt bevestigd, ziet u dat de status van de levering **[!UICONTROL Pending]** is. Deze status houdt in dat het uitvoeringsproces wacht op de beschikbaarheid van bepaalde bronnen.

De status **[!UICONTROL Pending]** kan eerst betekenen dat de levering gepland is en in behandeling is tot de opgegeven datum. Voor meer op dit, verwijs naar de [&#x200B; Campagne v8 documentatie &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/configure-and-send.html#schedule-delivery-sending){target="_blank"}

Als uw levering niet wordt verzonden en de status ervan **[!UICONTROL Pending]** blijft, kan dit het gevolg zijn van:

* MTA (de Agent van de Overdracht van het Bericht), die modules en processen op de leveringsserver in werking stelt en die e-mail het verzenden beheert, kan niet zijn begonnen, of kan moeten opnieuw worden begonnen.

  Voer de volgende stappen uit om dit te controleren en de module indien nodig te starten:

  >[!NOTE]
  >
  >Deze verrichting kan met een **op-gebouw** of **hybride** ontvangen model met toegang worden uitgevoerd de server van de Campagne (zie [&#x200B; ontvangende modellen &#x200B;](../../installation/using/hosting-models.md)).

   1. Controleer of uw `mta@<instance>` -modules zijn gestart op uw MTA-servers.

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<instance-name> (9268) - 23.0 Mb
      [...]
      ```

   1. Als MTA niet vermeld is, begin het met het volgende bevel:

      ```
      nlserver start mta@<instance-name>
      ```

      >[!NOTE]
      >
      >Vervang `<instance-name>` door de naam van de instantie (productie, ontwikkeling, enz.). De instantienaam wordt geïdentificeerd via de configuratiebestanden: `[path of application]nl6/conf/config-<instance-name>.xml`

* De levering kan een affiniteit gebruiken die niet op de verzendende server wordt gevormd.

  Controleer in dit geval de configuratie van het verkeersbeheer (IP-affiniteit) en gebruik het veld **[!UICONTROL Managing affinities with IP addresses]** om leveringen te koppelen aan de MTA die de affiniteit beheert. Voor meer informatie over affiniteiten, verwijs naar [&#x200B; deze sectie &#x200B;](../../installation/using/configure-delivery-settings.md).

* Wanneer te veel campagnes lopen, blijft de leveringsstatus in &quot;Hangende&quot;status.

  De limiet van gelijktijdige campagnes wordt gedefinieerd in de optie **[!UICONTROL NmsOperation_LimitConcurrency]** . De standaardwaarde is 10.

  Leer meer over opties in [&#x200B; deze pagina &#x200B;](../../installation/using/configuring-campaign-options.md).


**Verwante onderwerpen:**

* [Leveringslogboeken en geschiedenis](#delivery-logs-and-history)
* [Leveringsfouten begrijpen](understanding-delivery-failures.md)
* [Typen leveringsfouten en redenen](understanding-delivery-failures.md#delivery-failure-types-and-reasons)
