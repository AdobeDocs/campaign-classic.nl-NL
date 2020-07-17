---
title: Bijlagen
seo-title: FDA-bijlagen
description: FDA-bijlagen
seo-description: null
page-status-flag: never-activated
uuid: 2596fabc-679a-45c8-a62a-165c221654b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: a84a73a9-9930-449f-8b81-007a0e9d5233
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 353f5df040087175c9f211308704f1af1844ef2c
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 0%

---


# Bijlagen {#fda-appendices}

## Extra configuraties van Teradata {#teradata-configuration}

### Compatibiliteit {#teradata-compatibility}

**Gebaseerd in Unicode**

| Databaseversie | Stuurprogrammaversie | Minimale campagneversie vereist | Opmerking |
|:-:|:-:|:-:|:-:|
| 15 | 15 | Campaign Classic 17.9 | Onder Linux: Vragen met tijdstempel kunnen mislukken (hersteld in build 8937 voor 18.4 en 8977 voor 18.10) In de foutopsporingsmodus kunnen waarschuwingen optreden in verband met slecht geheugengebruik in het stuurprogramma. |
| 15 | 16 | Campaign Classic 17.9 | Aanbevolen installatie voor een Teradata 15-database onder Linux. |
| 16 | 16 | Campaign Classic 18.10 | Unicode-tekens met surrogaatparen worden niet volledig verwerkt. Het gebruik van vervangende tekens in gegevens moet werken. Het gebruiken van vervangingen in een het filtreren voorwaarde van een vraag zal niet zonder deze verandering werken. |
| 16 | 15 | niet ondersteund |   |

**Gebaseerd op Latin1**

Versies die ouder zijn dan Adobe Campaign Classic 17.9, ondersteunen alleen de Teradata Latin-1-database.

Vanaf Adobe Campaign Classic 17.9 ondersteunen we nu standaard Teradata-database in Unicode.

Klanten met een database met Latijn-1-gegevens die migreren naar een recente Campaign Classic-versie, moeten de parameter APICharSize=1 toevoegen in de opties van de externe account.

### Databaseconfiguratie {#database-configuration}

#### Gebruikersconfiguratie {#user-configuration}

De volgende rechten zijn vereist: aangepaste procedures maken/neerzetten/uitvoeren, tabellen maken/neerzetten/invoegen/selecteren. Het kan ook zijn dat u functies voor de gebruikersmodus moet maken als u de functies md5 en sha2 op uw Adobe Campaign-instantie wilt gebruiken.

Zorg ervoor om de correcte tijdzone te vormen. Deze moet overeenkomen met wat wordt ingesteld in de externe account die wordt gemaakt in de Adobe Campaign-instantie.

Adobe Campaign stelt geen beveiligingsmodus (fallback) in voor de objecten die worden gemaakt in de database. Mogelijk moet u een standaardquery instellen voor de gebruiker die Adobe Campaign gebruikt om verbinding te maken met de Teradata-database met behulp van de volgende query:

| standaard fallback uitschakelen |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

#### MD5-installatie {#md5-installation}

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

#### SHA2-installatie {#sha2-installation}

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

#### UDF_UTF16TO8-installatie {#UDF-UTF16TO8-installation}

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
   
### Configuratie van de campagneserver voor Linux {#campaign-server-linux}

Voor de installatie van het stuurprogramma is het volgende vereist:

