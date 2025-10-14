---
product: campaign
title: Technische e-mailconfiguratie
description: Leer hoe u Campagne configureert om de uitvoer van uw instanties te beheren bij het verzenden van e-mails
feature: Installation, Deliverability
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '3096'
ht-degree: 0%

---

# Technische e-mailconfiguraties{#email-deliverability}



## Overzicht {#overview}

In de volgende sectie vindt u een overzicht van de configuratie die is vereist voor het beheer van de uitvoer van Adobe Campaign-instanties bij het verzenden van e-mails.

>[!NOTE]
>
>Sommige configuraties kunnen alleen door Adobe worden uitgevoerd voor implementaties die door Adobe worden gehost, bijvoorbeeld voor toegang tot de server- en instantieconfiguratiebestanden. Om meer over de verschillende plaatsingen te leren, verwijs naar [ Hosting modellen ](../../installation/using/hosting-models.md) sectie of [ deze pagina ](../../installation/using/capability-matrix.md).

Voor meer op de concepten en de beste praktijken met betrekking tot leverbaarheid met Adobe Campaign, verwijs naar dit [ sectie ](../../delivery/using/about-deliverability.md).

Voor een diepere duik op wat de leverbaarheid is, met inbegrip van alle technische aanbevelingen betreffende het efficiënte verzenden van en het ontvangen van e-mails door een platform van Adobe, verwijs naar de [ Gids van de Beste praktijken van de Levering van Adobe ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl).

## Werkwijze {#operating-principle}

Het is mogelijk om de uitvoer van een of meer Adobe Campaign-instanties te beheren om het aantal verzonden e-mails te beperken, afhankelijk van een domein. Bijvoorbeeld, kunt u de output tot 20.000 per uur voor **yahoo.com** adressen beperken, terwijl het vormen van 100.000 berichten per uur voor alle andere domeinen.

De output van het bericht moet voor elk IP adres worden gecontroleerd dat door de leveringsservers (**wordt gebruikt mta**). Verscheidene **mta** verdeeld over verscheidene machines en die tot diverse instanties behoren van Adobe Campaign kunnen het zelfde IP adres voor e-maillevering delen: een proces moet opstelling zijn om het gebruik van deze IP adressen te coördineren.

Dit is wat de **staat** module doet: het door:sturen alle verbindingsverzoeken en berichten die naar de postservers voor een reeks IP adressen moeten worden verzonden. De statistiekserver houdt leveringen bij en kan verzending op basis van ingestelde quota in- of uitschakelen.

![](assets/s_ncs_install_mta.png)

* De statistiekserver (**staat**) is verbonden met een basis van Adobe Campaign om zijn configuratie te laden.
* De leveringsservers (**mta**) gebruiken UDP om een statistiekserver te contacteren die niet altijd tot hun eigen instantie behoort.

### Leveringsservers {#delivery-servers}

De **mta** module verdeelt berichten aan zijn **mtachild** kindmodules. Elk **mtachild** bereidt berichten voor alvorens om een vergunning van de statistiekserver te verzoeken, en hen te verzenden.

De stappen zijn als volgt:

1. **mta** selecteert in aanmerking komende berichten en wijst hen een beschikbaar **mtachild** toe.
1. **mtachild** laadt alle informatie die voor de bouw van het bericht (inhoud, verpersoonlijkingselementen, gehechtheid, beelden, enz.) wordt vereist en door:sturen het bericht aan de **Verkeer E-mailShaper**.
1. Zodra de vormer van het e-mailverkeer de vergunning van de statistiekserver (**smtp staat**) ontvangt, wordt het bericht verzonden naar de ontvanger.

![](assets/s_ncs_install_email_traffic_shaper.png)

### Statistieken en beperkingen van e-mailservers {#email-server-statistics-and-limitations}

De statistische server onderhoudt de volgende statistieken voor elke e-mailserver die berichten ontvangt:

