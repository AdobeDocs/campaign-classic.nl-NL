---
product: campaign
title: Toegang tot SAP HANA configureren
description: Leer hoe te om toegang tot SAP HANA in FDA te vormen
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Toegang tot SAP HANA configureren {#configure-access-to-sap-hana}



De optie van de Toegang van Gegevens van de Campagne van het gebruik [ Federated ](../../installation/using/about-fda.md) (FDA) om informatie te verwerken die in externe gegevensbestanden wordt opgeslagen. Voer de onderstaande stappen uit om toegang tot SAP HANA te configureren.

1. Vorm [ gegevensbestand van het SAP HANA ](#sap-config)
1. Vorm de SAP HANA [ externe rekening ](#sap-external) in Campagne

## SAPPEN HANA {#sap-config}

Voor verbinding met een externe database van een SAP HANA in FDA zijn bepaalde aanvullende configuraties op de Adobe Campaign-server vereist:

1. Installeer de ODBC-stuurprogramma&#39;s voor het SAP HANA, afhankelijk van het besturingssysteem dat u gebruikt:

   * **hdb_client_linux.tgz** voor Linux. Nadat u de installatie hebt beëindigd, start u de hdbinst-opdracht en volgt u de instructies om de installatie van de stuurprogramma&#39;s te voltooien.
   * **hdb_client_windows.zip** voor Vensters. Pak het dossier uit en begin uitvoerbaar: **hdbinst.exe**. Volg de instructies van de assistent om de installatie van de stuurprogramma&#39;s te voltooien.

1. Vorm het ODBC bestuurder. De configuratie kan worden uitgevoerd in de standaardbestanden: /etc/odbc.ini voor algemene parameters en /etc/odbcinst.ini voor het declareren van stuurprogramma&#39;s.

   * **/etc/odbc.ini**

     ```
     [ODBC]
     InstallDir=/etc/
     
     [HDB]
     Driver=HDBODBC
     servernode=localhost:39013 (this value depend of your server)
     User:SYSTEM
     ```

     &quot;InstallDir&quot;beantwoordt aan de plaats van het {**dossier 0} odbcinst.ini.**

   * **/etc/odbcinst.ini**

     ```
     [HDBODBC]
     Description = "SmartCloudPT HANA"
     Driver = /usr/sap/hdbclient/libodbcHDB.so
     ```

1. Geef de omgevingsvariabelen van de Adobe Campaign-server op:

   * **LD_LIBRARY_PATH**: Het zou de verbinding aan uw cliënt van SAP Hana (/usr/sap/hdbclient/libodbcHDB.so) door gebrek moeten omvatten).
   * **ODBCINI**: plaats van het odbc.ini- dossier (bijvoorbeeld /etc/odbc.ini).

## Externe rekening van SAP HANA{#sap-external}

Met de externe account van het SAP HANA kunt u uw Campagne-instantie verbinden met uw externe database van het SAP HANA.

1. Klik in Campagne **[!UICONTROL Explorer]** op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]** .

1. Klik op **[!UICONTROL New]** en selecteer **[!UICONTROL External database]** as **[!UICONTROL Type]** .

1. Als u de externe account van **[!UICONTROL SAP Hana]** wilt configureren, moet u opgeven:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL van de SAP Hana-server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: wachtwoord gebruikersaccount
