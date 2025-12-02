---
product: campaign
title: Machtigingen voor toegang tot een externe database
description: Toegangsrechten voor externe database
feature: Installation, Instance Settings, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 0%

---

# Toegangsrechten externe database {#remote-database-access-rights}



Ten eerste, zodat de gebruiker bewerkingen kan uitvoeren op een externe database via FDA, moet de laatste een specifiek benoemd recht hebben in Adobe Campaign.

1. Selecteer het knooppunt **[!UICONTROL Administration > Access Management > Named Rights]** in de Adobe Campaign Explorer.
1. Maak een nieuw recht door het gekozen label op te geven.
1. Het **[!UICONTROL Name]** gebied moet het volgende formaat **gebruiker :base@server** nemen, waar:

   * **gebruiker** beantwoordt met de naam van de gebruiker in het externe gegevensbestand.
   * **basis** beantwoordt met de naam van het externe gegevensbestand.
   * **server** beantwoordt met de naam van de externe gegevensbestandserver.

     >[!NOTE]
     >
     >Het **:base** -onderdeel is optioneel in Oracle.

1. Sla het benoemde recht op en koppel het aan de gekozen gebruiker vanuit het knooppunt **[!UICONTROL Administration > Access Management > Operators]** van de Adobe Campaign Explorer.

Als u vervolgens de gegevens in een externe database wilt verwerken, moet de Adobe Campaign-gebruiker ten minste schrijfrechten voor de database hebben om werktabellen te kunnen maken. Deze worden automatisch verwijderd door Adobe Campaign.

In het algemeen zijn de volgende rechten noodzakelijk:

* **CONNECT**: verbinding aan het verre gegevensbestand,
* **LEZEN Gegevens**: read-only toegang tot lijsten die klantengegevens bevatten,
* **LEZEN &quot;MetaData&quot;**: toegang tot de catalogi van servergegevens om de lijststructuur te verkrijgen,
* **LAST**: massa die in het werklijsten laadt (wanneer het werken aan inzamelingen en verbindingen) wordt vereist,
* **CREATE/DROP** voor **LIJST/INDEX/PROCEDURE/FUNCTIE** (slechts voor werktabellen die door Adobe Campaign worden geproduceerd),
* **VERKLARING** (geadviseerd): voor het controleren van prestaties in het geval van problemen,
* **SCHRIJF Gegevens** (afhankelijk van het integratiescenario).

De gegevensbestandbeheerder moet deze rechten met de rechten aanpassen specifiek voor elke gegevensbestandmotor. Raadpleeg de onderstaande sectie voor meer informatie.

## FDA-rechten {#fda-rights}

|   | Snowflake | Opnieuw | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Verbindend met ver gegevensbestand** | GEBRUIK OP WAREHOUSE, GEBRUIK OP DATABASE EN GEBRUIK OP SCHEMA-privileges | Een gebruiker maken die is gekoppeld aan de AWS-account | SESSIEBEVOEGDHEID MAKEN | CONNECT-machtiging | CONNECT-bevoegdheid | Een gebruiker maken die is gekoppeld aan een externe host die ALLE PRIVILEGES heeft |
| **Creërend lijsten** | TABEL MAKEN OP SCHEMA-voorrecht | BEVOEGDHEID MAKEN | TABELvoorrecht MAKEN | TABEL MAKEN, machtiging | BEVOEGDHEID MAKEN | BEVOEGDHEID MAKEN |
| **Creërend indexen** | N.v.t. | BEVOEGDHEID MAKEN | INDEX OF CREEER OM HET EVEN WELKE INDEXBEVOEGDHEID | ALTER-machtiging | BEVOEGDHEID MAKEN | INDEX-bevoegdheid |
| **Creërend functies** | FUNCTIE MAKEN VOOR SCHEMA-BEVOEGDHEID | GEBRUIK OP TAALvoorrecht om externe pythonuscripts aan te roepen | PROCEDURE MAKEN OF EEN PROCESBEVOEGDHEID MAKEN | FUNCTIE MAKEN, machtiging | GEBRUIKSRECHT | ROUTINE-bevoegdheden MAKEN |
| **Creërend procedures** | N.v.t. | GEBRUIK OP TAALvoorrecht om externe pythonuscripts aan te roepen | PROCEDURE MAKEN OF EEN PROCESBEVOEGDHEID MAKEN | TOESTEMMING VOOR PROCEDURE MAKEN | USAGE-bevoegdheid (procedures zijn functies) | ROUTINE-bevoegdheden MAKEN |
| **het Verwijderen van voorwerpen (lijsten, indexen, functies, procedures)** | Het object in eigendom hebben | Het object in eigendom of supergebruiker zijn | WILLEKEURIGE &lt;-object > bevoegdheid VERWIJDEREN | ALTER-machtiging | Tabel: eigenaar van tabel Index: eigenaar van index Functie: eigenaar van functie | DROP-voorrecht |
| **de uitvoeringen van de Controle** | BEVOEGDHEID MONITOR voor het vereiste object | Geen bevoegdheid vereist om de opdracht EXPLAIN te gebruiken | INSERT en SELECT privilege en vereiste bevoegdheid om de instructie uit te voeren waarvoor het EXPLAIN-PLAN is gebaseerd op | SHOWPLAN-machtiging | Geen bevoegdheid vereist om instructie EXPLAIN te gebruiken | SELECT, bevoegdheid |
| **het Schrijven gegevens** | INSERT- en/of UPDATE-bevoegdheden (afhankelijk van schrijfbewerking) | Rechten INVOEGEN en BIJWERKEN | TABELrechten INVOEGEN en BIJWERKEN of INVOEGEN en BIJWERKEN | Machtigingen INVOEGEN en BIJWERKEN | Rechten INVOEGEN en BIJWERKEN | Rechten INVOEGEN en BIJWERKEN |
| **Ladende gegevens in lijsten** | WERKGEBIED MAKEN OP SCHEMA, SELECTEREN en INVOEGEN in de rechten voor de doeltabel | SELECTEREN EN INVOEGEN, rechten | SELECTEREN EN INVOEGEN, rechten | BULKBEWERKINGEN INVOEGEN, BEHEREN en TABELmachtigingen WIJZIGEN | SELECTEREN EN INVOEGEN, rechten | Bestandsrechten |
| **Toegang tot cliëntgegevens** | SELECTEREN OP (TOEKOMSTIGE) TABLE(S)- OF WEERGAVEBEVOEGDHEDEN | SELECT, bevoegdheid | SELECTEER OF SELECTEER EEN TABELBEHEER | machtiging SELECTEREN | SELECT, bevoegdheid | SELECT, bevoegdheid |
| **Toegang tot meta-gegevens** | SELECTEER INFORMATIE_SCHEMA-SCHEMA-voorrecht | SELECT, bevoegdheid | Geen bevoegdheid vereist voor gebruik van DESCRIBE-instructie | machtiging DEFINITIE WEERGEVEN | Geen bevoegdheid vereist voor het gebruik van de opdracht &quot;\d table&quot; | SELECT, bevoegdheid |

