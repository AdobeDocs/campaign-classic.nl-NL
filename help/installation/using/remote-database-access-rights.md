---
product: campaign
title: Machtigingen voor toegang tot een externe database
description: Toegangsrechten voor externe database
feature: Installation, Instance Settings, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 1%

---

# Toegangsrechten voor externe databases {#remote-database-access-rights}



Ten eerste, zodat de gebruiker bewerkingen kan uitvoeren op een externe database via FDA, moet de laatste een specifiek benoemd recht hebben in Adobe Campaign.

1. Selecteer de **[!UICONTROL Administration > Access Management > Named Rights]** in de Adobe Campaign Explorer.
1. Maak een nieuw recht door het gekozen label op te geven.
1. De **[!UICONTROL Name]** veld moet de volgende notatie hebben **gebruiker:base@server**, waarbij:

   * **user** komt overeen met de naam van de gebruiker in de externe database.
   * **basis** komt overeen met de naam van de externe database.
   * **server** komt overeen met de naam van de externe databaseserver.

     >[!NOTE]
     >
     >De **:base** onderdeel is optioneel in Oracle.

1. Sla de benoemde versie op en koppel deze aan de gekozen gebruiker in het menu **[!UICONTROL Administration > Access Management > Operators]** knooppunt van de Adobe Campaign Explorer.

Als u vervolgens de gegevens in een externe database wilt verwerken, moet de Adobe Campaign-gebruiker ten minste schrijfrechten voor de database hebben om werktabellen te kunnen maken. Deze worden automatisch verwijderd door Adobe Campaign.

In het algemeen zijn de volgende rechten noodzakelijk:

* **CONNECT**: verbinding met de externe database,
* **Gegevens LEZEN**: alleen-lezen toegang tot tabellen met klantgegevens,
* **&#39;MetaData&#39; lezen**: toegang tot de catalogi van servergegevens om de tabelstructuur te verkrijgen;
* **LADEN**: massa-belasting in werktafels (vereist bij het werken aan verzamelingen en verbindingen);
* **MAKEN/NEERZETTEN** for **TABEL/INDEX/PROCEDURE/FUNCTIE** (alleen voor werktabellen die door Adobe Campaign worden gegenereerd),
* **VERKLAREN** (aanbevolen): voor het toezicht op prestaties in geval van problemen,
* **Gegevens SCHRIJVEN** (afhankelijk van het integratiescenario).

De gegevensbestandbeheerder moet deze rechten met de rechten aanpassen specifiek voor elke gegevensbestandmotor. Raadpleeg de onderstaande sectie voor meer informatie.

## FDA-rechten {#fda-rights}

|   | Snowflake | Opnieuw | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Verbinding maken met externe database** | GEBRUIK OP WAREHOUSE, GEBRUIK OP DATABASE EN GEBRUIK OP SCHEMA-privileges | Een gebruiker maken die is gekoppeld aan de AWS-account | SESSIEBEVOEGDHEID MAKEN | machtiging CONNECT | CONNECT-bevoegdheid | Een gebruiker maken die is gekoppeld aan een externe host die ALLE PRIVILEGES heeft |
| **Tabellen maken** | TABEL MAKEN OP SCHEMA-voorrecht | BEVOEGDHEID MAKEN | TABELvoorrecht MAKEN | TABEL MAKEN, machtiging | BEVOEGDHEID MAKEN | BEVOEGDHEID MAKEN |
| **Indexen maken** | N.v.t. | BEVOEGDHEID MAKEN | INDEX OF CREEER OM HET EVEN WELKE INDEXBEVOEGDHEID | ALTER-machtiging | BEVOEGDHEID MAKEN | INDEX-bevoegdheid |
| **Functies maken** | FUNCTIE MAKEN VOOR SCHEMA-BEVOEGDHEID | GEBRUIK OP TAALvoorrecht om externe pythonuscripts aan te roepen | PROCEDURE MAKEN OF EEN PROCESBEVOEGDHEID MAKEN | FUNCTIE MAKEN, machtiging | GEBRUIKSRECHT | ROUTINE-bevoegdheden MAKEN |
| **Procedures maken** | N.v.t. | GEBRUIK OP TAALvoorrecht om externe pythonuscripts aan te roepen | PROCEDURE MAKEN OF EEN PROCESBEVOEGDHEID MAKEN | TOESTEMMING VOOR PROCEDURE MAKEN | USAGE-bevoegdheid (procedures zijn functies) | ROUTINE-bevoegdheden MAKEN |
| **Objecten verwijderen (tabellen, indexen, functies, procedures)** | Het object in eigendom hebben | Het object in eigendom of supergebruiker zijn | WILLEKEURIGE &lt;-object > bevoegdheid VERWIJDEREN | ALTER-machtiging | Tabel: eigenaar van tabel Index: eigenaar van index Functie: eigenaar van functie | DROP-voorrecht |
| **Uitvoeringen controleren** | BEVOEGDHEID MONITOR voor het vereiste object | Geen bevoegdheid vereist om de opdracht EXPLAIN te gebruiken | INSERT en SELECT privilege en vereiste bevoegdheid om de instructie uit te voeren waarvoor het EXPLAIN-PLAN is gebaseerd op | SHOWPLAN-machtiging | Geen bevoegdheid vereist om instructie EXPLAIN te gebruiken | SELECT, bevoegdheid |
| **Gegevens schrijven** | INSERT- en/of UPDATE-bevoegdheden (afhankelijk van schrijfbewerking) | Rechten INVOEGEN en BIJWERKEN | TABELrechten INVOEGEN en BIJWERKEN of INVOEGEN en BIJWERKEN | Machtigingen INVOEGEN en BIJWERKEN | Rechten INVOEGEN en BIJWERKEN | Rechten INVOEGEN en BIJWERKEN |
| **Gegevens in tabellen laden** | WERKGEBIED MAKEN OP SCHEMA, SELECTEREN en INVOEGEN in de rechten voor de doeltabel | SELECTEREN EN INVOEGEN, rechten | SELECTEREN EN INVOEGEN, rechten | BULKBEWERKINGEN INVOEGEN, BEHEREN en TABELmachtigingen WIJZIGEN | SELECTEREN EN INVOEGEN, rechten | Bestandsrechten |
| **Toegang tot clientgegevens** | SELECTEREN OP (TOEKOMSTIGE) TABLE(S)- OF WEERGAVEBEVOEGDHEDEN | SELECT, bevoegdheid | SELECTEER OF SELECTEER EEN TABELBEHEER | machtiging SELECTEREN | SELECT, bevoegdheid | SELECT, bevoegdheid |
| **Toegang tot metagegevens** | SELECTEER INFORMATIE_SCHEMA-SCHEMA-voorrecht | SELECT, bevoegdheid | Geen bevoegdheid vereist voor gebruik van DESCRIBE-instructie | machtiging DEFINITIE WEERGEVEN | Geen bevoegdheid vereist voor het gebruik van de opdracht &quot;\d table&quot; | SELECT, bevoegdheid |

