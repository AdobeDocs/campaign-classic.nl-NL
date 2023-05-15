---
product: campaign
title: Aanbevelingen
description: Aanbevelingen
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# Aanbevelingen{#recommendations}



Adobe Campaign is een zeer transactioneel systeem (OLTP-database). Dit betekent dat de onderliggende database vaak wordt bijgewerkt, wat resulteert in een verslechtering van de prestaties in de loop der tijd. Om dit soort uitgifte te voorkomen, is regelmatig onderhoud van de database nodig.

>[!IMPORTANT]
>
>Een database functioneert alleen optimaal als deze regelmatig wordt onderhouden. Het automatische onderhoud dat door sommige RDBMS wordt aangeboden, is onvoldoende en vervangt geen diepgaand onderhoud, zoals bij alle transactionele beheersystemen van de relationele database.
>  
>De in dit document beschreven procedures zijn aanbevelingen. De plannen van het onderhoud zijn de verantwoordelijkheid van uw gegevensbestandbeheerder, die uw eerste contact in het geval van problemen moet zijn.
