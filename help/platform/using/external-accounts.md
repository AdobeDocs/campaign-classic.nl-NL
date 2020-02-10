---
title: Externe rekeningen
seo-title: Externe rekeningen
description: Externe rekeningen
seo-description: null
page-status-flag: never-activated
uuid: e06e7a36-b449-4ab0-a4f6-fa82dbb8de11
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: da60b9ca-4b51-4bff-affc-2b12c576973a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6ae45cbd87fc0152fc654202e03501fc8d2abd06

---


# Externe rekeningen{#external-accounts}

Een externe account is een configuratie waarmee u de toegang tot een externe server van Adobe Campaign kunt configureren en testen. Deze externe accounts kunnen in Campagneworkflows worden gebruikt voor toegang tot en beheer van gegevens.

U kunt de volgende typen externe accounts instellen:

* [Externe account routeren](#routing-external-account)
* [Externe FTP-account](#ftp-external-account)
* [Externe externe database-account](#external-database-external-account)
* [Externe account voor webanalyse](#web-analytics-external-account)
* [Externe account voor Facebook connect](#facebook-connect-external-account)
* [Uitvoerinstantie externe account](#execution-instance-external-account)
* [Externe account voor Adobe Experience Cloud](#adobe-experience-cloud-external-account)
* [Externe SFTP-account](#sftp-external-account)
* [Externe account voor Adobe Experience Manager](#adobe-experience-manager-external-account)
* [Amazon Simple Storage Service (S3) externe account](#amazon-simple-storage-service--s3--external-account)
* [Azure External Account](#azure-external-account)
* [Externe rekening](#hadoop-external-account)
* [Externe account voor Microsoft Dynamics CRM](#microsoft-dynamics-crm-external-account)
* [Oracle op verzoek externe account](#oracle-on-demand-external-account)
* [Externe rekening Salesforce CRM](#salesforce-crm-external-account)

## Een externe account maken {#creating-an-external-account}

Adobe Campagne wordt geleverd met een set vooraf gedefinieerde externe accounts. Als u verbindingen wilt instellen met externe systemen, zoals FTP-servers die worden gebruikt voor bestandsoverdracht, kunt u uw eigen externe accounts maken.

Externe accounts worden gebruikt door technische processen, zoals technische workflows of workflows voor campagnes. Wanneer u een bestandsoverdracht instelt in een workflow of een gegevensuitwisseling met een andere toepassing (Adobe Target, Experience Manager, enz.), moet u een externe account selecteren.

1. Maak het **[!UICONTROL Explorer]** menu los van het **[!UICONTROL Administration]** menu.
1. Ontgrendel het **[!UICONTROL Platform]** menu en klik **[!UICONTROL External accounts]**.

   ![](assets/ext_account_1.png)

1. Klik op de **[!UICONTROL New]** knop.

   ![](assets/ext_account_2.png)

1. Voer een **[!UICONTROL Label]** en **[!UICONTROL Internal Name]**. Beide worden gebruikt bij het selecteren van externe accounts in workflows.
1. Controleer **[!UICONTROL Enabled]** of u de verbinding wilt inschakelen.
1. Selecteer de externe account **[!UICONTROL Type]** die u wilt maken.
1. Configureer de toegang tot de account door referenties op te geven, afhankelijk van het gekozen type externe account.

   De noodzakelijke informatie wordt gewoonlijk verstrekt door de leverancier van de server u met verbindt.

1. Klik **[!UICONTROL Save]**.

De externe account wordt gemaakt en toegevoegd aan de lijst met externe accounts. Het is nu beschikbaar voor uw gegevens/dossier overdrachten of het verpletteren van configuraties in werkschemaactiviteiten en leveringseigenschappen.

## Externe account voor stuiterende berichten {#bounce-mails-external-account}

Met de externe account **Bounce mails** wordt de externe POP3-account opgegeven die moet worden gebruikt om verbinding te maken met de e-mailservice. Raadpleeg deze [pagina](../../workflow/using/inbound-emails.md)voor meer informatie over deze externe account.

Alle servers die voor POP3 toegang worden gevormd kunnen worden gebruikt om terugkeerpost te ontvangen.

![](assets/ext_account_6.png)

De **[!UICONTROL Bounce mails (defaultPopAccount)]** externe account configureren:

* **[!UICONTROL Server]**

   URL van de POP3-server.

* **[!UICONTROL Port]**

   POP3-poortnummer van verbinding. De standaardpoort is 110.

* **[!UICONTROL Account]**

   Naam van de gebruiker.

* **[!UICONTROL Password]**

   Wachtwoord voor gebruikersaccount.

* **[!UICONTROL Encryption]**

   Type van gekozen encryptie tussen **[!UICONTROL By default]**, **[!UICONTROL POP3 + STARTTLS]**, **[!UICONTROL POP3]** of **[!UICONTROL POP3S]**.

## Externe account routeren {#routing-external-account}

Met de **[!UICONTROL Routing]** externe account kunt u elk kanaal configureren dat beschikbaar is in Adobe Campaign, afhankelijk van de geïnstalleerde pakketten.

![](assets/ext_account_7.png)

De volgende kanalen kunnen worden gevormd:

* [E-mail](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [Mobiel (SMS)](../../delivery/using/sms-channel.md#activating-an-external-account).
* [Telefoon](../../delivery/using/other-channels.md)
* [Direct mail](../../delivery/using/about-direct-mail-channel.md)
* [Bureau](../../delivery/using/other-channels.md)
* [Facebook](../../social/using/publishing-on-facebook-walls.md#delegating-write-access-to-adobe-campaign)
* [Twitter](../../social/using/configuring-publishing-on-twitter.md)
* [iOS-kanaal](../../delivery/using/setting-up-mobile-app-channel.md#ios-connectors)
* [Android-kanaal](../../delivery/using/setting-up-mobile-app-channel.md#android-connectors)

## Externe FTP-account {#ftp-external-account}

Met de externe FTP-account kunt u de toegang tot een server buiten Adobe Campaign configureren en testen. Als u verbindingen wilt instellen met externe systemen, zoals FTP-servers 898 die worden gebruikt voor bestandsoverdracht, kunt u uw eigen externe accounts maken. Raadpleeg deze [pagina](../../workflow/using/file-transfer.md)voor meer informatie.

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

   Type gekozen encryptie tussen **[!UICONTROL None]** of **[!UICONTROL SSL]**.

Op deze [pagina](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials)vindt u de locatie van deze referenties.

## Externe externe database-account {#external-database-external-account}

De Campagne van Adobe verstrekt verscheidene schakelaars die u toestaan om met externe toepassingen te communiceren en met gegevensbestandmotoren te verbinden.

![](assets/ext_account_11.png)

De volgende verbindingstypen kunnen worden geconfigureerd:

* Oracle. Raadpleeg deze [pagina](../../platform/using/accessing-an-external-database.md#configure-access-to-oracle)voor meer informatie.
* MySQL. Raadpleeg deze [pagina](../../platform/using/accessing-an-external-database.md#configure-access-to-mysql)om toegang tot MYSQL te configureren.
* Netezza. Raadpleeg deze [pagina](../../platform/using/accessing-an-external-database.md#configure-access-to-netezza)voor meer informatie.
* SAP HANA. Raadpleeg deze [pagina](../../platform/using/accessing-an-external-database.md#configure-access-to-sap-hanaa)voor meer informatie.
* InfiniDB
* Microsoft SQL-server
* AsterData
* PostgreSQL
* TeraData
* DB2
* Amazon Redshift
* ODBC (Sybase ASE, Sybase IQ)
* HTTP-relais naar externe database

### Externe rekening met teragegevens {#teradata-external-account}

Met de externe **account van de Teradata** kunt u uw Campagne-instantie verbinden met uw externe database van Teradata. Raadpleeg deze [pagina](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html) of deze [sectie](../../platform/using/accessing-an-external-database.md#configure-access-to-teradata)voor meer informatie over het configureren van Campagne Classic met Teradata.

![](assets/ext_account_19.png)

Als u deze externe account wilt configureren voor gebruik met Adobe Campaign, moet u de volgende gegevens opgeven:

* **[!UICONTROL Type]**

   Kies het **[!UICONTROL Teradata]** type.

* **[!UICONTROL Server]**

   URL of naam van uw Teradata-server.

* **[!UICONTROL Account]**

   Naam van de account die wordt gebruikt voor toegang tot de Teradata-database.

* **[!UICONTROL Password]**

   Wachtwoord gebruikt om verbinding te maken met de Teradata-database.

* **[!UICONTROL Database]**

   Dit veld kan leeg blijven.

* **[!UICONTROL Options]**

   Opties die via metagegevens moeten worden doorgegeven

* **[!UICONTROL Timezone]**

   Tijdzone ingesteld in metagegevens

![](assets/ext_account_20.png)

Wanneer meerdere gebruikers van Adobe Campagne verbinding maken met dezelfde externe FDA-account voor metagegevens, kunt u op het **[!UICONTROL Query banding]** tabblad een queryband instellen, dat wil zeggen een set sleutel-/waardeparen, voor een sessie.

Telkens wanneer een campagnegebruiker een query uitvoert in de Teradata-database, verzendt Adobe Campaign metagegevens die bestaan uit een lijst met sleutels die aan deze gebruiker zijn gekoppeld. Deze gegevens kunnen vervolgens door de gegevensbeheerder van Teradata worden gebruikt voor auditdoeleinden of voor het beheer van toegangsrechten.

Schakel het **[!UICONTROL Active]** selectievakje in om deze functie te activeren

In het **[!UICONTROL Default]** veld kunt u een standaardqueryband invoeren die wordt gebruikt als een gebruiker geen bijbehorende queryband heeft. Als dit veld leeg blijft, kunnen gebruikers zonder queryband geen gebruik maken van metagegevens.

In het **[!UICONTROL Users]** veld kunt u voor elke gebruiker een queryband opgeven. U kunt zoveel sleutel-/waardeparen toevoegen als u nodig hebt, bijvoorbeeld priority=1;workload=high. Als aan de gebruiker geen queryband is toegewezen, wordt het **[!UICONTROL Default]** veld toegepast.

Raadpleeg de documentatie bij **[!UICONTROL Query banding]** de [metagegevens voor meer informatie over](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw)het document.

## Externe account voor webanalyse {#web-analytics-external-account}

Met het **[!UICONTROL Web Analytics (Adobe Analytics - Data connector)]** externe account kunt u gegevens van Adobe Analytics naar Adobe Campaign doorsturen in de vorm van segmenten. Omgekeerd verzendt het programma indicatoren en kenmerken van e-mailcampagnes die door Adobe Campaign worden geleverd naar Adobe Analytics - Data connector.

![](assets/ext_account_10.png)

Voor deze externe account moet de berekeningsformule voor bijgehouden URL&#39;s worden verrijkt en moet de verbinding tussen de twee oplossingen worden goedgekeurd. Raadpleeg deze [pagina](../../platform/using/adobe-analytics-data-connector.md#step-2--create-the-external-account-in-campaign)voor meer informatie.

## Externe account voor Facebook connect {#facebook-connect-external-account}

Met de **[!UICONTROL Facebook Connect]** externe account kunt u persoonlijke inhoud weergeven in uw Facebook-toepassingen, waardoor het eenvoudiger wordt om vooruitzichten te krijgen via dit sociale netwerk.

Voor elke Facebook-toepassing moet u een **[!UICONTROL Facebook Connect]** type extern account maken. Raadpleeg de [pagina](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)voor meer informatie.

![](assets/ext_account_12.png)

* **[!UICONTROL Hosting mode]**

   De hostingmodus van de toepassing tussen **[!UICONTROL hosted by a partner]** of **[!UICONTROL hosted by this instance]**.

* **[!UICONTROL Application ID]**

   Toepassings-id van uw Facebook-toepassing.

* **[!UICONTROL Application secret]**

   Toepassingsgeheim van uw Facebook-toepassing

Als u de host kiest in deze instantiemodus, moet de URL van het beveiligde canvas worden geplakt in het veld **Facebook-webgames (https)** op Facebook

Op deze [pagina](https://developers.facebook.com/docs/facebook-login/access-tokens)vindt u de locatie van deze referenties.

## Uitvoerinstantie externe account {#execution-instance-external-account}

Als u een opgesplitste architectuur hebt, moet u de uitvoeringsinstanties specificeren verbonden aan de controleinstantie en hen verbinden. Transactieberichtsjablonen worden geïmplementeerd in de uitvoeringsinstantie

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   URL van de server waarop de uitvoeringsinstantie is geïnstalleerd.

* **[!UICONTROL Account]**

   Naam van de rekening, moet het de Agent van het Centrum van het Bericht aanpassen zoals die in de exploitantomslag wordt bepaald.

* **[!UICONTROL Password]**

   Wachtwoord van de account zoals gedefinieerd in de map met operatoren.

Raadpleeg deze [pagina](../../message-center/using/creating-a-shared-connection.md#control-instance)voor meer informatie over deze configuratie.

## Externe account voor Adobe Experience Cloud {#adobe-experience-cloud-external-account}

Als u met een Adobe-id verbinding wilt maken met de Adobe Campaign-console, moet u de **[!UICONTROL Adobe Experience Cloud (MAC)]** externe account configureren.

![](assets/ext_account_9.png)

* **[!UICONTROL IMS server]**

   URL van uw IMS-server. Zorg ervoor zowel stadium als de productie instanties aan het zelfde IMS productieeindpunt richten.

* **[!UICONTROL IMS scope]**

   De hier gedefinieerde bereiken moeten een subset zijn van de gebieden die door IMS zijn ingericht.

* **[!UICONTROL IMS client identifier]**

   ID van uw IMS-client.

* **[!UICONTROL IMS client secret]**

   Credentials van uw IMS-clientgeheim

* **[!UICONTROL Callback server]**

   Toegang tot URL van uw Adobe Campaign-exemplaar

* **[!UICONTROL IMS organization ID]**

   ID van uw IMS-organisatie. Raadpleeg deze [pagina](https://marketing.adobe.com/resources/help/en_US/mcloud/faq.html) om uw organisatie-id te zoeken (**Waar vind ik mijn IMS-organisatie-id?**).

* **[!UICONTROL Association mask]**

   Syntaxis waarmee configuratienamen in het Enterprise-dashboard kunnen worden gesynchroniseerd met de groepen in Adobe Campaign.

* **[!UICONTROL Server]**

   URL van uw Adobe Experience Cloud-instantie.

* **[!UICONTROL Tenant]**

   Naam van uw Adobe Experience Cloud Tenant.

Raadpleeg deze [pagina](../../integrations/using/configuring-ims.md)voor meer informatie over deze configuratie.

## Externe SFTP-account {#sftp-external-account}

Met de externe SFTP-account kunt u toegang tot een server buiten Adobe Campaign configureren en testen. Als u verbindingen wilt instellen met externe systemen, zoals SFTP, die worden gebruikt voor bestandsoverdracht, kunt u uw eigen externe accounts maken. Raadpleeg deze [pagina](../../workflow/using/file-transfer.md)voor meer informatie.

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

   URL van de SFTP-server.

* **[!UICONTROL Port]**

   FTP-poortnummer. De standaardpoort is 22.

* **[!UICONTROL Account]**

   Accountnaam gebruikt om verbinding te maken met de SFTP-server.

* **[!UICONTROL Password]**

   Wachtwoord gebruikt om verbinding te maken met de SFTP-server.

## Externe account voor Adobe Experience Manager {#adobe-experience-manager-external-account}

Met het **[!UICONTROL AEM (AEM instance)]** externe account kunt u de inhoud van uw e-mailleveringen en uw formulieren rechtstreeks beheren in Adobe Experience Manager.

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

   URL van de Adobe Experience Manager-server.

* **[!UICONTROL Port]**

   Accountnaam gebruikt om verbinding te maken met de ontwerpinstantie van Adobe Experience Manager.

* **[!UICONTROL Password]**

   Wachtwoord waarmee u verbinding maakt met de ontwerpinstantie van Adobe Experience Manager.

Zie deze [sectie](../../integrations/using/about-adobe-experience-manager.md)voor meer informatie.

## Amazon Simple Storage Service (S3) externe account {#amazon-simple-storage-service--s3--external-account}

De Amazon Simple Storage Service (S3)-connector kan worden gebruikt voor het importeren of exporteren van gegevens naar Adobe Campagne. Deze kan worden ingesteld in een workflowactiviteit. Raadpleeg deze [pagina](../../workflow/using/file-transfer.md)voor meer informatie.

![](assets/ext_account_3.png)

Wanneer u deze nieuwe externe account instelt, moet u de volgende gegevens opgeven:

* **[!UICONTROL AWS S3 Account Server]**

   URL van uw server, zou het als volgt moeten worden gevuld:

   ```
   <S3bucket name>.s3.amazonaws.com/<s3object path>
   ```

* **[!UICONTROL AWS access key ID]**

   Raadpleeg deze [pagina](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) om te weten waar u uw AWS-toegangstoets-id kunt vinden.

* **[!UICONTROL Secret access key to AWS]**

   Raadpleeg deze [pagina](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/)om te weten waar u uw geheime toegangssleutel voor AWS vindt.

* **[!UICONTROL AWS Region]**

   Raadpleeg deze [pagina](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)voor meer informatie over het AWS-gebied.

* Met het **[!UICONTROL Use server side encryption]** selectievakje kunt u het bestand opslaan in de modus S3.

Raadpleeg de documentatie bij de Amazon-webservices voor informatie over de locatie waar u de toegangstoets-id en geheime toegangstoets kunt vinden [](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

## Azure External Account {#azure-external-account}

Met de **[!UICONTROL Azure]** externe account wordt een verbinding met een gedeelde externe database mogelijk gemaakt, zolang deze verbinding actief is, kunt u de database openen via Adobe Campaign.

![](assets/ext_account_15.png)

* **[!UICONTROL Server]**

   URL van de Azure-server.

* **[!UICONTROL Encryption]**

   Type gekozen encryptie tussen **[!UICONTROL None]** of **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

   Om te weten waar te om uw toegangssleutel te vinden, verwijs naar deze [pagina](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-manage) (de sectie **Mening en kopieert toegangssleutels**).

## Externe rekening {#hadoop-external-account}

Met de **[!UICONTROL Hadoop]** externe account wordt een verbinding met een gedeelde externe database mogelijk gemaakt, zolang deze verbinding actief is, kunt u de database openen via Adobe Campaign. Voor meer informatie over hoe te om toegang tot Hadoop te vormen, verwijs naar deze [sectie](../../platform/using/accessing-an-external-database.md#configure-access-to-hadoop).

![](assets/ext_account_16.png)

* **[!UICONTROL Server]**

   URL van de Hadoop-server.

* **[!UICONTROL User account name]**

   Naam van de account die wordt gebruikt voor toegang tot Hadoop.

## Externe account voor Microsoft Dynamics CRM {#microsoft-dynamics-crm-external-account}

Met het **[!UICONTROL Microsoft Dynamics CRM]** externe account kunt u gegevens van Microsoft Dynamics importeren en exporteren naar Adobe Campaign.

De configuratie voor de schakelaar van de Dynamiek van Microsoft om met de Campagne van Adobe te werken hangt van uw plaatsingstype af.
Met **[!UICONTROL On-premise]** en **[!UICONTROL Office 365]** plaatsingstypes, moet u de volgende details verstrekken:

![](assets/ext_account_21.png)

* **[!UICONTROL Account]**

   Account gebruikt om u aan te melden bij Microsoft CRM.

* **[!UICONTROL Server]**

   URL van uw Microsoft CRM-server.

* **[!UICONTROL Password]**

   Wachtwoord gebruikt om binnen aan Microsoft CRM te ondertekenen.

* **[!UICONTROL Company name]** voor on-premise en de plaatsing van Office 365

   Naam van uw bedrijf.

* **[!UICONTROL Organization name]** voor on-premise implementatie

   Naam van uw organisatie.
De naam van de organisatie die in het dashboard van de Middelen van Ontwikkelaars op de Dynamica van Microsoft, **[!UICONTROL Unique Name]** gebied kan worden gevonden.

* **[!UICONTROL CRM version]** voor on-premise

   Versie van de CRM tussen **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** of **[!UICONTROL Dynamics CRM 2016]**.

Met **[!UICONTROL Web API]** plaatsingstype en **[!UICONTROL Password credentials]** authentificatie, moet u de volgende details verstrekken:

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   Account gebruikt om u aan te melden bij Microsoft CRM.

* **[!UICONTROL Server]**

   URL van uw Microsoft CRM-server.

* **[!UICONTROL Client identifier]**

   Client-id die u kunt vinden op de Microsoft Azure-beheerportal in de **[!UICONTROL Update your code]** categorie en het **[!UICONTROL Client ID]** veld.

* **[!UICONTROL CRM version]**

   Versie van de CRM tussen **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** of **[!UICONTROL Dynamics CRM 2016]**.

Met **[!UICONTROL Web API]** plaatsingstype en **[!UICONTROL Certificate]** authentificatie, moet u de volgende details verstrekken:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   URL van uw Microsoft CRM-server.

* **[!UICONTROL Private Key (Base64 encoded)]**

   Persoonlijke sleutel die aan Base64 wordt gecodeerd

* **[!UICONTROL Custom Key identifier]**


* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   Client-id die u kunt vinden op de Microsoft Azure-beheerportal in de **[!UICONTROL Update your code]** categorie en het **[!UICONTROL Client ID]** veld.

* **[!UICONTROL CRM version]**

   Versie van de CRM tussen **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** of **[!UICONTROL Dynamics CRM 2016]**.

Raadpleeg deze [pagina](../../platform/using/crm-connectors.md#example-for-microsoft-dynamics)voor meer informatie over deze configuratie.

## Oracle op verzoek externe account {#oracle-on-demand-external-account}

Met het **[!UICONTROL Oracle on demand]** externe account kunt u Oracle-gegevens importeren en exporteren naar Adobe Campaign.

![](assets/ext_account_18.png)

Als u de externe Oracle-account op aanvraag wilt configureren voor gebruik met Adobe Campaign, moet u de volgende gegevens opgeven:

* **[!UICONTROL Account]**

   Account gebruikt om u aan te melden bij Oracle CRM op verzoek.

* **[!UICONTROL Server]**

   URL van uw Oracle CRM op aanvraag-server.

* **[!UICONTROL Password]**

   Wachtwoord gebruikt om u aan te melden bij Oracle CRM op verzoek.

Raadpleeg deze [pagina](../../platform/using/crm-connectors.md#example-for-oracle-on-demand)voor meer informatie over deze configuratie.

## Externe rekening Salesforce CRM {#salesforce-crm-external-account}

Met het **[!UICONTROL Salesforce CRM]** externe account kunt u Salesforce-gegevens importeren en exporteren naar Adobe Campagne.

![](assets/ext_account_17.png)

Als u de externe account van Salesforce CRM wilt configureren voor gebruik met Adobe Campaign, moet u de volgende gegevens opgeven:

* **[!UICONTROL Account]**

   Account gebruikt om u aan te melden bij Salesforce CRM.

* **[!UICONTROL Password]**

   Wachtwoord gebruikt om u aan te melden bij Salesforce CRM.

* **[!UICONTROL Client identifier]**

   Raadpleeg deze [pagina](https://help.salesforce.com/articleView?id=000205876&type=1)om te weten waar u uw client-id kunt vinden.

* **[!UICONTROL Security token]**

   Als u wilt weten waar u uw beveiligingstoken vindt, raadpleegt u deze [pagina](https://help.salesforce.com/articleView?id=000205876&type=1).

* **[!UICONTROL API version]**

   Versie van de API tussen **[!UICONTROL Version 37]**, **[!UICONTROL Version 21]** of **[!UICONTROL Version 15]**.

Voor deze externe rekening, moet u u Salesforce CRM met de configuratietovenaar vormen.

Raadpleeg deze [pagina](../../platform/using/crm-connectors.md#example-for-salesforce-com)voor meer informatie over deze configuratie.
