---
product: campaign
title: Beveiligingszones configureren
description: Leer hoe u beveiligingszones kunt configureren
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1464'
ht-degree: 0%

---

# Beveiligingszones definiëren (op locatie){#defining-security-zones}



Elke exploitant moet met een streek worden verbonden om aan een geval te login en exploitant IP moet in de adressen of adresreeksen worden omvat die in de veiligheidsstreek worden bepaald. Configuratie van de beveiligingszone wordt uitgevoerd in het configuratiebestand van de Adobe Campaign-server.

De exploitanten worden verbonden met een veiligheidsstreek van zijn profiel in de console, die in **[!UICONTROL Administration > Access management > Operators]** knooppunt. [Meer informatie](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>Deze procedure is beperkt tot **op locatie** implementaties.
>
>Als **gehost** klant, als u toegang hebt tot [Campagne](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=nl), kunt u de zelfdienstinterface van de Zone van de Veiligheid gebruiken. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html)
>
>Overige **hybride/gehost** de klanten moeten uit bereiken aan het ondersteuningsteam van Adobe om IP aan de lijst van gewenste personen toe te voegen.

## Beveiligingszones maken {#creating-security-zones}

Een zone wordt gedefinieerd door:

* één of meerdere waaiers van IP adressen (IPv4 en IPv6)
* een technische naam verbonden aan elke waaier van IP adressen

Beveiligingszones zijn onderling vergrendeld, wat betekent dat het definiëren van een nieuwe zone binnen een andere zone het aantal operatoren verlaagt dat zich daarop kan aanmelden, terwijl de rechten die aan elke operator zijn toegewezen, worden vergroot.

Zones moeten tijdens de serverconfiguratie worden gedefinieerd, in de **serverConf.xml** bestand. Alle parameters die beschikbaar zijn in het dialoogvenster **serverConf.xml** zijn vermeld in [deze sectie](../../installation/using/the-server-configuration-file.md).

Elke zone definieert rechten, zoals:

* HTTP-verbinding in plaats van HTTPS
* Foutweergave (Java-fouten, JavaScript, C++, enz.)
* Voorvertoning van rapport en webApp
* Verificatie via aanmelding/wachtwoord
* Niet-beveiligde verbindingsmodus

>[!NOTE]
>
>**Elke exploitant moet zijn verbonden met een zone**. Als het IP adres van de exploitant tot de waaier behoort die door de streek wordt bepaald, kan de exploitant aan de instantie het programma openen.\
>Het IP van de exploitant adres kan in verscheidene streken worden bepaald. In dit geval ontvangt de exploitant de **set** van de beschikbare rechten voor elke zone.

De out-of-the-box **serverConf.xml** bestand bevat drie zones: **public, VPN en LAN**.

>[!NOTE]
>
>**De uit-van-de-doos configuratie is veilig**. Het kan echter nodig zijn de beveiliging tijdelijk te verlagen om de nieuwe regels te migreren en goed te keuren, voordat een eerdere versie van Adobe Campaign naar een andere versie gaat.

Voorbeeld van het definiëren van een zone in het deelvenster **serverConf.xml** bestand:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" name="public">
<subNetwork label="All addresses" mask="*" name="all"/>

<securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)"
              name="vpn" showErrors="true">

  <securityZone allowDebug="true" allowEmptyPassword="true" allowHTTP="true"
                allowUserPassword="false" label="Private Network (LAN)" name="lan"
                sessionTokenOnly="true" showErrors="true">
    <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
    <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
    <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
    <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
    <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
    <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  </securityZone>

</securityZone>
</securityZone>
```

Alle rechten die een zone definiëren, zijn als volgt:

* **allowDebug**: schakelt een webApp in om te worden uitgevoerd in de modus &quot;foutopsporing&quot;
* **allowEmptyPassword**: Hiermee wordt een verbinding met een instantie zonder wachtwoord toegestaan
* **allowHTTP**: een sessie kan worden gemaakt zonder het HTTPS-protocol te gebruiken
* **allowUserPassword**: het sessietoken kan de volgende vorm hebben &quot;`<login>/<password>`&quot;
* **sessionTokenOnly**: het beveiligingstoken is niet vereist in de verbindings-URL
* **showErrors**: fouten aan de serverzijde worden doorgestuurd en weergegeven

>[!IMPORTANT]
>
>In een streekdefinitie, elk attribuut met **true** waarde vermindert de beveiliging.

Wanneer het gebruiken van het Centrum van het Bericht, als er verscheidene uitvoeringsinstanties zijn, moet u een extra veiligheidsstreek met tot stand brengen **sessionTokenOnly** kenmerk gedefinieerd als **true**, waarbij alleen de noodzakelijke IP-adressen moeten worden toegevoegd. Raadpleeg voor meer informatie over het configureren van instanties [dit document](../../message-center/using/configuring-instances.md).

## Aanbevolen procedures voor beveiligingszones {#best-practices-for-security-zones}

In de definitie van **lan** veiligheidszone, is het mogelijk om een IP adresmasker toe te voegen dat technische toegang bepaalt. Hierdoor wordt toegang mogelijk tot alle instanties die op de server worden gehost.

```
<securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true"
                    allowUserPassword="false" label="Private Network (LAN)" name="lan"
                    sessionTokenOnly="true" showErrors="true">
        <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
        <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
        <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
        <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
        <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
        <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  
        <!-- Customer internal IPs -->
        <subNetwork id="internalNetwork" mask="a.b.c.d/xx"/>

      </securityZone>
