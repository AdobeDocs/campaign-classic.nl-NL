---
solution: Campaign Classic
product: campaign
title: Toegang tot Vertica configureren
description: Leer hoe u toegang tot Vertica configureert in FDA
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 4%

---


# Toegang tot Vertica configureren {#configure-fda-vertica}

![](../../assets/v7-only.svg)

De Campagne van het gebruik **Federated Data Access** (FDA) optie om informatie te verwerken die in een extern gegevensbestand wordt opgeslagen. Voer de onderstaande stappen uit om toegang tot [!DNL Vertica] te configureren.

1. [!DNL Vertica] configureren op [CentOS](#vertica-centos), [Windows](#vertica-windows) of [Debian](#vertica-debian)
1. [!DNL Vertica] [externe account](#vertica-external) configureren in campagne


>[!NOTE]
>
>[!DNL Vertica] -aansluiting is beschikbaar voor hybride en on-premise implementaties. Raadpleeg [deze pagina](../../installation/using/capability-matrix.md) voor meer informatie.

![](assets/snowflake_3.png)

## Vertica op CentOS {#vertica-centos}

Volg onderstaande stappen om [!DNL Vertica] op CentOS te configureren:

1. Download de ODBC-stuurprogramma&#39;s voor [!DNL Vertica]. [Klik ](https://www.vertica.com/download/vertica/client-drivers/) hier en download de nieuwste Linux RPM.

1. U moet dan unixODBC met het volgende bevel installeren:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Als u eerder de [!DNL Vertica] Server hebt geïnstalleerd, zal een bestuurder ODBC reeds geïnstalleerd zijn. Werk in dit geval het station als volgt bij:

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. In Adobe Campaign kunt u vervolgens uw [!DNL Vertica] externe account configureren. Raadpleeg [deze sectie](#vertica-external) voor meer informatie over het configureren van uw externe account.

## Vertica in Windows {#vertica-windows}

1. Download het [ODBC-stuurprogramma voor Windows](https://www.vertica.com/download/vertica/client-drivers/). Om de bestuurder voor Vensters te installeren, zult u .NET Kader 3.5 moeten toelaten of de installatietovenaar zal proberen om het automatisch toe te laten en te downloaden.

1. Configureer het ODBC-stuurprogramma in Windows. Raadpleeg [deze pagina](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm) voor meer informatie

1. In Adobe Campaign kunt u vervolgens uw [!DNL Vertica] externe account configureren. Raadpleeg [deze sectie](#vertical-external) voor meer informatie over het configureren van uw externe account.

## Vertica op Debian {#vertica-debian}

1. Download de ODBC-stuurprogramma&#39;s voor [!DNL Vertica]. [Klik op ](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) Opnieuw downloaden.

1. U moet dan unixODBC met het volgende bevel installeren:

   ```
   apt-get install unixODBC
   ```

1. Als u eerder de [!DNL Vertica] Server hebt geïnstalleerd, zal een bestuurder ODBC reeds geïnstalleerd zijn. Werk in dit geval het station als volgt bij:

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
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. In Adobe Campaign kunt u vervolgens uw [!DNL Vertica] externe account configureren. Raadpleeg [deze sectie](#vertica-external) voor meer informatie over het configureren van uw externe account.

## Externe rekening Vertica {#vertica-external}

U moet een [!DNL Vertica] externe rekening tot stand brengen om uw instantie van de Campagne met uw [!DNL Vertica] externe gegevensbestand te verbinden.

1. Klik in Campagne **[!UICONTROL Explorer]** op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteer **[!UICONTROL External database]** als **[!UICONTROL Type]** van uw externe rekening.

1. Configureer de externe account **[!UICONTROL Vertica]**. Geef de volgende instellingen op:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL van de  [!DNL Vertica] server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database
   ![](assets/vertica.png)
