---
product: campaign
title: Externe accounts
description: Meer informatie over het maken van externe accounts
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: 7adde72f615e7c697fa2284235e180c29bc6d470
workflow-type: tm+mt
source-wordcount: '1636'
ht-degree: 7%

---

# Externe accounts{#external-accounts}

Adobe Campaign wordt geleverd met een set vooraf gedefinieerde externe accounts. Als u verbindingen met externe systemen wilt instellen, kunt u nieuwe externe accounts maken.

Externe accounts worden gebruikt door technische processen, zoals technische workflows of workflows voor campagnes. Als u bijvoorbeeld een bestandsoverdracht instelt in een workflow of een gegevensuitwisseling met een andere toepassing (Adobe Target, Experience Manager, enzovoort), moet u een externe account selecteren.

## Een externe account maken {#creating-an-external-account}

Voer de onderstaande stappen uit om een nieuwe externe account te maken. Gedetailleerde instellingen zijn afhankelijk van het type externe account.

1. Selecteer **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**&#39; in Campagne **[!UICONTROL Explorer]**.

   ![](assets/ext_account_1.png)

1. Klik op de knop **[!UICONTROL New]**.

   ![](assets/ext_account_2.png)

1. Voer een **[!UICONTROL Label]** en een **[!UICONTROL Internal Name]** in.
1. Selecteer uw externe account **[!UICONTROL Type]** die u wilt maken.
1. Configureer de toegang tot de account door referenties op te geven, afhankelijk van het gekozen type externe account.

   De benodigde informatie wordt meestal verstrekt door de provider van de server waarmee u verbinding maakt.

1. Schakel de optie **[!UICONTROL Enabled]** in om de verbinding te activeren.
1. Klik op **[!UICONTROL Save]**.

De externe account wordt gemaakt en toegevoegd aan de lijst met externe accounts.

## Campagne-specifieke externe rekeningen

### Niet bezorgde mails {#bounce-mails-external-account}

Met de externe account **Bounce mails** wordt de externe POP3-account opgegeven die moet worden gebruikt om verbinding te maken met de e-mailservice. Raadpleeg deze [pagina](../../workflow/using/inbound-emails.md) voor meer informatie over deze externe account.

Alle servers die voor POP3 toegang worden gevormd kunnen worden gebruikt om terugkeerpost te ontvangen.

![](assets/ext_account_6.png)

Om de **[!UICONTROL Bounce mails (defaultPopAccount)]** externe rekening te vormen:

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

Met de externe account **[!UICONTROL Routing]** kunt u elk kanaal dat beschikbaar is in Adobe Campaign configureren, afhankelijk van de geïnstalleerde pakketten.

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

