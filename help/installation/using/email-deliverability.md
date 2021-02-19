---
solution: Campaign Classic
product: campaign
title: E-maillevering
description: E-maillevering
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: fd6195ca447fa0345189f3153f44ad2f9a067210
workflow-type: tm+mt
source-wordcount: '2973'
ht-degree: 0%

---


# Technische e-mailconfiguraties{#email-deliverability}

## Overzicht {#overview}

In de volgende sectie vindt u een overzicht van de configuratie die is vereist voor het beheer van de uitvoer van Adobe Campaign-instanties bij het verzenden van e-mails.

>[!NOTE]
>
>Sommige configuraties kunnen slechts door Adobe voor plaatsingen worden uitgevoerd die door Adobe worden ontvangen, bijvoorbeeld, om tot de server en de dossiers van de instantieconfiguratie toegang te hebben. Raadpleeg de sectie [Modellen hosten](../../installation/using/hosting-models.md) of [deze pagina](../../installation/using/capability-matrix.md) voor meer informatie over de verschillende implementaties.

Voor meer informatie over de concepten en beste praktijken met betrekking tot leverability, verwijs naar dit [sectie](../../delivery/using/about-deliverability.md).

Alle technische aanbevelingen met betrekking tot het efficiënt verzenden en ontvangen van e-mails door een Adobe Campaign-platform zijn beschikbaar in [sectie](../../delivery/using/technical-recommendations.md).

## Werkwijze {#operating-principle}

Het is mogelijk om de uitvoer van een of meer Adobe Campaign-instanties te beheren om het aantal verzonden e-mails te beperken, afhankelijk van een domein. Bijvoorbeeld, kunt u de output tot 20.000 per uur voor **yahoo.com** adressen beperken, terwijl het vormen van 100.000 berichten per uur voor alle andere domeinen.

De output van het bericht moet voor elk IP adres worden gecontroleerd dat door de leveringsservers (**mta**) wordt gebruikt. Verschillende **mta** die zijn opgesplitst over meerdere computers en tot verschillende Adobe Campaign-instanties behoren, kunnen hetzelfde IP-adres delen voor e-maillevering: Er moet een proces worden ingesteld om het gebruik van deze IP-adressen te coördineren.

Dit is wat de **stat** module doet: het door:sturen alle verbindingsverzoeken en berichten die naar de postservers voor een reeks IP adressen moeten worden verzonden. De statistiekserver houdt leveringen bij en kan verzending op basis van ingestelde quota in- of uitschakelen.

![](assets/s_ncs_install_mta.png)

* De statistische server (**stat**) is verbonden met een basis van Adobe Campaign om zijn configuratie te laden.
* De leveringsservers (**mta**) gebruiken UDP om een statistiekserver te contacteren die niet altijd tot hun eigen instantie behoort.

### Leveringsservers {#delivery-servers}

De **mta** module verspreidt berichten aan zijn **mtachild** kindmodules. Elk **mtachild** bereidt berichten voor alvorens om een vergunning van de statistiekserver te verzoeken, en hen te verzenden.

De stappen zijn als volgt:

1. Met de **mta** worden in aanmerking komende berichten geselecteerd en worden deze en beschikbare **mtachild** toegewezen.
1. **mtachild** laadt alle informatie die nodig is voor het samenstellen van het bericht (inhoud, personalisatie-elementen, bijlagen, afbeeldingen, enz.) en stuurt het bericht door naar **Email Traffic Shaper**.
1. Zodra de vormer van het e-mailverkeer de vergunning van de statistiekserver (**smtp stat**) ontvangt, wordt het bericht verzonden naar de ontvanger.

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

Het bronIP adres past het openbare IP adres, d.w.z. het adres aan zoals het door de verre e-mailserver wordt gezien. Dit IP adres kan van het adres van de machine verschillend zijn die gastheren **mta**, als een NATIONAAL router wordt verstrekt. Dit is waarom de statistiekserver een herkenningsteken gebruikt dat openbare IP (**publicId**) aanpast. De koppeling tussen het lokale adres en deze id wordt gedeclareerd in het configuratiebestand **serverConf.xml**. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

## Uitvoerregeling van levering {#delivery-output-controlling}

Voor het verzenden van berichten naar e-mailservers vraagt de component **Email Traffic Shaper** om een verbinding van de statistische server. Nadat het verzoek is geaccepteerd, wordt de verbinding geopend.

