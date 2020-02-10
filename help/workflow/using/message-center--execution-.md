---
title: Berichtcentrum (uitvoering)
seo-title: Berichtcentrum (uitvoering)
description: Berichtcentrum (uitvoering)
seo-description: null
page-status-flag: never-activated
uuid: 8dfb09d1-da00-43fb-9df4-243bb915cbde
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: dc3d8998-9493-4d71-b3e2-6f9531cb9bac
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Berichtcentrum (uitvoering){#message-center-execution}

De hieronder beschreven workflows worden standaard geïnstalleerd met de module **Message Center - Execution** . Raadpleeg deze [sectie](../../message-center/using/about-transactional-messaging.md)voor meer informatie over deze module.

Meer over hoe te om technische werkschema&#39;s met betrekking tot de module van het Centrum van het Bericht te vormen, verwijs naar [deze pagina](../../message-center/using/technical-workflows.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Gebeurtenisstatus</span> bijwerken <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span><br /> </td> 
   <td> Met deze workflow kunt u een status aan een gebeurtenis toewijzen. Gebeurtenisstatussen zijn als volgt:<br /> 
    <ul> 
     <li> <p><strong>In behandeling</strong>: de gebeurtenis bevindt zich in een wachtrij. Er is nog geen berichtsjabloon aan gekoppeld.</p> </li> 
     <li> <p><strong>In afwachting van levering</strong>: Als de gebeurtenis zich in een wachtrij bevindt, is er een berichtsjabloon aan gekoppeld en wordt deze momenteel verwerkt door de levering.</p> </li> 
     <li> <p><strong>Verzonden</strong>: deze status wordt gekopieerd uit de leveringslogboeken. Dit betekent dat de levering is verzonden.</p> </li> 
     <li> <p><strong>Genegeerd door de levering</strong>: deze status wordt gekopieerd uit de leveringslogboeken. Het betekent dat de levering is genegeerd.</p> </li> 
     <li> <p><strong>Afleveringsfout</strong>: deze status wordt gekopieerd uit de leveringslogboeken. Het betekent dat de levering is mislukt.</p> </li> 
     <li> <p><strong>Gebeurtenis niet behandeld</strong>: de gebeurtenis is niet gekoppeld aan een berichtsjabloon. De gebeurtenis wordt niet opnieuw verwerkt.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Batchgebeurtenissen</span> verwerken <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span><br /> </td> 
   <td> Met deze workflow kunt u batchgebeurtenissen in een wachtrij plaatsen voordat u ze aan een berichtsjabloon koppelt. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Real-time gebeurtenissen</span> verwerken <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span><br /> </td> 
   <td> Dit werkschema laat u gebeurtenissen in real time in een rij zetten alvorens hen met een berichtmalplaatje te associëren. <br /> </td> 
  </tr> 
 </tbody> 
</table>

