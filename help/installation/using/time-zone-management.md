---
title: Tijdzonebeheer
seo-title: Tijdzonebeheer
description: Tijdzonebeheer
seo-description: null
page-status-flag: never-activated
uuid: b8926761-65e2-48fd-8689-2ae6b0596e72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: b9846eda-eeca-433e-b961-6dfc2aa2708b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7c2b5ce9afa45b472f161d6d62517513888e062e

---


# Tijdzonebeheer{#time-zone-management}

## Exploitatiebeginsel {#operating-principle}

Met Adobe Campaign kunt u datums uitdrukken als een functie van de tijdzone: dit stelt internationale gebruikers in staat wereldwijd aan verschillende tijdzones te werken . Elk land dat hetzelfde exemplaar gebruikt, kan de uitvoering van campagnes, bijhouden, archiveren, enz. beheren. afhankelijk van de lokale tijd.

Als u het gebruik van het Adobe Campaign-platform op internationale schaal wilt toestaan, moeten alle datums die door de systemen worden gebruikt, kunnen worden gekoppeld aan een tijdzone. Een datum waarvan de tijdzone gekend is kan zo in om het even welke andere tijdzone, of ongeacht tijdzone worden ingevoerd.

Met Adobe Campaign kunt u datums/tijden opslaan in de UTC-indeling (Coordinated Universal Time). Wanneer gegevens worden weergegeven, worden deze omgezet in de lokale datum/tijd van de operator. De omzetting wordt uitgevoerd automatisch wanneer het gegevensbestand in UTC (verwijs naar [Configuratie](#configuration)) wordt gevormd. Als het gegevensbestand niet in UTC wordt gevormd, wordt de informatie over de tijdzone van de data in het platform opgeslagen in een optie.

De belangrijkste platformfuncties voor het beheer van tijdzones zijn: invoer/uitvoer gegevens en exploitant en werkstroombeheer. Het **overervingsconcept** is beschikbaar voor import/export of Workflows. Door gebrek, worden zij gevormd voor de tijdzone van de gegevensbestandserver, nochtans kunt u nieuwe tijdstreken voor een werkschema en zelfs voor één enkele activiteit opnieuw bepalen.

**De exploitanten** kunnen tijdstreken tijdens **leveringsconfiguratie** wijzigen en kunnen de bijzondere tijdzone specificeren waarin de levering zal worden uitgevoerd.

>[!CAUTION]
>
>Als het gegevensbestand veelvoudige tijdstreken niet beheert, voor alle gegevens die manipulaties filtreren, SQL moeten de vragen in de tijdzone van de gegevensbestandserver worden uitgevoerd.

Elke Adobe Campagneoperator is gekoppeld aan een tijdzone: deze informatie is geconfigureerd in hun profiel. Raadpleeg [dit document](../../platform/using/access-management.md)voor meer informatie.

Wanneer het Adobe Campagne-platform geen tijdzonebeheer vereist, kunt u een opslagwijze in lokaal formaat met een specifieke verbonden tijdzone houden.

## Aanbevelingen {#recommendations}

In tijdzones zijn verschillende situaties samengevat: de expressie kan een constante tijdvertraging met de UTC-datum beschrijven, of de tijden van een regio die tweemaal per jaar (zomertijd) kunnen veranderen.

**Bijvoorbeeld, in postgreSQL, ZONE** SET TIME &quot;Europe/Paris&quot;; bij het commando wordt rekening gehouden met de zomer - en wintertijd : de datum wordt uitgedrukt in UTC+1 of UTC+2, afhankelijk van het tijdstip van het jaar.

**Als u echter de** SET TIME ZONE 0200 gebruikt; -opdracht, is de tijdvertraging altijd UTC+2.

## Configuratie {#configuration}

De opslagmodus voor datums en tijden wordt geselecteerd tijdens het maken van de database (zie [Een nieuwe instantie](#creating-a-new-instance)maken). In het geval van een migratie worden de aan datums gekoppelde uren omgezet in lokale datums en uren (zie [Migratie](#migration)).

Vanuit technisch oogpunt zijn er twee manieren om informatie over het type **Date+Time** in de database op te slaan:

1. TIJDSTEMPEL MET TIMEZONE-indeling: de database-engine de datums in UTC opslaat. Elke geopende sessie heeft een tijdzone en de datums worden overeenkomstig deze tijdzone omgezet.
1. Lokale notatie + lokale tijdzone: alle datums worden opgeslagen in de lokale notatie (geen tijdvertragingsbeheer) en er wordt één tijdzone aan toegewezen. De tijdzone wordt opgeslagen in de optie **WdbcTimeZone** van de Adobe Campagne-instantie en kan worden gewijzigd via het **[!UICONTROL Administration > Platform > Options]** menu van de boomstructuur.

>[!CAUTION]
>
>Houd er rekening mee dat deze wijziging kan leiden tot problemen met de consistentie en synchronisatie van gegevens.

### Een nieuwe instantie maken {#creating-a-new-instance}

Als verschillende internationale gebruikers aan hetzelfde exemplaar willen werken, moet u tijdzones configureren wanneer u het exemplaar maakt voor het beheer van tijdvertragingen tussen landen. Selecteer tijdens het maken van een instantie de datum- en tijdbeheermodus in het **[!UICONTROL Time zone]** gedeelte van de databaseconfiguratiefase.

Schakel de **[!UICONTROL UTC database (date fields with time zone)]** optie in om alle gegevens met datums en tijden op te slaan in de UTC-indeling (SQL-velden en XML-velden).

![](assets/install_wz_select_utc_option.png)

>[!CAUTION]
>
>Als u **Oracle** gebruikt, moeten de tijdzonebestanden (.dat) van de Oracle-clientlagen compatibel zijn met de tijdzonebestanden die op de server zijn geïnstalleerd.

Als de database geen UTC is, kunt u een van de tijdzones selecteren die in de vervolgkeuzelijst worden aangeboden. U kunt ook de tijdzone van de server gebruiken of de optie UTC (Coordinated Universal Time) selecteren.

![](assets/install_wz_unselect_utc_option.png)

Als de **[!UICONTROL UTC Database (date fields with time zone)]** optie is geselecteerd, worden de SQL-velden opgeslagen in de indeling TIMESTAMP MET TIMEZONE.

Anders, worden zij opgeslagen in het lokale formaat en u zult de tijdzone moeten selecteren om op het gegevensbestand toe te passen.

### Migratie {#migration}

Wanneer het migreren aan een vroegere versie (zonder tijdzonebeheer), zult u de wijze van de datumopslag in het gegevensbestand moeten bepalen.

Om compatibiliteit met externe hulpprogramma&#39;s die toegang krijgen tot de Adobe Campagne-database te garanderen, blijven de SQL-velden van het type **Date+Time** standaard opgeslagen in lokale indeling.

XML-velden met datums worden nu opgeslagen in UTC. Tijdens het laden worden velden die niet de UTC-indeling hebben, automatisch geconverteerd met de tijdzone van de servers. Dit betekent dat alle XML-velden progressief worden omgezet in UTC-indeling.

Als u een bestaande instantie wilt gebruiken, voegt u de optie **WdbcTimeZone** toe en voert u de tijdzone van de instantie in.

>[!CAUTION]
>
>Controleer of de juiste waarde is geconfigureerd voor de optie WdbcTimeZone: latere wijzigingen kunnen tot inconsistenties leiden .

Voorbeeld van mogelijke waarden:

* Europa/Parijs,
* Europa/Londen,
* Amerika/New_York, enz.

   Deze waarden zijn afkomstig uit de tz-database (Olson). Raadpleeg voor meer informatie [http://en.wikipedia.org/wiki/List_of_tz_database_time_zones](http://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

