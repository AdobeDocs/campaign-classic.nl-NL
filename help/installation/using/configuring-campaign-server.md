---
product: campaign
title: Campagneserver configureren
description: Campagneserver configureren
feature: Installation, Instance Settings
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1569'
ht-degree: 1%

---

# Ga aan de slag met de configuratie van de Campagneserver{#gs-campaign-server-config}



In dit hoofdstuk worden configuraties aan de serverzijde beschreven die kunnen worden uitgevoerd om aan uw behoeften en uw specifieke omgeving te voldoen.

## Beperkingen

Deze procedures zijn beperkt tot **op-gebouw**/ **hybride** plaatsingen en vereisen de toestemmingen van het Beleid.

Voor **ontvangen** plaatsingen, server-zijmontages kunnen door Adobe slechts worden gevormd. Nochtans, kunnen sommige montages opstelling binnen [ het Controlebord van de Campagne ](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=nl), zoals IP het beheer van de lijst van gewenste personen of toestemmingen URL zijn. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).

Raadpleeg de volgende secties voor meer informatie:

* [Configuratiescherm-documentatie](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=nl)
* [Hostmodellen](../../installation/using/hosting-models.md)
* [Campaign Classic On-premise &amp; Hosted Capability matrix](../../installation/using/capability-matrix.md)

## Configuratiebestanden

De configuratiedossiers van het Campaign Classic worden opgeslagen in de **conf** omslag van de installatiemap van Adobe Campaign. De configuratie wordt verspreid over twee bestanden:

* **serverConf.xml**: algemene configuratie voor alle instanties. Dit bestand combineert de technische parameters van de Adobe Campaign-server: deze worden door alle instanties gedeeld. Hieronder wordt een beschrijving van een aantal van deze parameters gegeven. De verschillende knopen en de parameters en vermeld in deze [ sectie ](../../installation/using/the-server-configuration-file.md).
* **config- `<instance>` .xml** (waar **instantie** de naam van de instantie) is: specifieke configuratie van de instantie. Als u uw server onder verschillende exemplaren deelt, gelieve de parameters specifiek voor elke instantie in hun relevant dossier in te gaan.

## Configuratiebereik

Vorm of pas de server van de Campagne afhankelijk van uw behoeften en configuratie aan. U kunt:

