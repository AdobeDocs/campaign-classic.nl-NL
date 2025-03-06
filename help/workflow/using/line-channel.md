---
product: campaign
title: LINE-kanaal
description: LINE-kanaal
hide: true
hidefromtoc: true
feature: Workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 2%

---


# LINE-kanaal{#line-channel}



De hieronder gedetailleerde werkschema&#39;s worden geïnstalleerd met de **het kanaal van de LIJN** module door gebrek. Voor meer op deze module, verwijs naar deze [ sectie ](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Label</strong><br /> </td> 
   <td> <strong> Interne naam </strong><br /> </td> 
   <td> <strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> lijn V2 de update van het toegangstoken </span> <br /> </td> 
   <td> <span class="uicontrol"> updateLineV2AccessToken </span> <br /> </td> 
   <td> Dit werkschema verfrist het toegangstoken aan LIJN V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Schrap geblokkeerde gebruikers van de LIJN </span> <br /> </td> 
   <td> <span class="uicontrol"> deleteBlockedLineUsersV2 </span> <br /> </td> 
   <td> Dit werkschema zorgt ervoor dat de gegevens van de gebruikers van de LIJN V2 worden geschrapt nadat zij de officiële rekening van de LIJN 180 dagen hebben geblokkeerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MID aan migratie LineUserID </span> <br /> </td> 
   <td> <span class="uicontrol"> MIDToUserIDMigration </span> <br /> </td> 
   <td> Deze workflow genereert de LINE V2 gebruikers'-id voor migratie van LIJN V1 naar LIJN V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

