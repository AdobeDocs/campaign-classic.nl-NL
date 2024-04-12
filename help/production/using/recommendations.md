---
product: campaign
title: Aanbevelingen
description: Aanbevelingen
feature: Monitoring
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 3%

---

# Aanbevelingen{#recommendations}



Adobe Campaign is een zeer transactioneel systeem (OLTP-database). Dit betekent dat de onderliggende database vaak wordt bijgewerkt, wat resulteert in een verslechtering van de prestaties in de loop der tijd. Om dit soort uitgifte te voorkomen, is regelmatig onderhoud van de database nodig.

>[!IMPORTANT]
>
>Een database functioneert alleen optimaal als deze regelmatig wordt onderhouden. Het automatische onderhoud dat door sommige RDBMS wordt aangeboden, is onvoldoende en vervangt geen diepgaand onderhoud, zoals bij alle transactionele beheersystemen van de relationele database.
>  
>De in dit document beschreven procedures zijn aanbevelingen. De plannen van het onderhoud zijn de verantwoordelijkheid van uw gegevensbestandbeheerder, die uw eerste contact in het geval van problemen moet zijn.
