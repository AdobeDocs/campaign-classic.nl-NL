---
product: campaign
title: Structuur van een gegevensschema
description: Structuur van een gegevensschema
feature: Custom Resources
role: Data Engineer, Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---

# Structuur van een gegevensschema{#structure-of-a-data-schema}

De structuur van een gegevensschema wordt weergegeven in de vorm van een boomstructuur. Als u het schema grafisch wilt weergeven in de Adobe Campaign-clientconsole, selecteert u het doelschema en klikt u op de knop **[!UICONTROL Structure]** subtab.

![](assets/d_ncs_integration_schema_arbo.png)

De velden worden standaard als eerste weergegeven (Actief, Geactiveerd, enz.) en in alfabetische volgorde. De volgende structurerende elementen komen (Postadres, Plaats), en tenslotte de verbindingen (E-mailinformatie, Omslag, enz.).

Primaire sleutels worden geïdentificeerd door een rode sleutel, en vreemde sleutels worden geïdentificeerd door een gele sleutel.

Koppelingen worden grafisch onderscheiden, afhankelijk van het feit of ze tot de tabel behoren. De items die uit de tabel beginnen, dat wil zeggen met de vreemde sleutel in de tabel, worden als eerste weergegeven (e-mailgegevens, map, land). &quot;Reverse&quot;inzamelingsverbindingen (Abonnement, Orders, enz.) worden aan het einde weergegeven.
