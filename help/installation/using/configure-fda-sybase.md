---
product: campaign
title: Toegang tot Sybases IQ configureren
description: Leer hoe u toegang tot Sybases IQ kunt configureren in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Toegang tot Sybases IQ configureren {#configure-access-to-sybase-iq}

![](../../assets/v7-only.svg)

Campagne gebruiken **Federale gegevenstoegang** (FDA) optie voor het verwerken van informatie die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot Sybase IQ te configureren.

1. Configureren [Database sybases IQ](#configuring-sybase)
1. De Sybases IQ configureren [externe rekening](#sybase-external) in Campagne

## Configuratie sybase IQ {#configuring-sybase}

Voor verbinding met een externe database van Sybase IQ in FDA zijn hieronder aanvullende configuraties op de Adobe Campaign-server vereist.

>[!NOTE]
>
>Voordat u begint, moet u ervoor zorgen dat **unixodbc** -pakket bevindt zich op de server.

1. Installeren **iq_odbc**. Er kan een fout optreden aan het einde van de installatie. Deze fout kan worden genegeerd.

1. Installeren **iq_client_common**. Er kan een Java-fout optreden aan het einde van de installatie. Deze fout kan worden genegeerd.

1. Configureer het ODBC-stuurprogramma. De configuratie kan in de standaarddossiers worden uitgevoerd: /etc/odbc.ini voor algemene parameters en /etc/odbcinst.ini voor het declareren van stuurprogramma&#39;s:

   * **/etc/odbc.ini** (vervang waarden als `<server_alias>` eigen tekens):

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

## sybase IQ externe rekening {#sybase-external}

Met de externe account Sybase IQ kunt u uw Campagne-instantie verbinden met uw Sybase IQ-database.

1. Van campagne **[!UICONTROL Explorer]**, klikt u op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klikken **[!UICONTROL New]** en selecteert u **[!UICONTROL External database]** als **[!UICONTROL Type]**.

1. Om het **[!UICONTROL Sybase IQ]** externe account, moet u opgeven:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Komt overeen met de ODBC-verbinding (`<server_alias>`) gedefinieerd in stap 5. Niet noodzakelijkerwijs de naam van de server zelf.

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database

>[!NOTE]
>
>Voor Windows moet u de Sybase IQ-client op de Adobe Campaign-server installeren en een ODBC-verbinding maken. Zorg ervoor dat u een systeemgegevensbron maakt wanneer de Adobe Campaign-server (nlserver) als service in Windows wordt uitgevoerd.
