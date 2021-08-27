---
product: campaign
title: Overschakelen naar Unicode
description: Overschakelen naar Unicode
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 7%

---

# Overschakelen naar Unicode{#switching-to-unicode}

![](../../assets/v7-only.svg)

Voor een bestaande **prod** instantie in Linux/PostgreSQL, zijn de stappen voor omschakeling aan unicode als volgt:

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

   Voeg het **u** karakter vóór de waarde met betrekking tot het gegevensbestandherkenningsteken (**databaseId**) toe:

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

1. Alle computers opnieuw opstarten:

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Bevestig de schakelaar. Hiervoor maakt u verbinding via de Adobe Campaign-console en:

   * controleert u of de gegevens correct worden weergegeven, met name de tekens met accent:
   * start een levering en controleer of de opzoekfunctie voor bijhouden werkt.
