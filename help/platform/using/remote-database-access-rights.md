---
title: Een externe database openen
seo-title: Een externe database openen
description: Een externe database openen
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ae44e38e9d05478e8ebfacb1e063cdfd5d7ff30c

---


# Toegangsrechten externe database {#remote-database-access-rights}

Ten eerste, zodat de gebruiker bewerkingen kan uitvoeren op een externe database via FDA, moet de gebruiker een specifiek benoemd recht hebben in Adobe Campaign.

1. Selecteer het **[!UICONTROL Administration > Access Management > Named Rights]** knooppunt in de Adobe Campaign Explorer.
1. Maak een nieuw recht door het gekozen label op te geven.
1. Het **[!UICONTROL Name]** veld moet de volgende **indelingsgebruiker hebben:base@server**, waarbij:

   * **gebruiker** komt overeen met de naam van de gebruiker in de externe database.
   * **de basis** komt overeen met de naam van de externe database.
   * **server** komt overeen met de naam van de externe databaseserver.

      >[!NOTE]
      >
      >Het **:base** -onderdeel is optioneel in Oracle.

1. Sla het benoemde recht op en koppel het aan de door u gekozen gebruiker vanuit het **[!UICONTROL Administration > Access Management > Operators]** knooppunt van de Adobe Campagneverkenner.

Als u vervolgens de gegevens in een externe database wilt verwerken, moet de Adobe Campagnegebruiker ten minste schrijfrechten voor de database hebben om werktabellen te kunnen maken. Deze worden automatisch verwijderd door Adobe Campaign.

In het algemeen zijn de volgende rechten noodzakelijk:

* **VERBINDING**: verbinding met de externe database,
* **LEESgegevens**: alleen-lezen toegang tot tabellen met klantgegevens,
* **&#39;MetaData&#39;** LEZEN: toegang tot de catalogi van servergegevens om de tabelstructuur te verkrijgen;
* **LADEN**: massabelasting in werktafels (vereist bij het werken aan verzamelingen en verbindingen);
* **CREATE/DROP** for **TABLE/INDEX/PROCEDURE/FUNCTION**,
* **EXPLAIN** (aanbevolen): voor het toezicht op prestaties in geval van problemen;
* **SCHRIJF Gegevens** (afhankelijk van het integratiescenario).

>[!NOTE]
>
>De gegevensbestandbeheerder moet deze rechten met de rechten aanpassen specifiek voor elke gegevensbestandmotor. Raadpleeg de specifieke rechten [van](https://docs.adobe.com/content/help/en/campaign-classic/using/assets/fda_rdbms_rights.pdf)RDBMS voor meer informatie.