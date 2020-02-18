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
source-git-commit: 4969c5e56f1911b3abfd770ca4f8f5ed25784a52

---


# Verbinding maken met de database {#connecting-to-the-database}

Als u een verbinding met de externe database wilt inschakelen, moet u de verbindingsparameters aangeven, dat wil zeggen de doelgegevensbron en de naam van de tabel met gegevens die moeten worden geladen.

>[!CAUTION]
>
>De gebruiker van de Campagne van Adobe heeft specifieke rechten voor het externe gegevensbestand en de de toepassingsserver van de Campagne van Adobe nodig om gegevens van een externe gegevensbestand te verwerken. Voor meer op dit, verwijs naar de [Verre sectie van de de toegangsrechten](#remote-database-access-rights) van het gegevensbestandtoegang.
>
>Om storingen te voorkomen, moeten operatoren die toegang krijgen tot externe, gedeelde gegevens werken vanuit aparte ruimten.

## Een gedeelde verbinding maken {#creating-a-shared-connection}

Als u een verbinding met een gedeelde externe database wilt inschakelen, zolang deze verbinding actief is, kunt u de database openen via Adobe Campaign.

1. De configuratie moet vooraf via de **[!UICONTROL Administration > Platform > External accounts]** knoop worden bepaald.
1. Klik op de **[!UICONTROL New]** knop en selecteer het **[!UICONTROL External database]** type.
1. Definieer de **[!UICONTROL Connection]** parameters van de externe database.

   Voor verbindingen met een **ODBC** typedatabase moet het **[!UICONTROL Server]** veld de naam van de ODBC-gegevensbron bevatten en niet de servernaam. Bovendien kunnen bepaalde aanvullende configuraties noodzakelijk zijn, afhankelijk van de gebruikte databanken. Raadpleeg de sectie [Specifieke configuraties per databasetype](#specific-configurations-by-database-type) .

1. Nadat de parameters zijn ingevoerd, klikt u op de **[!UICONTROL Test the connection]** knop om deze goed te keuren.

   ![](assets/wf-external-account-create.png)

1. Schakel indien nodig de **[!UICONTROL Enabled]** optie uit om toegang tot deze database uit te schakelen zonder de configuratie ervan te verwijderen.
1. Als u Adobe Campaign toegang wilt geven tot deze database, moet u de SQL-functies implementeren. Klik op het **[!UICONTROL Parameters]** tabblad en vervolgens op de **[!UICONTROL Deploy functions]** knop.

   ![](assets/wf-external-account-functions.png)

U kunt specifieke werktabelruimten definiëren voor de tabellen en voor de index op het **[!UICONTROL Parameters]** tabblad.

## Tijdelijke verbinding maken {#creating-a-temporary-connection}

U kunt rechtstreeks vanuit workflowactiviteiten een verbinding met een externe database definiëren. In dit geval bevindt het bestand zich in een lokale externe database die is gereserveerd voor gebruik in een huidige workflow: het wordt niet opgeslagen op de externe accounts. Dit type punctuele verbinding kan op verschillende activiteiten van het werkschema worden tot stand gebracht, met name de **[!UICONTROL Query]**, de **[!UICONTROL Data loading (RDBMS)]**, de **[!UICONTROL Enrichment]** activiteit of de **[!UICONTROL Split]** activiteit.

>[!CAUTION]
>
>Dit type configuratie wordt niet aanbevolen, maar kan periodiek worden gebruikt om gegevens te verzamelen. Desalniettemin moet u een externe account maken, zoals wordt weergegeven in de sectie [Een gedeelde verbinding](#creating-a-shared-connection) maken.

In de queryactiviteit ziet u bijvoorbeeld de volgende stappen voor het maken van een periodieke verbinding met een externe database:

1. Klik op de knop **[!UICONTROL Add data...]** en selecteer de **[!UICONTROL External data]** opties.
1. Selecteer de **[!UICONTROL Locally defining the data source]** optie.

   ![](assets/wf_add_data_local_external_data.png)

1. Selecteer de doeldatabase-engine in de vervolgkeuzelijst. Voer de naam van de server in en geef de verificatieparameters op.

   Geef ook de naam van de externe database op.

   ![](assets/wf_add_data_local_external_data_param.png)

   Klik op de **[!UICONTROL Next]** knop.

1. Selecteer de tabel waarin de gegevens zijn opgeslagen.

   U kunt de naam van de tabel rechtstreeks in het desbetreffende veld invoeren of op het pictogram Bewerken klikken om de lijst met databasetabellen te openen.

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. Klik op de **[!UICONTROL Add]** knop om een of meerdere afstemmingsvelden te definiëren tussen de externe databasegegevens en de gegevens in de Adobe Campagne-database. De **[!UICONTROL Edit expression]** pictogrammen van de tabel **[!UICONTROL Remote field]** en **[!UICONTROL Local field]** bieden u toegang tot de lijst met velden van elk van de tabellen.

   ![](assets/wf_add_data_local_external_data_join.png)

1. Geef zo nodig een filtervoorwaarde en de gegevenssorteermodus op.
1. Selecteer de aanvullende gegevens die in de externe database moeten worden verzameld. Dubbelklik hiertoe op de velden die u wilt toevoegen om deze weer te geven in het **[!UICONTROL Output columns]** deelvenster.

   ![](assets/wf_add_data_local_external_data_select.png)

   Klik **[!UICONTROL Finish]** om deze configuratie te bevestigen.

## Beveiligde verbinding {#secure-connection}

>[!NOTE]
>
>Beveiligde verbinding is alleen beschikbaar voor PostSQL.

U kunt toegang tot een extern gegevensbestand beveiligen wanneer het vormen van een externe rekening FDA.

Hiervoor voegt u &quot;**:ssl**&quot; toe na het serveradres en het adres van de gebruikte poort. Bijvoorbeeld: **192.168.0.52:4501:ssl**.

De gegevens worden vervolgens verzonden via het veilige SSL-protocol.

## Aanvullende configuraties {#additional-configurations}

Indien nodig, kunt u het schema voor de verwerking van gegevens in een extern gegevensbestand tot stand brengen. Op dezelfde manier kunt u in Adobe Campaign toewijzingen definiëren voor de gegevens in een externe tabel. Deze configuraties zijn algemeen en zijn niet uitsluitend van toepassing op workflows.

>[!NOTE]
>
>Raadpleeg [deze pagina](../../configuration/using/about-schema-edition.md)voor meer informatie over het maken van schema&#39;s in Adobe Campaign en het definiëren van een nieuwe gegevenstoewijzing.