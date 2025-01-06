---
product: campaign
title: Externe accounts
description: Meer informatie over het maken van externe accounts
feature: Installation, Application Settings, External Account
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1784'
ht-degree: 7%

---

# Externe accounts{#external-accounts}

Adobe Campaign wordt geleverd met een set vooraf gedefinieerde externe accounts. Als u verbindingen met externe systemen wilt instellen, kunt u nieuwe externe accounts maken.

Externe accounts worden gebruikt door technische processen, zoals technische workflows of workflows voor campagnes. Als u bijvoorbeeld een bestandsoverdracht instelt in een workflow of een gegevensuitwisseling met een andere toepassing (Adobe Target, Experience Manager, enzovoort), moet u een externe account selecteren.

## Een externe account maken {#creating-an-external-account}

Voer de onderstaande stappen uit om een nieuwe externe account te maken. Gedetailleerde instellingen zijn afhankelijk van het type externe account.

1. Selecteer in Campagne **[!UICONTROL Explorer]** de optie **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]** .

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

### Stuitberichten {#bounce-mails-external-account}

De **Stuits post** externe rekening specificeert de externe POP3 rekening die moet worden gebruikt om met de e-maildienst te verbinden. Voor meer op deze externe rekening, verwijs naar deze [ pagina ](../../workflow/using/inbound-emails.md).

Alle servers die voor POP3 toegang worden gevormd kunnen worden gebruikt om terugkeerpost te ontvangen.

![](assets/ext_account_6.png)

U configureert als volgt de externe account van **[!UICONTROL Bounce mails (defaultPopAccount)]** :

* **[!UICONTROL Server]**

  URL van de POP3-server.

* **[!UICONTROL Port]**

  POP3-poortnummer van verbinding. De standaardpoort is 10.

* **[!UICONTROL Account]**

  Naam van de gebruiker.

* **[!UICONTROL Password]**

  Wachtwoord voor gebruikersaccount.

* **[!UICONTROL Encryption]**

  Type gekozen codering tussen **[!UICONTROL By default]** , **[!UICONTROL POP3 + STARTTLS]** , **[!UICONTROL POP3]** of **[!UICONTROL POP3S]** .

* **[!UICONTROL Function]**

  Binnenkomende e-mail of SOAP router

>[!IMPORTANT]
>
>Voordat u uw POP3-externe account configureert met Microsoft OAuth 2.0, moet u uw toepassing eerst registreren in de Azure-portal. Raadpleeg [deze pagina](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app) voor meer informatie.

Om POP3 extern te vormen gebruikend **Microsoft OAuth 2.0**, controleer de **[!UICONTROL Microsoft OAuth 2.0]** optie en vul de volgende gebieden in:

* **[!UICONTROL Azure tenant]**

  Azure identiteitskaart (of identiteitskaart van de Folder (huurder)) kan in de **drop-down van de Hoofdzaak** van uw toepassingsoverzicht in het Azure portaal worden gevonden.

