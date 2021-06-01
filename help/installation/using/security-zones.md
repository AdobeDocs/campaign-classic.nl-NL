---
product: campaign
title: Beveiligingszones configureren
description: Leer hoe u beveiligingszones kunt configureren
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1462'
ht-degree: 0%

---


# Beveiligingszones definiëren (op locatie){#defining-security-zones}

Elke exploitant moet met een streek worden verbonden om aan een geval te login en exploitant IP moet in de adressen of adresreeksen worden omvat die in de veiligheidsstreek worden bepaald. Configuratie van de beveiligingszone wordt uitgevoerd in het configuratiebestand van de Adobe Campaign-server.

Operatoren zijn verbonden met een beveiligingszone vanuit het profiel in de console, toegankelijk via het knooppunt **[!UICONTROL Administration > Access management > Operators]**. [Meer informatie](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>Deze procedure is beperkt tot **on-premise** plaatsingen.
>
>Als **ontvangen** klant, als u tot [Controlebord van de Campagne](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html) kunt toegang hebben, kunt u de zelfdienstinterface van de Zone van de Veiligheid gebruiken. [Meer informatie](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html)
>
>Andere **hybride/gehoste** klanten moeten zich tot het ondersteuningsteam van Adobe richten om IP aan de lijst van gewenste personen toe te voegen.


## Beveiligingszones maken {#creating-security-zones}

Een zone wordt gedefinieerd door:

* één of meerdere waaiers van IP adressen (IPv4 en IPv6)
* een technische naam verbonden aan elke waaier van IP adressen

Beveiligingszones zijn onderling vergrendeld, wat betekent dat het definiëren van een nieuwe zone binnen een andere zone het aantal operatoren verlaagt dat zich daarop kan aanmelden, terwijl de rechten die aan elke operator zijn toegewezen, worden vergroot.

De zones moeten tijdens serverconfiguratie, in **serverConf.xml** dossier worden bepaald. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in [deze sectie](../../installation/using/the-server-configuration-file.md).

Elke zone definieert rechten, zoals:

* HTTP-verbinding in plaats van HTTPS
* Foutweergave (Java-fouten, JavaScript, C++, enz.)
* Voorvertoning van rapport en webApp
* Verificatie via aanmelding/wachtwoord
* Niet-beveiligde verbindingsmodus

>[!NOTE]
>
>**Elke exploitant moet met een zone** worden verbonden. Als het IP adres van de exploitant tot de waaier behoort die door de streek wordt bepaald, kan de exploitant aan de instantie het programma openen.\
>Het IP van de exploitant adres kan in verscheidene streken worden bepaald. In dit geval ontvangt de operator de **set** beschikbare rechten voor elke zone.

Het uit-van-de-doos **serverConf.xml** dossier omvat drie streken: **public, VPN en LAN**.

>[!NOTE]
>
>**De uit-van-de-doos configuratie is veilig**. Het kan echter nodig zijn de beveiliging tijdelijk te verlagen om de nieuwe regels te migreren en goed te keuren, voordat een eerdere versie van Adobe Campaign naar een andere versie gaat.

Voorbeeld van het definiëren van een zone in het bestand **serverConf.xml**:

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
* **allowUserPassword**: het zittingsteken kan de volgende vorm &quot;`<login>/<password>`&quot;hebben
* **sessionTokenOnly**: het beveiligingstoken is niet vereist in de verbindings-URL
* **showErrors**: fouten aan de serverzijde worden doorgestuurd en weergegeven

>[!IMPORTANT]
>
>In een streekdefinitie, vermindert elk attribuut met **true** waarde veiligheid.

Wanneer het gebruiken van het Centrum van het Bericht, als er verscheidene uitvoeringsinstanties zijn, moet u een extra veiligheidsstreek met **sessionTokenOnly** attributen tot stand brengen die als **true** worden bepaald, waar slechts de noodzakelijke IP adressen moeten worden toegevoegd. Raadpleeg [dit document](../../message-center/using/configuring-instances.md) voor meer informatie over het configureren van instanties.

## Aanbevolen procedures voor beveiligingszones {#best-practices-for-security-zones}

In de definitie van **lan** veiligheidsstreek, is het mogelijk om een IP adresmasker toe te voegen dat technische toegang bepaalt. Hierdoor wordt toegang mogelijk tot alle instanties die op de server worden gehost.

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

In het **`config-<instance>.xml`**-bestand:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## Subnetwerken en proxy&#39;s in een beveiligingszone {#sub-networks-and-proxies-in-a-security-zone}

De **proxy** parameter kan in een **subNetwork** element worden gebruikt om volmachtsgebruik in een veiligheidsstreek te specificeren.

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

De IP adressen van volmachten die waarschijnlijk tot de server van Adobe Campaign zullen toegang hebben moeten in zowel **`<subnetwork>`** betrokken als eerste niveau subnetwork **`<subnetwork name="all"/>`** zijn ingegaan. Bijvoorbeeld, hier voor een volmacht de waarvan IP adres 10.131.146.102 is:

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

Voorafgaand aan dit, moet u beginnen door de uit-van-de-doos **[!UICONTROL Security zone]** opsomming te vormen om een etiket met de interne naam van de streek te verbinden die in **serverConf.xml** dossier wordt bepaald.

Deze configuratie wordt gedaan in de ontdekkingsreiziger van de Campagne:

1. Klik op het knooppunt **[!UICONTROL Administration > Platform > Enumerations]**.
1. Selecteer de **[!UICONTROL Security zone (securityZone)]** systeemopsomming.

   ![](assets/enum_securityzone.png)

1. Voor elke veiligheidsstreek die in het configuratiedossier van de server wordt bepaald, klik **[!UICONTROL Add]** knoop.
1. Voer in het veld **[!UICONTROL Internal name]** de naam in van de zone die is gedefinieerd in het bestand **serverConf.xml**. Het komt overeen met het **@name**-kenmerk van het `<securityzone>`-element. Typ het label dat is gekoppeld aan de interne naam in het veld **Label**.

   ![](assets/enum_addsecurityvalue.png)

1. Klik op OK en sla de wijzigingen op.

Zodra de streken worden bepaald en de **[!UICONTROL Security zone]** opsomming wordt gevormd, moet u elke exploitant aan een veiligheidsstreek verbinden:

1. Klik op het knooppunt **[!UICONTROL Administration > Access management > Operators]**.
1. Selecteer de operator waaraan u een beveiligingszone wilt koppelen en klik op het tabblad **[!UICONTROL Edit]**.
1. Ga naar het **[!UICONTROL Access rights]** lusje en klik **[!UICONTROL Edit access parameters...]** verbinding.

   ![](assets/zone_operator.png)

1. Selecteer een zone in de vervolgkeuzelijst **[!UICONTROL Authorized connection zone]**

   ![](assets/zone_operator_selection.png)

1. Klik op **[!UICONTROL OK]** en sla de wijzigingen op om deze wijzigingen toe te passen.



## Aanbevelingen

* Zorg ervoor dat de reverse-proxy niet is toegestaan in subNetwork. Als het het geval is, zal **all** verkeer worden ontdekt zoals komend van dit lokale IP, zodat zal worden vertrouwd.

* Gebruik sessionTokenOnly=&quot;true&quot; minimaliseren:

   * Waarschuwing: Als dit attribuut aan waar wordt geplaatst, kan de exploitant aan een **CRSF aanval** worden blootgesteld.
   * Bovendien wordt het sessionToken koekje niet geplaatst met een markering httpOnly, zodat kan sommige cliënt-kant javascript code het lezen.
   * Nochtans vereist het Centrum van het Bericht op veelvoudige uitvoeringscellen sessionTokenOnly: creeer een nieuwe veiligheidsstreek met sessionTokenOnly die aan &quot;waar&quot;wordt geplaatst en voeg **slechts noodzakelijke IP(s)** in deze streek toe.

* Indien mogelijk, plaats allen allowHTTP, showErrors om vals (niet voor localhost) te zijn en hen te controleren.

   * allowHTTP = &quot;false&quot;: exploitanten dwingen HTTPS te gebruiken
   * showErrors = &quot;false&quot;: Hiermee verbergt u technische fouten (waaronder SQL-fouten). Het verhindert het tonen van teveel informatie, maar vermindert het vermogen voor de teller om fouten op te lossen (zonder om meer informatie van een beheerder te vragen)

* Plaats allowDebug aan waar slechts op IPs die door marketing gebruikers/beheerders wordt gebruikt die (in feite voorproef) onderzoeken, webApps en rapporten moeten tot stand brengen. Deze vlag staat deze IPs toe om relaisregels te krijgen die worden getoond en hen te zuiveren.

* Stel allowEmptyPassword, allowUserPassword, allowSQLInjection nooit in op true. Deze kenmerken zijn alleen hier voor een vloeiende migratie vanaf v5 en v6.0:

   * **Operatoren** allowEmptyPasswordlets hebben een leeg wachtwoord. Als dit voor u het geval is, breng al uw exploitanten op de hoogte om hen te vragen om een wachtwoord met een deadline te plaatsen. Als deze deadline is verstreken, wijzigt u dit kenmerk in false.

   * **Operatoren** allowUserPasswordlets verzenden hun gegevens als parameters (zodat deze door apache/IIS/proxy worden geregistreerd). Deze functie is in het verleden gebruikt om het gebruik van de API te vereenvoudigen. U kunt in uw kookboek (of in de specificatie) controleren of sommige derdetoepassingen dit gebruiken. Als dat het geval is, moet u de gebruiker een melding sturen om de manier waarop hij of zij de API gebruikt te wijzigen en deze functie zo snel mogelijk verwijderen.

   * **Met** allowSQLInjectionnlets kan de gebruiker SQL-injecties uitvoeren met behulp van een oude syntaxis. Voer zo snel mogelijk de correcties uit die in [deze pagina](../../migration/using/general-configurations.md) worden beschreven om deze eigenschap aan vals te kunnen plaatsen. U kunt /nl/jsp/ping.jsp gebruiken?zones=true om uw configuratie van de veiligheidsstreek te controleren. Deze pagina toont de actieve status van veiligheidsmaatregelen (die met deze veiligheidsvlaggen worden gegevens verwerkt) voor huidige IP.

* HttpOnly cookie/useSecurityToken: verwijs naar **sessionTokenOnly** vlag.

* Minimaliseer IPs die aan de lijst van gewenste personen wordt toegevoegd: Uit de doos, in veiligheidszones, hebben wij de 3 waaiers voor privé netwerken toegevoegd. Het is onwaarschijnlijk dat u al deze IP adressen zult gebruiken. Bewaar dus alleen die dingen die je nodig hebt.

* webApp/internal-operator bijwerken zodat deze alleen toegankelijk is in localhost.