```

Wij adviseren direct bepalend IP adreswaaiers in het configuratiedossier dat aan de instantie voor exploitanten wordt gewijd die tot slechts een specifieke instantie toegang hebben.

In de **`config-<instance>.xml`** bestand:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## Subnetwerken en proxy&#39;s in een beveiligingszone {#sub-networks-and-proxies-in-a-security-zone}

De **proxy** parameter kan worden gebruikt in een **subNetwork** -element om het proxygebruik in een beveiligingszone op te geven.

Wanneer naar een proxy wordt verwezen en een verbinding via deze proxy wordt ingeschakeld (zichtbaar via de HTTP X-Forwarded-For-header), is de geverifieerde zone die van de clients van de proxy en niet die van de proxy.

>[!IMPORTANT]
>
>Als een volmacht wordt gevormd en het mogelijk is om het (of het als niet bestaat) met voeten te treden, zal het IP adres dat zal worden getest kunnen worden vervalst.
>
>Bovendien worden nu relais gegenereerd als proxy&#39;s. U kunt daarom het IP adres 127.0.0.1 aan de lijst van volmachten in uw configuratie van de veiligheidszone toevoegen.
>
>Bijvoorbeeld: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

Er kunnen verschillende gevallen optreden:

* Een subnetwerk wordt direct van verwijzingen voorzien in de veiligheidsstreek en geen volmacht wordt gevormd: gebruikers van het subnetwerk kunnen rechtstreeks verbinding maken met de Adobe Campaign-server.

   ![](assets/8101_proxy1.png)

* Een volmacht wordt gespecificeerd voor een subnetwerk in de veiligheidsstreek: gebruikers van dit subnetwerk hebben via deze proxy toegang tot de Adobe Campaign-server.

   ![](assets/8101_proxy2.png)

* Een volmacht is inbegrepen in een subnetwerk van de veiligheidszone: gebruikers die toegang hebben via deze proxy, ongeacht de oorsprong ervan, hebben toegang tot de Adobe Campaign-server.

   ![](assets/8101_proxy3.png)

Het IP-adres van proxy&#39;s die waarschijnlijk toegang zullen krijgen tot de Adobe Campaign-server, moet worden ingevoerd in het dialoogvenster **`<subnetwork>`** betrokken en het eerste niveau subnetwork **`<subnetwork name="all"/>`**. Bijvoorbeeld, hier voor een volmacht de waarvan IP adres 10.131.146.102 is:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" 
                      name="public">
    <subNetwork label="All addresses" mask="*" name="all"
                      proxy="10.131.146.102,127.0.0.1, ::1"/>

    <securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)" 
                      name="vpn" showErrors="true">
        <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" 
                      allowUserPassword="false" label="Private Network (LAN)" 
                      name="lan" sessionTokenOnly="true" showErrors="true">
            <subNetwork label="Lan proxy" mask="10.131.193.182" name="lan3" 
                      proxy="10.131.146.102,127.0.0.1, ::1"/>
            <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" 
                      proxy="127.0.0.1, ::1"/>

        </securityZone>
    </securityZone>
</securityZone>
```

## Een beveiligingszone koppelen aan een operator {#linking-a-security-zone-to-an-operator}

Zodra de streken worden bepaald, moet elke exploitant met één van hen worden verbonden om aan een instantie te kunnen het programma openen en het IP adres van de exploitant moet in de adressen of de waaier van adressen inbegrepen zijn die in de streek van verwijzingen worden voorzien.

De technische configuratie van de zones wordt uitgevoerd in het configuratiebestand van de Campagneserver: **serverConf.xml**.

Voorafgaand aan dit, moet u beginnen door uit-van-de-doos te vormen **[!UICONTROL Security zone]** opsomming voor koppeling van een label aan de interne naam van de zone die is gedefinieerd in het dialoogvenster **serverConf.xml** bestand.

Deze configuratie wordt gedaan in de ontdekkingsreiziger van de Campagne:

1. Klik op de knop **[!UICONTROL Administration > Platform > Enumerations]** knooppunt.
1. Selecteer **[!UICONTROL Security zone (securityZone)]** systeemopsomming.

   ![](assets/enum_securityzone.png)

1. Voor elke die veiligheidsstreek in het configuratiedossier van de server wordt bepaald, klik **[!UICONTROL Add]** knop.
1. In de **[!UICONTROL Internal name]** veld, voert u de naam in van de zone die is gedefinieerd in het dialoogvenster **serverConf.xml** bestand. Het komt overeen met de **@name** kenmerk van de `<securityzone>`  element. Voer het label dat is gekoppeld aan de interne naam in het dialoogvenster  **Label** veld.

   ![](assets/enum_addsecurityvalue.png)