* Het ODBC-stuurprogramma voor Teradata, dat u vindt op deze [pagina](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata Tools and Utilities (used for the bulload), die u vindt op deze [pagina](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Bestandsnamen en sha1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f 44fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Als er geen pakket voor uw distributie van Linux is, kunt u installeren zoals verklaard op CentOS 7 (bijvoorbeeld gebruikend docker) en dan de inhoud van /opt/teradata op uw server van Adobe Campaign kopiëren.

#### Installatie van ODBC-stuurprogramma {#odbc-installation}

ODBC-stuurprogramma installeren:

1. Extraheer het bestand tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Ga naar de directory tdodbc1620.

1. Mogelijk moet u het setscript herstellen:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Voer setup_wrapper.sh uit.

#### Installatie van hulpprogramma&#39;s en hulpprogramma&#39;s {#teradata-tools-installation}

Gereedschappen installeren:

1. Extraheer het bestand TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz.

1. Ga naar de map TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Voer setup_wrapper.sh uit.

1. Ga naar de map TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Voer setup_wrapper.sh uit.

1. Ga naar de map TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Voer setup_wrapper.sh uit.

1. Een bestand libtelapi.so moet beschikbaar zijn in /opt/teradata/client/16.20/lib64.

#### Configuratie stuurprogramma {#driver-configuration}

Meer op bestuurdersconfiguratie leren, verwijs naar deze [sectie](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

#### Omgevingsvariabelen {#environment-varaiables}

Raadpleeg deze [sectie](../../platform/using/legacy-connectors.md#configure-access-to-teradata)voor meer informatie over de omgevingsvariabelen van de Adobe Campaign-server.

### Configuratie campagneserver voor Windows #campagne-server-windows}

U moet eerst de hulpprogramma&#39;s en hulpprogramma&#39;s van Teradata voor Windows downloaden. U kunt het van deze [pagina downloaden](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Installeer het ODBC-stuurprogramma en de Teradata Parallel Transporter Base. Het installeert telapi.dll dat wordt gebruikt voor het laden van grote hoeveelheden in de Teradata-database.

Zorg ervoor dat het pad van het stuurprogramma en de hulpprogramma&#39;s zich in de PATH-variabele bevindt die de server tijdens de uitvoering zal hebben. Standaard is het pad C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit).

### Problemen met externe accounts oplossen {#external-account-troubleshooting}

Als de volgende fout optreedt tijdens het testen van de verbinding **TIM-030008 Date &#39;2&#39;: ontbrekende tekens (iRc=-53)** zorgen ervoor dat het ODBC-stuurprogramma correct is geïnstalleerd en dat LD_LIBRARY_PATH (Linux) / PATH (Windows) is ingesteld voor de campagneserver.

De fout **ODB-240000 ODBC:[Naam van Microsoft][ODBC Driver Manager]-gegevensbron niet gevonden en er is geen standaardstuurprogramma opgegeven.** treedt met Windows op als u een 16.X-stuurprogramma gebruikt. Adobe Campaign verwacht dat de teragegevens &#39;{teradata}&#39; worden genoemd in odbcinst.ini.
Als u een 18.10 Adobe Campaign-serverversie hebt, kunt u ODBCDriverName=&quot;Teradata Database ODBC Driver 16.10&quot; toevoegen in de opties van de externe account. Het versienummer kan veranderen, de nauwkeurige naam kan worden gevonden door odbcad32.exe in werking te stellen en tot de Drivers tabel toegang te hebben.
Voor versie onder 18.10 moet u het gedeelte Teradata van odbcinst.ini dat door de installatie van het stuurprogramma is gemaakt, kopiëren naar een nieuwe sectie met de naam Teradata. In dit geval kunt u dit gedeelte gebruiken.

Als uw basis in latin1 is, zult u APICharSize=1 in de opties moeten toevoegen.

### Tijdzone {#timezone}

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

## MySQL 5.7-configuratie {#mysql-57-configuration}

### Serverconfiguratie {#server-configuration-mysql}

Voor de serverconfiguratie zijn geen specifieke installatiestappen vereist. Adobe Campaign moet werken met een latin1-database, standaard met MySQL of een unicode-database.

### Installatie van stuurprogramma {#driver-installation-mysql}

#### Debian {#debian-mysql}

Download mysql-apt-config.deb van deze [pagina](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

De clientbibliotheek installeren:

```
$ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
$ apt update
$ apt install libmysqlclient20
```

#### Windows {#windows-mysql}

Download de C schakelaar van deze [pagina](https://dev.mysql.com/downloads/connector/c). We raden u aan versie 5.7 te downloaden.

Zorg ervoor dat de map die libmysqlclient.dll bevat, wordt toegevoegd aan de PATH-omgevingsvariabele die nlserver zal gebruiken.

#### CentOS {#centos-mysql}

Download mysql57-community-release.noarch.rpm van deze [pagina](https://dev.mysql.com/downloads/repo/yum).

De clientbibliotheek installeren:

$ Yum installeert mysql57-community-release-el7-9.noarch.rpm$ yum installeert mysql-community-libs

### Configuratie externe account {#external-account-mysql}

Voor de configuratie van de externe account zijn geen specifieke stappen vereist. Zorg ervoor dat de tijdzone en de Unicode-gegevens gebruiken zijn ingesteld op basis van uw database.
