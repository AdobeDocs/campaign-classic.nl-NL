---
title: Overschakelen naar Unicode
seo-title: Overschakelen naar Unicode
description: Overschakelen naar Unicode
seo-description: null
page-status-flag: never-activated
uuid: 5f15b285-7377-453a-aa98-ca4cf14a4c80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 0f5399a8-860d-4a1b-86a9-9011b973346b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Overschakelen naar Unicode{#switching-to-unicode}

Voor een bestaande **prod** -instantie in Linux/PostgreSQL zijn de stappen voor het schakelen naar unicode als volgt:

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

   Voeg het **uu** -teken toe vóór de waarde met betrekking tot de database-id (**databaseId**):

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

1. Bevestig de schakelaar. U doet dit door verbinding te maken via de Adobe Campaign-console en:

   * controleert u of de gegevens correct worden weergegeven, met name de tekens met accent:
   * start een levering en controleer of de opzoekfunctie voor bijhouden werkt.

