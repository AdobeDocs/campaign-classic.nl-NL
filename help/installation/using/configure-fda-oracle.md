---
product: campaign
title: Toegang tot Oracle configureren
description: Leer hoe te om toegang tot Oracle in FDA te vormen
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Toegang tot Oracle {#configure-access-to-oracle} configureren

Gebruik de optie Campagne [Federated Data Access](../../installation/using/about-fda.md) (FDA) om informatie te verwerken die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot Oracle te configureren.

1. Oracle configureren op [Linux](#oracle-linux) of [Windows](#azure-windows)
1. Het Oracle [externe account](#oracle-external) configureren in Campagne

## Oracle op Linux {#oracle-linux}

Voor verbinding met een externe database van een Oracle in FDA zijn hieronder aanvullende configuraties op de Adobe Campaign-server vereist.

1. Installeer de volledige client van het Oracle die overeenkomt met uw versie van het Oracle.
1. Voeg uw definities TNS aan uw installatie toe. Om dit te doen, specificeer hen in een **tnsnames.ora** dossier in de /etc/oracle bewaarplaats. Als deze gegevensopslagruimte niet bestaat, maakt u deze.

   Maak vervolgens een nieuwe omgevingsvariabele TNS_ADMIN: Exporteer TNS_ADMIN=/etc/oracle en start de computer opnieuw op.

1. Integreer Oracle in uw Adobe Campaign-server (nlserver). Hiervoor controleert u of het bestand **customer.sh** aanwezig is in de map &quot;nl6&quot; van de Adobe Campaign-serverboomstructuur en of dit bestand de koppelingen naar de bibliotheken met Oracles bevat.

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

1. In Campaign Classic kunt u vervolgens uw [!DNL Oracle] externe account configureren. Raadpleeg [deze sectie](#oracle-external) voor meer informatie over het configureren van uw externe account.

## Oracle in Windows {#oracle-windows}

Voor verbinding met een externe database van een Oracle in FDA zijn hieronder aanvullende configuraties op de Adobe Campaign-server vereist.

1. Installeer de client van het Oracle.

1. Maak in de map C:Oracle een bestand **tnsnames.ora** met uw TNS-definitie.

1. Voeg een omgevingsvariabele TNS_ADMIN toe met C:Oracle als waarde en start de computer opnieuw op.

1. In Campaign Classic kunt u vervolgens uw [!DNL Oracle] externe account configureren. Raadpleeg [deze sectie](#oracle-external) voor meer informatie over het configureren van uw externe account.

## Externe rekening van oracle {#oracle-external}

Met de externe [!DNL Oracle]-account kunt u uw Campagne-instantie verbinden met de externe database van uw Oracle.

1. Selecteer **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**&#39; in Campagne **[!UICONTROL Explorer]**.

1. Kies **[!UICONTROL New]**.

1. Selecteer **[!UICONTROL External database]** als **[!UICONTROL Type]** van uw externe rekening.

1. Configureer de externe account **[!UICONTROL Oracle]**. Geef de volgende instellingen op:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: Naam van de DNS

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord gebruikersaccount

   * **[!UICONTROL Time zone]**: Tijdzone van server
   ![](assets/oracle_config.png)