* Beveilig het [ Interne herkenningsteken ](#internal-identifier)
* Laat [ processen van de Campagne ](#enabling-processes) toe
* Vorm [ Toestemmingen URL ](url-permissions.md)
* Bepaal [ Gebieden van de Veiligheid ](security-zones.md)
* Vorm [ Tomcat montages ](configure-tomcat.md)
* Pas [ parameters van de Levering ](configure-delivery-settings.md) aan
* Bepaal [ Dynamische paginaveiligheid en relais ](#dynamic-page-security-and-relays)
* Beperk de lijst van [ Toegestane externe bevelen ](#restricting-authorized-external-commands)
* Opstelling [ Overbodige het volgen ](#redundant-tracking)
* Beheer [ Hoge beschikbaarheid en werkschemaaffiniteiten ](#high-availability-workflows-and-affinities)
* Vorm dossierbeheer - [ Leer meer ](file-res-management.md)
   * Uploadbestandsindeling beperken
   * Toegang tot openbare middelen toestaan
   * Proxyverbinding configureren
* [Automatisch opnieuw opstarten van proces](#automatic-process-restart)


## Interne id {#internal-identifier}

Het **interne** herkenningsteken is technische login die voor installatie, beleid en onderhoudsdoeleinden moet worden gebruikt. Deze aanmelding is niet gekoppeld aan een instantie.

Operatoren die verbinding hebben met deze aanmelding, hebben alle rechten in alle gevallen. Deze aanmelding heeft geen wachtwoord in het geval van een nieuwe installatie. U moet dit wachtwoord handmatig definiëren.

Gebruik de volgende opdracht:

```sql
nlserver config -internalpassword
```

De volgende informatie wordt dan getoond. Voer het wachtwoord in en bevestig het:

```sql
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Processen inschakelen {#enabling-processes}

De processen van Adobe Campaign op de server worden toegelaten (en onbruikbaar gemaakt) via **config-default.xml** en **`config-<instance>.xml`** dossiers.

Om de veranderingen in deze dossiers toe te passen, als de dienst van Adobe Campaign is begonnen, moet u **in werking stellen nlserver config - herlaadt** bevel.

Er zijn twee typen processen: meerdere instanties en één instantie.

* **multi-instantie**: één enkel proces is begonnen voor alle instanties. Dit is het geval voor **Web**, **syslogd** en **volglogd** processen.

  Enablement kan van het {**dossier worden gevormd 0} config-default.xml.**

  Adobe Campaign-server declareren voor toegang tot clientconsoles en voor omleiding (tracking):

  ```
  vi nl6/conf/config-default.xml
  <web args="-tomcat" autoStart="true"/>  
  <!-- to start if the machine is also a redirection server -->  
  <trackinglogd autoStart="true"/>
  ```

  In dit voorbeeld, wordt het dossier uitgegeven gebruikend a **vi** bevel in Linux. Het kan worden uitgegeven gebruikend om het even welke **.txt** of **.xml** redacteur.

* **mono-instantie**: één proces is begonnen voor elke instantie (modules: **mta**, **wfserver**, **inMail**, **sms** en **staat**).

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

**de gegevensopslag van de Campagne**

U kunt de opslagfolder (**var** folder) van de gegevens van Adobe Campaign (logboeken, downloads, redirection, enz.) vormen. Om dit te doen, gebruik **XTK_VAR_DIR** systeemvariabele:

* In Vensters, wijs op de volgende waardewaarde in **XTK_VAR_DIR** systeemvariabele

  ```
  D:\log\AdobeCampaign
  ```

* In Linux, ga naar het {**dossier 0} customer.sh en wijs aan:** uitvoer XTK_VAR_DIR=/app/log/AdobeCampaign **.**

  Voor meer op dit, verwijs naar [ Persoonlijk parameters ](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Dynamische paginabeveiliging en -bedekkingen {#dynamic-page-security-and-relays}

Door gebrek, zijn alle dynamische pagina&#39;s automatisch verwant met de **lokale** server van Tomcat van de machine de waarvan module van het Web is begonnen. Deze configuratie is ingegaan in de **`<url>`** sectie van de configuratie van het vraagrelais voor het **ServerConf.xml** dossier.

U kunt uitvoering van de dynamische pagina op a **verre** server aflossen; als de module van het Web niet op de computer wordt geactiveerd. Om dit te doen, moet u **localhost** met de naam van de verre computer voor JSP en JSSP, de toepassingen van het Web, rapporten en koorden vervangen.

Voor meer op de diverse beschikbare parameters, verwijs naar het **serverConf.xml** configuratiedossier.

Voor JSP-pagina&#39;s is de standaardconfiguratie:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign gebruikt de volgende JSP-pagina&#39;s:

* /nl/jsp/**soaprouter.jsp**: de de dienstenverbindingen van de cliëntconsole en van het Web (SOAP APIs),
* /nl/jsp/**m.jsp**: spiegel pagina&#39;s,
* /nl/jsp/**opening van een sessie.jsp**: Web-based toegang tot rapporten en aan plaatsing van de cliëntconsole,
* /nl/jsp/**s.jsp** : Het gebruiken van virale marketing (het sponsoren en sociale netwerken).

De JSSPs die voor het Mobiele Kanaal van de App wordt gebruikt zijn als volgt:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Voorbeeld:**

Het is mogelijk om clientmachineverbindingen van buitenaf te verhinderen. Om dit te doen, eenvoudig de uitvoering van **soaprouter.jsp** beperken en slechts de uitvoering van spiegelpagina&#39;s, virale verbindingen, Webvormen en openbare middelen toestaan.

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

In dit voorbeeld valt de waarde **`<IP_addresses>`** samen met de lijst met IP-adressen (gescheiden door komma&#39;s) die zijn geautoriseerd voor het gebruik van de relaismodule voor dit masker.

>[!NOTE]
>
>De waarden zullen worden aangepast volgens uw configuratie en uw netwerkbeperkingen, vooral als specifieke configuraties voor uw installatie zijn ontwikkeld.

### HTTP-headers beheren {#managing-http-headers}

Standaard worden niet alle HTTP-headers weergegeven. U kunt specifieke kopballen in de antwoorden toevoegen die door relais worden verzonden. Dit doet u als volgt:

1. Ga naar het {**dossier 0} serverConf.xml.**
1. Ga in het knooppunt **`<relay>`** naar de lijst met afgeloste HTTP-headers.
1. Voeg een **`<responseheader>`** -element met de volgende kenmerken toe:

   * **naam**: kopbalnaam
   * **waarde**: waardenaam.

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

In de **exec** knoop van het dossier van de serverconfiguratie, moet u het eerder gecreeerde dossier in het **blacklistFile** attribuut van verwijzingen voorzien.

**slechts voor Linux**: in het dossier van de serverconfiguratie, adviseren wij dat u een gebruiker specifiek aan het uitvoeren van externe bevelen specificeert om uw veiligheidsconfiguratie te verbeteren. Deze gebruiker wordt geplaatst in de **exec** knoop van het configuratiedossier. Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in deze [ sectie ](../../installation/using/the-server-configuration-file.md).

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

Wanneer de veelvoudige servers voor omleiding worden gebruikt, moeten zij met elkaar via SOAP vraag kunnen communiceren om informatie van URLs te delen om worden omgeleid. Op het moment dat de levering wordt opgestart, is het mogelijk dat niet alle omleidingsservers beschikbaar zijn; daarom hebben ze mogelijk niet hetzelfde niveau van informatie.

>[!NOTE]
>
>Wanneer u de standaard- of bedrijfsarchitectuur gebruikt, moet de hoofdtoepassingsserver zijn geautoriseerd om trackinggegevens te uploaden naar elke computer.

URLs van de overtollige servers moet in de omleidingsconfiguratie, via het **serverConf.xml** dossier worden gespecificeerd.

**Voorbeeld:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

Het **enableIf** bezit is facultatief (leeg door gebrek) en staat u toe om de verbinding toe te laten slechts als het resultaat waar is. Dit laat u een identieke configuratie op alle omleidingsservers verkrijgen.

Om hostname van de computer te verkrijgen, stel het volgende bevel in werking: **hostname - s**.



## Workflows en affiniteiten met hoge beschikbaarheid {#high-availability-workflows-and-affinities}

U kunt verschillende workflowservers (wfserver) configureren en deze op twee of meer computers distribueren. Als u dit type architectuur kiest, configureert u de verbindingsmodus van de taakverdelingsmechanisme op basis van de Adobe Campaign-toegang.

Voor toegang van het Web, selecteer de **wijze van het taakverdelingsmechanisme** om verbindingstijden te beperken.

Als de toegang tot via de console van Adobe Campaign, **knoeiboel** of **kleverige ip** wijze kiezen. Zo kunt u de verbinding tussen de rijke client en de server onderhouden en voorkomen dat een gebruikerssessie wordt onderbroken tijdens bijvoorbeeld het importeren of exporteren.

U kunt ervoor kiezen om de uitvoering van een workflow of een workflowactiviteit op een bepaalde computer af te dwingen. Hiervoor moet u een of meer affiniteiten definiëren voor de betreffende workflow of activiteit.

1. Maak de affiniteiten van de workflow of activiteit door deze in te voeren in het veld **[!UICONTROL Affinity]** .

   U kunt elke affiniteitsnaam kiezen, maar gebruik geen spaties of leestekens. Geef verschillende namen op als u verschillende servers gebruikt.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   De vervolgkeuzelijst bevat eerder gebruikte affiniteiten. Het wordt voltooid in tijd met de verschillende ingegaan waarden.

1. Open het **nl6/conf/config-`<instance>.xml`** dossier.
1. Wijzig de lijn die overeenkomt met de module **[!UICONTROL wfserver]** als volgt:

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

Om dit te doen, ga naar het **serverConf.xml** dossier, dat in de **wordt gevestigd conf** bewaarplaats van uw installatie.

Elk die proces in dit dossier wordt gevormd heeft a **processRestartTime** attributen. U kunt de waarde van dit kenmerk wijzigen om de opstarttijd van elk proces aan te passen aan uw wensen.

>[!IMPORTANT]
>
>Verwijder dit kenmerk niet. Elke dag moeten alle processen opnieuw worden opgestart.
