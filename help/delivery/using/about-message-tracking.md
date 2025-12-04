---
product: campaign
title: Aan de slag met bijhouden
description: Meer informatie over de algemene richtlijnen voor bijhouden in Adobe Campaign
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: ba53107ce06c0484070cbe0943ba439d33d5f710
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 2%

---

# Aan de slag met bericht bijhouden {#get-started-tracking}

>[!IMPORTANT]
>
>Voor **algemene het volgen begeleiding** die op zowel Campaign Classic v7 als Campagne v8 van toepassing is, verwijs naar de [ het volgen van het Bericht van de Campagne v8 documentatie ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"}:
>
>* [ vorm getraceerde verbindingen ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"}
>* [Opties voor URL-tracking configureren](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/url-tracking){target="_blank"}
>* [ spoor gepersonaliseerde verbindingen ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/personalized-links){target="_blank"}
>* [ het volgen van de Toegang logboeken ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"}
>* [Tracking testen](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/testing-tracking){target="_blank"}
>* [ het Volgen rapporten ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/reporting/delivery-reports#tracking-indicators){target="_blank"}
>
>**deze pagina documenteert Campaign Classic v7-specifieke het volgen eigenschappen slechts**, hoofdzakelijk voor hybride en op-gebouw plaatsingen.

## Functies voor bijhouden

### Configuratie bijhouden {#configure-tracking}

Voor Campaign Classic v7 **hybride/op-gebouw plaatsingen**, moet u het volgen op het instantieniveau vormen alvorens het te gebruiken.

>[!NOTE]
>
>Voor Campagne v8 Managed Cloud Services wordt de trackingconfiguratie uitgevoerd door Adobe.

**Werkwijze**

Alvorens het volgen te gebruiken, moet u het voor uw instantie eerst vormen. De configuratie moet worden uitgevoerd op de Adobe Campaign-toepassingsserver(s) en webserver(s).

In Campagne, zijn er twee soorten het volgen:

* **het volgen van het Web**: deze wijze laat u bezoeken aan uw websitepagina&#39;s volgen
* **het volgen van het Bericht**: deze wijze laat u berichtleveringen en ontvankelijk gedrag volgen

De modus Tekstspatiëring wordt tijdens de installatie geselecteerd. Voor installaties op locatie moet de volgende configuratie op instantieniveau worden gedefinieerd. [Meer informatie](../../installation/using/deploying-an-instance.md#operating-principle)

**het Volgen server**

Voor het configureren van tracering moet uw instantie worden gedeclareerd en geregistreerd bij de volgende server(s). De volgende server wordt gebruikt om informatie over URLs te registreren en terug te winnen die door ontvangers wordt geklikt.

Voor installaties op locatie is de trackingserver doorgaans een webserver waarop de Adobe Campaign-webtoepassing wordt uitgevoerd. De URL van de trackingserver moet in uw instantieconfiguratie worden gedefinieerd. [Meer informatie](../../installation/using/deploying-an-instance.md#tracking-server)

**het Opslaan het volgen**

Zodra het volgen wordt gevormd en uw URLs bevolkt, moet de volgende server worden geregistreerd. Met de registratie kan Adobe Campaign trackinggegevens opslaan en rapporten en statistieken over bijgehouden activiteiten leveren.

Voor installaties op locatie wordt de trackinginformatie opgeslagen in de database en opgehaald via technische workflows. Het **Volgen** technische werkschemaprocessen en slaat de volgende gegevens op die van de redirection server worden verzameld. [Meer informatie](../../installation/using/deploying-an-instance.md#saving-tracking)

### Webtoepassing bijhouden {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

>[!NOTE]
>
>**toepassing het volgen van het Web is specifiek voor Campaign Classic v7** en is niet beschikbaar in Campagne v8.

**Een webapplicatie opvolgen**

U kunt bezoeken op de toepassingspagina&#39;s van het Web met het volgen markeringen ook volgen en meten. Deze functionaliteit kan voor alle toepassingstypes van het Web zoals vormen en landende pagina&#39;s worden gebruikt. [Meer informatie](../../web/using/tracking-a-web-application.md)

**Opt-out voor tracking van een webapplicatie**

Met de optie Web application tracking kunt u het webgedrag van eindgebruikers die zich afmelden voor het volgen van gedragingen, niet meer volgen. U kunt de mogelijkheid opnemen om een banner weer te geven in webtoepassingen of om pagina&#39;s te landen, zodat gebruikers zich kunnen afmelden. [Meer informatie](../../web/using/web-application-tracking-opt-out.md)

## Problemen met tracking oplossen {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

De volgende het oplossen van problemenuiteinden zijn op **hybride/op-gebouw plaatsingen van Campaign Classic v7** van toepassing. Sommige informatie kan ook van toepassing zijn op on-premise implementaties van Campagne v8. Neem voor Campagne v8 Managed Cloud Services contact op met uw Adobe-vertegenwoordiger voor hulp.

Voor basis het volgen van het oplossen van problemenstappen in Campagne v8, verwijs naar het [ Oplossen van problemen die in de documentatie van Campagne v8 volgen ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs#troubleshooting){target="_blank"}.

### Basiscontroles {#basic-checks}

**Controle dat het gevolgde logd proces** loopt

Dit proces leest van het gedeelde geheugen IIS/de Server van het Web en schrijft de redirection logboeken.

U kunt het van de Homepage tot toegang hebben door het lusje van de Controle in uw geval te selecteren. U kunt ook de volgende opdracht op de instantie uitvoeren: `<user>@<instance>:~$ nlserver pdump`

Als het trackinglogd-proces niet in de lijst wordt weergegeven, start u het proces met de volgende opdracht in de lijst: `<user>@<instance>:~$ nlserver start trackinglogd`

**Controle dat het Volgen technische werkschema onlangs** in werking is gesteld

U vindt de technische workflow voor bijhouden in de mappen Beheer > Productie > Technische workflows.

### Geavanceerde probleemoplossing {#advanced-troubleshooting}

+++De workflow voor bijhouden mislukt

>[!NOTE]
>
>Alleen beschikbaar voor Windows

Het beschadigde logbestand voor bijhouden van gegevens../nl6/var/&lt;instance_name>/redir/log/0x0000 log kan de volgende workflow stoppen. Om bedorven lijnen gemakkelijk te ontdekken en hen te verwijderen om het volgen werkschema te hervatten, kunt u de hieronder bevelen gebruiken.

**ik weet waarin het dossier de bedorven lijn is**

In dat geval kunnen beschadigde lijnen worden gevonden in het bestand 0x0000000000A0000.log, maar hetzelfde proces kan worden toegepast op een reeks bestanden - een voor een.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

Vervolgens kunt u de workflow voor het bijhouden van wijzigingen stoppen, de beschadigde regel(s) verwijderen en de workflow opnieuw starten.

**ik weet niet in welk dossier de bedorven lijn is**

1. Gebruik de volgende opdrachtregel om alle volgende bestanden in te checken.

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. De opdracht geeft een overzicht van alle beschadigde regels. Bijvoorbeeld:

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Regeleinde is toegevoegd vóór gebruikersagent voor een betere leesbaarheid en geeft geen effectieve rendering aan.

1. Voer een grep-opdracht uit om het corresponderende bestand te zoeken.

   ```
   $ grep -Rn <Log Id>
   # for example:
   $ grep -Rn 50x000000000FD7EC86
   ```

1. Zoek het foutenlogboek met filename en lijnaantal. Bijvoorbeeld:

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Er is een regelterugloop toegevoegd vóór de gebruikersagent om beter lezen toe te staan en dit geeft geen effectieve rendering aan.

Vervolgens kunt u de workflow voor het bijhouden van wijzigingen stoppen, de beschadigde regel(s) verwijderen en de workflow opnieuw starten.

+++

+++Koppelingen bijhouden mislukt soms

Wanneer u probeert toegang te krijgen tot de trackingkoppelingen, wordt het volgende bericht weergegeven:

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&p1=1' cannot be found`

1. Open &lt;redirection_server>/r/test URL en controleer of het bouwstijlaantal en de localhost door het verzoek zijn teruggekeerd.

1. Controleer de configuratie reserveServer in het serverConf.xml- dossier voor de volgende server. Deze configuratie zou op redirection wijze moeten zijn.

   ```
   <redirection>
      <spareServer _operation="update" enabledIf="$(hostname)!='test-rt1'" id="1"
      url="http://test-rt1:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt4'" id="4"
      url="http://test-rt4:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt3'" id="3"
      url="http://test-rt3:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!=test-rt2'" id="2"
      url="http://test-rt2:8080"/>
   </redirection>
   ```

1. Controleer handmatig of het bestand &lt;deliveryID>.xml aanwezig is op de computer in ../nl6/var/&lt;instance_name>/redir/url/&lt;YYYY>-map (YYYY vertegenwoordigt het leveringsjaar).

1. Controleer handmatig of &lt;trackingUrlId> kan worden gevonden in het bestand &lt;deliveryID>.xml.

1. Controleer manueel bestaan van broadlogID in verwante levering van deliveryID.

1. Controleer de machtigingen voor &lt;deliveryID>.xml in de map ../nl6/var/&lt;instance_name>/redir/url/year.

   Ze moeten minimaal 644 machtigingen hebben, zodat Apache URL&#39;s kan lezen die volgen om de aangevraagde koppeling om te leiden.

+++

+++De optie NmsTracking_Pointer bijwerken

Ga als volgt te werk wanneer u de optie NmsTracking_Pointer bijwerkt:

1. Stop de workflow voor bijhouden.

1. Stop de trackinglogd-service.

1. Werk de optie NmsTracking_Pointer bij naar de gewenste waarde.

1. Start de service Trackinglogd opnieuw.

1. Start de workflow voor bijhouden opnieuw.

+++

+++Het volgen werkt niet met sommige WebMail

U kunt de formule voor het bijhouden van klikken aanpassen en een aangepaste formule voor het bijhouden van Adobe Analytics opgeven.

Dat soort aanpassing moet met voorzichtigheid worden gedaan om extra linefeed karakters te vermijden. Alle regelfeeds die aanwezig zijn buiten de JavaScript-expressie, worden opgenomen in de uiteindelijke formule.

Dit soort extra linefeed-teken in de URL voor bijhouden leidt tot publicatie in bepaalde webMail (AOL, GMail, enz.).

**Eerste voorbeeld:**

* Onjuiste syntaxis

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>
  &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

* Correcte syntaxis

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

Om te begrijpen waar de extra linefeed is kunt u JavaScript-expressie vervangen door een vaste tekenreeks STRING.

```
// Incorrect
STRING1
&cid=STRING2&bid=STRING3

// Correct
STRING1&cid=STRING2&bid=STRING3
```

**Tweede voorbeeld**

* Onjuiste syntaxis

  ```
  <%@ include option='NmsTracking_ClickFormula' %>
  <% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

* Correcte syntaxis

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

Om te begrijpen waar de extra linefeed is kunt u JavaScript-expressie vervangen door een vaste tekenreeks STRING.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

+++

+++Ophalen van logbestanden bijhouden is te langzaam

Wanneer de instantie niet direct het volgen logboeken maar van een verre server van Adobe Campaign Classic terugwint, worden de logboeken teruggewonnen door de vraag van GetTrackingLogs SOAP die in het remoteTracking schema wordt bepaald.

Met een optie in het bestand serverConf.xml kunt u het aantal logbestanden instellen dat tegelijk wordt opgehaald met deze methode: logCountPerRequest.

De standaardwaarde van logCountPerRequest die 1000 is, kan het in sommige gevallen te klein blijken te zijn. De toegestane waarden moeten tussen 0 en 10.000 liggen.

+++

+++Logboeken bijhouden kan niet worden gekoppeld aan ontvangers

In Adobe Campaign Classic, wordt een doelafbeelding verondersteld uniek in termen van ontvangend schema tegenover de schema&#39;s van het broadlog/trackinglogschema&#39;s te zijn.

![](assets/tracking-troubleshooting.png)

Het is niet mogelijk om veelvoudige het richten schema&#39;s met het zelfde trackinglogschema te gebruiken aangezien het volgen werkschema gegevens met het richten van identiteitskaart niet zal kunnen aanpassen.

Als u niet de uit-van-de-doos doelafbeelding met nms :recipient wilt gebruiken, adviseren wij de volgende benaderingen:

* Als u douane het richten afmeting wilt gebruiken, moet u het schema tot stand brengen wideLog/trackingLog gebruikend nms :broadlog als malplaatje (b.v. nms :broadLogRcp, nms :broadLogSvc, enz.).

* Als u OOB trackingLogRcp/wideLogRcp wilt gebruiken, moet de het richten afmeting nms :recipient zijn en het filtreren afmeting zou een douaneschema kunnen zijn.

+++
