---
product: campaign
title: Toegang tot [!DNL Vertica Analytics] configureren
description: Leer hoe te om toegang tot  [!DNL Vertica Analytics]  in FDA te vormen
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Toegang configureren tot [!DNL Vertica Analytics] {#configure-fda-vertica}



De optie van de Toegang van Gegevens van de Campagne van het gebruik **Federated** (FDA) om informatie te verwerken die in een extern gegevensbestand wordt opgeslagen. Voer de onderstaande stappen uit om toegang tot [!DNL Vertica Analytics] te configureren.

1. Vorm [!DNL Vertica Analytics] op [ CentOS ](#vertica-centos), [ Vensters ](#vertica-windows) of [ Debian ](#vertica-debian)
1. Vorm de [!DNL Vertica Analytics] [ externe rekening ](#vertica-external) in Campagne

![](assets/snowflake_3.png)

## [!DNL Vertica Analytics] op CentOS {#vertica-centos}

Voer de onderstaande stappen uit om [!DNL Vertica Analytics] op CentOS te configureren:

1. Download de ODBC-stuurprogramma&#39;s voor [!DNL Vertica Analytics] . [ klik hier ](https://www.vertica.com/download/vertica/client-drivers/) en download recentste Linux RPM.

1. U moet dan unixODBC met het volgende bevel installeren:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Als u de [!DNL Vertica Analytics] Server eerder hebt geïnstalleerd, wordt al een ODBC-stuurprogramma geïnstalleerd. Werk in dit geval het station als volgt bij:

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [VerVertica Analyticstica]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. In Adobe Campaign kunt u vervolgens uw [!DNL Vertica Analytics] externe account configureren. Voor meer op hoe te om uw externe rekening te vormen, verwijs naar [ deze sectie ](#vertica-external).

## [!DNL Vertica Analytics] in Windows {#vertica-windows}

1. Download de [ bestuurder ODBC voor Vensters ](https://www.vertica.com/download/vertica/client-drivers/). Om de bestuurder voor Vensters te installeren, zult u .NET Kader 3.5 moeten toelaten of de installatiemedewerker zal proberen om het automatisch toe te laten en te downloaden.

1. Configureer het ODBC-stuurprogramma in Windows. Voor meer op dit, verwijs naar [ deze pagina ](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. In Adobe Campaign kunt u vervolgens uw [!DNL Vertica Analytics] externe account configureren. Voor meer op hoe te om uw externe rekening te vormen, verwijs naar [ deze sectie ](#vertical-external).

## [!DNL Vertica Analytics] op Debian {#vertica-debian}

1. Download de ODBC-stuurprogramma&#39;s voor [!DNL Vertica Analytics] . [ klik hier ](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) begin het downloaden.

1. U moet dan unixODBC met het volgende bevel installeren:

   ```
   apt-get install unixODBC
   ```

1. Als u de [!DNL Vertica Analytics] Server eerder hebt geïnstalleerd, wordt al een ODBC-stuurprogramma geïnstalleerd. Werk in dit geval het station als volgt bij:

   ```
   #Switch to root
   sudo su
   
   #Move or copy the downloaded file and change to /root
   mv vertica_9.3..xx_odbc_x86_64_linux.tar.gz /
   cd /
   
   #Uncompress the file you downloaded
   tar vzxf vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Remove the tar.gz since it is not needed anymore
   rm vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [Vertica Analytics]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. In Adobe Campaign kunt u vervolgens uw [!DNL Vertica Analytics] externe account configureren. Voor meer op hoe te om uw externe rekening te vormen, verwijs naar [ deze sectie ](#vertica-external).

## [!DNL Vertica Analytics] externe account {#vertica-external}

U moet een [!DNL Vertica Analytics] externe account maken om uw Campagne-instantie te verbinden met uw [!DNL Vertica Analytics] externe database.

1. Klik in Campagne **[!UICONTROL Explorer]** op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]** .

1. Klik op **[!UICONTROL New]**.

1. Selecteer **[!UICONTROL External database]** als de externe account van uw account **[!UICONTROL Type]** .

1. Configureer de externe account van **[!UICONTROL Vertica Analytics]** , u moet het volgende opgeven:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL van de [!DNL Vertica Analytics] -server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: naam van de database

   ![](assets/vertica.png)

De connector ondersteunt de volgende opties:

| Optie | Beschrijving |
|---|---|
| TimeZoneName | Standaard leeg, wat betekent dat de systeemtijdzone van de Campaign Classic-app-server wordt gebruikt. De optie kan worden gebruikt om de TIMEZONE-sessieparameter te forceren. |

