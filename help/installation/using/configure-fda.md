---
product: campaign
title: FDA-connectors configureren
description: Meer informatie over configuratiestappen voor FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: 11de485a97d112b308c145775537d9b6255f124f
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 5%

---

# FDA-connectoren configureren {#specific-configurations-by-database-type}

Afhankelijk van de externe databases die u vanuit Adobe Campaign wilt kunnen openen, moet u bepaalde specifieke configuraties uitvoeren. Bij deze configuraties worden vooral stuurprogramma&#39;s geïnstalleerd en worden omgevingsvariabelen opgegeven die bij elke RDBMS op de Adobe Campaign-server horen.

Als algemene regel geldt dat u de corresponderende clientlaag op de externe database op de Adobe Campaign-server moet installeren.

>[!NOTE]
>
>De compatibele versies zijn vermeld in [Matrix van de Verenigbaarheid van de Campagne](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).


## Configuratiestappen {#fda-configuration-steps}

Om toegang tot een extern gegevensbestand met FDA te plaatsen, zijn de configuratiestappen:

1. Installeer de stuurprogramma&#39;s en stel de externe account in die overeenkomt met uw database op de Adobe Campaign-server. Verwijs naar de gegevensbestand-specifieke pagina [hieronder vermeld ](#fda-specific-configuration)
1. Test de externe account of maak een tijdelijke verbinding tussen Adobe Campaign en de externe database. [Meer informatie](../../installation/using/connecting-to-database.md)
1. Maak het schema van de externe database in Adobe Campaign. Hierdoor kunt u de gegevensstructuur van de externe database identificeren. [Meer informatie](../../installation/using/creating-data-schema.md)
1. Indien nodig, creeer een nieuwe doelafbeelding van het eerder gecreeerd schema. Dit is vereist als de ontvangers van uw leveringen afkomstig zijn uit de externe database. Deze implementatie omvat beperkingen met betrekking tot berichtpersonalisatie. [Meer informatie](../../installation/using/defining-data-mapping.md)

Zodra het gegevensschema wordt gecreeerd, kunnen de gegevens in de werkschema&#39;s van Adobe Campaign worden verwerkt. Raadpleeg [deze sectie](../../workflow/using/accessing-an-external-database--fda-.md) voor meer informatie.

## Databasespecifieke configuratie {#fda-specific-configuration}

Afhankelijk van de externe databases die u vanuit Adobe Campaign wilt kunnen openen, moet u bepaalde specifieke configuraties uitvoeren. Deze configuraties omvatten hoofdzakelijk het installeren van bestuurders en het verklaren van milieuvariabelen die tot elke RDBMS op de server van Adobe Campaign behoren, en het vormen van de externe rekening.

Volg de onderstaande koppelingen voor meer informatie:

* Campagne verbinden en [Vertica](../../installation/using/configure-fda-vertica.md)

* Campagne voor Connect en [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)

* Campagne verbinden en [Azure synapse](../../installation/using/configure-fda-synapse.md)

* Campagne verbinden en [Snowflake](../../installation/using/configure-fda-snowflake.md)

* Campagne verbinden en [Hadoop](../../installation/using/configure-fda-hadoop.md)

* Campagne verbinden en [Oracle](../../installation/using/configure-fda-oracle.md)

* Campagne verbinden en [Netezza](../../installation/using/configure-fda-netezza.md)

* Campagne verbinden en [Sybase IQ](../../installation/using/configure-fda-sybase.md)

* Campagne verbinden en [Teradata](../../installation/using/configure-fda-teradata.md)

* Campagne verbinden en [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
