---
solution: Campaign Classic
product: campaign
title: Protocol en instellingen voor sms-connector
description: Leer meer op de schakelaar van SMS en hoe te om het te vormen.
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '2751'
ht-degree: 0%

---


# SMS-probleemoplossing {#troubleshooting-sms}

## Conflict tussen verschillende externe rekeningen {#external-account-conflict}

Als de instantie veelvoudige externe rekeningen van SMS heeft, moet u controleren dat de problemen niet door een conflict tussen externe rekeningen worden veroorzaakt.

Adobe Campaign beschouwt externe rekeningen als niet-verbonden entiteiten.

Als u meerdere accounts hebt, volgt u deze procedure om de externe account te isoleren. Dit veroorzaakt problemen:

1. Alle externe accounts uitschakelen.
1. Eén externe account inschakelen.
1. Probeer het probleem te reproduceren.
1. Als het oorspronkelijke probleem niet altijd zichtbaar is, doet u een redelijke hoeveelheid pogingen voordat u het sluit.
1. Als het probleem niet wordt weergegeven bij dat ene account, schakelt u het uit en start u de toepassing opnieuw op stap 2 voor het volgende account.

Nadat u elk account afzonderlijk hebt gecontroleerd, zijn er twee mogelijke scenario&#39;s:

* **Het probleem kwam voor op een of meerdere rekeningen**

   In dit geval kunt u op elke account afzonderlijk andere procedures voor het oplossen van problemen toepassen. Het is best om andere rekeningen onbruikbaar te maken terwijl het diagnostiseren van een rekening om netwerkverkeer en het aantal logboeken te verminderen.

* **Het probleem is niet opgetreden wanneer slechts één account actief is**

   Er is een conflict tussen accounts. Zoals eerder vermeld, behandelt Adobe Campaign accounts afzonderlijk, maar kan de provider ze als één enkele account behandelen.

   * U gebruikt verschillende aanmeldings-/wachtwoordcombinaties voor al uw accounts.
U moet contact opnemen met de provider om mogelijke conflicten aan de zijkant vast te stellen.

   * Sommige externe accounts hebben dezelfde combinatie van aanmelding/wachtwoord.