1. Klik op OK en sla de wijzigingen op.

Zodra de zones zijn gedefinieerd en de **[!UICONTROL Security zone]** de opsomming wordt gevormd, moet u elke exploitant aan een veiligheidsstreek verbinden:

1. Klik op de knop **[!UICONTROL Administration > Access management > Operators]** knooppunt.
1. Selecteer de operator waaraan u een beveiligingszone wilt koppelen en klik op de knop **[!UICONTROL Edit]** tab.
1. Ga naar de **[!UICONTROL Access rights]** en klik op de knop **[!UICONTROL Edit access parameters...]** koppeling.

   ![](assets/zone_operator.png)

1. Selecteer een zone in het menu **[!UICONTROL Authorized connection zone]** vervolgkeuzelijst

   ![](assets/zone_operator_selection.png)

1. Klikken **[!UICONTROL OK]** en sla de wijzigingen op om deze wijzigingen toe te passen.



## Aanbevelingen

* Zorg ervoor dat de reverse-proxy niet is toegestaan in subNetwork. Zo ja, **alles** verkeer zal worden ontdekt zoals komend van dit lokale IP, zodat zal worden vertrouwd.

* Gebruik sessionTokenOnly=&quot;true&quot; minimaliseren:

   * Waarschuwing: Als dit kenmerk is ingesteld op true, kan de operator worden blootgesteld aan een **CRSF-aanval**.
   * Bovendien wordt het sessionToken cookie niet ingesteld met een httpOnly-markering, zodat sommige JavaScript-code aan de clientzijde deze kan lezen.
   * Nochtans vereist het Centrum van het Bericht op veelvoudige uitvoeringscellen sessionTokenOnly: creeer een nieuwe veiligheidsstreek met sessionTokenOnly die aan &quot;waar&quot;wordt geplaatst en voeg toe **alleen de benodigde IP(&#39;s)** in deze zone.

* Indien mogelijk, plaats allen allowHTTP, showErrors om vals (niet voor localhost) te zijn en hen te controleren.

   * allowHTTP = &quot;false&quot;: exploitanten dwingen HTTPS te gebruiken
   * showErrors = &quot;false&quot;: Hiermee verbergt u technische fouten (waaronder SQL-fouten). Het verhindert het tonen van teveel informatie, maar vermindert het vermogen voor de teller om fouten op te lossen (zonder om meer informatie van een beheerder te vragen)

* Plaats allowDebug aan waar slechts op IPs die door marketing gebruikers/beheerders wordt gebruikt die (in feite voorproef) onderzoeken, webApps en rapporten moeten tot stand brengen. Deze vlag staat deze IPs toe om relaisregels te krijgen die worden getoond en hen te zuiveren.

   * Wanneer allowDebug is ingesteld op false, wordt de uitvoer als volgt ingesteld:

      ```
      <redir status='OK' date='...' sourceIP='...'/>
      ```

   * Wanneer allowDebug op true is ingesteld, wordt de uitvoer als volgt uitgevoerd:

      ```
      <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
      ```

* Stel allowEmptyPassword, allowUserPassword, allowSQLInjection nooit in op true. Deze kenmerken zijn alleen hier voor een vloeiende migratie vanaf v5 en v6.0:

   * **allowEmptyPassword** Laat exploitanten een leeg wachtwoord hebben. Als dit voor u het geval is, breng al uw exploitanten op de hoogte om hen te vragen om een wachtwoord met een deadline te plaatsen. Als deze deadline is verstreken, wijzigt u dit kenmerk in false.

   * **allowUserPassword** Laat exploitanten hun geloofsbrieven als parameters verzenden (zodat zullen zij door apache/IIS/proxy worden geregistreerd). Deze functie is in het verleden gebruikt om het gebruik van de API te vereenvoudigen. U kunt in uw kookboek (of in de specificatie) controleren of sommige derdetoepassingen dit gebruiken. Als dat het geval is, moet u de gebruiker een melding sturen om de manier waarop hij of zij de API gebruikt te wijzigen en deze functie zo snel mogelijk verwijderen.

   * **allowSQLInjection** Hiermee kan de gebruiker SQL-injecties uitvoeren met een oude syntaxis. Dit kenmerk moet op false worden ingesteld. U kunt /nl/jsp/ping.jsp gebruiken?zones=true om uw configuratie van de veiligheidsstreek te controleren. Deze pagina toont de actieve status van veiligheidsmaatregelen (die met deze veiligheidsvlaggen worden gegevens verwerkt) voor huidige IP.

* HttpOnly cookie/useSecurityToken: verwijzen naar **sessionTokenOnly** markering.

* Minimaliseer IPs die aan de lijst van gewenste personen wordt toegevoegd: Uit de doos, in veiligheidszones, hebben wij de 3 waaiers voor privé netwerken toegevoegd. Het is onwaarschijnlijk dat u al deze IP adressen zult gebruiken. Bewaar dus alleen die dingen die je nodig hebt.

* webApp/internal-operator bijwerken zodat deze alleen toegankelijk is in localhost.
