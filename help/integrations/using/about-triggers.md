---
product: campaign
title: Informatie over Adobe Experience Cloud-triggers
description: Aan de slag met Adobe Experience Cloud Triggers-implementatie
feature: Triggers
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 271e0f9fde0cbfb016e201c8390b26673d8fc696
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 7%

---

# Werken met Triggers voor campagnes en Experiencen Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] is een integratie tussen Adobe Campaign en Adobe Analytics door middel van de pijpleiding. De pijplijn haalt gebruikersacties of trekkers van uw website terug. Een achterlating van een winkelwagen is een voorbeeld van een trigger. Triggers worden in Adobe Campaign verwerkt om e-mails in bijna real-time te verzenden.

>[!CAUTION]
>
>Deze mogelijkheid is niet rechtstreeks beschikbaar als onderdeel van het product. Voor deze implementatie werkt u samen met uw Adobe/klantenservice. U kunt dan de in dit [page](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] Voer marketingacties uit binnen een korte tijdspanne na de actie van een gebruiker. De gemiddelde responstijd is minder dan een uur.

Het staat voor meer flexibele integratie toe aangezien de configuratie minimaal is en een derde niet betrokken is.
Ook wordt steun verleend aan grote verkeersvolumes zonder dat dit van invloed is op de prestaties van marketingactiviteiten. De integratie kan bijvoorbeeld een miljoen triggers per uur verwerken.

![](assets/do-not-localize/book.png) Ontdek hoe u [een trigger voor een Experience Cloud maken](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html) en kritieke consumentengedragingen identificeren, definiëren en bewaken.

## [!DNL Triggers] architectuur {#triggers-architecture}

De [!DNL pipelined] -proces wordt altijd uitgevoerd op de Adobe Campaign-marketingserver. Het verbindt met de pijpleiding, wint de gebeurtenissen terug, en verwerkt hen onmiddellijk.

![](assets/triggers_2.png)

De [!DNL pipelined] proces het programma opent aan het Experience Cloud gebruikend de authentificatiedienst en verzendt een privé sleutel. De verificatieservice retourneert een token. Het token wordt gebruikt voor verificatie bij het ophalen van de gebeurtenissen.

Raadpleeg deze voor meer informatie over verificatie [page](../../integrations/using/configuring-adobe-io.md).
