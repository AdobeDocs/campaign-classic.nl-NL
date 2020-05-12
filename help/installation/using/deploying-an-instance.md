---
title: Een instantie implementeren
seo-title: Een instantie implementeren
description: Een instantie implementeren
seo-description: null
page-status-flag: never-activated
uuid: 5694b07a-6c1c-45a3-8a22-fd9da163c28c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 71fc8bfc-40e0-4592-a540-bd6807ded3a0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3522f4f50770dde220610cd5f1c4084292d8f1f5
workflow-type: tm+mt
source-wordcount: '3055'
ht-degree: 0%

---


# Een instantie implementeren{#deploying-an-instance}

>[!NOTE]
>
>Configuraties aan de serverzijde kunnen alleen door Adobe worden uitgevoerd voor implementaties die worden gehost door Adobe. Meer over de verschillende plaatsingen leren, verwijs naar de [Hosting modelsectie](../../installation/using/hosting-models.md) of naar [dit artikel](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Implementatiewizard {#deployment-wizard}

Met een grafische wizard, die beschikbaar is in de Adobe Campaign-clientconsole, kunt u de parameters definiëren van de instantie waarmee u verbinding wilt maken.

Selecteer **Opties > Geavanceerd > de wizard** Implementatie om de wizard Implementatie te starten.

![](assets/s_ncs_install_deployment_wiz_01.png)

De configuratiestappen zijn als volgt:

1. [Algemene parameters](#general-parameters)
1. [Parameters e-mailkanaal](#email-channel-parameters)
1. [Beknopte e-mails beheren](#managing-bounced-emails)
1. [Configuratie bijhouden](#tracking-configuration)
1. [Parameters van mobiele kanalen](#mobile-channel-parameters)
1. [Regionale instellingen](#regional-settings)
1. [Toegang vanaf internet](#access-from-the-internet)
1. [Openbare middelen beheren](#managing-public-resources)
1. [Gegevens wissen](#purging-data)

## Algemene parameters {#general-parameters}

De eerste stap van de plaatsingstovenaar laat u algemene informatie over de instantie ingaan.

![](assets/s_ncs_install_deployment_wiz_02.png)

### Algemene informatie {#general-information}

In de onderste sectie van het venster kunt u de opties selecteren die moeten worden geactiveerd.

* **[!UICONTROL Customer identifier used in billing]** : dit kan de naam van de instantie en het versienummer zijn.
* **[!UICONTROL Common name of the customer]** : Voer een tekenreeks in met de naam van uw bedrijf. Deze informatie kan in de unsubscription verbindingen worden gebruikt.
* **[!UICONTROL Namespace]** : Voer een korte id in kleine letters in. Het doel is om bij een upgrade onderscheid te maken tussen uw specifieke configuratie en de fabrieksconfiguratie. De standaardnaamruimte is **geconcentreerd** - voor de klant.

### Technische opties {#technical-options}

In de onderste sectie van het venster kunt u de opties selecteren die moeten worden geactiveerd.

De volgende opties zijn beschikbaar:

* **[!UICONTROL Email channel]** : om e-maillevering te activeren. Raadpleeg de parameters [van het](#email-channel-parameters)e-mailkanaal.
* **[!UICONTROL Tracking]** : Om het volgen van de doelbevolking (opent en klikt) toe te laten. Zie [Configuratie](#tracking-configuration)bijhouden.
* **[!UICONTROL Managing bounced emails]** : Het POP-account definiëren waarmee inkomende e-mail wordt opgehaald. Zie [Verzonden e-mails](#managing-bounced-emails)beheren.
* **[!UICONTROL LDAP integration]** : Gebruikersverificatie configureren via een LDAP-directory. Zie [Verbinding maken via LDAP](../../installation/using/connecting-through-ldap.md).

## Parameters e-mailkanaal {#email-channel-parameters}

In de volgende stap kunt u de informatie definiëren die in berichtkoppen moet worden weergegeven.

Deze parameters kunnen in leveringsmalplaatjes, en individueel voor elke levering worden overbelast (als de gebruikers de vereiste rechten hebben).

### Parameters voor geleverde e-mails {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

Geef de volgende parameters op:

* **[!UICONTROL Sender name]** : Naam van de verzender
* **[!UICONTROL Sender address]** : het adres van de verzender,
* **[!UICONTROL Reply address text]** : De naam, die aanpasbaar is, die zal worden gebruikt wanneer de ontvanger de **[!UICONTROL Reply]** knoop in hun e-mailcliëntsoftware klikt,
* **[!UICONTROL Reply address]** : Het e-mailadres dat moet worden gebruikt wanneer de ontvanger op de **[!UICONTROL Reply]** knop klikt in zijn e-mailclientsoftware.
* **[!UICONTROL Error address]** : E-mailadres van berichten met fouten. Dit is het technische adres dat wordt gebruikt voor het afhandelen van stuiterende berichten, inclusief e-mails die door de Adobe Campagneserver zijn ontvangen vanwege niet-bestaande doeladressen.

Daarnaast kunt u de **maskers** opgeven die zijn geautoriseerd voor het verzendadres en het foutadres. Indien nodig, kunnen deze maskers met komma&#39;s worden gescheiden. Deze configuratie is optioneel. Wanneer de gebieden zijn ingegaan, controleert de Campagne van Adobe op het tijdstip van levering (tijdens analyse, als het adres geen variabelen omvat) dat de adressen geldig zijn. Deze werkende wijze zorgt ervoor dat geen adressen worden gebruikt die leveringskwesties konden teweegbrengen. De adressen van de levering moeten op de leveringsserver worden gevormd.

### Tekens geautoriseerd in adressen {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

In de Adobe Campagne-database moeten alle e-mailadressen als volgt worden gemaakt: `x@y.z`. De tekens **x**, **y** en **z** mogen niet leeg zijn en mogen geen niet-toegestane tekens bevatten.

Hier kunt u de geoorloofde tekens (&#39;gegevensbeleid&#39;) definiëren in het e-mailveld van de database. Tekens die niet in de lijst staan, worden verboden en daarom geweigerd wanneer gegevens in de database worden ingevoerd via de interface, via een webformulier en ook wanneer gegevens worden geïmporteerd.

Er zijn twee lijsten beschikbaar: **Alleen** Europees of alleen **** VS. Indien nodig kunnen andere tekens worden toegevoegd.

### Leveringsparameters {#delivery-parameters}

De **geavanceerde parameters...** de verbinding laat u toe om tot leveringsopties, parameters toegang te hebben verbonden aan retry en quarantines.

![](assets/s_ncs_install_deployment_wiz_05.png)

In dit venster kunt u voor alle e-mailcampagnes de opties voor levering en beheer van de adreskwaliteit definiëren.

De volgende opties zijn beschikbaar:

* **[!UICONTROL Delivery duration of messages]** : Daarna wordt de levering gestopt (standaard 5 dagen),
* **[!UICONTROL Online resources validity duration]** : Tijdstip waarop informatie uit het ontvangende profiel wordt bewaard om spiegelpagina&#39;s te genereren;
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** : Als deze optie is geselecteerd, wordt geen contact opgenomen met op de zwarte lijst geplaatste ontvangers.
* **[!UICONTROL Automatically ignore doubles]** : Als deze optie is geselecteerd, wordt de levering niet uitgevoerd naar dubbele adressen.

### Parameters opnieuw proberen {#retry-parameters}

De informatie over terugvorderingen wordt verstrekt in de velden **Herstelperioden** en **Aantal terugvorderingen** : wanneer een ontvanger onbereikbaar is, bijvoorbeeld als hun inbox volledig is, door gebrek zal het programma proberen contacterend hen vijf keer, met een interval van één uur tussen elke poging (tijdens de maximumleveringstijd). U kunt deze waarden naar wens wijzigen.

### Quarantaine-parameters {#quarantine-parameters}

De configuratieopties voor quarantines zijn als volgt:

* **[!UICONTROL Duration between two significant errors]** : Voer standaard een waarde in (&quot;1d&quot;): 1 dag) om de tijd te bepalen die de toepassing wacht alvorens de foutenteller in het geval van mislukking te verhogen,
* **[!UICONTROL Maximum number of errors before quarantine]** : zodra deze waarde is bereikt, wordt het e-mailadres in quarantaine geplaatst (standaard &quot;5&quot;: het adres zal in quarantined op de zesde fout) zijn. Dit betekent dat het contact automatisch van volgende leveringen wordt uitgesloten.

## Beknopte e-mails beheren {#managing-bounced-emails}

Bounce mail is uiterst belangrijk om leveringsfouten te kwalificeren. Deze fouten worden gecategoriseerd in NP@I zodra de regels hun oorzaak hebben bepaald.

Deze stap is alleen beschikbaar als de opties **E-mailkanaal** en **Bounce Mail** Management zijn geselecteerd in de eerste fase van de implementatiewizard. Zie [Algemene parameters](#general-parameters).

In dit werkgebied kunt u instellingen definiëren voor het beheer van stuiterende berichten.

![](assets/s_ncs_install_deployment_wiz_06.png)

### POP-account gebruikt om inkomende mails op te halen {#pop-account-used-to-retrieve-incoming-mails}

Geef de parameters op waarmee u verbinding wilt maken met de account voor het ophalen van inkomende e-mails.

* **[!UICONTROL Label]** : Naam die alle hieronder vermelde parameters bevat;
* **[!UICONTROL Server]** : Server gebruikt om stuiterende post (inkomende post) terug te winnen,
* **[!UICONTROL Security]** : Selecteer zo nodig een optie in de **[!UICONTROL SSL]** vervolgkeuzelijst.
* **[!UICONTROL Port]** : serverpoort (doorgaans 110),
* **[!UICONTROL Account]** : Naam van de rekening die voor stuiterende post wordt gebruikt,
* **[!UICONTROL Password]** : Wachtwoord dat aan het account is gekoppeld.

Nadat u de POP-instellingen hebt opgegeven, klikt u op **Testen** om te controleren of deze correct zijn.

### Onverwerkte stuitberichten {#unprocessed-bounce-mails}

Stemmen worden automatisch afgehandeld door Adobe Campaign. Hierbij worden de regels toegepast die worden vermeld in het knooppunt **Beheer > Campagnebeheer > Beheer van niet-te leveren items > Kwalificatieknooppunt** van leveringslogboek. Voor meer op dit, verwijs naar [Stuiteren postbeheer](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

Onverwerkte steunkleuren worden niet weergegeven in de interface van Adobe Campagne. Zij worden automatisch geschrapt tenzij zij aan een derdebrievenbus gebruikend de volgende gebieden worden overgebracht:

* **[!UICONTROL Forwarding address]** : Vul dit veld in om alle foutberichten (verwerkt of onverwerkt) die door het Adobe Campagneplatform zijn verzameld, over te brengen naar een adres van een derde.
* **[!UICONTROL Address for errors]** : Vul dit gebied in om aan een derdeadres slechts de foutenmeldingen over te brengen die het inMail proces niet in aanmerking kwam.
* **[!UICONTROL SMTP server]** : Server die wordt gebruikt om onverwerkte e-mails over bounce te verzenden.

>[!IMPORTANT]
>
>Adobe raadt u alleen aan het **[!UICONTROL Address for errors]** veld in te vullen als u onverwerkte e-mails met bounce wilt doorsturen. Nochtans, zorg ervoor het adres dat wordt gebruikt regelmatig wordt gecontroleerd, aangezien dit een zware lading op uw postserver kon zetten. Neem contact op met uw accountmanager voor meer informatie.

## Configuratie bijhouden {#tracking-configuration}

In de volgende stap kunt u tracering voor de instantie configureren. De instantie moet worden gedeclareerd en geregistreerd bij de volgende server(s).

Deze stap wordt alleen aangeboden als de opties **E-mailkanaal** en **Tekstspatiëring** zijn geselecteerd op de eerste pagina van de implementatiewizard. Zie [Algemene parameters](#general-parameters).

Raadpleeg [dit document](../../configuration/using/about-web-tracking.md)voor gedetailleerde informatie over webtracering (modus Tekstspatiëring, tags maken en invoegen...).

### Exploitatiebeginsel {#operating-principle}

Wanneer u tracking op een instantie activeert, worden de URL&#39;s in de leveringen tijdens het verzenden gewijzigd om tracking in te schakelen.

* De informatie over externe (of veilig of niet) ingevoerde URLs op deze pagina van de plaatsingstovenaar wordt gebruikt om nieuwe URL te bouwen. De gewijzigde koppeling bevat naast deze informatie ook: de identificatiecodes van de levering, de ontvanger en de URL.

   Trackinggegevens worden verzameld door Adobe Campagne op de trackingserver(s) om de ontvangende profielen en de gegevens die aan de levering zijn gekoppeld, te verrijken ( **[!UICONTROL Tracking]** tabbladen).

   Informatie over interne URL&#39;s wordt alleen door de toepassingsserver van Adobe Campagne gebruikt om contact op te nemen met de trackingserver(s).

   Raadpleeg de [Trackingserver](#tracking-server)voor meer informatie hierover.

* Zodra URLs wordt gevormd, moet u het volgen toelaten. Hiervoor moet de instantie zijn geregistreerd op de volgende server(s).

   Raadpleeg [Opslaan van reeksspatiëring](#saving-tracking)voor meer informatie.

### Trackingserver {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

Om de efficiëntie van het bijhouden van wijzigingen op dit exemplaar te garanderen, moet de volgende informatie worden weergegeven:
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** en/of **[!UICONTROL Secure external URL]** : Voer de URL voor omleiding in die moet worden gebruikt in de e-mail die moet worden verzonden.
* **[!UICONTROL Internal URL(s)]** : URL&#39;s die alleen door de Adobe-campagneserver worden gebruikt om contact op te nemen met de trackingserver(s) voor het verzamelen van logbestanden en het uploaden van de URL&#39;s. Het is niet nodig deze aan de instantie te koppelen.

   Als u geen URL opgeeft, wordt standaard de URL voor bijhouden gebruikt.

Met de architectuur van de middelste-sourcing, kunt u het volgen beheer externaliseren. Dit doet u als volgt:

1. Selecteer de optie **[!UICONTROL Externalize tracking management]** : hiermee kunt u een server voor midsourcing gebruiken als een trackingserver.
1. Vul de velden **[!UICONTROL External account]** en **[!UICONTROL Instance name]** velden in zodat u verbinding kunt maken met de server voor midsourcing.

   Raadpleeg de [server](../../installation/using/mid-sourcing-server.md)voor midsourcing voor meer informatie.

1. Klik op de **[!UICONTROL Enable the tracking instance]** knop om de verbinding met de server goed te keuren.

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### Tekstspatiëring opslaan {#saving-tracking}

Wanneer de URL&#39;s zijn gevuld, moet u de trackingserver registreren.

Klik op de koppeling **Registratie op de volgende server(s)** en selecteer een van de beschikbare opties.

![](assets/s_ncs_install_deployment_wiz_09.png)

Er zijn drie mogelijke soorten architectuur voor het uitvoeren van het volgen:

1. **Ondersteuning voor tekstspatiëring toevoegen in een bestaande instantie**

   Deze keuze is van toepassing als de instantie al voor andere behoeften is gemaakt (MTA-server, enz.) op servers die worden gebruikt als trackingservers.

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   Voer het wachtwoord voor de **interne** account in op de omleidingsserver(s) om de trackinginstantie te configureren.

   >[!NOTE]
   >
   >Als er meerdere trackingservers worden gebruikt, moeten deze allemaal dezelfde naam en hetzelfde wachtwoord gebruiken.

   Geef de naam van de instantie en het wachtwoord op.

1. **Een nieuwe instantie maken die is gewijd aan bijhouden**

   Deze optie is handig wanneer trackingsinstanties zijn gereserveerd voor tracering en geen andere toepassingsmodules hebben.

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   Voer het wachtwoord voor de **interne** account in op de omleidingsserver(s) om de trackinginstantie te configureren.

   >[!NOTE]
   >
   >Als er meerdere trackingservers zijn geconfigureerd, moeten ze allemaal hetzelfde wachtwoord gebruiken.

   Geef de naam van de instantie, het wachtwoord en eventuele bijbehorende DNS-maskers op, zoals **[!UICONTROL Campaign*]**.

1. **Valideer een volgende instantie reeds pre-gevormd voor u**

   Deze optie wordt gebruikt wanneer u niet het wachtwoord voor de **interne** rekening hebt; In dit geval is een account voor bijhouden vooraf geconfigureerd op de volgende server(s). Voer het wachtwoord in van de traceringsaccount van de omleidingsserver(s) om de volgende instantie te valideren.

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   Geef de naam op van de instantie die moet worden gevalideerd.

Klik op **Goedkeuren** om het opnameproces te starten met de trackingserver.

Terug in het vorige venster, bevestigt een bericht de registratie op het volgende serverniveau:

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

De parameters die gekoppeld zijn aan URL-zoekopdrachten **mogen niet worden gewijzigd** voor een standaardinstallatie. Neem voor alle andere parameters contact op met Adobe.

## Parameters van mobiele kanalen {#mobile-channel-parameters}

In de volgende stap kunt u de standaardinstellingen definiëren voor leveringen aan mobiele apparaten (SMS en WAP Push).

>[!NOTE]
>
>Het mobiele kanaal is optioneel: dit stadium wordt alleen weergegeven als het is aangeschaft . Controleer uw licentieovereenkomst.

![](assets/s_ncs_install_deployment_wiz_12.png)

### Standaardaccount voor SMS-levering {#default-account-for-sms-delivery}

Voer de volgende gegevens in:

* **[!UICONTROL Label]** : Voer een naam in voor dit SMS/Wap Push-account. Bijvoorbeeld, kunt u wensen om de naam van uw router te gebruiken.
* Voor de velden **[!UICONTROL Server]**, **[!UICONTROL Port]**, **[!UICONTROL Account]**, **[!UICONTROL Password]**, **[!UICONTROL Connector]**, **[!UICONTROL Send Endpoint]**, **[!UICONTROL Reception Endpoint]**, **[!UICONTROL Notification Endpoint]** : Neem contact op met het prepress-bureau voor de vereiste instellingen.

### Parameters van verzonden SMS {#parameters-of-sms-sent}

In de vervolgkeuzelijst **Prioriteit** : Selecteer &quot;Normaal&quot;, &quot;Hoog&quot; of &quot;Dringend&quot; om het op de te verzenden berichten toe te passen.

### Geavanceerde parameters {#advanced-parameters}

De **geavanceerde parameters...** Via de koppeling hebt u toegang tot de opties voor opnieuw proberen en quarantaine.

![](assets/s_ncs_install_deployment_wiz_13.png)

Informatie over pogingen is beschikbaar in de **velden Periode van opnieuw proberen** en **Aantal nieuwe pogingen** : Wanneer een mobiele telefoon niet bereikbaar is, probeert het programma standaard vijf keer opnieuw met intervallen van ten minste 15 minuten (voor de maximale leveringsperiode). Deze waarden kunnen aan uw behoeften worden aangepast.

De configuratieopties voor quarantines zijn als volgt:

* **[!UICONTROL Time between two significant errors]** : Voer een standaardwaarde in (standaard &quot;1d&quot;: dag) om de tijd te bepalen die de toepassing wacht alvorens de foutenteller voor een mislukking te verhogen.
* **[!UICONTROL Maximum number of errors before quarantine]** : Zodra deze waarde is bereikt, wordt het mobiele nummer in quarantaine geplaatst (standaard &quot;5&quot;: het nummer wordt in quarantaine geplaatst bij de zesde fout). Dit betekent dat het contact automatisch van toekomstige leveringen zal worden uitgesloten.

## Regionale instellingen {#regional-settings}

In dit stadium kunt u voorkeuren voor gegevensbeleid opnemen.

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]** : Als deze optie is geselecteerd, past de toepassing de internationale indeling toe op telefoonnummers (het voorvoegsel van het land is dan verplicht omdat het aantal cijfers niet wordt gecontroleerd voordat de opmaak wordt toegepast). Als deze optie niet is geselecteerd, moet u het internationale telefoonnummer zelf voorvoegsel &quot;+&quot; of &quot;00&quot; geven.
* **[!UICONTROL Store all phone numbers using the international format]** : Deze optie heeft alleen betrekking op **binnenlandse** telefoonnummers die worden geïmporteerd of bewerkt. Bepaal of u een binnenlandse indeling (zoals 425 555 0150) of de internationale indeling (bijvoorbeeld +1 425 555 0150)

## Toegang vanaf internet {#access-from-the-internet}

>[!IMPORTANT]
>
>Om privacyredenen raden we aan HTTPS te gebruiken voor alle externe bronnen.

Met deze stap kunt u toegangs-URL&#39;s definiëren voor Adobe Campagnepagina&#39;s die op internet worden weergegeven.

U moet hier ook de publicatieopties aangeven die aan webformulieren zijn gekoppeld.

![](assets/s_ncs_install_deployment_wiz_15.png)

### Servers die op het Web worden blootgesteld {#servers-exposed-on-the-web}

Gebruik deze pagina om de server-URL&#39;s te vullen met:

1. Toegang tot de toepassingsserver die beschikbaar is op internet: Abonnementsformulieren/abonnementsformulieren, extranet, enz.
1. Open de toepassingsserver voor bronnen die niet op het web beschikbaar zijn: formulieren, intranet, bevestigingspagina&#39;s.
1. Open de spiegelpagina&#39;s van leveringen.

   Een spiegelpagina is een dynamische pagina waarop de inhoud van het e-mailbericht wordt weergegeven. Het wordt betreden via een verbinding die in het bericht wordt opgenomen dat naar de ontvanger wordt verzonden en kan gepersonaliseerde elementen bevatten. De spiegelpagina biedt de ontvanger de mogelijkheid om het bericht in Internet browser in plaats van de e-mailsoftware te lezen, ongeacht het leveringsformaat (tekst of HTML). Er worden echter alleen spiegelpagina&#39;s gegenereerd voor een bepaalde levering als de vereiste HTML-inhoud is gedefinieerd.

Met Adobe Campagne kunt u deze drie URL&#39;s onderscheiden om de laadbewerking over meerdere platforms te spreiden.

## Openbare middelen beheren {#managing-public-resources}

>[!IMPORTANT]
>
>Om privacyredenen raden we aan HTTPS te gebruiken voor alle externe bronnen.

Om van buitenaf gezien te kunnen worden, moeten de afbeeldingen die worden gebruikt in e-mails en openbare middelen die aan campagnes zijn gekoppeld, aanwezig zijn op een extern toegankelijke server. Ze kunnen vervolgens beschikbaar zijn voor externe ontvangers of operatoren.

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

Voor deze stap, moet u ingaan:

1. De nieuwe URL voor openbare bronnen. Zie de sectie URL [van](#public-resources-url) openbare bronnen voor meer informatie.
1. De modus voor beelddetectie in een levering. Raadpleeg het gedeelte [Afbeeldingsdetectie](#delivery-image-detection) van levering voor meer informatie.
1. Publicatieopties Raadpleeg de sectie [Publicatiemodi](#publication-modes) voor meer informatie.

De openbare middelen zijn toegankelijk via het **Beleid > Middelen > Online > de knoop van Openbare middelen** van de Boom van de Campagne van Adobe. Ze worden verzameld in een bibliotheek en kunnen worden opgenomen in e-mails, maar ook worden gebruikt in campagnes of taken en in inhoudsbeheer.

![](assets/install_pub_resources_view.png)

### URL van openbare bronnen {#public-resources-url}

In het eerste veld kunt u het begin opgeven van de URL die wordt gebruikt voor de bronnen nadat deze zijn geüpload. Wanneer de bronnen zijn geüpload, zijn ze toegankelijk via deze nieuwe URL.

In een levering, kunt u beelden gebruiken die in de openbare middelbibliotheek of een ander lokaal beeld of beeld worden opgeslagen op een server worden opgeslagen.

* Voor e-mailafbeeldingen gebruikt u de URL **https://** server **/res/img** .

   Deze waarde kan voor elke levering worden overschreven.

* Voor openbare middelen, URL **https://** server **/res/** instantie ****waar de **instantie**de naam van de volgende instantie is.

### Afbeeldingsdetectie leveren {#delivery-image-detection}

In een levering, kunt u beelden gebruiken die in de openbare middelbibliotheek of een ander lokaal beeld of beeld worden opgeslagen op een server worden opgeslagen.

Met de veld- **URL-maskers** kunt u de lijst opgeven met URL-maskers die moeten worden overgeslagen wanneer afbeeldingen automatisch worden geüpload. Als u bijvoorbeeld afbeeldingen gebruikt die zijn opgeslagen op een site die van buitenaf toegankelijk is, met name op een website, kunt u de site-URL in dit veld invoeren.

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

U kunt meerdere URL-maskers opgeven door een komma te gebruiken om ze van elkaar te scheiden.

* Raadpleeg [deze sectie](../../delivery/using/defining-the-email-content.md#adding-images)voor meer informatie over het gebruik en het beheer van afbeeldingen in e-mails.
* In de leveringstovenaar, zullen de beelden die van deze URLs worden geroepen de status &quot;Genegeerd&quot;hebben.

### Publicatiemodi {#publication-modes}

In het onderste gedeelte van de wizard kunt u de publicatieopties van openbare bronnen en afbeeldingen selecteren. Deze opties zijn ook beschikbaar voor webformulieren en enquêtes.

De volgende publicatiemodi zijn beschikbaar:

* Volgserver(s)

   De bronnen worden automatisch naar de verschillende trackingservers gekopieerd. Zij worden gevormd in de stap [die configuratie](#tracking-configuration)volgen.

* Andere Adobe Campagne-servers

   U kunt nog een andere Adobe Campagne-server gebruiken waar de bronnen worden gekopieerd.

   Als u een speciale Adobe Campagneserver wilt gebruiken aan de serverzijde, moet u een nieuwe instantie maken met de volgende opdracht:

   ```
   nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
   ```

   Voer vervolgens het wachtwoord in.

   De parameters van de toegewijde server(s) worden gegeven in de **[!UICONTROL Media URL(s)]**, **[!UICONTROL Password]** en **[!UICONTROL Instance name]** gebieden.

   ![](assets/s_ncs_install_images_upload_b.png)

* Handmatig publicatiescript (alleen voor openbare bronnen)

   ![](assets/s_ncs_install_images_upload_c.png)

   U kunt de afbeeldingen publiceren met behulp van een script:

   * U moet dit script maken: Zijn inhoud hangt van uw configuratie af.
   * Het script wordt aangeroepen door de volgende opdracht:

      ```
      [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
      ```

      Hier `[INSTALL]` ziet u het toegangspad naar de installatiemap van Adobe Campaign.

   * Controleer in Unix of het script uitvoerbaar is.

Voor afbeeldingen moeten deze worden gekopieerd van de map &quot;images&quot; die via de optie **NmsDelivery_ImageSubDirectory** is opgegeven naar een of meer frontale servers. Deze servers slaan de afbeeldingen op zodat ze toegankelijk zijn via de nieuwe geconfigureerde URL.

In het geval van publicatie op een Adobe Campaign-server zonder handmatig publicatiescript worden de afbeeldingen van een levering standaard opgeslagen in het `$(XTK_INSTALL_DIR)/var/res/img/ directory`bestand. De bijbehorende URL is: **`https://server/res/img`**.

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`. De bijbehorende URL is als volgt: **`https://server/res/instance`** waarbij instantie de naam van de instantie tracking is.

>[!NOTE]
>
>Het is mogelijk om de openbare folder van de middelopslag te veranderen. Zie [Overheidsmiddelen](#managing-public-resources)beheren voor meer informatie hierover.

### Openbare bronnen synchroniseren {#synchronizing-public-resources}

Met deze functionaliteit kunt u openbare bronnen **op meerdere reserveservers** synchroniseren.

Als een openbaar middel niet aanwezig op de volgende server is of als het middel een 404 fout terugkeert, zal de volgende server proberen om het middel op één van reserve-servers te vinden.

Het verklaren en het vormen reserve-servers moeten in het dossier **serverConf.xml** van de Marketing worden gedaan. Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

**Verklaring**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**Configuratie**

Voor elk openbaar middel dat moet worden gesynchroniseerd, moet u een statusattribuut aan het `<url>` element in het `<relay>` deel toevoegen:

Het kenmerk status kan een van de volgende drie waarden hebben:

* reserve: De openbare bron is gesynchroniseerd

* normaal: Bestaand gedrag (zonder synchronisatie)

* zwarte lijst: De URL wordt op de zwarte lijst weergegeven als er een fout van 404 wordt geretourneerd. De duur (in seconden) van de zwarte lijst wordt gedefinieerd door een **time-outkenmerk** waarvan de standaardwaarde 60 seconden is.

De uit-van-de-doos configuratie van de synchronisatie is:

```
(extracted from the serverConf.xml file)

<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="false" trackingPassword="">
<spareServer enabledIf="" id="1" url=""/>
</redirection>

....


<relay debugRelay="false" forbiddenCharsInAuthority="?#.@/:" forbiddenCharsInPath="?#/"
           modDir="index.html" startRelay="false" startRelayInModule="true" timeout="60">
   <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/view/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jsp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jssp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/webApp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/report/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/jssp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/strings/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/interaction/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/barcode/*"/>

      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/favicon.*"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.html"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.png"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.jpg"/>

 </relay>
```

## Gegevens wissen {#purging-data}

Het laatste stadium van de plaatsingstovenaar laat u het automatische zuiveren van verouderde gegevens vormen. De waarden worden uitgedrukt in dagen.

![](assets/s_ncs_install_deployment_wiz_16.png)

Gegevens worden automatisch verwijderd via de workflow voor het opschonen van databases. Raadpleeg dit [document](../../production/using/database-cleanup-workflow.md)voor meer informatie over het configureren en gebruiken van deze workflow en over de verwijderde items.
