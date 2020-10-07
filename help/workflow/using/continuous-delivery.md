---
title: Doorlopende levering
seo-title: Doorlopende levering
description: Doorlopende levering
seo-description: null
page-status-flag: never-activated
uuid: af8b4582-299e-47f9-9819-987b35db94ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9d80be19-8dde-4278-ab5f-23f364fe422e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---


# Doorlopende levering{#continuous-delivery}

Met een actie **Ononderbroken leveringstype** kunt u nieuwe ontvangers toevoegen aan een bestaande levering. Met dit leveringstype hoeft u niet telkens een nieuwe levering te maken: Deze modus is vaak efficiënter, met name voor kleine waarschuwingen of meldingen die zo nodig worden verzonden. Op een niveau van het leveringsmalplaatje, kunt u een manuscript specificeren om het etiket (en de campagnemap) van de bijbehorende levering te berekenen. Als in het script een levering wordt berekend die nog niet bestaat, wordt deze direct gemaakt.

![](assets/edit_diffusion_fil.png)

De **[!UICONTROL Process errors]** optie geeft een bepaalde overgang weer die wordt geactiveerd wanneer een fout wordt gegenereerd. In dit geval gaat de workflow niet naar de foutmodus en gaat deze verder met de uitvoering.

Fouten waarmee rekening wordt gehouden, zijn fouten in het bestandssysteem (het bestand kan niet worden verplaatst, de map kan niet worden geopend, enz.).

Deze optie verwerkt geen fouten met betrekking tot activiteitsconfiguratie, d.w.z. ongeldige waarden.

## Invoerparameters {#input-parameters}

* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.

Alleen als de **[!UICONTROL Specified by the inbound event]** optie is geselecteerd.

## Uitvoerparameters {#output-parameters}

* tableName
* schema
* recCount

Deze reeks van drie waarden identificeert het doel dat uit de levering tijdens de vlucht voortvloeit. **[!UICONTROL tableName]** is de naam van de lijst die de herkenningstekens van het doel memoriseert, **[!UICONTROL schema]** is het schema van de bevolking (gewoonlijk nms:ontvanger) en **[!UICONTROL recCount]** is het aantal elementen in de lijst.

De overgang verbonden aan het complement heeft de zelfde parameters.

## Hoe te opstelling een ononderbroken levering

Deze sectie verklaart hoe te opstelling een ononderbroken levering.

De **ononderbroken levering** laat u nieuwe ontvangers aan een bestaande levering toevoegen en vermijdt u het moeten tot een nieuwe levering leiden telkens als een nieuwe ontvanger wordt toegevoegd. U kunt creatief direct in de campagnewerkschema bijwerken en het zal het malplaatje in de omslag van het Middel van het leveringsmalplaatje bijwerken.

Een ononderbroken levering zal tot één enkele levering en leveringslogboeken (wideLog) leiden en het volgen logboeken die erop wijzen dat één levering wordt toegevoegd telkens als het uitvoert.

![Doorlopende levering](assets/delivery_continuous.jpg)

Deze video toont hoe te om een ononderbroken levering met een stijgende vraag te vormen.

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)
