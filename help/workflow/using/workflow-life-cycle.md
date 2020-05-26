---
title: Levenscyclus van werkstroom
description: Meer informatie over de levenscyclus van een workflow.
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Levenscyclus van werkstroom {#workflow-life-cycle}

De workflowcyclus bestaat uit drie hoofdstappen.

* **Wordt bewerkt**

   Dit is de eerste ontwerpfase: Als er een nieuwe workflow wordt gemaakt, wordt de status ervan bewerkt. De workflow wordt nog niet door de server afgehandeld en kan zonder risico worden gewijzigd.

* **Gestart**

   Zodra de eerste ontwerpfase is voltooid, kan de workflow worden gestart. In deze fase, wordt de instantie behandeld door de server en de individuele taken worden uitgevoerd. De workflow kan nog steeds met bepaalde voorzorgen worden aangepast.

* **Voltooid**

   Een workflow is &#39;voltooid&#39; wanneer er geen taken meer worden uitgevoerd of wanneer een operator de instantie expliciet heeft gestopt.

De activiteiten **Start** en **Levering** worden bijvoorbeeld beschreven terwijl de activiteit **Goedkeuring** in de onderstaande workflow knippert.

![](assets/new-workflow-6.png)

Dit betekent dat de eerste twee activiteiten met succes zijn uitgevoerd en dat de goedkeuring in uitvoering is, d.w.z. dat zij is gecreëerd maar nog niet is voltooid.

De tekens **574 -Ok** boven de overgang na de **leveringsactiviteit** betekenen dat de voorbereiding van de levering gericht is op 574 ontvangers en dat de bewerking is voltooid. Deze informatie, die aan de overgangen wordt toegevoegd wanneer zij worden uitgevoerd, wordt berekend door de activiteiten die gegevens verwerken.

De workflow wordt gestart en er wordt gewacht tot een operator die behoort tot de groep die is opgegeven in de activiteit **Goedkeuring** , een beslissing neemt. De tot de groep behorende exploitanten die een e-mailadres of mobiel telefoonnummer hebben, worden op de hoogte gesteld.

Het beheer van de exploitant wordt gedetailleerd in deze [sectie](../../platform/using/access-management.md).

Raadpleeg [deze sectie](../../workflow/using/monitoring-workflow-execution.md)voor meer informatie over hoe u de workflows kunt controleren.