* Aantal open point-in-time verbindingen,
* Aantal verzonden berichten in het laatste uur,
* Snelheid van geslaagde/geweigerde verbindingen,
* Het tarief van verbindingen aan onbereikbare servers.

Tegelijkertijd laadt de module een lijst met beperkingen voor bepaalde e-mailservers:

* maximumaantal gelijktijdige aansluitingen,
* Maximum aantal berichten per uur,
* Maximum aantal berichten per verbinding.

### IP-adressen beheren {#managing-ip-addresses}

De statistiekserver kan verscheidene instanties of verscheidene machines met het zelfde openbare IP adres combineren. Het is daarom niet verbonden met een specifieke instantie, maar het moet een instantie contacteren om beperkingen per domein terug te krijgen.

De statistieken van de levering worden gehouden voor elke doel MX en voor elke bronIP. Als het doeldomein bijvoorbeeld 5 MX heeft en het platform 3 verschillende IP-adressen kan gebruiken, kan de server maximaal 15 reeksen indicatoren voor dit domein beheren.

Het bronIP adres past het openbare IP adres, d.w.z. het adres aan zoals het door de verre e-mailserver wordt gezien. Dit IP adres kan van het adres van de machine verschillend zijn die gastheren **mta**, als een NATIONAAL router wordt verstrekt. Dit is waarom de statistiekserver een herkenningsteken gebruikt dat openbare IP (**publicId**) aanpast. De vereniging tussen het lokale adres en dit herkenningsteken wordt verklaard in het **serverConf.xml** configuratiedossier. Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in deze [ sectie ](../../installation/using/the-server-configuration-file.md).

## Uitvoercontrole van levering {#delivery-output-controlling}

Om berichten aan e-mailservers te leveren, verzoekt de **component van de Verkeer 0} E-mailShapier van het Verkeer een verbinding van de statistiekenserver.** Nadat het verzoek is geaccepteerd, wordt de verbinding geopend.

Voordat de berichten worden verzonden, vraagt de module &#39;tokens&#39; van de server. Dit zijn over het algemeen reeksen van minstens 10 tokens, die het aantal vragen aan de server verminderen.

De server slaat alle statistieken op met betrekking tot verbindingen en leveringen. In geval van het opnieuw opstarten, wordt de informatie tijdelijk verloren: elke cliënt houdt een lokaal exemplaar van hun verzendende statistieken bij en keert hen aan de server op regelmatige basis (om de 2 minuten) terug. De server kan de gegevens vervolgens opnieuw samenvoegen.

De volgende secties beschrijven de verwerking van een bericht door de **component van de Shapier van het Verkeer E-mail**.

### Berichtlevering {#message-delivery}

Wanneer een bericht wordt verzonden, zijn er 3 mogelijke resultaten:

1. **Succes**: het bericht werd met succes verzonden. Het bericht wordt bijgewerkt.
1. **Ontbroken Bericht**: De gecontacteerde server verwierp het bericht voor de gekozen ontvanger. Dit resultaat komt overeen met de retourcodes 550 tot en met 599, maar er kunnen uitzonderingen worden gedefinieerd.
1. **Ontbroken Zitting** (voor 5.11): als **mta** een antwoord voor dit bericht ontvangt, wordt het bericht verlaten (verwijs naar [ Verlaten van het Bericht ](#message-abandonment)). Het bericht wordt verzonden naar een andere weg of geplaatst aan hangend als geen andere wegen beschikbaar zijn (verwijs naar [ Bestaand Bericht ](#message-pending)).

   >[!NOTE]
   >
   >A **weg** is een verbinding tussen Adobe Campaign **mta** en het doel **mta**. De Adobe Campaign **mta** kan van verscheidene beginIPs en verscheidene doelIPs kiezen.

### Berichten verlaten {#message-abandonment}

Verlaten berichten zijn teruggekeerd aan **mta** en niet meer door **mtachild** beheerd.

**mta** beslist over de procedure voor dit bericht (terugwinning, beëindiging, quarantaine, enz.) afhankelijk van de reactiecode en de regels.

### Bericht in behandeling {#message-pending}

Een bericht wordt toegevoegd wanneer het in de actieve rij aankomt en er geen beschikbare wegen zijn.

Een pad wordt doorgaans als niet beschikbaar gemarkeerd voor een variabele hoeveelheid tijd na een verbindingsfout. De periode van onbeschikbaarheid is afhankelijk van de frequentie en leeftijd van fouten.

## Configuratie van de Statistieken-server {#statistics-server-configuration}

De statistiekenserver kan door verscheidene instanties worden gebruikt: het moet onafhankelijk van de instanties worden gevormd die het zullen gebruiken.

Begin door het gegevensbestand te bepalen van Adobe Campaign dat de configuratie zal ontvangen.

### Configuratie starten {#start-configuration}

Door gebrek, is de **staat** module begonnen voor elke instantie. Wanneer de instanties op de zelfde machine worden samengevoegd, of wanneer de instanties het zelfde IP adres delen, wordt één enkele statistiekserver gebruikt: de anderen moeten worden onbruikbaar gemaakt.

### Definitie van de serverpoort {#definition-of-the-server-port}

Door gebrek, luistert de statistiekserver op haven 7777. Deze haven kan in het **serverConf.xml** dossier worden gewijzigd. Alle parameters beschikbaar in **serverConf.xml** zijn vermeld in deze [ sectie ](../../installation/using/the-server-configuration-file.md).

```
<stat port="1234"/>
```

## MX-configuratie {#mx-configuration}

>[!IMPORTANT]
>
>Voor ontvangen of hybride installaties, als u aan [ Verbeterde MTA ](../../delivery/using/sending-with-enhanced-mta.md) hebt bevorderd, worden de **[!UICONTROL MX management]** regels van de leveringsproductie niet meer gebruikt. Verbeterde MTA gebruikt zijn eigen MX regels die het toestaan om uw productie door domein aan te passen die op uw eigen historische e-mailreputatie wordt gebaseerd, en op real time terugkoppelen die uit de domeinen komt waar u e-mails verzendt.

### Informatie over MX-regels {#about-mx-rules}

>[!NOTE]
>
>Deze sectie en de onderstaande secties zijn alleen van toepassing op installaties op locatie en op gehoste/hybride installaties die gebruikmaken van de oude Campagne MTA.

MX-regels (Mail eXchanger) zijn de regels die de communicatie tussen een verzendende server en een ontvangende server beheren.

Deze regels worden automatisch elke ochtend om 6AM (servertijd) opnieuw geladen om de cliëntinstantie regelmatig te leveren.

Afhankelijk van de materiaalcapaciteiten en het interne beleid, zal ISP een vooraf bepaald aantal verbindingen en berichten per uur goedkeuren. Deze variabelen kunnen automatisch door het ISP systeem afhankelijk van de reputatie van IP worden gewijzigd en domein verzenden. Via zijn leverbaarheidsplatform, beheert Adobe Campaign meer dan 150 specifieke regels door ISP, en, daarnaast, één generische regel voor andere domeinen.

Het maximumaantal verbindingen hangt niet uitsluitend van het aantal openbare IP adressen af die door MTA worden gebruikt.

Bijvoorbeeld, als u 5 verbindingen in de MX regels hebt toegestaan en u 2 openbare IPs hebt gevormd zou u kunnen denken dat u niet meer dan 10 verbindingen kunt hebben gelijktijdig die aan dit domein worden geopend. Dit is niet waar, in feite verwijst het maximumaantal verbindingen naar een weg en een weg die een combinatie van één van onze MTA openbare IPs en openbaar IP van MTA van de cliënt MTA is.

In het onderstaande voorbeeld heeft de gebruiker twee openbare IP-adressen geconfigureerd en is het domein yahoo.com.

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

MX-records voor yahoo.com vertellen ons dat yahoo.com 3 Mail Exchange-apparaten heeft. Om de Peer Uitwisseling van de Post aan te sluiten, gaat MTA om het IP adres van IP van DNS verzoeken.

```
user:~ user$ host -t a mta5.am0.yahoodns.net
                mta5.am0.yahoodns.net has address 98.136.216.26
                mta5.am0.yahoodns.net has address 98.136.217.202
                mta5.am0.yahoodns.net has address 98.138.112.38
                mta5.am0.yahoodns.net has address 66.196.118.37
                mta5.am0.yahoodns.net has address 63.250.192.46
                mta5.am0.yahoodns.net has address 66.196.118.240
                mta5.am0.yahoodns.net has address 98.136.217.203
                mta5.am0.yahoodns.net has address 98.138.112.35
```

Voor deze record kan de gebruiker contact opnemen met 8 peer-IP-adressen. Aangezien de gebruiker 2 openbare IP adressen heeft, geeft dit hen 8 * 2 = 16 combinaties om de yahoo.com postservers te bereiken. Elk van deze combinaties wordt een pad genoemd.

De tweede MX-record wordt weergegeven als:

```
user:~ user$ host -t a mta6.am0.yahoodns.net
                mta6.am0.yahoodns.net has address 98.138.112.38
                mta6.am0.yahoodns.net has address 98.136.216.26
                mta6.am0.yahoodns.net has address 63.250.192.46
                mta6.am0.yahoodns.net has address 66.196.118.35
                mta6.am0.yahoodns.net has address 98.136.217.203
                mta6.am0.yahoodns.net has address 98.138.112.32
                mta6.am0.yahoodns.net has address 98.138.112.37
                mta6.am0.yahoodns.net has address 66.196.118.33
```

4 van deze 8 IP-adressen worden al gebruikt in mta5 (98.136.216.26 , 98.138.112.38 , 63.250.192.46 en 98.136.217.203). Met deze record kan de gebruiker 4 nieuwe IP-adressen gebruiken. De derde MX-record doet hetzelfde.

In totaal, hebben wij 16 verre IP adressen. In combinatie met onze 2 lokale openbare IPs hebben wij 32 wegen om yahoo.com postservers te bereiken.

>[!NOTE]
>
>Als 2 MX- verslagen van verwijzingen voorzien het zelfde IP adres, zal dit tellen als één weg en niet twee.

Hieronder volgen enkele voorbeelden van het gebruik van MX-regels:

![](assets/s_ncs_examples_mx_rules.png)

In het onderstaande voorbeeld heeft de gebruiker een limiet van 10.000 berichten per uur voor een bepaald domein, maar de MTA-productiecapaciteit is hoger dan deze limiet.

In dit geval, is het verkeer verdeeld in 12 periodes van 5 minuten voor elk uur, en de echte grens is 833 berichten per periode.

Deze berichten worden zo snel mogelijk verzonden.

![](assets/s_ncs_traffic_shaping.png)

### MX-beheer configureren {#configuring-mx-management}

De regels die voor MX moeten worden nageleefd, worden gedefinieerd in het **[!UICONTROL MX management]** -document van het **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** -knooppunt van de boomstructuur.

Als het **[!UICONTROL MX management]** -document niet bestaat in het knooppunt, kunt u het handmatig maken. Dit doet u als volgt:

1. Maak een nieuwe set regels voor e-mail.
1. Kies de modus **[!UICONTROL MX management]** .

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. Ga **defaultMXRules** op het **[!UICONTROL Internal name]** gebied in.

Als u rekening wilt houden met wijzigingen, moet u de statistische server opnieuw starten.

Als u de configuratie opnieuw wilt laden zonder de statistische server opnieuw te starten, gebruikt u de volgende opdracht op de computer die de server host: `nlserver stat -reload`

>[!NOTE]
>
>Deze bevellijn wordt verkiest aan **nlserver opnieuw beginnen**. Zo wordt voorkomen dat statistische gegevens die zijn verzameld voordat het opnieuw opstarten verloren gaat en worden pieken in gebruik voorkomen die in strijd kunnen zijn met de quota die in de MX-regels zijn vastgelegd.

### MX-regels configureren {#configuring-mx-rules}

In het **[!UICONTROL MX management]** -document worden alle domeinen weergegeven die aan een MX-regel zijn gekoppeld.

Deze regels worden op volgorde toegepast: de eerste regel waarvan het MX-masker compatibel is met de beoogde MX wordt toegepast.

De volgende parameters beschikbaar voor elke regel zijn:

* **[!UICONTROL MX mask]** : domein waarop de regel wordt toegepast. Elke regel bepaalt een adresmasker voor MX. Elke MX waarvan de naam overeenkomt met dit masker is daarom in aanmerking. Het masker kan &quot;&#42;&quot;en &quot; bevatten?&quot; algemene tekens.

  De volgende adressen zijn bijvoorbeeld:

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

  zijn compatibel met de volgende maskers:

   * &#42; .yahoo.com
   * ?.mx.yahoo.com

  Voor het e-mailadres foobar@gmail.com is het domein bijvoorbeeld gmail.com en de MX-record is:

  ```
  gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
  ```

  In dit geval wordt de MX-regel `*.google.com` gebruikt. Zoals u kunt zien, past het MX-regelmasker niet noodzakelijk het domein in de e-mail aan. De MX-regels die worden toegepast voor gmail.com-e-mailadressen zijn de regels met het masker `*.google.com` .

* **[!UICONTROL Range of identifiers]**: met deze optie kunt u de bereiken van id&#39;s (publicID) aangeven waarop de regel van toepassing is. U kunt het volgende opgeven:

   * Een getal: de regel is alleen van toepassing op deze publicId.
   * Een waaier van aantallen (**number1-number2**): de regel zal op alle publicIds tussen deze twee aantallen van toepassing zijn.

  >[!NOTE]
  >
  >Als het veld leeg is, geldt de regel voor alle id&#39;s.

  Een openbare identiteitskaart is een intern herkenningsteken van Openbare IP die door één of verscheidene MTAs wordt gebruikt. Deze IDs wordt bepaald in de servers MTA in het {**dossier 0} config-instance.xml.**

  ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**: definieert het bereik van de eigenschappen voor deze MX-regel. Wanneer gecontroleerd, worden alle parameters gedeeld op alle IPs beschikbaar op de instantie. Als deze optie uitgeschakeld is, worden de MX-regels voor elk IP gedefinieerd. Het maximumaantal berichten wordt vermenigvuldigd met het aantal beschikbare IPs.
* **[!UICONTROL Maximum number of connections]**: maximumaantal gelijktijdige verbindingen met het domein van de afzender.
* **[!UICONTROL Maximum number of messages]** : maximum aantal berichten dat via een verbinding kan worden verzonden. Wanneer de berichten dit aantal overschrijden, wordt de verbinding gesloten en nieuw geopend.
* **[!UICONTROL Messages per hour]** : maximum aantal berichten dat in één uur naar het domein van de afzender kan worden verzonden.
* **[!UICONTROL Connection time out]** : tijddrempel voor verbinding met een domein.

  >[!NOTE]
  >
  >De vensters kunnen a **onderbreking** vóór deze drempel uitgeven, die van uw versie van Vensters afhangt.

* **[!UICONTROL Timeout Data]**: maximale wachttijd na het verzenden van berichtinhoud (sectie DATA van het SMTP-protocol).
* **[!UICONTROL Timeout]**: maximale wachttijd voor andere uitwisselingen met de SMTP-server.
* **[!UICONTROL TLS]**: Het TLS-protocol, waarmee u e-mailleveringen kunt versleutelen, kan selectief worden ingeschakeld. Voor elk MX-masker zijn de volgende opties beschikbaar:

   * **[!UICONTROL Default configuration]**: dit is de algemene configuratie die is opgegeven in het configuratiebestand serverConf.xml dat wordt toegepast.

     >[!IMPORTANT]
     >
     >Het wordt niet aanbevolen de standaardconfiguratie te wijzigen.

   * **[!UICONTROL Disabled]** : de berichten worden systematisch zonder versleuteling verzonden.
   * **[!UICONTROL Opportunistic]** : de levering van berichten wordt gecodeerd als de ontvangende server (SMTP) het TLS-protocol kan genereren.

Voorbeeld van configuratie:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>Voor meer bij het gebruiken van MX servers met Adobe Campaign, zie [ deze sectie ](../../installation/using/using-mx-servers.md).

### E-mailindelingen beheren {#managing-email-formats}

U kunt de indeling van verzonden berichten definiëren, zodat de weergegeven inhoud automatisch wordt aangepast aan het domein van het adres van elke ontvanger.

Hiervoor gaat u naar het **[!UICONTROL Management of email formats]** -document, dat zich bevindt in **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]** .

Dit document bevat een lijst met alle vooraf gedefinieerde domeinen die overeenkomen met de Japanse indelingen die door Adobe Campaign worden beheerd. Raadpleeg de [Campaign v8-documentatie](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html){target="_blank"} voor meer informatie.

![](assets/mail_rule_sets.png)

De **MIME structuur** (Multipurpose Internet Mail Extensions) parameter staat u toe om de berichtstructuur te bepalen die naar de verschillende postcliënten zal worden verzonden. Er zijn drie opties beschikbaar:

* **Multipart**: Het bericht wordt verzonden in tekst of formaat van HTML. Als de HTML-indeling niet wordt geaccepteerd, kan het bericht nog steeds in tekstopmaak worden weergegeven.

  Door gebrek, is de multipart structuur **multipart/alternatief**, maar het wordt automatisch **multipart/related** wanneer een beeld aan het bericht wordt toegevoegd. Bepaalde leveranciers verwachten het **multipart/verwante** formaat door gebrek, legt de **[!UICONTROL Force multipart/related]** optie dit formaat voor zelfs als geen beeld in bijlage is.

* **HTML**: Een HTML slechts bericht wordt verzonden. Als de HTML-indeling niet wordt geaccepteerd, wordt het bericht niet weergegeven.
* **Tekst**: Een bericht in tekst slechts formaat wordt verzonden. Het voordeel van tekstformaatberichten is hun zeer kleine grootte.

Als de optie **[!UICONTROL Image inclusion]** is ingeschakeld, worden deze rechtstreeks in de tekst van de e-mail weergegeven. De afbeeldingen worden vervolgens geüpload en de URL-koppelingen worden vervangen door de inhoud ervan.

Deze optie wordt met name gebruikt door de Japanse markt voor **Deco-mail**, **Decore Mail** of **Decoration Mail**. Voor meer informatie, raadpleeg de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html){target="_blank"}.