Voordat de berichten worden verzonden, vraagt de module &#39;tokens&#39; van de server. Dit zijn over het algemeen reeksen van minstens 10 tokens, die het aantal vragen aan de server verminderen.

De server slaat alle statistieken op met betrekking tot verbindingen en leveringen. In geval van opnieuw opstarten gaat de informatie tijdelijk verloren: elke cliënt bewaart een lokaal exemplaar van hun verzendende statistieken en keert hen aan de server op regelmatige basis (om de 2 minuten) terug. De server kan de gegevens vervolgens opnieuw samenvoegen.

In de volgende secties wordt de verwerking van een bericht door de component **Email Traffic Shaper** beschreven.

### Berichtlevering {#message-delivery}

Wanneer een bericht wordt verzonden, zijn er 3 mogelijke resultaten:

1. **Geslaagd**: het bericht is verzonden. Het bericht wordt bijgewerkt.
1. **Bericht mislukt**: de gecontacteerde server verwierp het bericht voor de gekozen ontvanger. Dit resultaat komt overeen met de retourcodes 550 tot en met 599, maar er kunnen uitzonderingen worden gedefinieerd.
1. **Sessie mislukt**  (voor 5.11 naar boven): als de  **** meta een antwoord voor dit bericht ontvangt, wordt het bericht verlaten (verwijs naar de  [beëindiging](#message-abandonment) van het Bericht). Het bericht wordt verzonden naar een andere weg of geplaatst aan hangend als geen andere wegen beschikbaar zijn (verwijs naar [Bericht hangend](#message-pending)).

   >[!NOTE]
   >
   >Een **pad** is een verbinding tussen de Adobe Campaign **mta** en het doel **mta**. De Adobe Campaign **mta** kan van verscheidene beginIPs en verscheidene doeldomeinIPs kiezen.

### Afmelden van bericht {#message-abandonment}

Verlaten berichten zijn teruggekeerd aan **mta** en niet meer beheerd door **mtachild**.

De **mta** beslist over de procedure voor dit bericht (terugwinning, verlaten, quarantaine, enz.) afhankelijk van de antwoordcode en de regels.

### Bericht in behandeling {#message-pending}

Een bericht wordt toegevoegd wanneer het in de actieve rij aankomt en er geen beschikbare wegen zijn.

Een pad wordt doorgaans als niet beschikbaar gemarkeerd voor een variabele hoeveelheid tijd na een verbindingsfout. De periode van onbeschikbaarheid is afhankelijk van de frequentie en leeftijd van fouten.

## Configuratie Statistische server {#statistics-server-configuration}

De statistische server kan door verscheidene instanties worden gebruikt: het moet onafhankelijk van de instanties worden gevormd die het zullen gebruiken.

Begin door het gegevensbestand te bepalen van Adobe Campaign dat de configuratie zal ontvangen.

### Configuratie starten {#start-configuration}

Standaard wordt de **stat** module gestart voor elke instantie. Wanneer de instanties op de zelfde machine worden mutualiseerd, of wanneer de instanties het zelfde IP adres delen, wordt één enkele statistiekenserver gebruikt: de andere moeten worden uitgeschakeld .

### Definitie van serverpoort {#definition-of-the-server-port}

Door gebrek, luistert de statistiekserver op haven 7777. Deze poort kan worden gewijzigd in het bestand **serverConf.xml**. Alle parameters die beschikbaar zijn in **serverConf.xml** worden vermeld in deze [sectie](../../installation/using/the-server-configuration-file.md).

```
<stat port="1234"/>
```

## MX-configuratie {#mx-configuration}

>[!IMPORTANT]
>
>Voor gehoste of hybride installaties, als u aan [Verbeterde MTA](../../delivery/using/sending-with-enhanced-mta.md) hebt bevorderd, worden de **[!UICONTROL MX management]** leveringsproductieregels niet meer gebruikt. Verbeterde MTA gebruikt zijn eigen MX regels die het toestaan om uw productie door domein aan te passen die op uw eigen historische e-mailreputatie wordt gebaseerd, en op real time terugkoppelen die uit de domeinen komt waar u e-mails verzendt.

De onderstaande secties zijn alleen van toepassing op installaties op locatie en op gehoste/hybride installaties die gebruikmaken van de oude Campagne MTA.

### Informatie over MX-regels {#about-mx-rules}

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

MX-records voor yahoo.com vertellen ons dat yahoo.com 3 Mail Exchangers heeft. Om de Peer Uitwisseling van de Post aan te sluiten, gaat MTA om het IP adres van IP van DNS verzoeken.

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

Voor deze record kan de gebruiker contact opnemen met 8 peer-IP-adressen. Aangezien hij 2 openbaar IP adres heeft geeft dit hem 8 * 2 = 16 combinaties om de yahoo.com postservers te bereiken. Elk van deze combinaties wordt een pad genoemd.

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

4 van deze 8 IP-adressen worden al gebruikt in mta5 (98.136.216.26, 98.138.112.38, 63.250.192.46 en 98.136.217.203). Met deze record kan de gebruiker 4 nieuwe IP-adressen gebruiken. De derde MX-record doet hetzelfde.

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

De regels die voor MX moeten worden nageleefd worden bepaald in **[!UICONTROL MX management]** document van de **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** knoop van de boom.

Als het **[!UICONTROL MX management]** document niet in de knoop bestaat, kunt u het manueel tot stand brengen. Dit doet u als volgt:

1. Maak een nieuwe set regels voor e-mail.
1. Kies de modus **[!UICONTROL MX management]**.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. Typ **defaultMXRules** in het veld **[!UICONTROL Internal name]**.

Als u rekening wilt houden met wijzigingen, moet u de statistische server opnieuw starten.

Om de configuratie opnieuw te laden zonder de statistiekenserver opnieuw te beginnen, gebruik het volgende bevel op de machine die gastheren de server: `nlserver stat -reload`

>[!NOTE]
>
>Deze opdrachtregel heeft de voorkeur boven **Nlserver opnieuw opstarten**. Zo wordt voorkomen dat statistische gegevens die zijn verzameld voordat het opnieuw opstarten verloren gaat en worden pieken in gebruik voorkomen die in strijd kunnen zijn met de quota die in de MX-regels zijn vastgelegd.

### Het vormen MX regels {#configuring-mx-rules}

In het **[!UICONTROL MX management]**-document worden alle domeinen weergegeven die aan een MX-regel zijn gekoppeld.

Deze regels worden achtereenvolgens toegepast: de eerste regel wordt toegepast waarvan MX-masker compatibel is met de beoogde MX.

De volgende parameters beschikbaar voor elke regel zijn:

* **[!UICONTROL MX mask]**: domein waarop de regel wordt toegepast. Elke regel bepaalt een adresmasker voor MX. Elke MX waarvan de naam overeenkomt met dit masker is daarom in aanmerking. Het masker kan &quot;*&quot; en &quot;?&quot; bevatten algemene tekens.

   De volgende adressen zijn bijvoorbeeld:

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

   zijn compatibel met de volgende maskers:

   * *.yahoo.com
   * ?.mx.yahoo.com

   Voor het e-mailadres foobar@gmail.com is het domein bijvoorbeeld gmail.com en de MX-record is:

   ```
   gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
   ```

   In dit geval wordt de MX-regel `*.google.com` gebruikt. Zoals u kunt zien, past het MX-regelmasker niet noodzakelijk het domein in de e-mail aan. De MX regels die voor gmail.com e-mailadressen worden toegepast zullen degenen met het masker `*.google.com` zijn.

* **[!UICONTROL Range of identifiers]**: Met deze optie kunt u de bereiken van id&#39;s (publicID) aangeven waarop de regel van toepassing is. U kunt het volgende opgeven:

   * Een getal: de regel geldt alleen voor deze publicId;
   * Een reeks getallen (**number1-number2**): de regel zal op alle publicIds tussen deze twee aantallen van toepassing zijn.

   >[!NOTE]
   >
   >Als het veld leeg is, geldt de regel voor alle id&#39;s.

   Een openbare identiteitskaart is een intern herkenningsteken van Openbare IP die door één of verscheidene MTAs wordt gebruikt. Deze id&#39;s worden gedefinieerd in de MTA-servers in het bestand **config-instance.xml**.

   ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**: bepaalt het werkingsgebied van de eigenschappen voor deze MX regel. Wanneer gecontroleerd, worden alle parameters gedeeld op alle IPs beschikbaar op de instantie. Als deze optie uitgeschakeld is, worden de MX-regels voor elk IP gedefinieerd. Het maximumaantal berichten wordt vermenigvuldigd met het aantal beschikbare IPs.
* **[!UICONTROL Maximum number of connections]**: maximumaantal gelijktijdige verbindingen aan het domein van de afzender.
* **[!UICONTROL Maximum number of messages]**: maximum aantal berichten dat op een verbinding kan worden verzonden. Wanneer de berichten dit aantal overschrijden, wordt de verbinding gesloten en nieuw geopend.
* **[!UICONTROL Messages per hour]**: maximumaantal berichten dat in één uur naar het domein van de afzender kan worden verzonden.
* **[!UICONTROL Connection time out]**: tijddrempel voor verbinding maken met een domein.

   >[!NOTE]
   >
   >De vensters kunnen **timeout** vóór deze drempel uitgeven, die van uw versie van Vensters afhangt.

* **[!UICONTROL Timeout Data]**: maximumaantal wachttijd na het verzenden van berichtinhoud (sectie DATA van het SMTP-protocol).
* **[!UICONTROL Timeout]**: maximum wachttijd voor andere uitwisselingen met de server SMTP.
* **[!UICONTROL TLS]**: Het TLS-protocol, waarmee u e-mailleveringen kunt coderen, kan selectief worden ingeschakeld. Voor elk MX-masker zijn de volgende opties beschikbaar:

   * **[!UICONTROL Default configuration]**: Dit is de algemene configuratie die is opgegeven in het configuratiebestand serverConf.xml dat wordt toegepast.

      >[!IMPORTANT]
      >
      >Het wordt niet aanbevolen de standaardconfiguratie te wijzigen.

   * **[!UICONTROL Disabled]** : De berichten worden systematisch zonder encryptie verzonden.
   * **[!UICONTROL Opportunistic]** : De levering van berichten wordt gecodeerd als de ontvangende server (SMTP) het TLS-protocol kan genereren.

Voorbeeld van configuratie:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

### E-mailindelingen beheren {#managing-email-formats}

U kunt de indeling van verzonden berichten definiëren, zodat de weergegeven inhoud automatisch wordt aangepast aan het domein van het adres van elke ontvanger.

Hiervoor gaat u naar het **[!UICONTROL Management of email formats]**-document, dat zich bevindt in **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**.

Dit document bevat een lijst met alle vooraf gedefinieerde domeinen die overeenkomen met de Japanse indelingen die door Adobe Campaign worden beheerd. Raadpleeg [dit document](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles) voor meer informatie.

![](assets/mail_rule_sets.png)

Met de parameter **MIME structure** (Multipurpose Internet Mail Extensions) kunt u de berichtstructuur definiëren die naar de verschillende mailclients wordt verzonden. Er zijn drie opties beschikbaar:

* **Multipart**: Het bericht wordt verzonden in tekst of formaat HTML. Als de HTML-indeling niet wordt geaccepteerd, kan het bericht nog steeds in tekstopmaak worden weergegeven.

   Standaard is de multipart-structuur **multipart/alternatief**, maar wordt deze automatisch **multipart/related** wanneer een afbeelding aan het bericht wordt toegevoegd. Bepaalde providers verwachten standaard de **multipart/related**-indeling. Met de optie **[!UICONTROL Force multipart/related]** wordt deze indeling ook verplicht als er geen afbeelding is gekoppeld.

* **HTML**: Er wordt alleen een HTML-bericht verzonden. Als de HTML-indeling niet wordt geaccepteerd, wordt het bericht niet weergegeven.
* **Tekst**: Er wordt een bericht in alleen-tekstopmaak verzonden. Het voordeel van tekstformaatberichten is hun zeer kleine grootte.

Als de optie **[!UICONTROL Image inclusion]** is ingeschakeld, worden deze direct in de tekst van de e-mail weergegeven. De afbeeldingen worden vervolgens geüpload en de URL-koppelingen worden vervangen door de inhoud ervan.

Deze optie wordt met name gebruikt door de Japanse markt voor **Deco-mail**, **Decore Mail** of **Decoration Mail**. Raadpleeg [dit document](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles) voor meer informatie.

>[!IMPORTANT]
>
>Als u afbeeldingen in een e-mail invoegt, neemt de grootte aanzienlijk toe.

## Configuratie van de leveringsserver {#delivery-server-configuration}

### Synchronisatie van klok {#clock-synchronization}

De klokken van alle servers die het Adobe Campaign-platform (inclusief de database) vormen, moeten worden gesynchroniseerd en hun systemen moeten op dezelfde tijdzone worden ingesteld.

### Coördinaten van de statistische server {#coordinates-of-the-statistics-server}

Het adres van de statistische server moet worden opgegeven in **mta**.

Met de eigenschap **statServerAddress** van het element **mta** van de configuratie kunt u het adres en het nummer van de te gebruiken poort opgeven.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

Als u de statistische server op dezelfde computer wilt gebruiken, moet u ten minste de naam van de computer invoeren met de waarde **localhost**:

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>Als dit veld niet is ingevuld, wordt **mta** niet gestart.

### Lijst met IP-adressen die {#list-of-ip-addresses-to-use} moeten worden gebruikt

De configuratie betreffende verkeersbeheer wordt gevestigd in **mta/child/smtp** element van het configuratiedossier.

Voor elk **IPAffinity** element, moet u de IP adressen verklaren die voor de machine kunnen worden gebruikt.

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

* **publicId**: deze informatie is nuttig wanneer een IP adres door verscheidene  **** mtasas van Adobe Campaign achter een NATIONAAL router wordt gedeeld. De statistiekserver gebruikt deze id om verbinding te onthouden en statistieken tussen dit uitgangspunt en de doelserver te verzenden.
* **gewicht**: Hiermee kunt u de relatieve gebruiksfrequentie van het adres definiëren. Standaard hebben alle adressen een dikte gelijk aan 1.

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

* **includeDomains**: Hiermee kunt u dit IP-adres reserveren voor e-mailberichten die tot een bepaald domein behoren. Dit is een lijst met maskers die een of meer jokertekens (&#39;*&#39;) kunnen bevatten. Als het attribuut niet wordt gespecificeerd, kunnen alle domeinen dit IP adres gebruiken.

   Voorbeeld: **includeDomains=&quot;wanadoo.com,orange.com,yahoo.*&quot;**

* **excludeDomains**: sluit een lijst van domeinen voor dit IP adres uit. Dit filter wordt toegepast na het filter **includeDomains**.

   ![](assets/s_ncs_install_mta_ips.png)

## Optimalisatie voor verzenden van e-mail {#email-sending-optimization}

De interne architectuur van de Adobe Campaign **mta** heeft een effect op de configuratie voor het optimaliseren van e-maillevering. Hier volgen enkele tips voor het verbeteren van uw leveringen.

### Pas de parameter maxWaitingMessages {#adjust-the-maxwaitingmessages-parameter} aan

De **maxWaitingMessages** parameter wijst op het hoogste aantal berichten die vooraf door **mtachild** worden voorbereid. Berichten worden pas uit deze lijst verwijderd nadat ze zijn verzonden of verlaten.

Deze parameter is zeer belangrijk en vooral kritiek als de berichten niet door domein worden gesorteerd.

Zodra de **maxWorkingSetMb** (256) drempel wordt bereikt, houdt de leveringsserver op verzendend berichten. De prestaties zullen beduidend dalen tot **mtachild** opnieuw begint. U kunt deze kwestie omzeilen door de drempel van de parameter **maxWorkingSetMb** te verhogen of de drempel van de parameter **maxWaitingMessages** te verlagen.

De **maxWorkingSetMb** parameter wordt berekend empirisch door het maximumaantal berichten met de gemiddelde berichtgrootte te vermenigvuldigen en het resultaat met 2.5 te vermenigvuldigen. Als een bericht bijvoorbeeld een gemiddelde grootte heeft van 50 kB en de parameter **maxWaitingMessages** 1.000 is, wordt gemiddeld 125 MB gebruikt.

### Het aantal onderliggende elementen aanpassen {#adjust-the-number-of-mtachild}

Het aantal kinderen mag niet groter zijn dan het aantal processoren in de machine (ongeveer 1000 sessies). Wij adviseren dat u 8 **mtachild** niet overschrijdt. U kunt dan het aantal berichten per **child** (**maxMsgPerChild**) verhogen om een voldoende levensduur-spanwijdte te bereiken.
