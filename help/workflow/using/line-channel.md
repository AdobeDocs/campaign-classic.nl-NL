---
product: campaign
title: LINE-kanaal
description: LINE-kanaal
feature: Workflows
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 2%

---


# LINE-kanaal{#line-channel}



De hieronder beschreven workflows worden geïnstalleerd met de **LINE-kanaal** module standaard. Raadpleeg deze voor meer informatie over deze module [sectie](../../delivery/using/line-channel.md).

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
   <td> Deze werkstroom verfrist het toegangstoken aan LIJN V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Geblokkeerde lijngebruikers verwijderen</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> Deze workflow zorgt ervoor dat de gegevens van de gebruikers van de LIJN V2 worden verwijderd nadat ze de officiële account van de LIJN gedurende 180 dagen hebben geblokkeerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID naar migratie naar LineUserID</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> Deze workflow genereert de LINE V2-gebruikers-id voor migratie van LIJN V1 naar LIJN V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

