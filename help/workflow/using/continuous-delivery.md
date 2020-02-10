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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Doorlopende levering{#continuous-delivery}

Met een actie **Ononderbroken leveringstype** kunt u nieuwe ontvangers toevoegen aan een bestaande levering. Met dit type levering hoeft u niet telkens een nieuwe levering te maken: Deze modus is vaak efficiënter, met name voor kleine waarschuwingen of meldingen die zo nodig worden verzonden. Op een niveau van het leveringsmalplaatje, kunt u een manuscript specificeren om het etiket (en de campagnemap) van de bijbehorende levering te berekenen. Als in het script een levering wordt berekend die nog niet bestaat, wordt deze direct gemaakt.

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
