---
product: campaign
title: Toegang tot Sybases IQ configureren
description: Leer hoe u toegang tot Sybases IQ kunt configureren in FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 2%

---

# Toegang tot Sybases IQ configureren {#configure-access-to-sybase-iq}



Campagne gebruiken **Federale gegevenstoegang** (FDA) optie voor het verwerken van informatie die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot Sybase IQ te configureren.

1. Configureren [Database sybases IQ](#configuring-sybase)
1. De Sybases IQ configureren [externe rekening](#sybase-external) in Campagne

## Configuratie van sybase IQ {#configuring-sybase}

Voor verbinding met een externe database van Sybase IQ in FDA zijn hieronder aanvullende configuraties op de Adobe Campaign-server vereist.

>[!NOTE]
>
>Voordat u begint, moet u ervoor zorgen dat **unixodbc** -pakket bevindt zich op de server.

1. Installeren **iq_odbc**. Er kan een fout optreden aan het einde van de installatie. Deze fout kan worden genegeerd.

1. Installeren **iq_client_common**. Er kan een Java-fout optreden aan het einde van de installatie. Deze fout kan worden genegeerd.

1. Vorm het ODBC bestuurder. De configuratie kan worden uitgevoerd in de standaardbestanden: /etc/odbc.ini voor algemene parameters en /etc/odbcinst.ini voor het declareren van stuurprogramma&#39;s:

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

   * Als u een bestand customer.sh gebruikt om uw pad te declareren: voeg het pad /opt/sybase/IQ-16_0/lib64 voor de variabele LD_LIBRARY_PATH toe.
   * Gebruik anders een Unix-opdracht.

## Sybase IQ externe rekening {#sybase-external}

Met de externe account Sybase IQ kunt u uw Campagne-instantie verbinden met uw Sybase IQ-database.

1. Van campagne **[!UICONTROL Explorer]**, klikt u op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klikken **[!UICONTROL New]** en selecteert u **[!UICONTROL External database]** als **[!UICONTROL Type]**.

1. Om te vormen **[!UICONTROL Sybase IQ]** externe account, moet u opgeven:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Komt overeen met de ODBC-verbinding (`<server_alias>`) gedefinieerd in stap 5. Niet noodzakelijkerwijs de naam van de server zelf.

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord voor gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database

>[!NOTE]
>
>Voor Windows moet u de Sybase IQ-client op de Adobe Campaign-server installeren en een ODBC-verbinding maken. Zorg ervoor dat u een systeemgegevensbron maakt wanneer de Adobe Campaign-server (nlserver) als service in Windows wordt uitgevoerd.
