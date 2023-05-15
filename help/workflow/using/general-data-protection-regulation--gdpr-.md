---
product: campaign
title: Workflows voor privacygegevensbeschermingsverordening
description: Meer informatie over de workflows van de privacygegevensbeschermingsverordening
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Privacy
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 10%

---


# Verordening inzake bescherming van privacydata{#general-data-protection-regulation-gdpr}



De hieronder beschreven workflows worden geïnstalleerd met de **Privacy Data Protection-verordening** module standaard. Voor meer informatie over deze module, verwijs naar dit [artikel](https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Verzoeken om privacy verzamelen</span> <br /> </td> 
   <td> <span class="uicontrol">collectPrivacyRequests</span> <br /> </td> 
   <td> Met deze workflow worden de gegevens van de ontvanger gegenereerd die in Adobe Campaign zijn opgeslagen en kunnen deze worden gedownload op het scherm van de privacyaanvraag.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Gegevens over privacyverzoeken verwijderen</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> Deze workflow verwijdert de gegevens die de ontvanger in Adobe Campaign heeft opgeslagen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Opmaak van privacyverzoek</span> <br /> </td> 
   <td> <span class="uicontrol">cleanPrivacyRequests</span> <br /> </td> 
   <td> Deze workflow wist de bestanden met toegangsverzoeken die ouder zijn dan 90 dagen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

