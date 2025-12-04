---
product: campaign
title: Quarantainebeheer begrijpen
description: Quarantainebeheer begrijpen
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---

# Quarantainebeheer begrijpen{#understanding-quarantine-management}

>[!NOTE]
>
>De uitvoerige begeleiding op quarantainebeheer wordt gedocumenteerd in de [ het beheer van de Quarantaine v8 van de Campagne ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines) pagina. Deze inhoud is van toepassing op zowel Campaign Classic v7- als Campagne v8-gebruikers. Deze inhoud omvat:
>
>* Concepten quarantaine en lijst van gewezen personen
>* Waarom adressen naar quarantaine (hard/zachte fouten) worden verzonden
>* Zwak foutenbeheer en fout tegendrempelwaarden
>* Hoe te om tot quarantined adressen toegang te hebben en te identificeren
>* Hoe te om adressen uit quarantaine (automatisch, manueel, bulk) te verwijderen
>* Quarantainebeheerrapporten
>
>Deze pagina documenteert **Campaign Classic v7-specifieke configuratie** voor quarantainebeheer in hybride en op-gebouw plaatsingen.

Voor uitvoerige richtlijnen van het quarantainebeheer, verwijs naar de [ het beheersdocumentatie van de Campagne v8 Quarantine ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Quarantaineconfiguratie {#v7-quarantine-config}

De volgende configuratieopties zijn beschikbaar voor **de hybride/op-gebouw plaatsingen van Campaign Classic v7** om quarantainegedrag aan te passen.

### Configuratie van drempelwaarde voor zachte fout {#soft-error-threshold}

Voor installaties op locatie die de oudere Campagne MTA gebruiken, kunt u het aantal fouten en de periode tussen twee fouten wijzigen alvorens een adres quarantined is.

Deze instellingen configureren:

1. Via **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]** kunt u de wizard Implementatie openen.
2. Ga naar **[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**
3. Configureren:
   * **Aantal fouten**: Het maximumaantal zachte fouten alvorens een adres wordt quarantined (gebrek: 5)
   * **Periode tussen twee significante fouten**: Het tijdvenster (in seconden) voor fout het tellen (gebrek: 86.400 seconden = 1 dag)

Wanneer de foutenteller de drempel bereikt, is het adres quarantined. Als de laatste significante fout meer dan 10 dagen geleden voorkwam, wordt de foutenteller opnieuw geïnitialiseerd.

Voor meer details, verwijs naar [ deze pagina ](communication-channels.md) onder **het verzenden van de Levering** > **vormen opnieuw probeert**.

>[!NOTE]
>
>Voor Campagne v8 Managed Cloud Services-gebruikers worden instellingen voor opnieuw proberen en drempelwaarden voor fouten beheerd door Adobe op basis van IP-prestaties en domeinreputatie. Er is geen configuratie vereist.

### Workflow voor het opschonen van databases {#database-cleanup-workflow}

Voor installaties op locatie verwijdert de technische workflow van **[!UICONTROL Database cleanup]** automatisch quarantineadressen die overeenkomen met specifieke voorwaarden.

Open deze workflow via **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Database cleanup]** .

De workflow verwijdert adressen uit quarantaine in de volgende gevallen:

* Hiermee wordt de status **[!UICONTROL With errors]** na een geslaagde levering geactiveerd
* Hiermee wordt de status **[!UICONTROL With errors]** toegevoegd als de laatste zachte stuit meer dan 10 dagen geleden is opgetreden
* Vermeldt de status **[!UICONTROL With errors]** met de fout **[!UICONTROL Mailbox full]** na 30 dagen

Zorg ervoor dat deze workflow regelmatig wordt uitgevoerd (aanbevolen: dagelijks) om de hygiëne van de quarantainelijst te handhaven.

Voor meer op gegevensbestandschoonmaakbeurt, verwijs naar [ deze sectie ](../../production/using/database-cleanup-workflow.md).

>[!NOTE]
>
>Voor gebruikers van Campagne v8 Managed Cloud Services wordt de workflow voor het opschonen van databases gecontroleerd en beheerd door Adobe.

### quarantainespecificaties voor pushmeldingen {#push-quarantine-specifics}

Voor Campaign Classic v7 volgen pushmeldingen het algemene quarantainemechanisme met bepaalde kanaalspecifieke gedragingen.

Voor **iOS** en **Android** dupberichten, gebruikt het quarantainemechanisme apparatentokens eerder dan e-mailadressen. Wanneer een mobiele toepassing wordt verwijderd of opnieuw wordt geïnstalleerd, wordt het bijbehorende token in quarantaine geplaatst.

Voor gedetailleerde informatie over de scenario&#39;s van de duw- bericht quarantaine (de foutentypes van iOS en van Android, retry gedrag, enz.), verwijs naar de [ Begrijpende documentatie van de leveringsmislukkingen ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} die uitvoerige het type van de dupmeldingsfout lijsten omvat.

### SMS-quarantainespecificaties {#sms-quarantine-specifics}

Voor Campaign Classic v7, volgen SMS quarantines het algemene quarantainemechanisme met wat kanaal-specifieke gedrag met betrekking tot telefoonaantallen eerder dan e-mailadressen.

Het quarantainemechanisme van SMS varieert afhankelijk van de gebruikte schakelaar:

* **StandaardSMPP schakelaars**: De kwalificatieregels van de fout die in **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** worden bepaald zijn op de leveringen van SMS van toepassing.

* **Uitgebreide generische schakelaar SMPP**: Het beheer van de fout wordt behandeld verschillend gebruikend regelmatige uitdrukkingen (regexes) om de berichten van het Rapport van de Status (SR) te ontleden die door de leverancier SMSC zijn teruggekeerd.

Voor gedetailleerde informatie over de quarantainescenario&#39;s van SMS en foutentypes, verwijs naar [ Begrijpend leveringsmislukkingen ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} documentatie die uitvoerige de foutenentabellen van SMS omvat.

## Verwante onderwerpen

* [ het beheer van de quarantaine ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (de documentatie van de Campagne v8)
* [ Begrijpend leveringsmislukkingen ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (de documentatie van de Campagne v8)
* [ beste praktijken van de Levering ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (de documentatie van de Campagne v8)
* [ het schoonmaakbeurtenwerkschema van het Gegevensbestand ](../../production/using/database-cleanup-workflow.md) (v7 hybride/op-gebouw)
* [ vorm levering opnieuw probeert ](communication-channels.md) (v7 hybride/op-gebouw)
