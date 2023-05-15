---
product: campaign
title: Aan de slag met A/B-tests
description: Meer informatie over A/B-tests in Campagne
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: ae046ef6-d850-4222-b82c-8ef5b3da7037
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 3%

---

# Aan de slag met A/B-tests {#get-started-a-b-testing}



Met A/B-tests kunt u meerdere versies van een levering vergelijken met elkaar om te bepalen welke versie de grootste invloed heeft op de doelpopulatie.

Hiervoor moet u eerst meerdere varianten van de levering definiëren. Elke variant wordt dan verzonden naar bevolkingssteekproeven om te bepalen welke beter afhankelijk van de criteria van uw keus (opent, spamklachten, klikt op een specifieke verbinding,...) presteert.

In het onderstaande voorbeeld is de leveringsdoelstelling opgesplitst in twee groepen, die elk 50% van de doelpopulatie vertegenwoordigen. Elke groep ontvangt twee versies van de levering met twee verschillende promotieaanbiedingen. Nadat de levering wordt verzonden, wordt geconcludeerd dat de variant A beter presteerde, die op het aantal kliks op de promotieaanbiedingen wordt gebaseerd.

![](assets/a-b-testing-schema.png)

Met Campaign Classic, wordt A/B het testen uitgevoerd door werkschema&#39;s, waar u de te richten bevolking evenals de groepen specificeert die elke variant zullen ontvangen (zie [A/b-tests configureren](configuring-a-b-testing.md)).

De belangrijkste stappen zijn:

1. **Doel** de gewenste bevolking.
1. **De bevolking splitsen** in subsets waarop u de varianten van uw levering zult testen.

   U kunt bijvoorbeeld een versie van een levering verzenden naar een klein deel van de doelpopulatie en een andere versie naar de resterende populatie. Dit staat u toe om een nieuwe versie van een levering in tegenstelling tot de levering te testen die gewoonlijk naar uw klanten wordt verzonden. U kunt de doelpopulatie ook opsplitsen in drie groepen om ze drie verschillende versies van een levering te sturen.

1. **Meerdere versies maken** van de levering voor elke deelverzameling. De te testen variant kan het onderwerp, de berichtinhoud, de naam van de afzender enz. zijn.
1. Start de workflow en gebruik vervolgens de knop **leveringslogs** het gedrag van de subsets met elke variant te analyseren.

>[!NOTE]
>
>Met workflows kunt u ook uw processen automatiseren door automatisch de variant te identificeren die beter presteerde en deze vervolgens naar de resterende populatie te verzenden. Raadpleeg voor meer informatie deze [use case](a-b-testing-use-case.md).
