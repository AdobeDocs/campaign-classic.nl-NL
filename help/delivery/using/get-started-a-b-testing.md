---
product: campaign
title: Aan de slag met A/B-tests
description: Meer informatie over A/B testen in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: ae046ef6-d850-4222-b82c-8ef5b3da7037
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 3%

---

# Aan de slag met A/B-tests {#get-started-a-b-testing}

![](../../assets/common.svg)

Met A/B-tests kunt u meerdere versies van een levering vergelijken met elkaar om te bepalen welke versie de grootste invloed heeft op de doelpopulatie.

Hiervoor moet u eerst meerdere varianten van de levering definiëren. Elke variant wordt dan verzonden naar bevolkingssteekproeven om te bepalen welke beter afhankelijk van de criteria van uw keus (opent, spamklachten, klikt op een specifieke verbinding,...) presteert.

In het onderstaande voorbeeld is de leveringsdoelstelling opgesplitst in twee groepen, die elk 50% van de doelpopulatie vertegenwoordigen. Elke groep ontvangt twee versies van de levering met twee verschillende promotieaanbiedingen. Nadat de levering wordt verzonden, wordt geconcludeerd dat de variant A beter presteerde, die op het aantal kliks op de promotieaanbiedingen wordt gebaseerd.

![](assets/a-b-testing-schema.png)

Met Campaign Classic, A/B wordt het testen uitgevoerd door werkschema&#39;s, waar u de bevolking om evenals de groepen specificeert te richten die elke variant zullen ontvangen (zie [Vormend a/b het testen](configuring-a-b-testing.md)).

De belangrijkste stappen zijn:

1. **De** gewenste bevolking.
1. **Splits de** bevolking in subsets waarop u de varianten van uw levering zult testen.

   U kunt bijvoorbeeld een versie van een levering verzenden naar een klein deel van de doelpopulatie en een andere versie naar de resterende populatie. Dit staat u toe om een nieuwe versie van een levering in tegenstelling tot de levering te testen die gewoonlijk naar uw klanten wordt verzonden. U kunt de doelpopulatie ook opsplitsen in drie groepen om ze drie verschillende versies van een levering te sturen.

1. **Maak meerdere** versies van de levering voor elke subset. De te testen variant kan het onderwerp, de berichtinhoud, de naam van de afzender enz. zijn.
1. Start de workflow en gebruik vervolgens de **leveringslogs** om het gedrag van de subsets met elke variant te analyseren.

>[!NOTE]
>
>Met workflows kunt u ook uw processen automatiseren door automatisch de variant te identificeren die beter presteerde en deze vervolgens naar de resterende populatie te verzenden. Raadpleeg voor meer informatie deze [use case](a-b-testing-use-case.md).
