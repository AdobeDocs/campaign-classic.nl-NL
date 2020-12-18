---
solution: Campaign Classic
product: campaign
title: Schema’s opnieuw genereren
description: Schema’s opnieuw genereren
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---


# Schema’s opnieuw genereren{#regenerating-schemas}

Wanneer u een schema wijzigt en de wijzigingen opslaat, wordt het uitgebreide schema automatisch gegenereerd. Desalniettemin, kunt u schema&#39;s moeten manueel regenereren om wijzigingen toe te passen. Dit doet u als volgt:

1. Selecteer de schema&#39;s die u opnieuw moet genereren.
1. Klik met de rechtermuisknop en kies **[!UICONTROL Actions > Regenerate selected schemas...]**.
1. Klik **[!UICONTROL OK]** om het proces te bevestigen en te lanceren.

U kunt de structuur van het gegenereerde schema vervolgens controleren op de tabbladen Voorbeeld en Documentatie. Raadpleeg voor meer informatie de sectie [Principles](../../configuration/using/data-schemas.md#principles).

>[!NOTE]
>
>Als u het opnieuw genereren van alle schema&#39;s moet forceren, bijvoorbeeld om bepaalde afhankelijkheidsproblemen in de omgekeerde koppelingen op te lossen, kunt u de volgende opdracht starten vanaf de Adobe Campaign-toepassingsserver:
>
>**nlserver config -postupgrade -instance:&quot;&lt;instance_name>&#39; -force**
>
>Vervolgens moet u de Adobe Campaign-toepassingsserver opnieuw starten en de verbinding met de clientconsole verbreken of opnieuw tot stand brengen.
