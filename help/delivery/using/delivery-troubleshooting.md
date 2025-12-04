---
product: campaign
title: Problemen met verzenden van levering
description: Meer informatie over leveringsprestaties en hoe u problemen met betrekking tot leveringsbewaking kunt oplossen
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 1%

---

# Problemen met verzenden van levering {#delivery-troubleshooting}

>[!NOTE]
>
>Uitgebreide instructies voor het oplossen van problemen met de levering worden beschreven in de documentatie bij Campagne v8, die van toepassing is op zowel Campaign Classic v7- als Campagne v8-gebruikers:
>
>* Gemeenschappelijke leveringsmislukkingen en oplossingen: [&#x200B; Begrijpend leveringsmislukkingen &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Trage leveringsdiagnose: [&#x200B; leveringen van de Monitor in Campagne UI &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* De beste praktijken van de levering: [&#x200B; Beste praktijken van de Levering &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>Deze pagina documenteert **het v7-specifieke oplossen van problemen van Campaign Classic** voor hybride en op-gebouw plaatsingen.

## Problemen oplossen {#v7-specific}

Voor **de hybride/op-gebouw plaatsingen van Campaign Classic v7**, zijn de volgende het oplossen van problemenstappen specifiek voor infrastructuur u beheert:

### Configuratie van MX-regels

Als u throttling kwesties met specifieke ISPs ervaart, kunt u uw MX regelconfiguratie moeten herzien en aanpassen. Voor meer informatie over MX regels en quota, verwijs naar [&#x200B; deze sectie &#x200B;](../../installation/using/email-deliverability.md#about-mx-rules).

### Databaseonderhoud voor prestaties van levering

Als u de volgende fout in midsourcingimplementaties tegenkomt:

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

De oorzaak is gekoppeld aan prestatieproblemen waarbij de marketinginstantie te veel tijd besteedt aan het samenstellen van gegevens voordat deze naar de server voor midsourcing worden verzonden.

**voor op-gebouw installaties**, voer vacuüm en herdex op het gegevensbestand uit. Voor meer informatie over gegevensbestandonderhoud, verwijs naar [&#x200B; deze sectie &#x200B;](../../production/using/recommendations.md).

U moet ook alle werkstromen met een geplande activiteit opnieuw beginnen, en alle werkschema&#39;s in ontbroken status. Zie [deze sectie](../../workflow/using/scheduler.md).

### Technische werkstroomcontrole

Voor installaties op locatie moet u ervoor zorgen dat alle technische workflows met betrekking tot de te leveren items zonder fouten worden uitgevoerd:

**werkschema van de de updatewerkschema van de Leverbaarheid**: De updates stuiteren de regels van de postkwalificatie en de leveringsindicatoren.

**het Volgen werkschema**: Verwerkt het volgen gegevens voor verzonden leveringen.

**het schoonmaakbeurt van het Gegevensbestand werkschema**: Schoont regelmatig oude leveringslogboeken en tijdelijke lijsten om prestaties te handhaven.

Controleer de workflowstatus in **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** .

>[!NOTE]
>
>Voor gebruikers van Campagne v8 Managed Cloud Services worden de technische workflows en de infrastructuurbewaking beheerd door Adobe. De nadruk op leveringsinhoud en het richten zoals die in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} wordt beschreven.

## Verwante onderwerpen

* [&#x200B; Begrijpend leveringsmislukkingen &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; beste praktijken van de Levering &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; leveringen van de Monitor in Campagne UI &#x200B;](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (de documentatie van de Campagne v8)
* [&#x200B; onderhoud van het Gegevensbestand &#x200B;](../../production/using/recommendations.md) (v7 hybride/op-gebouw)
* [&#x200B; E-mailleverbaarheid &#x200B;](../../installation/using/email-deliverability.md) (v7 hybride/op-gebouw)
