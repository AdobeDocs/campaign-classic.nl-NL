---
title: Toegang tot synapse configureren
description: Leer hoe u toegang tot Synapse in FDA configureert
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: be3626e858ced32e9dbfd5d07da29a4ccf256ac4
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 1%

---


# Toegang tot Azure synapse configureren {#configure-access-to-azure-synapse}

Gebruik de optie Campagne [Federated Data Access](../../installation/using/about-fda.md) (FDA) om informatie te verwerken die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot Microsoft Azure synapse Analytics te configureren.

1. Azure synapse configureren op [CentOS](#azure-centos), [Windows](#azure-windows) of [Debian](#azure-debian)
1. De [externe Azure synapse-account](#azure-external) configureren in Campagne

## azure synapse op CentOS {#azure-centos}

>[!CAUTION]
>
>* U hebt basisrechten nodig om een ODBC-stuurprogramma te installeren.
>* Red Hat Enterprise ODBC-stuurprogramma&#39;s van Microsoft kunnen ook worden gebruikt met CentOS om verbinding te maken met SQL Server.
>* Versie 13.0 werkt met Red Hat 6 en 7.


Volg onderstaande stappen om Azure synapse op CentOS te configureren:

1. Installeer eerst het ODBC-stuurprogramma. U vindt deze op deze [pagina](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

   >[!NOTE]
   >
   >Dit is exclusief voor versie 13 van het ODBC-stuurprogramma.

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   # Uninstall if already installed Unix ODBC driver
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   
   sudo ACCEPT_EULA=Y yum install msodbcsql
   
   sudo ACCEPT_EULA=Y yum install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   
   # the Microsoft driver expects unixODBC to be here /usr/lib64/libodbc.so.1, so add soft links to the '.so.2' files
   cd /usr/lib64
   sudo ln -s libodbccr.so.2   libodbccr.so.1
   sudo ln -s libodbcinst.so.2 libodbcinst.so.1
   sudo ln -s libodbc.so.2     libodbc.so.1
   
   # Set the path for unixODBC
   export ODBCINI=/usr/local/etc/odbc.ini
   export ODBCSYSINI=/usr/local/etc
   source ~/.bashrc
   
   #Add a DSN information to /etc/odbc.ini
   sudo vi /etc/odbc.ini
   
   #Add the following:
   [Azure Synapse Analytics]
   Driver      = ODBC Driver 13 for SQL Server
   Description = Azure Synapse Analytics DSN
   Trace       = No
   Server      = [insert your server here]
   ```

1. Indien nodig, kunt u UnixODBC ontwikkelingsheaders installeren door het volgende bevel in werking te stellen:

   ```
   sudo yum install unixODBC-devel
   ```

1. Nadat u de stuurprogramma&#39;s hebt geïnstalleerd, kunt u het ODBC-stuurprogramma testen en controleren en zo nodig een query uitvoeren op uw database. Voer de volgende opdracht uit:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. In Campagne, kunt u uw [!DNL Azure Synapse] externe rekening dan vormen. Raadpleeg [deze sectie](#azure-external)voor meer informatie over het configureren van uw externe account.

1. Aangezien Azure synapse Analytics via de TCP 1433-poort communiceert, moet u deze poort openen op uw firewall. Gebruik de volgende opdracht:

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Om communicatie van de zijde van Analytics van Azure synapse toe te staan zou u uw openbare IP aan de lijst van gewenste personen kunnen moeten toevoegen. Raadpleeg de [Azure-documentatie](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)om dit te doen.

1. Voer in het geval van iptables de volgende opdracht uit:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

## azure synapse in Windows {#azure-windows}

>[!NOTE]
>
>Dit is exclusief aan versie 13 van de Bestuurder ODBC maar Adobe Campaign Classic kan SQL de Inheemse bestuurders van de Cliënt van de Server 11.0 en 10.0 ook gebruiken.

Azure synapse in Windows configureren:

1. Installeer eerst het Microsoft ODBC-stuurprogramma. U vindt deze op [deze pagina](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Kies de volgende bestanden om te installeren:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. Nadat het ODBC-stuurprogramma is geïnstalleerd, kunt u het indien nodig testen. Raadpleeg [deze pagina](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server) voor meer informatie.

1. In Campaign Classic kunt u vervolgens uw [!DNL Azure Synapse] externe account configureren. Raadpleeg [deze sectie](#azure-external)voor meer informatie over het configureren van uw externe account.

1. Aangezien de Analytics van Azure synapse door de haven van TCP 1433 communiceert, moet u deze haven op de Firewall van de Verdediger van Vensters openen. For more on this, refer to [Windows documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

## azure synapse op Debian {#azure-debian}

**Vereisten:**

* U hebt basisrechten nodig om een ODBC-stuurprogramma te installeren.
* Er is een curve nodig om het msodbcsql-pakket te installeren. Als u het geïnstalleerd hebt, stel het volgende bevel in werking:

   ```
   sudo apt-get install curl
   ```

Azure synapse configureren op Debian:

1. Installeer eerst het Microsoft ODBC-stuurprogramma voor SQL Server. Gebruik de volgende bevelen om Bestuurder ODBC 13.1 voor SQL Server te installeren:

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. Als u de volgende fout krijgt **&quot;Het methodebestuurder /usr/lib/apt/methods/https kon niet worden gevonden&quot;** wanneer het roepen van **sudo apt-get update**, zou u het bevel moeten in werking stellen:

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. U moet nu mssql-hulpmiddelen met de volgende bevelen installeren. Mssq-hulpmiddelen zijn nodig om het bulkexemplaarprogramma (of BCP) nut te gebruiken en vragen in werking te stellen.

   ```
   sudo ACCEPT_EULA=Y apt-get install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

1. Indien nodig, kunt u UnixODBC ontwikkelingsheaders installeren door het volgende bevel in werking te stellen:

   ```
   sudo yum install unixODBC-devel
   ```

1. Nadat u de stuurprogramma&#39;s hebt geïnstalleerd, kunt u het ODBC-stuurprogramma testen en controleren en zo nodig een query uitvoeren op uw database. Voer de volgende opdracht uit:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. In Campaign Classic kunt u nu uw [!DNL Azure Synapse] externe account configureren. Raadpleeg [deze sectie](#azure-external)voor meer informatie over het configureren van uw externe account.

1. Om iptables op Debian te vormen om de verbinding met Analytics van Azure synapse te verzekeren, laat de uitgaande haven van TCP 1433 voor uw hostname met het volgende bevel toe:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Om communicatie van de zijde van Analytics van Azure synapse toe te staan zou u uw openbare IP aan de lijst van gewenste personen kunnen moeten toevoegen. Raadpleeg de [Azure-documentatie](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)om dit te doen.


## Externe azure synapse-account {#azure-external}

Met de [!DNL Azure Synapse] externe account kunt u uw Campagne-instantie verbinden met uw externe Azure synapse-database.

Volg onderstaande stappen om uw [!DNL Azure Synapse] externe account te maken:

1. Klik in Campagne **[!UICONTROL Explorer]** op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

   ![](assets/azure_1.png)

1. Configureer de [!DNL Azure Synapse] externe account. Geef de volgende instellingen op:

   * **[!UICONTROL Type]**: azure synapse Analytics

   * **[!UICONTROL Server]**: URL van de Azure synapse-server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database

