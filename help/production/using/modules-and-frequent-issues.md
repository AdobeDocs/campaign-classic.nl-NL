---
product: campaign
title: Modules en frequente problemen
description: Modules en frequente problemen
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 5%

---

# Modules en frequente problemen{#modules-and-frequent-issues}



Hier volgt een lijst met modules die worden beïnvloed door frequente problemen:

<table> 
 <thead> 
  <tr> 
   <th> Module </th> 
   <th> Uitvoeringsbereik </th> 
   <th> Problemen oplossen </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> export </td> 
   <td> Uitvoering van een exportproces<br /> </td> 
   <td> De operator die deze export heeft gepland, moet deze opnieuw starten. Delta of volledige herstart.<br /> </td> 
  </tr> 
  <tr> 
   <td> import </td> 
   <td> Uitvoering van een invoerproces<br /> </td> 
   <td> De operator die deze export heeft gepland, moet deze opnieuw starten. Controleer de database op duplicaten.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Het lezen van de stuiterende brievenbus<br /> </td> 
   <td> Controleer deze module als de stuiterende berichten niet meer door:sturen.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Levert e-mails<br /> </td> 
   <td> Schakel deze module in als er geen e-mailberichten meer worden verzonden.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Handhaaft MTA verbindingsstatistieken<br /> </td> 
   <td> Schakel deze module in als er geen e-mailberichten meer worden verzonden.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Log schrijven<br /> </td> 
   <td> Als sommige logboeken in de logboekdossiers ontbreken, controleer om ervoor te zorgen dat de module haven 6666 gebruikt. Zie <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Lijst met open poorten</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> bijhouden </td> 
   <td> Logbestanden voor bijhouden consolideren en ophalen<br /> </td> 
   <td> Controleer deze module als het volgen logboeken niet meer door:sturen.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Logboek bijhouden bij schrijven en wissen van server<br /> </td> 
   <td> Controleer deze module als het volgen logboeken niet meer door:sturen en er geen sporen van logboeken in de dossiers op de server zijn. Zie <a href="../../production/using/tracking-logs-issues.md" target="_blank">Problemen met het bijhouden van logboeken</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> waakhond </td> 
   <td> Instantie voor opstarten en controleren<br /> </td> 
   <td> Controleer deze module als er geen processen starten.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Toepassingsserver (HTTP en SOAP)<br /> </td> 
   <td> Controleer deze module als de console en de Webverbindingen niet werken en teweegbrengen <strong>xtk:sessie</strong> tekstfout<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Bepaalt de uitvoering van workflowinstanties.<br /> </td> 
   <td> Start deze module opnieuw als u problemen ondervindt. Indien nodig de procedure toepassen om de nauwkeurigheid van de in de <a href="../../production/using/log-precision.md" target="_blank">Logboekprecisie</a> sectie.<br /> </td> 
  </tr> 
 </tbody> 
</table>
