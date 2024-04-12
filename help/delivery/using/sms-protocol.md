---
product: campaign
title: Protocol en instellingen voor sms-connector
description: Meer informatie over de SMS-connector en hoe u deze configureert
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: SMS
role: Developer, Data Engineer
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '8445'
ht-degree: 0%

---

# Protocol en instellingen voor sms-connector {#sms-connector-protocol}

>[!NOTE]
>
>In dit document verwijzen alle verwijzingen naar details over het protocol, veldnamen en waarden naar de [SMPP 3.4-specificatie](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).
>

## Overzicht {#overview}

SMS kan beperkt zijn tot het verzenden van korte tekstberichten zonder opmaak, maar de eenvoud ervan maakt het een waardevol communicatiekanaal.

Er zijn twee belangrijke manieren om SMS te verzenden:

* Verzend het manueel van een telefoon, de gebruikelijke manier om rechtstreeks tussen mensen te communiceren.
* Verzend het via internet, zoals Adobe Campaign berichten verzendt. Hiervoor hebt u een SMS-serviceprovider nodig die verbinding maakt met het mobiele netwerk.
Adobe Campaign gebruikt het protocol SMPP om SMS naar een dienstverlener te verzenden.

In dit document wordt de verbinding tussen Adobe Campaign en een SMPP-provider besproken.

SMPP-aanbieders kunnen soms afwijken van de officiële specificaties, maar de SMS-connector in Adobe Campaign biedt veel mogelijkheden om het gedrag aan te passen zodat het compatibel is met de meeste aanbieders.

>[!IMPORTANT]
>
>De vestiging een verbinding aan een nieuwe leverancier kan sommige technische vaardigheden, kennis van TCP, binaire, hexadecimale vertegenwoordiging en tekstcoderingen vereisen. Het zal ook actieve samenwerking met de leverancier vereisen.

### Typen SMS {#sms-types}

Wanneer u SMS-berichten verzendt via een SMS-provider, worden er drie verschillende soorten SMS-berichten weergegeven:

* **SMS MT (mobiel beëindigd)**: een SMS dat door Adobe Campaign via de SMPP-provider naar mobiele telefoons wordt gezonden.

* **SMS MO (mobiele oorsprong)**: een SMS dat door een mobiele telefoon via de SMPP-provider naar Adobe Campaign wordt verzonden.

* **SMS SR (Statusrapport) of DR. of DLR (Ontvangstbewijs)**: een door de mobiele telefoon via de SMPP-provider aan Adobe Campaign verzonden ontvangstbewijs waaruit blijkt dat het SMS met succes is ontvangen. Adobe Campaign kan ook SR ontvangen om aan te geven dat het bericht niet kan worden verzonden, vaak met een beschrijving van de fout.

U moet tussen erkenning (RESP PDU, een deel van het protocol SMPP) en SR onderscheid maken: SR is een soort SMS dat door het netwerk van begin tot eind wordt verzonden, terwijl een erkenning slechts een bevestiging is dat één overdracht succesvol is geweest.

Zowel erkenningen als SR kunnen fouten teweegbrengen, die tussen twee onderscheiden zal helpen het oplossen van problemen.

### Informatie die via een SMS wordt verzonden {#information-sms}

Een SMS bevat meer informatie dan tekst. Hier een lijst van wat u in SMS kunt verwachten te vinden:

