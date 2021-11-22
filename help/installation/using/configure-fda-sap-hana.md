---
product: campaign
title: Toegang tot SAP HANA configureren
description: Leer hoe te om toegang tot SAP HANA in FDA te vormen
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Toegang tot SAP HANA configureren {#configure-access-to-sap-hana}

![](../../assets/v7-only.svg)

Campagne gebruiken [Federale gegevenstoegang](../../installation/using/about-fda.md) (FDA) optie voor het verwerken van informatie die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot SAP HANA te configureren.

1. Configureren [SAP HANA-database](#sap-config)
1. Het SAP HANA configureren [externe rekening](#sap-external) in Campagne

## SAPPEN HANA {#sap-config}

Voor verbinding met een externe database van een SAP HANA in FDA zijn bepaalde aanvullende configuraties op de Adobe Campaign-server vereist:

1. Installeer de ODBC-stuurprogramma&#39;s voor het SAP HANA, afhankelijk van het besturingssysteem dat u gebruikt:

   * **hdb_client_linux.tgz** voor Linux. Nadat u de installatie hebt beëindigd, start u de hdbinst-opdracht en volgt u de instructies om de installatie van de stuurprogramma&#39;s te voltooien.
   * **hdb_client_windows.zip** voor Windows. Pak het bestand uit en start het uitvoerbare bestand: **hdbinst.exe**. Volg de aanwijzingen van de wizard om de installatie van de stuurprogramma&#39;s te voltooien.

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

      &quot;InstallDir&quot; komt overeen met de locatie van de **odbcinst.ini** bestand.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Geef de omgevingsvariabelen van de Adobe Campaign-server op:

   * **LD_LIBRARY_PATH**: Het zou de verbinding aan uw cliënt van SAP Hana (/usr/sap/hdbclient/libodbcHDB.so) door gebrek moeten omvatten.
   * **ODBCINI**: locatie van het bestand odbc.ini (bijvoorbeeld /etc/odbc.ini).

## Externe rekening van SAP HANA{#sap-external}

Met de externe account van het SAP HANA kunt u uw Campagne-instantie verbinden met uw externe database van het SAP HANA.

1. Van campagne **[!UICONTROL Explorer]**, klikt u op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klikken **[!UICONTROL New]** en selecteert u **[!UICONTROL External database]** als **[!UICONTROL Type]**.

1. Om het **[!UICONTROL SAP Hana]** externe account, moet u opgeven:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL van de SAP Hana-server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount
