---
product: campaign
title: FDA-connectors configureren
description: Meer informatie over configuratiestappen voor FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 2%

---

# FDA-connectors configureren {#specific-configurations-by-database-type}



Afhankelijk van de externe databases die u vanuit Adobe Campaign wilt kunnen openen, moet u bepaalde specifieke configuraties uitvoeren. Bij deze configuraties worden vooral stuurprogramma&#39;s geïnstalleerd en worden omgevingsvariabelen opgegeven die bij elke RDBMS op de Adobe Campaign-server horen.

Als algemene regel geldt dat u de corresponderende clientlaag op de externe database op de Adobe Campaign-server moet installeren.

>[!NOTE]
>
>De compatibele versies zijn vermeld in [ de Matrijs van de Verenigbaarheid van de Campagne ](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
>

## Configuratiestappen {#fda-configuration-steps}

Om toegang tot een extern gegevensbestand met FDA te plaatsen, zijn de configuratiestappen:

1. Installeer de stuurprogramma&#39;s en stel de externe account in die overeenkomt met uw database op de Adobe Campaign-server. Verwijs naar de gegevensbestand-specifieke hieronder vermelde pagina&#39;s [ ](#fda-specific-configuration)
1. Test de externe account of maak een tijdelijke verbinding tussen Adobe Campaign en de externe database. [Meer informatie](../../installation/using/connecting-to-database.md)
1. Maak het schema van de externe database in Adobe Campaign. Hierdoor kunt u de gegevensstructuur van de externe database identificeren. [Meer informatie](../../installation/using/creating-data-schema.md)
1. Indien nodig, creeer een nieuwe doelafbeelding van het eerder gecreeerd schema. Dit is vereist als de ontvangers van uw leveringen afkomstig zijn uit de externe database. Deze implementatie omvat beperkingen met betrekking tot berichtpersonalisatie. [Meer informatie](../../installation/using/defining-data-mapping.md)

Zodra het gegevensschema wordt gecreeerd, kunnen de gegevens in de werkschema&#39;s van Adobe Campaign worden verwerkt. Verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html){target="_blank"}.

## Databasespecifieke configuratie {#fda-specific-configuration}

Afhankelijk van de externe databases die u vanuit Adobe Campaign wilt kunnen openen, moet u bepaalde specifieke configuraties uitvoeren. Deze configuraties omvatten hoofdzakelijk het installeren van bestuurders en het verklaren van milieuvariabelen die tot elke RDBMS op de server van Adobe Campaign behoren, en het vormen van de externe rekening.

Volg de onderstaande koppelingen voor meer informatie:

* Verbind Campagne en [ Amazon Redshift ](../../installation/using/configure-fda-redshift.md)
* Verbind Campagne en [ Azure Synapse ](../../installation/using/configure-fda-synapse.md)
* Verbind Campagne en [ Google BigQuery ](../../installation/using/configure-fda-google-big-query.md)
* Verbind Campagne en [ Hadoop ](../../installation/using/configure-fda-hadoop.md)
* Verbind Campagne en [ de Server van Microsoft SQL ](../../installation/using/configure-fda-sql.md)
* Verbind Campagne en [ Netezza ](../../installation/using/configure-fda-netezza.md)
* Verbind Campagne en [ Oracle ](../../installation/using/configure-fda-oracle.md)
* Verbind Campagne en [ PostgreSQL ](../../installation/using/configure-fda-postgresql.md)
* Verbind Campagne en [ SAP HANA ](../../installation/using/configure-fda-sap-hana.md)
* Verbind Campagne en [ Snowflake ](../../installation/using/configure-fda-snowflake.md)
* Verbind Campagne en [ Sybase IQ ](../../installation/using/configure-fda-sybase.md)
* Verbind Campagne en [ Teradata ](../../installation/using/configure-fda-teradata.md)
* Verbind Campagne en [ Vertica Analytics ](../../installation/using/configure-fda-vertica.md)
