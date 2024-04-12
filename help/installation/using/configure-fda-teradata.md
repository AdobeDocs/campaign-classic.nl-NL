---
product: campaign
title: Toegang tot Teradata configureren
description: Leer hoe u toegang tot Teradata kunt configureren in FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3a5856c3-b642-4722-97ff-6ae7107efdbe
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1629'
ht-degree: 0%

---

# Toegang tot Teradata configureren {#configure-access-to-teradata}



Campagne gebruiken [Federale gegevenstoegang](../../installation/using/about-fda.md) (FDA) optie voor het verwerken van informatie die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot Teradata te configureren.

1. Installeren en configureren [Teradata-stuurprogramma&#39;s](#teradata-config)
1. De Teradata configureren [externe rekening](#teradata-external) in Campagne
1. Instellen [extra configuratie](#teradata-additional-configurations) voor Teradata- en Campagneserver

## Configuratie van teradata {#teradata-config}

U moet stuurprogramma&#39;s installeren voordat Teradata verbinding kan maken met de campagne.

1. Installeer de [ODBC-stuurprogramma voor Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   Het bestaat uit drie pakketten die in de volgende volgorde op Red Hat (of CentOS)/Suse kunnen worden geïnstalleerd:

   * TeraGSS
   * tdicu1510 (installeer het met setup_wrapper.sh)
   * tdodbc1510 (installeer het met setup_wrapper.sh)

1. Vorm het ODBC bestuurder. De configuratie kan in de standaarddossiers worden uitgevoerd: **/etc/odbc.ini** voor algemene parameters en /etc/odbcinst.ini voor het declareren van bestuurders:

   * **/etc/odbc.ini**

     ```
     [ODBC]
     InstallDir=/etc/
     ```

     &quot;InstallDir&quot; komt overeen met de locatie van de **odbcinst.ini** bestand.

   * **/etc/odbcinst.ini**

     ```
     [ODBC DRIVERS]
     teradata=Installed
     
     [teradata]
     Driver=/opt/teradata/client/17.10/lib64/tdataodbc_sb64.so
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
>Als u verbinding maakt met een externe Teradata-database in FDA, hebt u aanvullende configuratiestappen nodig op de Adobe Campaign-server. [Meer informatie](#teradata-additional-configurations).
>

## Externe rekening teradata{#teradata-external}

Met de externe account van Teradata kunt u uw Campagne-instantie verbinden met uw externe database van Teradata.

1. Van campagne **[!UICONTROL Explorer]**, klikt u op **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klikken **[!UICONTROL New]** en selecteert u **[!UICONTROL External database]** als **[!UICONTROL Type]**.

   ![](assets/ext_account_19.png)

1. Om te vormen **[!UICONTROL Teradata]** externe account, moet u opgeven:

   * **[!UICONTROL Type]**: Kies de optie **[!UICONTROL Teradata]** type.

   * **[!UICONTROL Server]**: URL of naam van uw Teradata-server

   * **[!UICONTROL Account]**: Naam van de account die wordt gebruikt voor toegang tot de database Teradata

   * **[!UICONTROL Password]**: Wachtwoord dat wordt gebruikt om verbinding te maken met de database Teradata

   * **[!UICONTROL Database]**: Naam van de database (optioneel)

   * **[!UICONTROL Options]**: Opties die door Teradata moeten worden doorgegeven. Gebruik de volgende indeling: &#39;parameter=value&#39;. Gebruik een puntkomma als scheidingsteken tussen waarden.

   * **[!UICONTROL Timezone]**: Tijdzone ingesteld in Teradata. [Meer informatie](#timezone)

De connector ondersteunt de volgende opties:

| Optie | Beschrijving |
|---|---|
| TD_MAX_SESSIONS | Specificeert het maximumaantal openings van een sessies dat de Parallelle Transporter van de Teradata voor een exploitantbaan kan verwerven. |
| TimeZoneName | Naam van de servertijdzone. |
| CharacterSet | Wordt gebruikt om de tekenset Teradata te configureren. <br>Raadpleeg voor meer informatie hierover [deze pagina](https://docs.teradata.com/r/ODBC-Driver-for-Teradata-User-Guide/May-2017/Configuration-of-odbc.ini-in-UNIX/Linux-and-Apple-OS-X/Teradata-DSN-Options#rub1478609534082__table_N102D3_N102B6_N102B3_N10001). |
| IANAppCodePage | Codepagina van ODBC-toepassing. <br>Raadpleeg voor meer informatie hierover [deze pagina](https://docs.teradata.com/r/ODBC-Driver-for-Teradata-User-Guide/May-2017/ODBC-Driver-for-Teradata-Application-Development/International-Character-Set-Support/Application-Code-Page) |

### Extra externe ODBC-accounts toevoegen {#add-external}

>[!NOTE]
>
> Deze optie is niet beschikbaar voor builds ouder dan versie 7.3.1.

Het stuurprogramma voor Teradata biedt een eigen ODBC-bibliotheek, maar deze bibliotheek is mogelijk niet compatibel met andere externe ODBC-accounts.

Als u een andere externe rekening wilt vormen die ODBC, bijvoorbeeld Snowflake ook gebruikt, zult u een optie ODBCLib moeten toevoegen die aan de weg van de standaardODBC bibliotheek wordt geplaatst (`/usr/lib/x86_64-linux-gnu/libodbc.so` over Debian en `/usr/lib64/libodbc.so` op RHEL/CentOS).

![](assets/ext_account_24.png)

### Query-streepjescodes

Wanneer meerdere Adobe Campaign-gebruikers verbinding maken met dezelfde FDA Teradata-externe account, wordt de **[!UICONTROL Query banding]** kunt u een queryband instellen, dat wil zeggen een set sleutel-/waardeparen, voor een sessie.

![](assets/ext_account_20.png)

Wanneer deze optie wordt gevormd, telkens als een gebruiker van de Campagne een vraag op het gegevensbestand van Teradata uitvoert, zal Adobe Campaign meta- gegevens verzenden, die uit een lijst van sleutels bestaan, verbonden aan deze gebruiker. Deze gegevens kunnen dan door de beheerders van Teradata voor controledoeleinden worden gebruikt of toegangsrechten beheren.

>[!NOTE]
>
>Voor meer informatie over **[!UICONTROL Query banding]**, verwijst u naar de [Teradata-documentatie](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

Voer de onderstaande stappen uit om querybanding te configureren:

1. Gebruik de  **[!UICONTROL Default]** om een standaardvraagband in te gaan die zal worden gebruikt als een gebruiker geen bijbehorende vraagband heeft. Als dit veld leeg blijft, kunnen gebruikers zonder queryband geen Teradata gebruiken.

1. Gebruik de **[!UICONTROL Users]** veld voor het opgeven van een queryband voor elke gebruiker. U kunt zoveel sleutel-/waardeparen toevoegen als u nodig hebt, bijvoorbeeld priority=1;workload=high. Als er geen queryband is toegewezen aan de gebruiker, wordt **[!UICONTROL Default]** wordt toegepast.

1. Controleer de **[!UICONTROL Active]** vak om deze functie te activeren

#### Problemen met externe accounts oplossen {#external-account-troubleshooting}

Als de volgende fout optreedt tijdens het testen van de verbinding **TIM-030008 Datum &#39;2&#39;: ontbrekend teken(s) (iRc=-53)** Controleer of het ODBC-stuurprogramma correct is geïnstalleerd en of LD_LIBRARY_PATH (Linux) / PATH (Windows) is ingesteld voor de campagneserver.

De fout **ODB-240000 ODBC-fout: [Microsoft][ODBC Driver Manager] Naam gegevensbron niet gevonden en geen standaardstuurprogramma opgegeven.** treedt met Windows op als u een 16.X-stuurprogramma gebruikt. Adobe Campaign verwacht dat de naam van de teradata &#39;{teradata}&quot; in odbcinst.ini.

* Vanaf Campagne 18.10 kunt u ODBCDriverName=&quot;Teradata Database ODBC Driver 16.10&quot;in de opties van de externe rekening toevoegen. Het versienummer kan veranderen, de nauwkeurige naam kan worden gevonden door odbcad32.exe in werking te stellen en tot de Drivers tabel toegang te hebben.

* Als u een oudere versie van de Campagne gebruikt, zult u de Teradata sectie van odbcinst.ini moeten kopiëren die door de bestuurdersinstallatie aan een nieuwe sectie wordt gecreeerd genoemd Teradata. In dit geval kan Regedit worden gebruikt. Als uw basis in latin1 is, zult u moeten toevoegen **APICharSize=1** in de opties.

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

Adobe Campaign stelt geen beveiligingsmodus (fallback) in voor de objecten die worden gemaakt in de database. Mogelijk moet u een standaard instellen voor de gebruiker die Adobe Campaign gebruikt om verbinding te maken met de Teradata-database met behulp van de volgende query:

| standaard fallback uitschakelen |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

### MD5-installatie {#md5-installation}

Als u md5-functies wilt gebruiken in uw Adobe Campaign-instantie, moet u de gebruikersmodusfunctie vanuit deze [page](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

De sha1 van het gedownloade bestand is als volgt 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Om md5 te installeren:

1. Pak het bestand md5_20080530.zip uit.

1. Ga naar de map md5/src.

1. Verbind met uw gegevensbestand van Teradata gebruikend bteq.

1. Voer de volgende opdracht bteq uit:

   ```
   .run file = hash_md5.btq
   ```

### SHA2-installatie {#sha2-installation}

Als u sha2 functies in uw instantie van Adobe Campaign wilt gebruiken, zult u de functie van de gebruikerswijze op uw gegevensbestand van Teradata van dit moeten installeren [page](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

De sha1 van het gedownloade bestand is als volgt: e87438d37424836358bd3902cf1adeb629349780.

Om sha2 te installeren:

1. Pak het zip-bestand teradata-udf-sha2-1.0.zip uit.

1. Ga naar de map teradata-udf-sha2-1.0/src.

1. Verbind met uw gegevensbestand van Teradata gebruikend bteq.

1. Voer de twee volgende bitmapopdrachten uit:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

### UDF_UTF16TO8-installatie {#UDF-UTF16TO8-installation}

Als u de functies udf_utf16to8 in uw Adobe Campaign-instantie wilt gebruiken, installeert u de gebruikersmodusfunctie in uw Teradata-database via de **Teradata unicode, gereedschapset**.

De sha1 van het gedownloade bestand is als volgt: e58235f434f52c71316a577cb48e20b97d24f470.

U installeert als volgt udf_utf16to8:

1. Pak het zip-bestand utk_release1.7.0.0.zip uit.

1. Zoek naar udf_utf16to8.o in de gehaalde dossiers en navigeer aan de folder die het dossier bevat. Deze moet utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/ worden genoemd.

1. Verbind met uw gegevensbestand van Teradata gebruikend bteq.

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

* Teradata ODBC-stuurprogramma, te vinden in dit [page](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata Tools and Utilities (gebruikt voor bulkload), te vinden in deze [page](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

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

### Installatie van gereedschappen en hulpprogramma&#39;s voor teradata {#teradata-tools-installation}

Gereedschappen installeren:

1. Extraheer het bestand TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz.

1. Ga naar de map TeradataToolsAndUtilitiesBase/Linux/i386-x864/tdicu.

1. Voer setup_wrapper.sh uit.

1. Ga naar de map TeradataToolsAndUtilitiesBase/Linux/i386-x864/cliv2.

1. Voer setup_wrapper.sh uit.

1. Ga naar de map TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Voer setup_wrapper.sh uit.

1. Een bestand libtelapi.so moet beschikbaar zijn in /opt/teradata/client/16.20/lib64.

## Configuratie van de campagneserver voor Windows {#campaign-server-windows}

U moet eerst Teradata Tools en Hulpprogramma&#39;s voor Vensters downloaden. U kunt het van dit downloaden [page](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Zorg ervoor dat u het ODBC-stuurprogramma en de Teradata Parallel Transporter Base installeert. Het zal telapi.dll installeren die wordt gebruikt om bulklading op het gegevensbestand van Teradata te doen.

Zorg ervoor dat het pad van het stuurprogramma en de hulpprogramma&#39;s zich in de PATH-variabele bevindt die de server tijdens de uitvoering zal hebben. Standaard is het pad C:\Program Files (x86)\Teradata\Client\15.10\bin op Windows 32 bits of C:\Program Files\Teradata\Client\15.10\bin op 64 bits).

## Tijdzone {#timezone}

Teradata gebruikt de naam van de tijdzone die niet standaard is, kunt u de lijst in de [Teradata](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). Adobe Campaign probeert de tijdzone die in de externe configuratie is opgegeven om te zetten in iets wat Teradata begrijpt. Als er geen overeenkomst wordt gevonden, wordt de dichtstbijzijnde GMT+X (of GMT-X)-tijdzone gevonden voor de sessie, met een waarschuwing in het logbestand.

De conversie is voltooid en er wordt een bestand met de naam teradata_timezones.txt gelezen dat zich in de volgende gegevensmap moet bevinden: /usr/local/neolane/nl6/datakit onder Linux. Als u dit bestand bewerkt, moet u contact opnemen met het Adobe Campaign-team om de wijziging in de broncode door te voeren anders wordt dit bestand overschreven tijdens de volgende campagneupdate.

De tijdzone die wordt gebruikt om te verbinden zal worden vermeld wanneer het runnen van nlserver met - verbose schakelaar, bijvoorbeeld:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Als de gebruikte tijdzone niet de juiste is, kan een optie met de naam &quot;TimeZoneName&quot; worden toegevoegd aan de externe account. In dat geval gebruikt u de waarde Teradata, bijvoorbeeld &quot;TimeZoneName=Europe Central&quot;.

Wanneer het gebruiken van bulklading, of &quot;snelle lading&quot;in de documenten van Teradata, kan de Campagne niet op de tijdzone wijzen. Daarom wordt geadviseerd om de standaardtijdzone van de gebruiker te plaatsen die de Campagne zal gebruiken om te verbinden:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```