* De tekst, die is beperkt tot 140 bytes, wat betekent tussen 70 en 160 karakters afhankelijk van de codering. Zie [SMS-tekstcodering](sms-protocol.md#sms-text-encoding) hieronder voor details en beperkingen.

* Een geadresseerd adres, soms ook wel `ADC` of `MSISDN`. Dat is het nummer van de mobiele telefoon die het SMS zal ontvangen.

* Een afzenderadres, dat kan worden genoemd `oADC` of soms `sender id`. Dat kan een telefoonaantal in daggebruik, een korte code zijn wanneer verzonden door een leverancier of een naam. Naam is een facultatieve eigenschap, in dat geval kunt u niet op SMS antwoorden.

* Een markering die aangeeft of het bericht een Flash-bericht is. Een flitsbericht is een pop-up die niet in geheugen wordt opgeslagen.

* Een vlag die aangeeft of een SR wordt verwacht of niet.

* Een geldigheidsdatum, waarna geen netwerkmateriaal wordt toegestaan om opnieuw te proberen.

* A `data_coding` veld, dat de codering van de tekst aangeeft.

## SMPP-protocol {#smpp-protocol}

Adobe Campaign Classic ondersteunt versie 3.4 van het SMPP-protocol. Dit is een wijdverbreid protocol dat het verzenden van SMS naar een leverancier (SMSC) en het ontvangen van SMS evenals ontvangstbewijzen toestaat. Raadpleeg voor meer informatie de [SMPP-documentatie](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Het netwerkmateriaal op de dienstverlener van SMS wordt vaak genoemd SMSC.

### SMPP-verbindingen {#smpp-connections}

Adobe Campaign maakt via TCP verbinding met de netwerkapparatuur van de SMS-serviceprovider. Het protocol SMPP plaatst permanente verbindingen van TCP van Adobe Campaign aan de leverancier. TCP-verbindingen worden altijd geïnitieerd door Adobe Campaign, zelfs om berichten te ontvangen.
SMPP opent 1 of 2 verbindingen van TCP, afhankelijk van zijn wijze. Alle verbindingen worden altijd geïnitieerd door Adobe Campaign.

Het protocol SMPP kan in twee wijzen werken:

* **Transmitter+ontvanger (of TX+RX)**: Voor het verzenden en ontvangen van berichten worden twee afzonderlijke TCP-verbindingen gebruikt.
* **Transceiver (of TRX)**: Eén TCP-verbinding wordt gebruikt voor het verzenden en ontvangen van berichten.

>[!NOTE]
>
> Adobe Campaign Classic ondersteunt alleen de TX+RX-modus. Deze beperking komt door de technische architectuur ervan.

### SMPP PDU {#smpp-pdu}

De transmissieeenheden van SMPP (&quot;pakketten&quot;) worden genoemd PDUs. A **PDU** bevat een opdracht, een status, een volgnummer en gegevens.

Elke PDU moet door een `SMPP RESP PDU` (synchrone reactie). Aanvragen kunnen via pijpleidingen worden verzonden: de afzender kan veel opdrachten verzenden zonder te wachten op `RESP`Het aantal aanvragen dat op elk gewenst moment via een pijpleiding kan worden verzonden, wordt het venster genoemd. `RESP PDU` kan in om het even welke orde aankomen, los van de orde van hun overeenkomstige initiator PDU.

In het gescheiden **Transmitter+ontvanger** de gebruikte verbinding is afhankelijk van het type verzonden bericht. De transmissieverbinding wordt gebruikt voor MT, en de ontvangerverbinding wordt gebruikt voor MO en SR. De verzoeken en de reacties voor elk soort bericht worden verzonden over de zelfde verbinding van TCP.

Bij het verzenden van een MT wordt bijvoorbeeld de verzendingsverbinding gebruikt en de `RESP` dat erkent wordt MT ook verzonden door het zenderkanaal. Wanneer u een MO (of een SR) ontvangt, wordt de ontvangerverbinding gebruikt om MO te ontvangen en om te verzenden `RESP` dat de GMO erkent.

![](assets/do-not-localize/sms_protocol_1.png)

In Adobe Campaign Classic geeft het SMSC, om SR met de bijbehorende MT te koppelen, een ID met de `SUBMIT_SM_RESP` en `DELIVER_SM` stappen. De id wordt opgeslagen in het dialoogvenster `providerId` van het `nms::providerMsgId` tabel en is gekoppeld aan `broadLogId` en `deliveryId`. Deze passende verrichting wordt gedaan door het proces van SMS wanneer het schrijven aan het gegevensbestand.

Een geslaagde `SUBMIT_SM_RESP PDU` activeert de &quot;verzonden&quot;berichtstatus in het verzendende logboek terwijl succesvol `DELIVER_SM (SR) PDU` activeert de status van het &quot;ontvangen&quot; bericht.

### Beveiligingsaspecten {#security-aspects}

Het protocol zelf is niet gecodeerd. De meeste leveranciers voeren een variant van IP op lijst van gewenste personen uit zodat moeten de serverIP van Adobe Campaign adressen aan de leverancier worden verklaard.

Adobe Campaign ondersteunt het doorgeven van een aanmelding en een wachtwoord tijdens de bind fase. Ook SMPP via TLS wordt ondersteund. Er zij op gewezen dat certificaten vereist zijn voor een goede beveiliging. Hoewel met de SMPP-connector certificaatcontroles kunnen worden overgeslagen, mag deze alleen worden gebruikt voor tests, aangezien TLS zonder certificaten een aanzienlijk lager beveiligingsniveau biedt.

De schakelaar gebruikt de standaardcertificaten die door het systeem worden verstrekt `openssl` bibliotheek. Meestal wordt het geleverd door de `/etc/ssl/certs` directory op Debian. Deze map wordt standaard geleverd door het pakket &quot;ca-certificates&quot;, maar kan worden aangepast.

### Informatie in elke soort PDU {#information-pdu}

Elk type PDU heeft verschillende gebieden die verschillende stukken van informatie dragen. Deze PDU&#39;s worden beschreven in het dialoogvenster [SMPP 3.4-specificatie](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

In elke onderstaande sectie worden zowel de PDU als de synchrone respons beschreven (`*_RESP PDU`). Alle PDU&#39;s moeten worden herkend door een corresponderende `RESP`, is dit een verplicht onderdeel van het productdossier.

PDU&#39;s kunnen optionele velden hebben. Alleen de meest voorkomende velden worden hier beschreven. Zie de [SMPP 3.4-specificatie](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) voor meer informatie .

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSCEIVER**

Deze PDU wordt gebruikt om een verbinding met SMSC in werking te stellen. **Transmitter**, **Ontvanger** en **Transceiver** De modi wijzigen alleen het type SMS dat via deze verbinding mag worden overgedragen, met name:

| Modus | Typen SMS toegestaan |
|:-:|:-:|
| Transmitter | MT |
| Ontvanger | MO + SR |
| Transceiver | MT + MO + SR |

Opvallende velden in een `BIND_* PDU`:

* **system_id**: Aanmelding gebruikt voor verificatie. Instellen in de externe account.

* **password**: Wachtwoord voor verificatie. Instellen in de externe account.

* **system_type**: Vereist om voor sommige providers op een specifieke waarde te worden ingesteld. Instellen in de externe account, beschikbaar in alle versies. Vaak wordt onderscheid gemaakt tussen verschillende soorten contracten, kanalen, landen, enz.

* **addr_ton** en **addr_npi**: Vereist door sommige providers. Door de `Bind TON` en `Bind NPI` instellingen in de externe account.

* **address_range**: Vereist door sommige providers. Meestal is dit een lijst met toegestane snelcodes voor deze verbinding. Instellen in de externe account.

`BIND_*_RESP` heeft geen specifiek veld, wordt bevestigd of de verbinding is gelukt of niet.

#### ONBINDEN {#unbind}

Deze PDU moet door het systeem worden verzonden alvorens los te maken van. De overeenkomst moet worden afgewacht `UNBIND_RESP` PDU alvorens de verbinding te sluiten.

Als u SMSC in overeenstemming acht, mag de verbinding niet worden gesloten, wordt de TCP-verbinding bestuurd door de Adobe Campaign-connector.

#### VERZENDEN_SM {#submit-sm}

Deze PDU verzendt een MT naar SMSC. Zijn reactie PDU geeft identiteitskaart van MT.

Opvallende velden in een `SUBMIT_SM` PDU:

* **service_type**: vereist door sommige aanbieders. Instellen in de eigenschappen van de levering.

* **source_addr_ton** en **source_addr_npi**: geeft aan welk type bronadres wordt verzonden. De betekenis van deze gebieden wordt gestandaardiseerd, maar aangezien sommige leveranciers het verschillend gebruiken, zou u de leverancier om zijn correcte waarde moeten vragen. Instellen in de externe account.

* **source_addr**: het bronadres / de ADC van de MT. Het wordt weergegeven op de mobiele telefoon. De waarde in de levering wordt in de externe account en in de levering ingesteld en heeft voorrang op de waarde van de externe account.

* **dest_addr_ton** en **dest_addr_npi**: geeft aan welk soort bestemmingsadres wordt verzonden (bijvoorbeeld lokale of internationale indeling). De betekenis van deze gebieden wordt gestandaardiseerd, maar aangezien sommige leveranciers het verschillend gebruiken, zou u de leverancier om zijn correcte waarde moeten vragen. Instellen in de externe account.

* **destination_addr**: geadresseerd adres, telefoonnummer of MSISDN.

* **esm_class**: wordt gebruikt om te bepalen of UDH wordt gebruikt of niet in het tekstveld. Automatisch ingeschakeld door de connector voor gesplitste SMS als de `message_payload` wordt niet gebruikt.

* **priority_flag**: prioriteit van deze boodschap boven anderen. Dit hangt samen met de prioriteit van de levering zelf.

* **validity_period**: tijdstempel waarna geen poging opnieuw moet worden uitgevoerd. In de levering zelf instellen.

* **registered_delivery**: geeft aan of een SR is aangevraagd of niet. Adobe Campaign stelt deze markering altijd in, behalve voor automatische reacties. Bij multipart-berichten wordt de markering alleen ingesteld voor het eerste deel. Alle versies hebben hetzelfde gedrag.

* **data_coding**: geeft de codering aan die in het tekstveld wordt gebruikt. Zie de [SMS-tekstcodering](sms-protocol.md#sms-text-encoding) voor meer informatie.

* **short_message**: de tekst van het bericht. Als UDH wordt gebruikt, bevat dit ook de UHD-header.

Adobe Campaign ondersteunt de volgende optionele velden:

* **dest_addr_subunit**: wordt gebruikt om het doel van SMS op te geven: flash, mobile of SIM-kaart. Instellen in de eigenschappen van de levering.

* **message_payload**: als deze optie is ingeschakeld in de externe account, worden lange berichten verzonden in één PDU en wordt de tekst in dit veld verzonden in plaats van in de `short_message` veld.

#### SUBMIT_SM_RESP {#submit-sm-resp}

Deze PDU zal identiteitskaart van MT bevatten. Dit is handig om deze aan te passen aan de binnenkomende SR.

>[!IMPORTANT]
>
>Vele leveranciers brengen identiteitskaart MT in hexadecimaal over. Zorg ervoor dat u de **ID-indeling in MT-bevestiging** correct instellen in de externe account.

Sommige providers verzenden `SUBMIT_SM_RESP` na verzending van de SR. Adobe Campaign wacht 30 seconden op het beantwoorden van dit gedrag om dit te verantwoorden **Ongeldige bericht-id** naar een SR met een onbekende id.

#### DELIVER_SM {#delivery-sm}

Deze PDU wordt door SMSC naar Adobe Campaign verzonden. Het bevat een MO of een SR.

De meeste velden hebben dezelfde betekenis als hun `SUBMIT_SM` tegenhanger. Hier volgt een lijst met nuttige velden:

* **source_addr**: bronadres van de MO/SR. Meestal is dit een telefoonnummer.

* **destination_addr**: korte code die de MO of de SR heeft ontvangen.

* **esm_class**: wordt gebruikt om te bepalen of PDU een MO of een SR is.

* **short_message**: tekst van het bericht. Voor SR bevat dit de gegevens die worden beschreven in aanhangsel B van de specificatie van het SMPP-protocol. Zie [SR-foutbeheer](sms-protocol.md#sr-error-management) voor meer informatie .

Adobe Campaign kan bericht-id lezen in het dialoogvenster `receipted_message_id` optioneel veld met een bepaalde configuratie.

#### DELIVER_SM_RESP {#deliver-sm-resp}

Deze PDU wordt door Adobe Campaign verzonden om SR en MO te erkennen.

Adobe Campaign Classic erkent SR en MO zodra deze in de database zijn ingevoegd. Er kunnen zich verwerkingsfouten voordoen, zelfs als de `DELIVER_SM_RESP` PDU is verzonden. Deze beperking wordt veroorzaakt door de softwarearchitectuur van Adobe Campaign Classic.

#### INQUIRE_LINK {#enquire-links}

Deze PDU wordt alleen gebruikt om te controleren of de verbinding live is. De frequentie moet worden vastgesteld op basis van de behoeften van de aanbieder.

De standaardconfiguratie 60 seconden moet overeenkomen met de meeste configuraties die zijn ingesteld in de externe account.

#### INQUIRE_LINK_RESP {#enquire-links-resp}

Deze PDU erkent dat de verbinding levend is.

### Multipart SMS (lang SMS) {#multipart}

>[!IMPORTANT]
>
> Adobe Campaign ondersteunt alleen multipart SMS of long SMS voor verzending. UDH en `message_payload` worden niet ondersteund voor binnenkomende SMS (MO), wat betekent dat MO beperkt is tot 160 tekens.

Multipart SMS, of lange SMS, zijn SMS die in veelvoudige delen worden verzonden. Vanwege technische beperkingen in het mobiele netwerkprotocol kan een SMS niet groter zijn dan 140 bytes of moet het worden gesplitst. Zie de [SMS-tekstcodering](sms-protocol.md#sms-text-encoding) voor meer informatie over het aantal tekens dat in een SMS kan worden geplaatst.

Elk deel van een lang bericht is een individueel SMS. Deze onderdelen reizen onafhankelijk op het netwerk en worden door de ontvangende mobiele telefoon gemonteerd. Om herpogingen en connectiviteitsproblemen te behandelen, verzendt Adobe Campaign deze delen in omgekeerde orde en verzoekt slechts om SR op het eerste deel van het bericht, het laatst verzonden. Aangezien de mobiele telefoon alleen een bericht weergeeft wanneer het eerste deel ervan is ontvangen, worden bij nieuwe pogingen op extra onderdelen geen duplicaten op de mobiele telefoon gegenereerd.

Het maximumaantal SMS per bericht kan per levering worden geplaatst gebruikend **Maximum aantal SMS per bericht** in het dialoogvenster **Afleveringssjabloon**. Berichten die deze limiet overschrijden, mislukken tijdens het verzenden met een te lange reden voor SMS-fout.

Er zijn twee manieren om lange SMS te verzenden:

* **UDH**: de standaard en aanbevolen manier om lange berichten te verzenden. In deze modus splitst de connector het bericht in meerdere `SUBMIT_SM PDU`Net als bij UDH-informatie. Dit protocol wordt gebruikt door mobiele telefoons zelf. Dit betekent dat Adobe Campaign de meeste controle heeft over het genereren van berichten, waardoor het precies kan berekenen hoeveel onderdelen zijn verzonden en hoe ze zijn gesplitst.

* **message_payload**: de manier om de hele lange boodschap in één keer te verzenden `SUBMIT_SM PDU`. De aanbieder moet het opsplitsen, wat betekent dat het voor Adobe Campaign onmogelijk is precies te weten hoeveel onderdelen zijn verzonden. Sommige providers vereisen deze modus, maar we raden u aan deze alleen te gebruiken als ze UDH niet ondersteunen.

Zie de beschrijving van de `esm_class`, `short_message` en `message_payload` van de [VERZENDEN_SM PDU](sms-protocol.md#information-pdu) voor meer informatie over het protocol en de formaten.

### Vastzetten en ramen van doorvoer {#throughput-capping}

De meeste leveranciers vereisen een productielimiet voor elke verbinding SMPP. Dit kan worden bereikt door een aantal SMS in te stellen in de externe account. Merk op dat de productiesnelheid per verbinding gebeurt, is de totale efficiënte productie de grens per verbinding die door het totale aantal verbindingen wordt vermenigvuldigd. Dit wordt beschreven in het [Gelijktijdige verbindingen](sms-protocol.md#connection-settings) sectie.

Om maximum mogelijke productie te bereiken, zult u het maximum verzendende venster moeten verfijnen. Het verzendende venster is het aantal `SUBMIT_SM PDU`s die kunnen worden verzonden zonder te wachten op `SUBMIT_SM_RESP`. Zie de [Instelling voor venster verzenden](sms-protocol.md#throughput-timeouts) voor meer informatie.

### SR- en foutbeheer (&quot;Bijlage B&quot;) {#sr-error-management}

Het protocol SMPP bepaalt standaard synchrone fouten in `RESP PDU`s, maar er worden geen foutcodes voor SR gedefinieerd. Elke provider gebruikt zijn eigen foutcodes met hun betekenis.

Een aanbeveling wordt gedaan in aanhangsel B van het [SMPP-protocolspecificatie](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (blz. 167), maar hierin worden de werkelijke foutcodes en de betekenis ervan niet vermeld.

Om zich aan foutenbeheer aan te passen, is het systeem van het uitzendingsbericht van Adobe Campaign gebruikt aan behoorlijk leveringsfouten en hun strengheid (hard, zacht, enz.).

Zoals hierboven vermeld, zijn er twee verschillende soorten fouten:

* synchrone antwoorden in de `SUBMIT_SM_RESP` die onmiddellijk na de verzending van het bericht aan het SMSC plaatsvinden
* ontvangstbewijzen die veel later kunnen komen wanneer de mobiele telefoon het bericht ontving of wanneer uit het bericht timed. In dat geval wordt de fout gevonden in een SR.

Wanneer een SR wordt ontvangen, kunnen de status en de fout in zijn `short_message` veld (voorbeeld voor in bijlage B opgenomen conformiteitsimplementaties). De `short_message` het gebied van PDU wordt vaak genoemd **tekstveld** omdat het tekst in MT bevat. In het geval van SR bevat het technische informatie plus een subveld genaamd **Tekst**. Deze twee velden zijn verschillend en `short_message` bevat de **Tekst** veld en andere informatie.

Adobe Campaign Classic-connectors (met uitzondering van Extended SMPP) gebruiken een gehard gedrag dat afhankelijk is van de geselecteerde provider. Algemene SMPP maakt alleen onderscheid tussen succes en fout, zonder detail. Het leveringslogboek kan bepaalde informatie bevatten die niet gegarandeerd is.

#### Indeling van het tekstveld SR {#sr-text-field-format}

De specificatie raadt u aan deze indeling te gebruiken voor het tekstveld SR. Het is een lijst van subvelden, spaties gescheiden met een dubbele punt om de veldnaam en de waarde ervan te scheiden. Veldnamen zijn niet hoofdlettergevoelig.

Voorbeeld van een SR-tekstveld dat overeenkomt met de aanbeveling in aanhangsel B:

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Het veld Id is de id die is ontvangen in het dialoogvenster `SUBMIT_SM_RESP PDU`, de erkenning van de MT.

`sub` en `dlvrd` de hoeveelheid geleverde onderdelen en geleverde berichten moeten tellen, maar dit wordt niet door Adobe Campaign gebruikt omdat het breedbandsysteem betere en meer geïntegreerde informatie biedt.

`submit date` en `done date` de velden zijn indicatieve tijdstempels van wanneer de MT is verzonden en wanneer de SR door de mobiele telefoon is verzonden. Verwacht enkele problemen met tijdzones of zelfs onjuiste tijdstempels die worden gegeven door mobiele apparaten met een onjuiste datumset.

Het statusveld is belangrijk omdat het de status van het bericht aangeeft. De enige belangrijke status is `DELIVRD`, `UNDELIV` en `REJECTD`. De `DELIVRD` de status geeft aan dat de bewerking is geslaagd, de andere twee geven een fout aan. Andere waarden zijn mogelijk, maar doorgaans zijn het tussentijdse meldingen, zoals de MT die de mobiele provider heeft bereikt, maar niet de mobiele telefoon. Deze tussentijdse meldingen worden genegeerd door Adobe Campaign.

Het foutveld bevat de providerspecifieke foutcode. De provider moet een tabel met mogelijke foutcodes en de betekenis ervan opgeven om deze waarde te kunnen interpreteren.

Ten slotte bevat het tekstveld gewoonlijk het begin van de tekst van de MT. Dit wordt genegeerd door Adobe Campaign en sommige providers verzenden het niet om PII-lekkage en netwerkbandbreedteverbruik te voorkomen. Het kan tijdens het oplossen van problemen worden gebruikt om SR te vlekken die een test MT door dit gebied gemakkelijker aanpast te lezen.

### Voorbeeld van SR-verwerking in Adobe Campaign Classic Extended algemeen SMPP {#sr-processing}

In dit voorbeeld wordt het geval van een implementatie weergegeven volgens de aanbeveling in appendix B, de standaardwaarden in de externe account en een geslaagde SMS MT.

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Ten eerste: `id extraction` regex wordt toegepast om de id te extraheren en deze te combineren met de bijbehorende MT.

Vervolgens worden de `status extraction` regex en `error code extraction` regex wordt toegepast om deze velden te extraheren en wordt aan de tekenreeks toegevoegd.

Het breedbandbericht wordt geconstrueerd met deze informatie, en het originele onveranderde koord wordt toegevoegd voor verwijzing:

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Het bericht wordt dan genormaliseerd, verwijderend het deel van het BERICHT om veelvoudige berichten met de zelfde staat en err codes te kunnen aanpassen.

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

Als het bericht niet reeds provisioned in de lijst van het uitzendingsbericht is, zal een nieuwe ingang worden gecreeerd, gebruikend het volledige bericht als **firstText** en het genormaliseerde bericht. Dan, gebruikt de schakelaar het succes en `error` regex om te bepalen of het een succes of een mislukking was:

* Als het overeenkomt met de `success` regex zal als een succes worden beschouwd .

* Als het overeenkomt met de `error` regex, wordt het bericht gekwalificeerd als fout.

* Als geen van deze twee regex-overeenkomsten overeenkomen, wordt de SR genegeerd. Het zou een tussenmelding kunnen zijn, die niet door Adobe Campaign wordt behandeld.

Standaard worden alle fouten weergegeven als schermfouten. Dit betekent dat harde fouten met de hand moeten worden opgelost.

### SMS-tekstcodering {#sms-text-encoding}

U moet **altijd contact opnemen met de SMSC-provider in het geval van coderingsproblemen**. Alleen de SMSC-aanbieders hebben kennis van de codering die zij ondersteunen en van de speciale regels die van toepassing kunnen zijn vanwege beperkingen in hun technische platform.

SMS-berichten gebruiken een speciale 7-bits codering, vaak de GSM7-codering genoemd.

In het protocol SMPP, zal de tekst GSM7 tot 8 beetjes per karakter voor het gemakkelijkere oplossen van problemen worden uitgebreid. Het SMSC zal het in 7 beetjes per karakter verpakken alvorens het naar mobiel wordt verzonden. Dit betekent dat de `short_message` Het veld van het SMS mag maximaal 160 bytes lang zijn in het SMPP-frame, terwijl het beperkt is tot 140 bytes wanneer het wordt verzonden op het mobiele netwerk.

In het geval van coderingsproblemen moet u een aantal belangrijke zaken controleren:

* Zorg ervoor dat u weet tot welke tekens codering behoort. GSM7 steunt niet volledig diakritische tekens of accenten. Vooral in het Frans, waar é en è deel uitmaken van GSM7, maar ê, â of ï niet. Hetzelfde geldt voor het Spaans.

* De C met cedilla (ç) is alleen in hoofdletters aanwezig in het GSM7 alfabet, maar sommige telefoons geven het in kleine letters of &quot;slimme&quot; gevallen terug. De algemene aanbeveling is om dit volledig te vermijden en het cedilla of de overschakeling op UCS-2 te verwijderen.

* **Gebruik ASCII niet in SMS** tenzij de SMSC-aanbieder uitdrukkelijk daarom verzoekt. Deze codering verspilt ruimte omdat deze 8-bits tekens bevat en minder dekking heeft dan GSM7. Deze codering kan vereist zijn voor CDMA-netwerken die in Noord-Amerika worden gebruikt.

* Latin-1 wordt niet altijd ondersteund. Controleer de compatibiliteit met uw SMSC-provider voordat u Latin-1 gaat gebruiken.

* Tabellen voor nationale taalverschuiving worden niet ondersteund door de Adobe Campaign-connector. U moet UCS-2 of andere `data_coding` in plaats daarvan.

* UCS-2 en UTF-16 worden vaak gemengd door telefoons. Dit is een probleem wanneer emojis en andere karakters worden gebruikt niet aanwezig in UCS-2.

* De meeste telefoons hebben doopvontglyphs niet voor alle karakters UCS-2. Smartphones kunnen zeldzame karakters vrij gemakkelijk tonen, maar eigenschaptelefoons hebben over het algemeen beperkte steun aan wat in de inheemse tong van het land nuttig is zij werden gekocht. Als u emoji of ASCII-kunst wilt gebruiken, test het op een grote verscheidenheid van telefoons alvorens te verzenden. In de Adobe Campaign-voorvertoning worden ontbrekende glyphs niet gesimuleerd en worden symbolen weergegeven die beschikbaar zijn in de webbrowser.

De `data_coding` in het veld wordt aangegeven welke codering wordt gebruikt. Een groot probleem is dat de waarde 0 standaard SMSC-codering in de specificatie betekent, die meestal naar GSM7 verwijst. Vraag de SMSC-partner aan welke codering is gekoppeld `data_coding` = 0 dat alleen door Adobe Campaign wordt ondersteund. Overige `data_coding` De waarden volgen meestal de specificatie, maar de enige manier om zeker te zijn is om met de leverancier van SMSC te controleren.

De maximumgrootte van een bericht hangt van zijn codering af. In deze tabel worden alle relevante gegevens samengevat:

| Codering | Gebruikelijke gegevens_codering | Berichtgrootte (tekens) | Onderdeelformaat voor SMS met meerdere onderdelen | Beschikbare tekens |
|:-:|:-:|:-:|:-:|:-:|
| GSM7 | 0 | 160 | 152 | GSM7 basis tekenset + extensie (uitgebreide tekens nemen 2 tekens in beslag) |
| Latin-1 | 3 | 140 | 134 | ISO-8859-1 |
| UCS-2 <br>UTF-16 | 8 | 70 | 67 | Unicode (varieert van telefoon tot telefoon) |

## SMPP-parameters voor externe account {#SMPP-parameters-external}

Elke implementatie van het protocol SMPP heeft vele variaties. Om de compatibiliteit en het aanpassingsvermogen te verbeteren, zijn er veel instellingen beschikbaar om het gedrag van de SMPP-connector te wijzigen. Deze sectie beschrijft elke parameter en zijn gevolgen op de schakelaar.

### Algemene parameters en routering {#general-parameters-routing}

**MTA-instanties voor deze account beperken**

Het is mogelijk om een grens aan het aantal MTA instanties te plaatsen die met de leverancier SMPP mogen verbinden. Wanneer gecontroleerd, kunt u specificeren hoeveel MTAs maximaal kan worden gebruikt.

Met deze optie hebt u meer controle over het aantal verbindingen. Zie [Gelijktijdige verbindingen](sms-protocol.md#connection-settings).

Als u een waarde hoger dan het aantal lopende MTAs plaatst, zullen alle MTAs normaal lopen: deze optie is slechts een grens en kan geen extra MTAs kweken.

Als u het aantal verbindingen, b.v. leveranciersvereiste moet nauwkeurig controleren, wordt het geadviseerd om deze optie altijd te plaatsen zelfs als de huidige plaatsing het juiste aantal lopende MTAs heeft. Als extra MTAs daarna wordt toegevoegd, zal de verbindingsgrens nog worden geëerbiedigd.

### Verbindingsinstellingen {#connection-settings}

#### Naam van SMSC-implementatie {#smsc-implementation-name}

Hier geeft u de naam van de SMSC-implementatie op. Deze moet op de naam van uw provider worden ingesteld. Neem contact op met de beheerder of het leveringsteam om te weten wat u in dit veld wilt toevoegen. De rol van dit veld wordt beschreven in het gedeelte [SR-foutbeheer](sms-protocol.md#sr-error-management) sectie.

#### Server {#server}

De DNS naam of IP adres van de server om met te verbinden.

#### Poort {#port}

De TCP-poort voor verbinding.

#### Account {#account}

De aanmelding van de verbinding. In het `system_id` veld van de PDU BIND.

#### Wachtwoord {#password}

Wachtwoord van de SMPP-verbinding. Wordt doorgegeven in het wachtwoordveld van de PDU BIND.

#### Systeemtype {#system-type}

Waarde doorgegeven in het dialoogvenster `system_id` veld van de PDU BIND. Sommige providers hebben hier een specifieke waarde nodig.

#### Aantal MTA kindverbindingen {#number-mta-child}

In Adobe Campaign Classic wordt het aantal verbindingen per MTA-onderliggend item gedefinieerd.

De Adobe Campaign Classic Extended SMPP-connector kan het aantal verbindingen per MTA-onderliggend item bepalen. Om de globale grens van verbindingen te controleren, zult u het aantal MTA kindprocessen moeten beperken, wat vaak het hebben van een specifiek midsourcingsplatform voor SMS betekent.

Voor Adobe Campaign Classic kan het aantal ontvangers- en transmissieverbindingen verschillen:

* **Transmitterverbindingen = Aantal MTA kindverbindingen * aantal MTA kindprocessen * aantal MTAs (als auto-antwoord wordt geplaatst) * aantal MTA kindverbindingen**

Zoals hierboven gesuggereerd, opent het proces van Adobe Campaign Classic SMS meer transmissieverbindingen als het auto-antwoord wordt toegelaten. Deze extra verbindingen worden gebruikt om de automatische antwoorden te verzenden.

* **De verbindingen van de ontvanger = Aantal MTA kindverbindingen**

Als u opstelling automatische antwoorden, zal het proces van SMS zenders/ontvangerparen openen, die het aantal transmissieverbindingen verhogen. Als u geen automatische reactie hebt ingesteld, worden alleen de ontvangerverbindingen geopend.

#### TLS inschakelen via SMPP {#enable-TLS}

Gebruik TLS om verbinding te maken met de provider. De verbinding wordt versleuteld. De TLS-verbinding wordt beheerd door de OpenSSL-bibliotheek en alles wat op OpenSSL van toepassing is, geldt voor deze verbinding.

#### Brede SMPP-sporen inschakelen in het logbestand {#enable-verbose-log-file}

Deze instelling dumpt al SMPP-verkeer in logbestanden. Het wordt vaak vereist om parameters tijdens aanvankelijke opstelling aan te passen. Dit moet worden toegelaten wanneer het oplossen van problemen de schakelaar en vergeleken met het verkeer dat door de leverancier wordt gezien.

In Adobe Campaign Classic bevindt de loguitvoer zich in het MTA-logboek voor MT-gerelateerd verkeer en in het SMS-logboek voor MO- en SR-gerelateerd verkeer.

### Verbindingsinstelling ontvanger {#receiver-connection}

Deze sectie is alleen zichtbaar in gescheiden **zender+ontvanger** -modus.

#### Verschillende parameters gebruiken voor de ontvanger {#receiver-parameters}

Als het selectievakje is uitgeschakeld, worden dezelfde instellingen gebruikt voor zender en ontvanger.

Als het selectievakje is ingeschakeld, worden de instellingen in het dialoogvenster **Verbindingsinstellingen** wordt toegepast op de zender en de instellingen in het dialoogvenster **Ontvangerverbinding** de instellingen zijn van toepassing op de ontvanger.

**Ontvangerserver, poort, account, wachtwoord, systeemtype**

Deze instellingen zijn van toepassing op de ontvanger in de modus zender+ontvanger. Ze werken als het zenderdeel, zie hierboven voor meer details.

### SMPP-kanaalinstellingen {#smpp-channel-settings}

#### Tekentransliteratie toestaan {#allow-character-transliteration}

Transliteratie is het zoeken naar tekens die equivalent zijn aan ontbrekende tekens. Het Franse &quot;ê&quot;-teken (e met omstreeks accent) ontbreekt bijvoorbeeld in GSM-codering, maar kan worden vervangen door &quot;e&quot; zonder dat dit de leesbaarheid aantast.

Als dit selectievakje is uitgeschakeld, mislukt de tekstcodering als de tekenreeks niet exact zo kan worden gecodeerd.

Als dit selectievakje is ingeschakeld, probeert de tekstcodering de tekenreeks om te zetten in een versie die bij benadering overeenkomt in plaats van te mislukken. Als sommige tekens geen equivalent hebben in de doelcodering, mislukt de tekstcodering.

Zie de [Een specifieke toewijzing van coderingsinstellingen definiëren](sms-protocol.md#SMSC-specifics) voor een meer algemene uitleg van het coderingsproces.

#### Inkomende MO opslaan in de database {#incoming-mo-storing}

Als deze optie is ingeschakeld, wordt de inkomende MO opgeslagen in de inSMS-tabel van de database. Deze lijst kan worden gevraagd gebruikend de vraagactiviteit van om het even welke werkschema.

Adobe Campaign Classic slaat altijd alle MO&#39;s op in de InSMS-database, zodat deze optie niet beschikbaar is.

#### Real-time KPI-updates inschakelen tijdens SR-verwerking {#real-time-kpi}

Indien toegelaten, KPIs zal in real time op de belangrijkste leveringspagina worden bijgewerkt wanneer het ontvangen van foutSR.

Het nadeel kan lage prestaties wegens het gegevensbestandgeschil zijn het produceert. Indien uitgeschakeld, worden de statistieken bijgewerkt door de **syncfromexec** om de 20 minuten.

Adobe Campaign Classic heeft een geheel ander mechanisme voor KPI&#39;s, dus deze optie is niet beschikbaar.

#### Bronnummer {#source-number}

Bepaalt het standaardbronadres voor berichten. Deze instelling is alleen van toepassing als het bronnummer leeg is gelaten in de levering.

Het veld Bronnummer wordt standaard niet doorgegeven, zodat de provider dit veld vervangt door de korte code.

Dit laat de de opheffingseigenschap van het afzenderadres/oADC toe.

#### Korte code {#short-code}

Geeft de korte hoofdcode van de account aan. Als er meerdere korte codes worden gebruikt voor deze account of als de korte code onbekend is, laat u dit veld leeg.

Het opgeven van korte code is handig voor twee functies:

* In de voorvertoning wordt de korte code weergegeven als er geen bronnummer is opgegeven. Het zal het echte gedrag op de mobiele telefoon weerspiegelen.

* De lijst van gewezen personen die van de auto antwoordeigenschap plaatst verzendt slechts naar quarantaine de gebruiker voor een specifieke korte code.

#### TON/NPI-bron, TON/NPI bestemming {#ton-npi}

TON (type nummer) en NPI (indicator nummerplan) worden beschreven in punt 5.2.5 van het [SMPP 3.4-specificatie](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (bladzijde 117). Deze waarden moeten op de behoeften van de leverancier worden ingesteld.

Ze worden ongewijzigd verzonden in `source_addr_ton`, `source_addr_npi`, `dest_addr_ton` en `dest_addr_npi` van de `SUBMIT_SM PDU`.

#### Servicetype {#service-type}

Dit veld wordt ongewijzigd verzonden in het dialoogvenster `service_type` van het `SUBMIT_SM PDU`. Stel dit in op de behoeften van de provider.

### Doorvoer en time-outs {#throughput-timeouts}

Deze montages controleren alle timingsaspecten van het kanaal SMPP. Sommige leveranciers vereisen zeer nauwkeurige controle van het berichttarief, venster en retry timings. Deze instellingen moeten worden ingesteld op waarden die overeenkomen met de capaciteit van de aanbieder en de voorwaarden die in het contract zijn vermeld.

#### Venster verzenden {#sending-window}

Het venster is het aantal `SUBMIT_SM PDU`Dat kan worden verzonden zonder te wachten op een overeenkomst `SUBMIT_SM_RESP`.

Voorbeeld van een transmissie met een maximum venster van 4:

![](assets/do-not-localize/sms_protocol_2.png)

De vensterhulp verhoogt de productie wanneer de netwerkverbinding een hoge latentie heeft.  De waarde van het venster moet minstens het aantal SMS/s zijn vermenigvuldigd met de latentie van de verbinding in seconden zodat de schakelaar nooit op een `SUBMIT_SM_RESP` voordat u het volgende bericht verzendt.
Als het venster te groot is, kunt u meer dubbele berichten verzenden in het geval van verbindingsproblemen. Bovendien hebben de meeste providers een zeer strikte limiet voor het venster en weigeren berichten die de limiet overschrijden.

Hoe te om de optimale verzendende vensterformule te berekenen:

* De maximale vertraging meten tussen `SUBMIT_SM` en `SUBMIT_SM_RESP`.

* Vermenigvuldig deze waarde in seconden tot de maximale MT-doorvoer. Dit geeft de optimale waarde voor het verzendende venster.

Voorbeeld: als u 300 SMS/s hebt ingesteld in maximale MT-doorvoer en er 100 ms vertraging is tussen `SUBMIT_SM` en `SUBMIT_SM_RESP` gemiddeld zou de optimale waarde `300×0.1 = 30`.

#### Maximale MT-doorvoer {#max-mt-throughput}

Maximum aantal MT per seconde en per verbinding. Deze instelling wordt strikt gehandhaafd, de MTA zal nooit berichten sneller dan deze grens duwen. Het is nuttig voor leveranciers die nauwkeurige vertraging vereisen.

Om de totale productielimiet te kennen, vermenigvuldig dit aantal met het totale aantal verbindingen zoals die in de bovenstaande formule worden beschreven.

0 betekent geen limiet, de MTA zal MT zo snel mogelijk verzenden.

Over het algemeen wordt aanbevolen deze instelling onder de 1000 te houden, aangezien het onmogelijk is een exacte doorvoer boven dit aantal te garanderen, tenzij deze op de uiteindelijke architectuur is gebaseerd en specifiek om een SMPP-leverancier is verzocht. Het kan beter zijn om het aantal verbindingen te verhogen om boven 1000 MT/s te gaan.

#### Tijd vóór opnieuw verbinden {#time-reconnection}

Wanneer de verbinding van TCP wordt verloren, zal de schakelaar dit aantal seconden wachten alvorens te proberen om een verbinding te maken.

#### Vervalperiode van de MT {#expiration-period}

Time-out tussen `SUBMIT_SM` en de overeenkomstige `SUBMIT_SM_RESP`. Als de `RESP` niet tijdig wordt ontvangen, zal de boodschap als gezakt worden beschouwd en zal het globale hertestbeleid van de MTA van toepassing zijn.

#### Time-out binden {#bind-timeout}

Time-out tussen de poging van TCP verbinden en de `BIND_*_RESP` antwoord. Wanneer de verbinding uitvalt, wordt deze door de Adobe Campaign-connector gesloten en wacht deze op Tijd voordat u opnieuw verbinding maakt. Probeer het opnieuw.

#### request_link period {#enquire-link-period}

`enquire_link` is een speciaal soort PDU die wordt verzonden om de verbinding levend te houden. Deze periode is in seconden. De campagnector verzendt slechts `enquire_link` wanneer de verbinding inactief is om bandbreedte te besparen. Als geen RESP na tweemaal deze periode wordt ontvangen, zal de verbinding als dood worden beschouwd en zal een reconnectieproces worden teweeggebracht.

### SMSC-specificaties {#SMSC-specifics}

Deze instellingen zijn geavanceerde instellingen die de Adobe Campaign-aansluiting aanpassen aan de meeste specifieke kenmerken van de SMPP-implementatie.

**Een specifieke toewijzing van coderingen definiëren**

Zie de [SMS-tekstcodering](sms-protocol.md#sms-text-encoding) voor meer informatie over tekstcodering.

Met deze instelling kunt u een aangepaste coderingstoewijzing definiëren die afwijkt van de specificatie. U kunt een lijst met coderingen en hun `data_coding` waarde.

De MTA zal proberen te coderen gebruikend het eerste coderen in de lijst. Als dit mislukt, probeert het de volgende codering in de lijst te gebruiken, enzovoort. Als het bericht niet kan worden gecodeerd, treedt er een fout op. Zodra het coderen wordt gevonden, zal MTA tot `SUBMIT_SM PDU` met de gecodeerde tekst en de `data_coding` veldset met de waarde die in de tabel is opgegeven.

De volgorde van items in de tabel is belangrijk: coderingen zijn pogingen van boven naar beneden. Plaats de goedkoopste of meest aanbevolen codering boven aan de lijst, gevolgd door meer en duurdere coderingen.

Houd er rekening mee dat UCS-2 nooit zal mislukken omdat het alle tekens kan coderen die in Adobe Campaign worden ondersteund en dat de maximale lengte van een UCS-2 SMS veel kleiner is: alleen 70 tekens.

U kunt deze instelling ook gebruiken om een specifieke codering te forceren die altijd moet worden gebruikt door slechts 1 regel in de toewijzingstabel te declareren.

De standaardtoewijzing die wordt gebruikt wanneer het selectievakje niet is ingeschakeld, is gelijk aan de volgende tabel:

| data_coding | Codering |
|---|---|
| 0 | GSM |
| 9 | UCS-2 |

Dit betekent dat de MTA zal proberen de boodschap in GSM te coderen. Als het erin slaagt, zal het het met verzenden `data_coding` ingesteld op 0.

Als het bericht niet in GSM kan worden gecodeerd, zal het in UCS-2 worden gecodeerd en zal plaatsen `data_coding` tot en met 8.

#### message_payload inschakelen {#enable-message-payload}

Als deze optie is uitgeschakeld, wordt lang SMS gesplitst door de MTA en verzonden in meerdere `SUBMIT_SM PDU`Net als bij UDH. Het bericht wordt opnieuw samengesteld door de mobiele telefoon na UDH-gegevens.

Wanneer gecontroleerd, lange SMS zal in één SUBMIT_SM PDU worden verzonden, die de tekst in het bericht_payload facultatieve gebied zetten. Zie de [SMPP-specificatie](sms-protocol.md#ACS-SMPP-connector) voor meer informatie hierover.

Als deze functie is ingeschakeld, kan Adobe Campaign geen SMS-onderdelen afzonderlijk tellen: alle berichten worden geteld zoals ze in één deel zijn verzonden.

#### Het volledige telefoonnummer verzenden {#send-full-phone-number}

Wanneer dit selectievakje niet is ingeschakeld, worden alleen cijfers van het telefoonnummer verzonden naar de provider (`destination_addr` van het `SUBMIT_SM` veld). Dit is het standaardgedrag aangezien de internationale aantalindicator, gewoonlijk a + prefix, door TON en NPI gebieden in SMPP wordt vervangen.

Als het selectievakje is ingeschakeld, wordt het telefoonnummer ongewijzigd verzonden, zonder voorbehandeling en mogelijke spaties, plus voorvoegsel- of hekje-/sterborden.

Deze eigenschap heeft ook een effect op het gedrag van de auto functie van de lijst van gewezen personen van de repliek: wanneer checkbox niet wordt gecontroleerd, zal een + prefix aan telefoonaantallen worden toegevoegd die in de quarantainetabel worden opgenomen om te compenseren + prefix die van het telefoonaantal door het protocol SMPP zelf wordt verwijderd.

#### TLS-certificaatcontrole overslaan {#skip-tls}

Wanneer TLS is ingeschakeld, slaat u alle certificaatcontroles over.

Wanneer gecontroleerd, is de verbinding niet veilig meer, zou het niet in productie moeten worden toegelaten.

Het kan nuttig voor het zuiveren of testdoeleinden zijn.

U kunt kiezen uit drie verschillende waarden voor de certificaatvalidatie:

* Volledige certificatiecontrole (met inbegrip van hostname), gebrek.
* De verificatie van de hostnaam overslaan.
* Sla de verificatie van het certificaat over.

#### Binden TON/NPI {#bind-ton-npi}

TON (type nummer) en NPI (indicator nummerplan) beschreven in punt 5.2.5 van het [SMPP 3.4-specificatie](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (bladzijde 117). Deze waarden moeten worden ingesteld op wat de provider nodig heeft.

Ze worden ongewijzigd verzonden in `addr_ton` en `addr_npi` velden van de PDU BIND.

#### Adresbereik {#address-range}

Verzonden as-is op het address_range gebied van BIND PDU. Deze waarde moet worden ingesteld op wat de provider nodig heeft.

#### Aantal voor ongeldige id-erkenning {#invalid-id}

Beperkt het aantal **Bericht-id is ongeldig** `DELIVER_SM_RESP` die voor één enkele SR kunnen worden verzonden.

**Dit zou slechts voor het oplossen van problemendoel als oplossing moeten worden gebruikt** en onder normale omstandigheden op 0 ingesteld.

Voorbeeld bij instelling op 2:

* De leverancier verzendt een SR (`DELIVER_SM`) met ID &quot;1234&quot;.

* ID &quot;1234&quot; is niet gevonden in de database.

* De schakelaartellingen 1 **Ongeldige id** fout voor die id, zodat het verzendt `DELIVER_SM_RESP` met de foutcode &quot;Bericht-ID ongeldig&quot; (normaal gedrag).

* De provider probeert dezelfde SR opnieuw met ID &quot;1234&quot;.

* De id &quot;1234&quot; is nog steeds niet gevonden in de database.

* De schakelaartellingen 2 **Ongeldige id** fout voor die id, zodat het verzendt `DELIVER_SM_RESP` &quot;OK&quot;, zelfs als het niet correct is verwerkt.

* Deze functie is bedoeld om SR-buffers op de providerzijde te verwijderen wanneer een ongeldig SR-blok legitiem is dat berichten niet kunnen worden verwerkt.

Als u dit veld instelt op 0, wordt het mechanisme uitgeschakeld waarbij **Bericht-id is ongeldig** altijd wordt geretourneerd, dit is normaal gedrag.

Als u dit veld instelt op 1, reageert de connector altijd op OK, zelfs als de id ongeldig is. Dit zou slechts aan 1 moeten worden geplaatst onder toezicht, voor het oplossen van problemen en voor de minimumhoeveelheid tijd, bijvoorbeeld om van een leverancier-zijkwestie terug te krijgen.

#### Extractieregex van de id in de SR {#regex-extraction}

SR-indeling wordt niet strikt afgedwongen door de specificatie van het SMPP-protocol. Het is slechts een aanbeveling die in [Aanhangsel B](sms-protocol.md#sr-error-management) (blz. 167). Sommige implementatoren van SMPP formatteren dit gebied verschillend, zodat heeft Adobe Campaign een manier nodig om het correcte gebied te halen.

Standaard worden maximaal 10 alfanumerieke tekens vastgelegd na `id:`.

De regex moet precies één vastleggroep hebben met een onderdeel tussen haakjes. Haakjes moeten rond het id-onderdeel staan. De regex-indeling is PCRE.

Wanneer u deze instelling aanpast, moet u zoveel mogelijk context opnemen om onjuiste triggers te voorkomen. Als er specifieke voorvoegsels zijn, zoals `id:` in de norm, neem hen in regex op. Gebruik ook woordscheidingstekens (\b) zoveel mogelijk om te voorkomen dat tekst in het midden van een woord wordt vastgelegd.

Als u niet genoeg context in de regex opneemt, kan er een klein veiligheidsprobleem ontstaan: de feitelijke inhoud van het bericht kan in de SR worden opgenomen. Als u alleen een specifieke id-indeling aanpast zonder context, bijvoorbeeld een UUID, wordt de werkelijke tekstinhoud mogelijk geparseerd, bijvoorbeeld een UUID die is ingesloten in het tekstveld, in plaats van de ID.

#### Regex is toegepast om de status van geslaagd/fout te bepalen {#regex-applied}

Wanneer berichten met een onbekende stat/err gebiedscombinatie worden ontmoet, worden deze regex toegepast op het staatsgebied om te bepalen of SR een succes of een fout was. SR met statuswaarden die niet overeenkomen met een van deze regexes wordt genegeerd.

Stelt standaard waarden in die beginnen met `DELIV`, bijvoorbeeld `DELIVRD` in de [Aanhangsel B](sms-protocol.md#sr-error-management), worden beschouwd als succesvol afgeleverd en alle statuswaarden die overeenkomen met fouten, bijvoorbeeld `REJECTED`, `UNDELIV`worden beschouwd als fouten.

#### ID-indeling in MT-bevestiging {#id-format-mt}

Dit geeft de indeling van de id aan die in het dialoogvenster `message_id` van het `SUBMIT_SM_RESP PDU`.

* **Niet wijzigen**: De id wordt als zodanig opgeslagen in de database, als ASCII-gecodeerde tekst. Er vindt geen voorbewerking of filtering plaats.

* **Decimaal getal**: Van de id wordt verwacht dat deze een decimaal getal in ASCII-vorm is. Voorloopspaties, volgspaties en voorloopnullen worden verwijderd wanneer deze instelling wordt gebruikt.

* **Hexadecimaal getal**: Van de id wordt verwacht dat het een hexadecimaal getal in ASCII-vorm is, zonder voorlooppunt 0x of navolgend h. De id wordt vervolgens omgezet in een decimaal getal voordat deze in de database wordt opgeslagen.

* **Hexadecimale tekenreeks**: Van de id wordt verwacht dat het een ASCII-gecodeerde tekst betreft die zelf een tekenreeks met bytes is die als hexadecimaal is gecodeerd. Bijvoorbeeld in PDU zult u vinden `0x34 0x31 0x34 0x32 0x34 0x33`, dat naar ASCII &quot;414243&quot; vertaalt. Deze tekenreeks wordt vervolgens gedecodeerd als een hexadecimale reeks bytes en u krijgt als resultaat &quot;ABC&quot;: u slaat de id &quot;ABC&quot; op in de database.

#### ID-indeling in SR {#id-format-sr}

Dit geeft de indeling aan van de id die is vastgelegd door de `Extraction` regex van identiteitskaart in SR. Waarden hebben dezelfde betekenis en hetzelfde gedrag als de notatie in MT hierboven.

**SR-id of foutcode in optioneel veld**

>[!NOTE]
>
>Alleen beschikbaar in de Adobe Campaign Classic Extended SMPP-connector.

Als deze optie is ingeschakeld, wordt de inhoud van optionele velden toegevoegd aan de tekst die wordt verwerkt door bovenstaande regexes. De tekst heeft de opmaak `0xTAG:VALUE`, `0xTAG` de 4-cijferige hexadecimale waarde van de tag in hoofdletters is, bijvoorbeeld `0x002E`.

U kunt bijvoorbeeld de id vastleggen in het dialoogvenster `receipted_message_id` veld. Hiervoor schakelt u dit selectievakje in en wordt de volgende tekst aan de status toegevoegd:

```
0x001E:05e3299e-8d37-49d0-97c6-8e4fe60c7739
```

In dit voorbeeld is 0x001E de tag van het optionele veld en is UUID de waarde van het veld.

Als u deze waarde wilt vastleggen, kunt u nu de volgende regex instellen in het vak Extractie van de id in het veld SR:

```
\b0x001E:([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})\b
```

>[!IMPORTANT]
>
>U kunt alleen optionele velden vastleggen die tekstwaarden (ASCII/UTF-8) hebben. Specifiek, kunnen de binaire gebieden niet betrouwbaar met het huidige regex systeem worden gevangen.

**SR-id of foutcode in tekstveld**

Als deze optie is ingeschakeld, wordt **Tekst** veld wordt bewaard tijdens de verwerking van de statustekst van de SR.

Dit is handig als de provider belangrijke gegevens in dit veld plaatst, zoals de id of de status. Dit veld kan gewoonlijk veilig worden verwijderd, omdat het tekst met een niet-ASCII-codering kan bevatten en de verwerking van regex kan verstoren.

Als u deze optie inschakelt, kan een zeer klein beveiligingsprobleem optreden als de `Extraction` Regex van de id in het veld SR is niet specifiek genoeg. De inhoud van de **Tekst** veld kan als een id worden geparseerd en een aanvaller kan dit gebruiken om vervalste id&#39;s te injecteren, wat tot een gedeeltelijke ontkenning van de servicesituatie kan leiden.

**Tag voor service-id**

Hiermee kunt u een aangepaste TLV toevoegen. In dit veld wordt het taggedeelte ingesteld. De waarde kan per levering in worden aangepast **Service- of programma-id** waarde in de geavanceerde parameters van de levering.

Met deze instelling kunt u slechts één TLV-optie per bericht toevoegen.

### Automatisch antwoord verzonden aan de MO {#automatic-reply}

>[!IMPORTANT]
>
>In Adobe Campaign Classic en in een hybride architectuur vereist het toepassen van auto-antwoord voor de uitgebreide schakelaar SMPP om schrijftoegang voor de middelste exploitant op toe te voegen **Externe rekening** map.

Met deze functie kunt u snel tekst op de MO beantwoorden en per korte code naar de lijst van gewezen personen verzenden.

De **Trefwoord** en **Korte code** kolommen bepalen voorwaarden om de auto reactie teweeg te brengen. Als beide velden overeenkomen, wordt de MO verzonden en wordt de aanvullende actie geactiveerd. Als u een jokerteken wilt opgeven, laat u het veld leeg. Trefwoorden komen overeen met het eerste alfanumerieke woord in de MO-tekst, waarbij leestekens en voorloopruimten worden genegeerd. Het betekent dat de **Trefwoord** veld mag geen spaties bevatten en moet één woord zijn.

De **Trefwoord** instelling is een voorvoegsel. Als u bijvoorbeeld &quot;AD&quot; opgeeft, komt deze overeen met &quot;AD&quot;, &quot;ADAPT&quot; en &quot;ADOBE&quot;. Als u meerdere trefwoorden met een algemeen voorvoegsel hebt, moet u rekening houden met de volgorde, aangezien de trefwoorden van boven naar beneden worden verwerkt.

De **Antwoord** kolom is de tekst die moet worden beantwoord. Er is geen personalisatie beschikbaar op dit gebied. Als u dit veld leeg laat, wordt er geen bericht geantwoord, maar wordt de aanvullende actie toch geactiveerd.

De **Aanvullende actie** de kolom verstrekt een extra actie wanneer allebei **Trefwoord** en **Korte code** overeenkomst, lege korte code komt overeen met alle korte codes. U kunt naar quarantaine verzenden of uit quarantaine verwijderen, waarde geen antwoorden op de tekst. Als u een **Aanvullende actie** maar laat de **Antwoord** veld leeg, wordt de actie uitgevoerd, maar er wordt geen antwoord verzonden. Quarantaine wordt alleen toegepast voor de opgegeven korte code of voor alle korte codes als het veld leeg blijft.

>[!IMPORTANT]
>
>De instelling voor het volledige telefoonnummer verzenden heeft invloed op het gedrag van het quarantainemechanisme voor automatische antwoorden: als het volledige telefoonnummer niet wordt gecontroleerd, wordt het telefoonnummer dat in quarantaine wordt geplaatst, vooraf bepaald door een plusteken (&quot;+&quot;), zodat het compatibel is met de indeling voor het internationale telefoonnummer.

Alle items in de tabel worden in de opgegeven volgorde verwerkt, totdat één regel overeenkomt. Als de veelvoudige regels een MO aanpassen, slechts zal de hoogste regel worden toegepast.

## Sjabloonparameters voor verzending via SMS {#sms-delivery-template-parameters}

Sommige parameters kunnen per leveringsmalplaatje worden geplaatst.

### Van veld {#from-field}

Dit veld is optioneel. Het staat met voeten treedt afzenderadres (oADC) toe. De inhoud van dit veld wordt in het dialoogvenster `source_addr` van het `SUBMIT_SM PDU`.

Het veld is door de SMPP-specificatie beperkt tot 21 tekens, maar sommige providers staan mogelijk langere waarden toe. Houd er rekening mee dat in sommige landen zeer strikte beperkingen kunnen worden toegepast, zoals lengte, inhoud en toegestane tekens.

### Leveringsparameters {#delivery-parameters}

#### Maximum aantal SMS per bericht {#maximum-sms}

Deze instelling werkt alleen als de instelling **Berichtlading** instellen is uitgeschakeld. Als het bericht meer SMS dan deze waarde vereist, zal een fout worden teweeggebracht.

Het protocol van SMS beperkt SMS tot 255 delen, maar sommige mobiele telefoons hebben moeite samenstellend lange berichten met meer dan 10 delen zo, hangt de grens van het nauwkeurige model af. We raden u aan niet meer dan 5 delen per bericht te verzenden.

Vanwege de manier waarop gepersonaliseerde berichten in Adobe Campaign werken, kan de grootte van berichten variëren. Een grote hoeveelheid lange berichten zou de verzendkosten kunnen verhogen.

#### Transmissiemodus {#transmission-mode}

In dit veld wordt het type SMS aangegeven dat u wilt overbrengen: normale of flash-berichten, die op de mobiele kaart of de simkaart worden opgeslagen.

Deze instelling wordt verzonden in het dialoogvenster `dest_addr_subunit` optioneel veld in de `SUBMIT_SM PDU`.

* **Niet opgegeven** verzendt geen optioneel veld in de PDU.

* **Flash** stelt de waarde in op 1. Er wordt een Flash-bericht verzonden dat op de mobiele telefoon verschijnt en niet in het geheugen is opgeslagen.

* **Normaal** stelt de waarde in op 0. Het stuurt een normaal bericht.

* **Opslaan op mobiele apparaten** stelt de waarde in op 2. Het vertelt de telefoon om SMS in intern geheugen op te slaan.

* **Opslaan op terminal** stelt de waarde in op 3. Het vertelt de telefoon om SMS in de kaart op te slaan SIM.

#### Geldigheidsperiode {#validity-period}

De geldigheidsperiode wordt meegedeeld in het `validity_period` van het `SUBMIT_SM PDU`. De datum wordt altijd opgemaakt als een absolute UTC-tijdnotatie. Het datumveld eindigt met &quot;00+&quot;.

## Uitgebreide algemene SMPP-connector {#acc-extended-connector}

![](assets/do-not-localize/sms_protocol_4.png)

Pijlen vertegenwoordigen gegevensstromen.

Wanneer het verzenden van leveringsdelen, paait MTA kinderen MTA. Het aantal MTA kindprocessen is dynamisch en hangt van een configuratie in serverConf.xml af. Elk kind MTA concretiseert de schakelaar `CSmppConnectorWorker` die verbinding maakt met de SMPP-provider. De verbindingen worden levend gehouden zolang het kind MTA levend wordt gehouden, ook configureerbaar in serverConf.xml.

Het proces van SMS verwerkt slechts SR, het verbindt met de leverancier en verlaat de verbinding open. Het proces verbindt opnieuw om de 10 minuten om nieuwe montages opnieuw te laden, dit is normale verrichting.

### Overeenkomende MT-, SR- en Broadlog-vermeldingen {#matching-mt}

Een tussenliggende tabel `nmsProviderMsgId` wordt gebruikt om MT en SR gegevens tijdelijk op te slaan alvorens asynchroon aan de breedband wordt begaan.

`nmsProviderMsgId` tabel bevat drie groepen kolommen:

* Kolommen die worden bijgewerkt wanneer een MT wordt verzonden en erkend: `iBroadLogId`, `iDeliveryId`

* Kolommen die worden bijgewerkt wanneer een SR wordt ontvangen: `iMsgId`, `iStatus`

* Kolommen die altijd worden bijgewerkt: `tsCreated`, `sProviderId`

Wanneer zowel MT als SR verwerking beëindigde, zou u volledige lijnen, met zowel breedbandinformatie als statusinformatie moeten hebben.

Hier, `iMsgId` is gekoppeld aan `nmsBroadLogMsg` tabel met de volledige status/foutmelding.

Het proces van SMS controleert volledige lijnen elke minuut, dan verwerkt hen asynchroon:

* De volledige regel wordt gelezen.
* Het proces van SMS berekent de naam van de uitzendingstabel die op de leveringsafbeelding wordt gebaseerd.
* Het proces van SMS werkt de uitzendingstabel met berichtidentiteitskaart en de status bij.

**Doorvoer en parallelle verbindingen**

Elk kind MTA leidt tot een configureerbare hoeveelheid verbindingen, zo beperkend het aantal kind MTA zal het aantal verbindingen beperken. Omdat de correlatie tussen MTA kindprocessen en verkeer gecorreleerd is, kan dit enigszins gecontroleerd maar nog een beetje onvoorspelbaar zijn.

## Voordat u live gaat {#checklist}

Deze checklist bevat een lijst met dingen die u moet controleren voordat u live gaat. Een onvolledige opstelling kan tot vele kwesties leiden.

### Controleren op conflicten met externe accounts {#external-account-conflict}

Controleer of je geen oude externe SMS-accounts hebt. Als u de testaccount uitschakelt, loopt u het risico dat deze weer wordt ingeschakeld in het productiesysteem en dat er potentiële conflicten ontstaan.

Als u meerdere accounts op dezelfde Adobe Campaign-instantie hebt die verbinding maken met dezelfde provider, neemt u contact op met de provider om ervoor te zorgen dat ze daadwerkelijk een onderscheid maken tussen deze accounts. Voor meerdere accounts met dezelfde aanmelding is een extra configuratie vereist.

### Brede SMPP-sporen tijdens controles inschakelen {#enable-verbose}

U zou uitgebreide sporen SMPP tijdens controles altijd moeten toelaten.
Zelfs als u de logboeken niet zelf kunt controleren, is het gemakkelijker voor [Klantenservice Adoben](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om u te helpen.

### Je SMS testen {#test}

* **SMS verzenden met allerlei tekens**
Als u SMS met niet-GSM of niet-ASCII karakters moet verzenden, probeer verzendend sommige berichten met zo vele diverse karakters mogelijk. Als u een aangepaste tekentoewijzingstabel instelt, moet u minstens één SMS verzenden voor alles wat mogelijk is `data_coding` waarden.

* **Controleren of SR correct is verwerkt**
Het SMS moet worden gemarkeerd als ontvangen in het leveringslogboek. Het leveringslogboek zou succesvol moeten zijn en als het volgende kijken:
  `SR yourProvider stat=DELIVRD err=000|#MESSAGE`
Controleer of u de naam van de leverancier van de levering hebt gewijzigd. Het leveringslogboek mag nooit bevatten **SR Generic** op productieomgevingen.

* **Controleren of MO wordt verwerkt**
Als u MO moet verwerken (automatische antwoorden, MO in het gegevensbestand opslaan, enz.) probeer een aantal tests uit te voeren. Verzend een paar SMS voor alle automatische antwoordsleutelwoorden en controleer als het antwoord snel genoeg, niet meer dan een paar seconden is.
Controleer in het logbestand dat Adobe Campaign met succes heeft gereageerd `DELIVER_SM_RESP` (command_status=0).

### PDU&#39;s controleren {#check-pdus}

Zelfs als de berichten succesvol kijken, is het belangrijk om te controleren dat PDUs behoorlijk geformatteerd is.

Deze stap is nodig wanneer u verbinding maakt met een provider die nog niet eerder verbinding had met Adobe Campaign.

#### BIND {#bind}

Controleren of `BIND_* PDUs` correct worden verzonden. Het belangrijkste om te controleren is dat de leverancier altijd succesvol terugkeert `BIND_*_RESP PDUs` (command_status = 0).

Controleren of er niet te veel zijn `BIND_* PDU`s. Als er teveel zijn, zou het erop kunnen wijzen dat de verbinding instabiel is. Zie de [Problemen met instabiele verbindingen](sms-protocol.md#issues-unstable-connection) voor meer informatie.

#### INQUIRE_LINK {#enquire-link-pdus}

Controleren of `ENQUIRE_LINK PDU`s regelmatig worden uitgewisseld wanneer de verbinding niet-actief is.

**SUBMIT_SM/DELIVER_SM**

Verzend een bericht, dan onderzoek in de logboeken naar zijn overeenkomstige `SUBMIT_SM`, `SUBMIT_SM_RESP`, `DELIVER_SM` en `DELIVER_SM_RESP PDU`s.

Met de `SUBMIT_SM PDU`:

* Controleren of `data_coding` is correct, 0 door gebrek.
* Controleren of `short_message` correct is gecodeerd. Decoderen met een hexadecimale converter die meerdere coderingen ondersteunt.

Met de `SUBMIT_SM_RESP PDU`:

* Controleer of dit gelukt was, command_status = 0.
* Controleer of de hoofdtekst een correct opgemaakte id bevat, gevolgd door de byte &#39;0&#39;.

Met de `DELIVER_SM PDU`:

* De hexadecimale code decoderen `short_message` veld.
* Controleer met een regex controlehulpmiddel dat regex in wordt bepaald `Extraction` regex van identiteitskaart in SR keert precies één vangstgroep terug en dat het volledige identiteitskaart in het bericht vangt.
* Controleer of de uitgepakte id overeenkomt met de id in `SUBMIT_SM_RESP`.
* Controleer of de regex is gedefinieerd in `Extraction` regex van de status in de SR retourneert de inhoud van het statusveld.
* Controleer of de regex is gedefinieerd in `Extraction` regex van de fout in de SR retourneert de inhoud van het foutveld.

Met de `DELIVER_SM_RESP PDU`:

* Controleer of het bericht snel is verzonden na ontvangst van de `DELIVER_SM PDU`, doorgaans minder dan 1 seconde.
* Controleer of dit gelukt was, command_status = 0.

### Raadpleeg uw provider {#provider}

Zelfs als uw SMS succesvol is, contacteer de leverancier om te zien of is alles in orde.

### Brede SMPP-sporen uitschakelen {#disable-verbose}

Wanneer alle controles zijn voltooid, is het laatste: **Brede SMPP-sporen uitschakelen** om niet te veel logbestanden te genereren. U kunt hen voor het oplossen van problemendoeleinden opnieuw toelaten zelfs op productiesystemen.