* **[!UICONTROL Azure Client ID]**

  Identiteitskaart van de cliënt (of identiteitskaart van de Toepassing (cliënt) kan in **Hoofdzaak** drop-down van uw toepassingsoverzicht in het Azure portaal worden gevonden.

* **[!UICONTROL Azure Client secret]**

  Identiteitskaart van het geheim van de cliënt kan in de **geheimen van de Cliënt** kolom van het **Certificaten &amp; geheimen** menu van uw toepassing in het Azure portaal worden gevonden.

* **[!UICONTROL Azure Redirect URL]**

  Redirect URL kan in het **menu van de Authentificatie** van uw toepassing in het Azure portaal worden gevonden. Deze moet eindigen met de volgende syntaxis `nl/jsp/oauth.jsp`, bijvoorbeeld `https://redirect.adobe.net/nl/jsp/oauth.jsp` .

Internettoegang is nodig om de knop **[!UICONTROL Test Connection]** in de clientconsole in te stellen en te gebruiken. Na installatie kan het InMail-proces zonder internet communiceren met Microsoft-servers.

Nadat u de verschillende referenties hebt ingevoerd, kunt u op **[!UICONTROL Setup the connection]** klikken om de configuratie van uw externe account te voltooien.

### Routering{#routing-external-account}

Met de externe account van **[!UICONTROL Routing]** kunt u elk kanaal dat beschikbaar is in Adobe Campaign configureren, afhankelijk van de geïnstalleerde pakketten.

![](assets/ext_account_7.png)

De volgende kanalen kunnen worden gevormd:

* [Email](#email-routing-external-account)
* [Mobile (SMS)](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [Telefoon](../../delivery/using/communication-channels.md#other-channels)
* [Direct mail](../../delivery/using/about-direct-mail-channel.md)
* [Bureau](../../delivery/using/communication-channels.md#other-channels)
* [X (voorheen bekend als Twitter)](../../social/using/about-social-marketing.md)
* [iOS-kanaal](../../delivery/using/configuring-the-mobile-application.md)
* [Android-kanaal](../../delivery/using/configuring-the-mobile-application-android.md)

### E-mailroutering {#email-routing-external-account}

De e-mail die externe rekening verplettert wordt verstrekt door gebrek, aangepast aan uw configuratie.

Als klant op locatie/hybride, kunt u nieuwe verpletterende externe rekeningen, of updateparameters tot stand brengen, zoals hieronder beschreven. Deze configuratie is gereserveerd voor deskundige gebruikers en kan van invloed zijn op uw prestaties. Neem voor alle vragen contact op met de klantenservice van de Adobe of met uw Adobe.

* U kunt a **gebruiken midsourcing**, **Extern** verpletterend, of **Bulk** levering die type verplettert.

* Voor **Bulk** en **Midden-sourcing** leveringswijzen, kunt u uw brandende parameters in het **Brandend** lusje specificeren. Deze parameters worden gebruikt om de [ standaardparameters ](../../installation/using/deploying-an-instance.md#email-channel-parameters) voor **spiegel pagina URL** en **adres van de Fout** met montages met voeten te treden specifiek voor uw merk.

  ![](assets/ext-account-branding.png)

* Om een Midden-sourcing externe rekening te vormen, verwijs naar [ deze sectie ](mid-sourcing-server.md)

### Uitvoeringsinstantie  {#execution-instance-external-account}

Als u een opgesplitste architectuur hebt, moet u de uitvoeringsinstanties specificeren verbonden aan de controleinstantie en hen verbinden. Transactionele berichtmalplaatjes worden opgesteld aan de uitvoeringsinstantie.

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

  URL van de server waarop de uitvoeringsinstantie is geïnstalleerd.

* **[!UICONTROL Account]**

  Naam van de rekening, moet het de Agent van het Centrum van het Bericht aanpassen zoals die in de exploitantomslag wordt bepaald.

* **[!UICONTROL Password]**

  Wachtwoord van de account zoals gedefinieerd in de map met operatoren.

Voor meer informatie over deze configuratie, verwijs naar deze [ pagina ](../../message-center/using/configuring-instances.md#control-instance).

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

  Type gekozen codering tussen **[!UICONTROL None]** of **[!UICONTROL SSL]** .

Om te weten waar te om van deze geloofsbrieven de plaats te bepalen, verwijs naar deze [ pagina ](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

### SFTP {#sftp-external-account}

Met de externe SFTP-account kunt u toegang tot een server buiten Adobe Campaign configureren en testen. Als u verbindingen wilt instellen met externe systemen, zoals SFTP, die worden gebruikt voor bestandsoverdracht, kunt u uw eigen externe accounts maken. Raadpleeg [deze pagina](../../workflow/using/file-transfer.md) voor meer informatie.

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

  URL van de SFTP-server.

* **[!UICONTROL Port]**

  FTP-poortnummer. De standaardpoort is 22.

* **[!UICONTROL Account]**

  Accountnaam gebruikt voor verbinding met de SFTP-server.

* **[!UICONTROL Password]**

  Wachtwoord gebruikt om verbinding te maken met de SFTP-server.

<!--To add SSH keys on Windows:

1. Create the **HOME** environment variable with value set as the installation directory.

2. Add your private key to the `/$HOME/.ssh/id_rsa` folder.

3. Restart the Adobe Campaign services.
-->

### Externe database (FDA) {#external-database-external-account}

Gebruik het **Externe gegevensbestand** type externe rekening om met extern een gegevensbestand te verbinden. Leer meer over de Federatieve optie van de Toegang van Gegevens (FDA) in [ deze sectie ](../../installation/using/about-fda.md).

De externe gegevensbestanden compatibel met Campagne zijn vermeld in de [ matrijs van de Verenigbaarheid ](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

De instellingen voor externe accountconfiguratie zijn afhankelijk van de database-engine. Meer informatie vindt u in de volgende secties:

* Vorm toegang tot [ Vertica analytics ](../../installation/using/configure-fda-vertica.md)
* Vorm toegang tot [ Snowflake ](../../installation/using/configure-fda-snowflake.md)
* Vorm toegang tot [ Google BigQuery ](../../installation/using/configure-fda-google-big-query.md)
* Vorm toegang tot [ Azure synapse ](../../installation/using/configure-fda-synapse.md)
* Vorm toegang tot [ Hadoop ](../../installation/using/configure-fda-hadoop.md)
* Vorm toegang tot [ Oracle ](../../installation/using/configure-fda-oracle.md)
* Vorm toegang tot [ Netezza ](../../installation/using/configure-fda-netezza.md)
* Vorm toegang tot [ SAP HANA ](../../installation/using/configure-fda-sap-hana.md)
* Vorm toegang tot [ Snowflake ](../../installation/using/configure-fda-snowflake.md)
* Vorm toegang tot [ Sybases IQ ](../../installation/using/configure-fda-sybase.md)
* Vorm toegang tot [ Teradata ](../../installation/using/configure-fda-teradata.md)


## Integratie externe accounts van oplossing voor Adobe

### Adobe Experience Cloud {#adobe-experience-cloud-external-account}

Als u verbinding wilt maken met de Adobe Campaign-console met een Adobe ID, moet u de **[!UICONTROL Adobe Experience Cloud (MAC)]** -externe account configureren.

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

  Id van uw organisatie. Om uw organisatieidentiteitskaart te vinden, verwijs naar [ deze pagina ](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=nl) {_blank}.

* **[!UICONTROL Association mask]**

  Syntaxis waarmee configuratienamen in Enterprise-dashboard kunnen worden gesynchroniseerd met de groepen in Adobe Campaign.

* **[!UICONTROL Server]**

  URL van je Adobe Experience Cloud-exemplaar.

* **[!UICONTROL Tenant]**

  Naam van je Adobe Experience Cloud Tenant.

Voor meer informatie over deze configuratie, verwijs naar [ deze pagina ](../../integrations/using/configuring-ims.md).

## Webanalyse {#web-analytics-external-account}

Met de externe account van **[!UICONTROL Web Analytics]** kunt u gegevens van Adobe Analytics naar Adobe Campaign doorsturen in de vorm van segmenten. Omgekeerd verzendt het programma indicatoren en kenmerken van e-mailcampagnes die door Adobe Campaign aan Adobe Analytics-connector worden geleverd.

![](assets/ext_account_10.png)

Voor deze externe account moet de berekeningsformule voor bijgehouden URL&#39;s worden verrijkt en moet de verbinding tussen de twee oplossingen worden goedgekeurd. Raadpleeg [deze pagina](../../integrations/using/gs-aa.md) voor meer informatie.

### Adobe Experience Manager {#adobe-experience-manager-external-account}

Met het externe account van **[!UICONTROL AEM (AEM instance)]** kunt u de inhoud van uw e-mailleveringen en uw formulieren rechtstreeks in Adobe Experience Manager beheren.

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

  URL van de Adobe Experience Manager-server.

* **[!UICONTROL Port]**

  Accountnaam gebruikt om verbinding te maken met de Adobe Experience Manager-ontwerpinstantie.

* **[!UICONTROL Password]**

  Wachtwoord waarmee verbinding wordt gemaakt met de Adobe Experience Manager-ontwerpinstantie.

Raadpleeg deze [sectie](../../integrations/using/about-adobe-experience-manager.md) voor meer informatie.

## Externe CRM-connectorrekeningen

### MICROSOFT DYNAMICS CRM {#microsoft-dynamics-crm-external-account}

>[!NOTE]
>
> De implementatietypen **[!UICONTROL On-premise]** en **[!UICONTROL Office 365]** zijn nu vervangen. [Meer informatie](../../rn/using/deprecated-features.md).

Met de externe account van **[!UICONTROL Microsoft Dynamics CRM]** kunt u Microsoft Dynamics-gegevens importeren en exporteren naar Adobe Campaign.

Leer meer over Campagne - de schakelaar van Microsoft Dynamics CRM in deze [ pagina ](../../platform/using/crm-ms-dynamics.md).

Bij het **[!UICONTROL Web API]** implementatietype en **[!UICONTROL Password credentials]** -verificatie moet u de volgende gegevens opgeven:

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

  Account gebruikt voor aanmelden bij Microsoft CRM.

* **[!UICONTROL Server]**

  URL van uw Microsoft CRM-server.

  Om uw Microsoft CRM **[!UICONTROL Server URL]** te vinden, toegang tot uw rekening van Microsoft Dynamics CRM dan klik **Dynamiek 365** en selecteer uw app. U kunt de **[!UICONTROL Server URL]** vervolgens vinden in de adresbalk van uw browser, bijvoorbeeld `https://myserver.crm.dynamics.com/` .

* **[!UICONTROL Client identifier]**

  Client-id die u kunt vinden via de Microsoft Azure-beheerportal in het veld **[!UICONTROL Update your code]** category **[!UICONTROL Client ID]** .

* **[!UICONTROL CRM version]**

  Kies **[!UICONTROL Dynamics CRM 365]** CRM-versie.

Bij het **[!UICONTROL Web API]** implementatietype en **[!UICONTROL Certificate]** -verificatie moet u de volgende gegevens opgeven:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

  URL van uw Microsoft CRM-server.

  Om uw Microsoft CRM **[!UICONTROL Server URL]** te vinden, toegang tot uw rekening van Microsoft Dynamics CRM dan klik **Dynamiek 365** en selecteer uw app. U kunt de **[!UICONTROL Server URL]** vervolgens vinden in de adresbalk van uw browser, bijvoorbeeld `https://myserver.crm.dynamics.com/` .

* **[!UICONTROL Private Key (Base64 encoded)]**

  Merk op dat de Privé sleutel aan Base64 moet worden gecodeerd.

  Hiertoe kunt u de hulp van een Base64-encoder gebruiken of de opdrachtregel `base64 -w0 private.key` voor Linux.

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

  Client-id die u kunt vinden via de Microsoft Azure-beheerportal in het veld **[!UICONTROL Update your code]** category **[!UICONTROL Client ID]** .

* **[!UICONTROL CRM version]**

  Versie van de CRM tussen **[!UICONTROL Dynamics CRM 2007]** , **[!UICONTROL Dynamics CRM 2015]** of **[!UICONTROL Dynamics CRM 2016]** .

Voor meer informatie over deze configuratie, verwijs naar deze [ pagina ](../../platform/using/crm-connectors.md).

### Salesforce.com CRM  {#salesforce-crm-external-account}

Met de externe account van **[!UICONTROL Salesforce CRM]** kunt u Salesforce-gegevens importeren en exporteren naar Adobe Campaign.

![](assets/ext_account_17.png)

Als u de externe Salesforce CRM-account wilt configureren voor Adobe Campaign, moet u de volgende gegevens opgeven:

* **[!UICONTROL Account]**

  Account gebruikt voor aanmelden bij Salesforce CRM.

* **[!UICONTROL Password]**

  Wachtwoord gebruikt om u aan te melden bij Salesforce CRM.

* **[!UICONTROL Client identifier]**

  Om te weten waar te om uw cliëntherkenningsteken te vinden, verwijs naar deze [ pagina ](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security token]**

  Om te weten waar te om uw veiligheidstoken te vinden, verwijs naar deze [ pagina ](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API version]**

  Selecteer de versie van de API.

Voor deze externe rekening, moet u u Salesforce CRM met de configuratiemedewerker vormen.

Voor meer informatie over deze configuratie, verwijs naar deze [ pagina ](../../platform/using/crm-connectors.md).

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

  Om te weten waar te om uw AWS toegangs belangrijkste identiteitskaart te vinden, verwijs naar deze [ pagina ](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

* **[!UICONTROL Secret access key to AWS]**

  Om te weten waar te om uw geheime toegangstoets aan AWS te vinden, verwijs naar deze [ pagina ](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS Region]**

  Om meer op het gebied van AWS te leren, verwijs naar deze [ pagina ](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* Met het selectievakje **[!UICONTROL Use server side encryption]** kunt u het bestand opslaan in de modus S3-versleuteling.

Leren waar te om toegangs zeer belangrijke identiteitskaart en geheime toegangssleutel te vinden, verwijs naar de diensten van het Web van Amazon [ documentatie ](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

### Azure Blob Storage {#azure-blob-external-account}

De **Azure Blob opslag** externe rekening kan worden gebruikt om gegevens in te voeren of naar Adobe Campaign uit te voeren gebruikend een **[!UICONTROL Transfer file]** werkschemaactiviteit. Raadpleeg deze [sectie](../../workflow/using/file-transfer.md) voor meer informatie.

![](assets/ext_account_23.png)

Als u **[!UICONTROL Azure external account]** wilt configureren om te werken met Adobe Campaign, moet u de volgende gegevens opgeven:

* **[!UICONTROL Server]**

  URL van uw Azure Blob-opslagserver.

* **[!UICONTROL Encryption]**

  Type gekozen codering tussen **[!UICONTROL None]** of **[!UICONTROL SSL]** .

* **[!UICONTROL Access key]**

  Om te weten waar te om uw **[!UICONTROL Access key]** te vinden, verwijs naar deze [ pagina ](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
