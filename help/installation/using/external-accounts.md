---
product: campaign
title: Externe accounts
description: Meer informatie over het maken van externe accounts
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1636'
ht-degree: 7%

---

# Externe accounts{#external-accounts}

![](../../assets/v7-only.svg)

Adobe Campaign wordt geleverd met een set vooraf gedefinieerde externe accounts. Als u verbindingen met externe systemen wilt instellen, kunt u nieuwe externe accounts maken.

Externe accounts worden gebruikt door technische processen, zoals technische workflows of workflows voor campagnes. Als u bijvoorbeeld een bestandsoverdracht instelt in een workflow of een gegevensuitwisseling met een andere toepassing (Adobe Target, Experience Manager, enzovoort), moet u een externe account selecteren.

## Een externe account maken {#creating-an-external-account}

Voer de onderstaande stappen uit om een nieuwe externe account te maken. Gedetailleerde instellingen zijn afhankelijk van het type externe account.

1. Van campagne **[!UICONTROL Explorer]**, selecteert u **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

   ![](assets/ext_account_1.png)

1. Klik op de knop **[!UICONTROL New]**.

   ![](assets/ext_account_2.png)

1. Voer een **[!UICONTROL Label]** en **[!UICONTROL Internal Name]**.
1. Externe account selecteren **[!UICONTROL Type]** welke u wilt maken.
1. Configureer de toegang tot de account door referenties op te geven, afhankelijk van het gekozen type externe account.

   De benodigde informatie wordt meestal verstrekt door de provider van de server waarmee u verbinding maakt.

1. Controleer de **[!UICONTROL Enabled]** om de verbinding te activeren.
1. Klik op **[!UICONTROL Save]**.

De externe account wordt gemaakt en toegevoegd aan de lijst met externe accounts.

## Campagne-specifieke externe rekeningen

### Niet bezorgde mails {#bounce-mails-external-account}

De **Stuitberichten** externe account geeft de externe POP3-account aan die moet worden gebruikt voor verbinding met de e-mailservice. Voor meer informatie over deze externe account raadpleegt u deze [page](../../workflow/using/inbound-emails.md).

Alle servers die voor POP3 toegang worden gevormd kunnen worden gebruikt om terugkeerpost te ontvangen.

![](assets/ext_account_6.png)

Om het **[!UICONTROL Bounce mails (defaultPopAccount)]** externe rekening:

* **[!UICONTROL Server]**

   URL van de POP3-server.

* **[!UICONTROL Port]**

   POP3-poortnummer van verbinding. De standaardpoort is 110.

* **[!UICONTROL Account]**

   Naam van de gebruiker.

* **[!UICONTROL Password]**

   Wachtwoord voor gebruikersaccount.

* **[!UICONTROL Encryption]**

   Type gekozen codering tussen **[!UICONTROL By default]**, **[!UICONTROL POP3 + STARTTLS]**, **[!UICONTROL POP3]** of **[!UICONTROL POP3S]**.

### Routering{#routing-external-account}

De **[!UICONTROL Routing]** met een externe account kunt u elk kanaal dat beschikbaar is in Adobe Campaign configureren, afhankelijk van de geïnstalleerde pakketten.

![](assets/ext_account_7.png)

De volgende kanalen kunnen worden gevormd:

