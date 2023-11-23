---
product: campaign
title: Toegang tot Amazon Redshift configureren
description: Leer hoe u toegang tot Amazon Redshift configureert in FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 6939307c0b33ff662fe4ef9ae0192ae7b500a95c
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 4%

---

# Toegang tot Amazon Redshift configureren {#configure-access-to-redshift}

Campagne gebruiken **Federale gegevenstoegang** (FDA) optie voor het verwerken van informatie die is opgeslagen in externe databases. Voer de onderstaande stappen uit om toegang tot Amazon Redshift te configureren.

1. Configureren [Amazon Redshift-database](#configuring-redshift)
1. Opnieuw plaatsen van Amazon configureren [externe rekening](#redshift-external) in Campagne

## Amazon Redshift op Linux {#redshift-linux}

Om te vormen [!DNL Amazon Redshift] Voer in Linux de onderstaande stappen uit:

1. Controleer vóór de ODBC-installatie of de volgende pakketten op uw Linux-distributie zijn geïnstalleerd:

   * Voor Red Hat/CentOS:

     ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
     ```

   * Voor Debian:

     ```
      apt-get update
      apt-get upgrade
      apt-get install -y grep sed tar wget perl curl
     ```

1. Voordat u het script uitvoert, hebt u toegang tot meer informatie via de `--help` optie:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./redshift_odbc-setup.sh --help
   ```

1. Open de map waarin het script zich bevindt en voer het volgende script als een hoofdgebruiker uit:

   ```
     cd /usr/local/neolane/nl6/bin/fda-setup-scripts
     ./redshift_odbc-setup.sh
   ```

1. Nadat u de ODBC-stuurprogramma&#39;s hebt geïnstalleerd, moet u het Campaign Classic opnieuw starten. Voer hiertoe de volgende opdracht uit:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campagne, kunt u uw [!DNL Amazon Redshift] externe rekening. Voor meer informatie over het configureren van uw externe account raadpleegt u [deze sectie](#redshift-external).

## Amazon Redshift externe account {#redshift-external}

De [!DNL Amazon Redshift] Met een externe account kunt u uw Campagne-instantie verbinden met uw Amazon Redshift-externe database.

1. In Campaign Classic, vorm uw [!DNL Amazon Redshift] externe rekening. Van de **[!UICONTROL Explorer]**, klikt u op **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klik op **[!UICONTROL New]**.

1. Selecteren **[!UICONTROL External database]** als externe account **[!UICONTROL Type]**.

1. Vorm **[!UICONTROL Amazon Redshift]** externe account, moet u opgeven:

   * **[!UICONTROL Type]**: Amazon Redshift

   * **[!UICONTROL Server]**: Naam van de DNS

   * **[!UICONTROL Account]**: Naam van de gebruiker

   * **[!UICONTROL Password]**: Wachtwoord voor gebruikersaccount

   * **[!UICONTROL Database]**: Naam van de database indien niet opgegeven in DSN. Deze kan leeg worden gelaten, indien opgegeven in de DSN

   * **[!UICONTROL Working schema]**: Naam van uw werkschema. [Meer informatie](https://docs.aws.amazon.com/redshift/latest/dg/r_Schemas_and_tables.html)

   * **[!UICONTROL Time zone]**: Tijdzone van server

   ![](assets/amazon_redshift.png)

1. Klik op **[!UICONTROL Save]**.
