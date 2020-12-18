---
solution: Campaign Classic
product: campaign
title: Toegang tot Oracle configureren
description: Leer hoe u toegang tot Oracle kunt configureren in FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# Toegang tot Oracle {#configure-access-to-oracle} configureren

Gebruik de optie Campagne [Federated Data Access](../../installation/using/about-fda.md) (FDA) om informatie te verwerken die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot Oracle te configureren.

1. Oracle configureren op [Linux](#oracle-linux) of [Windows](#azure-windows)
1. Oracle [externe account](#oracle-external) configureren in campagne

## Oracle op Linux {#oracle-linux}

Als u verbinding maakt met een externe Oracle-database in FDA, hebt u hieronder aanvullende configuraties op de Adobe Campaign-server nodig.

1. Installeer de volledige Oracle-client die overeenkomt met uw versie van Oracle.
1. Voeg uw definities TNS aan uw installatie toe. Om dit te doen, specificeer hen in een **tnsnames.ora** dossier in de /etc/oracle bewaarplaats. Als deze gegevensopslagruimte niet bestaat, maakt u deze.

   Maak vervolgens een nieuwe omgevingsvariabele TNS_ADMIN: Exporteer TNS_ADMIN=/etc/oracle en start de computer opnieuw op.

1. Integreer Oracle in uw Adobe Campaign-server (nlserver). Hiervoor controleert u of het bestand **customer.sh** aanwezig is in de map &quot;nl6&quot; van de Adobe Campaign-serverboomstructuur en of dit bestand de koppelingen naar de Oracle-bibliotheken bevat.

   Bijvoorbeeld voor een client in 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Deze waarden (in het bijzonder ORACLE_HOME) zijn afhankelijk van de installatieregisters. Controleer de boomstructuur voordat u naar deze waarden verwijst.

1. De bibliotheken installeren die nodig zijn voor Oracle:

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

## Oracle op Windows {#oracle-windows}

Als u verbinding maakt met een externe Oracle-database in FDA, hebt u hieronder aanvullende configuraties op de Adobe Campaign-server nodig.

1. Installeer de Oracle-client.

1. Maak in de map C:Oracle een bestand **tnsnames.ora** met uw TNS-definitie.

1. Voeg een omgevingsvariabele TNS_ADMIN toe met C:Oracle als waarde en start de computer opnieuw op.

1. In Campaign Classic kunt u vervolgens uw [!DNL Oracle] externe account configureren. Raadpleeg [deze sectie](#oracle-external) voor meer informatie over het configureren van uw externe account.

## Oracle externe account {#oracle-external}

Met de externe [!DNL Oracle]-account kunt u uw Campagne-instantie verbinden met uw externe Oracle-database.

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

