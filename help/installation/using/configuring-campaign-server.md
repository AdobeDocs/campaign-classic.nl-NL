---
product: campaign
title: Campagneserver configureren
description: Campagneserver configureren
feature: Installation, Instance Settings
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1568'
ht-degree: 1%

---

# Ga aan de slag met de configuratie van de Campagneserver{#gs-campaign-server-config}



In dit hoofdstuk worden configuraties aan de serverzijde beschreven die kunnen worden uitgevoerd om aan uw behoeften en uw specifieke omgeving te voldoen.

## Beperkingen

Deze procedures zijn beperkt tot **op locatie**/**hybride** plaatsingen en vereisen de toestemmingen van het Beleid.

Voor **gehost** implementaties, server-side instellingen kunnen alleen door Adobe worden geconfigureerd. Sommige instellingen kunnen echter worden ingesteld binnen [Campagne](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=nl), zoals IP het beheer van de lijst van gewenste personen of toestemmingen URL. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).

Raadpleeg de volgende secties voor meer informatie:

* [Configuratiescherm-documentatie](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=nl)
* [Hostmodellen](../../installation/using/hosting-models.md)
* [Campaign Classic On-premise &amp; Hosted Capability matrix](../../installation/using/capability-matrix.md)

## Configuratiebestanden

Campaign Classic configuratiebestanden worden opgeslagen in het dialoogvenster **conf** van de installatiemap van Adobe Campaign. De configuratie wordt verspreid over twee bestanden:

* **serverConf.xml**: algemene configuratie voor alle instanties. Dit bestand combineert de technische parameters van de Adobe Campaign-server: deze worden door alle instanties gedeeld. Hieronder wordt een beschrijving van een aantal van deze parameters gegeven. De verschillende knooppunten en parameters die in dit [sectie](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** waarbij **instance** is de naam van de instantie): specifieke configuratie van de instantie. Als u uw server onder verschillende exemplaren deelt, gelieve de parameters specifiek voor elke instantie in hun relevant dossier in te gaan.

## Configuratiebereik

Vorm of pas de server van de Campagne afhankelijk van uw behoeften en configuratie aan. U kunt:

* Beveilig de [Interne id](#internal-identifier)
* Inschakelen [Campagneprocessen](#enabling-processes)
* Configureren [URL-machtigingen](url-permissions.md)
* Definiëren [Beveiligingszones](security-zones.md)
* Configureren [Tomcat-instellingen](configure-tomcat.md)
* Aanpassen [Leveringsparameters](configure-delivery-settings.md)
* Definiëren [Dynamische paginabeveiliging en -bedekkingen](#dynamic-page-security-and-relays)
* De lijst met [Externe opdrachten toegestaan](#restricting-authorized-external-commands)
* Instellen [Overbodige tekstspatiëring](#redundant-tracking)
* Beheren [Hoge beschikbaarheid en workflowaffiniteit](#high-availability-workflows-and-affinities)
* Bestandsbeheer configureren - [Meer informatie](file-res-management.md)
   * Uploadbestandsindeling beperken
   * Toegang tot openbare middelen toestaan
   * Proxyverbinding configureren
* [Automatisch opnieuw opstarten van proces](#automatic-process-restart)


## Interne id {#internal-identifier}

De **internal** identifier is een technische aanmelding die voor installatie-, beheer- en onderhoudsdoeleinden moet worden gebruikt. Deze aanmelding is niet gekoppeld aan een instantie.

Operatoren die verbinding hebben met deze aanmelding, hebben alle rechten in alle gevallen. Deze aanmelding heeft geen wachtwoord in het geval van een nieuwe installatie. U moet dit wachtwoord handmatig definiëren.

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

## Processen inschakelen {#enabling-processes}

Adobe Campaign-processen op de server worden ingeschakeld (en uitgeschakeld) via de **config-default.xml** en **`config-<instance>.xml`** bestanden.

Als u de wijzigingen op deze bestanden wilt toepassen en de Adobe Campaign-service is gestart, moet u de opdracht **nlserver config-reload** gebruiken.

Er zijn twee typen processen: meerdere instanties en één instantie.

* **meerdere instanties**: er is één proces gestart voor alle instanties. Dit is het geval voor **web**, **syslogd** en **trackinglogd** processen.

  Enablement kan van worden gevormd **config-default.xml** bestand.

  Adobe Campaign-server declareren voor toegang tot clientconsoles en voor omleiding (tracking):

  ```
  vi nl6/conf/config-default.xml
  <web args="-tomcat" autoStart="true"/>  
  <!-- to start if the machine is also a redirection server -->  
  <trackinglogd autoStart="true"/>
  ```

  In dit voorbeeld wordt het bestand bewerkt met een **vi** in Linux. Het kan worden bewerkt met elke willekeurige **.txt** of **.xml** editor.

* **mono-instantie**: er wordt één proces gestart voor elke instantie (modules: **mta**, **wfserver**, **inMail**, **sms** en **stat**).

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

U kunt de opslagmap configureren (**var** directory) van Adobe Campaign-gegevens (logbestanden, downloads, omleidingen, enz.). Om dit te doen, gebruik **XTK_VAR_DIR** systeemvariabele:

* Geef in Windows de volgende waarde op in het dialoogvenster **XTK_VAR_DIR** systeemvariabele

  ```
  D:\log\AdobeCampaign
  ```

* Ga in Linux naar de **klant.sh** en vermelden: **XTK_VAR_DIR=/app/log/AdobeCampaign exporteren**.

  Raadpleeg voor meer informatie hierover [Parameters aanpassen](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Dynamische paginabeveiliging en -bedekkingen {#dynamic-page-security-and-relays}

Standaard worden alle dynamische pagina&#39;s automatisch gekoppeld aan de **lokaal** Tomcat-server van de computer waarvan de webmodule is gestart. Deze configuratie is ingegaan in **`<url>`** sectie van de vraag relaisconfiguratie voor **ServerConf.xml** bestand.

U kunt uitvoering van de dynamische pagina op een **extern** server; als de module Web niet op de computer wordt geactiveerd. Om dit te doen, moet u vervangen **localhost** met de naam van de verre computer voor JSP en JSSP, de toepassingen van het Web, rapporten en koorden.

Raadpleeg voor meer informatie over de verschillende beschikbare parameters de **serverConf.xml** configuratiebestand.

Voor JSP-pagina&#39;s is de standaardconfiguratie:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign gebruikt de volgende JSP-pagina&#39;s:

* /nl/jsp/**soaprouter.jsp**: verbinding met clientconsole en webservices (SOAP API&#39;s),
* /nl/jsp/**m.jsp**: pagina&#39;s spiegelen,
* /nl/jsp/**opening van een sessie.jsp**: Web-based toegang tot rapporten en aan plaatsing van de cliëntconsole,
* /nl/jsp/**s.jsp** : Virtuele marketing gebruiken (sponsoring en sociale netwerken).

De JSSPs die voor het Mobiele Kanaal van de App wordt gebruikt zijn als volgt:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Voorbeeld:**

Het is mogelijk om clientmachineverbindingen van buitenaf te verhinderen. Om dit te doen, beperkt eenvoudig de uitvoering van **soaprouter.jsp** en alleen toestaan dat spiegelpagina&#39;s, virale links, webformulieren en publieke middelen worden uitgevoerd.

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

In dit voorbeeld wordt **`<IP_addresses>`** De waarde valt samen met de lijst van IP adressen (die door koma&#39;s worden gescheiden) die worden gemachtigd om de relaismodule voor dit masker te gebruiken.

>[!NOTE]
>
>De waarden zullen worden aangepast volgens uw configuratie en uw netwerkbeperkingen, vooral als specifieke configuraties voor uw installatie zijn ontwikkeld.

### HTTP-headers beheren {#managing-http-headers}

Standaard worden niet alle HTTP-headers weergegeven. U kunt specifieke kopballen in de antwoorden toevoegen die door relais worden verzonden. Dit doet u als volgt:

1. Ga naar de **serverConf.xml** bestand.
1. In de **`<relay>`** , ga naar de lijst met afgeloste HTTP-headers.
1. Voeg een **`<responseheader>`** element met de volgende kenmerken:

   * **name**: naam koptekst
   * **value**: naam van waarde.

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

In de **exec** knooppunt van het serverconfiguratiebestand, moet u verwijzen naar het eerder gemaakte bestand in het dialoogvenster **blacklistFile** kenmerk.

**Alleen voor Linux**: in het dossier van de serverconfiguratie, adviseren wij dat u een gebruiker specificeert die aan het uitvoeren van externe bevelen wordt gewijd om uw veiligheidsconfiguratie te verbeteren. Deze gebruiker wordt ingesteld in het dialoogvenster **exec** knooppunt van het configuratiebestand. Alle parameters die beschikbaar zijn in het dialoogvenster **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

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

Wanneer de veelvoudige servers voor redirection worden gebruikt, moeten zij met elkaar via de vraag van de ZEEP kunnen communiceren om informatie van URLs te delen om worden omgeleid. Op het moment dat de levering wordt opgestart, is het mogelijk dat niet alle omleidingsservers beschikbaar zijn; daarom hebben ze mogelijk niet hetzelfde niveau van informatie.

>[!NOTE]
>
>Wanneer u de standaard- of bedrijfsarchitectuur gebruikt, moet de hoofdtoepassingsserver zijn geautoriseerd om trackinggegevens te uploaden naar elke computer.

De URL&#39;s van de redundante servers moeten worden opgegeven in de omleidingsconfiguratie via de **serverConf.xml** bestand.

**Voorbeeld:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

De **enableIf** Deze eigenschap is optioneel (standaard leeg) en u kunt de verbinding alleen inschakelen als het resultaat true is. Dit laat u een identieke configuratie op alle omleidingsservers verkrijgen.

Voer de volgende opdracht uit om de hostnaam van de computer op te halen: **hostnaam -s**.



## Workflows en affiniteiten met hoge beschikbaarheid {#high-availability-workflows-and-affinities}

U kunt verschillende workflowservers (wfserver) configureren en deze op twee of meer computers distribueren. Als u dit type architectuur kiest, configureert u de verbindingsmodus van de taakverdelingsmechanisme op basis van de Adobe Campaign-toegang.

Selecteer de optie **taakverdelingsmechanisme** om de verbindingstijden te beperken.

Kies bij toegang via de Adobe Campaign-console de optie **hash** of **kleverige ip** -modus. Zo kunt u de verbinding tussen de rijke client en de server onderhouden en voorkomen dat een gebruikerssessie wordt onderbroken tijdens bijvoorbeeld het importeren of exporteren.

U kunt ervoor kiezen om de uitvoering van een workflow of een workflowactiviteit op een bepaalde computer af te dwingen. Hiervoor moet u een of meer affiniteiten definiëren voor de betreffende workflow of activiteit.

1. Maak de affiniteit van de workflow of activiteit door deze in te voeren in het dialoogvenster **[!UICONTROL Affinity]** veld.

   U kunt elke affiniteitsnaam kiezen, maar gebruik geen spaties of leestekens. Geef verschillende namen op als u verschillende servers gebruikt.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   De vervolgkeuzelijst bevat eerder gebruikte affiniteiten. Het wordt voltooid in tijd met de verschillende ingegaan waarden.

1. Open de **nl6/conf/config-`<instance>.xml`** bestand.
1. Wijzig de lijn die met de **[!UICONTROL wfserver]** als volgt:

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

Ga om dit te doen naar de **serverConf.xml** bestand, bevindt zich in het **conf** opslagplaats van uw installatie.

Elk in dit bestand geconfigureerd proces heeft een **processRestartTime** kenmerk. U kunt de waarde van dit kenmerk wijzigen om de opstarttijd van elk proces aan te passen aan uw wensen.

>[!IMPORTANT]
>
>Verwijder dit kenmerk niet. Elke dag moeten alle processen opnieuw worden opgestart.
