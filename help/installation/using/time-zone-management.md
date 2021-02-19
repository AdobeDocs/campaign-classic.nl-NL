---
solution: Campaign Classic
product: campaign
title: Tijdzonebeheer
description: Tijdzonebeheer
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---


# Tijdzonebeheer{#time-zone-management}

## Werkwijze {#operating-principle}

Met Adobe Campaign kunt u datums uitdrukken als een functie van de tijdzone: dit stelt internationale gebruikers in staat wereldwijd aan verschillende tijdzones te werken . Elk land dat hetzelfde exemplaar gebruikt, kan de uitvoering van campagnes, bijhouden, archiveren, enz. beheren. afhankelijk van de lokale tijd.

Om het gebruik van het Adobe Campaign-platform op internationale schaal mogelijk te maken, moeten alle data die door de systemen worden gebruikt, aan een tijdzone kunnen worden gekoppeld. Een datum waarvan de tijdzone gekend is kan zo in om het even welke andere tijdzone, of ongeacht tijdzone worden ingevoerd.

Met Adobe Campaign kunt u datums/tijden opslaan in UTC-indeling (Coordinated Universal Time). Wanneer gegevens worden weergegeven, worden deze omgezet in de lokale datum/tijd van de operator. De omzetting wordt automatisch uitgevoerd wanneer het gegevensbestand in UTC (verwijs naar [Configuratie](#configuration)) wordt gevormd. Als het gegevensbestand niet in UTC wordt gevormd, wordt de informatie over de tijdzone van de data in het platform opgeslagen in een optie.

De belangrijkste platformfuncties voor het beheer van tijdzones zijn: invoer/uitvoer gegevens en exploitant en werkstroombeheer. Het **overervingsconcept** is beschikbaar voor import/export of Workflows. Door gebrek, worden zij gevormd voor de tijdzone van de gegevensbestandserver, nochtans kunt u nieuwe tijdstreken voor een werkschema en zelfs voor één enkele activiteit opnieuw bepalen.

**De** exploitant kan tijdstreken tijdens  **** leveringsconfiguratie wijzigen en kan de bijzondere tijdzone specificeren waarin de levering zal worden uitgevoerd.

>[!IMPORTANT]
>
>Als het gegevensbestand veelvoudige tijdstreken niet beheert, voor alle gegevens die manipulaties filtreren, SQL moeten de vragen in de tijdzone van de gegevensbestandserver worden uitgevoerd.

Elke Adobe Campaign-operator is gekoppeld aan een tijdzone: deze informatie is geconfigureerd in hun profiel. Raadpleeg [dit document](../../platform/using/access-management.md) voor meer informatie hierover.

Als het Adobe Campaign-platform geen tijdzonebeheer nodig heeft, kunt u een opslagmodus in lokale indeling behouden met een specifieke gekoppelde tijdzone.

## Aanbevelingen {#recommendations}

In tijdzones zijn verschillende situaties samengevat: de expressie kan een constante tijdvertraging met de UTC-datum beschrijven, of de tijden van een regio die tweemaal per jaar (zomertijd) kunnen veranderen.

In postgreSQL, zal **SET TIME ZONE &quot;Europe/Paris&quot;;** bevel zomer en wintertijden in rekening brengen: de datum wordt uitgedrukt in UTC+1 of UTC+2, afhankelijk van het tijdstip van het jaar.

Als u echter de opdracht **TIJDZONE INSTELLEN 0200;** gebruikt, is de tijdvertraging altijd UTC+2.

## Configuratie {#configuration}

De opslagmodus voor datums en tijden wordt geselecteerd tijdens het maken van de database (zie [Een nieuwe instantie maken](#creating-a-new-instance)). In het geval van een migratie worden de aan datums gekoppelde uren geconverteerd naar lokale datums en uren (zie [Migratie](#migration)).

Vanuit technisch oogpunt zijn er twee manieren om informatie van het type **Date+time** in de database op te slaan:

1. TIJDSTEMPEL MET TIMEZONE-indeling: de database-engine de datums in UTC opslaat. Elke geopende sessie heeft een tijdzone en de datums worden overeenkomstig deze tijdzone omgezet.
1. Lokale notatie + lokale tijdzone: alle datums worden opgeslagen in het lokale formaat (geen tijd-lag beheer) en er wordt één tijdzone aan toegewezen. De tijdzone wordt opgeslagen in de optie **WdbcTimeZone** van de Adobe Campaign-instantie en kan worden gewijzigd via het menu **[!UICONTROL Administration > Platform > Options]** van de boomstructuur.

>[!IMPORTANT]
>
>Houd er rekening mee dat deze wijziging kan leiden tot problemen met de consistentie en synchronisatie van gegevens.

### Een nieuwe instantie maken {#creating-a-new-instance}

Als verschillende internationale gebruikers aan hetzelfde exemplaar willen werken, moet u tijdzones configureren wanneer u het exemplaar maakt voor het beheer van tijdvertragingen tussen landen. Selecteer tijdens het maken van een instantie de datum- en tijdbeheermodus in de sectie **[!UICONTROL Time zone]** van het databaseconfiguratiestadium.

Schakel de optie **[!UICONTROL UTC database (date fields with time zone)]** in om alle gegevens met datums en tijden op te slaan in UTC-indeling (SQL-velden en XML-velden).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Als u **Oracle** gebruikt, moeten de timezone-bestanden (.dat) van de Oracle-clientlagen compatibel zijn met de tijdzonebestanden die op de server zijn geïnstalleerd.

Als de database geen UTC is, kunt u een van de tijdzones selecteren die in de vervolgkeuzelijst worden aangeboden. U kunt ook de tijdzone van de server gebruiken of de optie UTC (Coordinated Universal Time) selecteren.

![](assets/install_wz_unselect_utc_option.png)

Wanneer de optie **[!UICONTROL UTC Database (date fields with time zone)]** is geselecteerd, worden de SQL-velden opgeslagen in de indeling TIMESTAMP MET TIMEZONE.

Anders, worden zij opgeslagen in het lokale formaat en u zult de tijdzone moeten selecteren om op het gegevensbestand toe te passen.

### Migratie {#migration}

Wanneer het migreren aan een vroegere versie (zonder tijdzonebeheer), zult u de wijze van de datumopslag in het gegevensbestand moeten bepalen.

Om verenigbaarheid met externe hulpmiddelen die tot het gegevensbestand van Adobe Campaign toegang hebben, **Date+time** typeSQL gebieden blijven in lokaal formaat door gebrek worden opgeslagen.

XML-velden met datums worden nu opgeslagen in UTC. Tijdens het laden worden velden die niet de UTC-indeling hebben, automatisch geconverteerd met de tijdzone van de servers. Dit betekent dat alle XML-velden progressief worden omgezet in UTC-indeling.

Als u een bestaande instantie wilt gebruiken, voegt u de optie **WdbcTimeZone** toe en voert u de tijdzone van de instantie in.

>[!IMPORTANT]
>
>Controleer of de juiste waarde is geconfigureerd voor de optie WdbcTimeZone: latere wijzigingen kunnen tot inconsistenties leiden .

Voorbeeld van mogelijke waarden:

* Europa/Parijs,
* Europa/Londen,
* Amerika/New_York, enz.

   Deze waarden zijn afkomstig uit de tz-database (Olson). Raadpleeg [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) voor meer informatie.

