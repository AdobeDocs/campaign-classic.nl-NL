---
product: campaign
title: Best practices voor leveringen
description: Meer informatie over leveringsprestaties en aanbevolen procedures
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 3%

---

# Best practices voor leveringen {#delivery-performances}

>[!NOTE]
>
>De uitvoerige begeleiding op leveringsprestaties en beste praktijken wordt gedocumenteerd in de [ pagina van de Beste praktijken van de Lading van de Campagne v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices). Deze inhoud is van toepassing op gebruikers van Campaign Classic v7 en Campagne v8.
>
>Deze pagina documenteert **Campaign Classic v7-specifieke prestatiesconfiguraties** voor hybride en op-gebouw plaatsingen.

Voor uitvoerige beste praktijken op leveringsprestaties, platformoptimalisering, quarantainebeheer, gegevensbestandonderhoud, en het plannen van aanbevelingen, verwijs naar de [ documentatie van de beste praktijken van de Bevordering van de Campagne v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Prestaties afstemmen {#best-practices-performance}

Voor **de hybride/op-gebouw plaatsingen van Campaign Classic v7**, kunnen de volgende gegevensbestand en infrastructuuroptimalisaties leveringsprestaties verbeteren:

### Databaseoptimalisatie

**de adressen van de Index** om de prestaties van SQL vragen te optimaliseren die in de toepassing worden gebruikt. Een index kan van het belangrijkste element van het gegevensschema worden verklaard. Deze optimalisering vereist directe gegevensbestandtoegang en schemaaanpassing beschikbaar in plaatsingen op-gebouw.

### Afstelling van infrastructuur

**Grote leveringsconfiguratie**: Leveringen aan meer dan één miljoen ontvangers vereisen ruimte in de verzendende rijen. Voor installaties op locatie, kunnen de kinderen MTA worden gevormd om de grootte van de douanepartij te behandelen. Neem contact op met de systeembeheerder om deze instellingen aan te passen op basis van de capaciteit van uw infrastructuur.

>[!NOTE]
>
>Voor gebruikers van de Beheerde Cloud Services van Campagne v8 worden de optimalisatie van de infrastructuur en de MTA-configuratie beheerd door Adobe. Verwijs naar de [ beste praktijken van de Levering van de Campagne v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} voor prestatiesaanbevelingen van toepassing op uw plaatsing.

## Databaseonderhoud {#performance-issues}

Voor **Campaign Classic v7 hybride/op-gebouw plaatsingen**, platform en gegevensbestandonderhoud beïnvloedt direct levering verzendende prestaties.

Regelmatige onderhoudstaken omvatten:

**Schoonmaak van het Gegevensbestand**: Gebruik het gegevensbestand schoonmaakbeurt werkschema om oude leveringslogboeken, het volgen gegevens, en tijdelijke lijsten te verwijderen. Het slechte gegevensbestandonderhoud kan leveringsvoorbereiding en het verzenden vertragen.

**prestaties van het Gegevensbestand controle**: De prestaties van de vraagcontrole van de monitor, indexfragmentatie, en lijststatistieken. Voor gedetailleerde begeleiding, verwijs naar [ deze pagina ](../../production/using/database-performances.md).

**Technische werkschemacontrole**: Zorg alle technische werkschema&#39;s (vooral schoonmaak, het volgen, en de werkschema&#39;s van de leveringsupdate) correct zonder fouten lopen.

>[!NOTE]
>
>Voor gebruikers van Campagne v8 Managed Cloud Services worden het onderhoud van databases en de technische workflows gecontroleerd en beheerd door Adobe. De nadruk op levering-specifieke controle zoals die in de [ documentatie van de leveringen van de Monitor v8 van de Campagne wordt beschreven ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Verwante onderwerpen

* [ beste praktijken van de Levering ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (de documentatie van de Campagne v8)
* [ monitor uw leverbaarheid ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"} (de documentatie van de Campagne v8)
* [Problemen met een levering oplossen](delivery-troubleshooting.md)
* [ prestaties van het Gegevensbestand ](../../production/using/database-performances.md) (v7 hybride/op-gebouw)