|   | DB2 UDB | Teradata | InfiniDB | Sybase IQ/Sybase ASE | Netezza | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Verbinding maken met externe database** | CONNECT-autoriteit | CONNECT-bevoegdheid | Een gebruiker maken die is gekoppeld aan een externe host die ALLE PRIVILEGES heeft | Geen toestemming vereist om de instructie CONNECT te gebruiken | Geen bevoegdheid vereist | CONNECT-bevoegdheid |
| **Tabellen maken** | CREATETAB-instantie | CREATE TABLE or TABLE, trefwoord | BEVOEGDHEID MAKEN | RESOURCE Authority en CREATE permission | TABLE-bevoegdheid | BEVOEGDHEID MAKEN |
| **Indexen maken** | INDEX-bevoegdheid | INDEX- of INDEX-trefwoord MAKEN | INDEX-bevoegdheid | RESOURCE Authority en CREATE permission | INDEX-bevoegdheid | BEVOEGDHEID MAKEN |
| **Functies maken** | IMPLICIT_SCHEMA-autoriteit of CREATEIN-voorrecht | trefwoord FUNCTIE OF FUNCTIE MAKEN | ROUTINE-bevoegdheden MAKEN | RESOURCE-instantie of DBA-instantie voor Java-functies | FUNCTIE, voorrecht | FUNCTIE-bevoegdheden MAKEN |
| **Procedures maken** | IMPLICIT_SCHEMA-autoriteit of CREATEIN-voorrecht | PROCEDURE OF PROCEStrefwoord MAKEN | ROUTINE-bevoegdheden MAKEN | BRONNEN | PROCESBEVOEGDHEID | FUNCTIE-bevoegdheden MAKEN |
| **Objecten verwijderen (tabellen, indexen, functies, procedures)** | DROPIN-bevoegdheid of -BEHEER of -bevoegdheid voor het bezit van het object | DROP &lt; object > of objectgerelateerd trefwoord | DROP-voorrecht | Eigenaar van het object of de DBA-instantie | DROP-voorrecht | Het object in eigendom hebben |
| **Uitvoeringen controleren** | EXPLAIN-instantie | Geen bevoegdheid vereist om instructie EXPLAIN te gebruiken | SELECT, bevoegdheid | Alleen een systeembeheerder kan sp_showplan uitvoeren | Geen bevoegdheid vereist om instructie EXPLAIN te gebruiken | Geen bevoegdheid vereist om instructie EXPLAIN te gebruiken |
| **Gegevens schrijven** | Rechten of DATAACCESS-instantie INVOEGEN en bijwerken | Rechten INVOEGEN en BIJWERKEN | Rechten INVOEGEN en BIJWERKEN | Machtigingen INVOEGEN en BIJWERKEN | Rechten INVOEGEN en BIJWERKEN | Rechten INVOEGEN en BIJWERKEN |
| **Gegevens in tabellen laden** | LAADINSTANTIE | U kunt privileges SELECTEREN en INVOEGEN om respectievelijk KOPIËREN NAAR en KOPIËREN UIT instructies te gebruiken | Bestandsrechten | Ben de eigenaar van de lijst of ALTER toestemming. Afhankelijk van - gl optie, zou de LIJST van de Lading slechts kunnen worden uitgevoerd als de gebruiker de gezag DBA heeft | SELECTEREN EN INVOEGEN, rechten | SELECTEREN EN INVOEGEN, rechten |
| **Toegang tot clientgegevens** | Rechten of DATAACCESS-instantie INVOEGEN/BIJWERKEN | SELECT, bevoegdheid | SELECT, bevoegdheid | machtiging SELECTEREN | SELECT, bevoegdheid | SELECT, bevoegdheid |
| **Toegang tot metagegevens** | Geen toestemming vereist om de verklaring van DESCRIBE te gebruiken | Toon bevoegdheid | SELECT, bevoegdheid | Geen toestemming vereist om de instructie DESCRIBE te gebruiken | Geen bevoegdheid vereist voor het gebruik van de opdracht &quot;\d table&quot; | Geen bevoegdheid vereist om SHOW-opdracht te gebruiken |
