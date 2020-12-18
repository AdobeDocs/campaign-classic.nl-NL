---
solution: Campaign Classic
product: campaign
title: Toegang tot SAP HANA configureren
description: Leer hoe u toegang tot SAP HANA kunt configureren in FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Toegang tot SAP HANA {#configure-access-to-sap-hana} configureren

Gebruik de optie Campagne [Federated Data Access](../../installation/using/about-fda.md) (FDA) om informatie te verwerken die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot SAP HANA te configureren.

1. [SAP HANA-database](#sap-config) configureren
1. SAP HANA [externe account](#sap-external) configureren in campagne

## SAP HANA-stuurprogramma&#39;s {#sap-config}

Voor verbinding met een externe SAP HANA-database in FDA zijn bepaalde aanvullende configuraties op de Adobe Campaign-server vereist:

1. Installeer de ODBC-stuurprogramma&#39;s voor SAP HANA volgens het besturingssysteem dat u gebruikt:

   * **hdb_client_linux.** tgzfor Linux. Nadat u de installatie hebt beëindigd, start u de hdbinst-opdracht en volgt u de instructies om de installatie van de stuurprogramma&#39;s te voltooien.
   * **hdb_client_windows.** zipfor Windows. Pak het bestand uit en start het uitvoerbare bestand: **hdbinst.exe**. Volg de aanwijzingen van de wizard om de installatie van de stuurprogramma&#39;s te voltooien.

1. Configureer het ODBC-stuurprogramma. De configuratie kan in de standaarddossiers worden uitgevoerd: /etc/odbc.ini voor algemene parameters en /etc/odbcinst.ini voor het declareren van stuurprogramma&#39;s.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot; komt overeen met de locatie van het **odbcinst.ini**-bestand.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Geef de omgevingsvariabelen van de Adobe Campaign-server op:

   * **LD_LIBRARY_PATH**: Het zou de verbinding aan uw cliënt van SAP Hana (/usr/sap/hdbclient/libodbcHDB.so) door gebrek moeten omvatten.
   * **ODBCINI**: locatie van het bestand odbc.ini (bijvoorbeeld /etc/odbc.ini).

## SAP HANA externe account{#sap-external}

Met de externe SAP HANA-account kunt u uw Campagne-instantie verbinden met uw externe SAP HANA-database.

1. Klik in Campagne **[!UICONTROL Explorer]** op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klik **[!UICONTROL New]** en selecteer **[!UICONTROL External database]** als **[!UICONTROL Type]**.

1. Om de **[!UICONTROL SAP Hana]** externe rekening te vormen, moet u specificeren:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL van de SAP Hana-server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount
