---
product: campaign
title: Leveringsprestaties en probleemoplossing
description: Leer hoe u de prestaties van de levering kunt optimaliseren en problemen in Campaign Classic v7 kunt oplossen
feature: Monitoring, Deliverability, Troubleshooting
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# Leveringsprestaties en probleemoplossing {#delivery-performance-troubleshooting}

>[!NOTE]
>
>De uitvoerige begeleiding op leveringsprestaties en beste praktijken wordt gedocumenteerd in de [ pagina van de Beste praktijken van de Lading van de Campagne v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices). Deze inhoud is van toepassing op gebruikers van Campaign Classic v7 en Campagne v8.
>
>Deze pagina documenteert **Campaign Classic v7-specifieke configuraties** voor prestatiesoptimalisering en het oplossen van problemen in hybride en op-gebouw plaatsingen.

Voor uitvoerige beste praktijken op leveringsprestaties, platformoptimalisering, quarantainebeheer, gegevensbestandonderhoud, en het plannen van aanbevelingen, verwijs naar de [ documentatie van de beste praktijken van de Bevordering van de Campagne v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Optimalisatie van prestaties {#performance-optimization}

Voor **de hybride/op-gebouw plaatsingen van Campaign Classic v7**, kunnen de volgende gegevensbestand en infrastructuuroptimalisaties leveringsprestaties verbeteren.

### Databaseoptimalisatie

**de adressen van de Index** om de prestaties van SQL vragen te optimaliseren die in de toepassing worden gebruikt. Een index kan van het belangrijkste element van het gegevensschema worden verklaard. Deze optimalisering vereist directe gegevensbestandtoegang en schemaaanpassing beschikbaar in plaatsingen op-gebouw.

### Afstelling van infrastructuur

**Grote leveringsconfiguratie**: Leveringen aan meer dan één miljoen ontvangers vereisen ruimte in de verzendende rijen. Voor installaties op locatie, kunnen de kinderen MTA worden gevormd om de grootte van de douanepartij te behandelen. Neem contact op met de systeembeheerder om deze instellingen aan te passen op basis van de capaciteit van uw infrastructuur.

>[!NOTE]
>
>Voor gebruikers van de Beheerde Cloud Services van Campagne v8 worden de optimalisatie van de infrastructuur en de MTA-configuratie beheerd door Adobe. Verwijs naar de [ beste praktijken van de Levering van de Campagne v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} voor prestatiesaanbevelingen van toepassing op uw plaatsing.

### Databaseonderhoud {#database-maintenance}

Voor **Campaign Classic v7 hybride/op-gebouw plaatsingen**, platform en gegevensbestandonderhoud beïnvloedt direct levering verzendende prestaties.

Regelmatige onderhoudstaken omvatten:

**Schoonmaak van het Gegevensbestand**: Gebruik het gegevensbestand schoonmaakbeurt werkschema om oude leveringslogboeken, het volgen gegevens, en tijdelijke lijsten te verwijderen. Het slechte gegevensbestandonderhoud kan leveringsvoorbereiding en het verzenden vertragen.

**prestaties van het Gegevensbestand controle**: De prestaties van de vraagcontrole van de monitor, indexfragmentatie, en lijststatistieken. Voor gedetailleerde begeleiding, verwijs naar [ deze pagina ](../../production/using/database-performances.md).

**Technische werkschemacontrole**: Zorg alle technische werkschema&#39;s (vooral schoonmaak, het volgen, en de werkschema&#39;s van de leveringsupdate) correct zonder fouten lopen.

>[!NOTE]
>
>Voor gebruikers van Campagne v8 Managed Cloud Services worden het onderhoud van databases en de technische workflows gecontroleerd en beheerd door Adobe. De nadruk op levering-specifieke controle zoals die in de [ documentatie van de leveringen van de Monitor v8 van de Campagne wordt beschreven ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Problemen met de levering van oplossingen {#troubleshooting}

>[!NOTE]
>
>Uitgebreide instructies voor het oplossen van problemen met de levering worden beschreven in de documentatie bij Campagne v8, die van toepassing is op zowel Campaign Classic v7- als Campagne v8-gebruikers:
>
>* Gemeenschappelijke leveringsmislukkingen en oplossingen: [ Begrijpend leveringsmislukkingen ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Trage leveringsdiagnose: [ leveringen van de Monitor in Campagne UI ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* De beste praktijken van de levering: [ Beste praktijken van de Levering ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>Deze sectie documenteert **het v7-specifieke oplossen van problemen van Campaign Classic** voor hybride en op-gebouw plaatsingen.

Voor **Campaign Classic v7 hybride/op-gebouw plaatsingen**, zijn de volgende het oplossen van problemenstappen specifiek aan infrastructuur u beheert.

### Configuratie van MX-regels

Als u throttling kwesties met specifieke ISPs ervaart, kunt u uw MX regelconfiguratie moeten herzien en aanpassen. Voor meer informatie over MX regels en quota, verwijs naar [ deze sectie ](../../installation/using/email-deliverability.md#about-mx-rules).

### Databaseonderhoud voor prestaties van levering

Als u de volgende fout in midsourcingimplementaties tegenkomt:

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

De oorzaak is gekoppeld aan prestatieproblemen waarbij de marketinginstantie te veel tijd besteedt aan het samenstellen van gegevens voordat deze naar de server voor midsourcing worden verzonden.

**voor op-gebouw installaties**, voer vacuüm en herdex op het gegevensbestand uit. Voor meer informatie over gegevensbestandonderhoud, verwijs naar [ deze sectie ](../../production/using/recommendations.md).

U moet ook alle werkstromen met een geplande activiteit opnieuw beginnen, en alle werkschema&#39;s in ontbroken status. Zie [deze sectie](../../workflow/using/scheduler.md).

### Technische werkstroomcontrole

Voor installaties op locatie moet u ervoor zorgen dat alle technische workflows met betrekking tot de te leveren items zonder fouten worden uitgevoerd:

**werkschema van de de updatewerkschema van de Leverbaarheid**: De updates stuiteren de regels van de postkwalificatie en de leveringsindicatoren.

**het Volgen werkschema**: Verwerkt het volgen gegevens voor verzonden leveringen.

**het schoonmaakbeurt van het Gegevensbestand werkschema**: Schoont regelmatig oude leveringslogboeken en tijdelijke lijsten om prestaties te handhaven.

Controleer de workflowstatus in **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** .

>[!NOTE]
>
>Voor gebruikers van Campagne v8 Managed Cloud Services worden de technische workflows en de infrastructuurbewaking beheerd door Adobe. De nadruk op leveringsinhoud en het richten zoals die in de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} wordt beschreven.

## Verwante onderwerpen

* [ Begrijpend leveringsmislukkingen ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (de documentatie van de Campagne v8)
* [ beste praktijken van de Levering ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (de documentatie van de Campagne v8)
* [ leveringen van de Monitor in Campagne UI ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (de documentatie van de Campagne v8)
* [ onderhoud van het Gegevensbestand ](../../production/using/recommendations.md) (v7 hybride/op-gebouw)
* [ E-mailleverbaarheid ](../../installation/using/email-deliverability.md) (v7 hybride/op-gebouw)
* [ prestaties van het Gegevensbestand ](../../production/using/database-performances.md) (v7 hybride/op-gebouw)

