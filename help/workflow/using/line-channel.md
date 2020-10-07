---
title: LINE-kanaal
seo-title: LINE-kanaal
description: LINE-kanaal
seo-description: null
page-status-flag: never-activated
uuid: 0b0e34b2-7ee9-456a-9ed9-7ede889584b6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 367314a2-eb6d-4710-8a47-5a51049ad924
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 13%

---


# LINE-kanaal{#line-channel}

De hieronder beschreven workflows worden standaard geïnstalleerd met de module **LINE-kanaal** . For more on this module, refer to this [section](../../delivery/using/line-channel.md).

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

