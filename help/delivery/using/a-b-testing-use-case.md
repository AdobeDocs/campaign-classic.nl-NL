---
product: campaign
title: Gebruiksscenario voor tests door AB
description: Leer hoe u A/B-tests kunt uitvoeren met een speciale praktijkcase
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: A/B Testing
role: User
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 5%

---

# AB-tests: A/B Testen van dit gebruiksgeval {#ab-testing-use-case}

In dit geval gaan we twee inhoud van de e-maillevering vergelijken via een doelworkflow. Het bericht en de tekst zijn identiek in beide leveringen: alleen de layout wordt gewijzigd.

De beoogde populatie is verdeeld in drie: twee testgroepen en de resterende populatie. Een verschillende versie van de levering wordt verzonden naar elke testgroep.

Na de levering, wordt een 5 dagen wachttijdperiode gevormd alvorens de resultaten van de beste open tarieven te verzamelen. De inhoud van de levering met de hoogste score wordt dan teruggewonnen door een manuscript en verzonden naar de bevolking die niet als testgroep werd gebruikt.

Houd er rekening mee dat de criteria die bepalen welke levering het beste is, kunnen worden aangepast aan uw behoeften. Het kan de open tarief, het klikthrough tarief, het abonnementstarief, reactiviteit, enz. zijn.

Bovendien had de in dit gebruiksgeval gedetailleerde test alleen betrekking op twee leveringen, maar u kunt zo veel versies testen als nodig is. Voeg gewoon activiteiten toe aan de workflow.

De belangrijkste stappen voor dit gebruik zijn:

* [Stap 1: een doelworkflow maken](a-b-testing-uc-targeting-workflow.md)
* [Stap 2: bevolkingsmonsters configureren](a-b-testing-uc-population-samples.md)
* [Stap 3: twee leveringssjablonen maken](a-b-testing-uc-delivery-templates.md)
* [Stap 4: Configureer de leveringen in de workflow](a-b-testing-uc-configuring-deliveries.md)
* [Stap 5: Maak het script](a-b-testing-uc-script.md)
* [Stap 6: Definiëren van de uiteindelijke levering](a-b-testing-uc-final-delivery.md)
* [Stap 7: De workflow starten](a-b-testing-uc-start-workflow.md)
* [Stap 8: Analyseer het resultaat](a-b-testing-uc-analyzing.md)

**Verwante onderwerpen:**

* [Aan de slag met A/B-tests](get-started-a-b-testing.md)
* [A/B-tests configureren](configuring-a-b-testing.md)
