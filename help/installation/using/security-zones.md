---
product: campaign
title: Beveiligingszones configureren
description: Leer hoe u beveiligingszones kunt configureren
feature: Installation, Instance Settings
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1452'
ht-degree: 0%

---

# Beveiligingszones definiëren (op locatie){#defining-security-zones}



Elke exploitant moet met een streek worden verbonden om aan een geval te login en exploitant IP moet in de adressen of adresreeksen worden omvat die in de veiligheidsstreek worden bepaald. Configuratie van de beveiligingszone wordt uitgevoerd in het configuratiebestand van de Adobe Campaign-server.

Operatoren zijn vanuit hun profiel in de console gekoppeld aan een beveiligingszone, die toegankelijk is in het knooppunt **[!UICONTROL Administration > Access management > Operators]** . [Meer informatie](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>Deze procedure wordt beperkt tot **op-gebouw** plaatsingen.
>
>Als a **ontvangen** klant, als u tot [ het Controlebord van de Campagne ](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=nl) kunt toegang hebben, kunt u de zelfdienstinterface van de Zone van de Veiligheid gebruiken. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html)
>
>Andere **hybride/ontvangen** klanten moeten uit bereiken aan het team van de steun van de Adobe om IP aan de lijst van gewenste personen toe te voegen.
>

## Beveiligingszones maken {#creating-security-zones}

Een zone wordt gedefinieerd door:

* één of meerdere waaiers van IP adressen (IPv4 en IPv6)
* een technische naam verbonden aan elke waaier van IP adressen

Beveiligingszones zijn onderling vergrendeld, wat betekent dat het definiëren van een nieuwe zone binnen een andere zone het aantal operatoren verlaagt dat zich daarop kan aanmelden, terwijl de rechten die aan elke operator zijn toegewezen, worden vergroot.

De gebieden moeten tijdens serverconfiguratie, in het **serverConf.xml** dossier worden bepaald. Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in [ deze sectie ](../../installation/using/the-server-configuration-file.md).

Elke zone definieert rechten, zoals:

* HTTP-verbinding in plaats van HTTPS
* Foutweergave (Java-fouten, JavaScript, C++, enz.)
* Voorvertoning van rapport en webApp
* Verificatie via inlognaam/wachtwoord
* Niet-beveiligde verbindingsmodus

>[!NOTE]
>
>**elke exploitant moet met een streek** worden verbonden. Als het IP adres van de exploitant tot de waaier behoort die door de streek wordt bepaald, kan de exploitant aan de instantie het programma openen.\
>Het IP van de exploitant adres kan in verscheidene streken worden bepaald. In dit geval, ontvangt de exploitant de **reeks** van beschikbare rechten voor elke streek.

Het uit-van-de-doos **serverConf.xml** dossier omvat drie streken: **openbaar, VPN, en LAN**.

>[!NOTE]
>
>**de uit-van-de-doos configuratie is veilig**. Het kan echter nodig zijn de beveiliging tijdelijk te verlagen om de nieuwe regels te migreren en goed te keuren, voordat een eerdere versie van Adobe Campaign naar een andere versie gaat.

Voorbeeld van hoe te om een streek in het {**dossier te bepalen 0} serverConf.xml:**

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

* **allowDebug**: laat een webApp toe om op &quot;te worden uitgevoerd zuiveren&quot;wijze
* **allowEmptyPassword**: keurt een verbinding aan een instantie zonder een wachtwoord goed
* **allowHTTP**: Een zitting kan worden gecreeerd zonder het protocol te gebruiken HTTPS
* **allowUserPassword**: Het zittingsteken kan de volgende vorm &quot;`<login>/<password>`&quot; hebben
* **sessionTokenOnly**: het veiligheidsteken wordt niet vereist in de verbinding URL
* **showErrors**: De fouten op de serverkant door:sturen en getoond

>[!IMPORTANT]
>
>In een streekdefinitie, vermindert elk attribuut met de **ware** waarde veiligheid.

Wanneer het gebruiken van het Centrum van het Bericht, als er verscheidene uitvoeringsinstanties zijn, moet u een extra veiligheidsstreek met het **sessionTokenOnly** attribuut tot stand brengen dat als **waar** wordt bepaald, waar slechts de noodzakelijke IP adressen moeten worden toegevoegd. Voor meer bij het vormen van instanties, verwijs naar [ dit document ](../../message-center/using/configuring-instances.md).