>[!IMPORTANT]
>
>Als u afbeeldingen in een e-mail invoegt, neemt de grootte aanzienlijk toe.

## Configuratie van de leveringsserver {#delivery-server-configuration}

### Synchronisatie vergrendelen {#clock-synchronization}

De klokken van alle servers die het Adobe Campaign-platform (inclusief de database) vormen, moeten worden gesynchroniseerd en hun systemen moeten op dezelfde tijdzone worden ingesteld.

### Coördinaten van de statistiekserver {#coordinates-of-the-statistics-server}

Het adres van de statistiekserver moet in **worden verstrekt mta**.

Het **statServerAddress** bezit van het **mta** element van de configuratie laat u het adres en het aantal van de te gebruiken haven specificeren.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

Om de statistiekenserver op de zelfde machine te gebruiken, moet u minstens de naam van de machine met de **localhost** waarde ingaan:

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>Als dit gebied niet bevolkt is, zal **mta** niet beginnen.

### Lijst met IP-adressen die moeten worden gebruikt {#list-of-ip-addresses-to-use}

De configuratie betreffende verkeersbeheer wordt gevestigd in het **mta/child/smtp** element van het configuratiedossier.

Voor elk **** element IPAffinity, moet u de IP adressen verklaren die voor de machine kunnen worden gebruikt.

