---
product: campaign
title: Toegang tot SAP HANA configureren
description: Leer hoe te om toegang tot SAP HANA in FDA te vormen
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Toegang tot SAP HANA {#configure-access-to-sap-hana} configureren

Gebruik de optie Campagne [Federated Data Access](../../installation/using/about-fda.md) (FDA) om informatie te verwerken die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot SAP HANA te configureren.

1. [SAP HANA database](#sap-config) configureren
1. Het SAP HANA [externe account](#sap-external) configureren in Campagne

## Stuurprogramma&#39;s voor SAPPEN HANA {#sap-config}

Voor verbinding met een externe database van een SAP HANA in FDA zijn bepaalde aanvullende configuraties op de Adobe Campaign-server vereist:

1. Installeer de ODBC-stuurprogramma&#39;s voor het SAP HANA, afhankelijk van het besturingssysteem dat u gebruikt:

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

## Externe account van SAP HANA{#sap-external}

Met de externe account van het SAP HANA kunt u uw Campagne-instantie verbinden met uw externe database van het SAP HANA.

1. Klik in Campagne **[!UICONTROL Explorer]** op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klik **[!UICONTROL New]** en selecteer **[!UICONTROL External database]** als **[!UICONTROL Type]**.

1. Om de **[!UICONTROL SAP Hana]** externe rekening te vormen, moet u specificeren:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL van de SAP Hana-server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount
