---
product: campaign
title: Toegang tot Oracle configureren
description: Leer hoe te om toegang tot Oracle in FDA te vormen
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Toegang tot Oracle configureren {#configure-access-to-oracle}



Campagne gebruiken [Federale gegevenstoegang](../../installation/using/about-fda.md) (FDA) optie voor het verwerken van informatie die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot Oracle te configureren.

1. Oracle configureren op [Linux](#oracle-linux) of [Windows](#azure-windows)
1. Het Oracle configureren [externe rekening](#oracle-external) in Campagne

## Oracle op Linux {#oracle-linux}

Voor verbinding met een externe database van een Oracle in FDA zijn hieronder aanvullende configuraties op de Adobe Campaign-server vereist.

1. Installeer de volledige client van het Oracle die overeenkomt met uw versie van het Oracle.
1. Voeg uw definities TNS aan uw installatie toe. Om dit te doen, specificeer hen in a **tnsnames.ora** in de opslagplaats van het /etc/oracle. Als deze gegevensopslagruimte niet bestaat, maakt u deze.

   Maak vervolgens een nieuwe omgevingsvariabele TNS_ADMIN: Exporteer TNS_ADMIN=/etc/oracle en start de computer opnieuw op.

1. Integreer Oracle in uw Adobe Campaign-server (nlserver). Om dit te doen, controleer dat **klant.sh** Het bestand is aanwezig in de map &quot;nl6&quot; van de Adobe Campaign-serverboomstructuur en bevat de koppelingen naar de bibliotheken van het Oracle.

   Bijvoorbeeld voor een client in 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Deze waarden (met name ORACLE_HOME) zijn afhankelijk van de installatieregisters. Controleer de boomstructuur voordat u naar deze waarden verwijst.

1. De bibliotheken installeren die nodig zijn voor het Oracle:

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

1. In Campaign Classic, kunt u dan uw vormen [!DNL Oracle] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#oracle-external).

## Oracle in Windows {#oracle-windows}

Voor verbinding met een externe database van een Oracle in FDA zijn hieronder aanvullende configuraties op de Adobe Campaign-server vereist.

1. Installeer de client van het Oracle.

1. Maak in de map C:Oracle een **tnsnames.ora** bestand met uw TNS-definitie.

1. Voeg een omgevingsvariabele TNS_ADMIN toe met C:Oracle als waarde en start de computer opnieuw op.

1. In Campaign Classic, kunt u dan uw vormen [!DNL Oracle] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#oracle-external).

## Externe rekening van oracle {#oracle-external}

De [!DNL Oracle] Met een externe account kunt u uw Campagne-instantie verbinden met de externe database van uw Oracle.

1. Van campagne **[!UICONTROL Explorer]**, selecteert u **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Kies **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

1. Configureer de **[!UICONTROL Oracle]** externe account, moet u opgeven:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: Naam van de DNS

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Time zone]**: Tijdzone van server
   ![](assets/oracle_config.png)