|   | Teradata | InfiniDB | Sybase IQ/Sybase ASE | Netezza | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|
| **Verbindend met ver gegevensbestand** | CONNECT-bevoegdheid | Een gebruiker maken die is gekoppeld aan een externe host die ALLE PRIVILEGES heeft | Geen toestemming vereist om de CONNECT-instructie te gebruiken | Geen bevoegdheid vereist | CONNECT-bevoegdheid |
| **Creërend lijsten** | CREATE TABLE or TABLE, trefwoord | BEVOEGDHEID MAKEN | RESOURCE Authority en CREATE permission | TABLE-bevoegdheid | BEVOEGDHEID MAKEN |
| **Creërend indexen** | INDEX- of INDEX-trefwoord MAKEN | INDEX-bevoegdheid | RESOURCE Authority en CREATE permission | INDEX-bevoegdheid | BEVOEGDHEID MAKEN |
| **Creërend functies** | trefwoord FUNCTIE OF FUNCTIE MAKEN | ROUTINE-bevoegdheden MAKEN | RESOURCE-instantie of DBA-instantie voor Java-functies | FUNCTIE, voorrecht | FUNCTIE-bevoegdheden MAKEN |
| **Creërend procedures** | PROCEDURE OF PROCEStrefwoord MAKEN | ROUTINE-bevoegdheden MAKEN | BRONNEN | PROCESBEVOEGDHEID | FUNCTIE-bevoegdheden MAKEN |
| **het Verwijderen van voorwerpen (lijsten, indexen, functies, procedures)** | DROP &lt; object > of objectgerelateerd trefwoord | DROP-voorrecht | Eigenaar van het object of de DBA-instantie | DROP-voorrecht | Het object in eigendom hebben |
| **de uitvoeringen van de Controle** | Geen bevoegdheid vereist om instructie EXPLAIN te gebruiken | SELECT, bevoegdheid | Alleen een systeembeheerder kan sp_showplan uitvoeren | Geen bevoegdheid vereist om instructie EXPLAIN te gebruiken | Geen bevoegdheid vereist om instructie EXPLAIN te gebruiken |
| **het Schrijven gegevens** | Rechten INVOEGEN en BIJWERKEN | Rechten INVOEGEN en BIJWERKEN | Machtigingen INVOEGEN en BIJWERKEN | Rechten INVOEGEN en BIJWERKEN | Rechten INVOEGEN en BIJWERKEN |
| **Ladende gegevens in lijsten** | U kunt privileges SELECTEREN en INVOEGEN om respectievelijk KOPIËREN NAAR en KOPIËREN UIT instructies te gebruiken | Bestandsrechten | Ben de eigenaar van de lijst of ALTER toestemming. Afhankelijk van - gl optie, zou de LIJST van de Lading slechts kunnen worden uitgevoerd als de gebruiker de gezag DBA heeft | SELECTEREN EN INVOEGEN, rechten | SELECTEREN EN INVOEGEN, rechten |
| **Toegang tot cliëntgegevens** | SELECT, bevoegdheid | machtiging SELECTEREN | SELECT, bevoegdheid | SELECT, bevoegdheid |  |
| **Toegang tot meta-gegevens** | Toon bevoegdheid | SELECT, bevoegdheid | Geen toestemming vereist om de instructie DESCRIBE te gebruiken | Geen bevoegdheid vereist voor het gebruik van de opdracht &quot;\d table&quot; | Geen bevoegdheid vereist om SHOW-opdracht te gebruiken |