Voorbeeld:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

De parameters zijn als volgt:

* **adres**: dit is het IP adres van de MTA gastheermachine die moet worden gebruikt.
* **heloHost**: dit herkenningsteken vertegenwoordigt het IP adres aangezien het door de server SMTP zal worden gezien.

* **publicId**: deze informatie is nuttig wanneer een IP adres door verscheidene Adobe Campaign **mtas** achter een NATIONAAL router wordt gedeeld. De statistiekserver gebruikt deze id om verbinding te onthouden en statistieken tussen dit uitgangspunt en de doelserver te verzenden.
* **gewicht**: laat u de relatieve frequentie van gebruik van het adres bepalen. Standaard hebben alle adressen een dikte gelijk aan 1.

>[!NOTE]
>
>In het serverConf.xml- dossier, moet u verifiëren dat één IP aan één enkele helohost met een uniek herkenningsteken (public_id) beantwoordt. Het kan niet aan veelvoudige helohosts worden in kaart gebracht, wat in leveringsvertragende kwesties zou kunnen resulteren.

In het vorige voorbeeld, met normale voorwaarden, zullen de adressen als volgt worden verdeeld:

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

Als, bijvoorbeeld, het eerste adres niet voor een bepaalde MX kan worden gebruikt, zullen de berichten als volgt worden verzonden:

    * &quot;2&quot;: 5 / (5+1) = 83% 
    * &quot;3&quot;: 1 / (5+1) = 17% 

