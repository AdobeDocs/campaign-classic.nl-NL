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
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '2575'
ht-degree: 1%

---

# Ga aan de slag met de configuratie van de Campagneserver{#gs-campaign-server-config}

In dit hoofdstuk worden configuraties aan de serverzijde beschreven die kunnen worden uitgevoerd om aan uw behoeften en uw specifieke omgeving te voldoen.

## Beperkingen

Deze procedures zijn beperkt tot **on-premise**/**hybride** plaatsingen en vereisen de toestemmingen van het Beleid.

Voor **gehoste**-implementaties kunnen instellingen aan de serverzijde alleen door Adobe worden geconfigureerd. Nochtans, kunnen sommige montages opstelling binnen [het Controlebord van de Campagne](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html), zoals IP het beheer van de lijst van gewenste personen of toestemmingen URL zijn. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).

Raadpleeg de volgende secties voor meer informatie:

* [Configuratiescherm-documentatie](https://docs.adobe.com/content/help/nl-NL/control-panel/using/control-panel-home.html)
* [Hostmodellen](../../installation/using/hosting-models.md)
* [Campaign Classic On-premisse en gehoste capaciteitmatrix](../../installation/using/capability-matrix.md)

## Configuratiebestanden

Campaign Classic-configuratiebestanden worden opgeslagen in de map **conf** van de installatiemap van Adobe Campaign. De configuratie wordt verspreid over twee bestanden:

* **serverConf.xml**: algemene configuratie voor alle instanties. In dit bestand worden de technische parameters van de Adobe Campaign-server gecombineerd: deze worden door alle instanties gedeeld . Hieronder wordt een beschrijving van een aantal van deze parameters gegeven. De verschillende knooppunten en parameters en vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml**  (waarbij  **** instantie de naam van de instantie is): specifieke configuratie van de instantie. Als u uw server onder verschillende exemplaren deelt, gelieve de parameters specifiek voor elk geval in hun relevant dossier in te gaan.

Algemene richtlijnen voor serverconfiguratie worden beschreven in [Configuratie campagneserver](../../installation/using/configuring-campaign-server.md).


## Configuratiebereik

Vorm of pas de server van de Campagne afhankelijk van uw behoeften en configuratie aan. U kunt:

* Beveilig [Interne id](#internal-identifier)
* [Campagneprocessen inschakelen](#enabling-processes)
* [URL-machtigingen configureren](url-permissions.md)
* [Beveiligingszones](security-zones.md) definiëren
* [Tomcat-instellingen](configure-tomcat.md) configureren
* [Leveringsparameters](#delivery-settings) aanpassen
* [Dynamische paginabeveiliging en -bedekkingen definiëren](#dynamic-page-security-and-relays)
* De lijst met [Toegestane externe opdrachten beperken](#restricting-authorized-external-commands)
* [Overbodige tracking](#redundant-tracking) instellen
* [Hoge beschikbaarheid en workflow-affiniteiten beheren](#high-availability-workflows-and-affinities)
* Bestandsbeheer configureren - [Meer informatie](#file-and-resmanagement)
   * Uploadbestandsindeling beperken
   * Toegang tot openbare middelen toestaan
   * Proxyverbinding configureren
* [Automatisch proces opnieuw opstarten](#automatic-process-restart)


## Interne id {#internal-identifier}

De **interne**-id is een technische aanmelding die moet worden gebruikt voor installatie-, beheer- en onderhoudsdoeleinden. Deze aanmelding is niet gekoppeld aan een instantie.

Operatoren die verbinding hebben met deze aanmelding, beschikken over alle rechten. Deze aanmelding heeft geen wachtwoord in het geval van een nieuwe installatie. U moet dit wachtwoord handmatig definiëren.

Gebruik de volgende opdracht:

```
nlserver config -internalpassword
```

De volgende informatie wordt dan getoond. Voer het wachtwoord in en bevestig het:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Processen {#enabling-processes} inschakelen

Adobe Campaign-processen op de server worden ingeschakeld (en uitgeschakeld) via de bestanden **config-default.xml** en **`config-<instance>.xml`**.

Als u de wijzigingen op deze bestanden wilt toepassen en de Adobe Campaign-service is gestart, moet u de opdracht **nlserver config -reload** uitvoeren.

Er zijn twee soorten processen: meerdere instanties en één instantie.

* **meerdere instanties**: één proces is voor alle gevallen gestart . Dit is het geval voor **web**, **syslogd** en **trackinglogd** processen.

   Enablement kan van het **config-default.xml** dossier worden gevormd.

   Adobe Campaign-server declareren voor toegang tot clientconsoles en voor omleiding (tracking):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   In dit voorbeeld wordt het bestand bewerkt met de opdracht **vi** in Linux. Het kan worden uitgegeven gebruikend om het even welke **.txt** of **.xml** redacteur.

* **mono-instantie**: voor elke instantie wordt één proces gestart (modules:  **mta**,  **wfserver**,  **inMail**,  **** smand  **stat**).

   Enablement kan worden gevormd gebruikend het configuratiedossier van de instantie:

   ```
   config-<instance>.xml
   ```

   Een server declareren voor levering, workflowinstanties uitvoeren en stuiterende berichten herstellen:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**Campagne voor gegevensopslag**

U kunt de opslagdirectory (**var** directory) van Adobe Campaign-gegevens (logbestanden, downloads, omleidingen, enz.) configureren. Hiervoor gebruikt u de systeemvariabele **XTK_VAR_DIR**:

* Geef in Windows de volgende waarde op in de systeemvariabele **XTK_VAR_DIR**

   ```
   D:\log\AdobeCampaign
   ```

* Ga in Linux naar het bestand **customer.sh** en geef aan: **exporteer XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Raadpleeg [Parameters aanpassen](../../installation/using/installing-packages-with-linux.md#personalizing-parameters) voor meer informatie.

## Leveringsinstellingen configureren {#delivery-settings}

De leveringsparameters moeten worden geconfigureerd in de map **serverConf.xml**.

* **DNS-configuratie**: specificeer het leveringsdomein en de IP adressen (of gastheer) van de DNS servers die worden gebruikt om aan MX-type DNS vragen te antwoorden die door de MTA module van de  **`<dnsconfig>`** vanaf worden gemaakt.

   >[!NOTE]
   >
   >De **nameServers** parameter is essentieel voor een installatie in Vensters. Voor een installatie in Linux, moet het leeg worden verlaten.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Afhankelijk van uw behoeften en instellingen kunt u ook de volgende configuraties uitvoeren: configureer een [SMTP relais](#smtp-relay), pas het aantal [MTA kindprocessen](#mta-child-processes), [Beheer uitgaand verkeer SMTP](#managing-outbound-smtp-traffic-with-affinities) aan.

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

Het is mogelijk om het aantal kindprocessen (maxSpareServers door gebrek 2) te controleren om uitzendingsprestaties volgens de macht van cpu van de servers en de beschikbare netwerkmiddelen te optimaliseren. Deze configuratie moet in de **`<master>`** sectie van configuratie MTA op elke individuele computer worden gemaakt.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Zie ook [Optimalisatie voor verzenden via e-mail](../../installation/using/email-deliverability.md#email-sending-optimization).

### Beheer uitgaand verkeer SMTP met affiniteiten {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>De affiniteitsconfiguratie moet consistent zijn van de ene server naar de andere. Wij adviseren dat u Adobe voor affiniteitsconfiguratie contacteert, aangezien de configuratieveranderingen op alle toepassingsservers zouden moeten worden herhaald die MTA in werking stellen.

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



## Dynamische paginabeveiliging en -relays {#dynamic-page-security-and-relays}

Door gebrek, zijn alle dynamische pagina&#39;s automatisch verwant aan **local** de server van de Tomcat van de machine de waarvan module van het Web is begonnen. Deze configuratie is ingegaan in de **`<url>`** sectie van de configuratie van het vraagrelais voor het **ServerConf.xml** dossier.

U kunt uitvoering van de dynamische pagina op een **verre** server afgeven; als de module Web niet op de computer wordt geactiveerd. Om dit te doen, moet u **localhost** met de naam van de verre computer voor JSP en JSSP, de toepassingen van het Web, rapporten en koorden vervangen.

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

### HTTP-headers {#managing-http-headers} beheren

Standaard worden niet alle HTTP-headers weergegeven. U kunt specifieke kopballen in de antwoorden toevoegen die door relais worden verzonden. Dit doet u als volgt:

1. Ga naar het **serverConf.xml** dossier.
1. Ga in de **`<relay>`** knoop, naar de lijst van afgeloste kopballen van HTTP.
1. Voeg een **`<responseheader>`** element met de volgende attributen toe:

   * **naam**: koptekstnaam
   * **waarde**: naam van waarde.

   Bijvoorbeeld:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Toegestane externe opdrachten beperken {#restricting-authorized-external-commands}

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


## Overbodige tekstspatiëring {#redundant-tracking}

Wanneer de veelvoudige servers voor redirection worden gebruikt, moeten zij met elkaar via de vraag van de ZEEP kunnen communiceren om informatie van URLs te delen om worden omgeleid. Op het moment dat de levering wordt gestart, is het mogelijk dat niet alle omleidingsservers beschikbaar zijn; zij zouden derhalve niet dezelfde mate van informatie kunnen hebben .

>[!NOTE]
>
>Wanneer u de standaard- of bedrijfsarchitectuur gebruikt, moet de hoofdtoepassingsserver zijn geautoriseerd om trackinggegevens te uploaden naar elke computer.

De URL&#39;s van de redundante servers moeten worden opgegeven in de omleidingsconfiguratie via het bestand **serverConf.xml**.

**Voorbeeld:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

De eigenschap **enableIf** is optioneel (standaard leeg) en stelt u in staat de verbinding alleen in te schakelen als het resultaat waar is. Dit laat u een identieke configuratie op alle omleidingsservers verkrijgen.

Voer de volgende opdracht uit om de hostnaam van de computer op te halen: **hostnaam -s**.

## Bestands- en resourcebeheer{#file-and-resmanagement}

### Bestandsindeling voor uploaden beperken {#limiting-uploadable-files}

Gebruik het **uploadWhiteList** attribuut om de dossiertypes te beperken beschikbaar voor upload op de server van Adobe Campaign.

Dit kenmerk is beschikbaar in het **dataStore**-element van het **serverConf.xml**-bestand. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

De standaardwaarde van dit kenmerk is **.+** en laat u om het even welk dossiertype uploaden.

Als u de mogelijke indelingen wilt beperken, vervangt u de kenmerkwaarde door een geldige reguliere Java-expressie. U kunt verschillende waarden invoeren door deze met een komma te scheiden.

Bijvoorbeeld: **uploadWhiteList=&quot;.*.png,.Met *.jpg&quot;** kunt u PNG- en JPG-indelingen uploaden naar de server. Er worden geen andere indelingen geaccepteerd.

>[!NOTE]
>
>In Internet Explorer moet het volledige bestandspad worden gecontroleerd door de reguliere expressie.

U kunt belangrijke dossiers ook verhinderen worden geupload door de Server van het Web te vormen. [Meer informatie](web-server-configuration.md)

### Configuratie proxyverbinding {#proxy-connection-configuration}

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

### Overheidsbronnen beheren {#managing-public-resources}

Om voor het publiek toegankelijk te zijn, moeten de beelden die in e-mail en openbare middelen verbonden aan campagnes worden gebruikt op een extern toegankelijke server aanwezig zijn. Ze kunnen vervolgens beschikbaar zijn voor externe ontvangers of operatoren. [Meer informatie](../../installation/using/deploying-an-instance.md#managing-public-resources).

Openbare bronnen worden opgeslagen in de map **/var/res/instance** van de installatiemap van Adobe Campaign.

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

   U kunt elke affiniteitsnaam kiezen, maar gebruik geen spaties of leestekens. Geef verschillende namen op als u verschillende servers gebruikt.

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

## Automatisch opnieuw opstarten {#automatic-process-restart}

Standaard worden de verschillende Adobe Campaign-processen elke dag om zes uur (servertijd) automatisch opnieuw gestart.

U kunt deze configuratie echter wijzigen.

Hiervoor gaat u naar het bestand **serverConf.xml** in de opslagplaats **conf** van uw installatie.

Elk proces dat in dit dossier wordt gevormd heeft een **processRestartTime** attribuut. U kunt de waarde van dit kenmerk wijzigen om de opstarttijd van elk proces aan te passen aan uw wensen.

>[!IMPORTANT]
>
>Verwijder dit kenmerk niet. Elke dag moeten alle processen opnieuw worden opgestart.
