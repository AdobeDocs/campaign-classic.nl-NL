---
product: campaign
title: Berichtencentrum (uitvoering)
description: Berichtencentrum (uitvoering)
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 9%

---


# Berichtencentrum (uitvoering){#message-center-execution}

![](../../assets/common.svg)

De hieronder beschreven workflows worden geïnstalleerd met de **Berichtcentrum - uitvoering** standaard invoegtoepassing.

Raadpleeg de volgende secties voor meer informatie, afhankelijk van uw campagneversie:

![](assets/do-not-localize/v7.jpeg)[  Documentatie voor Campaign v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[  Documentatie voor Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Gebeurtenisstatus bijwerken</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> Met deze workflow kunt u een status aan een gebeurtenis toewijzen. Gebeurtenisstatussen zijn als volgt:<br /> 
    <ul> 
     <li> <p><strong>In behandeling</strong>: de gebeurtenis bevindt zich in een wachtrij. Er is nog geen berichtsjabloon aan gekoppeld.</p> </li> 
     <li> <p><strong>In behandeling</strong>: Als de gebeurtenis zich in een wachtrij bevindt, is er een berichtsjabloon aan gekoppeld en wordt deze momenteel verwerkt door de levering.</p> </li> 
     <li> <p><strong>Verzonden</strong>: deze status wordt gekopieerd uit de leveringslogboeken. Dit betekent dat de levering is verzonden.</p> </li> 
     <li> <p><strong>Genegeerd door levering</strong>: deze status wordt gekopieerd uit de leveringslogboeken. Het betekent dat de levering is genegeerd.</p> </li> 
     <li> <p><strong>Afleveringsfout</strong>: deze status wordt gekopieerd uit de leveringslogboeken. Het betekent dat de levering is mislukt.</p> </li> 
     <li> <p><strong>Gebeurtenis niet gedekt</strong>: de gebeurtenis is niet gekoppeld aan een berichtsjabloon. De gebeurtenis wordt niet opnieuw verwerkt.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Batchgebeurtenissen verwerken</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> Met deze workflow kunt u batchgebeurtenissen in een wachtrij plaatsen voordat u ze aan een berichtsjabloon koppelt. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Real-time gebeurtenissen verwerken</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> Dit werkschema laat u gebeurtenissen in real time in een rij zetten alvorens hen met een berichtmalplaatje te associëren. <br /> </td> 
  </tr> 
 </tbody> 
</table>

