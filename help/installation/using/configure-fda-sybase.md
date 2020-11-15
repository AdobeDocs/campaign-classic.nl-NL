---
title: Toegang tot Sybase IQ configureren
description: Leer hoe u toegang tot Sybase IQ in FDA configureert
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# Toegang tot Sybase IQ configureren {#configure-access-to-sybase-iq}

Gebruik de optie Campagne **Federated Data Access** (FDA) om informatie te verwerken die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot Sybase IQ te configureren.

1. Sybase IQ- [database configureren](#configuring-sybase)
1. Vorm de [externe rekening](#sybase-external) van Sybase IQ in Campagne

## Sybase IQ-configuratie {#configuring-sybase}

Voor verbinding met een externe Sybase-IQ-database in FDA zijn hieronder aanvullende configuraties op de Adobe Campaign-server vereist.

>[!NOTE]
>
>Voordat u begint, moet u controleren of het **unxodbc** -pakket zich op de server bevindt.

1. Installeer **iq_odbc**. Er kan een fout optreden aan het einde van de installatie. Deze fout kan worden genegeerd.

1. Installeer **iq_client_common**. Er kan een Java-fout optreden aan het einde van de installatie. Deze fout kan worden genegeerd.

1. Configureer het ODBC-stuurprogramma. De configuratie kan in de standaarddossiers worden uitgevoerd: /etc/odbc.ini voor algemene parameters en /etc/odbcinst.ini voor het declareren van stuurprogramma&#39;s:

   * **/etc/odbc.ini** (vervang uw eigen waarden, zoals `<server_alias>` tekens):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. Voeg het pad voor de nieuwe bibliotheek libodbc16.so toe in de variabele LD_LIBRARY_PATH. Dat doet u als volgt:

   * Als u een bestand customer.sh gebruikt om het pad te declareren: Voeg het pad /opt/sybase/IQ-16_0/lib64 toe voor de variabele LD_LIBRARY_PATH.
   * Gebruik anders een Unix-opdracht.

## Externe account voor IQ van Sybase {#sybase-external}

Met de externe Sybase IQ-account kunt u uw Campagne-instantie verbinden met uw externe Sybase IQ-database.

1. Klik in Campagne **[!UICONTROL Explorer]** op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Om de **[!UICONTROL Sybase IQ]** externe rekening te vormen, moet u specificeren:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Komt overeen met de ODBC-verbinding (`<server_alias>`) die is gedefinieerd in stap 5. Niet noodzakelijkerwijs de naam van de server zelf.

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database

>[!NOTE]
>
>Voor Windows moet u de Sybase IQ-client op de Adobe Campaign-server installeren en een ODBC-verbinding maken. Zorg ervoor dat u een systeemgegevensbron maakt wanneer de Adobe Campaign-server (nlserver) als service in Windows wordt uitgevoerd.

