---
product: campaign
title: Schema’s opnieuw genereren
description: Schema’s opnieuw genereren
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 7%

---

# Schema’s opnieuw genereren{#regenerating-schemas}

![](../../assets/v7-only.svg)

Wanneer u een schema wijzigt en de wijzigingen opslaat, wordt het uitgebreide schema automatisch gegenereerd. Desalniettemin, kunt u schema&#39;s moeten manueel regenereren om wijzigingen toe te passen. Dit doet u als volgt:

1. Selecteer de schema&#39;s die u opnieuw moet genereren.
1. Klik met de rechtermuisknop en kies **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Klikken **[!UICONTROL OK]** om het proces te bevestigen en te starten.

U kunt de structuur van het gegenereerde schema vervolgens controleren op de tabbladen Voorbeeld en Documentatie. Raadpleeg voor meer informatie de [Beginselen](../../configuration/using/data-schemas.md#principles) sectie.

>[!NOTE]
>
>Als u het opnieuw genereren van alle schema&#39;s moet forceren, bijvoorbeeld om bepaalde afhankelijkheidsproblemen in de omgekeerde koppelingen op te lossen, kunt u de volgende opdracht starten vanaf de Adobe Campaign-toepassingsserver:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>Vervolgens moet u de Adobe Campaign-toepassingsserver opnieuw starten en de verbinding met de clientconsole verbreken of opnieuw tot stand brengen.
