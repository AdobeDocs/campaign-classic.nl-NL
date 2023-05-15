---
product: campaign
title: Informatie over Adobe Experience Cloud-triggers
description: Aan de slag met Adobe Experience Cloud Triggers-implementatie
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 8%

---

# Werken met campagne- en Experience Cloud-triggers{#about-adobe-experience-triggers}



[!DNL Triggers] is een integratie tussen Adobe Campaign en Adobe Analytics die de pijpleiding gebruikt. De pijplijn haalt gebruikersacties of trekkers van uw website terug. Een achterlating van een winkelwagen is een voorbeeld van een trigger. Triggers worden in Adobe Campaign verwerkt om e-mails in bijna real-time te verzenden.

>[!CAUTION]
>
>Deze mogelijkheid is niet rechtstreeks beschikbaar als onderdeel van het product. Voor deze implementatie moet u eerst een ticket openen met Adobe Support. U kunt dan de in dit [page](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] Voer marketingacties uit binnen een korte tijdspanne na de actie van een gebruiker. De gemiddelde responstijd is minder dan een uur.

Het staat voor meer flexibele integratie toe aangezien de configuratie minimaal is en een derde niet betrokken is.
Ook wordt steun verleend aan grote verkeersvolumes zonder dat dit van invloed is op de prestaties van marketingactiviteiten. De integratie kan bijvoorbeeld een miljoen triggers per uur verwerken.

## [!DNL Triggers] architectuur {#triggers-architecture}

De [!DNL pipelined] -proces wordt altijd uitgevoerd op de Adobe Campaign-marketingserver. Het verbindt met de pijpleiding, wint de gebeurtenissen terug, en verwerkt hen onmiddellijk.

![](assets/triggers_2.png)

De [!DNL pipelined] proces meldt zich aan bij de Experience Cloud gebruikend de authentificatiedienst en verzendt een privé sleutel. De verificatieservice retourneert een token. Het token wordt gebruikt voor verificatie bij het ophalen van de gebeurtenissen.

Voor meer informatie over authentificatie, verwijs naar dit [page](../../integrations/using/configuring-adobe-io.md).
