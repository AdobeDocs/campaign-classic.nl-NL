---
product: campaign
title: Problemen met sms oplossen
description: Meer informatie over het oplossen van problemen met SMS-kanalen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: SMS, Troubleshooting
role: User
exl-id: 841f0c2f-90ef-4db0-860a-75fc7c48804a
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '2764'
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

  Er is een conflict tussen accounts. Zoals eerder vermeld behandelt Adobe Campaign accounts individueel, maar de provider kan ze behandelen als één account.

   * U gebruikt verschillende combinaties van aanmeldings-/wachtwoorden voor al uw accounts.
U moet contact opnemen met de provider om mogelijke conflicten aan hun kant te onderzoeken.

   * Sommige externe accounts gebruiken dezelfde combinatie van aanmelding/wachtwoord.
De provider kan niet zien van welk extern account de `BIND PDU` afkomstig is, dus behandelen ze alle verbindingen van de meerdere accounts als één enkel account. Ze hadden MO en SR mogelijk willekeurig rond de twee accounts gerouteerd, wat problemen veroorzaakte.
Als de leverancier veelvoudige korte codes voor de zelfde login/wachtwoordcombinatie steunt, zult u hen moeten vragen waar te om die korte code in te zetten `BIND PDU`. Deze informatie moet in de `BIND PDU`, en niet in `SUBMIT_SM`, sinds de `BIND PDU` is de enige plaats die het verpletteren van MOs correct zal toestaan.
Zie de [Informatie in elke soort PDU](sms-protocol.md#information-pdu) in de sectie hierboven om te weten welk veld beschikbaar is in het dialoogvenster `BIND PDU`, meestal voegt u de korte code toe in `address_range`, maar daarvoor is speciale steun van de leverancier nodig. Neem contact op om te weten hoe ze verwachten meerdere korte codes onafhankelijk van elkaar te routen.
Adobe Campaign biedt ondersteuning voor het verwerken van meerdere korte codes in hetzelfde externe account.

## Probleem met een extern account in het algemeen {#external-account-issues}

* Kijk of de connector onlangs is gewijzigd en door wie (schakel Externe accounts als groep in).

  ```
  select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
  
  (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
  
  (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
  
  N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
  
  from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
  ```

* Onderzoeken (in /postupgrade directory) of het systeem is geüpgraded en wanneer
* Onderzoek of pakketten die van invloed zijn op SMS mogelijk onlangs zijn geüpgraded (/var/log/dpkg.log).

## Probleem met midsourcing (gehost){#issue-mid-sourcing}

* Als het probleem zich voordoet in een omgeving voor midsourcing, moet u ervoor zorgen dat de bezorging en de brede logboeken op de server voor midsourcing correct worden gemaakt en bijgewerkt. Als dat niet het geval is, is dit geen kwestie van SMS.

* Als alles werkt op de server halverwege en SMS correct worden verzonden, maar de marketinginstantie niet correct wordt bijgewerkt, hebt u mogelijk een probleem met betrekking tot de medio-synchronisatie.

## Probleem bij verbinding met de provider {#issue-provider}

* Als de `BIND PDU` retourneert een andere waarde dan nul `command_status` Vraag de provider om meer informatie.

* Controleer of het netwerk correct is geconfigureerd, zodat de TCP-verbinding tot stand kan worden gebracht met de provider.

* Vraag de leverancier om te controleren dat zij behoorlijk IPs aan de lijst van gewenste personen van de instantie van Adobe Campaign toevoegden.

* Controleren **Externe rekening** instellingen. Vraag de provider de waarde van de velden.

* Als de verbinding succesvol maar instabiel is, controleert u [Probleem met instabiele verbindingen](troubleshooting-sms.md#issues-unstable-connection) sectie.

* Als verbindingsproblemen moeilijk te diagnosticeren zijn, kan een netwerk vangen informatie verstrekken. Zorg ervoor dat het netwerk vangt gelijktijdig loopt terwijl het probleem voor het efficiënt kan worden geanalyseerd. Let ook op het exacte tijdstip waarop het probleem verschijnt.

## Problemen met onstabiele verbinding {#issues-unstable-connection}

Een verbinding wordt als instabiel beschouwd als om het even welke volgend gebeurt:

* De verbinding duurt minder dan 1 uur. Adobe Campaign Classic-transmissieverbindingen vormen een uitzondering vanwege de manier waarop de Adobe Campaign Classic MTA werkt.

* De leverancier verzendt `UNBIND PDU`s.

* `enquire_link` keren uit, aan de kant van Adobe Campaign of aan de kant van de provider. Misschien ziet u `ENQUIRE_LINK_RESP` met een foutcode die niet gelijk is aan nul.

* Er zijn veel `BIND PDU`s. Er mogen niet meer dan enkele verbindingen per dag zijn, afhankelijk van het aantal verbindingen. Meer dan 1 BIND PDU per uur zou alarm moeten zijn.

Verbindingsstabiliteitsproblemen oplossen:

* De instabiele verbindingen zijn zelden de worteloorzaak, het is vaak het resultaat van een ander probleem die tot een losmaken leidt. Het vinden van de worteloorzaak is de prioriteit.

* Brede SMPP-sporen inschakelen. U zult hen nodig hebben om te zien wat gebeurt wanneer de verbinding opnieuw begint.

* Als de provider `BIND PDU`Er kan dus iets mis zijn. Vraag uw provider waarom `UNBING` wordt verzonden.

* Het vastleggen van een netwerk is soms de enige manier om te zien hoe de verbinding wordt gesloten.

* Als de leverancier de verbindingen door of te verzenden sluit `TCP FIN` of `TCP RST packet`, vraag uw provider om meer informatie.

* Als de provider de verbinding sluit na het verzenden van een schone fout, zoals `DELIVER_SM_RESP` met een foutcode, moeten ze hun connector op een andere manier repareren, zodat andere soorten berichten niet worden verzonden en de MTA-vertraging wordt geactiveerd. Dit is met name belangrijk in de transceivermodus, waarbij het sluiten van de verbinding invloed heeft op zowel MT als SR.

## Probleem bij het verzenden van een MT (regelmatig naar een eindgebruiker verzonden SMS){#issue-MT}

* Controleer of de verbinding stabiel is. Een verbinding SMPP zou omhoog minstens 1 uur ononderbroken behalve zenders op Adobe Campaign Classic moeten blijven. Zie de sectie [Probleem met instabiele verbindingen](sms-protocol.md#issues-unstable-connection).

* Als het opnieuw opstarten van de MTA het verzenden van MT opnieuw voor een kleine periode maakt, hebt u waarschijnlijk vertraging toe te schrijven aan een instabiele verbinding. Zie de sectie [Probleem met instabiele verbindingen](troubleshooting-sms.md#issues-unstable-connection).

* Controleer of het brede logboek aanwezig is en in de juiste status met de juiste datums. Als het niet is, zou dit een levering of leveringsvoorbereidingskwestie kunnen zijn.

* Controleer of de MTA het bericht daadwerkelijk verwerkt. Als het niet het geval is, zou dit geen kwestie van SMS kunnen zijn.

* Controleer of de SMS-connector daadwerkelijk is gebonden aan de apparatuur van de provider. Vraag de leverancier om feedback om te controleren of alle systemen correct communiceren. Zie `BIND_TRANSMITTER` en `BIND_TRANSCEIVER PDU`s voor informatie over bindt proces. Mogelijk moet u SMPP-sporen inschakelen voor het oplossen van problemen.

* Als de sporen SMPP toegelaten, controleer dat `SUBMIT_SM PDU` bevat de juiste informatie.

* Controleer of de provider reageert met een `SUBMIT_SM_RESP PDU` met een waarde &quot;OK&quot; (code 0). Zorg ervoor dat de PDU met een redelijke vertraging aankomt: iets langer dan 1 seconde moet met de leverancier worden besproken, komt het gewoonlijk binnen 100 ms aan.

* Als al deze stappen werken, kunt u erop vertrouwen dat het probleem aan de leverancierszijde is. Zij zullen het oplossen van problemen op hun platform moeten doen.

* Als het werkt maar de productie inconsequent is, probeer aanpassend het verzendende venster en verminderend de productie MT. U zult met de leverancier moeten werken om dat aan te passen. Adobe Campaign kan zeer snel berichten verzenden zodat kunnen de prestatiesproblemen zich op het materiaal van de leverancier voordoen.

## MT worden gedupliceerd (zelfde SMS wordt verzonden veelvoudige tijden in een rij){#duplicated-MT}

Duplicaten worden vaak veroorzaakt door nieuwe pogingen. Het is normaal om duplicaten te hebben wanneer het opnieuw proberen van berichten, zou u moeten proberen om de worteloorzaak van herpogingen te verwijderen.

* Als u duplicaten ziet die precies 60 seconden van elkaar zijn verwijderd, is dit waarschijnlijk een probleem aan de aanbodzijde, wordt er geen `SUBMIT_SM_RESP` snel genoeg.

* Als u veel `BIND/UNBIND`, u hebt een instabiele verbinding. Zie de[Probleem met instabiele verbindingen](troubleshooting-sms.md#issues-unstable-connection) voor oplossingen alvorens dubbele berichtkwesties op te lossen.

Het aantal duplicaten verlagen wanneer het opnieuw wordt uitgevoerd:

* Laat het verzendvenster lager. De verzendvenster moet groot genoeg zijn om de latency `SUBMIT_SM_RESP` te dekken. De waarde is het maximale aantal berichten dat kan worden gedupliceerd als er een fout optreedt terwijl het venster vol is.

## Uitgave bij verwerking van SR (ontvangstbewijzen) {#issue-process-SR}

* U hebt SMPP-sporen nodig die zijn ingeschakeld voor het uitvoeren van elk type SR-probleemoplossing.

* Controleer of de `DELIVER_SM PDU` komt van de leverancier en is goed gevormd.

* Controleer of Adobe Campaign tijdig met succes `DELIVER_SM_RESP PDU` reageert. Voor Adobe Campaign Classic garandeert dit dat de SR in de `providerMsgId` tabel is opgenomen voor uitgestelde verwerking via het SMS-proces.

Als het `DELIVER_SM PDU` document niet is bevestigd, moet u het volgende controleren:

* Controleer regex met betrekking tot id-extractie en foutverwerking in het **externe account**. Mogelijk moet u deze valideren aan de slag met de inhoud van de `DELIVER_SM PDU`extensie .

* Controleer of fouten correct zijn opgegeven in de `broadLogMsg` tabel.

Als de `DELIVER_SM PDU` is erkend door de Adobe Campaign Classic extended SMPP-connector, maar het wideLog is niet correct bijgewerkt. Controleer het in de sectie beschreven proces voor het afstemmen van de id [Overeenkomende MT-, SR- en Broadlog-vermeldingen](sms-protocol.md#matching-mt).

Als u alles hebt gecorrigeerd, maar sommige ongeldige SR nog steeds in de buffers van de provider staan, kunt u deze overslaan met de optie &quot;Ongeldige id bevestigt telling&quot;. Dit dient met voorzichtigheid te worden gebruikt en zo snel mogelijk na het schoonmaken van de buffers op 0 te worden ingesteld.

## Probleem bij verwerking MO (en zwarte lijst/automatisch antwoord){#issue-process-MO}

* SMPP-sporen inschakelen tijdens tests. Als u TLS niet toelaat, zou u een netwerk moeten doen vangt wanneer het oplossen van problemenMO om te controleren dat PDUs de correcte informatie bevatten en behoorlijk geformatteerd zijn.

* Wanneer het vangen van netwerkverkeer of het analyseren van sporen SMPP, ben zeker om het volledige gesprek met MO en zijn antwoord MT te vangen als een antwoord wordt gevormd.

* Als de MO (`DELIVER_SM PDU`) niet in de sporen wordt weergegeven, het probleem ligt aan de aanbodzijde. Zij zullen het oplossen van problemen op hun platform moeten doen.

* Als de `DELIVER_SM PDU` wordt weergegeven, controleert u of het door Adobe Campaign is erkend met succes `DELIVER_SM_RESP PDU` (code 0). Dit RESP garandeert dat alle verwerkingslogica is toegepast door Adobe Campaign (automatisch antwoord en allow/lijst van gewezen personen). Als het niet het geval is, zoek naar een foutenmelding in de het proceslogboeken van SMS.

* Als automatische reacties zijn ingeschakeld, controleert u of de `SUBMIT_SM` is naar de provider verzonden. Als niet, is het gegarandeerd om een foutenmelding in de het proceslogboeken van SMS te vinden.

* Als de `SUBMIT_SM MT PDU` die het antwoord bevat, wordt in de tracés gevonden maar het SMS komt niet aan de mobiele telefoon, u moet contact opnemen met de provider voor hulp bij het oplossen van problemen.

## Uitgave tijdens de voorbereiding van de levering, exclusief in quarantaine geplaatste ontvangers (in quarantaine geplaatst door de functie voor automatisch antwoord) {#issue-delivery-preparation}

* Controleer dat het formaat van het telefoonaantal precies het zelfde in de quarantainelijst en in het leveringslogboek is. Als het niet is, verwijs naar dit [sectie](sms-protocol.md#automatic-reply) als u problemen hebt met het plus-voorvoegsel van de internationale notatie voor telefoonnummers.

* Controleer korte codes. Uitsluitingen kunnen optreden als de korte code van de ontvanger gelijk is aan de code die in de externe account is gedefinieerd of als deze leeg is (leeg = enige snelcode). Als er maar één korte code wordt gebruikt voor de hele Adobe Campaign-instantie, is het eenvoudiger om alles te laten **korte code** velden zijn leeg.

## Coderingsproblemen {#encoding-issues}

**Stap 1: Neem contact op met de provider**

Neem contact met hen op en zie wat er mis is met hen. Ze moeten je kunnen vertellen of het probleem aan hun kant of aan Adobe Campaign ligt. Als het probleem zich in Adobe Campaign voordoet, moeten ze u exact kunnen vertellen welk veld onjuist is.

**Stap 2: Weet wat in uw bericht is**

Unicode staat veel varianten voor look-alike karakters toe en Adobe Campaign kan niet hen allen behandelen.

De meest voorkomende bron van problemen is een kopie-plak van een tekstverwerker, waarbij gewone tekens worden gewijzigd in typografisch correcte versies: spaties veranderen in vaste spaties, dubbele aanhalingstekens veranderen in open en sluitende aanhalingstekens, min-tekens gewijzigd in verschillende soorten afbreekstreepjes, enz.

Kopieer uw bericht niet en plak het tijdens het testen altijd rechtstreeks in de interface.

Met hexadecimaal kunt u het verschil zien tussen vergelijkbare tekens. Een L in kleine letters, een I in hoofdletters, O, 0, alle verschillende typen aanhalingstekens, niet-Latijnse coderingen of zelfs verschillende typen spaties kunnen er allemaal hetzelfde uitzien of zelfs helemaal niet worden weergegeven.

Om unicode in hexadecimaal om te zetten, kunt u online hulpmiddelen zoals gebruiken [Unicode-codeconverter](https://r12a.github.io/app-conversion/) website. Typ in de tekst, controleer of er geen PII is zoals telefoonnummers en klik op **Omzetten**. De hexadecimale waarden worden onderaan weergegeven (UTF-32-zone).

Bij het openen van tickets over coderingsproblemen, ongeacht of dit gebeurt bij de provider of [Klantenservice Adoben](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)Neem altijd een hexadecimale versie op van wat u typt en wat u ziet.

**Stap 3: weet wat u moet verzenden**

Bepaal de codering die u wilt gebruiken en zoek online naar de bijbehorende tekentabel. Controleer of de tekens die u wilt verzenden, daadwerkelijk beschikbaar zijn op de doelcodepagina. Controleer of de `data_coding` het veld is juist en komt overeen met wat u en de provider verwachten.

**Stap 4: weet wat u daadwerkelijk hebt verzonden**

U zult zuivert output van de schakelaar nodig hebben om precies te zien welke bytes u naar de leverancier verzendt. Coderingsproblemen verschijnen in `SUBMIT_SM PDU`s, zorg er dus voor dat u ze vastlegt. Verzend zeer duidelijke berichten die gemakkelijk in het logboek zijn te vinden.

Verschillende soorten speciale tekens verzenden tijdens het testen. GSM7-codering bevat bijvoorbeeld uitgebreide tekens die sterk van elkaar verschillen in hun hexadecimale vorm. Ze zijn gemakkelijk te vinden omdat ze niet in andere codering worden weergegeven.

## Elementen die moeten worden opgenomen bij communicatie over een SMS-probleem {#element-include}

Wanneer u om hulp over een kwestie van SMS, of het een steunkaartje aan Adobe Campaign, aan de leverancier van SMS, of om het even welk soort mededeling over de kwestie opent, zult u de volgende informatie moeten omvatten om ervoor te zorgen dat het behoorlijk gekwalificeerd zal zijn. Goed gekwalificeerde problemen zijn essentieel om problemen sneller op te lossen.

* **Brede SMPP-berichten inschakelen** wanneer het probleem verschijnt. De meeste SMS-problemen kunnen zonder deze oplossing niet worden opgelost.

* Als het probleem met het verkeer van SMS verwant is, contacteer eerst de leverancier. Hun platform is het meest geschikt voor efficiënte diagnose van de verkeersproblemen van SMS in real time.

* Neem een korte, maar feitelijke beschrijving van het probleem op.

* Een beschrijving van het verwachte resultaat opnemen.

* Neem de feedback van de provider op.

* Inclusief relevante logboeken en/of netwerkvastleggingen. Zorg er tijdens het vastleggen voor dat het probleem tijdens het vastleggen wordt gereproduceerd.

* Als u logboeken, sporen of vangen omvat, wijs de nauwkeurige plaats in het dossier aan wanneer het probleem verschijnt.

* Als u berichten, PDUs of logboeken van verwijzingen voorziet, duidelijk hun timestamp verklaren om hen gemakkelijker te maken te vinden.

* Probeer het probleem op een testomgeving te reproduceren. Als u niet zeker bent over een instelling, probeert u deze in de testomgeving en controleert u het resultaat met de SMPP-sporen. Het is doorgaans beter om problemen te melden die worden gerepliceerd in testomgevingen dan rechtstreeks problemen in productieomgevingen te melden.

* Neem alle wijzigingen of aanpassingen op die op het platform zijn aangebracht. Voeg ook alle wijzigingen toe die de provider mogelijk aan zijn kant heeft aangebracht.

### Netwerkvastlegging {#network-capture}

Een netwerk vangt is niet altijd nodig, gewoonlijk zijn de uitgebreide SMPP- berichten genoeg. Hier zijn sommige richtlijnen die u zullen helpen bepalen als een netwerk vangt nodig is:

* Verbindingsproblemen, maar de uitgebreide berichten tonen geen `BIND_RESP PDU`.

* Onverklaarbare ontkoppelingen zonder foutbericht, het gebruikelijke gedrag van de connector wanneer een protocolfout van het lage niveau wordt gedetecteerd.

* De leverancier klaagt over unbind/disconnection proces.

* Coderingsproblemen in optionele TLV-velden.

* Vermoedelijk wordt verkeer gemengd tussen verschillende verbindingen.

In alle andere situaties, probeer om verbose SMPP- berichten eerst te analyseren en een netwerk te verzoeken vangt slechts als de informatie in de verbose logboeken mist.

In sommige gevallen is het vastleggen van netwerkverkeer niet nodig. Hier volgen de meest voorkomende situaties:

* TLS ingeschakeld: TLS-verkeer wordt per definitie gecodeerd zodat het niet kan worden vastgelegd.

* Prestatieproblemen: logboeken bevatten alle benodigde informatie om prestatieproblemen op te sporen.

* Timingproblemen (`retry timing`, `enquire_link` punt, doorvoerlimiet, enz.)

* SR parseren en verwerken: uitgebreide logboeken geven veel meer context en een betere presentatie.

* MO-verwerking (automatische antwoorden, quarantaine).

* Fouten waarbij geen daadwerkelijk SMPP-verkeer is betrokken: voorbereiding van levering, problemen met de API van het berichtcentrum, workflowproblemen, enz.

## SMP-sporen inschakelen {#enabling-smpp-traces}

De nieuwe schakelaar steunt uitgebreide het registreren door sporen: SMPP. De sporen zijn output in het MTA logboek, niet op de standaardoutput.

**Per externe account inschakelen (voorkeursmethode)**

1. In de **Externe rekening**, controle **Brede SMPP-sporen inschakelen in het logbestand**.
1. Wacht 10 minuten om de server externe accounts opnieuw te laten laden.

Het zou nu actief moeten zijn.

**Configuratie inschakelen**

In de `config-instance.xml` , stelt u de volgende parameters in:

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## Het aantal open verbindingen op een container controleren {#open-connections}

Als u het aantal open verbindingen op een container wilt controleren, kunt u de volgende opdracht gebruiken:

```
(for pid in $(ss -neopts  | sed -n 's/^.*:3600[ \t].*users:(([0-9A-Za-z"]*,pid=\([0-9]*\),.*$/\1/p' | sort ); do  cat /proc/$pid/cmdline; echo  " $pid" ;done;) | uniq --count
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

4 open verbindingen voor het sms proces en 2 per mta kind met 5 kinderen.