De provider heeft geen manier om te bepalen van welke externe account de `BIND PDU` afkomstig is, zodat ze alle verbindingen van de meerdere accounts als één enkele beschouwen. Ze hadden MO en SR mogelijk willekeurig rond de twee accounts gerouteerd, wat problemen veroorzaakte.
Als de leverancier veelvoudige korte codes voor de zelfde login/wachtwoordcombinatie steunt, zult u hen moeten vragen waar te om die korte code in `BIND PDU` te zetten. Merk op dat dit stuk informatie binnen `BIND PDU`, en niet in `SUBMIT_SM` moet worden gezet, aangezien `BIND PDU` de enige plaats is die het verpletteren van MOs correct zal toestaan.
Zie [Informatie in elk type PDU](../../delivery/using/sms-protocol.md#information-pdu) sectie hierboven om te weten welk gebied in `BIND PDU` beschikbaar is, gewoonlijk voegt u de korte code in `address_range` toe, maar dat speciale steun van de leverancier vereist. Contacteer hen om te weten hoe zij verwachten om veelvoudige korte codes onafhankelijk te leiden.
Adobe Campaign biedt ondersteuning voor het verwerken van meerdere korte codes op dezelfde externe account.

## Uitgifte met externe rekening in het algemeen {#external-account-issues}

* Onderzoek of de schakelaar onlangs is veranderd en door wie (controleer Externe Rekeningen als groep).

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* Onderzoek (in /postupgrade folder) of het systeem werd bevorderd en wanneer
* Onderzoek of om het even welke pakketten die SMS beïnvloeden onlangs (/var/log/dpkg.log) zouden kunnen zijn bevorderd.

## Probleem met midsourcing (gehost){#issue-mid-sourcing}

* Als het probleem zich voordoet in een omgeving voor midsourcing, moet u ervoor zorgen dat de bezorging en de brede logboeken op de server voor midsourcing correct worden gemaakt en bijgewerkt. Als dat niet het geval is, is dit geen kwestie van SMS.

* Als alles werkt op de server halverwege en SMS correct worden verzonden, maar de marketinginstantie niet correct wordt bijgewerkt, hebt u mogelijk een probleem met betrekking tot de medio-synchronisatie.

## Probleem bij verbinding met de provider {#issue-provider}

* Als de `BIND PDU` een niet-nul `command_status` code terugkeert, vraag de leverancier om meer informatie.

* Controleer of het netwerk correct is geconfigureerd, zodat de TCP-verbinding tot stand kan worden gebracht met de provider.

* Vraag de leverancier om te controleren dat zij behoorlijk IPs aan de lijst van gewenste personen van de instantie van Adobe Campaign toevoegden.

* Controleer **Externe account** instellingen. Vraag de provider de waarde van de velden.

* Als de verbinding succesvol maar onstabiel is, controleer [Kwestie met instabiele verbindingen](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection) sectie.

* Als verbindingsproblemen moeilijk te diagnosticeren zijn, kan een netwerk vangen informatie verstrekken. Zorg ervoor dat het netwerk vangt gelijktijdig loopt terwijl het probleem voor het efficiënt kan worden geanalyseerd. Let ook op het exacte tijdstip waarop het probleem verschijnt.

## Problemen met onstabiele verbinding {#issues-unstable-connection}

Een verbinding wordt als instabiel beschouwd als om het even welke volgend gebeurt:

* De verbinding duurt minder dan 1 uur. Adobe Campaign Classic-transmissieverbindingen vormen een uitzondering vanwege de manier waarop de Adobe Campaign Classic MTA werkt.

* De provider verzendt `UNBIND PDU`s.

* `enquire_link` keren uit, aan de kant van Adobe Campaign of aan de kant van de provider. In dat geval ziet u `ENQUIRE_LINK_RESP` met een foutcode die niet gelijk is aan nul.

* Er zijn veel `BIND PDU`s. Afhankelijk van het aantal verbindingen mag er niet meer dan een paar zijn per dag. Meer dan 1 BIND PDU per uur zou alarm moeten zijn.

Verbindingsstabiliteitsproblemen oplossen:

* De instabiele verbindingen zijn zelden de worteloorzaak, het is vaak het resultaat van een ander probleem dat een losmaken veroorzaakt. Het vinden van de worteloorzaak is de prioriteit.

* Brede SMPP-sporen inschakelen. U zult hen nodig hebben om te zien wat gebeurt wanneer de verbinding opnieuw begint.

* Als de provider `BIND PDU`s verzendt, is er mogelijk iets mis. Vraag uw provider waarom `UNBING` is verzonden.

* Het vastleggen van een netwerk is soms de enige manier om te zien hoe de verbinding wordt gesloten.

* Als de provider de verbindingen sluit door een `TCP FIN` of een `TCP RST packet` te verzenden, vraagt u uw provider om meer informatie.

* Als de leverancier de verbinding sluit na het verzenden van een schone fout zoals `DELIVER_SM_RESP` met een foutencode, moeten zij hun schakelaar anders bevestigen die andere soorten berichten zullen verhinderen worden overgebracht en MTA throttling zullen teweegbrengen. Dit is met name belangrijk in de transceivermodus, waarbij het sluiten van de verbinding invloed heeft op zowel MT als SR.

## Probleem bij het verzenden van een MT (regelmatig naar een eindgebruiker verzonden SMS){#issue-MT}

* Controleer of de verbinding stabiel is. Een verbinding SMPP zou omhoog minstens 1 uur ononderbroken behalve zenders op Adobe Campaign Classic moeten blijven. Zie de sectie [Probleem met instabiele verbindingen](../../delivery/using/sms-protocol.md#issues-unstable-connection).

* Als het opnieuw opstarten van de MTA het verzenden van MT opnieuw voor een kleine periode maakt, hebt u waarschijnlijk vertraging toe te schrijven aan een instabiele verbinding. Zie de sectie [Probleem met instabiele verbindingen](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection).

* Controleer of het brede logboek aanwezig is en in de juiste status met de juiste datums. Als het niet is, zou dit een levering of leveringsvoorbereidingskwestie kunnen zijn.

* Controleer of de MTA het bericht daadwerkelijk verwerkt. Als het niet het geval is, zou dit geen kwestie van SMS kunnen zijn.

* Controleer of de SMS-connector daadwerkelijk is gebonden aan de apparatuur van de provider. Vraag de leverancier om feedback om te controleren of alle systemen correct communiceren. Zie `BIND_TRANSMITTER` en `BIND_TRANSCEIVER PDU`s voor informatie over het bindingsproces. Mogelijk moet u SMPP-sporen inschakelen voor het oplossen van problemen.

* Als de sporen SMPP toegelaten, controleer dat `SUBMIT_SM PDU` de juiste informatie bevat.

* Controleer of de provider reageert met een waarde `SUBMIT_SM_RESP PDU` met de waarde &quot;OK&quot; (code 0). Zorg ervoor dat de PDU met een redelijke vertraging aankomt: iets langer dan 1 seconde moet met de leverancier worden besproken , komt het gewoonlijk binnen minder dan 100 ms aan .

* Als al deze stappen werken, kunt u erop vertrouwen dat het probleem aan de leverancierszijde is. Zij zullen het oplossen van problemen op hun platform moeten doen.

* Als het werkt maar de productie inconsequent is, probeer aanpassend het verzendende venster en verminderend de productie MT. U zult met de leverancier moeten werken om dat aan te passen. Adobe Campaign kan zeer snel berichten verzenden zodat kunnen de prestatiesproblemen zich op het materiaal van de leverancier voordoen.

## MT worden gedupliceerd (zelfde SMS wordt verzonden veelvoudige tijden in een rij){#duplicated-MT}

Duplicaten worden vaak veroorzaakt door nieuwe pogingen. Het is normaal om duplicaten te hebben wanneer het opnieuw proberen van berichten, zou u moeten proberen om de worteloorzaak van herpogingen te verwijderen.

* Als u duplicaten ziet die precies 60 seconden van elkaar zijn verzonden, is het waarschijnlijk een probleem aan de kant van de provider, dan sturen ze niet snel genoeg een `SUBMIT_SM_RESP`.

* Als u veel `BIND/UNBIND` ziet, hebt u een instabiele verbinding. Zie [Probleem met instabiele verbindingen](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection) sectie voor oplossingen alvorens te proberen om dubbele berichtkwesties op te lossen.

Het verminderen van de hoeveelheid duplicaten wanneer er opnieuw wordt geprobeerd:

* Verlaag het verzendende venster. Het verzendende venster zou groot genoeg moeten zijn om voor `SUBMIT_SM_RESP` latentie te behandelen. De waarde ervan vertegenwoordigt het maximum aantal berichten dat kan worden gedupliceerd als een fout optreedt terwijl het venster vol is.

## Probleem bij verwerking SR (ontvangstbewijzen) {#issue-process-SR}

* U hebt SMPP-sporen nodig die zijn ingeschakeld voor het uitvoeren van elk type SR-probleemoplossing.

* Controleer of de `DELIVER_SM PDU` afkomstig is van de provider en of deze goed is samengesteld.

* Controleer of Adobe Campaign tijdig reageert met een geslaagde `DELIVER_SM_RESP PDU`. Op Adobe Campaign Classic garandeert dit dat de SR is ingevoegd in de tabel `providerMsgId` voor uitgestelde verwerking door het SMS-proces.

Als `DELIVER_SM PDU` niet met succes wordt erkend, dan zou u het volgende moeten controleren:

* Controleer regex met betrekking tot id-extractie en foutverwerking in de **External account**. Mogelijk moet u deze valideren op basis van de inhoud van de `DELIVER_SM PDU`.

* Controleer of de fouten correct zijn opgenomen in de tabel `broadLogMsg`.

Als de `DELIVER_SM PDU` door de Adobe Campaign Classic uitgebreide schakelaar SMPP is erkend maar het wideLog niet behoorlijk wordt bijgewerkt, controleer het proces van de aanpassing van identiteitskaart dat in de sectie [Matching MT, SR en uitzendingangen ](../../delivery/using/sms-protocol.md#matching-mt) wordt beschreven.

Als u alles hebt gecorrigeerd, maar sommige ongeldige SR nog steeds in de buffers van de provider staan, kunt u deze overslaan met de optie &quot;Ongeldige id bevestigt telling&quot;. Dit dient met voorzichtigheid te worden gebruikt en zo snel mogelijk na het schoonmaken van de buffers op 0 te worden ingesteld.

## Probleem bij verwerking MO (en zwarte lijst/automatische reactie){#issue-process-MO}

* SMPP-sporen inschakelen tijdens tests. Als u TLS niet toelaat, zou u een netwerk moeten doen vangt wanneer het oplossen van problemenMO om te controleren dat PDUs de correcte informatie bevatten en behoorlijk geformatteerd zijn.

* Wanneer het vangen van netwerkverkeer of het analyseren van sporen SMPP, ben zeker om het volledige gesprek met MO en zijn antwoord MT te vangen als een antwoord wordt gevormd.

* Als de MO (`DELIVER_SM PDU`) niet in de sporen verschijnt, is het probleem op de leverancierskant. Zij zullen het oplossen van problemen op hun platform moeten doen.

* Als `DELIVER_SM PDU` verschijnt, controleer dat het door Adobe Campaign met succes `DELIVER_SM_RESP PDU` (code 0) wordt erkend. Dit RESP garandeert dat alle verwerkingslogica is toegepast door Adobe Campaign (automatisch antwoord en allow/lijst van afgewezen personen). Als het niet het geval is, zoek naar een foutenmelding in de het proceslogboeken van SMS.

* Als automatische reacties zijn ingeschakeld, controleert u of `SUBMIT_SM` naar de provider is verzonden. Als niet, is het gegarandeerd om een foutenmelding in de het proceslogboeken van SMS te vinden.

* Als de `SUBMIT_SM MT PDU` met het antwoord in de sporen wordt gevonden maar SMS niet aan de mobiele telefoon aankomt, zult u voor hulp bij het oplossen van problemen contact met de leverancier moeten opnemen.

## Uitgave tijdens de voorbereiding van de levering zonder uitzondering van in quarantaine geplaatste ontvangers (in quarantaine geplaatst door de functie voor automatische reactie) {#issue-delivery-preparation}

* Controleer dat het formaat van het telefoonaantal precies het zelfde in de quarantainelijst en in het leveringslogboek is. Als het niet is, verwijs naar dit [sectie](../../delivery/using/sms-protocol.md#automatic-reply) als u kwesties met het plus voorvoegsel van het internationale formaat van het telefoonaantal hebt.

* Controleer korte codes. Uitsluitingen kunnen optreden als de korte code van de ontvanger gelijk is aan de code die in de externe account is gedefinieerd of als deze leeg is (leeg = enige snelcode). Als slechts één korte code voor de volledige instantie van Adobe Campaign wordt gebruikt, is het gemakkelijker om alle **korte code** gebieden leeg te verlaten.

## Coderingsproblemen {#encoding-issues}

**Stap 1: Neem contact op met de provider**

Neem contact met hen op en zie wat er mis is met hen. Ze moeten je kunnen vertellen of het probleem aan hun kant of aan Adobe Campaign ligt. Als het probleem zich in Adobe Campaign voordoet, moeten ze u exact kunnen vertellen welk veld onjuist is.

**Stap 2: Weet wat er in je bericht staat**

Unicode staat veel varianten voor look-alike karakters toe en Adobe Campaign kan niet hen allen behandelen.

De gemeenschappelijkste bron van problemen is een exemplaar-deeg van een tekstbewerker, die normale karakters in typografisch correcte versies verandert: Spaties zijn veranderd in vaste spaties, dubbele aanhalingstekens zijn veranderd in open en sluitende aanhalingstekens, mintekens zijn gewijzigd in verschillende soorten afbreekstreepjes, enz.

Kopieer uw bericht niet en plak het tijdens het testen altijd rechtstreeks in de interface.

Met hexadecimaal kunt u het verschil zien tussen vergelijkbare tekens. Een L in kleine letters, een I in hoofdletters, O, 0, alle verschillende typen aanhalingstekens, niet-Latijnse coderingen of zelfs verschillende typen spaties kunnen er allemaal hetzelfde uitzien of zelfs helemaal niet worden weergegeven.

Om unicode in hexadecimaal om te zetten, kunt u online hulpmiddelen zoals [de code van Unicode converter](https://r12a.github.io/app-conversion/) website gebruiken. Typ uw tekst, controleer of er geen PII zoals telefoonnummers is en klik op **Omzetten**. De hexadecimale waarden worden onderaan weergegeven (UTF-32-zone).

Wanneer het openen van kaartjes over coderingsproblemen, of met de leverancier of [Adobe de Zorg van de Klant ](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html), altijd een hexadecimale versie omvat van wat u typt en wat u ziet.

**Stap 3: Weet wat u moet verzenden**

Bepaal de codering die u wilt gebruiken en zoek online naar de bijbehorende tekentabel. Controleer of de tekens die u wilt verzenden, daadwerkelijk beschikbaar zijn op de doelcodepagina. Controleer of het veld `data_coding` correct is en overeenkomt met wat u en de provider verwachten.

**Stap 4: Weet wat je daadwerkelijk hebt verzonden**

U zult zuivert output van de schakelaar nodig hebben om precies te zien welke bytes u naar de leverancier verzendt. Coderingsproblemen verschijnen in `SUBMIT_SM PDU`s, zodat zeker ben om hen te vangen. Verzend zeer duidelijke berichten die gemakkelijk in het logboek zijn te vinden.

Verschillende soorten speciale tekens verzenden tijdens het testen. GSM7-codering bevat bijvoorbeeld uitgebreide tekens die sterk van elkaar verschillen in hun hexadecimale vorm. Ze zijn gemakkelijk te vinden omdat ze niet in andere codering worden weergegeven.

## Elementen die moeten worden opgenomen wanneer wordt gecommuniceerd over een SMS-probleem {#element-include}

Wanneer u om hulp over een kwestie van SMS, of het een steunkaartje aan Adobe Campaign, aan de leverancier van SMS, of om het even welk soort mededeling over de kwestie opent, zult u de volgende informatie moeten omvatten om ervoor te zorgen dat het behoorlijk gekwalificeerd zal zijn. Goed gekwalificeerde problemen zijn essentieel om problemen sneller op te lossen.

* **Schakel uitgebreide SMPP-** berichten in wanneer het probleem optreedt. De meeste SMS-problemen kunnen zonder deze oplossing niet worden opgelost.

* Als het probleem met het verkeer van SMS verwant is, contacteer eerst de leverancier. Hun platform is het meest geschikt voor efficiënte diagnose van de verkeersproblemen van SMS in real time.

* Neem een korte maar feitelijke beschrijving van het probleem op.

* Een beschrijving van het verwachte resultaat opnemen.

* Neem de feedback van de provider op.

* Inclusief relevante logboeken en/of netwerkvastleggingen. Zorg er tijdens het vastleggen voor dat het probleem tijdens het vastleggen wordt gereproduceerd.

* Als u logboeken, sporen of vangen omvat, wijs de nauwkeurige plaats in het dossier aan wanneer het probleem verschijnt.

* Als u berichten, PDUs of logboeken van verwijzingen voorziet, duidelijk hun timestamp verklaren om hen gemakkelijker te maken te vinden.

* Probeer het probleem op een testomgeving te reproduceren. Als u niet zeker bent over een instelling, probeert u deze in de testomgeving en controleert u het resultaat met de SMPP-sporen. Meestal is het beter om problemen te rapporteren die in testomgevingen worden gerepliceerd dan problemen rechtstreeks te melden in productieomgevingen.

* Omvat om het even welke verandering of tweaks die op het platform worden aangebracht. Neem ook alle wijzigingen op die de provider aan hun zijde heeft aangebracht.

### Netwerkopname {#network-capture}

Een netwerk vangt is niet altijd nodig, gewoonlijk zijn de uitgebreide SMPP- berichten genoeg. Hier zijn sommige richtlijnen die u zullen helpen bepalen als een netwerk vangt nodig is:

* Verbindingsproblemen, maar de uitgebreide berichten tonen geen `BIND_RESP PDU`.

* Onverklaarde verbanden zonder foutenmelding, het gebruikelijke gedrag van de schakelaar wanneer het een laag-vlakke protocolfout ontdekt.

* De leverancier klaagt over unbind/disconnection proces.

* Coderingsproblemen in optionele TLV-velden.

* Vermoedelijk wordt verkeer gemengd tussen verschillende verbindingen.

In alle andere situaties, probeer om verbose SMPP- berichten eerst te analyseren en een netwerk te verzoeken vangt slechts als de informatie in de verbose logboeken mist.

In sommige gevallen is het vastleggen van netwerkverkeer niet nodig. Hier volgen de meest voorkomende situaties:

* TLS ingeschakeld: Het TLS-verkeer is per definitie gecodeerd, zodat het niet kan worden vastgelegd.

* Prestatieproblemen: Logbestanden bevatten alle benodigde informatie om prestatieproblemen op te sporen.

* Timingproblemen (`retry timing`, `enquire_link` punt, doorvoerlimiet, enz.)

* SR-parsering en -verwerking: uitgebreide logboeken geven veel meer context en een betere presentatie .

* MO-verwerking (automatische antwoorden, quarantaine).

* Fouten waarbij geen daadwerkelijk SMPP-verkeer is betrokken: Voorbereiding van levering, problemen met de Berichtencentrum-API, workflowproblemen, enz.

## SMPP-sporen inschakelen {#enabling-smpp-traces}

De nieuwe schakelaar steunt uitgebreide het registreren door sporen: SMPP. De sporen zijn output in het MTA logboek, niet op de standaardoutput.

**Per externe account inschakelen (voorkeursmethode)**

1. Schakel in de **Externe account** **Brede SMPP-sporen inschakelen in het logbestand**.
1. Wacht 10 minuten om de server externe accounts opnieuw te laten laden.

Het moet nu actief zijn.

**Configuratie inschakelen**

Stel in het bestand `config-instance.xml` de volgende parameters in:

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## Het aantal open verbindingen op een container {#open-connections} controleren

Als u het aantal open verbindingen op een container wilt controleren, kunt u de volgende opdracht gebruiken:

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

Dit zal van het aantal verbindingen een lijst maken die voor een bepaalde haven worden geopend. Hier gebruiken we poort 3600.

Het resultaat moet als volgt zijn:

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

4 geopende verbindingen voor het sms-proces en 2 per mta-kind met 5 kinderen.
