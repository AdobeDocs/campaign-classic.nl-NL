---
product: campaign
title: Overschakelen naar Unicode
description: Overschakelen naar Unicode
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 13%

---

# Overschakelen naar Unicode{#switching-to-unicode}



Voor bestaande **prod** In Linux/PostgreSQL zijn de stappen voor het schakelen naar unicode als volgt:

1. Stop de processen die naar de database schrijven:

   ```
   su - neolane
   nlserver shutdown
   ```

1. Database dumpen:

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. Een Unicode-database maken:

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. De database herstellen:

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. Werk de optie bij die aangeeft dat de database Unicode is:

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. Op de volgende servers:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Voeg de **u** vóór de waarde met betrekking tot de database-id (**databaseId**):

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. Op servers die de database oproepen:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Wijzig de databasereferentie:

   ```
   <dataSource name="default">
    <dbcnx encrypted="1" 
    login="<dbuser>:<base_unicode>" password="xxxx="
    provider="postgresql" server="yyyy"/>
   </dataSource>
   ```

1. Start alle computers opnieuw op:

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Bevestig de schakelaar. Maak hiervoor verbinding via de Adobe Campaign-console en:

   * controleren of de gegevens correct worden weergegeven, met name de tekens waarvoor de accentuatie is toegestaan:
   * start een levering en controleer of de opzoekfunctie voor bijhouden werkt.
