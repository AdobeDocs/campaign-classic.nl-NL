---
title: De database maken en configureren
seo-title: De database maken en configureren
description: De database maken en configureren
seo-description: null
page-status-flag: never-activated
uuid: e5143d55-61fa-416a-80db-c29a0caf9a3e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 7dd8a6a5-7cca-4e92-8226-1b9e450dfaf9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc

---


# De database maken en configureren{#creating-and-configuring-the-database}

Wanneer u een database maakt, biedt Adobe Campaign twee verschillende opties:

1. Een database maken of recyclen: Kies deze opties als u een nieuwe database wilt maken of een bestaande database opnieuw wilt gebruiken. Zie [Zaak 1: Een database](#case-1--creating-recycling-a-database)maken/recyclen.
1. Een bestaande database gebruiken: Kies deze optie als de beheerder al een lege database heeft gemaakt en u deze wilt gebruiken. of om de structuur van een bestaande database uit te breiden. Zie [zaak 2: Een bestaande database](#case-2--using-an-existing-database)gebruiken.

De configuratiestappen worden hieronder beschreven.

>[!CAUTION]
>
>Namen van databases, gebruikers en schema&#39;s mogen niet beginnen met een getal of speciale tekens bevatten.
>
>Alleen de **interne** id kan deze bewerkingen uitvoeren. Raadpleeg de [interne id](../../installation/using/campaign-server-configuration.md#internal-identifier)voor meer informatie hierover.

## Zaak 1: Een database maken/recyclen {#case-1--creating-recycling-a-database}

De stappen voor het creëren van een database of het recyclen van een bestaande basis worden hieronder beschreven. Sommige configuraties zijn afhankelijk van de gebruikte database-engine:

De volgende stappen zijn hierbij betrokken:

* [Stap 1 - De database-engine](#step-1---selecting-the-database-engine)selecteren
* [Stap 2 - Verbinding maken met de server](#step-2---connecting-to-the-server),
* [Stap 3 - Verbinding en kenmerken van de database](#step-3---connection-and-characteristics-of-the-database),
* [Stap 4 - te installeren](#step-4---packages-to-install)pakketten,
* [Stap 5 - Aanmaakstappen](#step-5---creation-steps),
* [Stap 6 - Het creëren van het gegevensbestand](#step-6---creating-the-database).

### Stap 1 - De database-engine selecteren {#step-1---selecting-the-database-engine}

Selecteer de database-engine in de vervolgkeuzelijst.

![](assets/s_ncs_install_db_select_engine.png)

Ondersteunde databases worden weergegeven in de matrix [Compatibiliteit van de sectie](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Identificeer de server en kies het type van verrichting om uit te voeren. In dit geval, **[!UICONTROL Create or recycle a database]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

Afhankelijk van de geselecteerde database-engine kan de identificatie-informatie van de server variëren.

* Vul voor een **Oracle** -engine de **TNS-naam** in die voor de toepassingsserver is gedefinieerd.
* Voor een **PostgreSQL** - of **DB2** -engine moet u de DNS-naam (of het IP-adres) opgeven die op de toepassingsserver is gedefinieerd om toegang te krijgen tot de databaseserver.
* Voor een **Microsoft SQL Server** -engine moet u het volgende definiëren:

   1. de DNS-naam (of het IP-adres) die op de toepassingsserver is gedefinieerd voor toegang tot de databaseserver: **DNS** of **DNS\ `<instance>`** (instantiemodus),
   1. de authentificatiemethode die wordt gebruikt om tot de Server van Microsoft SQL toegang te hebben: **[!UICONTROL SQL Server authentication]** of **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_creation01.png)

### Stap 2 - Verbinding maken met de server {#step-2---connecting-to-the-server}

Definieer in het **[!UICONTROL Server access]** venster de toegang tot de databaseserver.

![](assets/s_ncs_install_db_oracle_creation02.png)

Om dit te doen, ga de naam en het wachtwoord van een het systeemrekening **van het** Beleid in dat toestemming heeft om tot de gegevensbestanden toegang te hebben, d.w.z.:

* **systeem** voor een Oracle-database,
* **zoals** voor een Microsoft SQL Server-database,
* **postgres** voor een PostgreSQL-database,
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

   Met de **[!UICONTROL Unicode database]** optie kunt u alle tekentypen in Unicode opslaan, ongeacht de taal.

   >[!NOTE]
   >
   >Met een Oracle-database kunt u met de **[!UICONTROL Unicode storage]** optie **NCLOB** - en **NVARCHAR** -tekstvelden gebruiken.
   > 
   >Als u deze optie niet selecteert, moet de tekenset (charset) van de Oracle-database gegevensopslag in alle talen inschakelen (AL32UTF8 wordt aanbevolen).

* Kies een tijdzone voor de database en geef op of u deze in UTC wilt plaatsen (indien beschikbaar).

   Voor meer op dit, verwijs naar het beheer [van de](../../installation/using/time-zone-management.md)Tijdzone.

### Stap 4 - Te installeren pakketten {#step-4---packages-to-install}

Selecteer de pakketten die u wilt installeren.

Raadpleeg de licentieovereenkomst om te controleren welke oplossingen en opties u mag installeren, zoals &quot;Interactie&quot; of &quot;Sociale marketing&quot;.

![](assets/s_ncs_install_modules.png)

### Stap 5 - Aanmaakstappen {#step-5---creation-steps}

In het **[!UICONTROL Creation steps]** venster kunt u het SQL-script weergeven en bewerken dat wordt gebruikt om de tabellen te maken.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Voor een Oracle-, Microsoft SQL Server- of PostSQL-database kan de beheerder ook de **opslagparameters** definiëren die moeten worden gebruikt bij het maken van databaseobjecten.

   Deze parameters krijgen de exacte namen van de tabelruimten (waarschuwing: hoofdlettergevoelig). Ze worden respectievelijk opgeslagen in het **[!UICONTROL Administration > Platform > Options]** knooppunt in de volgende opties:

   * **WdbcOptions_TableSpaceUser**: gebruikerstabellen die op een schema worden gebaseerd
   * **WdbcOptions_TableSpaceIndex**: index van gebruikerstabellen die op een schema worden gebaseerd
   * **WdbcOptions_TableSpaceWork**: werktabellen zonder schema
   * **WdbcOptions_TableSpaceWorkIndex**: index van werktabellen zonder schema

* Voor een Oracle-database moet de Adobe Campaign-gebruiker toegang hebben tot de Oracle-bibliotheken, meestal als lid van de **installatiegroep** .
* Met de **[!UICONTROL Set or change the administrator password]** optie kunt u het wachtwoord invoeren dat is gekoppeld aan de Adobe Campaign-operator met beheerdersrechten.

   We raden u aan om voor beveiligingsdoeleinden een beheerderswachtwoord voor een Adobe Campagne-account te definiëren.

### Stap 6 - De database maken {#step-6---creating-the-database}

In het laatste werkgebied van de wizard kunt u de database maken. Klik **[!UICONTROL Start]** om te bevestigen.

![](assets/s_ncs_install_db_oracle_creation06.png)

Zodra het gegevensbestand wordt gecreeerd, kunt u opnieuw verbinden om instantieconfiguratie te voltooien.

U moet nu de plaatsingstovenaar beginnen om het vormen van de instantie te beëindigen. Raadpleeg de wizard [Implementatie](../../installation/using/deploying-an-instance.md#deployment-wizard).

De verbindingsinstellingen voor de database die aan de instantie is gekoppeld, worden opgeslagen in het bestand **`/conf/config-<instance>.xml`** in de installatiemap van Adobe Campagne.

Voorbeeld van een configuratie van de Server van Microsoft SQL op base61 gegevensbestand verbonden aan de &quot;campagne&quot;rekening met zijn gecodeerd wachtwoord:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## Zaak 2: Bestaande databases gebruiken {#case-2--using-an-existing-database}

Het gegevensbestand, evenals de gebruiker, moet door de gegevensbestandbeheerder en de correct gevormde toegangsrechten zijn gecreeerd.

Voor een Oracle-database zijn de minimaal vereiste rechten bijvoorbeeld: VERLENEN VAN VERBINDING, MIDDELEN EN ONBEPERKTE TABLESPACE.

Om een bestaand gegevensbestand te gebruiken, zijn de configuratiestappen als volgt:

* [Stap 1 - De database-engine](#step-1---choosing-the-database-engine)kiezen
* [Stap 2 - Verbindingsinstellingen](#step-2---database-connection-settings)database,
* [Stap 3 - te installeren](#step-3---packages-to-install)pakketten,
* [Stap 4 - Aanmaakstappen](#step-4---creation-steps),
* [Stap 5 - Het creëren van het gegevensbestand](#step-5---creating-the-database).

### Stap 1 - De database-engine kiezen {#step-1---choosing-the-database-engine}

Kies de database-engine in de vervolgkeuzelijst.

![](assets/s_ncs_install_db_select_engine.png)

Identificeer de server en kies het type van verrichting u wilt uitvoeren. In dit geval, **[!UICONTROL Use an existing database]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

Afhankelijk van de geselecteerde database-engine kan de identificatie-informatie van de server variëren.

* Vul voor een **Oracle** -engine de **TNS-naam** in die voor de toepassingsserver is gedefinieerd.
* Voor een **PostgreSQL** - of **DB2** -engine moet u de DNS-naam (of het IP-adres) opgeven die op de toepassingsserver is gedefinieerd om toegang te krijgen tot de databaseserver.
* Voor een **Microsoft SQL Server** -engine moet u het volgende definiëren:

   1. de DNS-naam (of het IP-adres) die op de toepassingsserver is gedefinieerd voor toegang tot de databaseserver;
   1. de veiligheidsmethode die wordt gebruikt om tot de Server van Microsoft SQL toegang te hebben: **[!UICONTROL SQL Server authentication]** of **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Stap 2 - Verbindingsinstellingen database {#step-2---database-connection-settings}

Definieer in het **[!UICONTROL Database]** venster de instellingen voor de databaseverbinding.

![](assets/s_ncs_install_db_oracle_exists_02.png)

U moet de volgende instellingen definiëren:

* Voer de naam in van de te gebruiken database;
* Voer de naam en het wachtwoord in van de account die aan deze database is gekoppeld.

   >[!NOTE]
   >
   >Voor een Oracle-database hoeft u de accountnaam niet in te voeren.

* Geef aan of de database Unicode moet zijn of niet.

### Stap 3 - Te installeren pakketten {#step-3---packages-to-install}

Selecteer de pakketten die u wilt installeren.

Raadpleeg de licentieovereenkomst om te controleren welke oplossingen en opties u mag installeren, zoals &quot;Interactie&quot; of &quot;Leads&quot;.

![](assets/s_ncs_install_modules.png)

### Stap 4 - Aanmaakstappen {#step-4---creation-steps}

In het **[!UICONTROL Creation steps]** venster kunt u het SQL-script weergeven en bewerken dat wordt gebruikt om de tabellen te maken.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Voor Oracle-, Microsoft SQL Server- of PostSQL-databases kan de beheerder de **opslagparameters** definiëren die moeten worden gebruikt bij het maken van databaseobjecten.
* Voor een Oracle-database moet de Adobe Campaign-gebruiker toegang hebben tot de Oracle-bibliotheken, meestal als lid van de **installatiegroep** .
* Met de **[!UICONTROL Set or change the administrator password]** optie kunt u het wachtwoord invoeren dat is gekoppeld aan de Adobe Campaign-operator met beheerdersrechten.

   We raden u aan om voor beveiligingsdoeleinden een beheerderswachtwoord voor een Adobe Campagne-account te definiëren.

### Stap 5 - De database maken {#step-5---creating-the-database}

In het laatste werkgebied van de wizard kunt u de database maken. Klik **[!UICONTROL Start]** om te bevestigen.

![](assets/s_ncs_install_db_oracle_creation06.png)

Wanneer het maken van een database is voltooid, kunt u opnieuw verbinding maken om de instantieconfiguratie te voltooien.

U moet nu de plaatsingstovenaar beginnen om het vormen van de instantie te beëindigen. Raadpleeg de wizard [Implementatie](../../installation/using/deploying-an-instance.md#deployment-wizard).

De verbindingsinstellingen voor de database die aan de instantie is gekoppeld, worden opgeslagen in het bestand **`/conf/config-<instance>.xml`** in de installatiemap van Adobe Campagne.

Voorbeeld van een configuratie van de Server van Microsoft SQL op base61 gegevensbestand verbonden aan de &quot;campagne&quot;rekening met zijn gecodeerd wachtwoord:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