## Aanbevolen procedures voor beveiligingszones {#best-practices-for-security-zones}

In de definitie van de **LAN** veiligheidsstreek, is het mogelijk om een IP adresmasker toe te voegen dat technische toegang bepaalt. Hierdoor wordt toegang mogelijk tot alle instanties die op de server worden gehost.

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

In het **`config-<instance>.xml`** -bestand:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## Subnetwerken en proxy&#39;s in een beveiligingszone {#sub-networks-and-proxies-in-a-security-zone}

De **volmacht** parameter kan in a **subNetwork** element worden gebruikt om volmachtsgebruik in een veiligheidsstreek te specificeren.

Wanneer naar een proxy wordt verwezen en een verbinding via deze proxy wordt ingeschakeld (zichtbaar via de HTTP X-Forwarded-For-header), is de geverifieerde zone die van de clients van de proxy en niet die van de proxy.

>[!IMPORTANT]
>
>Als een volmacht wordt gevormd en het mogelijk is om het (of het als niet bestaat) met voeten te treden, zal het IP adres dat zal worden getest kunnen worden vervalst.
>
>Bovendien worden nu relais gegenereerd als proxy&#39;s. U kunt daarom het IP adres 127.0.0.1 aan de lijst van volmachten in uw configuratie van de veiligheidszone toevoegen.
>
>Bijvoorbeeld: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

Er kunnen verschillende gevallen optreden:

* Er wordt rechtstreeks verwezen naar een subnetwerk in de beveiligingszone en er wordt geen proxy geconfigureerd: gebruikers van het subnetwerk kunnen rechtstreeks verbinding maken met de Adobe Campaign-server.

  ![](assets/8101_proxy1.png)

* Er is een proxy opgegeven voor een subnetwerk in de beveiligingszone: gebruikers van dit subnetwerk hebben via deze proxy toegang tot de Adobe Campaign-server.

  ![](assets/8101_proxy2.png)

* Een proxy is opgenomen in een subnetwerk voor een beveiligingszone: gebruikers die toegang hebben via deze proxy, ongeacht hun oorsprong, hebben toegang tot de Adobe Campaign-server.

  ![](assets/8101_proxy3.png)

Het IP-adres van proxy&#39;s die waarschijnlijk toegang zullen krijgen tot de Adobe Campaign-server, moet worden ingevoerd in zowel het betreffende **`<subnetwork>`** als het eerste niveau van subnetwork **`<subnetwork name="all"/>`** . Bijvoorbeeld, hier voor een volmacht de waarvan IP adres 10.131.146.102 is:

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

De technische configuratie van de streken wordt uitgevoerd in het configuratiedossier van de Server van de Campagne: **serverConf.xml**.

Voorafgaand aan dit, moet u beginnen door de uit-van-de-doos **[!UICONTROL Security zone]** opsomming te vormen om een etiket aan de interne naam van de streek te verbinden die in het **wordt bepaald serverConf.xml** dossier.

Deze configuratie wordt gedaan in de ontdekkingsreiziger van de Campagne:

1. Klik op het knooppunt **[!UICONTROL Administration > Platform > Enumerations]** .
1. Selecteer de systeemopsomming **[!UICONTROL Security zone (securityZone)]** .

   ![](assets/enum_securityzone.png)

1. Klik op de knop **[!UICONTROL Add]** voor elke beveiligingszone die is gedefinieerd in het configuratiebestand van de server.
1. Op het **[!UICONTROL Internal name]** gebied, ga de naam van de streek in die in het **wordt bepaald serverConf.xml** dossier. Het komt overeen met het kenmerk **@name** van het element `<securityzone>` . Ga het etiket verbonden met de interne naam op het **Etiket** gebied in.

   ![](assets/enum_addsecurityvalue.png)

1. Klik op OK en sla de wijzigingen op.

Zodra de streken worden bepaald en de **[!UICONTROL Security zone]** opsomming wordt gevormd, moet u elke exploitant aan een veiligheidsstreek verbinden:

1. Klik op het knooppunt **[!UICONTROL Administration > Access management > Operators]** .
1. Selecteer de operator waaraan u een beveiligingszone wilt koppelen en klik op de tab **[!UICONTROL Edit]** .
1. Ga naar de tab **[!UICONTROL Access rights]** en klik op de koppeling **[!UICONTROL Edit access parameters...]** .

   ![](assets/zone_operator.png)