* [Email](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [Mobile (SMS)](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [Telefoon](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Direct mail](../../delivery/using/about-direct-mail-channel.md)
* [Bureau](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Facebook](../../social/using/publishing-on-facebook-walls.md#delegating-write-access-to-adobe-campaign)
* [Twitter](../../social/using/configuring-publishing-on-twitter.md)
* [iOS-kanaal](../../delivery/using/configuring-the-mobile-application.md)
* [Android-kanaal](../../delivery/using/configuring-the-mobile-application-android.md)

### Uitvoeringsinstantie  {#execution-instance-external-account}

Als u een opgesplitste architectuur hebt, moet u de uitvoeringsinstanties specificeren verbonden aan de controleinstantie en hen verbinden. Transactieberichtsjablonen worden geïmplementeerd in de uitvoeringsinstantie

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   URL van de server waarop de uitvoeringsinstantie is geïnstalleerd.

* **[!UICONTROL Account]**

   Naam van de rekening, moet het de Agent van het Centrum van het Bericht aanpassen zoals die in de exploitantomslag wordt bepaald.

* **[!UICONTROL Password]**

   Wachtwoord van de account zoals gedefinieerd in de map met operatoren.

Voor meer informatie over deze configuratie, verwijs naar dit [page](../../message-center/using/configuring-instances.md#control-instance).

## Toegang tot externe systeemrekeningen

### FTP {#ftp-external-account}

Met de externe FTP-account kunt u toegang tot een server buiten Adobe Campaign configureren en testen. Als u verbindingen wilt instellen met externe systemen, zoals FTP-servers 898 die worden gebruikt voor bestandsoverdracht, kunt u uw eigen externe accounts maken. Raadpleeg [deze pagina](../../workflow/using/file-transfer.md) voor meer informatie.

Hiertoe geeft u in deze externe account het adres en de referenties op waarmee de verbinding met de FTP-server tot stand wordt gebracht

![](assets/ext_account_8.png)

* **[!UICONTROL Server]**

   Naam van de FTP-server.

* **[!UICONTROL Port]**

   FTP-poortnummer. De standaardpoort is 21.

* **[!UICONTROL Account]**

   Naam van de gebruiker.

* **[!UICONTROL Password]**

   Wachtwoord voor gebruikersaccount.

* **[!UICONTROL Encryption]**

   Type gekozen codering tussen **[!UICONTROL None]** of **[!UICONTROL SSL]**.

Om te weten waar te om van deze geloofsbrieven de plaats te bepalen, verwijs naar dit [page](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

### SFTP {#sftp-external-account}

Met de externe SFTP-account kunt u toegang tot een server buiten Adobe Campaign configureren en testen. Als u verbindingen wilt instellen met externe systemen, zoals SFTP, die worden gebruikt voor bestandsoverdracht, kunt u uw eigen externe accounts maken. Raadpleeg [deze pagina](../../workflow/using/file-transfer.md) voor meer informatie.

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

   URL van de SFTP-server.

* **[!UICONTROL Port]**

   FTP-poortnummer. De standaardpoort is 22.

* **[!UICONTROL Account]**

   Accountnaam gebruikt om verbinding te maken met de SFTP-server.

* **[!UICONTROL Password]**

   Wachtwoord gebruikt om verbinding te maken met de SFTP-server.

### Externe database (FDA) {#external-database-external-account}

Gebruik de **Externe database** type external account to connect to external an database. Meer informatie over de FDA-optie (Federated Data Access) vindt u in [deze sectie](../../installation/using/about-fda.md).

Externe databases die compatibel zijn met Campagne worden vermeld in het dialoogvenster [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

De instellingen voor externe accountconfiguratie zijn afhankelijk van de database-engine. Meer informatie vindt u in de volgende secties:

* Toegang configureren tot [Vertica](../../installation/using/configure-fda-vertica.md)
* Toegang configureren tot [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Toegang configureren tot [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* Toegang configureren tot [azure synapse](../../installation/using/configure-fda-synapse.md)
* Toegang configureren tot [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Toegang configureren tot [Oracle](../../installation/using/configure-fda-oracle.md)
* Toegang configureren tot [Netezza](../../installation/using/configure-fda-netezza.md)
* Toegang configureren tot [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Toegang configureren tot [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Toegang configureren tot [sybase IQ](../../installation/using/configure-fda-sybase.md)
* Toegang configureren tot [Teradata](../../installation/using/configure-fda-teradata.md)

### Facebook connect {#facebook-connect-external-account}

De **[!UICONTROL Facebook Connect]** Met een externe account kunt u persoonlijke inhoud weergeven in uw Facebook-toepassingen, waardoor het eenvoudiger wordt om vooruitzichten te krijgen via dit sociale netwerk.

Voor elke Facebook-toepassing moet u een **[!UICONTROL Facebook Connect]** type external account. Raadpleeg voor meer informatie hierover [page](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/ext_account_12.png)

* **[!UICONTROL Hosting mode]**

   De hostingmodus van de toepassing tussen **[!UICONTROL hosted by a partner]** of **[!UICONTROL hosted by this instance]**.

* **[!UICONTROL Application ID]**

   Toepassings-id van uw Facebook-toepassing.

* **[!UICONTROL Application secret]**

   Toepassingsgeheim van uw Facebook-toepassing.

Als u de host hebt gekozen voor deze instantiemodus, moet de URL van het beveiligde canvas worden geplakt in de **Facebook Web Games (https)** veld op Facebook

Om te weten waar te om van deze geloofsbrieven de plaats te bepalen, verwijs naar dit [page](https://developers.facebook.com/docs/facebook-login/access-tokens).

## Adobe Oplossing integratie externe accounts

### Adobe Experience Cloud {#adobe-experience-cloud-external-account}

Als u verbinding wilt maken met de Adobe Campaign-console via een Adobe ID, moet u de **[!UICONTROL Adobe Experience Cloud (MAC)]** externe rekening.

![](assets/ext_account_9.png)

* **[!UICONTROL IMS server]**

   URL van uw IMS-server. Zorg ervoor zowel stadium als de productie instanties aan het zelfde IMS productieeindpunt richten.

* **[!UICONTROL IMS scope]**

   De hier gedefinieerde bereiken moeten een subset zijn van de gebieden die door IMS zijn ingericht.

* **[!UICONTROL IMS client identifier]**

   ID van uw IMS-client.

* **[!UICONTROL IMS client secret]**

   Credentials van het geheim van de IMS-client.

* **[!UICONTROL Callback server]**

   Toegang tot URL van je Adobe Campaign-instantie.

* **[!UICONTROL IMS organization ID]**

   ID van uw IMS-organisatie. Raadpleeg voor meer informatie over uw organisatie-id [deze pagina](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html) (**Waar kan ik mijn IMS organisatie ID vinden?**).

* **[!UICONTROL Association mask]**

   Syntaxis waarmee configuratienamen in Enterprise-dashboard kunnen worden gesynchroniseerd met de groepen in Adobe Campaign.

* **[!UICONTROL Server]**

   URL van je Adobe Experience Cloud-exemplaar.

* **[!UICONTROL Tenant]**

   Naam van je Adobe Experience Cloud Tenant.

Voor meer informatie over deze configuratie, verwijs naar [deze pagina](../../integrations/using/configuring-ims.md).

## Web Analytics {#web-analytics-external-account}

De **[!UICONTROL Web Analytics]** Met een externe account kunt u gegevens van Adobe Analytics naar Adobe Campaign doorsturen in de vorm van segmenten. Omgekeerd verzendt het programma indicatoren en kenmerken van e-mailcampagnes die door Adobe Campaign aan Adobe Analytics-connector worden geleverd.

![](assets/ext_account_10.png)

Voor deze externe account moet de berekeningsformule voor bijgehouden URL&#39;s worden verrijkt en moet de verbinding tussen de twee oplossingen worden goedgekeurd. Raadpleeg [deze pagina](../../platform/using/adobe-analytics-connector.md#external-account-classic) voor meer informatie.

### Adobe Experience Manager {#adobe-experience-manager-external-account}

De **[!UICONTROL AEM (AEM instance)]** Met een extern account kunt u de inhoud van uw e-mailleveringen en uw formulieren rechtstreeks in Adobe Experience Manager beheren.

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

   URL van de Adobe Experience Manager-server.

* **[!UICONTROL Port]**

   Accountnaam gebruikt om verbinding te maken met de Adobe Experience Manager-ontwerpinstantie.

* **[!UICONTROL Password]**

   Wachtwoord waarmee verbinding wordt gemaakt met de Adobe Experience Manager-ontwerpinstantie.

Raadpleeg deze [sectie](../../integrations/using/about-adobe-experience-manager.md) voor meer informatie.

## Externe CRM-connectorrekeningen

### Microsoft Dynamics CRM {#microsoft-dynamics-crm-external-account}

>[!NOTE]
>
> **[!UICONTROL On-premise]** en **[!UICONTROL Office 365]** de plaatsingstypes zijn nu verouderd. [Meer info](../../rn/using/deprecated-features.md).

De **[!UICONTROL Microsoft Dynamics CRM]** Met een externe account kunt u Microsoft Dynamics-gegevens importeren en exporteren naar Adobe Campaign.

Meer informatie over de Microsoft Dynamics CRM-connector in de campagne vindt u in deze [page](../../platform/using/crm-ms-dynamics.md).

Met **[!UICONTROL Web API]** implementatietype en **[!UICONTROL Password credentials]** de authentificatie, moet u de volgende details verstrekken:

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   Account gebruikt om u aan te melden bij Microsoft CRM.

* **[!UICONTROL Server]**

   URL van uw Microsoft CRM-server.

   Je Microsoft CRM vinden **[!UICONTROL Server URL]**, opent u uw Microsoft Dynamics CRM-account en klikt u op **Dynamiek 365** en selecteer uw app. U kunt dan uw **[!UICONTROL Server URL]** in de adresbalk van uw browser, bijvoorbeeld `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Client identifier]**

   Client ID, te vinden op de Microsoft Azure-beheerportal in het **[!UICONTROL Update your code]** categorie, **[!UICONTROL Client ID]** veld.

* **[!UICONTROL CRM version]**

   Kies **[!UICONTROL Dynamics CRM 365]** CRM-versie.

Met **[!UICONTROL Web API]** implementatietype en **[!UICONTROL Certificate]** de authentificatie, moet u de volgende details verstrekken:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   URL van uw Microsoft CRM-server.

   Je Microsoft CRM vinden **[!UICONTROL Server URL]**, opent u uw Microsoft Dynamics CRM-account en klikt u op **Dynamiek 365** en selecteer uw app. U kunt dan uw **[!UICONTROL Server URL]** in de adresbalk van uw browser, bijvoorbeeld `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Private Key (Base64 encoded)]**

   Merk op dat de Privé sleutel aan Base64 moet worden gecodeerd.

   Om dit te doen, kunt u de hulp van een Codeur gebruiken Base64 of de bevellijn gebruiken `base64 -w0 private.key` voor Linux.

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   Client ID, te vinden op de Microsoft Azure-beheerportal in het **[!UICONTROL Update your code]** categorie, **[!UICONTROL Client ID]** veld.

* **[!UICONTROL CRM version]**

   Versie van de CRM tussen **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** of **[!UICONTROL Dynamics CRM 2016]**.

Voor meer informatie over deze configuratie, verwijs naar dit [page](../../platform/using/crm-connectors.md).

### Salesforce.com CRM  {#salesforce-crm-external-account}

De **[!UICONTROL Salesforce CRM]** Met een externe account kunt u Salesforce-gegevens importeren en exporteren naar Adobe Campaign.

![](assets/ext_account_17.png)

Om de externe rekening van Salesforce CRM te vormen om met Adobe Campaign te werken, moet u de volgende details verstrekken:

* **[!UICONTROL Account]**

   Account gebruikt om u aan te melden bij Salesforce CRM.

* **[!UICONTROL Password]**

   Wachtwoord gebruikt om u aan te melden bij Salesforce CRM.

* **[!UICONTROL Client identifier]**

   Als u wilt weten waar u uw client-id vindt, raadpleegt u deze [page](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security token]**

   Als u wilt weten waar u uw beveiligingstoken vindt, raadpleegt u deze [page](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API version]**

   Selecteer de versie van de API.

Voor deze externe rekening, moet u u Salesforce CRM met de configuratietovenaar vormen.

Voor meer informatie over deze configuratie, verwijs naar dit [page](../../platform/using/crm-connectors.md).

## Externe accounts voor gegevensoverdracht

### Amazon Simple Storage Service (S3) {#amazon-simple-storage-service--s3--external-account}

De Amazon Simple Storage Service (S3)-connector kan worden gebruikt voor het importeren of exporteren van gegevens naar Adobe Campaign. Deze kan worden ingesteld in een workflowactiviteit. Raadpleeg [deze pagina](../../workflow/using/file-transfer.md) voor meer informatie.

![](assets/ext_account_3.png)

Wanneer u dit nieuwe externe account instelt, moet u de volgende data opgeven:

* **[!UICONTROL AWS S3 Account Server]**

   URL van uw server, zou het als volgt moeten worden gevuld:

   ```
   <S3bucket name>.s3.amazonaws.com/<s3object path>
   ```

* **[!UICONTROL AWS access key ID]**

   Als u wilt weten waar je AWS-toegangs sleutel-id moet worden gevonden, raadpleegt u deze [page](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

* **[!UICONTROL Secret access key to AWS]**

   Als je wilt weten waar je je geheime toegangssleutel voor AWS vindt, raadpleeg dan deze [page](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS Region]**

   Raadpleeg de volgende secties voor meer informatie over AWS-regio [page](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* De **[!UICONTROL Use server side encryption]** kunt u het bestand opslaan in de gecodeerde modus van S3.

Om te leren waar te om toegangs belangrijkste identiteitskaart en geheime toegangssleutel te vinden, verwijs naar de diensten van het Web van Amazon [documentatie](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

### Azure Blob Storage {#azure-blob-external-account}

De **Azure Blob-opslag** een externe account kan worden gebruikt om gegevens naar Adobe Campaign te importeren of te exporteren met behulp van een **[!UICONTROL Transfer file]** workflowactiviteit. Raadpleeg deze [sectie](../../workflow/using/file-transfer.md) voor meer informatie.

![](assets/ext_account_23.png)

Om het **[!UICONTROL Azure external account]** om met Adobe Campaign te werken, moet u de volgende details verstrekken:

* **[!UICONTROL Server]**

   URL van uw Azure Blob-opslagserver.

* **[!UICONTROL Encryption]**

   Type gekozen codering tussen **[!UICONTROL None]** of **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

   Om te weten waar te vinden uw **[!UICONTROL Access key]**, verwijzen naar [page](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
