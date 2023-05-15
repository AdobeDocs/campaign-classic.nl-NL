---
product: campaign
title: Regeneratieschema's
description: Leer hoe u campagnereschema's opnieuw kunt genereren
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 2%

---

# Regeneratieschema&#39;s{#regenerating-schemas}

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
