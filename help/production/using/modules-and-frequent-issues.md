---
solution: Campaign Classic
product: campaign
title: Modules en frequente problemen
description: Modules en frequente problemen
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
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
   <td> De operator die deze export heeft gepland, moet deze opnieuw starten. delta of volledige herstart.<br /> </td> 
  </tr> 
  <tr> 
   <td> import </td> 
   <td> Uitvoering van een importproces<br /> </td> 
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
   <td> Controleer deze module als de post niet meer wordt verzonden.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Behoudt MTA verbindingsstatistieken<br /> </td> 
   <td> Controleer deze module als de post niet meer wordt verzonden.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Logboek schrijven<br /> </td> 
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
   <td> Controleer deze module als het volgen logboeken niet meer door:sturen en er geen sporen van logboeken in de dossiers op de server zijn. Raadpleeg <a href="../../production/using/tracking-logs-issues.md" target="_blank">Problemen met bijhouden van logbestanden</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> waakhond </td> 
   <td> Instantie voor opstarten en controleren<br /> </td> 
   <td> Controleer deze module als geen processen beginnen.<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> Toepassingsserver (HTTP en SOAP)<br /> </td> 
   <td> Controleer deze module als de console en de Webverbindingen niet werken en een <strong>xtk activeren:session</strong> typefout<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Bepaalt de uitvoering van workflowinstanties.<br /> </td> 
   <td> Start deze module opnieuw als u problemen ondervindt. Indien nodig past u de procedure toe om de nauwkeurigheid van de logbestanden te verhogen die in de sectie <a href="../../production/using/log-precision.md" target="_blank">Logprecisie</a> worden beschreven.<br /> </td> 
  </tr> 
 </tbody> 
</table>

