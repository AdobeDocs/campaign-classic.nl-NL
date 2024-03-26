---
product: campaign
title: Informatie over Adobe Experience Cloud-triggers
description: Aan de slag met Adobe Experience Cloud Triggers-implementatie
feature: Triggers
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 7%

---

# Werken met Triggers voor campagnes en Experiencen Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] is een integratie tussen Adobe Campaign en Adobe Analytics door middel van de pijpleiding. De pijplijn haalt gebruikersacties of trekkers van uw website terug. Een achterlating van een winkelwagen is een voorbeeld van een trigger. Triggers worden in Adobe Campaign verwerkt om e-mails in bijna real-time te verzenden.

>[!CAUTION]
>
>Deze mogelijkheid is niet rechtstreeks beschikbaar als onderdeel van het product. Voor deze implementatie, moet u eerst een kaartje met de Steun van de Adobe openen. U kunt dan de in dit [page](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] Voer marketingacties uit binnen een korte tijdspanne na de actie van een gebruiker. De gemiddelde responstijd is minder dan een uur.

Het staat voor meer flexibele integratie toe aangezien de configuratie minimaal is en een derde niet betrokken is.
Ook wordt steun verleend aan grote verkeersvolumes zonder dat dit van invloed is op de prestaties van marketingactiviteiten. De integratie kan bijvoorbeeld een miljoen triggers per uur verwerken.

![](assets/do-not-localize/book.png) Ontdek hoe u [een trigger voor een Experience Cloud maken](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html) en kritieke consumentengedragingen identificeren, definiëren en bewaken.

## [!DNL Triggers] architectuur {#triggers-architecture}

De [!DNL pipelined] -proces wordt altijd uitgevoerd op de Adobe Campaign-marketingserver. Het verbindt met de pijpleiding, wint de gebeurtenissen terug, en verwerkt hen onmiddellijk.

![](assets/triggers_2.png)

De [!DNL pipelined] proces het programma opent aan het Experience Cloud gebruikend de authentificatiedienst en verzendt een privé sleutel. De verificatieservice retourneert een token. Het token wordt gebruikt voor verificatie bij het ophalen van de gebeurtenissen.

Raadpleeg deze voor meer informatie over verificatie [page](../../integrations/using/configuring-adobe-io.md).
