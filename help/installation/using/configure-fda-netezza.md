---
solution: Campaign Classic
product: campaign
title: Toegang tot Netezza configureren
description: Leer hoe u toegang tot Netezza kunt configureren in FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# Toegang tot Netezza {#configure-access-to-netezza} configureren

Gebruik de optie Campagne [Federated Data Access](../../installation/using/about-fda.md) (FDA) om informatie te verwerken die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot Netezza te configureren.

1. [Netezza-stuurprogramma&#39;s installeren en configureren](#netezza-config)
1. Netezza [externe account](#netezza-external) configureren in campagne

## Netezza-configuratie {#netezza-config}

Als u verbinding maakt met een externe Netezza-database in FDA, hebt u hieronder aanvullende configuraties op de Adobe Campaign-server nodig:

1. Installeer de ODBC-stuurprogramma&#39;s voor Netezza volgens het besturingssysteem dat u gebruikt:

   * **nz-linuxclient-v7.2.0.0.tar.** gzfor Linux. Selecteer de map die overeenkomt met uw besturingssysteem (linux of linux64) en start de opdracht Uitpakken. U kunt de installatie laten uitvoeren in de opslagplaats die standaard wordt voorgesteld: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.** zipfor Windows. Pak het bestand uit en start het uitvoerbare script dat overeenkomt met uw besturingssysteem: nzodbcsetup.exe of nzodbcsetup64.exe. Volg de aanwijzingen van de wizard om de installatie van de stuurprogramma&#39;s te voltooien.

1. Configureer het ODBC-stuurprogramma. De configuratie kan in de standaarddossiers worden uitgevoerd: **/etc/odbc.ini** voor algemene parameters en **/etc/odbcinst.ini** voor het declareren van stuurprogramma&#39;s.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; komt overeen met de locatie van het bestand odbcinst.ini.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Geef de omgevingsvariabelen van de Adobe Campaign-server op:

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib en /usr/local/nz/lib64. &quot;/usr/local/nz&quot; komt overeen met de standaardopslagplaats voor de installatie van de stuurprogramma&#39;s. Hier moet u de opslagplaats specificeren die u voor de installatie hebt geselecteerd.
   * **ODBCINI**: locatie van het bestand odbc.ini (bijvoorbeeld /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: locatie van het bestand odbc.ini. Netezza heeft deze tweede variabele ook nodig voor het gebruik van het bestand odbc.ini.

## Netezza externe account {#netezza-external}

Met de externe Netezza-account kunt u uw Campagne-instantie verbinden met uw externe Netezza-database.

1. Klik in Campagne **[!UICONTROL Explorer]** op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klik **[!UICONTROL New]** en selecteer **[!UICONTROL External database]** als **[!UICONTROL Type]**.

1. Om de **[!UICONTROL Netezza]** externe rekening te vormen, moet u specificeren:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: URL van de Netezza-server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database

>[!NOTE]
>
>Bewerkingen op schema&#39;s die automatisch gegenereerde primaire sleutels bevatten, worden niet in aanmerking genomen.
>
>De tabel gebruikt de **Organize on**-component op de eerste index die in het schema is gedefinieerd. Aangezien deze clausule tot 1 tot 4 kolommen met Netezza wordt beperkt, kan deze index niet meer dan 4 kolommen bevatten.
