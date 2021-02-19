---
solution: Campaign Classic
product: campaign
title: Over dit gebruiksgeval
description: Leer hoe u een A/B-test uitvoert met een speciale praktijkcase.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# Over dit gebruiksgeval {#about-use-case}

In dit geval gaan we twee inhoud van de e-maillevering vergelijken via een doelworkflow. Het bericht en de tekst zijn identiek in beide leveringen: alleen de layout wordt gewijzigd.

De doelgroep bestaat uit drie groepen: twee testgroepen en de resterende populatie. Een verschillende versie van de levering wordt verzonden naar elke testgroep.

Na de levering, wordt een 5 dagen wachttijdperiode gevormd alvorens de resultaten van de beste open tarieven te verzamelen. De inhoud van de levering met de hoogste score wordt dan teruggekregen door een manuscript en verzonden naar de bevolking die niet als testgroep werd gebruikt.

Houd er rekening mee dat de criteria die bepalen welke levering het beste is, kunnen worden aangepast aan uw behoeften. Het kan de open tarief, het klikthrough tarief, het abonnementstarief, reactiviteit, enz. zijn.

Bovendien had de in dit gebruiksgeval gedetailleerde test alleen betrekking op twee leveringen, maar u kunt zo veel versies testen als nodig is. Voeg gewoon activiteiten toe aan de workflow.

De belangrijkste stappen voor dit gebruik zijn:

* [Stap 1: Een doelworkflow maken](#step-1--creating-a-targeting-workflow)
* [Stap 2: Demonstratiemonsters configureren](#step-2--configuring-population-samples)
* [Stap 3: Twee leveringssjablonen maken](#step-3--creating-two-delivery-templates)
* [Stap 4: De leveringen in de workflow configureren](#step-4--configuring-the-deliveries-in-the-workflow)
* [Stap 5: Het script maken](#step-5--creating-the-script)
* [Stap 7: De workflow starten](#step-7--starting-the-workflow)
* [Stap 8: Analyseer het resultaat](#step-8--analyzing-the-result).

**Verwante onderwerpen:**

* [Aan de slag met A/B-tests](../../delivery/using/get-started-a-b-testing.md)
* [A/B-tests configureren](../../delivery/using/configuring-a-b-testing.md)
