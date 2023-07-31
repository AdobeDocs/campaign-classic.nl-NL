---
product: campaign
title: Toegang tot Vertica analytics configureren
description: Leer hoe u toegang tot Vertica analytics configureert in FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 3%

---

# Toegang tot Vertica analytics configureren {#configure-fda-vertica}



Campagne gebruiken **Federale gegevenstoegang** (FDA) om informatie te verwerken die in een externe database is opgeslagen. Voer de onderstaande stappen uit om toegang te configureren voor [!DNL Vertica Analytics].

1. Configureren [!DNL Vertica Analytics] op [CentOS](#vertica-centos), [Windows](#vertica-windows) of [Debian](#vertica-debian)
1. Vorm [!DNL Vertica Analytics] [externe rekening](#vertica-external) in Campagne

![](assets/snowflake_3.png)

## Vertica analytics op CentOS {#vertica-centos}

Om te vormen [!DNL Vertica Analytics] Voer in CentOS de onderstaande stappen uit:

1. Download de ODBC-stuurprogramma&#39;s voor [!DNL Vertica Analytics]. [Klik hier](https://www.vertica.com/download/vertica/client-drivers/) en download de nieuwste Linux RPM.

1. U moet dan unixODBC met het volgende bevel installeren:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Als u eerder de [!DNL Vertica Analytics] Server, wordt al een ODBC-stuurprogramma geïnstalleerd. Werk in dit geval het station als volgt bij:

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

1. In Adobe Campaign kunt u vervolgens uw [!DNL Vertica Analytics] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#vertica-external).

## Vertica analytics in Windows {#vertica-windows}

1. Download de [ODBC-stuurprogramma voor Windows](https://www.vertica.com/download/vertica/client-drivers/). Om de bestuurder voor Vensters te installeren, zult u .NET Kader 3.5 moeten toelaten of de installatietovenaar zal proberen om het automatisch toe te laten en te downloaden.

1. Configureer het ODBC-stuurprogramma in Windows. Raadpleeg [deze pagina](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm) voor meer informatie

1. In Adobe Campaign kunt u vervolgens uw [!DNL Vertica Analytics] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#vertical-external).

## Vertica analytics over Debian {#vertica-debian}

1. Download de ODBC-stuurprogramma&#39;s voor [!DNL Vertica Analytics]. [Klik hier](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) beginnen met downloaden.

1. U moet dan unixODBC met het volgende bevel installeren:

   ```
   apt-get install unixODBC
   ```

1. Als u eerder de [!DNL Vertica Analytics] Server, wordt al een ODBC-stuurprogramma geïnstalleerd. Werk in dit geval het station als volgt bij:

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

1. In Adobe Campaign kunt u vervolgens uw [!DNL Vertica Analytics] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#vertica-external).

## Externe rekening vertica analytics {#vertica-external}

U moet een [!DNL Vertica Analytics] externe account om uw Campagne-instantie aan te sluiten op uw [!DNL Vertica Analytics] externe database.

1. Van campagne **[!UICONTROL Explorer]**, klikt u op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

1. Vorm **[!UICONTROL Vertica Analytics]** externe account, moet u opgeven:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL van de [!DNL Vertica Analytics] server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord voor gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database

   ![](assets/vertica.png)

De connector ondersteunt de volgende opties:

| Option | Beschrijving |
|---|---|
| TimeZoneName | Standaard leeg, wat betekent dat de systeemtijdzone van de Campaign Classic-toepassingsserver wordt gebruikt. De optie kan worden gebruikt om de TIMEZONE-sessieparameter te forceren. |