* **includeDomains**: laat u dit IP adres voor e-mails reserveren die tot een specifiek domein behoren. Dit is een lijst van maskers die één of meerdere vervangingen (&#39;&#42;&#39;) kunnen bevatten. Als het attribuut niet wordt gespecificeerd, kunnen alle domeinen dit IP adres gebruiken.

  Voorbeeld: **includeDomains= &quot;wanadoo.com, orange.com, yahoo.&#42;&quot;**

* **excludeDomains**: sluit een lijst van domeinen voor dit IP adres uit. Dit filter wordt toegepast na de **includeDomains** filter.

  ![](assets/s_ncs_install_mta_ips.png)

## Optimalisatie van e-mailverzending {#email-sending-optimization}

De interne architectuur van Adobe Campaign **mta** heeft een effect op de configuratie voor het optimaliseren van e-maillevering. Hier volgen enkele tips voor het verbeteren van uw leveringen.

### De parameter maxWaitingMessages aanpassen {#adjust-the-maxwaitingmessages-parameter}

De **maxWaitingMessages** parameter wijst op het hoogste aantal berichten die vooraf door **worden voorbereid mtachild**. Berichten worden pas uit deze lijst verwijderd nadat ze zijn verzonden of verlaten.

Deze parameter is zeer belangrijk en vooral kritiek als de berichten niet door domein worden gesorteerd.

Zodra de **maxWorkingSetMb** (256) drempel wordt bereikt, houdt de leveringsserver op verzendend berichten. De prestaties zullen beduidend verminderen tot **mtachild** opnieuw begint. Om deze kwestie te negeren, kunt u of de drempel van de **maxWorkingSetMb** parameter verhogen, of de drempel van de **maxWaitingMessages** parameter verminderen.

De **maxWorkingSetMb** parameter wordt berekend empirisch door het maximumaantal berichten door de gemiddelde berichtgrootte te vermenigvuldigen en het resultaat door 2.5 te vermenigvuldigen. Bijvoorbeeld, als een bericht een gemiddelde grootte van 50 kB heeft en de **maxWaitingMessages** parameter 1.000 evenaart, zal het gebruikte geheugen 125 MB gemiddelde.

### Het aantal onderliggende items aanpassen {#adjust-the-number-of-mtachild}

Het aantal kinderen mag niet groter zijn dan het aantal processoren in de machine (ongeveer 1000 sessies). Wij adviseren dat u 8 **mtachild** niet overschrijdt. U kunt het aantal berichten per **kind** (**dan verhogen maxMsgPerChild**) om voldoende leven-spanwijdte te bereiken.