1. Een zone selecteren in de vervolgkeuzelijst **[!UICONTROL Authorized connection zone]**

   ![](assets/zone_operator_selection.png)

1. Klik op **[!UICONTROL OK]** en sla de wijzigingen op om deze wijzigingen toe te passen.



## Aanbevelingen

* Zorg ervoor dat de reverse-proxy niet is toegestaan in subNetwork. Als het het geval is, **zal al** verkeer zoals komend van dit lokale IP worden ontdekt, zodat zal worden vertrouwd.

* Gebruik sessionTokenOnly=&quot;true&quot; minimaliseren:

   * Waarschuwing: Als dit attribuut aan waar wordt geplaatst, kan de exploitant aan de aanval van a **worden blootgesteld CRSF**.
   * Bovendien wordt het sessionToken koekje niet geplaatst met een markering httpOnly, zodat kan sommige cliënt-kant JavaScript code het lezen.
   * Nochtans heeft het Centrum van het Bericht op veelvoudige uitvoeringscellen sessionTokenOnly nodig: creeer een nieuwe veiligheidsstreek met sessionTokenOnly die aan &quot;waar&quot;wordt geplaatst en voeg **slechts noodzakelijke IP(s)** in deze streek toe.

* Indien mogelijk, plaats allen allowHTTP, showErrors om vals (niet voor localhost) te zijn en hen te controleren.

   * allowHTTP = &quot;false&quot;: hiermee worden operators gedwongen HTTPS te gebruiken
   * showErrors = &quot;false&quot;: verbergt technische fouten (inclusief SQL-fouten). Het verhindert het tonen van teveel informatie, maar vermindert het vermogen voor de teller om fouten op te lossen (zonder om meer informatie van een beheerder te vragen)

* Plaats allowDebug aan waar slechts op IPs die door marketing gebruikers/beheerders wordt gebruikt die (in feite voorproef) onderzoeken, webApps en rapporten moeten tot stand brengen. Deze vlag staat deze IPs toe om relaisregels te krijgen die worden getoond en hen te zuiveren.

   * Wanneer allowDebug is ingesteld op false, wordt de uitvoer als volgt ingesteld:

     ```
     <redir status='OK' date='...' sourceIP='...'/>
     ```

   * Wanneer allowDebug op true is ingesteld, wordt de uitvoer als volgt uitgevoerd:

     ```
     <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
     ```

* Stel allowEmptyPassword, allowUserPassword, allowSQLInjection nooit in op true.

   * **allowEmptyPassword** laat exploitanten een leeg wachtwoord hebben. Als dit voor u het geval is, breng al uw exploitanten op de hoogte om hen te vragen om een wachtwoord met een deadline te plaatsen. Als deze deadline is verstreken, wijzigt u dit kenmerk in false.

   * **allowUserPassword** laat exploitanten hun geloofsbrieven als parameters verzenden (zodat zullen zij door apache/IIS/volmacht worden geregistreerd). Deze functie is in het verleden gebruikt om het gebruik van de API te vereenvoudigen. U kunt in uw kookboek (of in de specificatie) controleren of sommige derdetoepassingen dit gebruiken. Als dat het geval is, moet u de gebruiker een melding sturen om de manier waarop hij of zij de API gebruikt te wijzigen en deze functie zo snel mogelijk verwijderen.

   * **allowSQLInjection** laat de gebruiker SQL injecties uitvoeren door een oude syntaxis te gebruiken. Dit kenmerk moet op false worden ingesteld. U kunt /nl/jsp/ping.jsp gebruiken?zones=true om uw configuratie van de veiligheidsstreek te controleren. Deze pagina toont de actieve status van veiligheidsmaatregelen (die met deze veiligheidsvlaggen worden gegevens verwerkt) voor huidige IP.

* HttpOnly koekje/useSecurityToken: verwijs naar **sessionTokenOnly** vlag.

* Minimaliseer IPs die aan de lijst van gewenste personen wordt toegevoegd: Uit de doos, in veiligheidsstreken, hebben wij de 3 waaiers voor privé netwerken toegevoegd. Het is onwaarschijnlijk dat u al deze IP adressen zult gebruiken. Bewaar dus alleen die dingen die je nodig hebt.

* webApp/internal-operator bijwerken zodat deze alleen toegankelijk is in localhost.
