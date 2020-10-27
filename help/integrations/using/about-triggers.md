---
title: Informatie over Adobe Experience Manager
seo-title: Informatie over Adobe Experience Manager
description: Informatie over Adobe Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
translation-type: tm+mt
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 1%

---


# Informatie over Adobe Experience Cloud-triggers{#about-adobe-experience-triggers}

[!DNL Triggers] is een integratie tussen Adobe Campaign en Adobe Analytics die de pijpleiding gebruikt. De pijplijn haalt gebruikersacties of trekkers van uw website terug. Een achterlating van een winkelwagen is een voorbeeld van een trigger. Triggers worden in Adobe Campaign verwerkt om e-mails in bijna real-time te verzenden.

[!DNL Triggers] Voer marketingacties uit binnen een korte tijdspanne na de actie van een gebruiker. De gemiddelde responstijd is minder dan een uur.

Het staat voor meer flexibele integratie toe aangezien de configuratie minimaal is en een derde niet betrokken is.
Ook wordt steun verleend aan grote verkeersvolumes zonder dat dit van invloed is op de prestaties van marketingactiviteiten. De integratie kan bijvoorbeeld een miljoen triggers per uur verwerken.

## [!DNL Triggers] architectuur {#triggers-architecture}

Het [!DNL pipelined] proces wordt altijd uitgevoerd op de Adobe Campaign-marketingserver. Het verbindt met de pijpleiding, wint de gebeurtenissen terug, en verwerkt hen onmiddellijk.

![](assets/triggers_2.png)

Het [!DNL pipelined] proces logt aan de Experience Cloud binnen gebruikend een authentificatiedienst en verzendt een privé sleutel. De verificatieservice retourneert een token. Het token wordt gebruikt voor verificatie bij het ophalen van de gebeurtenissen.

For more information on authentication, refer to this [page](../../integrations/using/configuring-adobe-io.md).

>[!NOTE]
>
>De verdere verwerking van gebeurtenissen wordt gedaan als deel van het Pakket ACX dat buiten de standaardimplementatie wordt verstrekt. De ontvangen gebeurtenis wordt direct verwerkt met behulp van JavaScript-code. Deze wordt opgeslagen in een databasetabel zonder dat er in realtime verdere verwerking plaatsvindt. De triggers worden gebruikt voor het activeren van een campagneworkflow die e-mails verzendt. De campagne is zo ingesteld dat de klant die de gebeurtenis heeft geactiveerd, een e-mail ontvangt.
