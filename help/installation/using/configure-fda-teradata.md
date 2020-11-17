---
title: Toegang tot metagegevens configureren
description: Leer hoe u toegang tot metagegevens in FDA configureert
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 30eaabba8962c518c734cc4e9ad27065cfe9d467
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 0%

---


# Toegang tot metagegevens configureren {#configure-access-to-teradata}

Gebruik de optie Campagne [Federated Data Access](../../installation/using/about-fda.md) (FDA) om informatie te verwerken die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot Teradata te configureren.

1. Drivers voor [metagegevens installeren en configureren](#teradata-config)
1. De [externe account](#teradata-external) voor Teradata configureren in Campagne
1. Stel [extra configuratie](#teradata-additional-configurations) in voor de Teradata and Campaign-server

## Teragegevensconfiguratie {#teradata-config}

U moet stuurprogramma&#39;s installeren voordat Teradata verbinding kan maken met Campagne.

1. Installeer het [ODBC-stuurprogramma voor Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   Het bestaat uit drie pakketten die in de volgende volgorde op Red Hat (of CentOS)/Suse kunnen worden geïnstalleerd:

   * TeraGSS
   * tdicu1510 (installeer het met setup_wrapper.sh)
   * tdodbc1510 (installeer het met setup_wrapper.sh)

1. Configureer het ODBC-stuurprogramma. De configuratie kan in de standaarddossiers worden uitgevoerd: **/etc/odbc.ini** voor algemene parameters en /etc/odbcinst.ini voor het declareren van stuurprogramma&#39;s:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; komt overeen met de locatie van het bestand **odbcinst.ini** .

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed
      
      [teradata]
      Driver=/opt/teradata/client/15.10/lib64/tdata.so
      APILevel=CORE
      ConnectFunctions=YYY
      DriverODBCVer=3.51
      SQLLevel=1
      ```

1. Geef de omgevingsvariabelen van de Adobe Campaign-server op:

   * **LD_LIBRARY_PATH**: /opt/teradata/client/15.10/lib64 and /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**: locatie van het bestand odbc.ini (bijvoorbeeld /etc/odbc.ini).
   * **NLSPATH**: locatie van het bestand opermsgs.cat (/opt/teradata/client/15.10/msg/opermsgs.cat)

>[!NOTE]
>
>Als u verbinding maakt met een externe database met Teradata in FDA, hebt u aanvullende configuratiestappen nodig op de Adobe Campaign-server. [Meer informatie](#teradata-additional-configurations).


## Externe rekening met teragegevens{#teradata-external}

Met de externe account Teradata kunt u uw Campagne-instantie verbinden met uw externe database Teradata.

1. Klik in Campagne **[!UICONTROL Explorer]** op **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

   ![](assets/ext_account_19.png)

1. Om de **[!UICONTROL Teradata]** externe rekening te vormen, moet u specificeren:

   * **[!UICONTROL Type]**: Kies het **[!UICONTROL Teradata]** type.

   * **[!UICONTROL Server]**: URL of naam van uw Teradata-server

   * **[!UICONTROL Account]**: Naam van de account die wordt gebruikt voor toegang tot de Teradata-database

   * **[!UICONTROL Password]**: Wachtwoord gebruikt om verbinding te maken met de Teradata-database

   * **[!UICONTROL Database]**: Naam van de database (optioneel)

   * **[!UICONTROL Options]**: Opties die door Teradata moeten worden doorgegeven. Gebruik de volgende indeling: &#39;parameter=value&#39;. Gebruik een halve kolom als scheidingsteken tussen waarden.

   * **[!UICONTROL Timezone]**: Tijdzone ingesteld in metagegevens. [Meer informatie](#timezone)

### Query-streepjescodes

Wanneer meerdere Adobe Campaign-gebruikers verbinding maken met dezelfde externe FDA Teradata-account, kunt u op het **[!UICONTROL Query banding]** tabblad een queryband instellen, dat wil zeggen een set sleutel-/waardeparen, voor een sessie.

![](assets/ext_account_20.png)

Wanneer deze optie wordt gevormd, telkens als een gebruiker van de Campagne een vraag op het gegevensbestand van Teradata uitvoert, zal Adobe Campaign meta- gegevens verzenden, die uit een lijst van sleutels bestaan, verbonden aan deze gebruiker. Deze gegevens kunnen vervolgens door de gegevensbeheerder van Teradata worden gebruikt voor auditdoeleinden of voor het beheer van toegangsrechten.

>[!NOTE]
>
>For more information on **[!UICONTROL Query banding]**, refer to the [Teradata documentation](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

Voer de onderstaande stappen uit om querybanding te configureren:

1. Gebruik **[!UICONTROL Default]** om een standaardvraagband in te gaan die zal worden gebruikt als een gebruiker geen bijbehorende vraagband heeft. Als dit veld leeg blijft, kunnen gebruikers zonder queryband geen gebruik maken van metagegevens.

1. Gebruik het **[!UICONTROL Users]** veld om een queryband voor elke gebruiker op te geven. U kunt zoveel sleutel-/waardeparen toevoegen als u nodig hebt, bijvoorbeeld priority=1;workload=high. Als aan de gebruiker geen queryband is toegewezen, wordt het **[!UICONTROL Default]** veld toegepast.

1. Schakel het **[!UICONTROL Active]** selectievakje in om deze functie te activeren

#### Problemen met externe accounts oplossen {#external-account-troubleshooting}

Als de volgende fout optreedt tijdens het testen van de verbinding **TIM-030008 Date &#39;2&#39;: ontbrekende tekens (iRc=-53)** zorgen ervoor dat het ODBC-stuurprogramma correct is geïnstalleerd en dat LD_LIBRARY_PATH (Linux) / PATH (Windows) is ingesteld voor de campagneserver.

De fout **ODB-240000 ODBC: [Naam van Microsoft][ODBC Driver Manager] -gegevensbron niet gevonden en er is geen standaardstuurprogramma opgegeven.** treedt met Windows op als u een 16.X-stuurprogramma gebruikt. Adobe Campaign verwacht dat de teragegevens &#39;{teradata}&#39; worden genoemd in odbcinst.ini.

* Vanaf Campagne 18.10 kunt u ODBCDriverName=&quot;Teradata Database ODBC Driver 16.10&quot; toevoegen in de opties van de externe account. Het versienummer kan veranderen, de nauwkeurige naam kan worden gevonden door odbcad32.exe in werking te stellen en tot de Drivers tabel toegang te hebben.

* Als u een oudere versie van de Campagne gebruikt, zult u de sectie van Teradata van odbcinst.ini moeten kopiëren die door de bestuurdersinstallatie aan een nieuwe sectie wordt gecreeerd genoemd Teradata. In dit geval kan Regedit worden gebruikt. Als uw basis in latin1 is, zult u **APICharSize=1** in de opties moeten toevoegen.

## Aanvullende configuraties {#teradata-additional-configurations}

<!--
### Compatibility {#teradata-compatibility}

**Based in Unicode**

| Database version | Driver version |  Minimal Campaign version required |  Note |
|:-:|:-:|:-:|:-:|
| 15  |  15 |  Campaign Classic 17.9 | Under Linux: Queries with timestamp may fail (fixed in build 8937 for 18.4 and 8977 for 18.10) In debug mode, warnings relative to bad memory usage in the driver may occur. |
| 15  | 16  | Campaign Classic 17.9  | Recommended setup for a Teradata 15 database under Linux.  |
|  16 | 16  | Campaign Classic 18.10 |  Unicode characters with surrogate pairs are not fully handled. Using surrogate characters in data should work. Using surrogates in a filtering condition of a query will not work without this change. |
| 16  |  15 |  Campaign Classic 19.0 |  &nbsp; |

**Based in Latin1**

Versions previous to Adobe Campaign Classic 17.9 only supported Teradata Latin-1 database.

Starting from Adobe Campaign Classic 17.9, we now support by default Teradata database in Unicode.

Customers with a Latin-1 Teradata database migrating to a recent Campaign Classic release will have to add the parameter APICharSize=1 in the options of the external account.
-->

### Gebruikersconfiguratie {#user-configuration}

De volgende rechten zijn vereist voor de externe database: aangepaste procedures maken/neerzetten/uitvoeren, tabellen maken/neerzetten/invoegen/selecteren. Het kan ook zijn dat u functies voor de gebruikersmodus moet maken als u de functies md5 en sha2 op uw Adobe Campaign-instantie wilt gebruiken.

Zorg ervoor om de correcte tijdzone te vormen. Deze moet overeenkomen met wat wordt ingesteld in de externe account die wordt gemaakt in de Adobe Campaign-instantie.

Adobe Campaign stelt geen beveiligingsmodus (fallback) in voor de objecten die worden gemaakt in de database. Mogelijk moet u een standaardquery instellen voor de gebruiker die Adobe Campaign gebruikt om verbinding te maken met de Teradata-database met behulp van de volgende query:

| standaard fallback uitschakelen |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

### MD5-installatie {#md5-installation}

Als u md5-functies wilt gebruiken in uw Adobe Campaign-instantie, moet u de gebruikersmodusfunctie installeren in uw Teradata-database vanaf deze [pagina](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

De sha1 van het gedownloade bestand is als volgt 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Om md5 te installeren:

1. Pak het bestand md5_20080530.zip uit.

1. Ga naar de map md5/src.

1. Maak verbinding met uw Teradata-database met behulp van bteq.

1. Voer de volgende opdracht bteq uit:

   ```
   .run file = hash_md5.btq
   ```

### SHA2-installatie {#sha2-installation}

Als u sha2-functies wilt gebruiken in uw Adobe Campaign-instantie, moet u de gebruikersmodusfunctie installeren in uw Teradata-database vanaf deze [pagina](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

De sha1 van het gedownloade bestand is als volgt: e87438d37424836358bd3902cf1adeb629349780.

Om sha2 te installeren:

1. Pak het zip-bestand teradata-udf-sha2-1.0.zip uit.

1. Ga naar de map teradata-udf-sha2-1.0/src.

1. Maak verbinding met uw Teradata-database met behulp van bteq.

1. Voer de twee volgende bitmapopdrachten uit:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

### UDF_UTF16TO8-installatie {#UDF-UTF16TO8-installation}

Als u udf_utf16to8-functies in uw Adobe Campaign-instantie wilt gebruiken, moet u de gebruikersmodusfunctie in uw Teradata-database installeren vanuit de **Teradata unicode tool kit** van deze [pagina](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip).

De sha1 van het gedownloade bestand is als volgt: e58235f434f52c71316a577cb48e20b97d24f470.

U installeert als volgt udf_utf16to8:

1. Pak het zip-bestand utk_release1.7.0.0.zip uit.

1. Zoek naar udf_utf16to8.o in de gehaalde dossiers en navigeer aan de folder die het dossier bevat. De naam moet utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/ zijn.

1. Maak verbinding met uw Teradata-database met behulp van bteq.

1. Typ de volgende opdracht in het vak Bteq:

   ```
   REPLACE FUNCTION udf_utf16to8 (
   inputString VARCHAR(8000) CHARACTER SET UNICODE
   ) RETURNS VARCHAR(16000) CHARACTER SET LATIN
   LANGUAGE C
   NO SQL
   EXTERNAL NAME 'CO!i18n103!udf_utf16to8.o!F!udf_utf16to8'
   PARAMETER STYLE SQL;
   
   -- Test: should return 410042
   SELECT CAST(Char2HexInt(UDF_UTF16to8(_UNICODE'004100000042'XC)) AS VARCHAR(100));
   ```

## Configuratie van de campagnereserver voor Linux {#campaign-server-linux}

Voor de installatie van het stuurprogramma is het volgende vereist:

* Het ODBC-stuurprogramma voor Teradata, dat u vindt op deze [pagina](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata Tools and Utilities (used for the bulload), die u vindt op deze [pagina](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Bestandsnamen en sha1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f 44fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Als er geen pakket voor uw distributie van Linux is, kunt u installeren zoals verklaard op CentOS 7 (bijvoorbeeld gebruikend docker) en dan de inhoud van /opt/teradata op uw server van Adobe Campaign kopiëren.

### Installatie van ODBC-stuurprogramma {#odbc-installation}

ODBC-stuurprogramma installeren:

1. Extraheer het bestand tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Ga naar de directory tdodbc1620.

1. Mogelijk moet u het setscript herstellen:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Voer setup_wrapper.sh uit.

### Installatie van hulpprogramma&#39;s en hulpprogramma&#39;s {#teradata-tools-installation}

Gereedschappen installeren:

1. Extraheer het bestand TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz.

1. Ga naar de map TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Voer setup_wrapper.sh uit.

1. Ga naar de map TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Voer setup_wrapper.sh uit.

1. Ga naar de map TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Voer setup_wrapper.sh uit.

1. Een bestand libtelapi.so moet beschikbaar zijn in /opt/teradata/client/16.20/lib64.

## Configuratie van de campagneserver voor Windows {#campaign-server-windows}

U moet eerst de hulpprogramma&#39;s en hulpprogramma&#39;s van Teradata voor Windows downloaden. U kunt het van deze [pagina downloaden](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Installeer het ODBC-stuurprogramma en de Teradata Parallel Transporter Base. Het installeert telapi.dll dat wordt gebruikt voor het laden van grote hoeveelheden in de Teradata-database.

Zorg ervoor dat het pad van het stuurprogramma en de hulpprogramma&#39;s zich in de PATH-variabele bevindt die de server tijdens de uitvoering zal hebben. Standaard is het pad C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit).

## Tijdzone {#timezone}

De term gebruikt de naam van de tijdzone die niet standaard is, u kunt de lijst op de plaats [van](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA)Meta-gegevens vinden. Adobe Campaign probeert de tijdzone in de externe configuratie om te zetten in iets dat Teradata begrijpt. Als er geen overeenkomst wordt gevonden, wordt de dichtstbijzijnde GMT+X (of GMT-X)-tijdzone gevonden voor de sessie, met een waarschuwing in het logbestand.

De conversie is voltooid bij het lezen van een bestand met de naam teradata_timezones.txt dat zich in de volgende directory data zou moeten bevinden: /usr/local/neolane/nl6/datakit under linux. Als u dit bestand bewerkt, moet u contact opnemen met het Adobe Campaign-team om de wijziging in de broncode door te voeren anders wordt dit bestand overschreven tijdens de volgende campagneupdate.

De tijdzone die wordt gebruikt om te verbinden zal worden vermeld wanneer het runnen van nlserver met - verbose schakelaar, bijvoorbeeld:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Als de gebruikte tijdzone niet de juiste is, kan een optie met de naam &quot;TimeZoneName&quot; worden toegevoegd aan de externe account. In dat geval gebruikt u de waarde van de metagegevens, bijvoorbeeld &quot;TimeZoneName=Europe Central&quot;.

Bij het gebruik van bulkload of &#39;fast load&#39; in Teradata-documenten kan Campagne de tijdzone niet aangeven. Daarom wordt geadviseerd om de standaardtijdzone van de gebruiker te plaatsen die de Campagne zal gebruiken om te verbinden:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```
