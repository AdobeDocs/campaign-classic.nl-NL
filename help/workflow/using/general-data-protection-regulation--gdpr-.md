---
product: campaign
title: Workflows voor de privacygegevensbeschermingsverordening
description: Meer informatie over de workflows van de privacyverordening
hide: true
hidefromtoc: true
feature: Workflows, Privacy
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 2%

---


# Privacygegevensbeschermingsverordening{#general-data-protection-regulation-gdpr}



De hieronder gedetailleerde werkschema&#39;s worden geïnstalleerd met de **module van de Verordening van de Bescherming van Gegevens van de Privacy** door gebrek. Voor meer op deze module, verwijs naar dit [ artikel ](https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong> Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> verzamel privacyverzoeken </span> <br /> </td> 
   <td> <span class="uicontrol"> collectPrivacyRequests </span> <br /> </td> 
   <td> Dit werkschema produceert de gegevens van de ontvanger die in Adobe Campaign worden opgeslagen en stelt het voor download in het scherm van het privacyverzoek beschikbaar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Schrap privacy vraagt gegevens </span> <br /> </td> 
   <td> <span class="uicontrol"> deletePrivacyRequestsData </span> <br /> </td> 
   <td> Dit werkschema schrapt de gegevens van de ontvanger die in Adobe Campaign worden opgeslagen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> de verzoekschoonmaakbeurt van de Privacy </span> <br /> </td> 
   <td> <span class="uicontrol"> cleanPrivacyRequests </span> <br /> </td> 
   <td> Dit werkschema wist de dossiers van het toegangsverzoek die ouder zijn dan 90 dagen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

