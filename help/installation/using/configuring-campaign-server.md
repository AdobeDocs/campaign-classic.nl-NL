---
product: campaign
title: Campaign-server configureren
description: Campaign-server configureren
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 294309239bc476669e9e017c27bd1b51a0bdaf8c
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 1%

---

# Ga aan de slag met de configuratie van de Campagneserver{#gs-campaign-server-config}

![](../../assets/v7-only.svg)

In dit hoofdstuk worden configuraties aan de serverzijde beschreven die kunnen worden uitgevoerd om aan uw behoeften en uw specifieke omgeving te voldoen.

## Beperkingen

Deze procedures zijn beperkt tot **op locatie**/**hybride** plaatsingen en vereisen de toestemmingen van het Beleid.

Voor **gehost** implementaties, server-side instellingen kunnen alleen door Adobe worden geconfigureerd. Sommige instellingen kunnen echter worden ingesteld binnen [Campagne](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html), zoals IP het beheer van de lijst van gewenste personen of toestemmingen URL. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).

For more information, refer to these sections:

* [Configuratiescherm-documentatie](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=nl)
* [Hostmodellen](../../installation/using/hosting-models.md)
* [Campaign Classic On-premise &amp; Hosted capability matrix](../../installation/using/capability-matrix.md)

## Configuration files

Campaign Classic configuration files are stored in the **conf** folder of the Adobe Campaign installation folder. De configuratie wordt verspreid over twee bestanden:

* **serverConf.xml**: general configuration for all instances. This file combines the technical parameters of the Adobe Campaign server: these are shared by all instances. The description of some of these parameters is detailed below. The different nodes and parameters and listed in this [section](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (where **instance** is the name of the instance): specific configuration of the instance. Als u uw server onder verschillende exemplaren deelt, gelieve de parameters specifiek voor elk geval in hun relevant dossier in te gaan.

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
* [Automatisch proces opnieuw opstarten](#automatic-process-restart)


## Interne id {#internal-identifier}

De **internal** identifier is een technische aanmelding die voor installatie-, beheer- en onderhoudsdoeleinden moet worden gebruikt. Deze aanmelding is niet gekoppeld aan een instantie.

Operatoren die verbinding hebben met deze aanmelding, beschikken over alle rechten. Deze aanmelding heeft geen wachtwoord in het geval van een nieuwe installatie. U moet dit wachtwoord handmatig definiëren.

Gebruik de volgende opdracht:

```
nlserver config -internalpassword
```

De volgende informatie wordt dan getoond. Enter and confirm the password:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Enable processes {#enabling-processes}

Adobe Campaign-processen op de server worden ingeschakeld (en uitgeschakeld) via de **config-default.xml** en **`config-<instance>.xml`** bestanden.

To apply the changes to these files, if the Adobe Campaign service is started, you must run the **nlserver config -reload** command.

Er zijn twee soorten processen: meerdere instanties en één instantie.

* **meerdere instanties**: één proces is voor alle gevallen gestart . Dit is het geval voor **web**, **syslogd** en **trackinglogd** processen.

   Enablement kan van worden gevormd **config-default.xml** bestand.

   Adobe Campaign-server declareren voor toegang tot clientconsoles en voor omleiding (tracking):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   In dit voorbeeld wordt het bestand bewerkt met een **vi** in Linux. Het kan worden bewerkt met elke willekeurige **.txt** of **.xml** editor.

* **mono-instantie**: voor elke instantie wordt één proces gestart (modules: **mta**, **wfserver**, **inMail**, **sms** en **stat**).

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

* In Windows, indicate the following value value in the **XTK_VAR_DIR** system variable

   ```
   D:\log\AdobeCampaign
   ```

* In Linux, go to the **customer.sh** file and indicate: **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Raadpleeg voor meer informatie hierover [Parameters aanpassen](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Dynamic page security and relays {#dynamic-page-security-and-relays}

By default, all dynamic pages are automatically related to the **local** Tomcat server of the machine whose Web module has started. Deze configuratie is ingevoerd in het dialoogvenster **`<url>`** sectie van de vraag relaisconfiguratie voor **ServerConf.xml** bestand.

U kunt uitvoering van de dynamische pagina op een **extern** server; als de module Web niet op de computer wordt geactiveerd. To do this, you must replace the **localhost** with the name of the remote computer for JSP and JSSP, Web applications, reports and strings.

For more on the various parameters available, refer to the **serverConf.xml** configuration file.

Voor JSP-pagina&#39;s is de standaardconfiguratie:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign gebruikt de volgende JSP-pagina&#39;s:

* /nl/jsp/**soaprouter.jsp**: client console- en webserviceverbindingen (SOAP API&#39;s);
* /nl/jsp/**m.jsp**: spiegelpagina&#39;s,
* /nl/jsp/**logon.jsp**: Web-based access to reports and to deployment of the client console,
* /nl/jsp/**s.jsp** : Using viral marketing (sponsoring and social networks).

The JSSPs used for the Mobile App Channel are as follows:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Voorbeeld:**

Het is mogelijk om clientmachineverbindingen van buitenaf te verhinderen. To do this, simply restrict the execution of **soaprouter.jsp** and only authorize the execution of mirror pages, viral links, web forms and public resources.

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

In this example, the **`<IP_addresses>`** value coincides with the list of IP addresses (separated by comas) authorized to use the relay module for this mask.

>[!NOTE]
>
>De waarden zullen worden aangepast volgens uw configuratie en uw netwerkbeperkingen, vooral als specifieke configuraties voor uw installatie zijn ontwikkeld.

### HTTP-headers beheren {#managing-http-headers}

Standaard worden niet alle HTTP-headers weergegeven. U kunt specifieke kopballen in de antwoorden toevoegen die door relais worden verzonden. Dit doet u als volgt:

1. Ga naar de **serverConf.xml** bestand.
1. In de **`<relay>`** , ga naar de lijst met afgeloste HTTP-headers.
1. Voeg een **`<responseheader>`** element met de volgende kenmerken:

   * **name**: koptekstnaam
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

Wanneer de veelvoudige servers voor redirection worden gebruikt, moeten zij met elkaar via de vraag van de ZEEP kunnen communiceren om informatie van URLs te delen om worden omgeleid. Op het moment dat de levering wordt gestart, is het mogelijk dat niet alle omleidingsservers beschikbaar zijn; zij zouden derhalve niet dezelfde mate van informatie kunnen hebben .

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

Kies **hash** of **kleverige ip** in. Zo kunt u de verbinding tussen de rijke client en de server onderhouden en voorkomen dat een gebruikerssessie wordt onderbroken tijdens bijvoorbeeld het importeren of exporteren.

U kunt ervoor kiezen de uitvoering van een workflow of een workflowactiviteit op een bepaalde computer af te dwingen. Hiervoor moet u een of meer affiniteiten definiëren voor de betreffende workflow of activiteit.

1. Maak de affiniteit van de workflow of activiteit door deze in te voeren in het dialoogvenster **[!UICONTROL Affinity]** veld.

   U kunt elke affiniteitsnaam kiezen, maar gebruik geen spaties of leestekens. Geef verschillende namen op als u verschillende servers gebruikt.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   De vervolgkeuzelijst bevat eerder gebruikte affiniteiten. It is completed over time with the different entered values.

1. Open de **nl6/conf/config-`<instance>.xml`** bestand.
1. Modify the line which matches the **[!UICONTROL wfserver]** module as follows:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   If you define several affinities, they must be separated by commas without any spaces:

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

Each process configured in this file has a **processRestartTime** attribute. U kunt de waarde van dit kenmerk wijzigen om de opstarttijd van elk proces aan te passen aan uw wensen.

>[!IMPORTANT]
>
>Verwijder dit kenmerk niet. Elke dag moeten alle processen opnieuw worden opgestart.
