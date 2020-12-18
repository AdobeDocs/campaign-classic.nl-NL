---
solution: Campaign Classic
product: campaign
title: LINE-kanaal
description: LINE-kanaal
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 11%

---


# LINE-kanaal{#line-channel}

De hieronder beschreven workflows worden standaard geïnstalleerd met de module **LINE channel**. Voor meer op deze module, verwijs naar dit [sectie](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong>Interne naam</strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Update van toegangstoken LINE V2</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> Deze werkschema verfrist het toegangstoken aan LIJN V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Geblokkeerde lijngebruikers verwijderen</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> Deze workflow zorgt ervoor dat de gegevens van de gebruikers van de LINE V2 worden verwijderd nadat ze de officiële account van de LINE gedurende 180 dagen hebben geblokkeerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID naar migratie naar LineUserID</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> Deze workflow genereert de LINE V2-gebruikers-id voor migratie van LINE V1 naar LINE V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

