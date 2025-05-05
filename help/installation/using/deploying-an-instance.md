---
product: campaign
title: Een instantie implementeren
description: Meer informatie over de wizard Campagne implementeren
feature: Installation, Instance Settings, Deployment
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 8b07447c-9a86-4b56-8d29-e0b01357a6ec
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '3389'
ht-degree: 1%

---

# Een instantie implementeren{#deploying-an-instance}

>[!NOTE]
>
>Serverconfiguraties kunnen alleen worden uitgevoerd door Adobe voor implementaties die worden gehost door Adobe. Om meer over de verschillende plaatsingen te leren, verwijs naar [ Hosting modellen ](../../installation/using/hosting-models.md) sectie of [ deze pagina ](../../installation/using/capability-matrix.md).

## implementatiewizard {#deployment-assistant}

Adobe Campaign biedt een grafische assistent, beschikbaar in de Adobe Campaign-clientconsole, om de parameters van de instantie te definiëren waarmee u verbinding gaat maken.

Om de plaatsingstovenaar te beginnen, selecteer **Hulpmiddelen > Geavanceerd > plaatsingstovenaar**.

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
* **[!UICONTROL Common name of the customer]** : voer een tekenreeks in met de naam van uw bedrijf. Deze informatie kan in de unsubscription verbindingen worden gebruikt.
* **[!UICONTROL Namespace]** : voer een korte id in kleine letters in. Het doel is om bij een upgrade onderscheid te maken tussen uw specifieke configuratie en de fabrieksconfiguratie. Standaard namespace is **concentreert** - voor klant.

### Technische opties {#technical-options}

In de onderste sectie van het venster kunt u de opties selecteren die moeten worden geactiveerd.

De volgende opties zijn beschikbaar:

