---
product: campaign
title: De database maken en configureren
description: De database maken en configureren
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f40bab8c-5064-40d9-beed-101a9f22c094
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 2%

---

# De database maken en configureren{#creating-and-configuring-the-database}

![](../../assets/v7-only.svg)

Als u een database maakt, biedt Adobe Campaign twee verschillende opties:

1. Een database maken of recyclen: Kies deze opties als u een nieuwe database wilt maken of een bestaande database opnieuw wilt gebruiken. Zie [Zaak 1: Een database maken/recyclen](#case-1--creating-recycling-a-database).
1. Een bestaande database gebruiken: Kies deze optie als de beheerder al een lege database heeft gemaakt en u deze wilt gebruiken. of om de structuur van een bestaande database uit te breiden. Zie [Zaak 2: Bestaande databases gebruiken](#case-2--using-an-existing-database).

De configuratiestappen worden hieronder beschreven.

>[!CAUTION]
>
>Namen van databases, gebruikers en schema&#39;s mogen niet beginnen met een getal of speciale tekens bevatten.
>
>Alleen de **internal** identificator kan deze bewerkingen uitvoeren. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier) voor meer informatie.

## Zaak 1: Een database maken/recyclen {#case-1--creating-recycling-a-database}

De stappen voor het creëren van een database of het recyclen van een bestaande basis worden hieronder beschreven. Sommige configuraties zijn afhankelijk van de gebruikte database-engine:

De volgende stappen zijn hierbij betrokken:

* [Stap 1 - De database-engine selecteren](#step-1---selecting-the-database-engine),
* [Stap 2 - Verbinding maken met de server](#step-2---connecting-to-the-server),
* [Stap 3 - Verbinding en kenmerken van de database](#step-3---connection-and-characteristics-of-the-database),
* [Stap 4 - Te installeren pakketten](#step-4---packages-to-install),
* [Stap 5 - Aanmaakstappen](#step-5---creation-steps),
* [Stap 6 - De database maken](#step-6---creating-the-database).

### Stap 1 - De database-engine selecteren {#step-1---selecting-the-database-engine}

Selecteer de database-engine in de vervolgkeuzelijst.

![](assets/s_ncs_install_db_select_engine.png)

Ondersteunde databases worden vermeld in de campagne [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

Identificeer de server en kies het type van verrichting om uit te voeren. In dit geval: **[!UICONTROL Create or recycle a database]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

Afhankelijk van de geselecteerde database-engine kan de identificatie-informatie van de server variëren.

* Voor een **Oracle** motor, bevolken **TNS-naam** gedefinieerd voor de toepassingsserver.
* Voor een **PostgreSQL** of **DB2** -engine, moet u de DNS-naam (of het IP-adres) opgeven die op de toepassingsserver is gedefinieerd om toegang te krijgen tot de databaseserver.
* Voor een **Microsoft SQL Server** engine, moet u definiëren: de DNS-naam (of het IP-adres) die op de toepassingsserver is gedefinieerd voor toegang tot de databaseserver: **DNS** of **DNS`\<instance>`** (instantiemodus),

   >[!CAUTION]
   >
   > Beginnend 20.3, wordt de authentificatie van NT van Vensters ontmanteld. **[!UICONTROL SQL Server authentication]** is nu de enige verificatiemodus beschikbaar voor Microsoft SQL Server. [Meer informatie](../../rn/using/deprecated-features.md)

   ![](assets/s_ncs_install_db_mssql_creation01.png)

### Stap 2 - Verbinding maken met de server {#step-2---connecting-to-the-server}

In de **[!UICONTROL Server access]** , definieert u de toegang tot de databaseserver.

![](assets/s_ncs_install_db_oracle_creation02.png)

Voer hiertoe de naam en het wachtwoord van een **Systeemaccount voor beheerders** die toegang heeft tot de databanken, d.w.z.:

* **systeem** voor een database van Oracles,
* **sa** voor een Microsoft SQL Server-database,
* **postzegels** voor een PostgreSQL-database,
* **db2inst1** voor een DB2-database.

### Stap 3 - Verbinding en kenmerken van de database {#step-3---connection-and-characteristics-of-the-database}

In de volgende stap kunt u de instellingen configureren voor het aanmelden bij de database.

![](assets/s_ncs_install_db_oracle_creation03.png)

U moet de volgende instellingen definiëren:

* Geef de naam op van de database die u wilt maken.

   >[!NOTE]
   >
   >Voor een DB2-database mag de naam van de database maximaal 8 tekens bevatten.

* Voer het wachtwoord in van de account die aan deze database is gekoppeld.
* Geef aan of de database zich in Unicode moet bevinden.

   De **[!UICONTROL Unicode database]** Hiermee kunt u alle tekentypen opslaan in Unicode, ongeacht de taal.

   >[!NOTE]
   >
   >Met een gegevensbestand van het Oracle, **[!UICONTROL Unicode storage]** gebruiken **NCLOB** en **NVARCHAR** tekstvelden.
   > 
   >Als u deze optie niet selecteert, moet de tekenset (charset) van de database van het Oracle gegevensopslag in alle talen inschakelen (AL32UTF8 wordt aanbevolen).

* Kies een tijdzone voor de database en geef op of u deze in UTC wilt plaatsen (indien beschikbaar).

   Raadpleeg voor meer informatie hierover [Tijdzonebeheer](../../installation/using/time-zone-management.md).

### Stap 4 - Te installeren pakketten {#step-4---packages-to-install}

Selecteer de pakketten die u wilt installeren.

Raadpleeg de licentieovereenkomst om te controleren welke oplossingen en opties u mag installeren, zoals &quot;Interactie&quot; of &quot;Sociale marketing&quot;.

![](assets/s_ncs_install_modules.png)

### Stap 5 - Aanmaakstappen {#step-5---creation-steps}

De **[!UICONTROL Creation steps]** kunt u het SQL-script dat is gebruikt om de tabellen te maken, weergeven en bewerken.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Voor een Oracle, de Server van Microsoft SQL of het gegevensbestand PostgreSQL, kan de beheerder ook bepalen **opslagparameters** te gebruiken bij het maken van databaseobjecten.

   Deze parameters krijgen de exacte namen van de tabelruimten (waarschuwing: hoofdlettergevoelig). Zij worden respectievelijk in de **[!UICONTROL Administration > Platform > Options]** knoop in de volgende opties (zie [deze sectie](../../installation/using/configuring-campaign-options.md#database)):

   * **WdbcOptions_TableSpaceUser**: gebruikerstabellen die op een schema worden gebaseerd
   * **WdbcOptions_TableSpaceIndex**: index van gebruikerstabellen die op een schema worden gebaseerd
   * **WdbcOptions_TableSpaceWork**: werktabellen zonder schema
   * **WdbcOptions_TableSpaceWorkIndex**: index van werktabellen zonder schema

* Voor een gegevensbestand van het Oracle, moet de gebruiker van Adobe Campaign toegang tot de bibliotheken van het Oracle hebben, typisch als lid van **oinstall** groep.
* De **[!UICONTROL Set or change the administrator password]** kunt u het wachtwoord invoeren dat is gekoppeld aan de Adobe Campaign-operator met beheerdersrechten.

   We raden u aan om voor beveiligingsdoeleinden een Adobe Campaign-beheerderswachtwoord te definiëren.

### Stap 6 - De database maken {#step-6---creating-the-database}

In het laatste werkgebied van de wizard kunt u de database maken. Klik op **[!UICONTROL Start]** om te bevestigen.

![](assets/s_ncs_install_db_oracle_creation06.png)

Zodra het gegevensbestand wordt gecreeerd, kunt u opnieuw verbinden om instantieconfiguratie te voltooien.

U moet nu de plaatsingstovenaar beginnen om het vormen van de instantie te beëindigen. Zie [Implementatiewizard](../../installation/using/deploying-an-instance.md#deployment-wizard).

De verbindingsinstellingen voor de database die aan de instantie is gekoppeld, worden opgeslagen in het bestand **`/conf/config-<instance>.xml`** gevonden in de installatiemap van Adobe Campaign.

Voorbeeld van een Microsoft SQL Server-configuratie in de base61-database die is gekoppeld aan de &#39;campagne&#39;-account met het gecodeerde wachtwoord:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## Zaak 2: Bestaande databases gebruiken {#case-2--using-an-existing-database}

Het gegevensbestand, evenals de gebruiker, moet door de gegevensbestandbeheerder en de correct gevormde toegangsrechten zijn gecreeerd.

Voor een database van Oracles zijn de minimaal vereiste rechten bijvoorbeeld: GRANT CONNECT, RESOURCE en UNLIMITED TABLESPACE.

Om een bestaand gegevensbestand te gebruiken, zijn de configuratiestappen als volgt:

* [Stap 1 - De database-engine kiezen](#step-1---choosing-the-database-engine),
* [Stap 2 - Verbindingsinstellingen database](#step-2---database-connection-settings),
* [Stap 3 - Te installeren pakketten](#step-3---packages-to-install),
* [Stap 4 - Aanmaakstappen](#step-4---creation-steps),
* [Stap 5 - De database maken](#step-5---creating-the-database).

### Stap 1 - De database-engine kiezen {#step-1---choosing-the-database-engine}

Kies de database-engine in de vervolgkeuzelijst.

![](assets/s_ncs_install_db_select_engine.png)

Identificeer de server en kies het type van verrichting u wilt uitvoeren. In dit geval: **[!UICONTROL Use an existing database]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

Afhankelijk van de geselecteerde database-engine kan de identificatie-informatie van de server variëren.

* Voor een **Oracle** motor, bevolken **TNS-naam** gedefinieerd voor de toepassingsserver.
* Voor een **PostgreSQL** of **DB2** -engine, moet u de DNS-naam (of het IP-adres) opgeven die op de toepassingsserver is gedefinieerd om toegang te krijgen tot de databaseserver.
* Voor een **Microsoft SQL Server** engine, moet u definiëren:

   1. de DNS-naam (of het IP-adres) die op de toepassingsserver is gedefinieerd voor toegang tot de databaseserver;
   1. de veiligheidsmethode die wordt gebruikt om tot de Server van Microsoft SQL toegang te hebben: **[!UICONTROL SQL Server authentication]** of **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Stap 2 - Verbindingsinstellingen database {#step-2---database-connection-settings}

In de **[!UICONTROL Database]** , definieert u de instellingen voor de databaseverbinding.

![](assets/s_ncs_install_db_oracle_exists_02.png)

U moet de volgende instellingen definiëren:

* Voer de naam in van de te gebruiken database;
* Voer de naam en het wachtwoord in van de account die aan deze database is gekoppeld.

   >[!NOTE]
   >
   >Zorg ervoor dat zowel de naam van het schema als de gebruikersnaam overeenkomen. De geadviseerde manier om gegevensbestand te creëren is door cliënt van de campagneconsole.
   >Voor een database van een Oracle hoeft u de accountnaam niet in te voeren.

* Geef aan of de database Unicode moet zijn of niet.

### Stap 3 - Te installeren pakketten {#step-3---packages-to-install}

Selecteer de pakketten die u wilt installeren.

Raadpleeg de licentieovereenkomst om te controleren welke oplossingen en opties u mag installeren, zoals &quot;Interactie&quot; of &quot;Leads&quot;.

![](assets/s_ncs_install_modules.png)

### Stap 4 - Aanmaakstappen {#step-4---creation-steps}

De **[!UICONTROL Creation steps]** kunt u het SQL-script dat is gebruikt om de tabellen te maken, weergeven en bewerken.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Voor Oracle-, Microsoft SQL Server- of PostgreSQL-databases kan de beheerder de **opslagparameters** te gebruiken bij het maken van databaseobjecten.
* Voor een gegevensbestand van het Oracle, moet de gebruiker van Adobe Campaign toegang tot de bibliotheken van het Oracle hebben, typisch als lid van **oinstall** groep.
* De **[!UICONTROL Set or change the administrator password]** kunt u het wachtwoord invoeren dat is gekoppeld aan de Adobe Campaign-operator met beheerdersrechten.

   We raden u aan om voor beveiligingsdoeleinden een Adobe Campaign-beheerderswachtwoord te definiëren.

### Stap 5 - De database maken {#step-5---creating-the-database}

In het laatste werkgebied van de wizard kunt u de database maken. Klik op **[!UICONTROL Start]** om te bevestigen.

![](assets/s_ncs_install_db_oracle_creation06.png)

Wanneer het maken van een database is voltooid, kunt u opnieuw verbinding maken om de instantieconfiguratie te voltooien.

U moet nu de plaatsingstovenaar beginnen om het vormen van de instantie te beëindigen. Zie [Implementatiewizard](../../installation/using/deploying-an-instance.md#deployment-wizard).

De verbindingsinstellingen voor de database die aan de instantie is gekoppeld, worden opgeslagen in het bestand **`/conf/config-<instance>.xml`** gevonden in de installatiemap van Adobe Campaign.

Voorbeeld van een Microsoft SQL Server-configuratie in de base61-database die is gekoppeld aan de &#39;campagne&#39;-account met het gecodeerde wachtwoord:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```
