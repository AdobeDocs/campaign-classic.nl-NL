---
title: Schema’s opnieuw genereren
seo-title: Schema’s opnieuw genereren
description: Schema’s opnieuw genereren
seo-description: null
page-status-flag: never-activated
uuid: 455c37f1-cbaf-4503-b2e9-5eec7fad6e97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 0f7c835e-b429-422b-87ae-1234c7dd8fe6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 8%

---


# Schema’s opnieuw genereren{#regenerating-schemas}

Wanneer u een schema wijzigt en de wijzigingen opslaat, wordt het uitgebreide schema automatisch gegenereerd. Desalniettemin, kunt u schema&#39;s moeten manueel regenereren om wijzigingen toe te passen. Dit doet u als volgt:

1. Selecteer de schema&#39;s die u opnieuw moet genereren.
1. Klik met de rechtermuisknop en kies **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Klik **[!UICONTROL OK]** om het proces te bevestigen en te lanceren.

U kunt de structuur van het gegenereerde schema vervolgens controleren op de tabbladen Voorbeeld en Documentatie. For more on this, refer to the [Principles](../../configuration/using/data-schemas.md#principles) section.

>[!NOTE]
>
>Als u het opnieuw genereren van alle schema&#39;s moet forceren, bijvoorbeeld om bepaalde afhankelijkheidsproblemen in de omgekeerde koppelingen op te lossen, kunt u de volgende opdracht starten vanaf de Adobe Campaign-toepassingsserver:
>
>**nlserver config -postupgrade -instance:`&lt;instance_name>&#39; -force**
>
>Vervolgens moet u de Adobe Campaign-toepassingsserver opnieuw starten en de verbinding met de clientconsole verbreken of opnieuw tot stand brengen.
