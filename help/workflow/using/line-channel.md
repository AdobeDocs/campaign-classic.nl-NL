---
product: campaign
title: LINE-kanaal
description: LINE-kanaal
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 11%

---


# LINE-kanaal{#line-channel}



De hieronder beschreven workflows worden geïnstalleerd met de **LINE-kanaal** module standaard. Voor meer informatie over deze module, verwijs naar dit [sectie](../../delivery/using/line-channel.md).

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

