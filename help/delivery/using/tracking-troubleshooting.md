---
solution: Campaign Classic
product: campaign
title: Problemen bijhouden
description: Deze sectie biedt veelgestelde vragen over het bijhouden van configuratie en implementatie in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: efa36dc08ce4dd59805bb9eba63a4249e14609d7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# Problemen bijhouden {#tracking-troubleshooting}

In deze sectie vindt u algemene vragen over het bijhouden van configuratie en implementatie in Adobe Campaign Classic.

## De volgende workflow mislukt {#tracking-workflow-failing}

Mijn traceringsworkflow mislukt. Hoe kan ik de beschadigde regels in het trackingbestand detecteren?

>[!NOTE]
>
>Alleen beschikbaar voor Windows

Het beschadigde logbestand voor bijhouden../nl6/var/&lt;instance_name>/redir/log/0x0000 log kan de volgende workflow stoppen. Om bedorven lijnen gemakkelijk te ontdekken en hen te verwijderen om het volgen werkschema te hervatten, kunt u de hieronder bevelen gebruiken.

### Ik weet in welk bestand de beschadigde regel staat

In dat geval kunnen beschadigde lijnen worden gevonden in het bestand 0x0000000000A0000.log, maar hetzelfde proces kan worden toegepast op een reeks bestanden - een voor een.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

Vervolgens kunt u de workflow voor het bijhouden van wijzigingen stoppen, de beschadigde regel(s) verwijderen en de workflow opnieuw starten.

### Ik weet nu niet in welk bestand de beschadigde regel staat

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

1. Voer een grep-opdracht uit om het bijbehorende bestand te zoeken.

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

## Koppelingen bijhouden mislukt periodiek {#tracking-links-fail-intermittently}

Wanneer u probeert toegang te krijgen tot de trackingkoppelingen, wordt het volgende bericht weergegeven:

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

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

1. Controleer handmatig of het bestand &lt;deliveryID>.xml op de computer aanwezig is in .../nl6/var/&lt;instance_name>/redir/url/&lt;YYYY> directory (YYYY staat voor leveringsjaar).

1. Controleer handmatig of &lt;trackingUrlId> kan worden gevonden in het bestand &lt;deliveryID>.xml.

1. Controleer manueel bestaan van broadlogID in verwante levering van deliveryID.

1. Rechten voor &lt;deliveryID>.xml-bestanden controleren in .../nl6/var/&lt;instance_name>/redir/url/year directory.

   Ze moeten minimaal 644 machtigingen hebben, zodat Apache URL&#39;s kan lezen die volgen om de aangevraagde koppeling om te leiden.

## De optie NmsTracking_Pointer bijwerken? {#updating-option}

Voer de volgende stappen uit wanneer u de optie NmsTracking_Pointer bijwerkt:

1. Stop de workflow voor bijhouden.

1. Stop de trackinglogd-service.

1. Werk de optie NmsTracking_Pointer bij naar de gewenste waarde.

1. Start de service Trackinglogd opnieuw.

1. Start de workflow voor bijhouden opnieuw.

## Het volgen lijkt niet met sommige WebMail {#webmail} te werken

U kunt de formule voor het bijhouden van klikken aanpassen en een aangepaste formule voor het bijhouden van Adobe Analytics opgeven.

Dat soort aanpassing moet met voorzichtigheid worden gedaan om extra linefeed karakters te vermijden. Alle regelvoeders die zich buiten de JavaScript-expressie bevinden, worden in de uiteindelijke formule gebruikt.

Dit soort extra linefeed-teken in de URL voor bijhouden leidt tot publicatie in bepaalde webMail (AOL, GMail, enz.).

**Eerste voorbeeld:**

* Onjuiste syntaxis

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>
   &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

* Correcte syntaxis

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

Om te begrijpen waar de extra linefeed is kunt u de uitdrukking javascript door een vaste koordTEKENREEKS vervangen.

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
   <% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

* Correcte syntaxis

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

Om te begrijpen waar de extra linefeed is kunt u de uitdrukking javascript door een vaste koordTEKENREEKS vervangen.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

## Ophalen van logbestanden bijhouden is te langzaam {#slow-retrieval}

Wanneer de instantie niet direct het volgen logboeken maar van een verre server van Adobe Campaign Classic terugwint, worden de logboeken teruggewonnen door de vraag van de ZEEP GetTrackingLogs die in het remoteTracking schema wordt bepaald.

Met een optie in het bestand serverConf.xml kunt u het aantal logbestanden instellen dat tegelijk met deze methode wordt opgehaald: logCountPerRequest.

De standaardwaarde van logCountPerRequest die 1000 is, kan het in sommige gevallen te klein blijken te zijn. De toegestane waarden moeten tussen 0 en 10.000 liggen.

## Logbestanden voor bijhouden kunnen niet worden gekoppeld aan ontvangers {#link-recipients}

In Adobe Campaign Classic, wordt een doelafbeelding verondersteld uniek in termen van ontvangend schema tegenover de schema&#39;s van het broadlog/trackinglogschema&#39;s te zijn.

![](assets/tracking-troubleshooting.png)

Het is niet mogelijk om veelvoudige het richten schema&#39;s met het zelfde trackinglogschema te gebruiken aangezien het volgen werkschema gegevens met het richten van identiteitskaart niet zal kunnen aanpassen.

Als u niet de out-of-the-box doelafbeelding met nms wilt gebruiken:ontvanger, adviseren wij de volgende benaderingen:

* Als u een aangepaste dimensie voor het toewijzen van doelen wilt gebruiken, moet u een aangepast breedLog/trackinglogschema maken met nms:broadlog als sjabloon (bijvoorbeeld nms:wideLogRcp, nms:wideLogSvc, enz.).

* Als u OOB trackingLogRcp/wideLogRcp wilt gebruiken, moet de het richten dimensie nms zijn:ontvanger en het filtreren dimensie zou een douaneschema kunnen zijn.
