---
solution: Campaign Classic
product: campaign
title: Campaign-server configureren
description: Campaign-server configureren
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
translation-type: tm+mt
source-git-commit: 0c83c989c7e3718a989a4943f5cde7ad4717fddc
workflow-type: tm+mt
source-wordcount: '2810'
ht-degree: 6%

---

# Campaign-server configureren{#configuring-campaign-server}

In de onderstaande sectie vindt u informatie over configuraties aan de serverzijde die kunnen worden uitgevoerd om aan uw behoeften en uw specifieke omgeving te voldoen.

Deze configuraties moeten alleen door beheerders worden uitgevoerd en voor **On-premise**-hostmodellen.

Voor **Hosted**-implementaties kunnen instellingen aan de serverzijde alleen door Adobe worden geconfigureerd. Sommige instellingen kunnen echter worden ingesteld in het Configuratiescherm (bijvoorbeeld IP-lijst van gewenste personen of URL-machtigingen).

>[!NOTE]
>
>Het configuratiescherm is toegankelijk voor alle gebruikers met beheerdersrechten. De stappen om Admin-toegang aan een gebruiker te verlenen, worden gedetailleerd beschreven in [deze sectie](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=nl#discover-control-panel).
>
>Merk op dat uw instantie op AWS moet worden gehost en moet worden geüpgraded met de nieuwste [Gold Standard](../../rn/using/gs-overview.md)-build of de [nieuwste GA-build (21.1)](../../rn/using/latest-release.md). Leer hoe u uw versie kunt controleren in [deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Als u wilt controleren of uw instantie wordt gehost op AWS, voert u de stappen uit die worden beschreven in [deze pagina](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

Raadpleeg de volgende secties voor meer informatie:

* [Configuratiescherm-documentatie](https://docs.adobe.com/content/help/nl-NL/control-panel/using/control-panel-home.html)
* [Hostmodellen](../../installation/using/hosting-models.md)
* [Campaign Classic On-premisse en gehoste capaciteitmatrix](../../installation/using/capability-matrix.md)
* [Configuratiestappen voor hybride en gehoste modellen](../../installation/using/hosting-models.md)

Campaign Classic-configuratiebestanden worden opgeslagen in de map **conf** van de installatiemap van Adobe Campaign. De configuratie wordt verspreid over twee bestanden:

* **serverConf.xml**: algemene configuratie voor alle instanties. In dit bestand worden de technische parameters van de Adobe Campaign-server gecombineerd: deze worden door alle instanties gedeeld . Hieronder wordt een beschrijving van een aantal van deze parameters gegeven. De verschillende knooppunten en parameters en vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml**  (waarbij  **** instantie de naam van de instantie is): specifieke configuratie van de instantie. Als u uw server onder verschillende exemplaren deelt, gelieve de parameters specifiek voor elk geval in hun relevant dossier in te gaan.

## Tomcat {#configuring-tomcat} configureren

### Standaardpoort voor Tomcat {#default-port-for-tomcat}

Wanneer de 8080 luisterpoort van de Tomcat-server al bezig is met een andere toepassing die vereist is voor uw configuratie, moet u de 8080-poort vervangen door een gratis poort (bijvoorbeeld 8090). Als u dit wilt wijzigen, bewerkt u het bestand **server.xml** dat is opgeslagen in de map **/tomcat-8/conf** van de installatiemap van Adobe Campaign.

Pas dan de haven van de JSP relaispagina&#39;s aan. Hiervoor wijzigt u het bestand **serverConf.xml** dat is opgeslagen in de map **/conf** van de installatiemap van Adobe Campaign. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

### Een map toewijzen in Tomcat {#mapping-a-folder-in-tomcat}

Als u klantspecifieke instellingen wilt definiëren, kunt u een bestand **user_context.xml** maken in de map **/tomcat-8/conf**, die ook het bestand **context.xml** bevat.

Dit bestand bevat het volgende type informatie:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Deze bewerking kan zo nodig op de server worden gereproduceerd.

## Leveringsparameters aanpassen {#personalizing-delivery-parameters}

De leveringsparameters worden gedefinieerd in het configuratiebestand **serverConf.xml**. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

Algemene serverconfiguratie en opdrachten worden beschreven in [Configuratie campagnemeserver](../../installation/using/campaign-server-configuration.md).

Afhankelijk van uw behoeften en instellingen kunt u ook de volgende configuraties uitvoeren.

### SMTP-relais {#smtp-relay}

De module MTA doet dienst als inheemse agent van de postoverdracht voor uitzending SMTP (haven 25).

Het is echter mogelijk deze te vervangen door een relaisserver als dit voor uw beveiligingsbeleid is vereist. In dat geval, zal de globale productie relais zijn één (op voorwaarde dat de productie van de relaisserver aan Adobe Campaign minder is).

In dit geval, worden deze parameters geplaatst door de server SMTP in **`<relay>`** sectie te vormen. U moet het IP adres (of de gastheer) van de server specificeren SMTP die wordt gebruikt om post en zijn bijbehorende haven (25 door gebrek) over te brengen.

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Deze werkende wijze impliceert ernstige beperkingen op leveringen, aangezien het de productie wegens de intrinsieke prestaties van de relaisserver (latentie, bandbreedte...) kan zeer verminderen. Bovendien zal de capaciteit om synchrone leveringsfouten (die door het analyseren van verkeer SMTP worden ontdekt) te kwalificeren beperkt zijn, en het verzenden zal niet mogelijk zijn als de relaisserver niet beschikbaar is.

### MTA onderliggende processen {#mta-child-processes}

Het is mogelijk om de populatie van kindprocessen (maxSpareServers door gebrek 2) te controleren om uitzendingsprestaties volgens de macht van cpu van de servers en de beschikbare netwerkmiddelen te optimaliseren. Deze configuratie moet in de **`<master>`** sectie van configuratie MTA op elke individuele computer worden gemaakt.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Zie ook [Optimalisatie voor verzenden via e-mail](../../installation/using/email-deliverability.md#email-sending-optimization).

### Het leiden van uitgaande verkeer SMTP met affiniteiten {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>De affiniteitsconfiguratie moet van de ene server op de andere coherent zijn. Wij adviseren dat u Adobe voor affiniteitsconfiguratie contacteert, aangezien de configuratieveranderingen op alle toepassingsservers zouden moeten worden herhaald die MTA in werking stellen.

U kunt uitgaand verkeer SMTP door affiniteiten met IP adressen verbeteren.

Hiervoor voert u de volgende stappen uit:

1. Voer de affiniteiten in de sectie **`<ipaffinity>`** van het bestand **serverConf.xml** in.

   Een affiniteit kan verschillende namen hebben: om hen te scheiden, gebruik **;** karakter.

   Voorbeeld:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Raadpleeg het bestand **serverConf.xml** om de relevante parameters weer te geven.

1. Als u affiniteitselectie wilt inschakelen in de vervolgkeuzelijsten, moet u de affiniteitsnaam of -namen toevoegen in de **IPAffinity**-opsomming.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Opsommingen worden beschreven in [dit document](../../platform/using/managing-enumerations.md).

   Vervolgens kunt u de affiniteit selecteren die u wilt gebruiken, zoals hieronder voor typologieën wordt getoond:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >U kunt ook naar [Configuratie leveringsserver](../../installation/using/email-deliverability.md#delivery-server-configuration) verwijzen.

## URL-machtigingen {#url-permissions}

De standaardlijst met URL’s die via JavaScript-codes kunnen worden aangeroepen (workflows, enz.) door uw Campaign Classic-instanties, is beperkt. Dit zijn URL’s waardoor uw instanties correct kunnen werken.

Instanties mogen standaard geen verbinding maken met externe URL’s. Het is echter mogelijk om sommige externe URL&#39;s toe te voegen aan de lijst met geoorloofde URL&#39;s, zodat uw instantie hiermee verbinding kan maken. Hierdoor kunt u uw Campaign-instanties verbinden met externe systemen zoals SFTP-servers of websites, om de overdracht van bestanden en/of data mogelijk te maken.

Wanneer een URL is toegevoegd, wordt hiernaar verwezen in het configuratiebestand van de instantie (serverConf.xml).

De manier waarop u URL-machtigingen kunt beheren, is afhankelijk van uw hostingmodel:

* **** Hybridor  **op locatie**: Voeg de toe te staan URLs in het  **serverConf.xml- dossier** toe. Gedetailleerde informatie is beschikbaar in de onderstaande sectie.
* **Gehost**: Voeg de URL&#39;s toe die u via het  **Configuratiescherm** wilt toestaan. Raadpleeg de [desbetreffende documentatie](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/url-permissions.html) voor meer informatie.

   >[!NOTE]
   >
   >Het configuratiescherm is toegankelijk voor alle gebruikers met beheerdersrechten. De stappen om Admin-toegang aan een gebruiker te verlenen, worden gedetailleerd beschreven in [deze sectie](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel).
   >
   >Merk op dat uw instantie op AWS moet worden ontvangen en met de recentste [Gold Standard](../../rn/using/gs-overview.md) bouwstijl moet worden bevorderd. Leer hoe u uw versie kunt controleren in [deze sectie](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Als u wilt controleren of uw instantie wordt gehost op AWS, voert u de stappen uit die worden beschreven in [deze pagina](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

Met **Hybride** en **On-premise** het ontvangen modellen, moet de beheerder een nieuwe **urlPermission** in **serverConf.xml** dossier van verwijzingen voorzien. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

Er zijn drie modi voor verbindingsbeveiliging:

* **Blokkeren**: alle URL&#39;s die niet bij de lijst van gewenste personen horen, worden geblokkeerd, met een foutbericht. Dit is de standaardwijze na een postupgrade.
* **Toestemming**: alle URL&#39;s die niet bij de lijst van gewenste personen horen, zijn toegestaan.
* **Waarschuwing**: alle URL&#39;s die niet tot de lijst van gewenste personen behoren, zijn toegestaan, maar de JS-interpreter geeft een waarschuwing weer, zodat de beheerder deze kan verzamelen. In deze modus worden JST-310027-waarschuwingsberichten toegevoegd.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Standaard gebruikt de client van nieuwe klanten de **blokkeringsmodus**. Als zij een nieuwe URL moeten toestaan, zouden zij hun beheerder moeten contacteren om het aan de lijst van gewenste personen toe te voegen.
>
>Bestaande klanten die afkomstig zijn van een migratie kunnen de **waarschuwingsmodus** een tijdje gebruiken. Ondertussen moeten zij het uitgaande verkeer analyseren alvorens URLs toe te laten. Zodra de lijst van erkende URLs wordt bepaald, zouden zij hun beheerder moeten contacteren om URLs aan de lijst van gewenste personen toe te voegen en **blokkerende wijze te activeren**.

## Dynamische paginabeveiliging en -relays {#dynamic-page-security-and-relays}

Door gebrek, zijn alle dynamische pagina&#39;s automatisch verwant aan **local** de server van de Tomcat van de machine de waarvan module van het Web is begonnen. Deze configuratie is ingegaan in de **`<url>`** sectie van de configuratie van het vraagrelais voor het **ServerConf.xml** dossier. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

Om uitvoering van de dynamische pagina op een **verre** server af te lossen; als de module Web niet op de computer wordt geactiveerd. Om dit te doen, moet u **localhost** met de naam van de verre computer voor JSP en JSSP, de toepassingen van het Web, rapporten en koorden vervangen.

Raadpleeg het configuratiebestand **serverConf.xml** voor meer informatie over de verschillende beschikbare parameters.

Voor JSP-pagina&#39;s is de standaardconfiguratie:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign gebruikt de volgende JSP-pagina&#39;s:

* /nl/jsp/**soaprouter.jsp**: client console- en webserviceverbindingen (SOAP API&#39;s),
* /nl/jsp/**m.jsp**: spiegelpagina&#39;s,
* /nl/jsp/**aanmeldings.jsp**: Web-based toegang tot rapporten en tot plaatsing van de cliëntconsole,
* /nl/jsp/**s.jsp**: Het gebruik van virale marketing (sponsoring en sociale netwerken).

De JSSPs die voor het Mobiele Kanaal van de App wordt gebruikt zijn als volgt:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Voorbeeld:**

Het is mogelijk om clientmachineverbindingen van buitenaf te verhinderen. Om dit te doen, eenvoudig de uitvoering van **soaprouter.jsp** te beperken en slechts de uitvoering van spiegelpagina&#39;s, virale verbindingen, Webvormen en openbare middelen toe te staan.

De parameters zijn als volgt:

```
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/> 
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="m.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="s.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="webForm.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/webApp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/jssp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/strings/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/interaction/pub*"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/>
```

In dit voorbeeld, valt de **`<IP_addresses>`** waarde met de lijst van IP adressen (die door komma&#39;s worden gescheiden) die worden gemachtigd om de relaismodule voor dit masker te gebruiken.

>[!NOTE]
>
>De waarden zullen worden aangepast volgens uw configuratie en uw netwerkbeperkingen, vooral als specifieke configuraties voor uw installatie zijn ontwikkeld.

## Toegestane externe opdrachten beperken {#restricting-authorized-external-commands}

>[!NOTE]
>
>De volgende configuratie wordt slechts vereist voor op-gebouw installaties.

Van bouwstijl 8780, kunnen de technische beheerders de lijst van geoorloofde externe bevelen beperken die in Adobe Campaign kunnen worden gebruikt.

Hiervoor moet u een tekstbestand maken met de lijst met opdrachten die u niet wilt gebruiken, bijvoorbeeld:

```
ln
dd
openssl
curl
wget
python
python3
perl
ruby
sh
```

>[!IMPORTANT]
>
>Deze lijst is niet limitatief.

In **exec** knoop van het dossier van de serverconfiguratie, moet u het eerder gecreeerd dossier in **blacklistFile** attributen van verwijzingen voorzien.

**Alleen** voor Linux: in het dossier van de serverconfiguratie, adviseren wij dat u een gebruiker specificeert die aan het uitvoeren van externe bevelen wordt gewijd om uw veiligheidsconfiguratie te verbeteren. Deze gebruiker wordt geplaatst in **exec** knoop van het configuratiedossier. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>Als er geen gebruiker is opgegeven, worden alle opdrachten uitgevoerd in de gebruikerscontext van de Adobe Campaign-instantie. De gebruiker moet anders zijn dan de gebruiker die Adobe Campaign uitvoert.

Bijvoorbeeld:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Deze gebruiker moet worden toegevoegd aan de sudoerlijst van de &#39;neolane&#39; Adobe Campaign-operator.

>[!IMPORTANT]
>
>Gebruik geen aangepast sudo. Er moet een standaardsudo op het systeem worden geïnstalleerd.

## HTTP-headers {#managing-http-headers} beheren

Standaard worden niet alle HTTP-headers weergegeven. U kunt specifieke kopballen in de antwoorden toevoegen die door relais worden verzonden. Dit doet u als volgt:

1. Ga naar het **serverConf.xml** dossier. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).
1. Ga in de **`<relay>`** knoop, naar de lijst van afgeloste kopballen van HTTP.
1. Voeg een **`<responseheader>`** element met de volgende attributen toe:

   * **naam**: koptekstnaam
   * **waarde**: naam van waarde.

   Bijvoorbeeld:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Overbodige tekstspatiëring {#redundant-tracking}

Wanneer de veelvoudige servers voor redirection worden gebruikt, moeten zij met elkaar via de vraag van de ZEEP kunnen communiceren om informatie van URLs te delen om worden omgeleid. Op het moment dat de levering wordt gestart, is het mogelijk dat niet alle omleidingsservers beschikbaar zijn; zij zouden derhalve niet dezelfde mate van informatie kunnen hebben .

>[!NOTE]
>
>Wanneer u de standaard- of bedrijfsarchitectuur gebruikt, moet de hoofdtoepassingsserver zijn geautoriseerd om trackinggegevens te uploaden naar elke computer.

De URL&#39;s van de redundante servers moeten worden opgegeven in de omleidingsconfiguratie via het bestand **serverConf.xml**. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

**Voorbeeld:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

De eigenschap **enableIf** is optioneel (standaard leeg) en stelt u in staat de verbinding alleen in te schakelen als het resultaat waar is. Dit laat u een identieke configuratie op alle omleidingsservers verkrijgen.

Voer de volgende opdracht uit om de hostnaam van de computer op te halen: **hostnaam -s**.

## Openbare bronnen beheren {#managing-public-resources}

De openbare middelen worden voorgesteld in [Beheer van openbare middelen](../../installation/using/deploying-an-instance.md#managing-public-resources).

Ze worden opgeslagen in de map **/var/res/instance** van de installatiemap van Adobe Campaign.

De overeenkomende URL is: **http://server/res/instance** waarbij **instance** de naam van de volgende instantie is.

U kunt een andere folder specificeren door een knoop aan **conf-`<instance>`.xml** dossier toe te voegen om opslag op de server te vormen. Dit betekent dat de volgende regels moeten worden toegevoegd:

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

In dit geval, zou nieuwe URL voor de openbare middelen die in het hogere gedeelte van het venster van de plaatsingstovenaar worden gegeven aan deze omslag moeten richten.

## Workflows en affiniteiten voor hoge beschikbaarheid {#high-availability-workflows-and-affinities}

U kunt verschillende workflowservers (wfserver) configureren en deze op twee of meer computers distribueren. Als u dit type architectuur kiest, configureert u de verbindingsmodus van de taakverdelingsmechanisme op basis van de Adobe Campaign-toegang.

Selecteer voor toegang vanaf het web de modus **load balancer** om de verbindingstijden te beperken.

Kies **hash** of **sticky ip** modus als u toegang wilt tot de Adobe Campaign-console. Zo kunt u de verbinding tussen de rijke client en de server onderhouden en voorkomen dat een gebruikerssessie wordt onderbroken tijdens bijvoorbeeld het importeren of exporteren.

U kunt ervoor kiezen de uitvoering van een workflow of een workflowactiviteit op een bepaalde computer af te dwingen. Hiervoor moet u een of meer affiniteiten definiëren voor de betreffende workflow of activiteit.

1. Maak de affiniteiten van de workflow of activiteit door deze in te voeren in het veld **[!UICONTROL Affinity]**.

   U kunt de affiniteitsnamen vrij kiezen. Zorg er echter voor dat u geen spaties of leestekens gebruikt. Geef verschillende namen op als u verschillende servers gebruikt.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   De vervolgkeuzelijst bevat eerder gebruikte affiniteiten. Het wordt voltooid in tijd met de verschillende ingegaan waarden.

1. Open het bestand **nl6/conf/config-`<instance>.xml`**.
1. Wijzig de lijn die de **[!UICONTROL wfserver]** module als volgt aanpast:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Als u meerdere affiniteiten definieert, moeten deze worden gescheiden door komma&#39;s zonder spaties:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   De komma achter de naam van de affiniteit is nodig voor het uitvoeren van workflows waarvoor geen affiniteit is gedefinieerd.

   Als u alleen werkstromen wilt uitvoeren waarvoor een affiniteit is gedefinieerd, voegt u geen komma toe aan het einde van de lijst met affiniteiten. Wijzig bijvoorbeeld de regel als volgt:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Automatisch proces opnieuw starten {#automatic-process-restart}

Standaard worden de verschillende Adobe Campaign-processen elke dag om zes uur (servertijd) automatisch opnieuw gestart.

U kunt deze configuratie echter wijzigen.

Hiervoor gaat u naar het bestand **serverConf.xml** in de opslagplaats **conf** van uw installatie. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

Elk proces dat in dit dossier wordt gevormd heeft een **processRestartTime** attribuut. U kunt de waarde van dit kenmerk wijzigen om de opstarttijd van elk proces aan te passen aan uw wensen.

>[!IMPORTANT]
>
>Verwijder dit kenmerk niet. Elke dag moeten alle processen opnieuw worden opgestart.

## Uploadbare bestanden beperken {#limiting-uploadable-files}

Met een nieuw kenmerk **uploadWhiteList** kunt u de bestandstypen beperken die beschikbaar zijn voor uploaden op de Adobe Campaign-server.

Dit kenmerk is beschikbaar in het **dataStore**-element van het **serverConf.xml**-bestand. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

De standaardwaarde van dit kenmerk is **.+** en het laat u om het even welk dossiertype uploaden.

Als u de mogelijke indelingen wilt beperken, moet u de kenmerkwaarde vervangen door een geldige reguliere Java-expressie. U kunt verschillende waarden invoeren door deze met een komma te scheiden.

Bijvoorbeeld: **uploadWhiteList=&quot;.*.png,.Met *.jpg&quot;** kunt u PNG- en JPG-indelingen uploaden naar de server. Er worden geen andere indelingen geaccepteerd.

>[!IMPORTANT]
>
>In Internet Explorer moet het volledige bestandspad worden gecontroleerd door de reguliere expressie.

## Configuratie proxyverbinding {#proxy-connection-configuration}

U kunt de Campagneserver met een extern systeem door een volmacht verbinden, gebruikend een **de werkschemaactiviteit van de Overdracht van het Dossier** bijvoorbeeld. Hiervoor moet u de sectie **proxyConfig** van het bestand **serverConf.xml** via een specifieke opdracht configureren. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

De volgende proxyverbindingen zijn mogelijk: HTTP, HTTPS, FTP, SFTP. Houd er rekening mee dat de HTTP- en HTTPS-protocolparameters **niet meer beschikbaar zijn** vanaf de campagneversie 20.2. Deze parameters worden nog steeds hieronder vermeld, aangezien ze in eerdere gebouwen beschikbaar blijven - waaronder 9032.

>[!CAUTION]
>
>Alleen de standaardverificatiemodus wordt ondersteund. NTLM-verificatie wordt niet ondersteund.
>
>SOCKS-proxy&#39;s worden niet ondersteund.


U kunt de volgende opdracht gebruiken:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

protocolparameters zijn &quot;http&quot;, &quot;https&quot; of &quot;ftp&quot;.

Als u FTP instelt op dezelfde poort als HTTP/HTTPS-verkeer, kunt u het volgende gebruiken:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

De opties &quot;http&quot; en &quot;https&quot; worden alleen gebruikt wanneer de protocolparameter &quot;ftp&quot; is en geven aan of de tunnelmethode op de opgegeven poort via HTTPS of via HTTP wordt uitgevoerd.

Als u verschillende poorten gebruikt voor FTP/SFTP- en HTTP/HTTPS-verkeer via proxyserver, moet u de parameter &#39;ftp&#39;-protocol instellen.


Bijvoorbeeld:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Voer vervolgens het wachtwoord in.

HTTP-verbindingen worden gedefinieerd in de parameter proxyHTTP:

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS-verbindingen worden gedefinieerd in de parameter proxyHTTPS:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP-/FTPS-verbindingen worden gedefinieerd in de proxyFTP-parameter:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Als u dezelfde proxy voor verschillende verbindingstypen gebruikt, wordt alleen proxyHTTP gedefinieerd met useSingleProxy ingesteld op &quot;1&quot; of &quot;true&quot;.

Als u interne verbindingen hebt die door de volmacht zouden moeten gaan, voeg hen in de opheffingsparameter toe.

Als u de proxyverbinding tijdelijk wilt uitschakelen, stelt u de ingeschakelde parameter in op &quot;false&quot; of &quot;0&quot;.