* **[!UICONTROL Email channel]** : voor het activeren van de e-maillevering. Verwijs naar [ parameters van het E-mailkanaal ](#email-channel-parameters).
* **[!UICONTROL Tracking]** : Als u het bijhouden van de doelpopulatie wilt inschakelen (opent en klikt). Verwijs naar [ het Volgen configuratie ](#tracking-configuration).
* **[!UICONTROL Managing bounced emails]** : Als u het POP-account wilt definiëren waarmee inkomende e-mail wordt opgehaald. Verwijs naar [ het Leiden van bweere-mails ](#managing-bounced-emails).
* **[!UICONTROL LDAP integration]** : gebruikersverificatie configureren via een LDAP-directory. Verwijs naar [ het Verbinden door LDAP ](../../installation/using/connecting-through-ldap.md).

## Parameters e-mailkanaal {#email-channel-parameters}

In de volgende stap kunt u de informatie definiëren die in berichtkoppen moet worden weergegeven.

Deze parameters kunnen in leveringsmalplaatjes, en individueel voor elke levering worden overbelast (als de gebruikers de vereiste rechten hebben).

### Parameters voor geleverde e-mails {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

Geef de volgende parameters op:

* **[!UICONTROL Sender name]** : voer de naam van de afzender in.
* **[!UICONTROL Sender address]** : voer het e-mailadres van de afzender in. Wanneer het verzenden van e-mails van Adobe Campaign, wordt de **brievenbus van het Adres van de afzender** niet gecontroleerd en de marketing gebruikers hebben geen toegang tot deze brievenbus. Adobe Campaign biedt ook niet de mogelijkheid om e-mails die in dit postvak zijn ontvangen automatisch te beantwoorden of door te sturen. Leer meer over de beste praktijken van de Leverbaarheid [ in deze documentatie ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-starting-new-platform.html?lang=nl-NL) {_blank}.

* **[!UICONTROL Reply address text]** : voer de naam in die wordt gebruikt wanneer de ontvanger op de knop **[!UICONTROL Reply]** klikt.
* **[!UICONTROL Reply address]** : voer het e-mailadres in dat moet worden gebruikt wanneer de ontvanger op de knop **[!UICONTROL Reply]** klikt in de software van zijn e-mailclient. Het doel van het **gebied van het Adres van de Reactie** is wanneer u de ontvanger aan een verschillend adres wilt antwoorden dan het **Adres van de Afzender**.  Dit adres moet een geldig e-mailadres zijn, verbonden aan een gecontroleerd brievenbus, en ontvangen door de klant.  Dit kan bijvoorbeeld een ondersteuningsmailbox zijn, `customer-care@customer.com` , waar e-mails worden gelezen en waarop wordt gereageerd.

* **[!UICONTROL Error address]** : voer het e-mailadres in van berichten met fouten. Dit is het technische adres dat wordt gebruikt om stuiterende post, met inbegrip van e-mails te behandelen die door de server van Adobe Campaign wegens niet bestaande doeladressen worden ontvangen. Dit adres moet een geldig e-mailadres zijn, verbonden aan een gecontroleerd brievenbus, en ontvangen door de klant. Het kan bijvoorbeeld een stuiterende postbus zijn, `errors@customer.com` . Dit adres kan voor een levering of in de leveringsmalplaatjes, van het **SMTP** lusje van de levering/leveringsmalplaatjeeigenschappen worden veranderd. [Meer informatie](../../delivery/using/email-parameters.md#managing-bounce-emails-managing-bounce-emails).


Naast dit, kunt u de **maskers** specificeren die voor het afzenderadres en het foutenadres worden gemachtigd. Indien nodig, kunnen deze maskers met komma&#39;s worden gescheiden. Deze configuratie is optioneel. Wanneer de gebieden zijn ingegaan, controleert Adobe Campaign op het tijdstip van levering (tijdens analyse, als het adres geen variabelen omvat) dat de adressen geldig zijn. Deze werkende wijze zorgt ervoor dat geen adressen worden gebruikt die leveringskwesties konden teweegbrengen. De adressen van de levering moeten op de leveringsserver worden gevormd.

>[!NOTE]
>
>* Deze instellingen worden opgeslagen in de opties voor het campagneplatform. [Meer informatie](../../installation/using/configuring-campaign-options.md).
> 
>* Voor configuraties met meerdere branding kunt u het adres van de Fout aanpassen en deze configuratie overschrijven vanuit de e-mail die externe account verplettert. [Meer informatie](../../installation/using/external-accounts.md#email-routing-external-account).
>


### Tekens geautoriseerd in adressen {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

In de Adobe Campaign-database moeten alle e-mailadressen als volgt worden gemaakt: `x@y.z` . **x**, **y** en **z** karakters moeten niet leeg zijn en moeten niet geoorloofde karakters omvatten.

Hier kunt u de geoorloofde tekens (&#39;gegevensbeleid&#39;) definiëren in het e-mailveld van de database. Tekens die niet in de lijst staan, worden verboden en daarom geweigerd wanneer gegevens in de database worden ingevoerd via de interface, via een webformulier en ook wanneer gegevens worden geïmporteerd.

Twee lijsten zijn beschikbaar: **slechts Europees** of **slechts US**. Indien nodig kunnen andere tekens worden toegevoegd.

### Leveringsparameters {#delivery-parameters}

De **Geavanceerde parameters...** verbinding laat u toe om tot leveringsopties, parameters toegang te hebben verbonden aan retry en quarantines.

![](assets/s_ncs_install_deployment_wiz_05.png)

In dit venster kunt u voor alle e-mailcampagnes de opties voor levering en beheer van de adreskwaliteit definiëren.

De volgende opties zijn beschikbaar:

* **[!UICONTROL Delivery duration of messages]** : Na deze tijd wordt de levering gestopt (standaard 5 dagen).
* **[!UICONTROL Online resources validity duration]** : tijd waarvoor de informatie van het ontvankelijke profiel wordt gehouden om spiegelpagina&#39;s te produceren.
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** : Als deze optie is ingeschakeld, wordt geen contact opgenomen met ontvangers van lijsten van gewezen personen.
* **[!UICONTROL Automatically ignore doubles]** : Wanneer deze optie is geselecteerd, wordt de levering niet uitgevoerd naar dubbele adressen.

>[!NOTE]
>
>Voor ontvangen of hybride installaties, als u aan [ Verbeterde MTA ](../../delivery/using/sending-with-enhanced-mta.md) hebt bevorderd, zal **[!UICONTROL Delivery duration of the messages]** slechts als reeks aan **3.5 dagen of minder** worden gebruikt. Als u een waarde definieert die hoger is dan 3,5 dagen, wordt hiermee geen rekening gehouden.

### Parameters opnieuw proberen {#retry-parameters}

De informatie over terugvorderingen wordt verstrekt in de **periodes van de Terugwinning** en **Aantal teruggekregen** gebieden: wanneer een ontvanger onbereikbaar is, bijvoorbeeld als hun inbox volledig is, door gebrek zal het programma proberen contacterend hen 5 keer, met een interval van één uur tussen elke poging (tijdens de maximumleveringstijd). U kunt deze waarden naar wens wijzigen.

>[!NOTE]
>
>Voor ontvangen of hybride installaties, als u aan [ Verbeterde MTA ](../../delivery/using/sending-with-enhanced-mta.md) hebt bevorderd, worden de het opnieuw proberen van de Campagne parameters niet meer gebruikt. De zachte stuitpogingen en de tijdsduur tussen hen worden bepaald door Verbeterde MTA gebaseerd op het type en de strengheid van de stuiteringsreacties die van het e-maildomein van het bericht terugkomen.

### Quarantaine-parameters {#quarantine-parameters}

De configuratieopties voor quarantines zijn als volgt:

* **[!UICONTROL Duration between two significant errors]** : voer een waarde in (&quot;1d&quot; standaard: 1 dag) om de tijd te definiëren die de toepassing wacht voordat de foutenteller bij een fout wordt verhoogd,
* **[!UICONTROL Maximum number of errors before quarantine]** : zodra deze waarde is bereikt, wordt het e-mailadres in quarantaine geplaatst (standaard &quot;5&quot;: het adres wordt in quarantaine geplaatst bij de zesde fout). Dit betekent dat het contact automatisch van volgende bezorgingen wordt uitgesloten.

## Beknopte e-mails beheren {#managing-bounced-emails}

Bounce mail is uiterst belangrijk om leveringsfouten te kwalificeren. Deze fouten worden gecategoriseerd in NP@I zodra de regels hun oorzaak hebben bepaald.

Deze stap is slechts beschikbaar als het **E-mailkanaal** en **Bounce post** beheersopties in het eerste stadium van de plaatsingstovenaar worden geselecteerd. Verwijs naar [ Algemene parameters ](#general-parameters).

In dit werkgebied kunt u instellingen definiëren voor het beheer van stuiterende berichten.

![](assets/s_ncs_install_deployment_wiz_06.png)

### POP-account gebruikt om inkomende mails op te halen {#pop-account-used-to-retrieve-incoming-mails}

Geef de parameters op waarmee u verbinding wilt maken met de account voor het ophalen van inkomende e-mails.

* **[!UICONTROL Label]** : naam die alle onderstaande parameters bevat,
* **[!UICONTROL Server]** : server die wordt gebruikt om stuiterende post (inkomende post) op te halen,
* **[!UICONTROL Security]** : Selecteer indien nodig **[!UICONTROL SSL]** in de vervolgkeuzelijst,
* **[!UICONTROL Port]** : serverpoort (doorgaans 110),
* **[!UICONTROL Account]** : naam van de account die wordt gebruikt voor stuiterende berichten,
* **[!UICONTROL Password]** : wachtwoord dat aan het account is gekoppeld.

Zodra de montages van POP worden gespecificeerd, klik **Test** om ervoor te zorgen zij correct zijn.

### Onverwerkte stuitberichten {#unprocessed-bounce-mails}

De grenzen worden behandeld automatisch door Adobe Campaign, die de regels toepassen in het **Beleid > Campaign Management > het Beheer van Niet te leveren stoffen > de kwalificatieknooppunt van het Logboek van de Levering** worden vermeld. Voor meer op dit, verwijs naar [ Stuiteren postbeheer ](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

Onverwerkte grenzen worden niet weergegeven in de Adobe Campaign-interface. Zij worden automatisch geschrapt tenzij zij aan een derdebrievenbus gebruikend de volgende gebieden worden overgebracht:

* **[!UICONTROL Forwarding address]** : vul dit veld in om alle foutberichten (verwerkt of onverwerkt) die door het Adobe Campaign-platform zijn verzameld, over te brengen naar een derde.
* **[!UICONTROL Address for errors]** : vul dit veld in om naar een adres van een derde alleen de foutberichten te verzenden die tijdens het InMail-proces niet in aanmerking kwamen.
* **[!UICONTROL SMTP server]** : de server die wordt gebruikt voor het verzenden van onverwerkte e-mails met bounce.

>[!IMPORTANT]
>
>Als u onverwerkte e-mails met bounce wilt doorsturen, wordt u door de Adobe aangeraden het veld **[!UICONTROL Address for errors]** alleen in te vullen. Nochtans, zorg ervoor het adres dat wordt gebruikt regelmatig wordt gecontroleerd, aangezien dit een zware lading op uw postserver kon zetten. Neem contact op met uw accountmanager voor meer informatie.

## Configuratie bijhouden {#tracking-configuration}

In de volgende stap kunt u tracering voor de instantie configureren. De instantie moet worden gedeclareerd en geregistreerd bij de volgende server(s).

Deze stap wordt slechts aangeboden wanneer het **E-mailkanaal** en **het Volgen** opties in de eerste pagina van de plaatsingstovenaar worden geselecteerd. Verwijs naar [ Algemene parameters ](#general-parameters).

Voor meer gedetailleerde informatie over Web het volgen (het volgen wijze, het creëren van en het opnemen van markeringen..), verwijs naar [ dit document ](../../configuration/using/about-web-tracking.md).

### Werkwijze {#operating-principle}

Wanneer u tracking op een instantie activeert, worden de URL&#39;s in de leveringen tijdens het verzenden gewijzigd om tracking in te schakelen.

* De informatie over externe (of veilig of niet) ingevoerde URLs op deze pagina van de plaatsingstovenaar wordt gebruikt om nieuwe URL te bouwen. Naast deze informatie bevat de gewijzigde koppeling: de id&#39;s van de levering, de ontvanger en de URL.

  De trackinggegevens worden door Adobe Campaign verzameld op de trackingserver(s) om de ontvangende profielen en de aan de levering gekoppelde gegevens te verrijken ( **[!UICONTROL Tracking]** tabs).

  Informatie over interne URL&#39;s wordt alleen door de Adobe Campaign-toepassingsserver gebruikt om contact op te nemen met de trackingserver(s).

  Voor meer op dit, verwijs naar [ het Volgen server ](#tracking-server).

* Zodra URLs wordt gevormd, moet u het volgen toelaten. Hiervoor moet de instantie zijn geregistreerd op de volgende server(s).

  Voor meer op dit, verwijs naar [ het Opslaan het volgen ](#saving-tracking).

### Trackingserver {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

Om de efficiëntie van het bijhouden van wijzigingen op dit exemplaar te garanderen, moet de volgende informatie worden weergegeven:
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** en/of **[!UICONTROL Secure external URL]** : voer de URL voor omleiding in die moet worden gebruikt in de e-mail die moet worden verzonden.
* **[!UICONTROL Internal URL(s)]** : URL&#39;s die alleen door de Adobe Campaign-server worden gebruikt om contact op te nemen met de trackingserver(s) voor het verzamelen van logbestanden en het uploaden van de URL&#39;s. Het is niet nodig deze aan de instantie te koppelen.

  Als u geen URL opgeeft, wordt standaard de URL voor bijhouden gebruikt.

Met de architectuur van de middelste-sourcing, kunt u het volgen beheer externaliseren. Dit doet u als volgt:

1. Selecteer de optie **[!UICONTROL Externalize tracking management]** : hiermee kunt u een mid-sourcingserver gebruiken als trackingserver.
1. Vul de velden **[!UICONTROL External account]** en **[!UICONTROL Instance name]** in om verbinding te kunnen maken met de server voor midsourcing.

   Voor meer informatie, verwijs naar [ Midden-sourcende server ](../../installation/using/mid-sourcing-server.md).

1. Klik op de knop **[!UICONTROL Enable the tracking instance]** om de verbinding met de server goed te keuren.

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### Tekstspatiëring opslaan {#saving-tracking}

Wanneer de URL&#39;s zijn gevuld, moet u de trackingserver registreren.

Klik de verbinding **Registratie op de volgende server(s)** en selecteer dan één van de beschikbare opties.

![](assets/s_ncs_install_deployment_wiz_09.png)

Er zijn drie mogelijke soorten architectuur voor het uitvoeren van het volgen:

1. **voegt steun voor het volgen in een bestaande instantie** toe

   Deze keuze is van toepassing als de instantie al voor andere behoeften (MTA-server, enz.) is gemaakt op servers die als trackingservers zullen worden gebruikt.

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   Ga het wachtwoord voor de **interne** rekening op redirection server(s) in om de volgende instantie te vormen.

   >[!NOTE]
   >
   >Als er meerdere trackingservers worden gebruikt, moeten deze allemaal dezelfde naam en hetzelfde wachtwoord gebruiken.

   Geef de naam van de instantie en het wachtwoord op.

1. **creeer een nieuwe instantie specifiek aan het volgen**

   Deze optie is handig wanneer trackingsinstanties zijn gereserveerd voor tracering en geen andere toepassingsmodules hebben.

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   Ga het wachtwoord voor de **interne** rekening op redirection server(s) in om de volgende instantie te vormen.

   >[!NOTE]
   >
   >Als er meerdere trackingservers zijn geconfigureerd, moeten ze allemaal hetzelfde wachtwoord gebruiken.

   Geef de naam van de instantie, het wachtwoord en eventuele bijbehorende DNS-maskers op, zoals **[!UICONTROL Campaign*]** .

1. **bevestigt reeds een volgende instantie pre-gevormd voor u**

   Deze optie wordt gebruikt wanneer u niet het wachtwoord voor de **interne** rekening hebt; In dit geval, wordt een volgende rekening preconfigured voor u op de volgende server(s). Voer het wachtwoord in van de traceringsaccount van de omleidingsserver(s) om de volgende instantie te valideren.

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   Geef de naam op van de instantie die moet worden gevalideerd.

Klik **goedkeuren** om het opnameproces met de volgende server te beginnen.

Terug in het vorige venster, bevestigt een bericht de registratie op het volgende serverniveau:

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

De parameters verbonden aan URL onderzoeken **moeten niet** voor een standaardinstallatie worden gewijzigd. Neem voor alle andere parameters contact op met de Adobe.

## Parameters van mobiele kanalen {#mobile-channel-parameters}

In de volgende stap kunt u de standaardinstellingen definiëren voor leveringen aan mobiele apparaten (SMS en WAP Push).

>[!NOTE]
>
>Het mobiele kanaal is optioneel: dit werkgebied wordt alleen weergegeven als het is aangeschaft. Controleer hiervoor uw licentieovereenkomst.

![](assets/s_ncs_install_deployment_wiz_12.png)

### Standaardaccount voor SMS-levering {#default-account-for-sms-delivery}

Voer de volgende gegevens in:

* **[!UICONTROL Label]** : voer een naam in voor dit SMS/Wap Push-account. Bijvoorbeeld, kunt u wensen om de naam van uw router te gebruiken.
* Voor de velden **[!UICONTROL Server]**, **[!UICONTROL Port]**, **[!UICONTROL Account]**, **[!UICONTROL Password]**, **[!UICONTROL Connector]**, **[!UICONTROL Send Endpoint]**, **[!UICONTROL Reception Endpoint]** en **[!UICONTROL Notification Endpoint]** neemt u contact op met het prepress-bureau voor de vereiste instellingen.

### Parameters van verzonden SMS {#parameters-of-sms-sent}

In de **Prioriteit** drop-down lijst: Selecteer &quot;Normaal&quot;, &quot;Hoog&quot;of &quot;Dringend&quot;om het op de te verzenden berichten toe te passen.

### Geavanceerde parameters {#advanced-parameters}

De **Geavanceerde parameters...** verbinding laat u toe om tot de herprobeer en quarantaineopties toegang te hebben.

![](assets/s_ncs_install_deployment_wiz_13.png)

De informatie over herpogingen is beschikbaar in de **Periode van herpogingen** en **Aantal herpogingen** gebieden: Wanneer een mobiel onbereikbaar is, door gebrek, zal het programma opnieuw 5 keer met intervallen van minstens 15 minuten (voor de maximumleveringsperiode) proberen. Deze waarden kunnen aan uw behoeften worden aangepast.

De configuratieopties voor quarantines zijn als volgt:

* **[!UICONTROL Time between two significant errors]** : voer een standaardwaarde (standaard &quot;1d&quot;: dag) in om de tijd te definiëren die de toepassing wacht voordat de foutenteller voor een fout wordt verhoogd.
* **[!UICONTROL Maximum number of errors before quarantine]** : Zodra deze waarde is bereikt, wordt het mobiele nummer in quarantaine geplaatst (standaard &quot;5&quot;: het nummer wordt in quarantaine geplaatst bij de zesde fout). Dit betekent dat het contact automatisch van toekomstige leveringen zal worden uitgesloten.

## Regionale instellingen {#regional-settings}

In dit stadium kunt u voorkeuren voor gegevensbeleid opnemen.

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]** : Wanneer deze optie is geselecteerd, past de toepassing de internationale indeling toe op telefoonnummers (het landvoorvoegsel is dan verplicht omdat het aantal cijfers niet wordt gecontroleerd voordat de opmaak wordt toegepast). Als deze optie niet is geselecteerd, moet u het internationale telefoonnummer zelf voorvoegsel &quot;+&quot; of &quot;00&quot; geven.
* **[!UICONTROL Store all phone numbers using the international format]**: Deze optie heeft slechts betrekking op **binnenlandse** telefoonaantallen die worden ingevoerd of uitgegeven. Bepaal of u een binnenlands formaat (zoals 425 555 0150) of het internationale formaat (bijvoorbeeld +1 425 555 0150) wilt gebruiken

## Toegang vanaf internet {#access-from-the-internet}

>[!IMPORTANT]
>
>Om privacyredenen raden we aan HTTPS te gebruiken voor alle externe bronnen.

Met deze stap kunt u toegangs-URL&#39;s definiëren voor Adobe Campaign-pagina&#39;s die op internet worden weergegeven.

U moet hier ook de publicatieopties aangeven die aan webformulieren zijn gekoppeld.

![](assets/s_ncs_install_deployment_wiz_15.png)

### Servers die op het Web worden blootgesteld {#servers-exposed-on-the-web}

Gebruik deze pagina om de server-URL&#39;s te vullen met:

1. Toegang tot de toepassingsserver die beschikbaar is op internet: abonnements- en uitstapformulieren, extranet, enz.
1. Open de toepassingsserver voor bronnen die niet beschikbaar zijn op het web: formulieren, intranet en bevestigingspagina&#39;s.
1. Open de spiegelpagina&#39;s van leveringen.

   Een spiegelpagina is een dynamische pagina waarop de inhoud van het e-mailbericht wordt weergegeven. Het wordt betreden via een verbinding die in het bericht wordt opgenomen dat naar de ontvanger wordt verzonden en kan gepersonaliseerde elementen bevatten. De spiegelpagina geeft de ontvanger de mogelijkheid om het bericht in Internet browser in plaats van de e-mailsoftware te lezen, ongeacht het leveringsformaat (tekst of HTML). Er worden echter alleen spiegelpagina&#39;s gegenereerd voor een bepaalde levering als de vereiste HTML-inhoud is gedefinieerd.

Met Adobe Campaign kunt u deze drie URL&#39;s onderscheiden om de laadbewerking over meerdere platforms te spreiden.


>[!NOTE]
>
>* Deze instellingen worden opgeslagen in de opties voor het campagneplatform. [Meer informatie](../../installation/using/configuring-campaign-options.md).
>* Voor configuraties met meerdere branding kunt u de URL van de pagina Mirror aanpassen en deze configuratie overschrijven via de e-mail die een externe account verplettert. [Meer informatie](../../installation/using/configuring-campaign-options.md).


## Openbare middelen beheren {#managing-public-resources}

>[!IMPORTANT]
>
>Om privacyredenen raden we aan HTTPS te gebruiken voor alle externe bronnen.

Om van buitenaf gezien te kunnen worden, moeten de afbeeldingen die worden gebruikt in e-mails en openbare middelen die aan campagnes zijn gekoppeld, aanwezig zijn op een extern toegankelijke server. Ze kunnen vervolgens beschikbaar zijn voor externe ontvangers of operatoren.

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

Voor deze stap, moet u ingaan:

1. De nieuwe URL voor de openbare bron. Voor meer informatie verwijs naar de [ Openbare middelen URL ](#public-resources-url) sectie.
1. De modus voor beelddetectie in een levering. Voor meer informatie, verwijs naar de [ sectie van de het beeldopsporing van de Levering ](#delivery-image-detection).
1. Publicatieopties Voor meer informatie, verwijs naar de [ wijzen van de Publicatie ](#publication-modes) sectie.

De openbare middelen zijn toegankelijk via het **Beleid > Middelen > Online > Openbare middelen** knoop van de boom van Adobe Campaign. Ze worden verzameld in een bibliotheek en kunnen worden opgenomen in e-mails, maar ook worden gebruikt in campagnes of taken en in inhoudsbeheer.

![](assets/install_pub_resources_view.png)

### URL van openbare bronnen {#public-resources-url}

In het eerste veld kunt u het begin opgeven van de URL die wordt gebruikt voor de bronnen nadat deze zijn geüpload. Wanneer de bronnen zijn geüpload, zijn ze toegankelijk via deze nieuwe URL.

In een levering, kunt u beelden gebruiken die in de openbare middelbibliotheek of een ander lokaal beeld of beeld worden opgeslagen op een server worden opgeslagen.

* Voor e-mailbeelden, **https://** server **/res/img** URL.

  Deze waarde kan voor elke levering worden overschreven.

* Voor openbare middelen, is URL **https://** server **/res/** instantie **&#x200B;**&#x200B;waar **instantie**&#x200B;de naam van de volgende instantie is.

### Afbeeldingsdetectie leveren {#delivery-image-detection}

In een levering, kunt u beelden gebruiken die in de openbare middelbibliotheek of een ander lokaal beeld of beeld worden opgeslagen op een server worden opgeslagen.

Het gebied **maskers URL** laat u de lijst van te slaan maskers URL specificeren wanneer het uploaden van beelden automatisch. Als u bijvoorbeeld afbeeldingen gebruikt die zijn opgeslagen op een site die van buitenaf toegankelijk is, met name op een website, kunt u de site-URL in dit veld invoeren.

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

U kunt meerdere URL-maskers opgeven door een komma te gebruiken om ze van elkaar te scheiden.

* Voor informatie bij het gebruiken van en het beheren van beelden in e-mail, verwijs naar [ deze sectie ](../../delivery/using/defining-the-email-content.md#adding-images).
* In de leveringsassistent hebben de afbeeldingen die vanuit deze URL&#39;s worden aangeroepen de status &quot;Genegeerd&quot;.

### Publicatiemodi {#publication-modes}

In het onderste gedeelte van de assistent kunt u de publicatieopties van openbare bronnen en afbeeldingen selecteren.

De volgende publicatiemodi zijn beschikbaar:

* Volgserver(s)

  De bronnen worden automatisch naar de verschillende trackingservers gekopieerd. Zij worden gevormd in de stap [ het Volgen configuratie ](#tracking-configuration).

* Andere Adobe Campaign-servers

  U kunt nog een Adobe Campaign-server gebruiken waarop de bronnen worden gekopieerd.

  Als u een specifieke Adobe Campaign-server wilt gebruiken aan de serverzijde, moet u een nieuwe instantie maken met de volgende opdracht:

  ```
  nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
  ```

  Voer vervolgens het wachtwoord in.

  De parameters van de toegewezen server(s) worden gegeven in de velden **[!UICONTROL Media URL(s)]** , **[!UICONTROL Password]** en **[!UICONTROL Instance name]** .

  ![](assets/s_ncs_install_images_upload_b.png)

* Handmatig publicatiescript (alleen voor openbare bronnen)

  ![](assets/s_ncs_install_images_upload_c.png)

  U kunt de afbeeldingen publiceren met behulp van een script:

   * U moet dit manuscript tot stand brengen: Zijn inhoud hangt van uw configuratie af.
   * Het script wordt aangeroepen door de volgende opdracht:

     ```
     [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
     ```

     waarbij `[INSTALL]` het toegangspad naar de installatiemap van Adobe Campaign is.

   * Controleer in Unix of het script uitvoerbaar is.

Voor beelden, moet het hen van de &quot;beelden&quot;omslag kopiëren die via de **wordt gespecificeerd NmsDelivery_ImageSubDirectory** optie aan één of meerdere frontale servers. Deze servers slaan de afbeeldingen op zodat ze toegankelijk zijn via de nieuwe geconfigureerde URL.

In het geval van publicatie op een Adobe Campaign-server zonder handmatig publicatiescript worden de afbeeldingen van een levering standaard opgeslagen in de `$(XTK_INSTALL_DIR)/var/res/img/ directory` . De overeenkomende URL is de volgende: **`https://server/res/img`** .

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`. De bijbehorende URL is als volgt: **`https://server/res/instance`** waarbij instance de naam van de volgende instantie is.

>[!NOTE]
>
>Het is mogelijk om de openbare folder van de middelopslag te veranderen. Voor meer op dit, verwijs naar [ het Leiden openbare middelen ](#managing-public-resources).

### Openbare bronnen synchroniseren {#synchronizing-public-resources}

Deze functionaliteit staat u toe om openbare middelen **op veelvoudige reserve-servers te synchroniseren**.

Als een openbaar middel niet aanwezig op de volgende server is of als het middel een 404 fout terugkeert, zal de volgende server proberen om het middel op één van reserve-servers te vinden.

Het verklaren en het vormen reserve-servers moeten in het dossier van Server van de Marketing **serverConf.xml** worden gedaan. Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in deze [ sectie ](../../installation/using/the-server-configuration-file.md).

**Verklaring**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**Configuratie**

Voor elke openbare bron die moet worden gesynchroniseerd, moet u een statuskenmerk toevoegen aan het element `<url>` in het `<relay>` -deel:

Het kenmerk status kan een van de volgende drie waarden hebben:

* reserve: De openbare middelen zijn gesynchroniseerd

* normal: Existing behavior (without synchronization)

* zwarte lijst: de URL wordt toegevoegd aan de lijst van gewezen personen als er een fout van 404 wordt geretourneerd. De duur (in seconden) van URL die in de lijst van gewezen personen is wordt bepaald door a **onderbrekings** attribuut de waarvan standaardwaarde 60s is.

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

Gegevens worden automatisch verwijderd via de workflow voor het opschonen van databases. Voor meer op om dit werkschema en details op de geschrapte punten te vormen en in werking te stellen, verwijs naar dit [ document ](../../production/using/database-cleanup-workflow.md).
