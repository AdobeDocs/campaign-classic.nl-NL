---
product: campaign
title: Tijdzonebeheer
description: Tijdzonebeheer
feature: Installation, Instance Settings
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 1%

---

# Tijdzonebeheer{#time-zone-management}



## Werkwijze {#operating-principle}

In Adobe Campaign kunt u datums uitdrukken als een functie van de tijdzone: dit stelt internationale gebruikers in staat wereldwijd aan verschillende tijdzones te werken. Elk land dat hetzelfde exemplaar gebruikt, kan de uitvoering van campagnes, bijhouden, archiveren, enz. beheren. afhankelijk van de lokale tijd.

Om het gebruik van het Adobe Campaign-platform op internationale schaal mogelijk te maken, moeten alle data die door de systemen worden gebruikt, aan een tijdzone kunnen worden gekoppeld. Een datum waarvan de tijdzone gekend is kan zo in om het even welke andere tijdzone, of ongeacht tijdzone worden ingevoerd.

Met Adobe Campaign kunt u datums/tijden opslaan in UTC-indeling (Coordinated Universal Time). Wanneer gegevens worden weergegeven, worden deze omgezet in de lokale datum/tijd van de operator. De omzetting wordt uitgevoerd automatisch wanneer het gegevensbestand in UTC (verwijs naar [ Configuratie ](#configuration)) wordt gevormd. Als het gegevensbestand niet in UTC wordt gevormd, wordt de informatie over de tijdzone van de data in het platform opgeslagen in een optie.

De belangrijkste platformfuncties met betrekking tot tijdzonebeheer zijn: invoer-/exportgegevens en beheer van de exploitant en werkstroom. Het **overervingsconcept** is beschikbaar voor invoer/uitvoer of Werkstromen. Door gebrek, worden zij gevormd voor de tijdzone van de gegevensbestandserver, nochtans kunt u nieuwe tijdstreken voor een werkschema en zelfs voor één enkele activiteit opnieuw bepalen.

**de Exploitanten** kunnen tijdstreken tijdens **leveringsconfiguratie** wijzigen en kunnen de bijzondere tijdzone specificeren waarin de levering zal worden uitgevoerd.

>[!IMPORTANT]
>
>Als het gegevensbestand veelvoudige tijdstreken niet beheert, voor alle gegevens die manipulaties filtreren, SQL moeten de vragen in de tijdzone van de gegevensbestandserver worden uitgevoerd.

Elke Adobe Campaign-operator is gekoppeld aan een tijdzone: deze informatie wordt geconfigureerd in hun profiel. Voor meer op dit, verwijs naar [ dit document ](../../platform/using/access-management.md).

Als het Adobe Campaign-platform geen tijdzonebeheer nodig heeft, kunt u een opslagmodus in lokale indeling behouden met een specifieke gekoppelde tijdzone.

## Aanbevelingen {#recommendations}

In tijdzones worden verschillende realiteiten gecombineerd: in de expressie kan een constante tijdsvertraging met de UTC-datum worden beschreven, of de tijdstippen van een regio die tweemaal per jaar (zomertijd) kunnen veranderen.

Bijvoorbeeld, in postgreSQL, zal het **GEPLAATSTE GEBIED VAN DE TIJD &quot;Europa/Parijs&quot;;** bevel zomer en wintertijden in rekening brengen: de datum zal in UTC+1 of UTC+2 afhankelijk van de tijd van jaar worden uitgedrukt.

Nochtans, als u **GEPLAATSTE ZONE 0200 gebruikt;** bevel, zal de tijd-vertraging altijd UTC+2 zijn.

## Configuratie {#configuration}

De opslagwijze voor data en tijden wordt geselecteerd tijdens gegevensbestandverwezenlijking (verwijs naar [ Creërend een nieuwe instantie ](#creating-a-new-instance)). In het geval van een migratie, worden de uren verbonden aan data omgezet in lokale data en uren (verwijs naar [ Migratie ](#migration)).

Van een technisch standpunt, zijn er twee manieren om **Date+time** typeinformatie in het gegevensbestand op te slaan:

1. TIJDSTEMPEL MET TIMEZONE-indeling: de database-engine slaat datums op in UTC. Elke geopende sessie heeft een tijdzone en de datums worden overeenkomstig deze tijdzone omgezet.
1. Lokale notatie + lokale tijdzone: alle datums worden opgeslagen in de lokale notatie (geen tijdvertragingsbeheer) en er wordt één tijdzone aan toegewezen. De tijdzone wordt opgeslagen in de **WdbcTimeZone** optie van de instantie van Adobe Campaign en kan via het **[!UICONTROL Administration > Platform > Options]** menu van de boom worden veranderd.

>[!IMPORTANT]
>
>Houd er rekening mee dat deze wijziging kan leiden tot problemen met de consistentie en synchronisatie van gegevens.

### Een nieuwe instantie maken {#creating-a-new-instance}

Als verschillende internationale gebruikers aan hetzelfde exemplaar willen werken, moet u tijdzones configureren wanneer u het exemplaar maakt voor het beheer van tijdvertragingen tussen landen. Selecteer tijdens het maken van een instantie de modus voor datum- en tijdbeheer in het gedeelte **[!UICONTROL Time zone]** van het configuratiewerkgebied van de database.

Schakel de optie **[!UICONTROL UTC database (date fields with time zone)]** in om alle gegevens met datums en tijden op te slaan in de UTC-indeling (SQL-velden en XML-velden).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Als u **Oracle** gebruikt, moeten de timezone dossiers (.dat) van de de cliëntlagen van het Oracle compatibel zijn met de timezones dossiers die op de server worden geïnstalleerd.

Als de database geen UTC is, kunt u een van de tijdzones selecteren die in de vervolgkeuzelijst worden aangeboden. U kunt ook de tijdzone van de server gebruiken of de optie UTC (Coordinated Universal Time) selecteren.

![](assets/install_wz_unselect_utc_option.png)

Als de optie **[!UICONTROL UTC Database (date fields with time zone)]** is geselecteerd, worden de SQL-velden opgeslagen in de indeling TIMESTAMP MET TIMEZONE.

Anders, worden zij opgeslagen in het lokale formaat en u zult de tijdzone moeten selecteren om op het gegevensbestand toe te passen.

### Migratie {#migration}

Wanneer het migreren aan een vroegere versie (zonder tijdzonebeheer), zult u de wijze van de datumopslag in het gegevensbestand moeten bepalen.

Om verenigbaarheid met externe hulpmiddelen te waarborgen die tot het gegevensbestand van Adobe Campaign toegang hebben, blijven het **Date+time** typeSQL gebieden in lokaal formaat door gebrek worden opgeslagen.

XML-velden met datums worden nu opgeslagen in UTC. Tijdens het laden worden velden die niet de UTC-indeling hebben, automatisch geconverteerd met de tijdzone van de servers. Dit betekent dat alle XML-velden progressief worden omgezet in UTC-indeling.

Om een bestaande instantie te gebruiken, voeg de **WdbcTimeZone** optie toe en ga de tijdzone van de instantie in.

>[!IMPORTANT]
>
>Controleer of de juiste waarde is geconfigureerd voor de optie WdbcTimeZone: wijzigingen die u later uitvoert, kunnen leiden tot inconsistenties.

Voorbeeld van mogelijke waarden:

* Europa/Parijs,
* Europa/Londen,
* Amerika/New_York, enz.

  Deze waarden zijn afkomstig uit de tz-database (Olson). Voor meer informatie, verwijs naar [ https://en.wikipedia.org/wiki/List_of_tz_database_time_zones ](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

## Tijdzone van database en server oracles

Voor de hoofddatabase gebruikt Campagne de tijdzone van de server om de tijdzone van de sessie in te stellen op de databaseverbinding. De optie &quot;WdbcTimeZone&quot; heeft geen invloed. De tijdzone van de server moet dus overeenkomen met de tijdzone van de hoofddatabase die door Campagne wordt gebruikt. Als u niet de server timezone kunt veranderen, kan de timezone die door Campagne wordt gebruikt worden met voeten getreden door de de omgevingsvariabele van TZ in customer.sh te plaatsen.