Voor meer informatie over deze configuratie, verwijs naar deze [pagina](../../message-center/using/configuring-instances.md#control-instance).

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

   Type van gekozen encryptie tussen **[!UICONTROL None]** of **[!UICONTROL SSL]**.

Om te weten waar te om van deze geloofsbrieven de plaats te bepalen, verwijs naar deze [pagina](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

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

Gebruik de **External database** type external account om verbinding te maken met een externe database. Meer informatie over de optie Federated Data Access (FDA) in [deze sectie](../../installation/using/about-fda.md).

Externe databases die compatibel zijn met Campagne worden vermeld in de [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

De instellingen voor externe accountconfiguratie zijn afhankelijk van de database-engine. Meer informatie vindt u in de volgende secties:

* Toegang tot [Vertica](../../installation/using/configure-fda-vertica.md) configureren
* Toegang tot [Snowflake](../../installation/using/configure-fda-snowflake.md) configureren
* Toegang tot [Google BigQuery](../../installation/using/configure-fda-google-big-query.md) configureren
* Toegang tot [Azure synapse](../../installation/using/configure-fda-synapse.md) configureren
* Toegang tot [Hadoop](../../installation/using/configure-fda-hadoop.md) configureren
* Toegang tot [Oracle](../../installation/using/configure-fda-oracle.md) configureren
* Toegang tot [Netezza](../../installation/using/configure-fda-netezza.md) configureren
* Toegang tot [SAP HANA](../../installation/using/configure-fda-sap-hana.md) configureren
* Toegang tot [Snowflake](../../installation/using/configure-fda-snowflake.md) configureren
* Toegang tot [Sybase IQ](../../installation/using/configure-fda-sybase.md) configureren
* Toegang tot [Teradata](../../installation/using/configure-fda-teradata.md) configureren

### Facebook connect {#facebook-connect-external-account}

Met de externe account **[!UICONTROL Facebook Connect]** kunt u gepersonaliseerde inhoud weergeven in uw Facebook-toepassingen, waardoor het eenvoudiger wordt om vooruitzichten te krijgen via dit sociale netwerk.

Voor elke Facebook-toepassing moet u een externe account van het type **[!UICONTROL Facebook Connect]** maken. Raadpleeg [page](../../social/using/creating-a-facebook-application.md#configuring-external-accounts) voor meer informatie.

![](assets/ext_account_12.png)

* **[!UICONTROL Hosting mode]**

   Hosting mode of the application between **[!UICONTROL hosted by a partner]** or **[!UICONTROL hosted by this instance]**.

* **[!UICONTROL Application ID]**

   Toepassings-id van uw Facebook-toepassing.

* **[!UICONTROL Application secret]**

   Toepassingsgeheim van uw Facebook-toepassing.

Als u de host kiest voor deze instantiemodus, moet de URL van het beveiligde canvas worden geplakt in het veld **Facebook-webgames (https)** op Facebook

Om te weten waar te om van deze geloofsbrieven de plaats te bepalen, verwijs naar deze [pagina](https://developers.facebook.com/docs/facebook-login/access-tokens).

## Adobe Oplossing integratie externe accounts

### Adobe Experience Cloud {#adobe-experience-cloud-external-account}

Als u verbinding wilt maken met de Adobe Campaign-console met een Adobe ID, moet u de externe account **[!UICONTROL Adobe Experience Cloud (MAC)]** configureren.

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

   ID van uw IMS-organisatie. Als u uw organisatie-id wilt zoeken, raadpleegt u [deze pagina](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html) (**Waar kan ik mijn IMS-organisatie-id vinden?**).

* **[!UICONTROL Association mask]**

   Syntaxis waarmee configuratienamen in Enterprise-dashboard kunnen worden gesynchroniseerd met de groepen in Adobe Campaign.

* **[!UICONTROL Server]**

   URL van je Adobe Experience Cloud-exemplaar.

* **[!UICONTROL Tenant]**

   Naam van je Adobe Experience Cloud Tenant.

Raadpleeg [deze pagina](../../integrations/using/configuring-ims.md) voor meer informatie over deze configuratie.

## Web Analytics {#web-analytics-external-account}

Met de externe account **[!UICONTROL Web Analytics]** kunt u gegevens van Adobe Analytics naar Adobe Campaign doorsturen in de vorm van segmenten. Omgekeerd verzendt het programma indicatoren en kenmerken van e-mailcampagnes die door Adobe Campaign aan Adobe Analytics-connector worden geleverd.

![](assets/ext_account_10.png)

Voor deze externe account moet de berekeningsformule voor bijgehouden URL&#39;s worden verrijkt en moet de verbinding tussen de twee oplossingen worden goedgekeurd. Raadpleeg [deze pagina](../../platform/using/adobe-analytics-connector.md#external-account-classic) voor meer informatie.

### Adobe Experience Manager {#adobe-experience-manager-external-account}

Met de externe account **[!UICONTROL AEM (AEM instance)]** kunt u de inhoud van uw e-mailleveringen en uw formulieren rechtstreeks in Adobe Experience Manager beheren.

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
> **[!UICONTROL On-premise]** en de  **[!UICONTROL Office 365]** plaatsingstypes zijn nu verouderd. [Meer info](../../rn/using/deprecated-features.md).

Met de externe account **[!UICONTROL Microsoft Dynamics CRM]** kunt u Microsoft Dynamics-gegevens importeren en exporteren naar Adobe Campaign.

Meer informatie over Campagne - de schakelaar van CRM van de Dynamica van Microsoft in deze [pagina](../../platform/using/crm-ms-dynamics.md).

Met **[!UICONTROL Web API]** plaatsingstype en **[!UICONTROL Password credentials]** authentificatie, moet u de volgende details verstrekken:

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   Account gebruikt om u aan te melden bij Microsoft CRM.

* **[!UICONTROL Server]**

   URL van uw Microsoft CRM-server.

   Als u uw Microsoft CRM **[!UICONTROL Server URL]** wilt zoeken, opent u uw Microsoft Dynamics CRM-account en klikt u op **Dynamics 365** en selecteert u uw app. U kunt uw **[!UICONTROL Server URL]** in de adresbar van uw browser dan vinden, b.v. `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Client identifier]**

   Client-id die u kunt vinden op de Microsoft Azure-beheerportal in het veld **[!UICONTROL Update your code]**.**[!UICONTROL Client ID]**

* **[!UICONTROL CRM version]**

   Kies **[!UICONTROL Dynamics CRM 365]** versie van CRM.

Met **[!UICONTROL Web API]** plaatsingstype en **[!UICONTROL Certificate]** authentificatie, moet u de volgende details verstrekken:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   URL van uw Microsoft CRM-server.

   Als u uw Microsoft CRM **[!UICONTROL Server URL]** wilt zoeken, opent u uw Microsoft Dynamics CRM-account en klikt u op **Dynamics 365** en selecteert u uw app. U kunt uw **[!UICONTROL Server URL]** in de adresbar van uw browser dan vinden, b.v. `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Private Key (Base64 encoded)]**

   Merk op dat de Privé sleutel aan Base64 moet worden gecodeerd.

   Om dit te doen, kunt u de hulp van een Codeur gebruiken Base64 of de bevellijn `base64 -w0 private.key` voor Linux gebruiken.

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   Client-id die u kunt vinden op de Microsoft Azure-beheerportal in het veld **[!UICONTROL Update your code]**.**[!UICONTROL Client ID]**

* **[!UICONTROL CRM version]**

   Versie van de CRM tussen **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** of **[!UICONTROL Dynamics CRM 2016]**.

Voor meer informatie over deze configuratie, verwijs naar deze [pagina](../../platform/using/crm-connectors.md).

### Salesforce.com CRM  {#salesforce-crm-external-account}

Met de externe account **[!UICONTROL Salesforce CRM]** kunt u Salesforce-gegevens importeren en exporteren naar Adobe Campaign.

![](assets/ext_account_17.png)

Om de externe rekening van Salesforce CRM te vormen om met Adobe Campaign te werken, moet u de volgende details verstrekken:

* **[!UICONTROL Account]**

   Account gebruikt om u aan te melden bij Salesforce CRM.

* **[!UICONTROL Password]**

   Wachtwoord gebruikt om u aan te melden bij Salesforce CRM.

* **[!UICONTROL Client identifier]**

   Als u wilt weten waar de client-id moet worden gevonden, raadpleegt u deze [pagina](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security token]**

   Om te weten waar te om uw veiligheidstoken te vinden, verwijs naar dit [pagina](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API version]**

   Selecteer de versie van de API.

Voor deze externe rekening, moet u u Salesforce CRM met de configuratietovenaar vormen.

Voor meer informatie over deze configuratie, verwijs naar deze [pagina](../../platform/using/crm-connectors.md).

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

   Om te weten waar te om uw AWS toegangs belangrijkste identiteitskaart te vinden, verwijs naar deze [pagina](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

* **[!UICONTROL Secret access key to AWS]**

   Om te weten waar te om uw geheime toegangssleutel aan AWS te vinden, verwijs naar deze [pagina](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS Region]**

   Voor meer informatie over AWS-gebied raadpleegt u deze [pagina](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* Met het selectievakje **[!UICONTROL Use server side encryption]** kunt u het bestand opslaan in de gecodeerde modus van S3.

Om te leren waar te om toegangs belangrijkste identiteitskaart en geheime toegangssleutel te vinden, verwijs naar de diensten [documentatie](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) van het Web van Amazon.

### Azure Blob Storage {#azure-blob-external-account}

De externe account **Azure Blob storage** kan worden gebruikt voor het importeren of exporteren van gegevens naar Adobe Campaign met behulp van een **[!UICONTROL Transfer file]**-workflowactiviteit. Raadpleeg deze [sectie](../../workflow/using/file-transfer.md) voor meer informatie.

![](assets/ext_account_23.png)

Als u **[!UICONTROL Azure external account]** wilt configureren om met Adobe Campaign te werken, moet u de volgende gegevens opgeven:

* **[!UICONTROL Server]**

   URL van uw Azure Blob-opslagserver.

* **[!UICONTROL Encryption]**

   Type van gekozen encryptie tussen **[!UICONTROL None]** of **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

   Om te weten waar te om uw **[!UICONTROL Access key]** te vinden, verwijs naar deze [pagina](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
