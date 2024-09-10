---
product: campaign
title: Toegang tot Netezza configureren
description: Leer hoe te om toegang tot Netezza in FDA te vormen
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Toegang tot Netezza configureren {#configure-access-to-netezza}



De optie van de Toegang van Gegevens van de Campagne van het gebruik [ Federated ](../../installation/using/about-fda.md) (FDA) om informatie te verwerken die in externe gegevensbestanden wordt opgeslagen. Voer de onderstaande stappen uit om toegang tot Netezza te configureren.

1. Installeer en vorm [ bestuurders van de Netezza ](#netezza-config)
1. Vorm de Netezza [ externe rekening ](#netezza-external) in Campagne

## Configuratie van netezza {#netezza-config}

Als u verbinding maakt met een externe database van een Netezza in FDA, hebt u hieronder aanvullende configuraties op de Adobe Campaign-server nodig:

1. Installeer de ODBC-stuurprogramma&#39;s voor de Netezza, afhankelijk van het besturingssysteem dat u gebruikt:

   * **nz-linuxclient-v7.2.0.0.tar.gz** voor Linux. Selecteer de map die overeenkomt met uw besturingssysteem (linux of linux64) en start de opdracht Uitpakken. U kunt de installatie laten uitvoeren in de opslagplaats die standaard wordt voorgesteld: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip** voor Vensters. Pak het bestand uit en start het uitvoerbare script dat overeenkomt met uw besturingssysteem: nzodbcsetup.exe of nzodbcsetup64.exe. Volg de instructies van de assistent om de installatie van de stuurprogramma&#39;s te voltooien.

1. Vorm het ODBC bestuurder. De configuratie kan in de standaarddossiers worden uitgevoerd: **/etc/odbc.ini** voor algemene parameters en **/etc/odbcinst.ini** voor het verklaren van bestuurders.

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

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib en /usr/local/nz/lib64. &quot;/usr/local/nz&quot; komt overeen met de standaardopslagplaats voor de installatie van de drivers. Hier moet u de opslagplaats specificeren die u voor de installatie hebt geselecteerd.
   * **ODBCINI**: plaats van het odbc.ini- dossier (bijvoorbeeld /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: plaats van het odbc.ini- dossier. Netezza vereist ook deze tweede variabele voor het gebruiken van het odbc.ini- dossier.

## Externe rekening van netezza {#netezza-external}

Met de externe account van de Netezza kunt u uw Campagne-instantie verbinden met de externe database van uw Netezza.

1. Klik in Campagne **[!UICONTROL Explorer]** op **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]** .

1. Klik op **[!UICONTROL New]** en selecteer **[!UICONTROL External database]** as **[!UICONTROL Type]** .

1. Als u de externe account van **[!UICONTROL Netezza]** wilt configureren, moet u opgeven:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: URL van de Netezza-server

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: wachtwoord gebruikersaccount

   * **[!UICONTROL Database]**: naam van de database

>[!NOTE]
>
>Bewerkingen op schema&#39;s met automatisch gegenereerde primaire sleutels worden niet in aanmerking genomen.
>
>De lijst zal **gebruiken organiseert zich op** clausule op de eerste die index in het schema wordt bepaald. Aangezien deze clausule tot 1 tot 4 kolommen met Netezza wordt beperkt, kan deze index niet meer dan 4 kolommen bevatten.
