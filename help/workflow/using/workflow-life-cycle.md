---
solution: Campaign Classic
product: campaign
title: Levenscyclus van workflow
description: Meer informatie over de levenscyclus van een workflow
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---


# Levenscyclus van workflow {#workflow-life-cycle}

De workflowcyclus bestaat uit drie hoofdstappen.

* **Wordt bewerkt**

   Dit is de eerste ontwerpfase: Als er een nieuwe workflow wordt gemaakt, wordt de status ervan bewerkt. De workflow wordt nog niet door de server afgehandeld en kan zonder risico worden gewijzigd.

* **Gestart**

   Zodra de eerste ontwerpfase is voltooid, kan de workflow worden gestart. In deze fase, wordt de instantie behandeld door de server en de individuele taken worden uitgevoerd. De workflow kan nog steeds met bepaalde voorzorgen worden aangepast.

* **Voltooid**

   Een workflow is &#39;voltooid&#39; wanneer er geen taken meer worden uitgevoerd of wanneer een operator de instantie expliciet heeft gestopt.

De activiteiten **Start** en **Delivery** worden bijvoorbeeld beschreven terwijl de activiteit **Approval** in de onderstaande workflow knippert.

![](assets/new-workflow-6.png)

Dit betekent dat de eerste twee activiteiten met succes zijn uitgevoerd en dat de goedkeuring in uitvoering is, d.w.z. dat zij is gecreëerd maar nog niet is voltooid.

De tekens **574 -Ok** die boven de overgang na de activiteit **Delivery** worden weergegeven, betekenen dat de voorbereiding van de levering gericht is op 574 ontvangers en dat de bewerking met succes is voltooid. Deze informatie, die aan de overgangen wordt toegevoegd wanneer zij worden uitgevoerd, wordt berekend door de activiteiten die gegevens verwerken.

De werkstroom is begonnen en wacht op een exploitant die tot de groep behoort die in **Goedkeuring** activiteit wordt gespecificeerd om een besluit te nemen. De tot de groep behorende exploitanten die een e-mailadres of mobiel telefoonnummer hebben, worden op de hoogte gesteld.

Operator management is gedetailleerd in deze [sectie](../../platform/using/access-management.md).

Raadpleeg [deze sectie](../../workflow/using/monitoring-workflow-execution.md) voor meer informatie over hoe u workflows kunt controleren.
