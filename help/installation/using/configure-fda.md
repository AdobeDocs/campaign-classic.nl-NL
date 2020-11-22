---
solution: Campaign Classic
product: campaign
title: FDA-connectors configureren
description: Meer informatie over configuratiestappen voor FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---


# FDA-connectoren configureren {#specific-configurations-by-database-type}

Afhankelijk van de externe databases die u vanuit Adobe Campaign wilt kunnen openen, moet u bepaalde specifieke configuraties uitvoeren. Bij deze configuraties worden vooral stuurprogramma&#39;s geïnstalleerd en worden omgevingsvariabelen opgegeven die bij elke RDBMS op de Adobe Campaign-server horen.

Als algemene regel geldt dat u de corresponderende clientlaag op de externe database op de Adobe Campaign-server moet installeren.

>[!NOTE]
>
>Compatibele versies worden vermeld in de Matrix [van de Verenigbaarheid van de](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)Campagne.


## Configuratiestappen {#fda-configuration-steps}

Om toegang tot een extern gegevensbestand met FDA te plaatsen, zijn de configuratiestappen:

1. Installeer de stuurprogramma&#39;s die overeenkomen met uw database op de Adobe Campaign-server. Drivers worden vermeld in de database-specifieke pagina&#39;s [hieronder](#fda-specific-configuration).
1. [Maak en configureer een externe account](../../installation/using/connecting-to-database.md) waarmee u de verbinding tussen Adobe Campaign en de externe database tot stand kunt brengen. Raadpleeg [deze pagina](../../installation/using/external-accounts.md)voor meer informatie over externe accounts in de campagne.
1. [Maak het schema](../../installation/using/creating-data-schema.md) van de externe database in Adobe Campaign. Hierdoor kunt u de gegevensstructuur van de externe database herkennen.
1. Indien nodig, [creeer een nieuwe doelafbeelding](../../installation/using/defining-data-mapping.md) van het eerder gecreeerd schema. Dit is vereist als de ontvangers van uw leveringen afkomstig zijn uit de externe database. Deze implementatie omvat beperkingen met betrekking tot berichtpersonalisatie.

Zodra het gegevensschema wordt gecreeerd, kunnen de gegevens in de werkschema&#39;s van Adobe Campaign worden verwerkt. Raadpleeg [deze sectie](../../workflow/using/accessing-an-external-database--fda-.md) voor meer informatie.

## Databasespecifieke configuratie {#fda-specific-configuration}

Afhankelijk van de externe databases die u vanuit Adobe Campaign wilt kunnen openen, moet u bepaalde specifieke configuraties uitvoeren. Bij deze configuraties worden vooral stuurprogramma&#39;s geïnstalleerd en worden omgevingsvariabelen opgegeven die bij elke RDBMS op de Adobe Campaign-server horen.

Volg de onderstaande koppelingen voor meer informatie:

* [azure synapse](../../installation/using/configure-fda-synapse.md)

* [Snowflake](../../installation/using/configure-fda-snowflake.md)

* [Hadoop](../../installation/using/configure-fda-hadoop.md)

* [Oracle](../../installation/using/configure-fda-oracle.md)

* [Netezza](../../installation/using/configure-fda-netezza.md)

* [sybase IQ](../../installation/using/configure-fda-sybase.md)

* [Teradata](../../installation/using/configure-fda-teradata.md)

* [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
